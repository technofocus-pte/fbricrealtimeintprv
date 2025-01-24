# **Use case 01- Performing Real-Time Intelligence using Microsoft Fabric**

**Introduction**

Microsoft Fabric Real-Time Analytics is a fully managed,
high-performance, big data analytics platform that makes it easy to
analyze high volumes of data in near real time. The Microsoft Fabric
Real-Time Analytics toolbox gives you an end-to-end solution for data
ingestion, query, visualization, and management.

By analyzing structured, semi-structured, and unstructured data across
time series, and by using Machine Learning, Microsoft Fabric Real-Time
Analytics makes it simple to extract key insights, spot patterns and
trends, and create forecasting models. Microsoft Fabric Real-Time
Analytics is scalable, secure, robust, and enterprise-ready, and is
useful for log analytics, time series analytics, IoT, and
general-purpose exploratory analytics.

**Objective**

- Create **KQL database** in your Fabric enabled Power BI workspace

- Run powerful KQL queries to explore the data via **KQL Queryset**

- Manage KQL Database using control commands and policies

- Visualize data in Fabric **Real Time Dashboards** 

# **Exercise 1: Database Creation, Data Ingestion and Exploration**

This exercise will focus on enabling the participants to Create a KQL
database, and ingest data into the KQL database table - One click
ingestion of historic data , update policy to perform ETL and write some
KQL queries.

## **Task 0: Sync Host environment time**

1.  In your VM, navigate and click in the **Search bar**, type
    **Settings** and then click on **Settings** under **Best match**.

      ![](./media/image1.png)

2.  On Settings window, navigate and click on **Time & language**.

      ![](./media/image2.png)

3.  On **Time & language** page, navigate and click on **Date & time**.

     ![](./media/image3.png)

4.  Scroll down and navigate to **Additional settings** section, then
    click on **Syn now** button. It will take 3-5 minutes to syn.

     ![](./media/image4.png)

5.  Close the **Settings** window.

      ![](./media/image5.png)

## Task 1: Sign in to Power BI account and sign up for the free 

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL: +++https://app.fabric.microsoft.com/+++ then
    press the **Enter** button.

      ![](./media/image6.png)

2.  In the **Microsoft Fabric** window, enter your given credentials,
    and click on the **Submit** button.

     ![](./media/image7.png)

3.  Then, In the **Microsoft** window enter the password and click on
    the **Sign in** button . 

      ![](./media/image8.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

     ![](./media/image9.png)

5.  You’ll be directed to Power BI Home page.

      ![](./media/image10.png)

## Task 2: Start the Microsoft Fabric trial

Follow these steps to start your Fabric trial.

1.  On **Power BI Home** page, click on the **Account manager** on the
    right side. In the Account manager blade, navigate and
    select **Start trial as shown in the below image.**

      ![](./media/image11.png)

2.  If prompted, agree to the terms and then select **Activate**.

      ![](./media/image12.png)

3.  Once your trial capacity is ready, you receive a confirmation
    message. Select **Fabric Home Page** to begin working in Fabric.

     ![](./media/image13.png)

4.  Open your Account manager again. Notice that you now have a heading
    for **Trial status**. Your Account manager keeps track of the number
    of days remaining in your trial. You will also see the countdown in
    your Fabric menu bar when you work in a product experience.

     ![](./media/image14.png)

## Task 3: Create a workspace 

Before working with data in Fabric, create a workspace with the Fabric
trial enabled.

1.  In the **Microsoft Fabric** home page, select the **Power BI**
    template.

     ![](./media/image15.png)

2.  In the **Power BI Home** page menu bar on the left,
    select **Workspaces** (the icon looks similar to 🗇).

     ![](./media/image16.png)

3.  In the Workspaces pane, select **+New workspace**.

     ![](./media/image17.png)

4.  In the **Create a workspace tab**, enter the following details and
    click on the **Apply** button.

      |   |   |
      |---|----|
      |Name|+++Fabric Real-Time AnalyticsXX+++(XX can be a unique number) |
      |Advanced|	Under License mode, select Trial|
      |Default| storage format	Small dataset storage format|

     ![](./media/image18.png)

     ![](./media/image19.png)

     ![](./media/image20.png)

5.  Wait for the deployment to complete. It takes 2-3 minutes to
    complete. When your new workspace opens, it should be empty.

    ![](./media/image21.png)

## **Task 4:** [**Create a KQL Database**](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab1.md#challenge-1-create-a-kql-database)

Kusto query language (KQL) is used to query static or streaming data in
a table that is defined in a KQL database. To analyze the sales data,
you must create a table in a KQL database and ingest the data from the
file.

1.  At the bottom left of the Power BI portal, select the **Power
    BI** icon and switch to the **Real-Time Intelligence** experience.

     ![](./media/image22.png)
 
     ![](./media/image23.png)

2.  In the **New Eventhouse** dialog box, enter the **Eventhouse name**
    as +++FabricRTA+++ (or new database with a name of your choice)
    and click on **Create** button.

   **Note**: Remove any extra space before and after **FabricRTA.**
    ![](./media/image24.png)
    ![](./media/image25.png)

## **Task 5: Create a KQL queryset**

The KQL Queryset exists within the context of a workspace. A new KQL
queryset is always associated with the workspace you're using when you
create it.

1.  Select ***Fabric Real-Time AnalyticsXX*** workspace in the left
    navigation pane.

      ![](./media/image26.png)

2.  On the **Synapse Real-Time Analytics Home** page, from the menu bar,
    select the  +**New item**, and then select **KQL Queryset**

      ![](./media/image27.png)

3.  In the **New KQL Queryset** dialog box, enter the **KQL Query name**
    as **+++querysetXX+++**(or new database with a name of your choice)
    and click on **Create** button.

      Note: KQL Query name should be alphanumeric characters, underscores,
      periods, and hyphens. Special characters aren't supported.

      ![](./media/image28.png)

4.  In **OneLake data hub** pane ,select **FabricRTA** KQL Database and
    click on **Select** button.

     ![](./media/image29.png)

    ![](./media/image30.png)
5.  Now you can write a simple KQL query:
   
     +++print "Hello World"+++

      ![](./media/image31.png)

6.  Highlight the line with the code and hit the **Run** button. The
    query will be executed and its result can be seen in the result grid
    at the bottom of the page.

      ![](./media/image32.png)

# **Exercise 2: Ingest data from Azure Storage Account**

Data ingestion to KQL Database is the process used to load data records
from one or more sources into a table. Once ingested, the data becomes
available for query.

KQL Database supports several ingestion methods, including Eventstream,
Fabric Pipeline, and Fabric Dataflow. Also available with Azure Data
Factory and Event Hubs.

## **Task 1: Create the raw table - logsRaw**

Ingest data using one-click ingestion from Azure Blob Storage to your
KQL Database.

1.  In KQL queryset pane, replace all the code in the **cell** with the
    following code and click on **▷ Run** button to create a table
      ```
      .create table logsRaw(
          Timestamp:datetime, 
          Source:string, 
          Node:string, 
          Level:string, 
          Component:string, 
          ClientRequestId:string, 
          Message:string, 
          Properties:dynamic
      )
      ```
      
      ![](./media/image33.png)

2.  Click on refresh to see the new table on the left.

      ![](./media/image34.png)

      ![](./media/image35.png)

## **Task 2: Use the “One-click” User Interface to ingest data from Azure blob storage**

You need to analyze the system logs for Contoso, which are stored in
Azure blob storage.

1.  Select **FabricRTA** d*atabase* in the left navigation pane.

     ![](./media/image36.png)

     ![](./media/image37.png)

2.  In **FabricRTA** database, under the **Home** tab, navigate and
    click on **Get data** in the command bar, then select **Azure
    Storage**.

     ![](./media/image38.png)

3.  Then use the wizard to import the data into a new table by selecting
    the following options:

4.  In the **Get data** tab, select the existing table as **logsRaw**.
    Under the Configure the data source tab enter the **URI :**
    +++https://adxsamplefiles.blob.core.windows.net/publiccsvsamples/logsbenchmark-onegb/2014+++    
      ![](./media/image39.png)

5.  In the **Get data** tab, click on the **+** and click on **Next**
    button.

    ![](./media/image40.png)

6.  In Get data tab under the Inspect the data click on the horizontal
    **ellipses (…)** beside Edit columns, select the **Advanced** and
    check the **Keep table schema.** Click on the **Finish** button.

    ![](./media/image41.png)

7.  Wait for the Data ingestion to be completed, and click **Close**.

      ![](./media/image42.png)

       ![](./media/image43.png)

8.  Select **querysetXX** KQL queryset in the left navigation pane.

      ![](./media/image44.png)

9.  Replace all the code in the **cell** with the following code and
    click on **▷ Run** button
      ```
        logsRaw
        | count
      ```
      
      ![](./media/image45.png)

The logsRaw table should have 3,834,012 records.

# **Exercise 3: Starting with the basics of KQL**

A *Kusto query* is a read-only request to process data and return
results. The request is stated in plain text that's easy to read,
author, and automate. A Kusto query has one or more query statements and
returns data in a tabular or graph format.

## **Task 1: Journey from SQL to KQL!**

1.  For all the SQL pros out there, KQL Database allows a subset of TSQL
    queries. Try running the following SQL query in web UI. Replace all
    the code in the **cell** with the following code and click on **▷Run** button.

      **Copy**
      ```
      SELECT COUNT() FROM logsRaw
      ```
      ![](./media/image46.png)

2.  The primary language to interact with Kusto is KQL (Kusto Query
    Language). To make the transition and learning experience easier,
    you can use the explain operator to translate SQL queries to KQL.

3.  Replace all the code in the **cell** with the following code and
    click on **▷ Run** button.

   **Copy**
   ```
   explain SELECT MAX(Timestamp) AS MaxTimestamp FROM logsRaw WHERE Level='Error'
   ```
   ![](./media/image47.png)

   Output of the above query will be a corresponding KQL query
   
   logsRaw
   
   | where (Level == "Error")
   
   | summarize MaxTimestamp=max(Timestamp)
   
   | project MaxTimestamp

## **Task 2: Basic KQL queries - explore the data**

In this task, you will see some KQL examples. For this task, we will use
the table logsRaw, which has data we loaded in previous challenge from
storage account.

1.  Execute the queries and view the results. KQL queries can be used to
    filter data and return specific information. Now, you'll learn how
    to choose specific rows of data. The **where** operator filters
    results that satisfy a certain condition.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run** button.

      **Copy**
    ```
       logsRaw
      | where Level=="Error"
      | take 10
    ```
   ![](./media/image48.png)

The take operator samples any number of records from our table without
any order. In the above example, we asked to provide 10 random records.

3.  Find out how many records are in the table. Replace all the code in
    the **cell** with the following code and click on **▷ Run** button.

      **Copy**
      ```
      logsRaw
      | summarize count() // or: count
      ```

      ![](./media/image49.png)

4.  Find out the minimum and maximum Timestamp. Replace all the code in
    the **cell** with the following code and click on **▷ Run** button.

      **Copy**
      ```
      logsRaw
      | summarize min(Timestamp), max(Timestamp)
      ```
      ![](./media/image50.png)

5.  Our dataset has trace records written by Contoso's DOWNLOADER
    program, which downloads files from blob storage as part of its
    business operations. Replace all the code in the **cell** with the
    following code and click on **▷ Run** button.

      **Copy**
      ```
      logsRaw
      | where Component == "DOWNLOADER"
      | take 10
      ```
      
      ![](./media/image51.png)

6.  Select the **Properties** column is dynamic. The dynamic data type
    is special in that it can take on any value of other data types, as
    well as arrays and property bags (dictionaries).

      ![](./media/image52.png)

7.  The dynamic type is extremely beneficial when it comes to storing
    JSON data, since KQL makes it simple to access fields in JSON and
    treat them like an independent column: just use either the dot
    notation (dict.key) or the bracket notation (dict\["key"\]).

8.  The extend operator adds a new calculated column to the result set,
    during query time. This allows for the creation of new standalone
    columns to the result set, from the JSON data in dynamic columns.
    Replace all the code in the **cell** with the following code and
    click on **▷ Run** button.

      **Copy**
      ```
      logsRaw
      | where Component == "DOWNLOADER"
      | take 100
      | extend originalSize=Properties.OriginalSize, compressedSize=Properties.compressedSize
      ```
      ![](./media/image53.png)

## [Task 3: Explore the table and columns](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab1.md#challenge-3-task-2-explore-the-table-and-columns-)

After subscripting a dynamic object, it is necessary to cast (convert)
the value to a simple type in order to utilize them (for example, if you
want to summarize the sizes of all the OriginalSize, you should convert
the dynamic type to a numeric type, like long).

1.  This below query to get the table that is shown in the image below
    (we want to convert the OriginalSize and CompressedSize columns to
    long)

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | where Component == "DOWNLOADER"
      | take 100
      | extend originalSize=tolong(Properties.OriginalSize), compressedSize=tolong(Properties.compressedSize), toguid(ClientRequestId)
      | getschema
      ```
      ![](./media/image54.png)

## **Task 4: Keep the columns of your interest**

You are investigating an incident and wish to review only several
columns of the dataset.

1.  A query to get only specific desired columns: Timestamp,
    ClientRequestId, Level, Message. Take arbitrary 10 records.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | project Timestamp, ClientRequestId, Level, Message
      | take 10
      ```
      
      ![](./media/image55.png)

## **Task 5: Filter the output**

You are investigating an incident that occurred within a specific time
frame.

1.  Write a query to get only specific desired
    columns: Timestamp, ClientRequestId, Level, Message. Take all the
    records between 2014-03-08 01:00 and 2014-03-08 10:00.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | project Timestamp, ClientRequestId, Level
      | where Timestamp >= datetime(2014-03-08 01:00) and Timestamp <= datetime(2014-03-08 10:00)
      | count
      ```
    ![](./media/image56.png)

## **Task 6: Sorting the results**

Your system generated an alert indicating a significant decrease in
incoming data. You want to check the traces of the "INGESTOR_EXECUTER"
\[sic\] component of the program.

1.  Write a query that returns 20 sample records in which
    the Component column equals the word "INGESTOR_EXECUTER" \[sic\].

2.  Once done, rewrite the query to take the top 1 records by the value
    of rowCount (for the "INGESTOR_EXECUTER" \[sic\] records).

3.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | where Component == 'INGESTOR_EXECUTER'
      | extend rowCount=toint(Properties.rowCount)
      | where isnotempty(rowCount)
      | sort by rowCount
      | top 10 by rowCount desc
      ```
      ![](./media/image57.png)

##  **Task 7: Data profiling**

1.  As part of the incident investigation, you want to
    extract format and rowCount from INGESTOR_EXECUTER \[sic\]
    component. Rename the calculated fields to fileFormat and rowCount
    respectively. Also, Make Sure Timestamp, fileFormat and rowCount are
    the first 3 columns.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | where Component == 'INGESTOR_EXECUTER'
      | extend rowCount=toint(Properties.rowCount), fileFormat=tostring(Properties.format) 
      | project Timestamp, fileFormat, rowCount, ClientRequestId, Component, Level, Message
      | take 10
      ```
      ![](./media/image58.png)

## **Task 8: Total number of records** 

The system comprises of several "components", but you don't know their
names or how many records were generated by each.

1.  Write a query to find out how many records were generated by each
    component. Use the Component column.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

       **Copy**
      ```
      logsRaw
      | summarize count() by Component
      ```
      ![](./media/image59.png)

## [**Task 9: Aggregations and string operations **](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab1.md#challenge-3-task-8-aggregations-and-string-operations-)

You assume that the incident being investigated has a connection to the
ingestion process run by Contoso's program.

1.  Write a query to find out how many records contain the
    string **ingestion** in the Message column. Aggregate the results
    by **Level**

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | where Message has "ingestion"
      | summarize count() by Level
      ```
      
      ![](./media/image60.png)

## **Task 10: Render a chart ** 

1.  Write a query to find out how many total records are present
    per Level (aggregated by Level) and render a piechart.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | where Component =='INGESTOR_EXECUTER'
      | project Timestamp, Properties.size, fileFormat=tostring(Properties.format), rowCount=Properties.rowCount
      | summarize count() by fileFormat
      | render piechart 
      ```
      ![](./media/image61.png)

##  **Task 11: Create bins and visualize time series ** 
1.  Write a query to show a timechart of the number of records in 30
    minute bins (buckets). Each point on the timechart represent the
    number of logs in that bucket.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | summarize count() by bin(Timestamp, 30m)
      | render timechart
      ```
      ![](./media/image62.png)

#  **Exercise 4: Explore and Transform Data** 

In this exercise we will explore 3 capabilities of Data Explorer

- **User-defined functions** are reusable KQL subqueries that can be
  defined as part of the query itself (ad-hoc functions), or persisted
  as part of the database metadata (stored functions - reusable KQL
  query, with the given name). Stored functions are invoked through a
  name, are provided with zero or more input arguments (which can be
  scalar or tabular), and produce a single value (which can be scalar or
  tabular) based on the function body.

- **Update Policy** is like an internal ETL. It can help you manipulate
  or enrich the data as it gets ingested into the source table (e.g.
  extracting JSON into separate columns, creating a new calculated
  column, joining the newly ingested records with a static dimension
  table that is already in your database, etc). For these cases, using
  an update policy is a very common and powerful practice.

> Each time records get ingested into the source table, the update
> policy's query (which we'll define in the update policy) will run on
> them (**only on newly ingested records** - other existing records in
> the source table aren’t visible to the update policy when it runs),
> and the results of the query will be appended to the target table.
> This function's output schema and target table schema should exactly
> match.

##  **Task 1: User defined Function (Stored Functions)** 

1.  Create a stored functions, named ManiputatelogsRaw, that will
    contain the code below. Make sure the function works.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      .create function ManiputatelogsRaw() {
      logsRaw
      | where Component in (
        'INGESTOR_EXECUTER', 
        'INGESTOR_GATEWAY', 
        'INTEGRATIONDATABASE',
        'INTEGRATIONSERVICEFLOWS', 
        'INTEGRATIONSERVICETRACE', 
        'DOWNLOADER')
      }
      ```
      ![](./media/image63.png)

## [**Task 2: Create an update policy**](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab1.md#challenge-4-task-2-create-an-update-policy-)

In this task, we will use an update policy to filter the raw data in
the logsRaw table (the source table) for ingestion logs, that will be
ingested into the new table ingestionLogs that we’ll create.

1.  Build the target table,replace all the code in the **cell** with the
    following code and click on **▷ Run cell** button and review the
    output.

      **Copy**
      ```
      .create table ingestionLogs (
        Timestamp: datetime, 
        Source: string,
        Node: string, 
        Level: string, 
        Component: string, 
        ClientRequestId: string, 
        Message: string, 
      Properties: dynamic)
      ```
      ![](./media/image64.png)

2.  Create a function for the update policy, replace all the code in the
    **cell** with the following code and click on **▷ Run cell** button
    and review the output.

      **Copy**
      ```
      .alter table ingestionLogs policy update @'[{ "IsEnabled": true, "Source": "logsRaw", "Query": "ManiputatelogsRaw()", "IsTransactional": true, "PropagateIngestionProperties": false}]'
      ```
      ![](./media/image65.png)

3.  Update policy can transform and move the data from source table from
    the time it is created. It cannot look back at already existing data
    in source table. We will ingest new data into logsraw table and see
    new data flowing into ingestionLogs table

4.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

5.  copy **operationIds** and paste them in a notepad , and then
    **Save** the notepad to use the information in the upcoming step.

      **Copy**
      ```
      // Note, the following .ingest commands set creationTime to 2014 as you may notice in the file path.
      // This param allows to backfill the table with historical data and index it according ot the creationTime setting.
      
      .execute database script <|
      .ingest async into table logsRaw (h'https://adxsamplefiles.blob.core.windows.net/publiccsvsamples/logsbenchmark-onegb/2014/03/08/00/data.csv.gz') with (format='csv', creationTime='2024-03-08T00:00:00Z');
      .ingest async into table logsRaw (h'https://adxsamplefiles.blob.core.windows.net/publiccsvsamples/logsbenchmark-onegb/2014/03/08/01/data.csv.gz') with (format='csv', creationTime='2024-03-08T01:00:00Z');
      .ingest async into table logsRaw (h'https://adxsamplefiles.blob.core.windows.net/publiccsvsamples/logsbenchmark-onegb/2014/03/08/02/data.csv.gz') with (format='csv', creationTime='2024-03-08T02:00:00Z');
      .ingest async into table logsRaw (h'https://adxsamplefiles.blob.core.windows.net/publiccsvsamples/logsbenchmark-onegb/2014/03/08/03/data.csv.gz') with (format='csv', creationTime='2024-03-08T03:00:00Z');
      .ingest async into table logsRaw (h'https://adxsamplefiles.blob.core.windows.net/publiccsvsamples/logsbenchmark-onegb/2014/03/08/04/data.csv.gz') with (format='csv', creationTime='2024-03-08T04:00:00Z');
      ```
      
      ![](./media/image66.png)

      **Note:** The above command does not complete immediately. Because we
      used the async parameter, the output of the above query will
      be operationIds. The progress of the query can be checked by used the
      below command

6.  Check progress of the commands, replace all the code in the **cell**
    with the following code and click on **▷ Run cell** button and
    review the output.

      Copy
      ```
        .show operations 
      | where OperationId == ' OperationId '
      ```
      **Note:** Replace the operationIds which you have saved in Step 6

      ![](./media/image67.png)

7.  Make sure the data is transformed correctly in the destination
    table. Replace all the code in the **cell** with the following code
    and click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      ingestionLogs
      | count
      ```
      ![](./media/image68.png)

      **Note:** If the count is not matching for ingestionLogs table, it means
      that one of the above .ingest commands have throttled or failed.

#  [**Exercise 5: Advanced KQL, Policies, and Visualization**](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab2.md#lab-2-advanced-kql-policies-and-visualization)

#  [Caching and Retention Policies](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab2.md#challenge-5-how-long-will-my-data-be-kept---caching-and-retention-policies)

Among the different policies you can set to the KQL Database, two
policies are of particular importance:

- Retention policy (retention period)

- Cache policy (cache period)

First, a policy is used to enforce and control the properties of the KQL
Database.

- The **retention** policy: the time span, in days, for which it’s
  guaranteed that the data is kept available for querying. The time span
  is measured from the time that the records are ingested. When the
  period expires, the records will not be available for querying any
  more.

> In other words, the retention policy defines the period during which
> data is retained and available to query, measured since ingestion
> time. Note that a large retention period may impact the cost.

- The **cache** policy: the time span, in days, for which to keep
  recently ingested data (which is usually the frequently queried data)
  available in the hot cache rather than in long term storage (this is
  also known as cold tier. Specifically, it is Azure blob storage). Data
  stored in the hot cache is actually stored in local SSD or the RAM of
  the machine, very close to the compute nodes.

> Therefore, more readily available for querying. The availability of
> data in the hot cache improves query performance but can potentially
> increase the cluster cost (as more data is being stored, more VMs are
> required to store it). In other words, the caching policy defines the
> period during which data is kept in the hot cache.
>
> All the data is always persisted in the cold tier, for the duration
> defined in the retention policy. Any data whose age falls within the
> hot cache policy will also be stored in the hot cache. If you query
> data from cold cache, it’s recommended to target a small specific
> range in time (“point in time”) for the queries to be efficient.

## [**Task 1: Change the retention policy via commands **](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab2.md#challenge-5-task-1-change-the-retention-policy-via-commands-)

Database policies can be overridden per table using a KQL control
command. A database cache and retention policies can be edited from the
Fabric UI. Tables policies can be managed via a KQL command.

1.  Select  **querysetXX**  KQL queryset in the left navigation pane.

      ![](./media/image69.png)

2.  Always use KQL commands to alter the policies of the entire
    Database/tables. Table level policy takes precedence over database
    level which takes precedence over cluster level.

3.  Run the below query to find the total hours is the retention policy
    of **ingestionLogs** table

4.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output

      Copy
  >  
    .alter table ingestionLogs policy retention 
      ```
      { 
          "SoftDeletePeriod": "10:12:00:00",
          "Recoverability": "Enabled"
      }
      ```
>     ![](./media/image70.png)

5.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output
      ```
      .alter-merge table ingestionLogs policy retention softdelete = 30d
      ```
      ![](./media/image71.png)

# [Exercise 6: Metadata objects handling using Control Commands](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab2.md#challenge-6-metadata-objects-handling-using-control-commands)

## **Task 1: .show/diagnostic logs/Insights**

Control commands are requests to the service to retrieve information
that is not necessarily data in the database tables, or to modify the
service state, etc. In addition, they can be used to manage Azure Data
Explorer. The first character of the KQL text determines if the request
is a control command or a query. Control commands must start with the
dot (.) character, and no query may start with that character.

- The .show queries command returns a list of queries that have reached
  a final state, and that the user invoking the command has access to
  see.

- The .show commands command returns a table of the admin commands that
  have reached a final state. The TotalCpu column is the value of the
  total CPU clock time (User mode + Kernel mode) consumed by this
  command.

- The .show journal command returns a table that contains information
  about metadata operations that are done on the Azure Data Explorer
  database. The metadata operations can result from a control command
  that a user executed, or internal control commands that the system
  executed, such as drop extents by retention

- The .show tables details command returns a set that contains the
  specified table or all tables in the database with a detailed summary
  of each table's properties.

1.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output

      **Copy**
      ```
      // 1. Using pipe: Count how many tables are in the database-in-scope:
      .show tables
      | count
      
      // 2. Using semicolon: Count how many tables are in the database-in-scope:
      .show tables;
      $command_results
      | count
      
      // 3. Using semicolon, and including a let statement:
      .show tables;
      let useless=(n:string){strcat(n,'-','useless')};
      $command_results | extend LastColumn=useless(TableName)
      ```
      ![](./media/image72.png)

## **Task 2: Use .show queries**

As part of an incident investigation, you need to find out how many
queries were executed in the past 3 hours.

1.  To count the number of queries that were run, in the past 3 hours
    execute the below query

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output

      **Copy**
      ```
      .show queries 
      | where StartedOn >ago(7d)
      | summarize count() by User
      ```
      
      ![](./media/image73.png)

## **Task 3: Use .journal commands**

1.  To show the details of the function that you created earlier,
    replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output

      **Copy**
      ```
      .show journal
      | where EventTimestamp > ago(1h) and Event =='ADD-FUNCTION'
      | project Event, EventTimestamp, ChangeCommand
      ```
      ![](./media/image74.png)

## **Task 4: Use .show commands**

1.  To show the details of commands that you ran, in the past 4 hours,
    replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      .show commands
      | where StartedOn >ago(4h)
      | summarize count() by User
      ```
      ![](./media/image75.png)

## **Task 5: Table details and size**

1.  Use control command to show details on **ingestionLogs** tables in
    the database.

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output

      Copy
      ```
      .show extents
      | summarize format_bytes(sum(OriginalSize),2,'MB'), format_bytes(sum(ExtentSize),2,'MB') by TableName
      
      .show tables details
      ```
      
      ![](./media/image76.png)

# [Exercise 7: Going more advanced with KQL](https://github.com/microsoft/FabricRTA-in-a-Day/blob/main/Lab2.md#challenge-7-going-more-advanced-with-kql)

## **Task 1: Declaring variables and using 'let' statements**

You can use the let statement to set a variable name equal to an
expression or a function, or to create views (virtual, temporary, tables
based on the result-set of another KQL query).

let statements are useful for:

- Breaking up a complex expression into multiple parts, each represented
  by a variable.

- Defining constants outside of the query body for readability.

- Defining a variable once and using it multiple times within a query.

1.  Use 2 let statements to
    create **LogType** and **TimeBucket **variables with the following
    values:

      - LogType = 'Warning'
      
      - TimeBucket = 1m

2.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      let LogType = 'Warning';
      let TimeBucket = 1m;
      logsRaw
      | summarize count() by Level = LogType, bin(Timestamp,TimeBucket)
      | render timechart
      ```
      ![](./media/image77.png)

## **Task 2: Use the search operator**

You received an alert early in the morning regarding multiple Timeouts
in your system. You want to quickly search the traces without using
specific columns or table names.

1.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      Copy
      ```
      search  "Exception=System.Timeout" | count
      ```
      ![](./media/image78.png)

## **Task 3: Parse Key-Value pairs strings into separate columns**

As part of an incident investigation, you need to look at
the **INGESTOR_GATEWAY** records (Component == 'INGESTOR_GATEWAY').You
need to use the *Message* column, which contains the message of the
trace, representing the information in a key/value form.

1.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      Copy
      ```
      logsRaw 
      | where Component == "INGESTOR_EXECUTER" 
      //| parse-kv Properties as (size: int, format: string, rowCount: int, cpuTime: string , duration: string) //bug: cpuTime, duration truncated
      | take 20
      | evaluate bag_unpack(Properties)
      
      ingestionLogs 
      | where Component == "INGESTOR_EXECUTER" 
      | take 20 
      | parse-kv Message as (IngestionCompletionEvent:string, path:string) with (pair_delimiter=' file', kv_delimiter=':')
      ```
      
      ![](./media/image79.png)

## **Task 4: Nulls are important in timeseries analysis (Compare summarize and make-series)**

In this task, calculate the average size of data ingested per 30 min by
the node 'Engine000000000378'. Use Component as 'INGESTOR_EXECUTER'.
File size is available in the 'Properties' column. Render it as a
timechart.

1.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      logsRaw
      | where Component=='INGESTOR_EXECUTER' and Node =='Engine000000000378'
      | extend size=tolong(Properties.size)
      | summarize avg(size) by bin(Timestamp, 1h), Node
      | render timechart 
      
      logsRaw
      | where Component=='INGESTOR_EXECUTER' and Node =='Engine000000000378'
      | extend size=tolong(Properties.size)
      | make-series avg(size) default=0 on Timestamp step 1h by Node
      | render timechart
      ```
      
      ![](./media/image80.png)

## **Task 5: Anomaly detection**

Anomaly detection lets you find outliers/anomalies in the data.

Let's find out any file size anomalies by summarizing the average of
file sizes in 1-minute intervals.

1.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      ingestionLogs
      | extend size=tolong(Properties.size)
      | make-series avg(size) default=0 on Timestamp step 10m
      | extend anom=series_decompose_anomalies(avg_size)
      | render anomalychart  with (anomalycolumns=anom)
      
      
      ingestionLogs
      | extend size=tolong(Properties.size)
      | make-series avg(size) default=0 on Timestamp step 10m
      | extend anom=series_decompose_anomalies(avg_size, 0.5)
      | mv-expand Timestamp, avg_size, anom
      | where anom <> 0
      ```
      ![](./media/image81.png)

2.  To get a tabular format of the detected anomalies, you can use
    the mv-expand operator to expand the multi-value dynamic array of
    the anomaly detection component (AnomalyFlags, AnomalyScore,
    PredictedUsage) into multiple match records, and then filter by
    positive and negative deviations from expected usage (where
    AnomalyFlags != 0).

3.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      ingestionLogs
      | where Component == "INGESTOR_EXECUTER"
      | extend fileSize=tolong(Properties.size)
      | make-series ActualSize=avg(fileSize) on Timestamp step 1min // Creates the time series, listed by data type
      | extend(AnomalyFlags, AnomalyScore, PredictedSize) = series_decompose_anomalies(ActualSize, -1) // Scores and extracts anomalies based on the output of make-series 
      | mv-expand ActualSize to typeof(double), Timestamp to typeof(datetime), AnomalyFlags to typeof(double),AnomalyScore to typeof(double), PredictedSize to typeof(long) // Expands the array created by series_decompose_anomalies()
      | where AnomalyFlags != 0  // Returns all positive and negative deviations from expected usage
      | project Timestamp,ActualSize = format_bytes(ActualSize, 2),PredictedSize = format_bytes(PredictedSize, 2), AnomalyScore, AnomalyFlags // Defines which columns to return 
      | sort by abs(AnomalyScore) desc // Sorts results by anomaly score in descending ordering
      ```
      ![](./media/image82.png)

# **Exercise 8: Visualization**

## **Task 1: Find the anomaly value**

1.  Create a Timechart using following query. Observe that we
    used \_startTime? and \_endTime. These 2 are parameters from
    TimeRange filter in ADX Dashboard with which we can filter the
    minimum and maximum time of our data.

2.  Use the below example query as reference to add Timestamp filter
    with \_startTime and \_endTime filter to queries in task 1 and task
    2.

3.  The following 2 tasks use the timefilter
    between 2014-03-08T00:00:00 and 2014-03-08T10:00:00

      ingestionLogs
      | where Timestamp between (todatetime(_startTime) .. todatetime(_endTime))
      | summarize count() by bin(Timestamp, 10m), Component


4.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      ingestionLogs
      | where Timestamp between (datetime(2014-03-08 01:00).. datetime(2014-03-08 10:00))
      | summarize count() by bin(Timestamp, 10m), Component
      ```
      
      ![](./media/image83.png)

5.  Parameterize (add Timefilter) and render an Anomaly chart using the
    following Anomaly detection query. The chart should show values
    between 2014-03-08T00:00:00 and 2014-03-08T10:00:00.

6.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.
      
      **Copy**
      ```
      ingestionLogs
      | where Timestamp between (datetime(2014-03-08 01:00).. datetime(2014-03-08 10:00))
      | summarize count() by bin(Timestamp, 10m), Component
      | render timechart
      ```
      
      ![](./media/image84.png)

7.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      let bucket=10m;
      logsRaw
      | where Timestamp between(datetime(2014-03-08 01:00).. datetime(2014-03-08 10:00))
      | make-series count() on Timestamp step bucket by Level
      | extend anom = series_decompose_anomalies(count_)
      | render anomalychart with (anomalycolumns=anom)
      ```
      ![](./media/image85.png)

## **Task 2: Find the warning percentage**

1.  Replace all the code in the **cell** with the following code and
    click on **▷ Run cell** button and review the output.

      **Copy**
      ```
      ingestionLogs
      | where Timestamp between(datetime(2014-03-08 01:00).. datetime(2014-03-08 10:00))
      | summarize count() by Level
      | render piechart
      ```
    ![](./media/image86.png)

**Summary**

This practical lab focuses designing, creating, and configuring KQL
database. Once the KQL database is created, this lab enlists the steps
to ingest data into KQL database and tables using One Click ingestion,
basic KQL queries, explore and transform the data. The lab also covered
Caching and Retention Policies, metadata objects handling using control
commands and Visualize data in Fabric Real Time Dashboards 
