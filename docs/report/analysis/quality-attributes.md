---
sidebar-position: 3
---


# Quality Attributes


Quality attributes are the non-functional requirements that define the overall quality of the system and how it delivers its functionalities.


We have identified the following quality attributes for our system:


## Quality Attributes Overview


### Operational Properties

1. **Availability**:
   - Fault tolerance: The system should be able to recover from failures and continue to operate.
   - Redundancy: The system should have the possibility to use redundant components to ensure availability.
2. **Reliability**:
   - Error handling: The system should be able to handle errors gracefully.
   - Data integrity: The system should ensure that data is consistent and accurate.
3. **Performance**:
   - Response time: The system should respond to user actions promptly.
   - Scalability: The system should be able to handle a growing number of users.
4. **Deployability**:
   - Portability: The system should be able to run on different platforms.
   - Upgradability: The system should automatically deploy new versions.


### Structural Properties

1. **Modifiability**:
   - Extensibility: The system should be able to add new features easily.
   - Maintainability: The system should be easy to maintain and update.
2. **Testability**:
   - Observability: The system should be able to provide information about its internal state.
   - Controllability: The system should be able to be controlled during testing.
3. **Security**:
   - Authentication: The system should be able to authenticate users.
   - Authorization: The system should be able to authorize users to access resources.
   - Data protection: The system should protect sensitive data.
4. **Usability**:
   - Learnability: The system should be easy to learn.
   - Efficiency: The system should be efficient to use.
   - Satisfaction: The system should be satisfying to use.

## Scenarios

For some quality attributes, we have defined scenarios to illustrate how they will be achieved.

### Availability

#### Scenario 1: Fault Tolerance

- **Stimulus Source**: Hardware failure.
- **Stimulus**: A server node fails.
- **Environment**: Normal operation.
- **Artifact**: Server node.
- **Response**: The system detects the failure and redirects the traffic to another server node.


### Reliability

#### Scenario 1: Error Handling

- **Stimulus Source**: User action.
- **Stimulus**: User enters invalid data.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system displays an error message to the user.


#### Scenario 2: Data Integrity

- **Stimulus Source**: User action.
- **Stimulus**: User updates their profile.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system updates the user's profile without data loss.


### Performance


#### Scenario 1: Response Time

- **Stimulus Source**: User action.
- **Stimulus**: The user clicks on a button.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system responds to the user's action within 1 second.


### Deployability


#### Scenario 1: Portability

- **Stimulus Source**: Deployment.
- **Stimulus**: Deploy the system on a new platform.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system runs on the new platform without modification.


#### Scenario 2: Upgradability

- **Stimulus Source**: Deployment.
- **Stimulus**: Deploy a new version of the system.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system automatically deploys the new version.


### Modifiability

#### Scenario 1: Extensibility

- **Stimulus Source**: New feature request.
- **Stimulus**: Add a new feature to the system.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The new feature is added to the system without affecting existing features.


#### Scenario 2: Maintainability

- **Stimulus Source**: Bug report.
- **Stimulus**: Fix a bug in the system.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The bug is fixed without introducing new bugs.


### Testability

#### Scenario 1: Observability


- **Stimulus Source**: Testing.
- **Stimulus**: Monitor the system during testing.
- **Environment**: Testing.
- **Artifact**: System.
- **Response**: The system provides information about its internal state.


#### Scenario 2: Controllability


- **Stimulus Source**: Testing.
- **Stimulus**: Control the system during testing.
- **Environment**: Testing.
- **Artifact**: System.
- **Response**: The system can be controlled during testing.


### Security


#### Scenario 1: Authentication


- **Stimulus Source**: User action.
- **Stimulus**: User logs in to the system.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system authenticates the user.


#### Scenario 2: Authorization

- **Stimulus Source**: User action.
- **Stimulus**: User accesses a protected resource.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system authorizes the user to access the resource.


#### Scenario 3: Data Protection

- **Stimulus Source**: User action.
- **Stimulus**: User enters sensitive data.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system encrypts the sensitive data.


### Usability


#### Scenario 1: Learnability

- **Stimulus Source**: User action.
- **Stimulus**: User interacts with the system for the first time.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The user learns how to use the system within 5 minutes.


#### Scenario 2: Efficiency

- **Stimulus Source**: User action.
- **Stimulus**: User performs a task.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The system allows the user to perform the task quickly.


#### Scenario 3: Satisfaction

- **Stimulus Source**: User action.
- **Stimulus**: User interacts with the system.
- **Environment**: Normal operation.
- **Artifact**: System.
- **Response**: The user enjoys using the system.

