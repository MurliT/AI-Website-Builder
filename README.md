# BuilderAI -- AI Website Builder

Build websites by describing your idea in natural language.
**BuilderAI** uses AI to generate a React project, displays the result
in a live preview, and lets users refine the website through chat-based
instructions.

## Project Overview

BuilderAI is a full-stack AI-powered website generation platform. A user
enters a prompt such as "Create a portfolio website", and the
application plans and generates the required React files. Users can
inspect the generated files, preview the website, and request changes
conversationally.

## Features

-   **AI website generation:** Turn natural-language prompts into React
    website code.
-   **Live preview:** View the generated website while working on the
    project.
-   **Chat-based editing:** Improve an existing website by asking for
    changes in plain language.
-   **Project management:** Create, save, open, update, and delete
    projects.
-   **User authentication:** Register and log in to manage personal
    projects.
-   **Cloud deployment:** Run the application on an AWS EC2 instance
    using Docker containers.
-   **Cloud database:** Store user accounts and project data in MongoDB
    Atlas.

## Screenshots

### 1. System Architecture

The architecture connects the user's browser to the React frontend
served by Nginx. The frontend communicates with the Node.js/Express API,
which uses MongoDB Atlas for persistence and OpenRouter for AI-powered
code generation.

![BuilderAI system architecture](assets/architecture-diagram.png)

### 2. BuilderAI Homepage

The homepage provides the prompt interface where users describe the
website they want to create.

![BuilderAI homepage](assets/builderai-homepage.png)

### 3. Generated Project -- File Explorer and Editor

Generated project files can be explored and inspected in the builder
interface.

![Generated project editor](assets/generated-project-editor.png)

### 4. Live Preview and Database

The generated React website is displayed in the live preview. Project
and user records are stored in MongoDB Atlas.

![Live preview and MongoDB
database](assets/live-preview-and-database.png)

## Technology Stack

  Layer              Technologies
  ------------------ --------------------------------------------------
  Frontend           React 19, Vite, Tailwind CSS
  Code preview       Sandpack
  Backend            Node.js, Express 5, REST API
  Database           MongoDB Atlas, Mongoose
  AI integration     OpenRouter API, Vercel AI SDK (`generateObject`)
  Authentication     bcrypt, JWT, secure HTTP-only cookie
  Containers         Docker, Docker Compose
  Cloud deployment   AWS EC2 (Mumbai region), Nginx

## High-Level Workflow

1.  The user enters a website idea in the BuilderAI interface.
2.  The frontend sends the request to the Express backend.
3.  The backend sends the prompt to the AI service through OpenRouter.
4.  The AI plans the project structure and generates the required files.
5.  The backend validates the generated code and stores project data in
    MongoDB Atlas.
6.  The frontend displays the generated files and renders the website
    preview.
7.  The user can request further edits through chat; edit operations are
    applied to the existing files.

## Docker and Cloud Deployment

The application is packaged into two Docker services:

-   **Client container:** Builds the React application and serves the
    production files through Nginx.
-   **Server container:** Runs the Node.js/Express API.

Docker Compose starts both services together. The deployed application
uses AWS EC2 as its cloud host and MongoDB Atlas as its managed
database.

Typical commands used to run the services:

``` bash
# Build the images
docker compose build

# Start the containers in the background
docker compose up -d

# Check container status
docker compose ps

# View application logs
docker compose logs -f
```

## Project Structure

``` text
builder-ai/
├── client/
│   └── src/
│       ├── pages/
│       ├── components/
│       └── api/
└── server/
    ├── config/
    ├── routes/
    ├── controllers/
    ├── models/
    └── services/
```

## Security Notes

-   Keep `.env` files and API keys out of GitHub.
-   Add secret files to `.gitignore` and `.dockerignore`.
-   Store credentials in environment variables rather than inside Docker
    images.
-   Restrict SSH access to trusted IP addresses.
-   Limit MongoDB Atlas network access to the required server IP.
-   Use HTTPS for production deployments.

## Learning Outcomes

This project provided practical experience with full-stack development,
AI API integration, REST APIs, authentication, database persistence,
Docker containerization, and deployment on AWS EC2.

## Project Report

The detailed project report includes the architecture, application
workflow, Docker configuration, AWS deployment steps, and implementation
screenshots.

------------------------------------------------------------------------

**Project:** BuilderAI -- AI Website Builder\
**Domain:** Cloud Computing\
**University:** Vishwakarma University, Pune
