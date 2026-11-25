Category 1: JUnit – Unit Testing
A. JUnit Fundamentals
1. What is JUnit, and why is it used in Java application development?
2. How is JUnit 5 different from JUnit 4?
3. What are the advantages of automated unit testing?
4. What makes a good unit test?
B. JUnit Annotations and Test Lifecycle
5. What are the different lifecycle annotations in JUnit 5?
6. What is the execution order of @BeforeAll, @BeforeEach, @Test, @AfterEach, and @AfterAll?
7. What is the purpose of @DisplayName?
8. What is the use of @Nested annotation?
9. What is the purpose of @Tag annotation?
10. How do you skip a test or execute it only under certain conditions?
C. JUnit Assertions and Testing
11. How do you test whether a method throws an exception?
12. What is the difference between assertEquals(), assertSame(), and assertAll()?
13. What are parameterized tests in JUnit 5?
14. How do you test methods that return void?
15. How do you test a method that accepts multiple input parameters?
D. JUnit with Mockito
16. What is Mockito, and why is it used along with JUnit?
17. How does JUnit work with Mockito?
18. What is the difference between @Mock and @InjectMocks?
19. What is the purpose of @ExtendWith(MockitoExtension.class)?
20. What is the difference between when(), thenReturn(), and verify()?

Category 2: Maven – Fundamentals
A. Introduction to Maven
1. What is Apache Maven? What are its advantages over traditional Java project development?
2. What is the POM.xml file in Maven? What information does it contain?
3. What is the difference between Maven and Apache Ant?
4. What are the advantages of using Maven in enterprise Java projects?
5. What is a Maven dependency? How does Maven resolve and download dependencies?
B. Maven Repositories
6. Explain the different types of Maven repositories:
- Local Repository
- Central Repository
- Remote Repository
7. Where does Maven store downloaded dependencies locally?
8. What is the default location of the Maven local repository?
9. What happens when Maven cannot find a dependency in the local repository?
10. How do you configure a custom remote repository?
C. Maven Dependency Management
11. What is the difference between dependencies and dependencyManagement in Maven?
12. How do you add an external JAR dependency to a Maven project?
13. What is transitive dependency in Maven?
14. How do you resolve a dependency conflict in Maven?
15. What is the difference between SNAPSHOT and RELEASE versions in Maven?

Category 3: Maven – Build Lifecycle and Commands
A. Maven Build Lifecycle
1. What are Maven build lifecycles? Explain the three main lifecycles:
- Clean
- Default
- Site
2. What is the difference between a lifecycle, phase, and goal?
3. What are the important phases of the Default Lifecycle?
4. What is the difference between validate, compile, test, package, verify, install, and deploy?
5. What happens internally when you execute mvn clean install?
6. Why does Maven delete the target directory during the clean phase?
B. Maven Commands
7. What is the difference between the following Maven commands?
- mvn compile
- mvn test
- mvn package
- mvn install
8. Does mvn package execute JUnit test cases?
9. What is the difference between mvn install and mvn deploy?
10. Can we execute a Maven plugin goal without executing the entire lifecycle?
11. How do you execute a specific test class using Maven?
12. How do you skip test execution while building a Maven project?
13. What is the difference between -DskipTests and -Dmaven.test.skip=true?
14. What is the purpose of mvn clean install?
15. What is the purpose of mvn dependency:tree?

Category 4: Java Logging and Logging Levels
A. Logging Fundamentals
1. What is logging in Java? Why is logging important in application development?
2. What is the difference between System.out.println() and a logging framework?
3. What are the advantages of using logging instead of System.out.println()?
4. What are the popular logging frameworks available in Java?
   - Java Util Logging (JUL)
   - Log4j
   - Logback
   - SLF4J
5. What is SLF4J? How is it different from Log4j and Logback?
6. What is the difference between logging and exception handling?
7. How do you implement logging in a Java application?
B. Logging Levels
8. What are the different logging levels in Java?
9. Explain the following logging levels with suitable examples:
   - TRACE
   - DEBUG
   - INFO
   - WARN
   - ERROR
   - FATAL (Log4j)
10. What is the difference between DEBUG and INFO logging levels?
11. What is the difference between WARN and ERROR logging levels?
12. What is the difference between TRACE and DEBUG?
13. What happens when the logging level is configured as INFO? Which messages will be displayed?
14. Can we change the logging level without modifying the Java source code?
C. Logging Configuration and Advanced Concepts
15. How do you configure logging in a Spring Boot application using application.properties?
16. How do you configure different logging levels for different packages?
17. How do you write logs into a file instead of displaying them on the console?
18. What is log rotation? Why is it important in enterprise applications?
19. What is the difference between synchronous and asynchronous logging?
20. What are the best practices for logging in enterprise applications?
