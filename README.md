AI Chatbot for Academic Grading

Summary
This project delivers an advanced AI chatbot designed to assist with academic grading. Building upon a foundational chat interface, this iteration introduces robust features for enhanced user control, conversation management, and improved user experience. It provides a client-side interface for interacting with an AI model (simulated in this demo) to generate feedback, analyze rubrics, and assist with various grading tasks. The application emphasizes usability with a collapsible settings panel, persistent configurations, and comprehensive chat utility functions.

Setup
1.  Save the provided `index.html` content into a file named `index.html`.
2.  Open `index.html` in a modern web browser (e.g., Chrome, Firefox, Edge).
3.  The application will load directly in your browser.

Usage
Upon opening the `index.html` file, you will be presented with the AI Chatbot interface:

*   **Chat Interface:** Type your queries into the text area at the bottom and click "Send" or press Enter (Shift+Enter for a new line).
*   **Settings Panel:**
    *   Click the "Toggle Settings" button to expand or collapse the panel.
    *   **OpenAI API Key:** Enter your personal OpenAI API key here. For full AI functionality, this field should contain a valid key. The key is persisted in your browser's local storage.
    *   **Show API Key:** Check this box to reveal the API key you've entered, uncheck to hide it.
    *   **Temperature Slider:** Adjust this slider (0.0 to 1.0) to control the AI's response creativity. Lower values result in more focused and deterministic responses, while higher values yield more varied and creative outputs.
    *   **Max Tokens:** Set the maximum length for the AI's responses (default is 1000 tokens).
    *   All settings (API Key, Temperature, Max Tokens) are automatically saved to your browser's `localStorage` under 'chatSettings' and will persist across sessions.
*   **Clear Chat:** Click the "Clear Chat" button to remove all messages from the current conversation. A confirmation prompt will appear to prevent accidental deletion.
*   **Export Chat:** Click the "Export Chat" button to download your entire conversation history as a JSON file, including timestamps and sender roles.
*   **Message Timestamps:** Each message (both user and bot) is accompanied by a timestamp in 'HH:MM AM/PM' format.
*   **Message Counter:** The "Messages: X" display in the "Chat Statistics" panel keeps track of the total number of messages in the conversation.
*   **Character Counter:** A character counter is displayed below the input area, showing the current character count and the maximum limit (2000 characters) for your message.
*   **Copy Bot Message:** Each message from the bot includes a "Copy" button. Clicking this button will copy the bot's response text to your clipboard.

Main Code Logic

The application is built as a single-page HTML file (`index.html`) using HTML for structure, CSS for styling, and JavaScript for all interactive logic.

1.  **HTML Structure:**
    *   The `index.html` defines a clear layout with a header, a main container split into a chat area and a control panel, and a footer.
    *   The chat area includes `#chat-history` (for messages) and `#input-area` (for user input and counters).
    *   The `#control-panel` houses the toggle for settings, chat management buttons, and chat statistics.
    *   The `#settings-panel` is a collapsible `div` containing API key input, temperature slider, and max tokens input.

2.  **CSS Styling:**
    *   Modern CSS (`flexbox` for layout) is used to create a responsive and visually appealing interface.
    *   Clear visual distinctions are made between user and bot messages.
    *   The `#settings-panel` utilizes `max-height` and `opacity` transitions for a smooth collapse/expand animation.
    *   Basic styling for inputs, buttons, and counters ensures readability and usability.

3.  **JavaScript Core:**
    *   **DOM Manipulation:** All interactive elements are selected using `document.getElementById` and `document.querySelector`.
    *   **State Management:**
        *   `conversationHistory`: An array of objects, each representing a message with `role`, `content`, and `timestamp`, to maintain the chat state.
        *   `chatSettings`: An object (`apiKey`, `temperature`, `maxTokens`) stores chatbot configuration.
    *   **`localStorage` for Persistence:**
        *   `loadSettings()`: Retrieves `chatSettings` from `localStorage` on page load and populates the UI elements.
        *   `saveSettings()`: Persists `chatSettings` to `localStorage` whenever a setting is changed. This ensures user preferences are retained across browser sessions.
    *   **Dynamic Message Rendering (`appendMessage`):**
        *   Creates `div` elements for each message, applying appropriate CSS classes (`user` or `bot`).
        *   Generates and attaches a timestamp (`getCurrentTimestamp()`) to each message.
        *   For bot messages, a "Copy" button is dynamically added, utilizing `navigator.clipboard.writeText` for clipboard functionality.
    *   **Chat Interaction:**
        *   `sendMessage()`: Handles user input, appends the user message, clears the input, and then calls `getBotResponse()`.
        *   `getBotResponse()`: (Placeholder) This function simulates an AI response. In a real application, it would perform a `fetch` request to an AI API (e.g., OpenAI's Chat Completions endpoint), passing the `apiKey`, `temperature`, `maxTokens`, and `conversationHistory` for contextual replies. Error handling for API calls is included.
    *   **Utility Features:**
        *   `updateCounters()`: Keeps the `#message-count` and `#char-count` displays current.
        *   **Clear Chat:** The `#clear-btn` uses `confirm()` for user verification before resetting `chatHistory` and `conversationHistory`.
        *   **Export Chat:** The `#export-btn` serializes `conversationHistory` to a JSON string, creates a `Blob`, and then triggers a download using a temporary `<a>` element and `URL.createObjectURL()`.
    *   **Event Handling:** Event listeners are set up for input changes, button clicks, and keypresses to manage all interactive features. `userInput` includes logic for auto-resizing the textarea.

License
This project is released under the MIT License. See the license text embedded in the `index.html` file for full details.

Contact
For any questions or feedback, please contact [Your Name/Email or Placeholder].