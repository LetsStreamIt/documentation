---
sidebar_position: 4
---

# Bounded Contexts


The bounded contexts of the system are:


- Auth
- Profile
- Session


In the following sections, each one will be described in detail.
Commands, Events, and Reactions are grouped based on the aggregate they're related to.


## Auth


The authentication context is responsible for managing user authentication to the LetsStreamIt platform. It manages user registration and login.


### Ubiquitous Language


| Term          | Meaning                                  |
| ------------- | ---------------------------------------- |
| User          | Anyone registered to the system          |
| Token         | A unique identifier for a User           |
| Access Token  | A token used to authenticate the User    |
| Refresh Token | A token used to refresh the Access Token |


## Profile


Profile context is responsible for managing the user profile information in the LetsStreamIt platform. It manages the user's username, bio, and watched videos.


### Ubiquitous Language


| Term    | Meaning                         |
| ------- | ------------------------------- |
| User    | Anyone registered to the system |
| Profile | User's profile information      |
| Video   | A Youtube video                 |


## Session


Session Service is the core of LetsStreamIt and is responsible for managing a Youtube streaming session.


It ensures synchronized video playback, in response to play and stop performed by the users. It also manages a chat through which users can communicate with each other while watching the video.


### Ubiquitous Language


| Term                  | Meaning                                                                                   |
|-----------------------|-------------------------------------------------------------------------------------------|
| User                  | Anyone registered to the system                                                           |
| Video                 | A Video is a YouTube video                                                                |
| Video State           | Pair of values representing the current timestamp of the video and if it's Playing/Stopped   |
| Text message          | Texual message sent by a User                                                             |
| Notification message  | Message sent by the context                                                               |
| Chat                  | A Collection of Text Messages                                                             |
| Session               | A group of Users watching a Video and interacting with a Chat                             |


### Commands


#### Session


Commands related to Session aggregate concern Session creation and joining:
- *UserTokenCommand*: sent whenever an actor wants to connect to the context;
- *CreateSessionCommand*: sent whenever a User wants to create a new session;
- *JoinSessionCommand*: sent whenever a User wants to join an existing session;
- *LeaveSessionCommand*: sent whenever a User wants to leave a session.


#### Chat


- *SendMessageCommand*: sent whenever a User wants to send a message in the Chat.


#### Video


- *PlayVideoCommand*: sent whenever a User wants to play the Video;
- *StopVideoCommand*: sent whenever a User wants to stop the Video.


### Events


Events are emitted when commands are accepted and validated by the context.


#### Session


- *SessionCreatedEvent*: triggered whenever a new Session is created;
- *UserJoinedSessionEvent*: triggered whenever a User joined a Session;
- *UserLeftSessionEvent*: triggered whenever a User leaves a Session.


#### Chat


- *MessageSentEvent*: triggered whenever a User has sent a message in the Chat.


#### Video


- *VideoPlayedEvent*: triggered whenever a User has played the Video;
- *VideoStoppedEvent*: triggered whenever a User has stopped the Video;




### Reactions


Reactions are actions that are executed whenever an event occurs.
In the Session context, they correspond to actions performed to communicate back with Users, either single Users or all Users connected to a Session.


#### Session


- *joinUserToSession*: executed whenever the aggregate wants to add the User reference to the list of connected Users;
- *leaveUserFromSessionAndDisconnect*: executed whenever the aggregate wants to remove the User reference from the list of connected Users.


#### Chat


- *emitNotificationToSession*: executed whenever the aggregate wants to emit a Notification Message to the Session;
- *emitTextMessagesToClient*: executed whenever the aggregate wants to emit one or more Text Messages to a single User;
- *emitTextMessagesToSession*: executed whenever the aggregate wants to emit one or more Text Messages to all the Users connected to the Session.


#### Video


- *retreiveVideoState*: executed whenever the aggregate wants to retrieve the Video state from a single User;
- *synchronizeClient*: executed whenever the aggregate wants to synchronize the Video of a single User;
- *syncronizeSession*: executed whenever the aggregate wants to synchronize the Video of all Users connected to the Session.







