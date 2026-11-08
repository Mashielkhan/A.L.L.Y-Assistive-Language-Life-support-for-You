# A.L.L.Y — AI-Powered Assistive Companion

### Assistive Language Life Support for You

**An intelligent, voice-enabled AI companion designed to support elderly individuals living independently through proactive companionship, personalized assistance, and emergency communication.**

A.L.L.Y combines conversational AI, speech technologies, personalized user experiences, and automated emergency communication into an accessible web-based platform.

Developed by **Mashiel Khan**  
GitHub: [github.com/Mashielkhan](https://github.com/Mashielkhan)

---

## Overview

A.L.L.Y is an AI-powered assistive companion that explores how artificial intelligence can improve independent living for elderly individuals.

Older adults living independently may experience social isolation, difficulty managing daily routines, or delays in contacting others during emergencies.

A.L.L.Y addresses these challenges through a conversational interface that supports natural voice interaction, personalized reminders, proactive engagement, and emergency contact escalation.

The application emphasizes accessibility, simplicity, and a supportive user experience.

## Key Features

### 1. Proactive AI Companionship

A.L.L.Y is designed to engage users through conversational interactions rather than depending entirely on user-initiated requests.

Capabilities include:

- AI-assisted conversations.
- Proactive conversational engagement.
- Personalized reminders.
- Routine-aware interactions.
- A supportive and accessible communication experience.

### 2. Personalized User Experience

The application allows users to configure personal information that helps tailor the companion's interactions.

Configuration includes:

- Personal preferences.
- Interests and daily routines.
- Companion behavior settings.
- Emergency contact information.

Configuration data is stored through the backend using a JSON-based persistence approach.

### 3. Voice-Based Interaction

A.L.L.Y supports voice-driven communication using browser speech recognition and speech synthesis integration.

**Voice technologies:**

- Web Speech API for speech recognition.
- ElevenLabs for AI-generated voice responses.
- JavaScript for frontend interaction handling.

Voice functionality depends on browser compatibility, permissions, and configured API credentials.

### 4. Emergency Communication System

A.L.L.Y includes an emergency escalation workflow that integrates with Twilio.

The emergency system provides:

- An emergency escalation API.
- Emergency contact configuration.
- Twilio-powered outbound calling integration.
- Webhook handling for telephone interactions.
- An emergency testing endpoint.

The emergency workflow requires valid Twilio credentials and appropriate configuration.

**Safety note:** A.L.L.Y is a prototype assistive application, not a certified medical device, emergency monitoring service, or replacement for professional emergency response systems.

### 5. Interactive Companion Interface

The application features a minimalist, responsive-style web interface designed around accessibility and conversational interaction.

Interface elements include:

- Dedicated login screen.
- User configuration workflow.
- Animated AI companion sphere.
- Split-screen companion layout.
- Conversation history display.
- Voice and text interaction controls.

---

## Technology Stack

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | HTML5, CSS3, JavaScript | Web application interface |
| Backend | Python, Flask | API and application logic |
| API Communication | REST, JSON | Frontend/backend interaction |
| Cross-Origin Support | Flask-CORS | Cross-origin API communication |
| Speech Recognition | Web Speech API | Voice input |
| Voice Generation | ElevenLabs API | Natural speech responses |
| Communication | Twilio API | Emergency phone calling |
| Data Persistence | JSON Files | User configuration storage |
| Development Tunneling | ngrok | Local webhook accessibility |

## System Architecture

```text
                  +------------------------+
                  |         USER           |
                  |   Voice / Text Input   |
                  +-----------+------------+
                              |
                              v
                  +------------------------+
                  |   FRONTEND WEB APP     |
                  |  HTML / CSS / JS       |
                  |  Animated Companion    |
                  +-----------+------------+
                              |
                              v
                  +------------------------+
                  |      FLASK API         |
                  | Configuration          |
                  | Conversation Handling  |
                  | Task Scheduling        |
                  | Emergency Escalation   |
                  +-----------+------------+
                              |
             +----------------+----------------+
             |                |                |
             v                v                v
     +---------------+ +--------------+ +--------------+
     | JSON STORAGE  | | ELEVENLABS   | | TWILIO       |
     | User Config   | | Voice Output | | Phone Calls  |
     +---------------+ +--------------+ +--------------+
```

### Application Workflow

1. The user opens the A.L.L.Y web application.
2. Personal information and emergency contact details are configured.
3. The frontend communicates with the Flask backend.
4. Users interact through voice or text.
5. The application processes requests and returns conversational responses.
6. ElevenLabs generates speech when configured.
7. The backend exposes scheduled tasks for proactive interactions.
8. The emergency workflow can initiate Twilio communication when triggered.

---

## Project Structure

```text
A.L.L.Y/
|
+-- backend/
|   +-- app.py
|   +-- requirements.txt
|   +-- .env-template
|
+-- frontend/
|   +-- login.html
|   +-- [Additional frontend assets]
|
+-- README.md
```

*The structure above reflects the main components documented for the application. Additional files may be present in the repository.*

---

## Getting Started

### Prerequisites

Before running the project, ensure you have:

- Python 3.8 or later.
- pip package manager.
- A modern web browser.
- ElevenLabs API credentials for voice synthesis.
- Twilio credentials for outbound calling.

### Step 1 — Clone the Repository

```bash
git clone <YOUR-REPOSITORY-URL>
cd <YOUR-PROJECT-DIRECTORY>
```

Replace the placeholders with the actual repository URL and cloned directory name.

### Step 2 — Configure the Backend

Navigate to the backend directory:

```bash
cd backend
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Create the environment configuration file.

**Windows PowerShell:**

```powershell
Copy-Item .env-template .env
```

**Linux / macOS:**

```bash
cp .env-template .env
```

Add your API credentials to the `.env` file:

```ini
ELEVENLABS_API_KEY=your_elevenlabs_api_key

TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=your_twilio_phone_number
```

Never commit actual API credentials to GitHub.

Start the backend:

```bash
python app.py
```

### Step 3 — Launch the Frontend

Open another terminal and navigate to the frontend directory:

```bash
cd frontend
```

Start a local HTTP server:

```bash
python -m http.server 8000
```

Open the application:

http://localhost:8000/login.html

Ensure the backend is running and the frontend is configured to connect to the correct API address.

---

## API Documentation

The Flask backend exposes the following routes.

### User Configuration

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/save-config` | Save user configuration |
| GET | `/api/get-config` | Retrieve configuration |

### Conversational AI

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/ask-ai` | Process conversational input and return an AI response |
| GET | `/api/get-scheduled-tasks` | Retrieve proactive tasks |

### Emergency Communication

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/test-emergency` | Test emergency escalation |
| POST | `/twilio-webhook` | Handle Twilio webhook requests |

Exact request and response schemas should be verified against the Flask implementation.

---

## Emergency Calling Configuration

The emergency escalation system uses Twilio for phone-based communication.

### Setup

1. Create a Twilio account.
2. Obtain a Twilio-enabled phone number.
3. Configure the required environment variables.
4. Ensure the designated emergency contact number is valid.
5. Configure webhook accessibility if needed.
6. Test the integration using permitted test numbers before attempting real calls.

### Local Webhook Testing

Twilio webhooks require a reachable endpoint.

For local development, ngrok can expose your Flask server:

```bash
ngrok http 5000
```

Configure the corresponding public webhook URL in the Twilio integration.

For production deployments, webhook requests should be validated, HTTPS should be enforced, and sensitive user information should be protected.

---

## User Experience and Design

A.L.L.Y uses a clean design language intended to reduce visual complexity.

### Design Principles

- Accessibility-first interaction.
- Minimal visual distractions.
- Clear typography.
- Friendly conversational feedback.
- Consistent UI components.
- Voice-driven accessibility.

### Design System

| Component | Specification |
|---|---|
| Primary Font | Inter |
| Brand Typography | Instrument Serif |
| Primary Accent | `#61459E` |
| Secondary Accent | `#A78CDE` |
| Layout | Split-screen companion interface |
| Main Visual | Animated AI sphere |
| Design Direction | Minimal, calm, and professional |

The interface is designed to communicate trust and simplicity while maintaining a modern AI product identity.

---

## Demonstration Workflow

The application can be demonstrated through the following sequence:

**1. User Login**

Open the application and introduce the A.L.L.Y interface.

**2. Personal Configuration**

Configure personal preferences, routine information, and an emergency contact.

**3. AI Companion Interaction**

Explore the companion interface and demonstrate proactive conversational behavior.

**4. Voice Communication**

Use speech recognition to submit requests and demonstrate synthesized responses.

**5. Emergency Escalation**

Use the emergency test workflow to demonstrate Twilio integration in an authorized test environment.

---

## Engineering Considerations

The application uses lightweight technologies appropriate for rapid development and prototyping.

### Flask Backend

Flask provides a straightforward API layer for configuration management, conversational processing, and external service integration.

### Vanilla JavaScript Frontend

Using HTML, CSS, and JavaScript avoids a complex frontend build process and allows the application to run directly in compatible browsers.

### JSON-Based Storage

JSON files provide simple local configuration persistence without requiring database infrastructure.

For multi-user production deployment, a secure database with access controls would be more suitable.

### External AI and Communication Services

ElevenLabs and Twilio separate specialized voice-generation and telephony functionality from the application's core backend.

Their availability, operating costs, and API configurations must be considered when deploying the system.

---

## Current Scope and Limitations

A.L.L.Y is presented as a prototype implementation of an AI-powered assistive companion.

Important limitations include:

- Emergency communications depend on external telephony services.
- Voice recognition depends on browser support.
- JSON file storage is not intended for large-scale multi-user deployment.
- Proactive conversations depend on the backend's scheduling and task logic.
- The system is not a substitute for medical monitoring or emergency services.
- Authentication, encryption, and privacy controls require review before production deployment.

These considerations are especially important because the application may handle personal information and emergency contact details.

---

## Future Roadmap

Planned enhancements include:

- **Advanced AI integration:** More capable conversational models with improved context handling.
- **Wake-word detection:** Hands-free activation using technologies such as Picovoice.
- **Family dashboard:** Authorized family members can monitor selected activity and receive relevant updates.
- **Health integrations:** Optional connections with supported health monitoring devices and services.
- **Multilingual interaction:** Additional languages for improved accessibility.
- **Secure cloud storage:** Database-backed configuration and account management.
- **Enhanced emergency detection:** More robust detection, verification, and escalation workflows.
- **Improved accessibility:** Larger controls, keyboard navigation, readable contrast, and screen-reader support.

These features represent development opportunities rather than confirmed current functionality.

---

## Project Motivation

Artificial intelligence has applications beyond productivity and automation.

A.L.L.Y explores the potential for conversational technology to provide meaningful day-to-day assistance, particularly for people who benefit from accessible interfaces and proactive communication.

The project brings together web development, backend engineering, conversational AI integration, voice technologies, and automated communication into one practical application.

---

## Developer

**Mashiel Khan**  
BS Computer Science  
Software Development | AI Applications | Full-Stack Development

GitHub: [github.com/Mashielkhan](https://github.com/Mashielkhan)

---

**A.L.L.Y — Making independent living more connected, accessible, and supported.**
