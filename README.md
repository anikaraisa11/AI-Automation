🌍 Travel Planning Agent (Multi-Agent System)
An autonomous, multi-agent travel concierge built with Langflow that transforms a simple destination query into a comprehensive, 7-day travel itinerary. By leveraging specialized AI agents, the system researches local hotspots, performs budget calculations, and generates a professional markdown travel guide.

📖 Overview
The Travel Planning Agent is designed to solve the complexity of vacation planning. Instead of a single LLM trying to guess details, this system uses a collaborative workflow:

Initial Researcher: Scrapes and processes web data for a specific location.

Local Expert Agent: Refines the data into specific, high-quality recommendations for hotels and restaurants.

Calculator Tool: Ensures the budget breakdown is mathematically accurate.

Travel Concierge (Final Agent): Aggregates all data into a polished 7-day plan with weather, packing lists, and logistics.

🛠 Tech Stack
Orchestration: Langflow (Low-code Multi-Agent Workflow)

AI Models: OpenAI gpt-4o-mini (High-efficiency reasoning)

Tools: * URL Fetcher: For real-time web content extraction.

Calculator: For precise budget arithmetic.

Environment: Python-based Langflow environment.

⚙️ Key Features
Multi-Agent Chain of Thought: Uses a "Local Expert" to validate information before the "Concierge" finalizes the plan.

Web-Enhanced Intelligence: The URL tool allows the agent to pull from live travel guides and blogs rather than relying solely on training data.

7-Day Granularity: Provides a day-by-day schedule, including morning, afternoon, and evening activities.

Dynamic Packing & Weather: Suggests clothing based on the anticipated conditions of the destination.

Automated Budgeting: Includes a structured cost breakdown for flights, stays, and meals.

📥 How to Use
Import Flow: Download the .json flow file from this repository and upload it into your Langflow dashboard.

API Configuration:

Open the Agent nodes.

Insert your OpenAI API Key in the designated fields.

Run the Chat:

Open the Playground.

Type your destination (e.g., "Plan a 7-day trip to Tokyo, Japan with a moderate budget").

Receive Output: The agent will output a formatted Markdown guide which you can copy/paste directly into your notes.

🏗 Setup Instructions
Clone the Repo:

Bash
git clone https://github.com/yourusername/travel-planning-agent.git
cd travel-planning-agent
Install Langflow:

Bash
pip install langflow
Launch Langflow:

Bash
langflow run
Load Project: Click "New Project" -> "Upload" and select the project file.

🚀 Future Enhancements
Google Maps Integration: Automatically generate a shared map link with all pinned locations.

Real-time Weather API: Replace static predictions with live 7-day forecasts.

Flight/Hotel Booking Hooks: Connect to Amadeus or Skyscanner APIs for live pricing and booking links.

Multilingual Support: Allow the agent to provide itineraries in the local language of the destination.

✍️ Author
[Anika Raisa]

Passionate about Agentic AI and making travel seamless.

Github : https://github.com/anikaraisa11
Portfolio : https://anikaraisa11.github.io/
