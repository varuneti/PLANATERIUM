### Test Case : Planet and Moon Visibility
- Use Case ID: 3
- Description: Users should be able to see planets and moons added to the Planetarium
- Actors:
    - User that is already in the system

### Test Data

#### Requirement: Users should only be able to interact with resources they have added to the Planetarium
- User should only be able to see the the Planets and Moons that the User created themselves
    - User Batman should be able to see 2 planets, Earth and Mars, as well as 2 moons, Luna and Titan.  

#### Requirement: Only logged in Users should be able to access the Planetarium home page
- Only once a correct username and password is created can the Planetarium home page be seen
    - When logged in as Batman, homepage is visibile but otherwise it should not be possible. (Unless another User is created)

#### Requirement: Planets should be “owned” by the user that added it to the Planetarium  
- Each Planet has a planet ID which should correlate withe the User who created them. 
    - For User Batman - He is Ownner ID 1 and the 2 planets he created have the same ID 


#### Environment Data
- Browser: Chrome
- Operating System: Mac OS Sonoma 
- Version of Planetarium: 1.0
- Background Data:
    - Home Page for Planetarium: http://localhost:8080/planaterium 

### Test Scenarios

#### Conditional Testing for Homepage Visibility 
- IF user is logged in THEN he should be able to see the homepage

|User|Logged In?|Visibility|URL|
|-|-|-|-|
|Batman|Yes|Able to see HomePage|http://localhost:8080/planaterium|
|None|No|Unable to See|Stays on http://localhost:8080/|


#### Equivalence Partition Testing to Verify Planets relate to Users
- Check using 'Batman' User
    - Making sure user can only see the Planets created by themselves: 2 planets, Earth and Mars, as well as 2 moons, Luna and Titan

#### Parameterized Test Scenario

|Step|Actor|Data|Result|
|-|-|-|-|
|given the user was able to correctly login to the appliction|User|{username}{password}|http://localhost:8080/|
|given the user is on the home page|User||http://localhost:8080/planaterium|
|the user should be able to see the planets and moons added to the planetarium|User||Able to see Planets and Moons on http://localhost:8080/planaterium|
|this includes the Type, ID, Name, Owner and a phtot of the planet/moon|||| 