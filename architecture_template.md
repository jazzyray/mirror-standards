# Architecture Markdown Template

Author: Jem Rayfield

Markdown template based on artefacts required for 

# Table of contents
1. [Introduction and Goals](#introduction)
	* [Requirements Overview] (#requirements_overview)
	* [Quality Goals] (#quality_goals)
	* [Stakeholders] (#stakeholders)
2. [Architecture Constraints](#archconstraints)
3. [System Context](#systemcontext)
    * [Context](#context)
4. [Solution] (#solution)
	* [Motivation] (#solution_motivation)
	* [Important Interfaces] (#solution_important_interfaces)
	* [Container View] (#container_view)
		* [{Name} Container 1] (#container_1)
		* [{Name} Container 2] (#container_2)
		* [{Name} Container n] (#container_n)
	* [Component View] (#component_view)
		* [{Name} Component 1] (#component_1)
			* [{Name} Component Interface 1] (#component_interface_1)
		* [{Name} Component 2] (#component_2)
			* [{Name} Component Interface 2] (#component_interface_2)
		* [{Name} Component n] (#component_n)
			* [{Name} Component Interface n] (#component_interface_n)
	* [Sequence View] (#sequence_view)
		* [Scenario 1] (#scenario_1)
		* [Scenario 2] (#scenario_2)
		* [Scenario n] (#scenario_n)
	* [Deployment View] (#deployment_view)
		* [Infrastructure Level 1](#infrastructure_level_1)
		* [Infrastructure Level 2](#infrastructure_level_2)
5. [Design Decisions] (#design_decisions)
6. [Quality/Acceptance Requirements] (#quality_requirements)
	* [Quality/Acceptance Scenarios] (#quality_acceptance_scenarios)
7. [Risks and Technical Debt] (#risks_and_tech_debt)
8. [Glossary](#glossary)

<a name="introduction"></a>
# Introduction and Goals 
<a name="requirements_overview"></a>
## Requirements Overview 
| Requirement   | Expectation     | Priority.      |
|:------------- |:---------------:| :-------------:|
| Requirement 1 | Expectation 1.  | low            | 
| Requirement 2 | Expectation 2.  | medium         |
| Requirement 2 | Expectation 2.  | high           |
<a name="quality_goals"></a>
## Quality Goals  
<a name="stakeholders"></a>
## Stakeholders 

| Role/Name     | Contact.        | Expectations  |
|:------------- |:---------------:| -------------:|
| Role 1        | Contact 1.      | Expectation 1 |
| Role 2        | Contact 2.      | Expectation 2 |

<a name="archconstraints"></a>
# Architecture Constraints 
<a name="systemcontext"></a>
# System Context 
<a name="context"></a>
## Context 
**&lt;Diagram or Table&gt;**

**&lt;optionally: Explanation of external domain interfaces&gt;**

**&lt;optionally: Explanation of technical interfaces&gt;**

**&lt;Mapping Input/Output to Channels&gt;**
<a name="solution"></a>
# Solution 
<a name="solution_motivation"></a>
## Motivation

   *&lt;text explanation&gt;*

   *&lt;Description of containers&gt;*
<a name="solution_important_interfaces"></a>
## Important Interfaces

   *&lt;Description of important interfaces&gt;*

<a name="container_view"></a>
## Container View

***&lt;Overview Diagram&gt;***

   
<a name="container_1"></a>
###{Name} Container {1}

*&lt;Purpose/Responsibility&gt;*

*&lt;Interface(s)&gt;*

*&lt;(Optional) Quality/Performance Characteristics&gt;*

*&lt;(Optional) Directory/File Location&gt;*

*&lt;(Optional) Fulfilled Requirements&gt;*

*&lt;(Optional) Open Issues/Problems/Risks&gt;*

<a name="container_2"></a>
###{Name} Container {2}

*&lt;Purpose/Responsibility&gt;*

*&lt;Interface(s)&gt;*

*&lt;(Optional) Quality/Performance Characteristics&gt;*

*&lt;(Optional) Directory/File Location&gt;*

*&lt;(Optional) Fulfilled Requirements&gt;*

*&lt;(Optional) Open Issues/Problems/Risks&gt;*

<a name="container_n"></a>
###{Name} Container {n}

*&lt;Purpose/Responsibility&gt;*

*&lt;Interface(s)&gt;*

*&lt;(Optional) Quality/Performance Characteristics&gt;*

*&lt;(Optional) Directory/File Location&gt;*

*&lt;(Optional) Fulfilled Requirements&gt;*

*&lt;(Optional) Open Issues/Problems/Risks&gt;*

<a name="component_view"></a>
## Component View


<a name="component_1"></a>
###{Name} Component {1}

*&lt;Purpose/Responsibility&gt;*

*&lt;Interface(s)&gt;*

*&lt;(Optional) Quality/Performance Characteristics&gt;*

*&lt;(Optional) Directory/File Location&gt;*

*&lt;(Optional) Fulfilled Requirements&gt;*

*&lt;(Optional) Open Issues/Problems/Risks&gt;*

<a name="component_interface_1"></a>
#### {Name} Component Interface {1})

<a name="component_2"></a>
###{Name} Component {2}

*&lt;Purpose/Responsibility&gt;*

*&lt;Interface(s)&gt;*

*&lt;(Optional) Quality/Performance Characteristics&gt;*

*&lt;(Optional) Directory/File Location&gt;*

*&lt;(Optional) Fulfilled Requirements&gt;*

*&lt;(Optional) Open Issues/Problems/Risks&gt;*

<a name="component_interface_2"></a>
#### {Name} Component Interface {2})

<a name="component_n"></a>
###{Name} Component {n}

*&lt;Purpose/Responsibility&gt;*

*&lt;Interface(s)&gt;*

*&lt;(Optional) Quality/Performance Characteristics&gt;*

*&lt;(Optional) Directory/File Location&gt;*

*&lt;(Optional) Fulfilled Requirements&gt;*

*&lt;(Optional) Open Issues/Problems/Risks&gt;*

<a name="component_interface_n></a>
#### {Name} Component Interface {n})

<a name="sequence_view"></a>
## Sequence View 

<a name="scenario_1></a>
### Scenario 1

-   *&lt;insert sequnce diagram or textual description of the
    scenario&gt;*

-   *&lt;insert sequence diagram of the notable aspects of the interactions
    between the component instances &gt;*

<a name="scenario_2></a>
### Scenario 2

-   *&lt;insert sequnce diagram or textual description of the
    scenario&gt;*

-   *&lt;insert sequence diagram of the notable aspects of the interactions
    between the component instances &gt;*
    
<a name="scenario_n></a>
### Scenario n

-   *&lt;insert sequnce diagram or textual description of the
    scenario&gt;*

-   *&lt;insert sequence diagram of the notable aspects of the interactions
    between the component instances &gt;*
    
<a name="deployment_view"></a>
## Deployment View 

<a name="infrastructure_level_1"></a>
### Infrastructure Level 1 

***&lt;Overview Diagram&gt;***

Motivation

:   *&lt;explanation in text form&gt;*

Quality and/or Performance Features

:   *&lt;explanation in text form&gt;*

Mapping of Containers to Infrastructure

:   *&lt;description of the mapping&gt;*

<a name="infrastructure_level_2"></a>
### Infrastructure Level 2

***&lt;Overview Diagram&gt;***

Motivation

:   *&lt;explanation in text form&gt;*

Quality and/or Performance Features

:   *&lt;explanation in text form&gt;*

Mapping of Containers to Infrastructure

:   *&lt;description of the mapping&gt;*

<a name="design_decisions"></a>
# Design Decisions 

:   *&lt;Links to approach documents and decisions.&gt;*

<a name="quality_requirements"></a>
# Quality/Acceptance Requirements 

<a name="quality_acceptance_scenarios"></a>
## Quality/Acceptance Scenarios 

<a name="risks_and_tech_debt"></a>
# Risks and Technical Debt

<a name="glossary"></a>
#Glossary

| Term          | Definition         | 
|:------------- |:------------------:|
| Term 1        | Definition 1       | 
| Term 2        | Definition 2       | 


