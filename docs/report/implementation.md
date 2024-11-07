---
sidebar_position: 4
---

# Implementation

In this section the implementation details of each microservice is exposed.

## Session microservice

### Reaction details

As described in detailed design, the domain aggregates can use Reactions passed by the infrastructure layer to react to domain events. Through these they can send messages to either single users connected to the session, or to all session users.
The Reactions that are triggered are the following, grouped by domain events:

- *SessionCreated* do not trigger any Reaction;
- *UserJoinedSession*: whenever a user joins a session, Reactions are used to:
    - Update the infrastructure layer list of users connected to the session;
    - Emit a join notification message to all session users, to inform that a new user has joined;
    - Update the chat of the new user with all the chat messages sent so far;
    - Retreive the current timestamp of the video from all the users that have already joined the session and synchronize the new user's video accordingly.
    As a rule, the timestamp with the minimum value is selected for the new user.
- *UserLeftSession*: Reactions are used to emit a leave notification message to all session users;
- *MessageSent*: Reaction are exploited to update the chat of each session user;
- *VideoPlayed* and *VideoStopped*: the video is played or stopped by one user, so  Reactions will serve to synchronize all the videos.

### Communication details

The communication with the session microservice is managed in such a way that it incrementally starts accepting new messages from the user, as new commands are validated by the `SessionService` implementation.

In this way the number of messages it receives is limited at mimimum and the risk of inconsistencies arising is eliminated. For example, we don't want a user to leave a session if he hasn't previously joined one, or we don't want a user to start sending commands if the token is not valid.

During messages exchanges, the client that contacts the microservice can pass between multiple states: this connection mechanisms be described using a Final State Machine (FSM) model:

![FSM](/img/ddd/detailed_design/session/session-connection.png)


#### Socket IO

For the communication technology, [Socket IO](https://socket.io/) has been chosen (WebSockets). Socket IO is a library that enables real-time, bidirectional and event-based communication between the browser and the server.


## Frontend Microservice

### Technologies

#### Socket IO Client

For the communication with the Session microservice [Socket IO Client](https://www.npmjs.com/package/socket.io-client) API has been used.

#### Youtube Player API

The embedding of the Youtube video frame is achieved by the use of the [Youtube Player API](https://developers.google.com/youtube/iframe_api_reference).

The Player allows to programmatically [play](https://developers.google.com/youtube/iframe_api_reference#playVideo), [pause](https://developers.google.com/youtube/iframe_api_reference#stopVideo), or [seek](https://developers.google.com/youtube/iframe_api_reference#seekTo) the video, which is fundamental to be externally synchronized. It also allows to react to Player State changes through a [listener](https://developers.google.com/youtube/iframe_api_reference#onStateChange). This listener will serve to react to video play/pause actions performed by the user. 