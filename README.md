# 🌍 EcoRide CRM – Electric Vehicle Ride-Hailing & Fleet Management

EcoRide CRM is a Salesforce-based solution designed for managing an **electric vehicle (EV) ride-hailing business**.  
It helps manage customers, drivers, vehicles, fleet maintenance, ride bookings, invoicing, and reporting—all in a centralized Salesforce environment.

---

## 📌 Phase 1: Problem Understanding & Industry Analysis

### Requirement Gathering
EV ride-hailing companies face challenges in managing rides, drivers, vehicles, and fleet health. Key requirements include:
- Centralized ride booking & customer management
- Driver allocation & vehicle assignment
- EV battery health and charging tracking
- Automated invoicing post-ride
- Dashboards for revenue, ride statistics, and fleet utilization

### Stakeholder Analysis
- **Customers** → Book rides, give feedback  
- **Drivers** → Accept rides, update ride status  
- **Fleet Managers** → Track EV vehicles, maintenance, and charging  
- **Admins** → Configure CRM, monitor operations, generate reports  
- **Corporate Clients** → Bulk ride bookings, corporate billing

### Business Process Mapping
1. Customer requests a ride (pickup & drop).  
2. Dispatcher/admin assigns a driver + EV vehicle.  
3. Driver completes the ride.  
4. System generates an invoice & marks ride completed.  
5. Vehicle logs charging/maintenance data for future reference.

### Industry-Specific Use Case Analysis
- Ride-hailing efficiency, EV fleet management, sustainability tracking

### AppExchange Exploration
- Ride Management & Fleet Management apps as inspiration  
- Custom Salesforce solution built for learning and cost-effectiveness

---

## 📌 Phase 2: Org Setup & Configuration

### Salesforce Editions
- Developer Edition for project  
- Enterprise Edition recommended for production

### Company Profile Setup
- **Company Name:** EcoRide Pvt. Ltd  
- **Time Zone:** IST  
- **Currency:** INR  
- Business Hours: 24x7

### User Setup & Licenses
- Admin → Full access  
- Dispatcher → Assign rides/vehicles  
- Driver → Update ride status only  
- Corporate Client → Limited access for bookings & invoices

### Profiles & Roles
- Profiles: Admin, Dispatcher, Driver, Customer  
- Roles: Admin > Dispatcher > Driver > Customer  

### Permission Sets
- Fleet_Reports_Access → Dashboard access  
- EV_API_Access → For future integration

### OWD & Sharing Rules
- Customer, Driver, Vehicle, Ride → Private / controlled  
- Share ride records with assigned driver and management

### Login Access Policies
- Drivers → Restricted hours  
- Admins → Full access

### Dev Org & Deployment
- Built in Developer Org  
- Deployment via Change Sets or SFDX

---

## 📌 Phase 3: Data Modeling & Relationships

### Objects
- Customer__c → Name, Contact Info, Ride History  
- Driver__c → Name, Vehicle Assigned, Availability  
- Vehicle__c → Type, Battery %, Maintenance Logs  
- Ride__c → Pickup, Drop, Status, Fare  
- Invoice__c → Ride, Amount, Payment Status

### Relationships
- Ride ↔ Customer (Lookup)  
- Ride ↔ Driver (Lookup)  
- Vehicle ↔ Driver (Lookup)  
- Invoice ↔ Ride (Master-Detail)

### Record Types & Page Layouts
- Ride → Standard vs Premium  
- Vehicle → Sedan vs SUV  
- Layouts for Customer, Driver, Vehicle, Ride

### Schema Builder
- Visualize Customer ↔ Ride ↔ Driver ↔ Vehicle relationships

---

## 📌 Phase 4: Process Automation (Admin)

### Validation Rules
- Ride cannot be completed without driver/vehicle assigned  
- Vehicle battery % must be between 0–100

### Approval Processes
- High-fare rides → Manager approval  
- Vehicle maintenance requests → Fleet manager approval

### Flows
- Record-Triggered Flow → Auto-assign driver for new ride  
- Screen Flow → Dispatcher updates ride status  
- Scheduled Flow → Daily fleet maintenance reminders  
- Auto-Launched Flow → Send invoices on ride completion

### Email Alerts & Tasks
- Ride confirmation emails  
- Maintenance reminders  
- Auto-create task for driver when ride assigned

### Custom Notifications
- Notify customer on ride assignment  
- Notify driver of new ride

---

## 📌 Phase 5: Apex Programming (Developer)

### Apex Classes
- RideService → Ride creation and assignment logic  
- VehicleService → Track vehicle availability and battery  
- DriverService → Driver load management  
- InvoiceService → Invoice generation

### Triggers
- RideTrigger → Update driver/vehicle assignment  
- VehicleTrigger → Update vehicle availability on ride completion  
- InvoiceTrigger → Generate invoice when ride completed

### Best Practices
- Bulkified triggers  
- No SOQL/DML in loops  
- Centralized service classes

### Asynchronous Apex
- Batch Apex → Update monthly driver performance  
- Queueable Apex → Send bulk ride notifications  
- Scheduled Apex → Weekly revenue & utilization summary

### Exception Handling & Test Classes
- Use try/catch, log to Ride_Error_Log__c  
- Create test data and achieve >85% coverage

---

## 📌 Phase 6: User Interface Development

- Lightning App: “EcoRide CRM”  
- Record pages for Customers, Drivers, Vehicles, Rides, Invoices  
- Utility Bar: Quick access to dashboards & reports  
- LWCs:  
  - Ride summary dashboard  
  - Driver load visualization  
  - Fleet status tracker  
- Wire Adapters to fetch Salesforce data  
- Navigation Service for smooth module transitions

---

## 📌 Phase 7: Integration & External Access

- External API integration for GPS route tracking  
- Named Credentials for secure callouts  
- REST API → External system can fetch ride & invoice data  
- Platform Events → Notify external apps of ride updates  
- Salesforce Connect for connecting with fleet telemetry systems  
- OAuth → Secure authentication

---

## 📌 Phase 8: Data Management & Deployment

- Data Import Wizard → Initial customer, driver, vehicle data  
- Data Loader → Bulk ride & invoice uploads  
- Duplicate Rules → Prevent duplicate entries  
- Scheduled Data Export → Weekly backups  
- Deployment → Change Sets (sandbox → production)  
- Advanced → ANT Migration Tool & SFDX with GitHub

---

## 📌 Phase 9: Reporting, Dashboards & Security Review

### Reports
- Ride Bookings by Vehicle/Driver  
- Vehicle Utilization Summary  
- Customer Ride History  

### Dashboards
- Management → Revenue, rides, fleet utilization  
- Dispatcher → Ride assignments, pending rides  
- Drivers → Workload & schedule

### Security
- Role hierarchy → Admin > Dispatcher > Driver > Customer  
- Field-level security → Sensitive info hidden  
- Sharing Rules → Controlled ride & vehicle access  
- Session Settings → Stricter login policies

---

## 📌 Phase 10: Final Presentation & Demo Day

- Prepared presentation highlighting EcoRide CRM benefits  
- Live demo: Booking → Driver assignment → Ride completion → Invoice generation → Dashboard insights  
- Collected feedback from management & fleet  
- Handoff documentation (PDF + architecture diagram)  
- Repository published on GitHub and ready for submission

---

## 🛠️ Tech Stack
- Platform: Salesforce CRM  
- Tools: Apex, Flows, LWC, Reports, Dashboards, Process Builder  
- Deployment: Change Sets, SFDX  
- Integration: REST API, Named Credentials, Platform Events  

---

## 📌 Outcomes
- Centralized ride & fleet management  
- Optimized driver & vehicle allocation  
- Automated invoicing & reporting  
- Real-time dashboards for management decisions  
- Enhanced customer experience and fleet sustainability