| Name of function   | Log in    |
| ------- | ------------ |
| Description of the function | Log in and getting Access token from AWS Cognito using login and password.  |
| Input data | e-mail, passowrd |
| Input data source | User type it in the bracket in the web interafce |
| Conditions | The e-mail and password brackets must be fill up |
| Destination | Giving accees to user to use LLM service |
| Start contition | E-mail password |
| End contition | Log in, getting access token and renewer token |
| Additional effect | AWS Congnito will retrive an error, in case of wrong passord or token |
| Term of calling the function | User has to log in to use LLM |


| Name of function   | Registration    |
| ------- | ------------ |
| Description of the function | Registration to AWS congnito user pool  |
| Input data | e-mail, passowrd |
| Input data source | User type it in the bracket in the web interafce |
| Conditions | The e-mail and password brackets must be fill up, password has to have at least one big letter, 8 characters and some special character |
| Destination | Creating a new user, adding functionality to qurry a LLM |
| Start contition | E-mail password |
| End contition | Registration of the user, getting access token and renewer token |
| Additional effect | Error because of password that not meet the requirements or no e-mail |
| Term of calling the function | User has to register to use LLM |

| Name of function   | Password change    |
| ------- | ------------ |
| Description of the function | Password change for a log in user  |
| Input data | old password, new password |
| Input data source | User type it in the bracket in the web interafce |
| Conditions | The passwords brackets must be fill up, new password has to have at least one big letter, 8 characters and some special character. User must be first log in. |
| Destination | Changing user password to increate the security |
| Start contition | E-mail, old password, new passowrd |
| End contition | Changing user password in AWS Congnito user pool |
| Additional effect | In case of wrong old password or not meeting requirements for the new password, AWS cogniot will sent an error |
| Term of calling the function | When user what to change the password |

| Name of function   | Retrive avatar    |
| ------- | ------------ |
| Get avatar photo of the user from S3 using auth token and sesion token, photo is named with the user e-mail  |
| Input data | - |
| Input data source | - |
| Conditions | When the user log in, get the user avatar photo |
| Destination | Add customization to the web app |
| Start contition | auth token, sesion token, e-mail |
| End contition | Get avatar photo |
| Additional effect | When photo not found, use default avatar |
| Term of calling the function | When user log in to the service |

| Name of function   | Uploading avatar    |
| ------- | ------------ |
| Uploading avator to S3 using auth token, session token and e-mail  |
| Input data | photo |
| Input data source | User upload photo via web interface |
| Conditions |When the user wants to change the avatar photo |
| Destination | Add customization to the web app |
| Start contition | photo,auth token, sesion token, e-mail |
| End contition | Change avatar on S3 |
| Additional effect | Give an error when the image is not correct (wrong size, type) |
| Term of calling the function | User uploading the photo and clicking replace |