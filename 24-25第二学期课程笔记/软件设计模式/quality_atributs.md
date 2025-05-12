## Quality attributes

Requirements includes three specific requirement below: 

### Functional requirements

state: what the system must do and how the system provice value for stakeholders, it means the behavior of system.

### Constraints

A constrains is a pre-specified decisions that the system MUST comply with, and they are satisfied by accepting the 
design decision and reconciling it with other affected decisions

### Quality requirements/attributes

**state**: quality requirements is the qualification of the functional requirement, if the quality requirement is important, then software architecture should constrains the allocation of functional onto various structure, like a system must handle 5000 requests per second.

**quality attibutes**: same as quality requirements, but is expressed in a different abstract remedy like performance, security etc.

**non-functional requirements**: an alternative term of quality requirements, must be considered during any decision. there two broad category of non-function reuqirements:
- **Observable during execution**: how well a system satisfied its funcional requirements like performance, availibility...
- **Not observable during execution**: how easily a system can be mantained like modifiability, reusability...

**Quality attibutes**: it is over system's functionality, a system is often re-design because they lack a desirable level of quality. software architecture constrains the achievement of quality, so software is considered as most proper level of addressing quality issue.

### Scenarios

**Specifying quality attibutes**: we need precise definition of quality attribute to evaluate at architecture level.
so we use **Scenarios** to describe quality attributes which has a certain structure. There are two categories of scenarios:
- **General Scenarios**: system independent, a framework to guide the specification of quality attributes
- **Concrete Scenarios**: a specific scenarios for particular system, a instance of general scenarios

**General Scenarios Model**: it include below proportion:
- Stimulus: A condition that needs to be considered when ti arrives at a system.
- Source of Stimulus: An entity (human, system, or any actuator) that generates the stimulus.
- Response: The activity undertaken after the arrival of the stimulus.
- Response Measure: The response to the stimulus should be measurable in some fashion so that the requirement can be testable.
- Environment: Asystem's condition when a stimulus occurs, e.g., overloaded, running etc.
- Artifact: The whole system or the portion of the system ot which the requirement applies.

### Tactics

a design decision, like redundancy, to meet specific quality attribute. A system design consist of a collection of tactics/design decision: some of these helo control quality attribute response, and others are used to achieve functionality.

**Property**: 
1. Tactics can be composed of other tactic, e.g: redundancy may be composed to redundancy of data or computation
1. Tactics can be used as **hierarchy tactic**(ChatGPT: Tactics can be organized in a hierarchy, where high-level design goals are supported by layered or combined lower-level tactics.)

**Conclusion**: that is to say, a quality attributs correspond to a general scenario which intend to define the quality attribute and a tactic which intend to achieve quality attribute


## Specific Quality Attributes

### Availability

**state**: key requirement, measured by proportion of requirement time it is usable, related to system's relliability. the specific calculating format is(the scheduled downtime is not considered):
- MTBF(mean time between failure)
- MTTR(mean time to repair)
- Availability = $\frac{MTBF}{MTBF+MTTR}$

**loss**: time to detect and correct failure, and the time to restart application

**strategy**: 
- eliminate single point of failure
- replication and failover
- automatic detection and recovery

**Fault,Error and Failure**
1. Failure is a observable characristics of system'state, it occurs when system can't provide service
1. Fault is the cause of Failure, it is potential in system design or implementation
1. Error is intermediate state between Fault and Failure, if the Error is not fixed timely, it will cause Failure

**General Scenario**
1. Source: people, hardware...
1. Stimulus: fault like memory leak, crash...
1. Artifact/Environment: ...
1. Response: prevent fault to become a failure, detect the fault and recover it
1. Response Measure: downtime to detect and recover

**Tactic**

1. **Detect Fault**:
    - Ping/Echo
    - Heartbeat
    - Exception
1. **Recover**:
    - Vote
    - Active redundancy
    - Spare
    - ...
1. **Prevent**:

***

### Interoperability

1. **state**: the degree to which two or more system can usefully exchange information. Interoperability needs to identify with whom, with what, and under what circumstances (the context). include two abilities:
- Ability to excahnge data
- Ability to interpret the data

2. **two important part**:
- Discovery: consumers of service must find the location, interfaces...about the service
- Handling: how service handle consumers' requests, there are three ways below:
    1. reports back to requester
    1. send the request to another system
    1. broadcast the request to any interested parties

**General Scenarios**

1. **Stimulus**: a request to exchange information
1. **Response**: reject or response to request
1. **Response Measure**: the percentage of correct rejection and correct response

**Tactics**

1. **Locate**:
1. **Manage interfaces**

***

### Modifiability

**State**: measure the cost of **CHANGE** in time or money, include the extent to which this change affects other 
functionality or quality attributes

**General Scenario**:

- **Source**: developer, system administrator
- **Stimulus**: A directive to add/change/remove a functionality or change quality attribute...
- **Artifact**: Code,data...
- **Response**: Make and Test and Deplore Modification
- **Response Measure**: Cost like time, money, effort, number/size/complexity of affected artifact...

**Tactics**:

- **Split Module**
- **Increase Semantic Coherence**: make sure there is a sole responsibility in a module, if two responsibility in
one module serve different purppose, developer should create a new module or moving a responsibility to an existing module
- **Encapsulation**: set explicit interface and prevent the modification of a module affect another module
- **Refactor** when two modules are affected by the change.
- **Defer Binding**

***

### Performance

**State**: System's ability to meet time requirements(All system has this quality attribute), the response time has two basic factors:
- **Processing time**
- **Blocked time**

**General Scenarios**:
- **Stimulus**: arrival of various kind of event
- **Response**: precess evnet or change level of service
- **Response Measure**: Latency(main), Deadline, Trhoughput, Miss rate

**Tactics**: include two side:
- **Demand side**:
    1. **Reduce sampling frequency**: means reduce the frequency of sampling data from users
    1. **Limit event response**: when discrete event arrive too rapidly, the events must be queued until it can be processed
    1. **Prioritize the event**
- **Resouce side**:
    1. **Increase Resource** like additional memory or faster network
    1. **Introduce Concurrency**
    1. **Use load balancer** to assign new work to available dublicated server
    1. **Maintain multiple copies of data** means use cache

***

### Security

**State**: system's ability to protect data and information from unauthorized access,  Three characteristics of security:
- Confidentiality: data and service are protected from unauthorized access
- Integrity: Data and services are not subject to **unauthorized manipulation**.
- Availability: system will be available for legitimate use

**General Scenario**:
- **Source**: normal user or potential attacker
- **Stimulus**: unauthorized attempt to display or change or delete data, access system service...
- **Response**: data are protected, parties are identified with assurance, and record the access and attemptation
- **Response Measure**: like how much time to detect a potential attack, how many attack were resisted, how much data is vunerable to particular attack...

**Tactics**:
1. Limit access
1. Limit exprosure
1. Encrypt data
1. ...

***

### Testability

**State**: Testability refers to ease with which software can be made to demonstrate its faults through testing.
to a well testable system, it must be possible to control components' input and observe the output

**General Scenario**:
- **Source**: tester
- **Response**: execute test suite and capture result, capture activities which result the fault
- **Response Measure**: effort to find fault, time to precess test, the effectiveness of test, the coverage of test

**Tactics**:
- **Control and Observe system state**: use specialized interface to control and capture data in a component, record the state that caused the fault
- **Limit complexity**: Limit the number of classes from which a class si derived. Limit the depth of the inheritance tree and the number of children of a class. Limit polymorphism and dynamic calls.

### Usability

...
