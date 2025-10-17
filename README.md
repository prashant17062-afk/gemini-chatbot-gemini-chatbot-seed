Academic Grading Chatbot - Round 2 Enhancement

Summary
This project presents an enhanced web-based chatbot designed to assist with academic grading inquiries. Building upon the previous version, this iteration introduces several key features for improved usability and persistence: a 'Clear Chat' button, conversation history persistence using localStorage, automatic restoration of chat on page load, a real-time message counter, timestamps for each message, and a character counter for the input field. The chatbot provides automated responses to common questions regarding student names, performance, and grade recommendations.

Setup
To set up and run this chatbot locally, follow these simple steps:
1.  Save the provided `index.html` file to your local machine.
2.  Open the `index.html` file using any modern web browser (e.g., Chrome, Firefox, Edge).
No additional dependencies or server-side configurations are required as the application is entirely client-side.

Usage
Upon opening the `index.html` file in your browser, you will be presented with the Academic Grading Chatbot interface.
-   **Chat with the Bot**: Type your academic grading-related questions into the input field at the bottom and click the 'Send' button or press 'Enter'.
-   **Conversation History**: Your previous messages and the bot's responses will be displayed in the chat area. The conversation history is automatically saved and restored when you revisit the page.
-   **Clear Chat**: To remove all messages from the current conversation and clear the saved history, click the 'Clear Chat' button. A confirmation prompt will appear to prevent accidental deletion.
-   **Message Count**: The header displays the total number of messages in the current conversation.
-   **Timestamps**: Each message is accompanied by a timestamp (HH:MM) indicating when it was sent.
-   **Character Counter**: Below the input field, a counter shows the remaining characters out of a maximum of 500 allowed for each message.

Main Code Logic
The core functionality is implemented using HTML for structure, CSS for styling, and JavaScript for interactive logic.

1.  **HTML Structure**:
    *   `#chat-messages`: A container `div` where all user and bot messages are dynamically added.
    *   `#user-input`: The text input field for user messages, now with `maxlength="500"`.
    *   `#send-btn`: The button to submit user messages.
    *   `#clear-btn`: A new button to clear the entire chat history from both the display and localStorage.
    *   `#message-count`: A `span` in the header displaying the total number of messages.
    *   `#char-count`: A `span` below the input field showing remaining characters.

2.  **CSS Styling**:
    *   Provides a clean, modern chat interface with distinct styling for user and bot messages, including custom border-radius for message bubbles and a responsive layout.

3.  **JavaScript Logic**:
    *   **DOM Element References**: All interactive elements are referenced using `document.querySelector`.
    *   **`chatHistory` Array**: A global array `chatHistory` stores message objects, each containing `sender`, `text`, and `timestamp`.
    *   **`formatTimestamp(date)`**: A utility function to format `Date` objects into `HH:MM` strings.
    *   **`displayMessage(sender, messageText, timestamp)`**: Appends a new message `div` to `#chat-messages`, styling it based on the `sender` and including the provided `timestamp`. It also ensures the chat area scrolls to the latest message.
    *   **`updateMessageCounter()`**: Updates the text content of `#message-count` based on the `chatHistory` array's length.
    *   **`saveChatHistory()`**: Serializes `chatHistory` into a JSON string and saves it to `localStorage` under the key `'chatHistory'`. This ensures persistence across sessions.
    *   **`loadChatHistory()`**: On page load (`DOMContentLoaded`), this function retrieves `chatHistory` from `localStorage`, parses it, and then iterates through the loaded messages to `displayMessage` them, effectively restoring the previous conversation.
    *   **`getBotResponse(userMessage)`**: Contains the simple conditional logic to generate predefined bot responses based on keywords in the user's input.
    *   **`sendMessage()`**: This is the core function for message handling. It captures user input, generates a timestamp, calls `displayMessage` for both user and bot, pushes messages to `chatHistory`, then calls `saveChatHistory()` and `updateMessageCounter()`. Finally, it clears the input field and updates the character counter.
    *   **`clearChat()`**: Triggered by the `Clear Chat` button, this function clears the DOM, empties the `chatHistory` array, and removes the `chatHistory` item from `localStorage` after user confirmation. It then updates the message counter.
    *   **`updateCharCounter()`**: Calculates and displays the remaining characters in the `user-input` field relative to `MAX_CHARACTERS` (500).
    *   **Event Listeners**: Listeners are attached to the 'Send' button (click), input field (keypress for 'Enter'), 'Clear Chat' button (click), and input field (input for character counting).
    *   **Initialization**: `loadChatHistory()` and `updateCharCounter()` are called on `DOMContentLoaded` to set up the initial state of the chat.

License
This project is released under the MIT License.

MIT License

Copyright (c) 2023 [Your Name / AI Developer Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Contact
For questions or feedback, please contact [Your Contact Information - e.g., your_email@example.com or GitHub profile link].