# 1. Client Requirements


Ngwedi Country Inn (Kimberley) is a small hospitality organization that offers accommodation services, it is far smaller than large scale hotels. As a small property, the inn operates with tighter operational and IT budgets, which includes limited and costly internet bandwidth. The client has also indicated plans for a future branch office, meaning the network and addressing scheme must be designed with scalability in mind, even though the second site is not being built as part of this project.


## Organizational Assumptions

The client brief does not specify the exact room counts, staff numbers, or device counts, so the assumptions of this project are made based on the definition of what an inn is, in order to size the network properly.

Ngwedi Country Inn (Kimberley) is assumed to have 20 guest rooms, which is consistent with the definition of an inn, a full-service one that includes a small restaurant and grounds, rather than that of a large hotel chain.

The client’s network is divided based on who is using it and the sensitive data or systems each group needs to access, essentially into guests and hotel operations.

Guests require internet access only and are inherently untrusted, since their devices are personal and unmanaged, so they are fully separated from every internal system. 

The remaining zones represent different operational functions within the hotel. We have Front desk, HR, Finance, IT and general staff, each grouped separately because they differ in the type of access they require and the risk they would pose to the network if compromised. This division allows sensitive functions such as Finance and HR to be protected more strictly, while less sensitive zones such as Guest Wifi and General Staff are kept isolated from critical hotel systems.

### Zone Criticality and Access

Finance is treated as the most critical zone in the network since it handles banking details and processes payments to both staff and external suppliers. Any compromise of this zone would directly impact the Inn’s finances, which makes it the highest priority to protect.

HR/Admin is treated as the second most critical zone since it stores personal staff information, including records covered under POPIA (the Protection of Personal Information Act), which legally requires this data to be safeguarded.

Front Desk/Reservations is considered moderately sensitive, since it handles guest bookings and processes payments, and therefore communicates directly with Finance, but does not store the same level of sensitive data as HR or Finance.

IT/Management does not represent a distinct operational department in the same way as others, but rather an administrative function with access across all zones. This access is required to configure, monitor and secure the network as a whole, including managing content filtering and preventing malicious access on the Guest and General Staff Networks.

### Per-Zone Device Estimates

Front Desk / Reservations has approximately 2 staff working in shifts, they are equipped with a primary reception PC, a backup PC, a shared printer and a card payment terminal totalling an estimated 4 devices.

HR / Admin has approximately 2 staff, appropriately sized to the property’s overall staff count, they are equipped with staff PCs and a shared printer, totalling an estimated 3 devices.

Finance has approximately 2 staff, kept as a separate function from HR due to sensitivity of financial and banking data, they are equipped with staff PCs and shared printer, totaling an estimated 3 devices.

IT / Management has approximately 1-2 staff, equipped with admin devices, a small local server for network management and monitoring, totalling an estimated 4 devices.

General Staff has an estimated complement of approximately 20 people, made up of cleaners/housekeeping staff, kitchen/chef staff, gardening/maintenance staff, security staff, and waitstaff. With each individual carrying 1 device, totalling an estimated 20 devices.

Guest is sized for approximately 40 devices, accounting for the Inn’s 20 rooms with multiple guest devices (phone, laptop/tablet) per room, plus reasonable headroom.


### Network Zones


| Zone | Who is in it | What they need | Talks to |
|---|---|---|---|
| Guest Wifi | Guests | Internet only | Nobody |
| Front Desk / Reservations | Reception Staff | Booking system, internet, printer | Finance |
| HR / Admin | HR staff | Internet, worker records, clock-in | Finance |
| Finance | Accounts staff | Internet (banking/suppliers), finance records | Front Desk, HR |
| General Staff | Cleaners kitchen, gardeners, security, e.t.c. | Internet, basic internal communication | Nobody critical |
| IT / Management | Network Admin | Access to all zones for config/security | All zones (admin only)
