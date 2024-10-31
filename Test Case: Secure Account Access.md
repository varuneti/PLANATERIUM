### Test Case : Secure Account Access 
- Use Case ID: 2
- Description: Users should be able to securely access their account
- Actors:
    - User that is already in the system

### Test Data

#### Requirement: Passwords should never be visible in plaintext
- Password that should be obfuscated: "I am the night"
- use for both Exploratory Testing and Error Guess Testing

### Requirement: Usernames and passwords should not be longer than 30 characters
- Testing should have been done in last Use Case 
    - Cannot securely access account if account has not been successfully created

#### Requirement: Users should have unique usernames
|Unique Username|Non-Unique Username|
|-|-|
|Robin|Batman|

#### Acceptance Testing Data
This is the only profile that has already been created.
|Username|Password|Success/Fail|
|-|-|-|
|Batman|I am the night|Success|

#### Environment Data
- Browser: Chrome
- Operating System: Mac OS Sonoma 
- Version of Planetarium: 1.0
- Background Data:
    - Login Page for Planetarium: http://localhost:8080/

### Test Scenarios

#### Decision Table For Username/Password Security Testing
|Username|Password|Success/Fail|
|-|-|-|
|Batman|I am the night|Success|
|Robin|Sidekick|Fail|

#### Exploratory Testing and Error Guess Testing

#### Parameterized Test Scenario
|Step|Actor|Data|Result|
|-|-|-|-|
|given the user is on the login page|User||http://localhost:8080/|
|when the user inputs the correct username and password information|User|{username:Batman},{password:I am the night}|Should be unable to see Password for Secure Access|
and clicks the login button|User|User Click|Redirected to the Home Page|
then the user should login to the application successfully|User|||
and be redirected to the homepage|User||Redirected to the Home Page|