# BankerBot-AI-Chatbot-with-Amazon-Lex-AWS-Lambda

## Project Overview
BankerBot is an AI-powered banking chatbot built using Amazon Lex V2 and AWS Lambda. This virtual banking assistant is designed to handle common user interactions, including greetings, balance inquiries, fund transfers, and managing unsupported inputs. By leveraging Lex's natural language understanding (NLU) and speech recognition capabilities, BankerBot can interpret both text and voice inputs, offering a versatile conversational experience. This project was an excellent opportunity to gain practical experience in building conversational interfaces using cloud-native technologies.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e5a71afc-baea-4ade-b649-4c22239cbef1">
</p>

The chatbot was built using Amazon Lex V2, with secure access granted through a least-privilege IAM role that allowed Lex to communicate with other AWS services. One of the key configuration choices was setting the intent confidence threshold to 0.40, ensuring that the bot only responds when it is reasonably confident about the user’s intent. This improves response accuracy and minimizes confusion. 

![image](https://github.com/user-attachments/assets/403ccae8-9ac5-4094-a816-eef1204041d8)

Additionally, I defined a custom slot type for accountType, limiting it to specific values like “Checking,” “Savings,” and “Credit” to maintain input integrity and enhance the reliability of the interaction.

![image](https://github.com/user-attachments/assets/f34b7a7e-4bc1-4028-9503-b8ab12077dce)

The bot supports several intents tailored to simulate common banking tasks. 
### Welcoming Users
The `WelcomeIntent` sets a friendly tone by greeting users and introducing them to the chatbot, making interactions smooth and engaging.

### Checking Balances
The `CheckBalance` intent gathers key details like the user's account type and date of birth, triggering a Lambda function that generates a randomized balance for demonstration purposes. The `FollowupCheckBalance` intent allows users to check their balance again without re-authenticating, making repeated inquiries effortless.

BankerBot uses input and output context tags to retain information across interactions. For instance, the user's date of birth, collected during a CheckBalance query, is stored and reused for follow-up intents, creating a seamless conversation flow.

### Transferring Funds
The `TransferFunds` intent guides users through money transfers, collecting the source and target account types along with the transfer amount. A confirmation prompt ensures transactions are verified before completion, adding security and peace of mind.

### Handling the Unexpected Inputs
The `FallbackIntent` prevents disruptions by responding intelligently to unrecognized inputs. Instead of default error messages, it offers guidance and redirects users to relevant options.

## Refinement Opportunities
BankerBot successfully recognizes greetings like "Help me" and "Hiya," but phrases such as "Good morning", "Heya," and "What's up?" still trigger fallback responses. This highlights an opportunity for expanding intent coverage to further enhance natural conversations.

## Backend Powered by AWS Lambda
On the backend, all business logic was implemented using AWS Lambda. These functions, triggered via Lex’s code hooks, are responsible for processing user input, retrieving slot values, generating dynamic responses, and returning them in a format suitable for Lex. To simplify version control and ensure smooth integration, I used an alias named TestBotAlias to connect Lex with Lambda, making updates non-disruptive and easier to manage.

![image](https://github.com/user-attachments/assets/9f73a3f3-9511-4e9c-87a4-2f016e478c2b)

## Conclusion
BankerBot is a robust example of a serverless, AI-driven chatbot built with AWS services. It showcases how to design, implement, and deploy a conversational agent capable of managing multi-step workflows, retaining context, and providing a user-friendly experience. Through this project, I gained valuable hands-on experience in conversational AI, cloud infrastructure, secure integrations, and deployment automation. BankerBot reflects my growing capabilities in building intelligent, scalable, and maintainable solutions in a cloud-native environment.
