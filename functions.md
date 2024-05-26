| Name of function   | Log in    |
| ------- | ------------ |
| Description of the function | Log in and getting Access token from AWS Cognito using login and password.  |
| Input data | e-mail, passowrd |
| Input data source | User type it in the bracket in the web interafce |
| Conditions | The e-mail and password brackets must be fill up |
| Destination | Giving accees to user to use the service |
| Start contition | E-mail password |
| End contition | Log in, getting access token and renewer token |
| Additional effect | AWS Congnito will retrive an error, in case of wrong passord |
| Term of calling the function | User has to log in to use the service|


| Name of function   | Register    |
| ------- | ------------ |
| Description of the function | Registration to AWS congnito user pool  |
| Input data | e-mail, passowrd |
| Input data source | User type it in the bracket in the web interafce |
| Conditions | The e-mail and password brackets must be fill up, password has to have at least one big letter, 8 characters and some special character |
| Destination | Creating a new user, adding functionality to use the service |
| Start contition | E-mail password |
| End contition | Registration of the user, getting access token and renewer token |
| Additional effect | Error because of password that not meet the requirements or no e-mail |
| Term of calling the function | User has to register to use the service |

| Name of function   | Password change    |
| ------- | ------------ |
| Description of the function | Password change for a user  |
| Input data | old password, new password, e-mail |
| Input data source | User type it in the bracket in the web interafce |
| Conditions | The passwords brackets must be fill up, new password has to have at least one big letter, 8 characters and some special character. User must be first log in. |
| Destination | Changing user password to increate the security |
| Start contition | E-mail, old password, new passowrd |
| End contition | Changing user password in AWS Congnito user pool |
| Additional effect | In case of wrong old password or not meeting requirements for the new password, AWS cogniot will sent an error |
| Term of calling the function | When user what to change the password |

| Name of function   | Log out    |
| ------- | ------------ |
| Description of the function | Log out from the sesion  |
| Input data | - |
| Input data source | - |
| Conditions | The user must be log in first to log out |
| Destination | Deleteting sesion data |
| Start contition | e-mail, password, sessionToken |
| End contition | Log out and all the temporary data is deleted |
| Additional effect | Error, when the sesion is already deleted |
| Term of calling the function | When user what to log out |

| Name of function   | Delete account    |
| ------- | ------------ |
| Description of the function | Delete an account from the AWS cognito  |
| Input data | - |
| Input data source | - |
| Conditions | The user must be log in first to delete an account|
| Destination | Deleteting user account |
| Start contition | e-mail, sessionToken |
| End contition | Deleting an account |
| Additional effect | Error from AWS congnito |
| Term of calling the function | When user whats to delete an account |

| Name of function   | Delete user account using admin panel    |
| ------- | ------------ |
| Description of the function | Delete an user account from the AWS cognito  |
| Input data | e-mail of the user to delete, sessionToken |
| Input data source | Fill the brackets in the admin panel delete user site |
| Conditions | The user must be log in first to delete an account and have the admin priviledges|
| Destination | Deleteting user account |
| Start contition | e-mail of the user to delete, sessionToken, admin priviledges |
| End contition | Deleting an user account |
| Additional effect | Error from AWS congnito |
| Term of calling the function | When admin whats to delete an account |

| Name of function   | Change priviledges to the user    |
| ------- | ------------ |
| Description of the function | Change priviledges to the user via AWS Cognito  |
| Input data | e-mail of the user to add priviledges, sessionToken |
| Input data source | Fill the brackets in the admin priviledge panel |
| Conditions | The user must be log in first to add privilendges and have the admin priviledges|
| Destination | Change user priviledges |
| Start contition | e-mail of the user to change priviledge, sessionToken, admin priviledges |
| End contition | Changing IAM rule assigned to the user |
| Additional effect | Error from AWS congnito |
| Term of calling the function | When admin whats to changee an account priviledges |