### UiPEngineLocalProcess ###
** Simple engine to pull and process a Transaction from an local data source**

This workblock contains code that will do the following:
1. Read a configuration file, by default located in Data\Config.xlsx and output as a dictionary named config

2. Calls ProcessLayer\InitAllApplications.xaml, where you should initialize apps

3. Read the collection of data

4. For each piece of data (if you have only one transaction pull 4.1 out of 4)

--4.1 Execute Process - retry if you run into a AppEx

----4.1.1 Calls ProcessLayer\ProcessTransaction.xaml, where you should input data into your opened applications

----4.1.2 Evaluate Process wb output

----4.1.3 Recover if wb failed with AppEx

------4.1.3.1 Call ProcessLayer\CloseAllApplications.xaml

------4.1.3.2 Call ProcessLayer\InitAllApplications.xaml

5. Call ProcessLayer\CloseAllApplications.xaml

### Dependencies ###
* UiPath.Core.Activities
* UiPath.Credentials.Activities
* UiPath.Excel.Activities
* UiPath.Mail.Activities
* UiPath.WebAPI.Activities

### For New Project ###
To begin implementing take the following steps:

1. Check out the *Data\Config.xlsx* file and add/customize any required fields and values.

2. Decide what the process is going to achieve. Think about what kind of data is moving around in the process. Think about whether or not it is a cyclical process or executes just once.

3. Go in Main.xaml and change the following data types to suit your project needs:
TransactionData - by default a Datatable represents the collection of transaction data to be used in this process run
TransactionItem - it is a piece of the collection stored in TransactionData. In the above example, a DataRow.
Do not worry about errors so far.

4. Open *ProcessLayer\ProcessTransaction.xaml* and change io_TransactionItem's datatype to match the one you set up in the Main.xaml file.

5. Open Main.xaml and update the interface to **PROCESS TRANSACTION** states by clicking the import button. The errors from point 1. should now disappear.

6. Begin writing business code in the workflows located in the *ProcessLayer* folder

*ProcessLayer\InitAllApplications.xaml* - write business code to open all applications needed during processing.

*ProcessLayer\CloseAllApplications.xaml* - write business code to close all applications you have opened at previous step.

*ProcessLayer\ProcessTransaction.xaml* - write business code to use applications that are open and data from io_TransactionItem and complete the transaction. At the end of the transaction, take the applications to the page they were at when you began the transaction.

7. Execute and have fun!
