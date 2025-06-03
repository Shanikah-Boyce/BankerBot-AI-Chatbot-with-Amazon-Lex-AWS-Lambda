# BankerBot-AI-Chatbot-with-Amazon-Lex-AWS-Lambda

## Project Overview
BankerBot is an AI-powered banking chatbot designed using Amazon Lex V2 and AWS Lambda. It serves as a virtual banking assistant that can greet users, respond to balance inquiries, process fund transfers, handle fallback interactions and maintain context across multiple exchanges. By leveraging Lex’s built-in natural language understanding and speech recognition, the bot is capable of interpreting both text and voice inputs. This project was an opportunity to gain practical experience in building conversational interfaces using cloud-native technologies.

![Amzon Lex drawio](https://github.com/user-attachments/assets/e5a71afc-baea-4ade-b649-4c22239cbef1)


The chatbot was built using Amazon Lex V2, with secure access granted through a least-privilege IAM role that allowed Lex to communicate with other AWS services. One of the key configuration choices was setting the intent confidence threshold to 0.40, ensuring that the bot only responds when it is reasonably confident about the user’s intent. This improves response accuracy and minimizes confusion. 

![image](https://github.com/user-attachments/assets/403ccae8-9ac5-4094-a816-eef1204041d8)

Additionally, I defined a custom slot type for accountType, limiting it to specific values like “Checking,” “Savings,” and “Credit” to maintain input integrity and enhance the reliability of the interaction.

![image](https://github.com/user-attachments/assets/f34b7a7e-4bc1-4028-9503-b8ab12077dce)

The bot supports several intents tailored to simulate common banking tasks. The WelcomeIntent introduces the chatbot and sets a friendly tone. The CheckBalance intent collects the user's account type and date of birth, then triggers a Lambda function that returns a randomized balance for demonstration purposes. 


![image](https://github.com/user-attachments/assets/d8ab9c53-d15e-4b82-b920-4a05e6b7a6de)

![image](https://github.com/user-attachments/assets/92813e3c-cdd2-437a-89b0-d047f69b351e)

Similarly, the TransferFunds intent gathers the source and target account types along with the desired transfer amount, incorporating a confirmation prompt to ensure that users verify the transaction before it's completed. 

![image](https://github.com/user-attachments/assets/9868638d-a457-4bfe-bf70-b44dcfb36869)

These structured interactions are designed to mimic real-world banking flows, providing both functionality and conversational depth.

![Screenshot 2025-05-31 170255](https://github.com/user-attachments/assets/1746b7fd-58d3-4187-bebd-56dbade92a2b)


## Handling Fallbacks and Improving User Experience

To manage unsupported or unclear user inputs, I configured the built-in FallbackIntent with customized, varied responses that offer guidance instead of default error messages. This significantly improves user experience by offering suggestions or redirecting users to supported options. While the bot responded well to phrases like “Help me” and “Hiya,” some greetings like “Good morning”, “Heya” and “what’s up?” triggered fallback responses, highlighting an area for future improvement through additional intent coverage.

![image](https://github.com/user-attachments/assets/c2e27b97-0c17-4252-9d2f-748ede496816)

A key feature of BankerBot is its use of input and output context tags, which allow information to persist across multiple intents. For example, the user’s date of birth, collected during a CheckBalance query, is stored using an output context and then reused by a follow-up intent without requiring the user to repeat the information. This creates a more natural, fluid conversation and reflects real-world expectations for intelligent systems.

On the backend, all business logic was implemented using AWS Lambda. These functions, triggered via Lex’s code hooks, are responsible for processing user input, retrieving slot values, generating dynamic responses, and returning them in a format suitable for Lex. To simplify version control and ensure smooth integration, I used an alias named TestBotAlias to connect Lex with Lambda, making updates non-disruptive and easier to manage.

![image](https://github.com/user-attachments/assets/9f73a3f3-9511-4e9c-87a4-2f016e478c2b)

## Conclusion
BankerBot is a robust example of a serverless, AI-driven chatbot built with AWS services. It showcases how to design, implement, and deploy a conversational agent capable of managing multi-step workflows, retaining context, and providing a user-friendly experience. Through this project, I gained valuable hands-on experience in conversational AI, cloud infrastructure, secure integrations, and deployment automation. BankerBot reflects my growing capabilities in building intelligent, scalable, and maintainable solutions in a cloud-native environment.
