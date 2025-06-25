Data Flow Diagram (DFD)
The Data Flow Diagram (DFD) provides a visual representation of how data moves through the backend of the Airbnb Clone system. It highlights the interactions between external entities, core system processes, and internal data stores — offering a clear overview of how backend operations are structured and connected.

📌 Key Elements in the Diagram
External Entities:
The diagram includes three key user types:

Guest – interacts with features like booking, payments, and notifications.

Host – manages property listings and receives booking payouts.

Admin – oversees system-wide operations such as user and payment monitoring.

Core Processes:
These represent the major backend modules and functionalities:

User Management – handles registration, authentication, and profile updates.

Property Listings – allows hosts to create and manage property data.

Booking Management – manages reservation requests, availability, and status tracking.

Payments Processing – supports secure guest payments and host payouts.

Notifications System – dispatches booking confirmations, alerts, and system updates.

Data Stores:
Each process connects to a dedicated database component where persistent information is stored:

User Database, Property Database, Booking Database, Payments Database, and Notification Log.

🧭 Purpose of the Diagram
This DFD serves as a blueprint for backend design by:
Demonstrating how data flows between users and backend processes.
Clarifying which system modules are responsible for which operations.
Supporting planning for database schema design, API development, and role-based access control.