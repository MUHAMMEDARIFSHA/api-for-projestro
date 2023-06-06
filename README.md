# api-doc
             PROJESTRA API DOCUMENTATION



Version
Date
Author
Description
1.0
02-06-2023
MUHAMMED ARIFSHA
 Initial Draft



Introduction

Projestra is a webapplication for project management.In this application we can manage individual projects and group projects. It connects the workes to a common working place.
The companies can use it to manage their large projects and to ensure the proper workflow in between different employes.  



ADMIN PANEL

Admin Sign-In

Method
URL            
POST
/api/admin/signin



Description: Sign in to the admin account.(The admin will be registered directly to the database)

Request Body:
name (string, required): The name of the admin.
password (string, required): The password for the admin account.
Response
200 OK: Sign-in successful. Returns an authentication token.
400 Bad Request: Invalid request format or missing required fields.
401 Unauthorized: Incorrect email or password.
500 Internal Server Error: An error occurred on the server.


Admin Dashboard


Method
URL            
GET
/api/admin/dashboard




Description: Retrieve data for the admin dashboard.

Responses:
200 OK: Dashboard data retrieved successfully. Returns the data for the admin dashboard.
401 Unauthorized: User is not authorized to access the admin dashboard.
500 Internal Server Error: An error occurred on the server.

Admin Users View

Method
URL            
GET
/api/admin/users


Description: Retrieve the list of users and reported accounts.

Responses:
200 OK: User data retrieved successfully. Returns the list of users and reported accounts.
401 Unauthorized: User is not authorized to access the admin users view.
500 Internal Server Error: An error occurred on the server.

Block User


Method
URL            
POST
/api/admin/user/block{userId}




Description: Block a user.

Parameters:
userId (string, required): The ID of the user to be blocked.
Responses:
200 OK: User blocked successfully.
401 Unauthorized: User is not authorized to block users.
404 Not Found: User with the provided ID not found.
500 Internal Server Error: An error occurred on the server.





Admin Subscription Details

Method
URL            
GET
/api/admin/subcription_datails





Description: Retrieve the list of people who has prime subscriptions with the details of plans and time period.

Responses:
200 OK: Subscription data retrieved successfully. Returns the list of users with subscription.
401 Unauthorized: User is not authorized to access the subscription list.
500 Internal Server Error: An error occurred on the server.



Cancel Subcription
(due to the violation of T&C the subscription is canceled)

Method
URL            
POST
/api/admin/cancel_subcription{userId}




Description: Remove the prime subscription)

Parameters:
userId(string, required): The ID of the user to cancel subscription.


Responses:
200 OK: Organization blocked successfully.
401 Unauthorized: User is not authorized to block organizations.
404 Not Found: Organization with the provided ID not found.
500 Internal Server Error: An error occurred on the server.

Delete Project
(Project violating the laws should be removed)


Method
URL            
DELETE
/api/admin/delete_project




Description :Delete the project.

Responses:
200 OK: Deleted the project sucessfully. Return the name of project.
401 Unauthorized: User is not authorized to delete the project.
500 Internal Server Error: An error occurred on the server.










USER PANEL

Authentication and Authorization

To access the JOBCY API, users and organizations must authenticate themselves and obtain an access token. This token must be included in the headers of subsequent API calls for authorization.


User Registration

Method
URL            
POST
/api/user/register




Description: Register a new user account.


Parameters:
email (string, required): The email address of the user.
password (string, required): The password for the user account.

Request Body:
email (string, required): The email address of the user.
password (string, required): The password for the user account.
Responses:
201 Created: Registration successful. The user account is created.
400 Bad Request: Invalid request format or missing required fields.
409 Conflict: Email already exists. The provided email is already registered.
500 Internal Server Error: An error occurred on the server.
User Registration form

Method
URL            
GET
/api/user/register




Description: Retrieve the user registration form.

Responses:
200 OK: User registration form retrieved successfully. Returns the user registration form.
401 Unauthorized: User is not authorized to access the user registration form.
500 Internal Server Error: An error occurred on the server.


User Login Form


Method
URL            
GET
   /api/user/sign-in


Description: Retrieve the user signin form.

Responses:
200 OK: User sign in  form retrieved successfully. Returns the user login form..
401 Unauthorized: User is not authorized to access the user registration form.
500 Internal Server Error: An error occurred on the server.



User Sign IN


Method
URL            
POST
   /api/user/sign-in


Description: Sign In the user by verifying the details.


Request Body:
email (string, required): The email address of the user.
password (string, required): The password for the user account.

Responses:
200 OK: Authentication successful. Access token provided.
400 Bad Request: Invalid request format or missing required fields.
401 Unauthorized: Incorrect email or password.
500 Internal Server Error: An error occurred on the server.

OTP Form 

Method
URL            
GET
   /api/user/otp-verify

Description: Retrieve the OTP verification form.

Responses:
200 OK: OTP verification form retrieved successfully. Returns the OTP verification form.
401 Unauthorized: User is not authorized to access the OTP verification form.
500 Internal Server Error: An error occurred on the server.

OTP Verification


Method
URL            
POST
   /api/user/otp-verify{userId}





Request Body:
otp (string, required): The OTP (One-Time Password) entered by the user for verification.
Responses:
200 OK: OTP verification successful.
400 Bad Request: Invalid request format or missing required fields.
401 Unauthorized: Invalid OTP provided.
500 Internal Server Error: An error occurred on the server.

Forgot Password

Method
URL            
POST
   /api/user/forgot-password




Request Body:
email (string, required): The email address of the user who forgot the password.
Responses:
200 OK: Request for password reset initiated successfully. An email will be sent to the user with further instructions.
400 Bad Request: Invalid request format or missing required fields.
404 Not Found: User with the provided email address not found.
500 Internal Server Error: An error occurred on the server.

Forget Password Form

Method
URL            
GET
   /api/user/forget-password



Description: Retrieve the Forgot Password form.
Responses:
200 OK: Forgot Password form retrieved successfully. Returns the Forgot Password form.
401 Unauthorized: User is not authorized to access the Forgot Password form.
500 Internal Server Error: An error occurred on the server.


Reset Password


Method
URL            
POST
   /api/user/reset-password



Request Body:
email (string, required): The email address of the user.
newPassword (string, required): The new password for the user account.
confirmPassword (string, required): Confirm the new password by entering it again.
Responses:
200 OK: Password reset successful.
400 Bad Request: Invalid request format or missing required fields.
401 Unauthorized: Invalid or expired password reset token.
404 Not Found: User with the provided email address not found.
500 Internal Server Error: An error occurred on the server.

Password Reset Page

Method
URL            
GET
   /api/user/reset-password



Description: Retrieve the Reset Password form.

Responses:
200 OK: Reset Password form retrieved successfully. Returns the Reset Password form.
401 Unauthorized: User is not authorized to access the Reset Password form.
500 Internal Server Error: An error occurred on the server.



Create Project Page


Method
URL            
GET
   /api/user/create-project


Responses:
201 Retrive the project creation page  successfully.
400 Bad Request: Invalid request format or missing required fields.
500 Internal Server Error: An error occurred on the server.

Endpoint: GET /api/posts

Parameters:
page (integer, optional): The page number for pagination.
pageSize (integer, optional): The number of posts per page.

Responses:
200 OK: Posts retrieved successfully.
400 Bad Request: Invalid request format.
500 Internal Server Error: An error occurred on the server.

Profile Page

Method
URL            
GET
   /api/user/profile{userId}


Description: Retrieve the profile information of a user.

Parameters:
userId (string, required): The ID of the user whose profile information is being retrieved.
Responses:
200 OK: Profile information retrieved successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to access the profile information.
404 Not Found: User with the provided ID not found.
500 Internal Server Error: An error occurred on the server.


Edit Profile

Method
URL            
POST
   /api/user/profile-edit


Request Body:
email (string, required): The email address of the user.
phone(string):Phone Number of user
company(string):company name of user.
about(string):details of user.
Responses:
200 OK: Profile information updated successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to access the profile information.
404 Not Found: User with the provided ID not found.
500 

ADD Project


Method
URL            
POST
   /api/user/add-project



Description:add individual project of the user.

Parameters:
userId (string, required): The ID of the user whose  is creatin the project.
Request Body:
 Project name (string,required):Name of the project.
Description(string):Description of the project.

Responses:
200 OK: Project created  successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to create a project.
404 Not Found: User with the provided ID not found.
500 Internal Server Error: An error occurred on the server.

ADD  Group  Project


Method
URL            
POST
   /api/user/add-group-project



Description: Start group project .

Parameters:
userId (string, required): The ID of the user whose id the admin of the group project..
Request Body:
 Project name (string,required):Name of the project.
Description(string):Description of the project.
Project manager name(string): Name of project manager.
Team Lead Name(string): Name of team lead.
 StartingDate(Date):Date of starting the project.
Dead Line(Date): Date of ending the project.
Members Name(string):Name of workers in the group.

Responses:
200 OK: Project created  successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to create a project.
404 Not Found: User with the provided ID not found.
500 Internal Server Error: An error occurred on the server.

Chat Page

Endpoint: GET /api/chats/{chatId}

Description:

 Retrieve the chat history between the current user and another person.
 Or the chat in the group chat .

Parameters:
chatId (string, required): The ID of the chat conversation.
Responses:
200 OK: Chat history retrieved successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to access the chat history.
404 Not Found: Chat with the provided ID not found.
500 Internal Server Error: An error occurred on the server.

Endpoint: GET /api/chats/{chatId}/older-messages

Description: 
Retrieve older messages in the chat conversation.

Parameters:
chatId (string, required): The ID of the chat conversation.
page (integer, optional): The page number for pagination.
pageSize (integer, optional): The number of messages per page.
Responses:
200 OK: Older messages retrieved successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to access the older messages.
404 Not Found: Chat with the provided ID not found.
500 Internal Server Error: An error occurred on the server.

Call 



Method
URL            
POST
   /api/call/{call Id}/start


Endpoint: POST /api/chats/{chatId}/call

Description: Initiate a call .

Parameters:
Call Id(string, required): The ID of the  call .
Responses:
200 OK: Call initiated successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to initiate the call.
404 Not Found: Chat with the provided ID not found.

Project Page - Individual


Method
URL            
GET
   /api/user/project-page



Description: 

Retrieve a list of  projects the user has.

Responses:
200 OK: projects retrieved successfully.
400 Bad Request: Invalid request format.
500 Internal Server Error: An error occurred on the server.



Project Page - Group


Method
URL            
GET
   /api/user/group-project-page



Description: 

Retrieve a list of group projects the user has.

Responses:
200 OK: group projects retrieved successfully.
400 Bad Request: Invalid request format.
500 Internal Server Error: An error occurred on the serve.

Notification Page

Endpoint: GET /api/users/notifications/{userId}

Description:
 Retrieve the notifications for a user.

Parameters:
userId (string, required): The ID of the user whose notifications are being retrieved.
Responses:
200 OK: Notifications retrieved successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to access the notifications.
404 Not Found: User with the provided ID not found.
500 Internal Server Error: An error occurred on the server


Video Call Page

Method
URL            
POST
   /api/user/video-calls




Description: 
Initiate a video call.

Request Body:
callerId (string, required): The ID of the user initiating the call.
receiverId (string, required): The ID of the user receiving the call.
Responses:
200 OK: Video call initiated successfully.
400 Bad Request: Invalid request format or missing required fields.
401 Unauthorized: User is not authorized to initiate the call.
404 Not Found: User with the provided ID not found.
500 Internal Server Error: An error occurred on the server.


Endpoint: PUT /api/video-calls/{callId}

Description: Update the video call status.

Parameters:
callId (string, required): The ID of the video call.
Request Body:
status (string, required): The updated status of the video call (e.g., "connected", "disconnected").
Responses:
200 OK: Video call status updated successfully.
400 Bad Request: Invalid request format or missing required fields.
401 Unauthorized: User is not authorized to update the call status.
404 Not Found: Video call with the provided ID not found.
500 Internal Server Error: An error occurred on the server.

Team Lead

Poject Page for Team Lead

Method
URL            
GET
   /api/user/team/group-project-page


Description: 

Retrieve the details of the group project.

Responses:
200 OK: group projects details retrieved successfully.
400 Bad Request: Invalid request format.
500 Internal Server Error: An error occurred on the serve.

Add Members to the team

Method
URL            
POST
   /api/user/team/add-group-member


Parameters:
userId(string, required): The ID of the team lead.

Request Body

Member Name(string,required): Name of the new member.
Member Id(string,required): Id of the member
Position(string):Position of the new member.

Responses:
200 OK: new member added sucessfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to update the call status.
500 Internal Server Error: An error occurred on the serve.

Remove Members to the team

Method
URL            
POST
   /api/user/team/remove-group-member{userId}


Parameters:
userId(string, required): The ID of the team lead.

Request Body

Member Name(string,required): Name of the new member.
Member Id(string,required): Id of the member
Position(string):Position of the new member.

Responses:
200 OK:  member removed from the group sucessesfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to update the call status.
500 Internal Server Error: An error occurred on the serve.

Assign task

Method
URL            
POST
   /api/user/team/add-task.


Parameters:
userId(string, required): The ID of the team lead.

Request Body

Task Name(string,required): Name of the task.
Task description(string):Description of the task.
Member (string):the member(s) assigned the task.

Responses:
200 OK:  task added successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to update the call status.
500 Internal Server Error: An error occurred on the serve.



Delete task

Method
URL            
POST
   /api/user/team/delete-task.


Parameters:
userId(string, required): The ID of the team lead.

Request Body

Task ID(string,required): Id of the task.

Responses:
200 OK:  task deleted successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to update the call status.
500 Internal Server Error: An error occurred on the serve.


Delete Project 

Method
URL            
POST
   /api/user/team/delete-project.


Parameters:
userId(string, required): The ID of the team lead / project manager.

Request Body

Project ID(string,required): Id of the project.

Responses:
200 OK:  project deleted successfully.
400 Bad Request: Invalid request format.
401 Unauthorized: User is not authorized to update the call status.
500 Internal Server Error: An error occurred on the serve.






—------------------------------------------------END—--------------------------------------------------------






