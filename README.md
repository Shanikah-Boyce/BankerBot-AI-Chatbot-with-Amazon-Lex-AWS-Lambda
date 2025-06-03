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
## Setting the Stage
The WelcomeIntent greets users warmly, setting a friendly tone and introducing them to the chatbot. This immediately creates a welcoming and engaging experience.

## Checking Balances
For balance inquiries, the CheckBalance intent efficiently gathers essential information like the user's account type and date of birth. This triggers a Lambda function that provides a randomized balance for demonstration. To enhance convenience, the FollowupCheckBalance intent allows users to request a subsequent balance check without needing to re-authenticate, streamlining their experience.

## Transferring Funds
When it comes to moving money, the TransferFunds intent guides users through the process. It collects the source and target account types, along with the desired transfer amount. A crucial confirmation prompt is included to ensure users verify the transaction before it's completed, adding a layer of security and peace of mind.

## Handling the Unexpected
Finally, the FallbackIntent acts as a safety net, gracefully managing situations where no other intent matches the user's input. This ensures the conversation remains smooth and intuitive, even when queries are unexpected.

## Handling Fallbacks and Improving User Experience
To manage unsupported or unclear user inputs, I configured the built-in FallbackIntent with customized, varied responses that offer guidance instead of default error messages. This significantly improves user experience by offering suggestions or redirecting users to supported options. While the bot responded well to phrases like “Help me” and “Hiya,” some greetings like “Good morning”, “Heya” and “what’s up?” triggered fallback responses, highlighting an area for future improvement through additional intent coverage.

![image](https://github.com/user-attachments/assets/c2e27b97-0c17-4252-9d2f-748ede496816)

A key feature of BankerBot is its use of input and output context tags, which allow information to persist across multiple intents. For example, the user’s date of birth, collected during a CheckBalance query, is stored using an output context and then reused by a follow-up intent without requiring the user to repeat the information. This creates a more natural, fluid conversation and reflects real-world expectations for intelligent systems.

On the backend, all business logic was implemented using AWS Lambda. These functions, triggered via Lex’s code hooks, are responsible for processing user input, retrieving slot values, generating dynamic responses, and returning them in a format suitable for Lex. To simplify version control and ensure smooth integration, I used an alias named TestBotAlias to connect Lex with Lambda, making updates non-disruptive and easier to manage.

![image](https://github.com/user-attachments/assets/9f73a3f3-9511-4e9c-87a4-2f016e478c2b)

## Conclusion
BankerBot is a robust example of a serverless, AI-driven chatbot built with AWS services. It showcases how to design, implement, and deploy a conversational agent capable of managing multi-step workflows, retaining context, and providing a user-friendly experience. Through this project, I gained valuable hands-on experience in conversational AI, cloud infrastructure, secure integrations, and deployment automation. BankerBot reflects my growing capabilities in building intelligent, scalable, and maintainable solutions in a cloud-native environment.
