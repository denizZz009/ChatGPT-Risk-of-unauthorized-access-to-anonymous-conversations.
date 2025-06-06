ChatGPT Anonymous Conversation Vulnerability Research
Overview
This repository documents a potential security vulnerability discovered in the ChatGPT platform's anonymous conversation system. The finding highlights a risk of unauthorized access to anonymous conversation data using exposed conversation_id values. This research was conducted in good faith to contribute to the security of OpenAI's systems.

Date of Discovery: June 6, 2025
Time: 09:35 PM +03
Researcher: [Your Name or Alias]

Description
The vulnerability allows anyone with a valid conversation_id to access anonymous conversation histories on ChatGPT without authentication. This is possible due to the exposure of conversation_id in client-side network traffic, accessible via the backend-anon/conversation endpoint.
Impact

Potential exposure of sensitive user data shared anonymously.
Privacy breach for users assuming anonymity.
Risk of exploitation if conversation_id values are collected or leaked.

Mitigation

Implement session-based access controls.
Limit the lifespan of anonymous conversation data.
Restrict conversation_id exposure in client-side responses.

How It Works
The vulnerability was identified through the following steps:

Access ChatGPT anonymously using a manipulated URL (e.g., https://chatgpt.com/?hints=search&q=testdenememerhaba).
Open browser developer tools (Network tab) and initiate a conversation.
Inspect the backend-anon/conversation request response to find the conversation_id (e.g., 68432f63-3bd4-8001-8a53-d436f5cc0c75).
Visit https://chatgpt.com/c/{conversation_id} to view the conversation without logging in.

Screenshots
Below are screenshots illustrating the discovery process:

Backend-Anon Endpoint:

Conversation Metadata:

Conversation ID:


Note: Ensure the corresponding PNG files (conversation_backend_anon.png, conversation_metadata.png, conversation_id.png) are uploaded to the repository for the images to display correctly.
Reporting to OpenAI
This vulnerability has been reported to OpenAI as part of their Bug Bounty Program. The submission includes:

Title: "Unauthorized access to anonymous conversations"
Target: ChatGPT
Severity: Access control vulnerability
Details: Replication steps, impact assessment, and attached screenshots.

Status

 Awaiting OpenAI's response.
 Update with any feedback or resolution.

Legal and Ethical Notes

This research was conducted in accordance with OpenAI's Coordinated Vulnerability Disclosure Policy.
No exploitation or malicious use was intended or performed.
Public disclosure is avoided until OpenAI provides explicit permission or evidence of active exploitation emerges.

Contributing
If you have additional findings or improvements, feel free to open an issue or submit a pull request. Collaboration is welcome to enhance this research.
License
This project is shared under the MIT License for educational purposes. See the LICENSE file for details.
Note: Add a LICENSE file to the repository if you haven't already.
Contact
For questions or further discussion, you can reach out via [your email or GitHub profile].
Last Updated: June 6, 2025, 09:44 PM +03
