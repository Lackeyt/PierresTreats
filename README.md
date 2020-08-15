<h1 align="center"><strong>Pierre's Sweet and Savory Treats</strong></h1>

<h4 align="center"><em>A store portal to track flavors and treats</em></h4>


##### __Created:__ 8/7/2020
##### __Last Updated:__ 8/7/2020 
##### By _**Tyson Lackey**_  


## Description

A SQL database stores treat and flavor detials as well as a join table to associate their many to many relationship. The program can allow a user to create, edit, delete, and view treat/flavor records. Joins can be added from either the treat or flavor view to records in the other, allowing the user to assign/remove flavors to treats and visa versa. Identity authorization is included to limit access to edit/create/and delete for records to only authorized users

## Setup/Installation Requirements

##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Open via Bash/GitBash:

1. Clone this repository onto your computer:
    "git clone https://github.com/Lackeyt/PierresTreats.Solution"
2. Navigate into the "PierresTreats.Solution" directory in Visual Studio Code or preferred text editor:
3. Open the project by typing "code ." while in the previous directory in your terminal.
4. Open your computer's terminal and navigate to the directory bearing the name of the program and containing the top level subdirectories and files.
5. Enter the command "dotnet build" in the terminal and press "Enter".
6. Enter the command "dotnet watch run" in the terminal and press "Enter".


##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Configue MySQL Workbench Database:
1. Launch MySQL Workbench
2. Select "Create a new SQL tab for executing queries"
![NewQuery](./PierresTreats/wwwroot/assets/images/readme/NewQuery.PNG)
3. Enter the following SQL into the query window and click "execute"

```
DROP DATABASE IF EXISTS tyson_lackey;
CREATE DATABASE tyson_lackey;
USE tyson_lackey;

CREATE TABLE `engineers` (
  `EngineerId` int NOT NULL AUTO_INCREMENT,
  `Name` longtext,
  PRIMARY KEY (`EngineerId`)
);

CREATE TABLE `machines` (
  `MachineId` int NOT NULL AUTO_INCREMENT,
  `Name` longtext,
  PRIMARY KEY (`MachineId`)
);

CREATE TABLE `treatflavor` (
  `TreatFlavorId` int NOT NULL AUTO_INCREMENT,
  `TreatId` int NOT NULL,
  `FlavorId` int NOT NULL,
  PRIMARY KEY (`TreatFlavorId`),
  KEY `IX_TreatFlavor_FlavorId` (`FlavorId`),
  KEY `IX_TreatFlavor_TreatId` (`TreatId`),
  CONSTRAINT `FK_TreatFlavor_Flavors_FlavorId` FOREIGN KEY (`FlavorId`) REFERENCES `flavors` (`FlavorId`) ON DELETE CASCADE,
  CONSTRAINT `FK_TreatFlavor_Treats_TreatId` FOREIGN KEY (`TreatId`) REFERENCES `treats` (`TreatId`) ON DELETE CASCADE
);
```

##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Configue MySQL Workbench Database using database import:
1. In the Administration window of SQL Workbench, select 'Data Import/Restore'
![DataImportRestore](./PierresTreats/wwwroot/assets/images/readme/DataImportRestore.PNG)
2. Select 'Import from self-contained file" from the data import window.
![ImportSelfContainedFile](./PierresTreats/wwwroot/assets/images/readme/ImportSelfContainedFile.PNG)
3. Navigate to the file path titled tyson_lackey.sql in the Solution file.
![ImportFilePath](./PierresTreats/wwwroot/assets/images/readme/ImportFilePath.PNG)
4. Under 'Default Schema to be Imported To', click the "new" button.
![SelectNew](./PierresTreats/wwwroot/assets/images/readme/SelectNew.PNG)
5. Name the schema 'tyson_lackey' and click "ok"
![NameSchema](./PierresTreats/wwwroot/assets/images/readme/NameSchema.PNG)
6. Click 'Start Import'
![StartImport](./PierresTreats/wwwroot/assets/images/readme/StartImport.PNG)
7. reopen the schemas tab, right click and select "refresh all".

## Known Bugs

* No Error handling for empty values in form (currently saves values as empty strings, which erases ActionLinks)
* Additional fields not added to Machine and Engineer classes (currently only Name)

## Support and contact details

* Discord: TysonL#4409
* Email: lackeyt90@gmail.com


## Technologies Used

* Visual Studio Code
* HTML
* CSS
* Bootstrap
* C#
* MVC
* MySQL Workbench
* Entity Framework
* .NET Core

### License

Copyright (c) 2020 **_Tyson Lackey_**

This software is licensed under the MIT license.