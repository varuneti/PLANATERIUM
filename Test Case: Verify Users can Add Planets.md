### Test Case : Verify Users can Add Planets 
- Use Case ID: 4
- Description: Users should be able to add new Planets to the Planetarium
- Actors:
    - User that is already in the system

### Test Data

#### Requirement: Planet and Moon names should not have more than 30 characters and should be unique
- Will work on Planet Requirement here and Moon requirements on Use Case ID 6
- Planet names must be Unique

|0 character Planet|30 characters Planet|31 characters Planet|
|-|--|--|
||BatmanBrokeHisLegFightingJoker|CybertronAndKryptonAreExploding|

#### Requirement: Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database
- Check to see if it is possible to create a Planet without an associate image. 
    - Should be possible with and without

|Planet Name|Image|Success?|
|-|-|-|
|Jupiter|{image}|Succesful|
|Krypton|No Image|Successful|
|(no values)|{image}|Successful|
|(no values)|no image|Successful|

#### Requirement: Planets should be “owned” by the user that added it to the Planetarium 
- Planet should be given associated Owner ID that is related to the Owner who created the Planet inside of the Planetarium
    - For User Batman, Planets Earth and Mars have an Owner ID of 1 which relates them to their creator of Batman 

#### Environment Data
- Browser: Chrome
- Operating System: Mac OS Sonoma 
- Version of Planetarium: 1.0
- Background Data:
    - Home Page for Planetarium: http://localhost:8080/planaterium

### Test Scenarios

#### Boundary Analysis for Planet Name 
|Planet|Planet Creation Result|Redirect|
|-|-|-|
|(0 characters)|Planet Created|User redirected to Home Page|
|CybertronAndKryptonExploding!|Planet Created|User redirected to Home Page|
|BatmanBrokeHisLegFightingJoker!|Planet Not Created|User redirected to Home Page|


#### Equivalence Partitioning for uniquness of Planet Names 
- Check that you cannot create a Planet with a name that already exists
    - For user Batman, Planets cannot be creates witht the name 'Earth' and 'Mars' 

#### Parameterized Test Scenario

|Step|Actor|Data|Result|
|-|-|-|-|
|given the user was able to correctly login to the appliction |User|{username:Batman},{password:I am the night}|http://localhost:8080/|
|given the user is on the home page|User||Redirected to Home Page {http://localhost:8080/planaterium}|
|s|User|planet name, photo, presses submit||
|then the Planet is created successfully and the table is refreshed|User||Planet Created|
|and the user should be redirected to the home page|User||http://localhost:8080/planaterium|
