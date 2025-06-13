# Architectural Drivers and Design Strategy

The state of software architecture is a set of structures, which comprise software elements, relationship between them and properties of both;The activities is that Architect uses Design purpose, functionality, Quality attributes, constraints and concerns, along with their Design Concepts to produce Structures

## Architecture Drivers

They are input to design process:
- Function requirements: primary funcionality
- Quality attributes: Measurable Characteristics, specified using scenario technique;have two kinds of priority: importance to success of system by users and technical risk by architect(H,M,L)
- Constraints: Time, Budget, Technical limitation, Business rules and regulation
- The type of System: include greenfield system in novel domains and mature domains, it require more/less innovation which shape the software architecture
- Design Objectives: Be clear about your purpose, such as for pre-sales proposal, or custom system with certain constraints, or continuously evolving system
- Concerns: The factor which is not expressed as traditional requirements, include:
    1. General Concerns: overall system structure
    2. Specific Concerns: more detailed, internal issues like Logging, API version
    3. Internal requirements: technical requirements the customers don't know, like program language, platform
    4. Issues: like security risk and performance bottleneck

## Design Strategy

1. **Decomposition**: 
2. **Design to ASRs**: ASRs means significant requirements, like main funcionality or some quality attributes; You are about to use your intuition to design, when architecture meet ASRs, maybe some non-ASRs are not meet, thus you could: 
    1. make slight adjustment
    2. reprioritize the requirements and revisit the design
    3. regenerate when current design cannot meet non-ASRs thouroughly
3. **Generate and Test**: make a hypothesis first, and test and then fix wrong thing of current hypothesis to produce next hypothesis and repeat this hook, till the design meet all ASRs or the budget is exhausted.(first hypothesis come from existing system, frameworks or ...)

## Design Concepts

Use concepts to solve problems as existing solution to avoid reinventing the wheel, such as:

### Reference Architectures

A blueprint for structuring an application for many kinds of application like Mobile, Rich client...

### Deployment patterns

provide a guidance on how to structure the system from physical standpoint, such as load balanced cluster, to achieve quality attributes such as availablity

### Tactics

The tactic of quality attributes, which is used to achieve these attributes

### Patterns

Design patterns which in the former chapters, provide solution to recurring problems, originated from building architecture;

### Externally developed components

The framework, the reusable code solutions which provide generic functionality
