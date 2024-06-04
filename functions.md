| Name of function   | Log in    |
| ------- | ------------ |
| Description of the function | Log in and get an Access token from AWS Cognito using login and password.  |
| Input data | e-mail, password |
| Input data source | User type it in the bracket in the web interface |
| Conditions | The e-mail and password brackets must be filled up |
| Destination | Giving access to users to use the service |
| Start condition | E-mail password |
| End condition | Log in, getting access token and renewer token |
| Additional effect | AWS Cognito will receive an error, in case of wrong password |
| Term of calling the function | User has to log in to use the service|


| Name of function   | Register    |
| ------- | ------------ |
| Description of the function | Registration to AWS Cognito user pool  |
| Input data | e-mail, password |
| Input data source | User type it in the bracket in the web interface |
| Conditions | The e-mail and password brackets must be filled up, and the password has to have at least one big letter, 8 characters, and some special characters |
| Destination | Creating a new user, adding functionality to use the service |
| Start condition | E-mail password |
| End condition | Registration of the user, getting access token and renewer token |
| Additional effect | Error because of password that does not meet the requirements or no e-mail |
| Term of calling the function | User has to register to use the service |

| Name of function   | Password change    |
| ------- | ------------ |
| Description of the function | Password change for a user  |
| Input data | old password, new password, e-mail |
| Input data source | User type it in the bracket in the web interface |
| Conditions | The password brackets must be filled up, the new password has to have at least one big letter, 8 characters, and some special characters. The user must first log in. |
| Destination | Changing user password to increase the security |
| Start condition | E-mail, old password, new password |
| End condition | Changing user password in AWS Cognito user pool |
| Additional effect | In case of the wrong old password or not meeting requirements for the new password, AWS Cognito will send an error |
| Term of calling the function | When user what to change the password |

| Name of function   | Log out    |
| ------- | ------------ |
| Description of the function | Log out from the session  |
| Input data | - |
| Input data source | - |
| Conditions | The user must log in first to log out |
| Destination | Deleteting sesion data |
| Start condition | e-mail, password, session token |
| End condition | Log out and all the temporary data is deleted |
| Additional effect | Error, when the session is already deleted |
| Term of calling the function | When user what to log out |

| Name of function   | Delete account    |
| ------- | ------------ |
| Description of the function | Delete an account from the AWS Cognito  |
| Input data | - |
| Input data source | - |
| Conditions | The user must log in first to delete an account|
| Destination | Deleting user account |
| Start condition | e-mail, session token |
| End condition | Deleting an account |
| Additional effect | Error from AWS Cognito |
| Term of calling the function | When user whats to delete an account |

| Name of function   | Delete user account using admin panel    |
| ------- | ------------ |
| Description of the function | Delete a user account from the AWS Cognito  |
| Input data | e-mail of the user to delete, session token |
| Input data source | Fill the brackets in the admin panel delete user site |
| Conditions | The user must log in first to delete an account and have the admin privileges |
| Destination | Deleting user account |
| Start condition | e-mail of the user to delete, session token, admin privileges |
| End condition | Deleting an user account |
| Additional effect | Error from AWS Cognito |
| Term of calling the function | When admin whats to delete an account |

| Name of function   | Add user account using admin panel    |
| ------- | ------------ |
| Description of the function | Add a user account to the AWS Cognito  |
| Input data | e-mail of the user to create, new user password |
| Input data source | Fill the HTML form in the admin panel add user site |
| Conditions | The user must log in first to delete an account and have the admin privileges |
| Destination | Adding user account |
| Start condition | e-mail of the user to create, session token, new user password admin privileges |
| End condition | Adding an user account |
| Additional effect | Error from AWS Cognito |
| Term of calling the function | When admin whats to add an account |

| Name of function   | Change priviledges to the user    |
| ------- | ------------ |
| Description of the function | Change privileges to the user via AWS Cognito  |
| Input data | e-mail of the user to add privileges, session token |
| Input data source | Fill the brackets in the admin privilege panel |
| Conditions | The user must log in first to add privileges and have admin privileges |
| Destination | Change user privileges |
| Start condition | e-mail of the user to change privilege, session token, admin privileges |
| End condition | Changing IAM rule assigned to the user |
| Additional effect | Error from AWS Cognito |
| Term of calling the function | When admin whats to change account privileges |

| Name of function   | CV Upload    |
| ------- | ------------ |
| Description of the function | Uploading CV to the server  |
| Input data | CV file in PDF |
| Input data source | Upload CV file to the HTML form |
| Conditions | The user must be logged in and have default privileges |
| Destination | CV file uploaded safely to the S3 |
| Start condition | e-mail, session token, default privileges, pdf file |
| End condition | PDF file on S3 |
| Additional effect | Error from AWS S3, wrong file format |
| Term of calling the function | When user wants to upload the CV |

| Name of function   | Edit data    |
| ------- | ------------ |
| Description of the function | Edit data uploaded in the CV so the correct data can be sent to analysis  |
| Input data | form with CV data |
| Input data source | HTML form |
| Conditions | The user must be logged in and have default privileges, the user had to upload the CV first|
| Destination | CV data send to the aws DynamaDB |
| Start condition | e-mail, session token, default privileges, HTML form |
| End condition | User CV data uploaded to DynamoDB in the correct format and ready for analysis |
| Additional effect | Error from WAF, error from DynamoDB |
| Term of calling the function | When the user uploaded the CV in pdf and wants to send all the data for further analyses |

| Name of function   | Apply for the job    |
| ------- | ------------ |
| Description of the function | User uploaded the CV and edited the data and now has to trigger the analyses |
| Input data | - |
| Input data source | - |
| Conditions | The user must be logged in have default privileges, and upload CV and data edited|
| Destination | User changes status for ready |
| Start condition | e-mail, session token, default privileges |
| End condition | message that the process has been successfully started |
| Additional effect | Error from Backend |
| Term of calling the function | When the user is ready and wants to apply for a job |

| Name of function   | Ask AI chat    |
| ------- | ------------ |
| Description of the function | User asks chat about the application |
| Input data | text query |
| Input data source | HTML from |
| Conditions | The user must log in have default privileges, and finish the application process|
| Destination | User triggers lambda that triggers the AI chatbot |
| Start condition | e-mail, session token, default privileges |
| End condition | Answer from the LLM |
| Additional effect | Error from AWS Lambda |
| Term of calling the function | When user wants to ask about the  |

| Name of function   | Generate answer    |
| ------- | ------------ |
| Description of the function | Chat bot function that generates answer |
| Input data | text query |
| Input data source | AWS Lambda |
| Conditions | When triggered by AWS Lambda |
| Destination | Generating answer and sending it back with another lambda |
| Start condition | text querry|
| End condition | Answer from the LLM |
| Additional effect | Error from AWS Lambda |
| Term of calling the function | When triggered by AWS Lambda |

| Name of function   | Process data    |
| ------- | ------------ |
| Description of the function | LLM model process data and save the answer in AWS DynamoDB |
| Input data | CV data |
| Input data source | AWD DynamoDB |
| Conditions | When triggered by AWS Lambda |
| Destination | Candidate evaluation results send data to AWD DynamoDB |
| Start condition | CV data from DynamoDB|
| End condition | Candidate evaluation results |
| Additional effect | Error and sending information about it to admins using AWS SNS |
| Term of calling the function | When triggered by AWS Lambda |

| Name of function   | Begin data analysys    |
| ------- | ------------ |
| Description of the function | Trigger lambda that triggers the data analysis |
| Input data | - |
| Input data source | - |
| Conditions | User has recruiter privileges and some candidates uploaded the CV to the system |
| Destination | LLM starts the work |
| Start condition | session token, Some data from CVs in AWS DunamoDB |
| End contition | LLM evalutaion in progress |
| Additional effect | Error From Lambda |
| Term of calling the function | Recruiter wants to start candidates evaluation automatisation |

| Name of function   | Show candidates    |
| ------- | ------------ |
| Description of the function | Retrieving candidates that uploaded data |
| Input data | - |
| Input data source | - |
| Conditions | User has recruiter privileges and candidate evaluation has finished |
| Destination | Retreving list from AWS DynamoDB and evalutaion data |
| Start condition | session token, Some data from CVs in AWS DunamoDB |
| End condition | List of the candidates |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruiter wants to see a list of the recruits with system evaluation |

| Name of function   | Edit candidate data    |
| ------- | ------------ |
| Description of the function | Editing data candidates' data that was retrieved by the function 'Show candidates' |
| Input data | form |
| Input data source | HTML form |
| Conditions | User has recruiter privileges, gets candidate list, and selects the correct user to edit |
| Destination | Update data in the AWS DynamoDB  |
| Start condition | session token, HTML form |
| End condition | updated DynamoDB |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruiter wants to update candidate data |

| Name of function   | Send invitation to candidate    |
| ------- | ------------ |
| Description of the function | Sedning invitation to the candidate chosen from the list retrieved by the function 'Show candidates' |
| Input data | invitation date |
| Input data source | HTML form |
| Conditions | User has recruiter privileges, got candidate list, and chose the invitation date |
| Destination | Sending an invitation to the candidate's mail  |
| Start condition | session token, candidate's email, HTML form |
| End condition | updated DynamoDB and e-mail sent to the user via AWS SNS |
| Additional effect | Error From DynamoDB, AWS SNS |
| Term of calling the function | Recruiter wants to send an invitation to the candidate |

| Name of function   | Change candidate status    |
| ------- | ------------ |
| Description of the function | Changing candidate status in the database |
| Input data | candidate status |
| Input data source | HTML form |
| Conditions | User has recruiter privileges, got candidate list, and wants to change candidate status |
| Destination | Change candidate status in the database  |
| Start condition | session token, candidate's email, HTML form |
| End condition | updated DynamoDB |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruiter wants to change candidate status |

| Name of function   | Candidate acceptance    |
| ------- | ------------ |
| Description of the function | Changing the status of the candidate and sending a message to the HR department |
| Input data | - |
| Input data source | - |
| Conditions | User has recruiter privileges, got candidate list, and wants to accept the candidate|
| Destination | Change candidate status in the database and send a message to HR  |
| Start condition | session token, candidate's email |
| End condition | updated DynamoDB, message sent to HR |
| Additional effect | Error From DynamoDB, error from SNS |
| Term of calling the function | Recruiter wants to accept the candidate |

| Name of function   | Candidate decline    |
| ------- | ------------ |
| Description of the function | Changing the status of the candidate and deleting data from DynamoDB |
| Input data | - |
| Input data source | - |
| Conditions | User has recruiter privileges, got candidate list, and wants to decline the candidate|
| Destination | Change candidate status in the database and remove data from DynamoDB  |
| Start condition | session token, candidate's email |
| End condition | updated DynamoDB |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruiter wants to decline the candidate |