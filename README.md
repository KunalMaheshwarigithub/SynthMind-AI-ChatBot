# 🤖 SynthMind – AI Chatbot with User Sessions & Authentication

SynthMind is an intelligent, session-aware AI chatbot built with **Streamlit**, **MySQL**, and **Ollama's Gemma 2B** model. It provides a secure user authentication system, real-time conversational capabilities, and session-wise chat history tracking. The project demonstrates how to integrate large language models with modern web frameworks and backend databases for full-stack AI applications.

---

## 🚀 Features

- 🔐 **User Authentication** – Secure login and registration system with unique UserID.
- 💬 **Chat with AI** – Interact with an AI assistant powered by Ollama’s Gemma 2B model.
- 📁 **Session Management** – Conversations are grouped into sessions using UUIDs.
- 🧠 **Auto-Generated Session Titles** – First prompt auto-generates the session topic.
- 🗂️ **Chat History View** – Easily revisit previous chat sessions from the sidebar.
- 🎨 **Modern UI** – Built using Streamlit with custom CSS styling for dark mode.

---

## 🧑‍💻 Technologies Used

- **Frontend**: Streamlit (Python Web Framework)
- **Backend**: Python, MySQL
- **AI/LLM**: Ollama with Gemma 2B
- **Database**: MySQL with `user_data` and `chat_history` tables
- **Libraries**: `streamlit`, `mysql-connector-python`, `datetime`, `uuid`, `logging`

---

## 🧱 Database Schema

### `user_data` Table

| Field         | Type          | Description              |
|---------------|---------------|--------------------------|
| ID            | INT (PK)      | Auto-increment ID        |
| Name          | VARCHAR(250)  | Full Name                |
| Age           | INT           | User's Age               |
| Gender        | VARCHAR(30)   | Gender                   |
| Country       | VARCHAR(150)  | Country Name             |
| City          | VARCHAR(250)  | City Name                |
| UserID        | VARCHAR(100)  | Unique Username          |
| password      | VARCHAR(100)  | Password (plain text)    |
| RegisteredAt  | DATETIME      | Registration timestamp   |

### `chat_history` Table

| Field           | Type              | Description                           |
|------------------|-------------------|---------------------------------------|
| ID               | INT (PK)          | Auto-increment ID                     |
| UserID           | VARCHAR(100)      | Linked to `user_data.UserID`          |
| messege_role     | ENUM              | 'user' or 'assistant'                 |
| message_content  | MEDIUMTEXT        | Text of the message                   |
| DateTime         | DATETIME          | Timestamp of the message              |
| Session_ID       | VARCHAR(255)      | Unique session identifier (UUID)      |
| Session_Title    | VARCHAR(255)      | Title generated from first user input |

---

## ⚙️ How It Works

1. **Register/Login** using a simple form in the sidebar.
2. After authentication, start a new chat or select a past session.
3. Chat messages are saved along with metadata: sender, session, timestamp.
4. The first prompt of each session is used to generate a session title.
5. Sessions are displayed in the sidebar for easy retrieval.
6. Chats are handled via Ollama's Gemma 2B model and responses are rendered in real-time.

---

## 📦 Installation & Setup

1. Clone this repo:
   ```bash
   git clone https://github.com/your-username/SynthMind.git
   cd SynthMind
   
2. Install Dependencies
 ```bash
  pip install streamlit mysql-connector-python ollama

3. Set Up .streamlit/secrets.toml

   Create a file at .streamlit/secrets.toml with your MySQL credentials:
   toml
   [mysql]
   host = "localhost"
   user = "your_mysql_user"
   password = "your_password"
   database = "your_database_name"
   port = "your_port" # By deafult 3305

4. Run Ollama Locally
   Make sure Ollama is installed and running with the Gemma model:
 ```bash
   ollama run gemma:2b

5. Start the Streamlit App
 ```bash
   streamlit run app.py

## Developed by Kunal Maheshwari
