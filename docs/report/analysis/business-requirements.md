---
sidebar_position: 3
---

# Business Requirements

Business requirements for the LetsStreamIt project are described using use cases diagrams and a textual description.

## User Login/Registration

![User Login/Registration](/img/analysis/business-requirements/login-registration.svg)

A user who accesses the system must be able to:

1. **Register a new account (Sign Up)**

   - **Actor**: User
   - **Preconditions**: User is not registered in the system.
   - **Postconditions**: User is registered in the system.
   - **Main Success Scenario**
     1. User accesses the registration page.
     2. User fills in the registration form.
     3. User submits the registration form.
     4. System validates the registration form.
     5. System registers the user.
     6. System redirects the user to the login page.
   - **Extensions**
     - **A1**: User submits an invalid registration form.
       1. System displays an error message.
       2. The user returns to step 2 and corrects the form.
     - **A2**: User submits a registration form with an existing email.
       1. System displays an error message.
       2. The user returns to step 2 and enters a different email.

2. **Login**
   - **Actor**: User
   - **Preconditions**: User is registered in the system.
   - **Postconditions**: User is authenticated in the system.
   - **Main Success Scenario**
     1. User accesses the login page.
     2. User fills in the login form.
     3. User submits the login form.
     4. System validates the login form.
     5. System authenticates the user.
     6. System redirects the user to the home page.
   - **Extensions**
     - **A1**: User submits a login form with incorrect credentials.
       1. System displays an error message.
       2. The user returns to step 2 and enters the correct credentials.
