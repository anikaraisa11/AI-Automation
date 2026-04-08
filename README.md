# CanvasChat AI / PixelMind Image Generator
An intelligent, full-stack Image Generation SaaS that leverages the power of n8n automation and Google Gemini's creative reasoning to transform simple text into high-fidelity digital art.
# 📖 Overview 
*CanvasChat AI*  (branded as PixelMind) is designed to bridge the gap between simple user ideas and complex prompt engineering. While most generators require detailed technical descriptions to produce quality results, this platform uses an AI Agent architecture to automatically enhance user inputs, ensuring professional-grade aesthetics with every click.
# 🛠 Tech Stack
*Frontend:* Lovable (React/Vite) for a sleek, responsive user interface.
Automation Engine: n8n to orchestrate the backend logic and API communications.
LLM (The Brain): Google Gemini for intelligent prompt expansion and creative refinement.
Image Generation: Pollinations AI (Flux model) for high-speed, high-quality image rendering.
Communication: Webhook-based architecture for real-time data transfer.

# ⚙️ Key Features
*Autonomous Prompt Engineering:* Uses a Gemini-powered agent to expand basic queries into "ultra-detailed" photographic descriptions.
*High-Resolution Output:* Optimized for $1080 \times 1080$ resolution, ideal for mobile and social media content.
*Watermark-Free Rendering:* Integrated with nologo parameters for a professional SaaS feel.
*Real-Time Processing:* Fast execution via n8n's asynchronous HTTP request handling.
*Sleek Dashboard:* A modern, dark-themed UI that tracks generation history and current status.

# 🚀 How it Works
*Trigger:* The user enters a short prompt (e.g., "Cyberpunk City") into the PixelMind dashboard.
*Webhooks:* The frontend sends a POST request to an n8n Webhook node.
*Expansion:* The Google Gemini Chat Model node takes the input and rewrites it into a complex, cinematic prompt (adding lighting, style, and camera details).
*Generation:* An HTTP Request node sends the enhanced prompt to the Pollinations AI API.
*Return:* The binary image file is returned to the frontend via the Respond to Webhook node and displayed instantly to the user.

# 📥 Setup Instructions
*Frontend Deployment:* 
-Clone the repository from Lovable.
-Set up your environment variables for the n8n Webhook URL.
*n8n Workflow:*
-Import the provided .json workflow file.
-Configure your Google Gemini credentials in the AI Agent node.
-Ensure the HTTP Request node is set to GET with the URL: https://image.pollinations.ai/prompt/{{prompt}}.
*Connection:*
-Copy the Production Webhook URL from n8n and paste it into your frontend API configuration.

# 🔮 Future Enhancements
[ ] User Authentication: Sign-up/Login functionality using Supabase.

[ ] Payment Integration: Stripe gateway for credit-based image generation.

[ ] Personal Gallery: Cloud storage for users to save and download past generations.

[ ] Social Sharing: Direct-to-LinkedIn/Instagram posting features.

# 👤 Author
*Anika Raisa*
AI Automation SpecialistExpert in n8n, Langflow, and Zapier development.
