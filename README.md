# Monthly Expenses Database
This repository contains the Liquibase scripts for versioning and managing the database schema changes for the Monthly Expenses application.

### Installation and Usage
1.  Clone the repository:
```bash
git clone git@github.com:yourusername/liquidbase-db.git
```
2.  Install Liquibase (if not already installed).
3.  To start the database, execute the following Gradle command:
```bash
sudo -E ./gradlew startDockerCompose
```
4.  Run Liquibase with the following command to apply all changes in the **changelogs-index.json** file:

```bash
liquibase --logLevel=info --changeLogFile=./src/main/resources/db/monthlyExpensesDb/changelogs-index.json update
```
This will apply all the database changes defined in the **changelogs-index.json** file

5.  To stop the database, execute the following Gradle command:
```bash
sudo -E ./gradlew stopDockerCompose
```

### Project Structure
The Liquibase changelogs are organized into separate directories for each type of database change, with each directory containing the appropriate **changelogs-sprint-index.json** file that lists the order in which the changes should be applied. The directories for each type of change (tables, stored procedures, index, views) are located under the **resources/db/monthlyExpensesDb/[type_of_change]/changelogs/** directory.

For example, if you have a new table to add to the database, you would create a new directory under tables called "tables/changelogs/SPx" where "SPx" represents the sprint. Then, you would create a changelog file called something like "date-createTable_name.json" inside that directory. Finally, you would create the **changelogs-sprint-index.json** file to include the new changelog (Note that this file could contain more than one change).

The **changelogs-index.json** file is located at **resources/db/monthlyExpensesDb/changelogs-index.json** and includes all of the **changelogs-sprint-index.json** files in the correct order.
To apply all the changes, use the following command:
```bash
liquibase --logLevel=info --changeLogFile=./src/main/resources/db/monthlyExpensesDb/changelogs-index.json update
```
