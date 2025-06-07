## Project Overview
<p align="center">
  <img src="https://github.com/user-attachments/assets/e5a71afc-baea-4ade-b649-4c22239cbef1">
</p>

BankerBot is a banking chatbot powered by AI that aims to improve financial access and automate everyday transactions using Amazon Lex V2 and AWS Lambda.

Its main purpose is to simplify banking interactions with a secure, efficient, and user-friendly virtual assistant that can handle balance inquiries, fund transfers, greetings, and even manage unsupported inputs. By utilizing Lex’s natural language understanding (NLU) and speech recognition tech, it guarantees smooth communication through both text and voice functions.

To maintain security and precision, BankerBot works under a least-privilege IAM role and sets a 0.40 intent confidence threshold, meaning it will only respond when it’s fairly sure of what the user needs. It also ensures data integrity through a custom slot type for accountType, restricting options to "Checking," "Savings," and "Credit." The "Credit" category includes leading providers such as Visa, Mastercard, Amex, and American Express, making it easy for users to manage a variety of financial accounts.

Building BankerBot has given me lots of hands-on experience in cloud-native conversational AI, focusing on best practices regarding security, efficiency, and user-centered design.

![image](https://github.com/user-attachments/assets/403ccae8-9ac5-4094-a816-eef1204041d8)



![image](https://github.com/user-attachments/assets/f34b7a7e-4bc1-4028-9503-b8ab12077dce)

## Core Functionality: Supporting Key Banking Interactions
BankerBot supports multiple intents tailored for common banking interactions, ensuring smooth user experiences.

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
While BankerBot successfully recognizes standard greetings like "Help me" and "Hiya," there's an opportunity to expand its understanding of more casual phrases such as "Good morning," "Heya," and "What's up?" Currently, these trigger fallback responses. Expanding the training data for these and similar expressions would significantly enhance the naturalness and fluidity of conversations.

## Backend Powered by AWS Lambda
BankerBot's business logic is entirely managed by AWS Lambda functions, which are activated through Lex's code hooks. These functions are responsible for processing user inputs, retrieving slot values, and generating dynamic responses. To ensure smooth version control and continuous updates, an alias called TestBotAlias was established, enabling seamless improvements without disrupting active deployments.

![image](https://github.com/user-attachments/assets/9f73a3f3-9511-4e9c-87a4-2f016e478c2b)

## Lessons Learned: Enhancing BankerBot’s Capabilities
Using Amazon Lex for BankerBot has provided valuable insights. While the chatbot effectively addresses common queries, it struggles with casual greetings and ambiguous requests. A key takeaway is the importance of robust training data—more data leads to a more responsive and engaging chatbot experience.

To make BankerBot even more intelligent and adaptable, the following improvements could be implemented:
- **Leveraging Amazon Bedrock with RAG:** Rather than relying solely on predefined responses, integrating Amazon Bedrock with Retrieval-Augmented Generation (RAG) would enable BankerBot to generate contextually relevant answers dynamically, enhancing user interactions.
- **Connecting RAG to Amazon S3 for financial insights:** By accessing financial documents stored in Amazon S3, BankerBot could retrieve and summarize accurate, up-to-date financial information, making responses more reliable and useful.
These enhancements would significantly expand BankerBot’s capabilities, allowing it to handle a wider range of inquiries and provide more valuable assistance to users.

## Conclusion
BankerBot is a powerful example of an AI-driven, serverless chatbot designed for modern banking needs. By leveraging Amazon Lex and AWS Lambda, the chatbot ensures efficient, secure, and intelligent interactions. This project showcases expertise in building scalable conversational agents, maintaining user context, and delivering seamless digital banking solutions.
