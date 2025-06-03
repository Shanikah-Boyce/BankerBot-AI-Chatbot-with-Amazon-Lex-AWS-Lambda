# BankerBot-AI-Chatbot-with-Amazon-Lex-AWS-Lambda

## Project Overview
BankerBot is an AI-powered banking chatbot designed using Amazon Lex V2 and AWS Lambda. It serves as a virtual banking assistant that can greet users, respond to balance inquiries, process fund transfers, handle fallback interactions and maintain context across multiple exchanges. By leveraging Lex’s built-in natural language understanding and speech recognition, the bot is capable of interpreting both text and voice inputs. This project was an opportunity to gain practical experience in building conversational interfaces using cloud-native technologies.

architecture diagram here*

The chatbot was built using Amazon Lex V2, with secure access granted through a least-privilege IAM role that allowed Lex to communicate with other AWS services. One of the key configuration choices was setting the intent confidence threshold to 0.40, ensuring that the bot only responds when it is reasonably confident about the user’s intent. This improves response accuracy and minimizes confusion. 
![image](https://github.com/user-attachments/assets/403ccae8-9ac5-4094-a816-eef1204041d8)

Additionally, I defined a custom slot type for accountType, limiting it to specific values like “Checking,” “Savings,” and “Credit” to maintain input integrity and enhance the reliability of the interaction.

![image](https://github.com/user-attachments/assets/f34b7a7e-4bc1-4028-9503-b8ab12077dce)

The bot supports several intents tailored to simulate common banking tasks. The WelcomeIntent introduces the chatbot and sets a friendly tone. The CheckBalance intent collects the user's account type and date of birth, then triggers a Lambda function that returns a randomized balance for demonstration purposes. 
![image](https://github.com/user-attachments/assets/d8ab9c53-d15e-4b82-b920-4a05e6b7a6de)

![image](https://github.com/user-attachments/assets/92813e3c-cdd2-437a-89b0-d047f69b351e)

Similarly, the TransferFunds intent gathers the source and target account types along with the desired transfer amount, incorporating a confirmation prompt to ensure that users verify the transaction before it's completed. 
