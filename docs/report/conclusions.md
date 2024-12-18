---
sidebar_position: 8
---

# Conclusions

The project allowed us to deepen our knowledge on multiple aspects. Building a strong CI/CD pipeline has been useful for making the development process as streamlined as possible, and for delivering a robust system. Additionally, adopting Clean Architecture helped us manage the project structure more easily and minimize code changes required due to bugs.


Future improvements of the project may touch on several aspects:

- For the Streaming Session, one feature to add is the possibility to accept video URLs coming from multiple sources and not be constrained to YouTube videos only. While this feature would be quite easy to add to the Session service, the Frontend's may encounter several technical problems concerning the embedding of the video, and the possibility of programmatically interact with it;
- Another feature to add is the possibility of scaling the Session microservice. One idea is to add a middleware that links a Session to its respective microservice deployment, such that a Session is managed by only one deployment. The middleware then redirects the user to the specific server to start interacting with the Session.
 In this case, the deployments are not replicas, so problems may arise if failures occur, but it may be the easiest way to manage lots of user requests;
- For the User Profile, other features may enrich it with other information. Some examples are the possibility to group videos by the type of content, or to add statistics such as the number of videos watched recently;
- Security. Session microservice security makes use of JWT tokens at the initial interaction, but if the token expires during the streaming, the connection is maintained. Future developments should add the possibility to embed the token inside every WebSocket message and disconnect the user whenever not valid anymore.

