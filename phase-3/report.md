| Page / Feature	| Guest |	Reserver | Administrator |
| :---         |     :---:      |     :---:      |     :---:      |
| /	| | | |		
| └─ View booked resources	| ❌	| ✅	| ✅ |
| └─ Can see "Add a new resource" button | ❌	| ✅	| ✅ |
| └─ Can see "Add a new reservation" button | ❌	| ✅	| ✅ |
| /resources	| | | |	
| └─ Create a new resource	| ⚠️(Note 3*)	| ✅	| ✅ |
| └─ Can modify a resource	| ⚠️(Note 6*)	| ⚠️(Note 7*)	| ✅ |
| /reservation	| | ⚠️(Note 4*) | |		
| └─ Change a reserver from own booked resources	| ❌	| ⚠️(Note 1*)	| ✅ |
| └─ Change a reserver from all booked resources	| ❌	| ❌	| ✅ |
| └─ Change a reserved resource from own booked resources	| ❌	| ✅	| ✅ |
| └─ Change a reserved resource from all booked resources	| ❌	| ❌	| ✅ |
| └─ Change a reservation time from own booked resources	| ❌	| ✅(Note 2*)	| ✅(Note 2*) |
| └─ Change a reservation time from all booked resources	| ❌	| ❌(Note 2*)	| ✅(Note 2*) |
| └─ Create a new reservation	| ❌ | ✅ | ✅ |
| /admin ⚠️(Note 5*)| | | |
| /profile ⚠️(Note 5*)| | | |		
| /login | | | |
| └─ Can login	| ✅ | ✅ | ✅ |
| /logout | | | |
| └─ Can logout	| ❌ | ✅ | ✅ |
| /register | | | |
| └─ Can register	| ✅ | ✅ | ✅ |

Symbols used:
✅ Pass
❌ Fail
⚠️ Attention

Notes:

1. It's not good that a reserver user can change the reserver to whoever he/she wants
2. Changing the reservation end time to smaller than start time throws an error
3. Quest can add new resources if he/she goes directly to resources page
4. Reserver can see all reservation forms even he/she is not the reserver when he/she goes directly to the page (e.g. http://localhost:8000/reservation?id=3). 
5. Not implemented
6. Quest can see empty form, but can't save anything
7. Reserver cannot go to edit page via normal way, but can edit resources when he/she goes directly to the edit page

WFUZZ:

Sites found: logout, login, register, resources, reservation
Api folders found: resources, session, users
Reservation pages between 1-1000 found: 1-63 found (some numbers missing between them)
The api page contains JSON data

ZAP report:

My PC couldn't handle the ZAP process well (It couldn't execute multiple test rounds). Virtual Box crashed multiple times so there is only the raport of one test round. 
[Zap report](https://github.com/liskomes/musical-waffle/blob/main/The%20Booking%20System%20Phase%203/Zap%20report.md)

Results:

✅ 1. The system is accessed via a web browser.

✅ 2. Users can register and, after registration, log in to the system.

✅ 3. A registered and logged-in user acts as either a resource reserver or an administrator.

⚠️ 4. The administrator can add, remove, and modify resources and reservations. ⚠️Reservers can also add/modify resources

⚠️ 5. The administrator can delete the reserver. ⚠️Administrator and user can change the reserver

✅ 6. A reserver can book a resource if they are over 15 years old.

✅ 7. Resources can be booked on an hourly basis.

✅ 8. The booking system displays booked resources without requiring login, but does not show the reserver's identity| Page / Feature	| Guest |	Reserver | Administrator |
| :---         |     :---:      |     :---:      |     :---:      |
| /	| | | |		
| └─ View booked resources	| ❌	| ✅	| ✅ |
| └─ Can see "Add a new resource" button | ❌	| ✅	| ✅ |
| └─ Can see "Add a new reservation" button | ❌	| ✅	| ✅ |
| /resources	| | | |	
| └─ Create a new resource	| ⚠️(Note 3*)	| ✅	| ✅ |
| └─ Can modify a resource	| ⚠️(Note 6*)	| ⚠️(Note 7*)	| ✅ |
| /reservation	| | ⚠️(Note 4*) | |		
| └─ Change a reserver from own booked resources	| ❌	| ⚠️(Note 1*)	| ✅ |
| └─ Change a reserver from all booked resources	| ❌	| ❌	| ✅ |
| └─ Change a reserved resource from own booked resources	| ❌	| ✅	| ✅ |
| └─ Change a reserved resource from all booked resources	| ❌	| ❌	| ✅ |
| └─ Change a reservation time from own booked resources	| ❌	| ✅(Note 2*)	| ✅(Note 2*) |
| └─ Change a reservation time from all booked resources	| ❌	| ❌(Note 2*)	| ✅(Note 2*) |
| └─ Create a new reservation	| ❌ | ✅ | ✅ |
| /admin ⚠️(Note 5*)| | | |
| /profile ⚠️(Note 5*)| | | |		
| /login | | | |
| └─ Can login	| ✅ | ✅ | ✅ |
| /logout | | | |
| └─ Can logout	| ❌ | ✅ | ✅ |
| /register | | | |
| └─ Can register	| ✅ | ✅ | ✅ |

Symbols used:
✅ Pass
❌ Fail
⚠️ Attention

Notes:

1. It's not good that a reserver user can change the reserver to whoever he/she wants
2. Changing the reservation end time to smaller than start time throws an error
3. Quest can add new resources if he/she goes directly to resources page
4. Reserver can see all reservation forms even he/she is not the reserver when he/she goes directly to the page (e.g. http://localhost:8000/reservation?id=3). 
5. Not implemented
6. Quest can see empty form, but can't save anything
7. Reserver cannot go to edit page via normal way, but can edit resources when he/she goes directly to the edit page

WFUZZ:

Sites found: logout, login, register, resources, reservation
Api folders found: resources, session, users
Reservation pages between 1-1000 found: 1-63 found (some numbers missing between them)
The api page contains JSON data

ZAP report:

My PC couldn't handle the ZAP process well (It couldn't execute multiple test rounds). Virtual Box crashed multiple times so there is only the raport of one test round. 
[Zap report](https://github.com/liskomes/musical-waffle/blob/main/The%20Booking%20System%20Phase%203/Zap%20report.md)

Results:

✅ 1. The system is accessed via a web browser.

✅ 2. Users can register and, after registration, log in to the system.

✅ 3. A registered and logged-in user acts as either a resource reserver or an administrator.

⚠️ 4. The administrator can add, remove, and modify resources and reservations. ⚠️Reservers can also add/modify resources

⚠️ 5. The administrator can delete the reserver. ⚠️Administrator and user can change the reserver

✅ 6. A reserver can book a resource if they are over 15 years old.

✅ 7. Resources can be booked on an hourly basis.

✅ 8. The booking system displays booked resources without requiring login, but does not show the reserver's identity
