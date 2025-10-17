# Simple Chatbot

## Summary

This is a simple chatbot web application that allows users to exchange messages with a bot powered by the OpenAI API. The application features a clean user interface, message persistence using local storage, and character count for input.

## Features

-   **Chat Interface:** A user-friendly interface for sending and receiving messages.
-   **OpenAI Integration:** Uses the OpenAI API to generate bot responses. (API key required)
-   **Message Persistence:** Saves the conversation history in the browser's local storage, allowing users to resume their conversation even after refreshing the page.
-   **Clear Chat:** A button to clear the entire chat history.
-   **Message Counter:** Displays the total number of messages in the conversation.
-   **Timestamps:** Each message includes a timestamp indicating when it was sent.
-   **Character Counter:** Shows the remaining characters allowed in the input field (maximum 500).

## Usage

1.  **API Key:** Replace `"sk-YOUR_API_KEY"` in the JavaScript code with your actual OpenAI API key.
2.  **Open the HTML file:** Open the `index.html` file in your web browser.
3.  **Start Chatting:** Type your message in the input field and press "Send" or hit the Enter key. The bot's response will appear in the chat log.
4.  **Clear Chat:** Click the "Clear Chat" button to remove all messages and clear the local storage.

## License

This project is licensed under the MIT License.