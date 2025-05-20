# Secure-Code-Implementation-Application
General info
The PasswordManagerApp project is web application written in C# using .NET Core 3.1 with ASP.NET Core MVC. This app enable users to store sensitive data in a secure way. The main feature of this app is to check if stored password has previously appeared in data breach.

The application can be developed, built and run cross-platform on Windows, and Linux distribution(macOS not tested).

Table of contents
General info
Technologies
Features
Security
Configuration
Setup
Requirements
Build
Usage
Technologies
Have I Been Pwned API - allows Internet users to check whether their personal data has been compromised by data breaches
JSON Web Token - defines a compact and self-contained way for securely transmitting information between parties as a JSON object
Quartz.NET - job scheduling system
SignalR - library that allows server code to send asynchronous notifications to client-side web applications
Otp.NET - an implementation of TOTP
Password Generator - library which generates random passwords
ipstack - geolocation API. Allows us to locate and identify website visitors by IP address
Features
Password pwned check
The web vault check every 5h or on user demand whether stored passwords have been compromised. To be more specific, system call Have I Been Pwned API to check if selected password has appeared in a data breach.

imagepasscheck

Client application pass only first 5 characters of password hash to the Have I Been Pwned API .As the response client received a set of matching records( password hash list followed by a count of how many times it appears in a data breach). What makes our app safe is client app can then search the result records for the presence of source hash.

We do not send full password hash to the external API.

Security
After successfull authentication server generates tenable JWT Token which gives user permission to access sensitive data
JWT Token payload is additionally encrypted
Web vault check authenticity and integrity of JWT token
Two-factor authentication
Sensitive user data are encrypted with symmetric key( based on user's password hash)
User is notified in case of password breach or unauthorized login attempt
User's passwords breach are checked in a secure way( More in this paragraph)
Configuration
To run this app first of all you''ll need to run backend PasswordManagerApp server.

(Optionally) Set up your ipstack api key, default one is incorrect!

Setup
Requirements
.NET Core 3.1 SDK
To run this project:
restore, build and run using commands:
cd PasswordManagerApp
dotnet run
type localhost:5004 in the browser
Usage
Next move is up to you
Store any data you wish


Customize your profile
profileWebvault

Check if your password was previously exposed in data breaches
