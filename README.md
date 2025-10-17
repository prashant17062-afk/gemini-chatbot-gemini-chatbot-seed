# Academic Grading AI Chatbot powered by Google Gemini

## Summary
This project presents an interactive AI chatbot specifically designed to assist with academic grading scenarios. It integrates with the Google Gemini API to offer intelligent responses to queries related to rubrics, assignment feedback, assessment criteria, and general educational grading practices. The application features a user-friendly and mobile-responsive interface styled with Bootstrap, robust API key management (stored in local storage), real-time chat message display, a typing indicator, and comprehensive error handling for API interactions.

## Setup

To set up and run this chatbot, follow these simple steps:

1.  **Save the file:** Copy the entire content of `index.html` into a new file named `index.html` on your local machine.
2.  **Open in Browser:** Navigate to the saved `index.html` file and open it using any modern web browser (e.g., Google Chrome, Mozilla Firefox, Microsoft Edge). No server environment or build tools are required.
3.  **Obtain a Google Gemini API Key:**
    *   Visit the [Google AI Studio](https://aistudio.google.com/) or the [Google Cloud Console](https://console.cloud.google.com/apis/credentials).
    *   Create or select an existing Google Cloud project.
    *   Ensure the "Generative Language API" is enabled for your project.
    *   Generate a new API key. It is crucial to keep this key confidential and never embed it directly into publicly accessible code.

## Usage

1.  **Enter API Key:** When the application loads, the chat input area will be disabled. Locate the "Gemini API Key" input field (#api-key-input) at the top of the page. Paste your obtained Gemini API key into this field.
2.  **Set API Key:** Click the 'Set API Key' button (#set-api-btn). The API status indicator (#api-status) will update to 'API Key: Set ✓' (in green), and the main chat input field (#user-input) and send button (#send-btn) will become active. Your API key will be securely stored in your browser's `localStorage` for future sessions, meaning you won't need to re-enter it every time you open the page.
3.  **Start Chatting:** Type your academic grading-related questions or prompts into the now-enabled chat input field (#user-input) and press the Enter key or click the 'Send' button.
4.  **Receive AI Responses:** While the AI processes your request, a 'AI is typing...' indicator (#typing-indicator) will be visible. Once the response is generated, it will appear in the chat messages area (#chat-messages) with distinct styling for bot messages.
5.  **Error Handling:** In case of an invalid API key, network issues, or other problems during the API call, an informative error message will be displayed in the chat, guiding you on potential next steps.

## Main Code Logic

The primary functionality of this chatbot is encapsulated within the `<script>` tag of the `index.html` file.

*   **DOM Element Caching:** At the start of the script, references to all interactive HTML elements (inputs, buttons, display areas) are obtained using `document.querySelector` to optimize subsequent DOM manipulations.
*   **API Key Management (`localStorage`):**
    *   The `localStorage` API is utilized to persist the Gemini API key under the key `'geminiApiKey'`. This allows the key to be saved across browser sessions.
    *   The `loadApiKey()` function executes on `DOMContentLoaded`, checking for a previously stored key. If found, it initializes the `GoogleGenerativeAI` model and enables the chat interface.
    *   The `setApiBtn`'s event listener handles storing the API key entered by the user, updating the UI status (`#api-status`), clearing the input field, and initializing the `GoogleGenerativeAI` model. Robust error handling is included for model initialization.
*   **Chat Message Display (`addMessage`):**
    *   The `addMessage(sender, text)` utility function is responsible for dynamically creating new chat message bubbles. It applies specific CSS classes (`user` or `bot`) to differentiate the sender and ensure messages are automatically scrolled into view. Newlines in messages are converted to HTML `<br>` tags for proper rendering.
*   **Gemini API Interaction (`sendMessage`):**
    *   The `sendMessage()` asynchronous function orchestrates the communication with the Google Gemini API.
    *   It captures the user's input, displays it in the chat, clears the input field, and temporarily disables user input while showing a `#typing-indicator`.
    *   It then uses the `generativeModel.generateContent(message)` method (from the `GoogleGenerativeAI` SDK) to send the prompt to the AI and await its response.
    *   The AI's textual response is extracted and displayed in the chat.
*   **Error Handling:**
    *   `try-catch` blocks are strategically placed around API calls within `loadApiKey()`, `setApiBtn`'s listener, and `sendMessage()` to gracefully manage and display errors directly in the chat interface, providing feedback to the user without crashing the application.
*   **UI State Management:**
    *   Helper functions like `updateApiStatus()`, `toggleChatInput()`, and `showTypingIndicator()` manage the interactive elements' visibility and enabled states, ensuring a responsive and intuitive user experience.
*   **Mobile Responsiveness:** The layout is primarily managed using Bootstrap's flexbox and spacing utilities (`d-flex`, `flex-column`, `flex-md-row`, `mb-2 mb-md-0`, etc.) combined with custom CSS media queries to adapt gracefully to various screen sizes.

## License

This project is licensed under the MIT License. A copy of the license is explicitly included as comments in the JavaScript section of the `index.html` file and referenced in the footer.

## Contact

For any questions, feedback, or suggestions regarding this Academic Grading AI Chatbot, please feel free to reach out:

*   **Developer:** AI Web Developer
*   **Email:** aid@example.com
*   **GitHub:** [https://github.com/your-ai-dev-profile](https://github.com/your-ai-dev-profile) (Placeholder)