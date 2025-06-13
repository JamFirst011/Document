# Architecure-Driver Design Method

和Stategy的不同点，即策略是为了实现Architecture-drivers的指导性技术或方法，是概念性的，灵活的；设计方法是一套具体的，结构化的流程或技术，来指导架构师完成整个设计过程；

Why is design method indispensable: because design is difficult, need extensive knowledge and existing solutions, but design method provide a chance to design in a systematic way, to ensure decision are recorded, justified ...

And ADD Create a high - quality, predictable, and reusable software architectures through a systematic approach

**ADD supports iterative rounds within project increments like sprints, enabling structured design through micro-iterations**, the detailed steps are as follows, note that iteration include step 2-7:

## Step1: review Inputs

Check if any important stakeholders are overlooked or business condition has changed, then get the drivers and prioritize them right

## Step2: Establish iteration goal by selecting drivers

design problems has been divided into sub-prolblems, and iteration started by deciding which sub-problem to solve;

A goal means designing to solve a subset of drivers, and ensure the goal is right-sized, in the other word, select proper set of drivers like:
    1. a single import driver
    2. a set of similar drivers
    3. a set of related drivers

## Step3: Refine system element

there are 3 refine approaches:
- Decomposition(top - bottom)
- Combination(bottom - top)
- Improvement of previous identified elements

For greenfield system, you can only choose sole element(system itself) to Decompostion

For existing system or later iteration of greenfield system, you can...

## Step4: Choose concepts that satisfy the iteration goal

How to select:

**Basic Method: create pros-cons table**: list advantage and disadvantage of each alternative concepts

**CBAM**: 

**SWOT**:

**ProtoType**: create throwaway prototype, if project involves new tech

## Step5: Instantiate element, allocate accountability and define interfaces

## Step6: Sketch views and Record design decisions

create sketches after Stpe5 which instantiate design concepts, which is init documentation, and Recording during design ensure you won't have to remenber them

## Step7: Analyse current design, review iteration goal and purpose

Analyse and review to decide whether to take next iteration, use Kanban to track all drivers


## Terminate condition

1. decisions are made for all drivers
2. main tech risk has been mitigated
3. time runs out...



