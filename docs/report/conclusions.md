---
sidebar_position: 8
---

# Conclusions

Future improvements of the project may touch several aspects:

- For the Streaming Session, one feature to add is the possibility to accept video URLs coming from multiple sources, and to not be constrained on Youtube videos only. While this feature would be quite easy to add in the Session service, the Frontend's may encounter several technical problems concerning the embedding of the video, and the possibility to programmatically interact with it;
- Another feature to add is the possibility of scaling the Session microservice. One idea is to add a middleware that links a Session to its respective microservice deployment, such that a Session is managed by only one deployment. The middleware then redirects the user to the specific server to start interacting with the Session.
In this case the deployments are not replicas, so problems may arise if errors occur, but it may be easiest way to manage lots of user requests; 
- For the User Profile, other features may enrich it with other information. Some examples are the possibility to group videos by the type of content, or to add statistics such as the number of videos watched recently;
- Security. Session microservice security makes uses of JWT tokens at the initial interaction, but if the token expires during the streaming, the connection is maintained. Future developments should add the possibility to embed the token inside every WebSocket message, and disconnect the user whether is not valid anymore.