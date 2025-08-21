Java Data Base Connectivity
https://www.youtube.com/playlist?list=PLsyeobzWxl7rU7Jz3zDRpqB-EODzBbHOI

**THEORY**
7 steps to connect the DB:
1. Import the package - java.sql.*
2. Load and Register the driver - different drivers for different Databases
	1. Load - driver for MySQL - `com.mysql.jdbc.driver` - also requires a .jar file
	2. Register - use the method: `forName("com.mysql.jdbc.driver")`
3. Establish the connection - Instantiate the Interface Connection
4. Create the statement - Normal Statement, Prepared Statement, Callable Statement
5. Execute the Query
6. Process the result
7. Close


![[Screenshot (1).png]]

