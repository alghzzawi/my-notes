# Authentication
---
* ## What is OAuth?
#### OAuth is an open standard for access delegation, commonly used as a way for internet users to grant websites or applications access to their information on other websites but without giving them the passwords.
---
* ## Give an example of what using OAuth would look like.
#### when you log in into a site and it can merge you into other pages.
---
* ## How does OAuth work? What are the steps that it takes to authenticate the user?
#### authorization request --> authorization grant
#### authorization grant --> access token
#### access token --> protected resource
---
* ## What is OpenID?
#### OpenID is an open standard and decentralized authentication protocol promoted by the non-profit OpenID Foundation.
---
* ## What is the difference between authorization and authentication?
#### Authentication and authorization are two vital information security processes that administrators use to protect systems and information. Authentication verifies the identity of a user or service, and authorization determines their access rights.
---
* ## What is Authorization Code Flow?
#### Exchanges an Authorization Code for a token.
---
* ## What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?
#### During authentication, mobile and native applications can use the Authorization Code Flow, but they require additional security. Additionally, single-page apps have special challenges.
---
* ## What is Implicit Flow with Form Post?
#### As an alternative to the Authorization Code Flow, OAuth 2.0 provides the Implicit Flow, which is intended for Public Clients, or applications which are unable to securely store Client Secrets. While this is no longer considered a best practice for requesting Access Tokens, when used with Form Post response mode, it does offer a streamlined workflow if the application needs only an ID token to perform user authentication.
---
* ## What is Client Credentials Flow?
#### With machine-to-machine (M2M) applications, such as CLIs, daemons, or services running on your back-end, the system authenticates and authorizes the app rather than a user. For this scenario, typical authentication schemes like username + password or social logins don't make sense. Instead, M2M apps use the Client Credentials Flow.
---
* ## What is Device Authorization Flow?
#### With input-constrained devices that connect to the internet, rather than authenticate the user directly, the device asks the user to go to a link on their computer or smartphone and authorize the device. This avoids a poor user experience for devices that do not have an easy way to enter text. To do this, device apps use the Device Authorization Flow. For use with mobile/native applications.
---
* ## What is Resource Owner Password Flow?
#### Though we do not recommend it, highly-trusted applications can use the Resource Owner Password Flow, which requests that users provide credentials (username and password), typically using an interactive form. The Resource Owner Password Flow should only be used when redirect-based flows (like the Authorization Code Flow) cannot be used.