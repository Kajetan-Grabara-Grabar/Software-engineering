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

| Name of function   | CV Upload    |
| ------- | ------------ |
| Description of the function | Uploading CV to the server  |
| Input data | CV file in PDF |
| Input data source | Upload CV file to the HTML form |
| Conditions | The user must be log in and have default priviledges|
| Destination | CV file uploaded safetly to the S3 |
| Start contition | e-mail, sessionToken, default priviledges, pdf file |
| End contition | PDF file on S3 |
| Additional effect | Error from AWS S3, wrong file format |
| Term of calling the function | When user wants to upload the CV |

| Name of function   | Edit data    |
| ------- | ------------ |
| Description of the function | Edit data uploaded in the CV so the correct data can be sent to analysys  |
| Input data | form with CV data |
| Input data source | HTML form |
| Conditions | The user must be log in and have default priviledges, user had to uploaded the CV first|
| Destination | CV data send to the aws DynamaDB |
| Start contition | e-mail, sessionToken, default priviledges, HTML form |
| End contition | User CV data uploaded to DynamoDB in correct format and ready for analysys |
| Additional effect | Error from WAF, error from DynamoDB |
| Term of calling the function | When user uploaded the CV in pdf and wants to send all the data for furder analysys |

| Name of function   | Apply for the job    |
| ------- | ------------ |
| Description of the function | User uploaded the CV and edited the data and now has to trigger the analysys |
| Input data | - |
| Input data source | - |
| Conditions | The user must be log in and have default priviledges, and uploaded CV and data edited|
| Destination | User triggers lambda that trigges the AI analysys |
| Start contition | e-mail, sessionToken, default priviledges|
| End contition | Message that the proccess has been successfuly started |
| Additional effect | Error from AWS Lambda |
| Term of calling the function | When the user is ready and wants to apply for a job |

| Name of function   | Ask AI chat    |
| ------- | ------------ |
| Description of the function | User asks chat about the applicaiton |
| Input data | text querry |
| Input data source | HTML from |
| Conditions | The user must be log in and have default priviledges, and finished the application process|
| Destination | User triggers lambda that trigges the AI chatbot |
| Start contition | e-mail, sessionToken, default priviledges|
| End contition | Answer from the LLM |
| Additional effect | Error from AWS Lambda |
| Term of calling the function | When user wants to ask about the  |

| Name of function   | Generate answer    |
| ------- | ------------ |
| Description of the function | Chat bot funciton that generates answer |
| Input data | text querry |
| Input data source | AWS Lambda |
| Conditions | When triggered by AWS Lambda |
| Destination | Generating answer and sending it back with another lambda |
| Start contition | text querry|
| End contition | Answer from the LLM |
| Additional effect | Error from AWS Lambda |
| Term of calling the function | When triggered by AWS Lambda |

| Name of function   | Process data    |
| ------- | ------------ |
| Description of the function | LLM model process data and save the answer in AWS DynamoDB |
| Input data | CV data |
| Input data source | AWD DynamoDB |
| Conditions | When triggered by AWS Lambda |
| Destination | Candidate evaluation results sends data to AWD DynamoDB |
| Start contition | CV data from DynamoDB|
| End contition | Candidate evaluation results |
| Additional effect | Error and seding information about it to admins using AWS SNS |
| Term of calling the function | When triggered by AWS Lambda |

| Name of function   | Begin data analysys    |
| ------- | ------------ |
| Description of the function | Trigger lambda that triggers the data analysys |
| Input data | - |
| Input data source | - |
| Conditions | User has a recruter priviledges and some candidate uploaded the CV to the system |
| Destination | LLM starts the work |
| Start contition | sesion token, Some data from CVs in AWS DunamoDB |
| End contition | LLM evalutaion in progress |
| Additional effect | Error From Lambda |
| Term of calling the function | Recruter wants to start candidates evaluation automatisation |

| Name of function   | Show candidates    |
| ------- | ------------ |
| Description of the function | Retreving candidates that uploaded data |
| Input data | - |
| Input data source | - |
| Conditions | User has a recruter priviledges and candidates evaluation has finished |
| Destination | Retreving list from AWS DynamoDB and evalutaion data |
| Start contition | sesion token, Some data from CVs in AWS DunamoDB |
| End contition | List of the candidates |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruter wants to see list of the recrutes with system evaluation |

| Name of function   | Edit candidate data    |
| ------- | ------------ |
| Description of the function | Edditing data candidates' data that was retrived by function 'Show candidates' |
| Input data | form |
| Input data source | HTML form |
| Conditions | User has a recruter priviledges, got candidate list and select correct user to edit |
| Destination | Update data in the AWS DynamoDB  |
| Start contition | sesion token, HTML form |
| End contition | updated DynamoDB |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruter wants to update candidate data |

| Name of function   | Send invitation to candidate    |
| ------- | ------------ |
| Description of the function | Sedning invitation to the candidate chosen from list retrived by function 'Show candidates' |
| Input data | invitation date |
| Input data source | HTML form |
| Conditions | User has a recruter priviledges, got candidate list and chose the invitation date |
| Destination | Sending invitation to the candidate's mail  |
| Start contition | sesion token, canidate's email, HTML form |
| End contition | updated DynamoDB and e-mail send to user via AWS SNS |
| Additional effect | Error From DynamoDB, AWS SNS |
| Term of calling the function | Recruter wants to send invitation to the candidate |

| Name of function   | Change candidate status    |
| ------- | ------------ |
| Description of the function | Changing candidate status in the database |
| Input data | candidat status |
| Input data source | HTML form |
| Conditions | User has a recruter priviledges, got candidate list and wants to change candidate status |
| Destination | Change candidate status in the database  |
| Start contition | sesion token, canidate's email, HTML form |
| End contition | updated DynamoDB |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruter wants to change candidate status |

| Name of function   | Candidate acceptance    |
| ------- | ------------ |
| Description of the function | Changing status of the candidate and seding message to the HR department |
| Input data | - |
| Input data source | - |
| Conditions | User has a recruter priviledges, got candidate list and wants to accept the candidate|
| Destination | Change candidate status in the database and send message to HR  |
| Start contition | sesion token, canidate's email |
| End contition | updated DynamoDB, message send to HR |
| Additional effect | Error From DynamoDB, error from SNS |
| Term of calling the function | Recruter wants to accept the candidate |

| Name of function   | Candidate decline    |
| ------- | ------------ |
| Description of the function | Changing status of the candidate and deleting data from DynamoDB |
| Input data | - |
| Input data source | - |
| Conditions | User has a recruter priviledges, got candidate list and wants to decline the candidate|
| Destination | Change candidate status in the database and remove data from DynamoDB  |
| Start contition | sesion token, canidate's email |
| End contition | updated DynamoDB |
| Additional effect | Error From DynamoDB |
| Term of calling the function | Recruter wants to decline the candidate |