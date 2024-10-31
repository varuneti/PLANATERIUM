### Test Case : Verify Deletion of Planets 
- Use Case ID: 5
- Description: Users should be able to remove Planets from the Planetarium
- Actors:
    - User that is already in the system

### Test Data

#### Requirement: Planet and Moon names should not have more than 30 characters and should be unique
- Will work on Planet Requirement here and Moon requirements on Use Case ID 6
- Planet names must be Unique 

|0 character Planet|30 characters Planet|31 characters Planet|
|-|--|--|
||CybertronAndKryptonExploding!|BatmanBrokeHisLegFightingJoker!|

#### Requirement: Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database
- Check to see if it is possible to create a Planet without an associate image. 
    - Should be possible with and without

|Planet Name|Image|Success?|
|-|-|-|
|Jupiter|{image}|Succesful|
|Krypton|No Image|Successful|

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
- Should be tested in a past Use Case(ID:4)

|Planet|Planet Creation Result|Redirect|
|-|-|-|
|(0 characters)|Planet Created|User redirected to Home Page|
|CybertronAndKryptonExploding!|Planet Created|User redirected to Home Page|
|BatmanBrokeHisLegFightingJoker!|Planet Not Created|User redirected to Home Page|


#### Equivalence Partitioning for uniquness of Planet Names 
- Should be tested in a past Use Case(ID:4)
- Check that you cannot create a Planet with a name that already exists
    - For user Batman, Planets cannot be creates witht the name 'Earth' and 'Mars' 

#### Parameterized Test Scenario

|Step|Actor|Data|Result|
|-|-|-|-|
|given the user was able to correctly login to the appliction|User|{username:Batman},{password:I am the night}|http://localhost:8080/|
|given the user is on the home page|User||Redirected to Home Page {http://localhost:8080/planaterium}|
|when the user provides a valid name and presses the delete button|User|Valid Name and presses Delete||
|then the Planet is deleted successfully and the table is refreshed|User||Planet Deleted|
|and the user should be redirected to the home page|User||http://localhost:8080/planaterium|
