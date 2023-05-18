# User-Management-Module-In-Mendix
This module covers CRUD operation on User Entity with default password settings, Importing the data from external excel sheet, Exporting/Downloading the user data to excel sheet. Also creating login functionality and rights as per assigned roles (user/admin) .

# Prerequisites 

1. Mendix Studio Pro 9.12.4. 

Create domain models (see Creating a Basic Data Layer) 

Create overview and detail pages (see How to Create Your First Two Overview and Detail Pages) 

 MxReflection 

 Excel Importer from MarketPlace 

Excel Exporter from MarketPlace 

 


# User CRUD Operation 

On the User_Overview Page Admin Can Perform CRUD operation on the User Entity which is associated with administration.account activity where the default password is saved if the password is not set by the Admin. All the users are displayed using data grid in User_Overview page. 

# Implementation. 

1.Create a Persistable entity named User and then associate it with administration.Account entity also provide an association with userRole entity 

 

 


2.You can generate User_Overview Page and User_NewEdit Page by right clicking “Generate Overview Page” on the User Entity in domain model (This will automatically generate Overview and NewEdit page of user) 

 

 

 

3.Go to User_Overview  uage and add a call a microflow button and name the button as “change password” button to it from tootlbox>widget. 

4.Create a new microflow named “GTCP_GoToChangePassword”. 

 

 

 

 

Creating Administration.AccountPasswordData and assigning account object in it from user argument pass it to User_confirmPassword page.. 

 

5.Click Save on button -> change its action to “Call a microflow” and add a microflow named “CUP_ChangeUserPassword”. 

 

Inserting image... 

 

6.Validate the attributes Password and confirmPassword of AccountPasswordData. 

7.Retrive the acount object from the AccountPasswordData argument and then change password attribute of account object and assign it to user object and commit user object. 

 

#Import Data From Excel Sheet 

 

# Introduction 

Adding large amounts of data to your application can be very time-consuming. In order to save time and effort, this process can be automated using the Excel Importer from the Mendix Marketplace. In this how-to, you will set up import templates and import data into your app using this module. 

 

# Screenshot Explanation 

 

Before you can start importing data into your application, you first need to set up the data structure and GUI by following these steps: 

 

Create the domain model with Main Entity(User). 

 

Create and Enumeration for both Active(Yes or No) and for Role(Admin or User). 

Generate the overview page for User. 

Link the overview pages to the navigation to access them directly. 

Download the Excel Importer and Mx Model Reflection modules from the Mendix Marketplace (available by clicking the shopping-cart icon in the upper right of Studio Pro). 

Create menu items for the ExcelImportOverview and the MxObjects_Overview pages (these pages already exist in the _USE_ME folders of the downloaded modules). 

Configure the Administrator user role to have the Configurator module role for the ExcelImporter module, and the ModelAdministrator module role for the Mx Model Reflection module. 

On import Overview page create a new template using Excel file and fill the details accordingly by referring to the following documentation:Excel Importer 

Add a “Call a microflow” Button in the User_Overview page and create a microflow (OpenImport_Page) as shown below. 

 

In OpenImport_Page microflow Retriving the Template from Database and Creating a TemplateDocument and Pass the TemplateDocument object to ExcelImport_Overview Page and show “ExcelImport_Overview” page. 

 

Graphical user interface, application

Description automatically generated 

10.Select a Excel File to import data and click Import. 

11.On Import button call a microflow “Import_ExcelPage” as shown below 

Diagram

Description automatically generated 

Retrieving the user selected template from frontend and validate the selected file from user then import it to user Excel Entity then call a microflow “TDFEUTU_TransferDataFromUserExcelToUser” and pass object “Template”. 

12.Create a microflow shown below: 

 

Retrieving the Excel Imported List of User which is in ExcelUser Entity and Transfering its Objects to User Entity in batches of 100 entries if Delete Status is false. 

 

#Export Data to Excel Sheet 

#Introduction 

This Feature Exports the User data to Excel Document. 

 

 #Implementation 

1.In the User_Overview page add microflow button and call microflow “ACT_ExportToExcel”. 

For further Implementation do refer the Excel Export documentation. 

 

#Adding User and Admin Security 

 

#For Admin Security: 

All the Privileges are assigned. 

 

#For Users Security: 

Export to Excel and Search User only privileges are assigned. 

 

 

 

 

 # Login as Per Roles and Privileges (User/Admin) 

5.1 Introduction 

This Component is used to Provide Sign-in Functionality as per respective 		 

Roles (User/Admin) and Privileges assigned to that role. For example: In User 		Management Module if the data entered is assigned User as a Role, then that 

data will be allocated with all user privileges and in this case User 

Privileges are only to Login and Export to Excel data feature. All the rights are given  

to Admin Role. To perform login Operation User or admin role can login using 

Username (Provided in the email Address excluding “@ and domain name from 

email” for e.g. for this email Address “Nagarro@gmail.com ” username will be 

“Nagarro”) default password as well which is “123456789Abc”. 

 
           This is all about User MAnagement
 

 

 
