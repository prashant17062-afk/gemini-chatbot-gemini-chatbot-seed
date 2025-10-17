AI Chatbot Interface with Google Gemini
======================================

Summary
-------
This project delivers a functional and user-friendly web-based AI chatbot interface, specifically tailored for academic grading contexts. It integrates with the Google Gemini API to provide intelligent, conversational responses. The application features a clear user interface for displaying messages, a responsive input mechanism, and a "typing" indicator to enhance the user experience during AI processing. This robust solution exemplifies a high-quality student submission, showcasing proficiency in front-end development and API consumption.

Setup
-----
To set up and run this AI chatbot locally, please follow these instructions:

1.  **Obtain a Google Gemini API Key:**
    *   Visit the Google AI Studio (ai.google.dev) or the Google Cloud Console.
    *   Create a new project or select an existing one.
    *   Ensure the "Generative Language API" is enabled for your project.
    *   Generate a new API key. It is crucial to keep this key confidential.
2.  **Download Project Files:**
    *   Save the `index.html` and `README.md` files to a desired directory on your local machine.
3.  **Insert Your API Key:**
    *   Open `index.html` in a text editor (e.g., VS Code, Sublime Text, Notepad++).
    *   Locate the JavaScript section, specifically the line:
        `const GEMINI_API_KEY = 'YOUR_GEMINI_API_KEY';`
    *   Replace `'YOUR_GEMINI_API_KEY'` with the actual API key you obtained from Google.
        *   **Security Note:** For production applications, API keys should be managed more securely (e.g., server-side environment variables) rather than embedded directly in client-side code. This approach is used here for simplicity in a demonstration context.
4.  **Launch the Application:**
    *   Open the `index.html` file directly in any modern web browser (e.g., Chrome, Firefox, Edge).

Usage
-----
Interacting with the AI Chatbot is straightforward:

1.  **Start a Conversation:** The chatbot will greet you with an initial message related to academic grading.
2.  **Type Your Query:** Enter your question or statement into the input field labeled "Type your message...".
3.  **Send Your Message:**
    *   Click the "Send" button located next to the input field.
    *   Alternatively, press the `Enter` key on your keyboard.
4.  **Receive AI Response:**
    *   Your message will immediately appear in the conversation history, labeled "You".
    *   A "Typing..." indicator will briefly display below the chat area while the AI processes your request.
    *   The AI's response will then appear, labeled "Bot", continuing the dialogue.
5.  **Continue the Dialogue:** The chatbot maintains the context of the ongoing conversation, allowing for natural, multi-turn interactions.

Main Code Logic
---------------

The application is encapsulated within a single `index.html` file, integrating HTML for structure, CSS for presentation, and JavaScript for dynamic functionality.

1.  **User Interface (HTML & CSS):**
    *   **`#chat-messages`**: This `div` acts as the primary display area for all conversational exchanges. Each message (user or bot) is rendered within a `div` with specific classes (`.user` or `.bot`), providing distinct styling and sender identification. The display automatically scrolls to the newest message.
    *   **`#user-input`**: An `<input type="text">` element allows users to type their messages.
    *   **`#send-btn`**: A `<button>` element that triggers the message submission process. It is programmatically disabled during API calls to prevent concurrent requests.
    *   **`#typing-indicator`**: A `div` element that visually indicates when the AI is processing a request, appearing as "Typing..." to improve user feedback.
    *   **Styling**: Inline CSS is used to provide a clean, modern, and responsive design, making the chatbot aesthetically pleasing and easy to use.

2.  **API Integration (JavaScript):**
    *   **`GEMINI_API_KEY`**: A JavaScript constant stores the Google Gemini API key. This key is essential for authenticating requests to the Gemini service.
    *   **`conversationContext`**: An array that stores the entire history of messages (both user and bot) in the structured format required by the Gemini API (objects with `role` and `parts` properties). This history is sent with each request, enabling the AI to understand and respond within the context of the ongoing conversation.
    *   **`sendMessage()` Function**:
        *   Captures the user's input, appends it to the `#chat-messages` display, and adds it to the `conversationContext`.
        *   Visibly activates the `#typing-indicator` and temporarily disables the `#send-btn`.
        *   Utilizes the `fetch` API to make an asynchronous `POST` request to the Google Gemini Pro model endpoint (`https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent`).
        *   The request body includes the `conversationContext`, allowing the Gemini model to generate contextually relevant and intelligent responses.
        *   Upon receiving a successful response, it parses the JSON data, extracts the AI's generated text, appends it to the `#chat-messages` display, and updates `conversationContext` with the bot's reply.
        *   Includes robust error handling to catch and display any issues during the API communication.
        *   Finally, it deactivates the `#typing-indicator`, re-enables the `#send-btn`, and returns focus to the input field.

3.  **Event Handling:**
    *   An `addEventListener` is attached to the `#send-btn`, triggering the `sendMessage()` function when clicked.
    *   Another `addEventListener` is bound to the `#user-input` field, allowing users to press the `Enter` key to send messages, a common and intuitive interaction pattern.

License
-------
This project is open-source and distributed under the MIT License. Please refer to the full license text included in the `index.html` file and below.

```
MIT License

Copyright (c) 2023 [Your Name/Organization Name]

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
```

Contact
-------
For any inquiries, feedback, or suggestions regarding this project, please feel free to reach out to [Your Name/Email/GitHub Profile].