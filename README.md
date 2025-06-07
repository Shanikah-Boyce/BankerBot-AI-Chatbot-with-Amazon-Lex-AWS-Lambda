## Project Overview
BankerBot is an AI-powered banking chatbot designed to enhance financial accessibility and streamline everyday transactions using Amazon Lex V2 and AWS Lambda.

Its core function is to provide a secure, efficient, and intuitive virtual banking assistant capable of handling balance inquiries, fund transfers, greetings, and even managing unsupported inputs. Leveraging Lex’s advanced natural language understanding (NLU) and speech recognition technology, BankerBot ensures seamless interaction via both text and voice.

For optimal security and accuracy, BankerBot operates under a least-privilege IAM role and maintains a 0.40 intent confidence threshold, responding only when confident in the user's request. Data integrity is upheld through a custom slot type for accountType, restricting selections to "Checking," "Savings," and "Credit." The "Credit" category encompasses leading providers like Visa, Mastercard, Amex, and American Express, allowing users to efficiently manage various financial accounts.

Developing BankerBot has provided valuable hands-on experience in cloud-native conversational AI, emphasizing best practices in security, efficiency, and user-centric design.
<p align="center">
  <img src="https://github.com/user-attachments/assets/e5a71afc-baea-4ade-b649-4c22239cbef1">
</p>

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
