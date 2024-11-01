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

## Authenticated User

After the user is authenticated, it can perform numerous actions such as:

- Logout
- Modify its profile
- Create a new session
- Join a session
- Look at another user's profile

![Authenticated User](/img/analysis/business-requirements/authenticated-user.svg)

1. **Logout**

   - **Actor**: Authenticated User
   - **Preconditions**: User is authenticated in the system.
   - **Postconditions**: User is not authenticated in the system.
   - **Main Success Scenario**
     1. User accesses the logout page.
     2. User clicks on the logout button.
     3. System logs out the user.
     4. System redirects the user to the login page.

2. **Modify Profile**

   - **Actor**: Authenticated User
   - **Preconditions**: User is authenticated in the system.
   - **Postconditions**: User's profile is updated.
   - **Main Success Scenario**
     1. User accesses the profile page.
     2. User fills in the profile form.
     3. User submits the profile form.
     4. System validates the profile form.
     5. System updates the user's profile.
   - **Extensions**
     - **A1**: User submits an invalid profile form.
       1. System displays an error message.
       2. The user returns to step 2 and corrects the form.

3. **Create Session**

   - **Actor**: Authenticated User
   - **Preconditions**: User is authenticated in the system.
   - **Postconditions**: Session is created.
   - **Main Success Scenario**
     1. User accesses the create session page.
     2. User fills in the session form.
     3. User submits the session form.
     4. System validates the session form.
     5. System creates the session.
     6. System redirects the user to the session page.
   - **Extensions**
     - **A1**: User is already in a session.
       1. System displays an error message.
       2. The user goes back to the home page.
     - **A2**: User submits an invalid session form.
       1. System displays an error message.
       2. The user returns to step 2 and corrects the form.

4. **Join Session**

   - **Actor**: Authenticated User
   - **Preconditions**: User is authenticated in the system.
   - **Postconditions**: User is in the session.
   - **Main Success Scenario**
     1. User accesses the join session page using the session url.
     2. System validates the session url.
     3. System adds the user to the session.
     4. System redirects the user to the session page.
   - **Extensions**
     - **A1**: User is already in a session.
       1. System displays an error message.
       2. The user goes back to the home page.
     - **A2**: User accesses an invalid session url.
       1. System displays an error message.
       2. The user goes back to the home page.

5. **Look at Another User's Profile**
   - **Actor**: Authenticated User
   - **Preconditions**: User is authenticated in the system.
   - **Postconditions**: User is looking at another user's profile.
   - **Main Success Scenario**
     1. User accesses another user's profile page.
     2. System displays the user's profile.
   - **Extensions**
     - **A1**: User accesses an invalid user's profile.
       1. System displays an error message.
       2. The user goes back to the home page.
     - **A2**: User accesses its own profile.
       1. System redirects the user to its profile page.
     - **A3**: User accesses a non-existing user's profile.
       1. System displays an error message.
       2. The user goes back to the home page.

## User in a Session

When the user is in a session, it can perform actions such as:

- Leave the session
- Send a message
- Play the video
- Pause the video
- Move the video to a specific time

![User in a Session](/img/analysis/business-requirements/user-session.svg)

1. **Leave Session**

   - **Actor**: User in a Session
   - **Preconditions**: User is in a session.
   - **Postconditions**: User is not in the session.
   - **Main Success Scenario**
     1. User clicks on the leave session button.
     2. System removes the user from the session.
     3. System redirects the user to the home page.

2. **Send Message**

   - **Actor**: User in a Session
   - **Preconditions**: User is in a session.
   - **Postconditions**: Message is sent.
   - **Main Success Scenario**
     1. User fills in the message form.
     2. User submits the message form.
     3. System sends the message to the session.
     4. System displays the message in the session.

3. **Play Video**

   - **Actor**: User in a Session
   - **Preconditions**: User is in a session.
   - **Postconditions**: Video is playing.
   - **Main Success Scenario**
     1. User clicks on the play button.
     2. System plays the video.

4. **Pause Video**

   - **Actor**: User in a Session
   - **Preconditions**: User is in a session.
   - **Postconditions**: Video is paused.
   - **Main Success Scenario**
     1. User clicks on the pause button.
     2. System pauses the video.

5. **Move Video to a Specific Time**
   - **Actor**: User in a Session
   - **Preconditions**: User is in a session.
   - **Postconditions**: Video is moved to a specific time.
   - **Main Success Scenario**
     1. User fills in the time form.
     2. User submits the time form.
     3. System moves the video to the specific time.
