# DataSources

Before we can build a reporting page, we first need to define and create a so called *DataSource* that will provide the data that our report(s) will render.

As mentioned in the introduction of this scenario, a DataSet in Process Automation Manager 7 can be based on various data providers, including Java Beans, CSV and SQL. In this example we will use a DataSet that uses the SQL provider.

For this scenario, we’ve prepared a database with task data and customer satisfaction data of our *Credit Card Dispute* use-case. The database is a pre-provisioned PostgreSQL database running in our OpenShift environment.

* Host: `postgresql.labs-infra.svc.cluster.local`
* Port: `5432`
* User: `postgres`
* Password: `postgres`
* Database:  `postgres`

In Business Central, you can use this information to create a new *DataSource* that we can later use in our *DataSet*.

Before we can create a new *DataSource*, we first need to install the correct driver for our database.

---
**NOTE**

Process Automation Manager 7 can come with pre-provisioned database-drivers for MariaDB, MySQL and PostgreSQL, depending on the configuration settings of the platform. If your version already comes with a pre-configured PostgreSQL driver, you can skip the steps of adding the driver.

---

1. Go to the “Settings” screen by clicking on the gear icon in the upper right corner:
![Business Central Settings]({% image_path business-central-settings.png %}){:width="600px"}
2. Click on the *Data Sources* tile.
![Business Central Datasource Settings]({% image_path business-central-settings-datasource.png %}){:width="600px"}
3. In the *Drivers* section, click on *+ Add Driver*.
4. In the *New driver* from, entering the following values and click on *Finish*:
    - Name: `PostgreSQL`  
    - Driver Class Name: `org.postgresql.Driver`  
    - Group Id: `org.postgresql`  
    - Artifact Id: `postgresql`  
    - Version: `9.4.1212.jre7`  

![Business Central New Driver]({% image_path business-central-settings-datasource-driver.png %}){:width="600px"}

Next, we can create the *DataSource* that connects to our PostgreSQL database.

1. In the *Data Sources* screen, click on *+ Add DataSource* on the left-hand side of the screen, which will open the *New data source form*.
2. Fill in the following values:
    - Name: `PAM-Workshop-Reporting`  
    - Connection URL: `jdbc:postgresql://postgresql.labs-infra.svc.cluster.local:5432/postgres`  
    - User: `postgres`  
    - Password: `postgres`  
    - Driver: `PostgreSQL`  
3. Click on `Test Connection` to test the setup and if the test is OK, click on `Finish`
![Business Central New Datasource]({% image_path business-central-settings-add-datasource.png %}){:width="600px"}

![Business Central Test New Datasource]({% image_path business-central-settings-add-datasource-test-connection.png %}){:width="600px"}

Now that we've created the DataSource, we can explore its content.

1. Click on the *PAM-Workshop-Reporting* DataSource that we've just created.
2. Click on the *Browse content* button at the top of the panel. This will open the *Schemas* of the datasource.
![RHPAM Enablement Dataset List]({% image_path business-central-navigate-datasource.png %}){:width="600px"}-
3. Click on thew *Open* button of the `public` schema.
![RHPAM Enablement Dataset Explore]({% image_path pam-enablement-dataset-explore.png %}){:width="600px"}
4. The `public` schema of our database contains two tables. One `task` table which contains the open and completed tasks of our credit-card dispute cases, and a `customer_satisfaction` table which contains information of the customer satisfaction related to our credit-card dispute cases.
5. Click on the *Open* button next to the `task` table and explore the table's content.
6. Go back to the *public* schema page and click on the *Open* button next to the `customer_satisfaction` table and explore the table's content.

Now that we've created a connection to our PostgreSQL *DataSource* we can define the *DataSets* that we will use to render our reports.
creating-datasets.mdcreating-datasets.md