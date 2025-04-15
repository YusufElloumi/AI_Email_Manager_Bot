# AI_Email_Manager_Bot
This n8n workflow processes incoming emails, summarizes them with AI, and prepares draft responses for human review before sending.

This automated workflow streamlines the processing of incoming emails by summarizing content, generating tailored responses via a retrieval-augmented generation (RAG) strategy, and securing approval before sending any replies. The workflow is structured in two primary stages:

1. Email Processing and Summarization:

The process initiates with an IMAP Email Trigger node that continuously monitors a designated inbox for new messages.

Upon receipt of an email, a Markdown node converts any HTML content into plain text if needed. Subsequently, an AI-driven Email Summarization Chain creates a concise summary—up to 100 words—highlighting the key points of the message.

2. Response Generation and Approval:

A Write Email node crafts a professional draft response based on the summarized information, ensuring both clarity and brevity.

Before dispatching the response, the draft is forwarded for human review via a Gmail node configured to allow free-text feedback. Depending on the review outcome, the response is either finalized and sent using the Send Email node or redirected for further refinement.

Additionally, a Text Classifier node evaluates the feedback by categorizing it as either “Approved” or “Declined,” determining if the email should be sent immediately or if additional edits are required.
