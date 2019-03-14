# SensorDataFirebase
SensorDataFirebase is a group of libraries that were created to help to send data from sensors to the Firebase RealTimeDatabase using some Arduino and one NodeMCU or Raspberry PI. The data sent to the Firebase is formated to help users to plot graph using the data.

Because the Raspberry and the NodeMCU work with 3.3V, sometimes can be difficult to use analog sensors (Raspberry problem) or sensors that send data with 5V (Raspberry and NodeMCU problem). The use of communication with some 5V Arduino solves this problem (the library do not work yet using only the Raspberry or NodeMCU).

The libraries allow the user to add as much sensor as (s)he wants. All the data colected about these sensors will be sent to the Firebase.
Be warned: because sometimes is slow to read data from the firebase using NodeMCU and Raspberry, the use of a lot of sensors can result in bugs.

## How the data is stored in Firebase?
First, is necessary to have created the "Real TimeDatabase" in your Firebase project. The data is stored only in this type of database.
In the database is created two folders: "Sensors" and "Time". In the first folder is created a subfolder for each sensor. In the second folder is stored data about the current time ("CurrentTime") and current date ("CurrentDate").

The data from sensors are organized in 5 ways in each subfolder: Today, Yesterday, Week, Month, Year.

### Today
In this folder is stored all the data collected today by that sensor. The data in this the folder "Today" is stored every 30 minutes. For each cycle a new variable will be created on the folder "Today" to store the average of all readings performed by that sensor (only data sent to the Arduino libray).

### Yesterday
Every 00h00 all data stored in Today is copied to the subfolder "Yesterday". (The data in "Today" is deleted after copied)

### Week
Every 00h00 a variable is created in the subfolder "Week". This variable stores the mean of all data in "Today".
The variable name can be: 
"1" to Monday | "2" to Tuesday | "3" to Wednesday | "4" to Thursday | "5" to Friday | "6" to Saturday | "7" to Sunday

### Month
Every 00h00 a variable is created in the subfolder "Month". This variable stores the mean of all data in "Today".
The variable name is the number of the day.

### Year
Every Monday 00h01 a variable is created in the subfolder "Year". This variable stores the mean of all data in "Week". The folder "Week" is deleted after this.

## Hardware to use the libraries
These library can work in two ways, the first one consists of using some Arduino and one NodeMCU, the second one consists of using some Arduino and one Raspberry.
In both systems the Arduino is connected to sensors and send the data to the other device. When the other device receive the bytes, it 

## Using Arduino and NodeMCU



Any doubt, error, or sugestion, please let me know.
