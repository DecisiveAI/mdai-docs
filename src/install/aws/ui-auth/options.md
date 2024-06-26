# Options for AWS Authentication for your MDAI Console

This documentation outlines how to configure AWS access for the MDAI Console. We will cover three scenarios: 

## 🌐 [Public access (no authentication)](./no-auth.md) 
**[Pre-Installation]** - *Fastest, least secure*

*Note: You should've already explored this option pre-install.*

You just need to spin this darn cluster up and don't mind your Console being open to any user on the internet. 

## 🔒 [Cognito](./cognito.md) 
**[Post-Installation]** - *Secure, slightly complex*

AWS Cognito provides a scalable and secure authentication mechanism for your application. You get a login interface and can connect it to your custom domain.

## 🥷 [VPC-based access](./vpc.md) 
**[Post-Installation]** - *Most secure, most complex*

This is the most secure option as you have the most control over inbound traffic/access to the cluster. 

----
## Choose your adventure...

Please select from the options above you'd like to use for auth for your MDAI Console.

🌐 [Public access (no authentication)](./no-auth.md) 

🔒 [Cognito](./cognito.md) 

🥷 [VPC-based access](./vpc.md) 