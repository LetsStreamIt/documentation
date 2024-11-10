---
sidebar_position: 4
---
# Implementation


In this section, the implementation details of each microservice are exposed.


## Session microservice


### Reaction details


As described in the detailed design, the domain aggregates can use Reactions passed by the infrastructure layer to react to domain events. Through these, they can send messages to either single users connected to the session, or to all session users.
The Reactions that are triggered are the following, grouped by domain events:


- _SessionCreated_ do not trigger any Reaction;
- _UserJoinedSession_: whenever a user joins a session, Reactions are used to:
 - Update the infrastructure layer list of users connected to the session;
 - Emit a join notification message to all session users, to inform them that a new user has joined;
 - Update the chat of the new user with all the chat messages sent so far;
 - Retrieve the current timestamp of the video from all the users that have already joined the session and synchronize the new user's video accordingly.
   As a rule, the timestamp with the minimum value is selected for the new user.
- _UserLeftSession_: Reactions are used to emit a leave notification message to all session users;
- _MessageSent_: Reactions are exploited to update the chat of each session user;
- _VideoPlayed_ and _VideoStopped_: the video is played or stopped by one user, so Reactions will serve to synchronize all the videos.


### Communication details


The communication with the session microservice is managed in such a way that it incrementally starts accepting new messages from the user, as new commands are validated by the `SessionService` implementation.


In this way, the number of messages it receives is limited at minimum and the risk of inconsistencies arising is eliminated. For example, we don't want a user to leave a session if he hasn't previously joined one, or we don't want a user to start sending commands if the token is not valid.


During message exchanges, the client that contacts the microservice can pass between multiple states: these connection mechanisms be described using a Final State Machine (FSM) model:


![FSM](/img/ddd/detailed_design/session/session-connection.png)


#### Socket IO


For the communication technology, [Socket IO](https://socket.io/) has been chosen (WebSockets). Socket IO is a library that enables real-time, bidirectional, and event-based communication between the browser and the server.


## Frontend Microservice


### Technologies


#### Socket IO Client


For the communication with the Session microservice [Socket IO Client](https://www.npmjs.com/package/socket.io-client) API has been used.


#### Youtube Player API


The embedding of the Youtube video frame is achieved by the use of the [Youtube Player API](https://developers.google.com/youtube/iframe_api_reference).


The Player allows to programmatically [play](https://developers.google.com/youtube/iframe_api_reference#playVideo), [pause](https://developers.google.com/youtube/iframe_api_reference#stopVideo), or [seek](https://developers.google.com/youtube/iframe_api_reference#seekTo) the video, which is fundamental to be externally synchronized. It also allows to react to Player State changes through a [listener](https://developers.google.com/youtube/iframe_api_reference#onStateChange). This listener will serve to react to video play/pause actions performed by the user.


## Authentication Microservice


### Technologies


#### JSON Web Tokens


The Authentication microservice is responsible for generating and validating JSON Web Tokens (JWT) for the users. The JWT is a standard that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed.


Since the JWT is signed, it can be verified and trusted. The JWT is signed using a secret key, which is stored in the environment variables of the microservice, meaning that only this microservice can generate and validate the JWT, while the other microservices have to contact this microservice to validate the JWT.


#### Express


The Authentication microservice is built using the Express framework, which is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications. Being a simple microservice, Express is a reasonable choice for this microservice.


#### Bcrypt


For securely storing the user's password, the Bcrypt library is used. Bcrypt is a password-hashing function that is used to securely store the user's password in the database. The password is hashed using a salt, which is a random string that is added to the password before hashing it. The passwords will then be stored in the database as a hash, which is a one-way function, meaning that it is not possible to reverse the hash to obtain the original password. It is instead possible to compare the hashed password with a plaintext one to verify if they match.


#### Mongoose


This implementation of the Authentication microservice stores the user's data in a MongoDB database. To interact with the MongoDB database, the Mongoose library is used. Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js, which provides a straightforward schema-based solution to model the application data.


### Interaction with other microservices


#### Incoming requests


The Authentication microservice receives incoming requests from the other microservices to validate the JWT. The JWT is sent in the Authorization header of the request, and the Authentication microservice extracts the JWT from the header and validates it.
Since some information about the user is stored in the JWT, the Authentication microservice can extract this information and send it back to the other microservices, which can then use this information to perform the necessary operations.


#### Outgoing requests


The Authentication microservice needs to contact the Profile microservice when a new user is created, to store the user's profile data. The Authentication microservice sends a request to the Profile microservice with the user's profile data, and the Profile microservice stores this data in the database.


![registration-sequence](/img/implementation/registration-sequence.svg)


## Profile Microservice


### Technologies


#### Akka HTTP


The Profile microservice is built using the Akka HTTP framework, which is a modern, lightweight, and high-performance toolkit for building HTTP applications with Scala. Akka HTTP is a good choice for this microservice because it is built on top of Akka, which is a powerful actor-based toolkit for building concurrent and distributed applications.


#### MongoDB scala driver


The Profile microservice stores the user's profile data in a MongoDB database. To interact with the MongoDB database, the MongoDB Scala driver is used. The MongoDB Scala driver is a reactive, asynchronous, and non-blocking driver for MongoDB that provides a simple and idiomatic Scala API for interacting with the MongoDB database.
