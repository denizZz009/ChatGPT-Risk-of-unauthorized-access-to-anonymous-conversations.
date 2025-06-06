
Vulnerability Description:
This vulnerability allows unauthorized access to anonymous conversations on ChatGPT by exploiting the conversation_id exposed in network traffic. Anonymous users can initiate conversations via manipulated URLs (e.g., https://chatgpt.com/?hints=search&q=testdenememerhaba) and inspect the backend-anon/conversation endpoint to retrieve a conversation_id. Using this ID in the format https://chatgpt.com/c/{conversation_id}, anyone with the ID can view the conversation history without authentication.

Impact:

Potential exposure of sensitive user data shared in anonymous conversations.
Breach of privacy for users who assume anonymity protects their data.
Risk of exploitation if conversation_id values are collected (e.g., via social engineering or server-side leaks).
Replication Steps:

Access ChatGPT anonymously using https://chatgpt.com/?hints=search&q=testdenememerhaba.
Open browser developer tools (Network tab) and initiate a conversation.
Locate the backend-anon/conversation request and inspect the response.
Find the conversation_detail_metadata event containing the conversation_id (e.g., 68432f63-3bd4-8001-8a53-d436f5cc0c75).
Visit https://chatgpt.com/c/{conversation_id} in a browser to view the conversation without logging in.
Additional Notes:

The conversation_id appears to be a random UUID, reducing the likelihood of random guessing, but its exposure in client-side traffic creates a risk if shared or leaked.
Tested on June 6, 2025, at 09:35 PM +03.
Recommendation:
Implement session-based access controls or limit the lifespan of anonymous conversation data to mitigate this issue.
