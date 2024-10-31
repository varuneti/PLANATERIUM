### Test Case : Verify Creation of Moon Relating to Planet
- Use Case ID: 6
- Description: Users should be able to add Moons to the Planetarium associated with a Planet
- Actors:
    - User that is already in the system

### Test Data

#### Requirement: Planet and Moon names should not have more than 30 characters and should be unique
- Will work on Moon Requirement here as Planet requirements was done on Use Case ID 4
- Moon names must be Unique

|0 character Planet|30 characters Planet|31 characters Planet|
|-|--|--|
||TheMoonOfOaFullOfGreenLanterns|KryptonHasNoMoonBecauseItIsAsh!|

#### Requirement: Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database
- Check to see if it is possible to create a Moon without an associate image. 
    - Should be possible with and without an image

|Moon Name|Image|Success?|
|-|-|-|
|Cybertron|{image}|Succesful|
|Oa|No Image|Successful|

#### Requirement: Moons should be “owned” by the Planet the User adding the moon associated it with 
- The Moons associated Owner ID will be the same as the ID that is given to a Planet at creation
    - For User Batman, Moon Luna is associated with Planet Earth by Owner ID 1
- Planet should be given associated Owner ID that is related to the Owner who created the Planet inside of the Planetarium
    - For User Batman, Planets Earth and Mars have an Owner ID of 1 which relates them to their creator of Batman 

#### Environment Data
- Browser: Chrome
- Operating System: Mac OS Sonoma 
- Version of Planetarium: 1.0
- Background Data:
    - Home Page for Planetarium: http://localhost:8080/planaterium

### Test Scenarios

#### Boundary Analysis for Moon Name 
|Moon|Moon Creation Result|Redirect|
|-|-|-|
|(0 characters)|Moon Created|User redirected to Home Page|
|TheMoonOfOaFullOfGreenLanterns|Planet Created|User redirected to Home Page|
|KryptonHasNoMoonBecauseItIsAsh!|Planet Not Created|User redirected to Home Page|


#### Equivalence Partitioning for uniquness of Moon Names 
- Check that you cannot create a Moon with a name that already exists
    - For user Batman, Moons cannot be creates witht the name 'Luna' and 'Titan' 

#### Parameterized Test Scenario

|Step|Actor|Data|Result|
|-|-|-|-|
|given the user was able to correctly login to the appliction |User|{username:Batman},{password:I am the night}|http://localhost:8080/|
|given the user is on the home page|User||Redirected to Home Page {http://localhost:8080/planaterium}|
|when the user provides a valid name, planet ID and adds a photo and presses the submit button|User|Valid Name, Planet ID, Photo(not mandatory) and presses submit||
|then the Moon is created successfully and the table is refreshed|User||Moon Created|
|and the user should be redirected to the home page|User||http://localhost:8080/planaterium|
