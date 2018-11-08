# TDD Microservices API with Flask, Docker, TDD, EC2.
microservices with flask, docker, aws, tdd, etc.

[![Build Status](https://travis-ci.org/kevincw0/testdriven-app.svg?branch=master)](https://travis-ci.org/kevincw0/testdriven-app)


1. Introduction (Part 1, Lesson 1) 
    1. Reproducible Development Env with Docker
    2. Create a RESTful API powered by Python, Postgres, and Flask
    3. Deploy it to Amazon EC2 Instance
2. Prerequisites
    1. Docker 
        1. Images and Containers
        2. Image : package includes everything need to run an app (env variables, config, libraries) 
        3. Container: discrete process - no more memory than other executable, runs natively on Linux vs. VM (“guest”)
    2. Docker Compose
        1. Tool for defining and running multi-container docker apps
    3. Docker Machine
        1. Docker Machine is a tool that lets you install Docker Engine on virtual hosts, and manage the hosts with
        2. Deploy to EC2 Instance
    4. Flask
3. Objectives
    1. Build RESTful APIs with Flask
    2. Practice Test-Driven Development (TDD)
    3. Config and run services with Docker
    4. Utilize Volumes to Mount code into container
    5. Run unit and integration tests inside Docker Container
    6. Enable services running in different containers to talk to one another
    7. Work with Python and Flask running inside a Docker Container
    8. Install Flask, Nginx, and Gunicorn on Amazon EC2 Instance
    9. Deploy to EC2 using Docker Machine
4. Endpoints:
    1. /users GET
    2. /users/:id GET
    3. /users POST
    4. /users/ping
5. App is running in three containers
    1. Flask
    2. Postgres
    3. Nginx 
    4. Future:
        1. Add authentication + other services
6. Dependencies
    1. Python, Flask, Docker, Compose, Machine, Flask-SQLAlchemy, psycopg2, Flask-Testing, Gunicorn, Nginx, Bulma

### Microservicees

Microservice Architecture - provides a means of breaking apart large applications into smaller services that interact and communicate with each other. 
- Each service has independent deliverables 
- Each one can be deploy, upgraded, scaled, and replaced on their own, separate from own
- Communication between services usually happens over a network connection through HTTP calls (request/response), web sockets, message queues, and remote procedure calls (RPC) can be used to connect standalone components

- Each individual service performs a single task, separated from a business unit, governed by its RESTful contract

Less about the why and more about the how. MIcroservices are hard. Present a number of challenges and issues that are very difficult to solve. Keep this in mind before start breaking apart monolith.

Pros 
1. Separation of Concerns
2. Smaller Code Bases
3. Accelerated Feedback Loops

1. Separation of Concerns
    1. Clear separation between services - free to focus on their own areas of expertise, like languages, frameworks, dependencies, tools, and build pipelines
    2. Example:
        1. JavaScript Engineer (Front-End) build client-facing views without ever understanding code in backend API - free to use languages frameworks of choice - AJAX requests to consume RESTful API
        2. Treat service like a black box since services communicates via APIs
        3. Actual implementation and complexity are hidden
    3. Organization-wide standards 
        1. Each team can work and function together
        2. Code quality, style checking, code reviews
        3. API Design
    4. Clear separation means that errors are mostly localized to the service developer working on
        1. Assign a junior developer to a less critical service - so that if he/she brings down that service - remainder not affect
    5. Less coupling makes scaling easier 
        1. Each service can be deployed separately
        2. Helps to eliminate one team having to wait on another team to finish up work
2. Smaller Code Bases
    1. Smaller code bases tend to be easier to understand since you do not have to grasp the entire system
    2. Necessity for solid API design, means that apps in a micro service stack faster to develop, test, refactor and scale
    3. Consistent coding standards across all services
3. Accelerated Feedback Loops
    1. Engineers often own entire lifecycle of the app - from inception to delivery
    2. Product-focused, responsible for delivering app to customers 
    3. Fix bugs and iterates

Cons
1. Design Complexity
    1. No easy task to split off a piece of app into micro service
    2. Easier to refactor Into a separate module within monolith than splitting it out
    3. Split out a service, no going back
2. Network Complexity
    1. Monolith no need for inter-service communication
    2. Network before when you needed a function call
    3. Problems: multiple services need to communicate one another - ping-pong like effect in network effects
3. Infrastructure
    1. Multiple services -> Complexity from codebase to infrastructure and platform (costly) 
4. Data Persistence
    1. App - Stateful layer (DB or Task Queues)
    2. Microservices keep. Track of where services are deployed and total number of deployed instances
        1. New instance of a service is stood up - traffic can be re-routed
        2. Service Discovery
    3. Containers - special care in how we handle stateful containers since they should not come down
    4. Isolating particular service’s state - not shared or duplicated is difficult 
5. Integration Tests
    1. Microservice architecture - during development cannot fully test out all services until deploy to a staging or production server. 
    2. Take too long to get feedback
    3. Docker helps speed up process by making it easier to link small, independent services locally
    4. Logging, monitoring, and debugging are much more difficult as well

Testing Strategies:

https://martinfowler.com/articles/microservice-testing/#definition


### App Overview
App Overview
- Code Evaluation tool for grading code exercises
- Similar to codecademy (Python, Flask, JS, React)

App:
- Login, Submit solutions to coding problems
- Feedback: correct or not

Design Pattern: Twelve-Factor App Methodology 
- 12 Best practices for building modern, cloud-native apps apps
    - Codebase, Depende
- Methodology for building SaaS that
    - Declarative Formats - automation, minimize new developers joining
    - Clean contract
    - Deployment and cloud
- The twelve-factor methodology can be applied to apps written in any programming language, and which use any combination of backing services (database, queue, memory cache, etc).
- https://aws.amazon.com/blogs/compute/applying-the-twelve-factor-app-methodology-to-serverless-applications/
- https://12factor.net/ 

Test-Driven Development (TDD)
- Writing tests first when it makes sense to do so
- Server-side unit, functional, and integration tests
- Client-side unit tests
- E2E tests to ensure system works as expected 

App: 
- Reverse Proxy (Nginx) 
- E2E Tests (Cypress), Users (Flask), Exercises (Flask), API Docs(Swagger), Client (React.js)
- AWS Lambda, API Gateway, Scores (Flask), Database (Postgres) 

Dive into docker and container orchestration to help manage, scale, and deploy our fleet of micro services
