# Steps to reproduce the issue

### Configure your local database 
(tested on mysql version 8.0.40-0ubuntu0.22.04.1)

### Change connexions values in the pom.xml if necessary
> url (localhost:3306)

> username (root)

> password

### Use the following command to create the DB "testdb" from changelog
> mvn liquibase:update -Dliquibase.url="jdbc:mariadb://localhost:3306/testdb?createDatabaseIfNotExist=true" -Dliquibase.defaultCatalogName="testdb"

### Generate diff
> mvn clean compile

> mvn liquibase:diff

### Error message with liquibase version 4.30.0:
liquibase.exception.CommandExecutionException: java.lang.NullPointerException: Cannot invoke "liquibase.datatype.LiquibaseDataType.getName()" because "liquibaseDataType" is null


Works with liquibase version 4.23.2. Fails starting version 4.24.0