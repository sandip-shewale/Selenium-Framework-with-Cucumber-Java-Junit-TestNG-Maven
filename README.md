# Selenium Framework with Cucumber Java Junit TestNG Maven

==============================================================

301. Cucumber Framework Design Plan 

Cucumber Framework Learning Plan :

1. Understand the importance of Behavior Driven Development
2. Cucumber Framework Architecture and it's core functionalities
3. Selenium Integration with Cucumber

==============================================================

Difference between TDD and BDD in Selenium

==============================================================

Test-driven development
Behavior-Driven Development

TDD approach is basically used for the unit of modular Framework
BDD approach is basically used with Hybrid or data-driven framework.

TDD focuses on the implementation of the system
BDD explains the behavior of an application for the end-user

Here we use programing language to write test cases like java etc.
Here is use gherkin language like English

This approach is basically used for a small application like application have 4 to 6 pages
This approach is basically used for a big application like application have more than 10 pages.

If some functionality changes then it will impact more
If some functionality changes then it will impact less than TDD

==============================================================

303. QA role in BDD

305. Advantages of BDD, Why it is getting popular

Advantages :

This can be used as Standard Template where all QA can stick to one common standards of defining testcases.
Each scenario reflects a Business Value.
We can estimate the Test covereage happened for each Business outcome by going through Test testcases.
Common standardised test case template for both Manual and Automation testing.

==============================================================

307. cucumber project template

Cucumber installation / setup =

Help - Ecplise Marketplace - Cucumber eclipse plugin

NOTE - Maven gives skeleton of cucumber - Maven generated template

Cucumber supports quickstart template while creating Maven project

Create Cucumber template though Maven -

New -> Other -> Maven -> Maven project -> Next -> All catalogs -> quickstart template

Add below dependencies in pom.xml file -

cucumber-java, cucumber-junit, cucumber-testng

<dependency>
	<groupId>io.cucumber</groupId>
	<artifactId>cucumber-java</artifactId>
	<version>6.10.4</version>
</dependency>
<dependency>
	<groupId>info.cukes</groupId>
	<artifactId>cucumber-junit</artifactId>
	<version>1.2.6</version>
	<type>pom</type>
	<scope>test</scope>
</dependency>
<dependency>
	<groupId>io.cucumber</groupId>
	<artifactId>cucumber-testng</artifactId>
	<version>6.10.4</version>
</dependency>

==============================================================

Cucumber is a Behavior Driven Development (BDD) framework tool to write test cases.

Given � When � Then Approach

Given: What you have need to perform action (Preconditions)
When: Some Action is performed (Actions)
Then: The desired outcome for the user (Result / validation).

Sample Feature File
Feature: BDD implementation using Cucumber

Scenario: Login to G-mail using Cucumber plugin

Given - User is navigating to G-mail Login Page
When - User need to enter username as "Username" and password as "Password"
Then - User is successfully navigated to the G-mail Mail Box
And - If we want to add multiple tests 

==============================================================

309. Understanding Cucumber Framework terminologies

1. Feature file - All given, when, then scenarios we can write in feature file - define all test cases
Feature file extension should be .feature
We use Gherkin language in feature file
Install Gherkin plugin - Natural plugin
http://rlogiacco.github.io/Natural

Gherkin is a Business Readable, Domain Specific Language created especially for behavior descriptions.
Note - Should not gap beetween Feature / Scenario and : => Feature:

2. stepDefination file - scenario definition - Every scenario written in 
feature file must be define in stepDefination file - How to automate in step definition
Step definition file matches with Tagname and Description 

TidyGherkin - Convert feature file into stepDefinition file - chrome plugin app

3. Junit testRunner - Will run test cases
We can run tests using Junit give reference of Feature file and stepDefination in testRunner
To give reference of Feature file and stepDefination in testRunner use below annotations

		@RunWith(Cucumber.class)
		@CucumberOptions(  
			// single feature file execution
			// features = "src/test/java/features/Login.feature",
	    	features = "src/test/java/features",
	    	glue="stepDefinations"
	    )

- If we will give specific feature file name then it will execute only this
- If we will give features path then it will execute all inside this 
- testRunner and  cucumberOptions package should have same parent
- glue - need to give only package name of stepDefination file

Cucumber project setup -

Try to create all files inside same package

src/test/java 
 	features (package)
		Login.feature
	stepDefinition (package)
		

==============================================================

313. Importance of Regular expressions in feature files

Create stepDefination file using feature file without using any plugin

- Right click on testRunner file then in console we can see stepDefinations just need to add code

- We can pass hard code values in .feature file with regular expressions in stepDefinition file
- Cucumber consider values within "" as dynamic
- Regular expression for same implementation but different data

e.g. -

// .feature file
When User enters "user" and "pass" and logs in

// stepDefinition file
@When("^User enters \"([^\"]*)\" and \"([^\"]*)\" and logs in$")
	public void user_enters_something_and_something_and_logs_in(String strArg1, String strArg2) throws Throwable {
	}

==============================================================

317. Add page objects and handle dynamic popups in home page

318. Parameterizing Selenium tests with Cucumber

Cucumber parameterization -

- To run test cases with multiple diff parameter combinations

Question - How to pass parameters in .feature file
Question - Diff between or when we use Scenario: / Scenario Outline: in .feature file
Answer - For parameterization we use Scenario Outline: in .feature file

Question - Where we define parameters in .feature file / using which keyword
Answer - Using Examples: keywork we define parameters in .feature file

Question - In which symbol / bracket we put argumnets
Answer - Inside angle brackets we put parameters / arguments : <username>

// .feature file

Scenario Outline: Positive test validating login

When User enters <username> and <password> and logs in

Examples:
|username			|password	|
|test99@gmail.com	|123456		|
|test123@gmail.com	|12345      |

==============================================================

319. Integrate Cucumber with TestNG and Maven

- TestRunner class extends with AbstractTestNGCucumberTests abstract class
- AbstractTestNGCucumberTests abstract class will help to run cucumber tests using TestNG

==============================================================
