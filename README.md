PROJECT: ISABELLA COMPLETE SOURCE-CODE ANALYSIS, REPLICATION, AND DEVELOPMENT DIRECTIVE 1. YOUR RO

Act as a senior full-stack developer, AI architect, conversational AI engineer, frontend specialist, Three.js/VRM developer, voice systems engineer, and mobile application optimization expert.

I am uploading a ZIP archive containing the source code of my existing AI companion project, Alicia Elswarth.

Your task is to study the uploaded project thoroughly and use it as the primary reference for developing a new AI companion named ISABELLA.

Isabella should reproduce the functionality, interaction patterns, personalization, and overall experience of my existing project wherever technically possible.

This is not a request to create a generic chatbot or a superficial UI clone.

I want a functional, integrated application that preserves the useful features of the uploaded project while improving its reliability, organization, and usability.

IMPORTANT: The uploaded ZIP is the primary source of truth. Do not guess how the existing application works when you can inspect the source code.

2. FIRST TASK: READ AND ANALYZE THE ENTIRE UPLOADED ZIP 

Before changing or generating any code, inspect the uploaded ZIP archive.

You MUST perform the following steps:

Identify the project framework, language, dependencies, and application entry points. Inspect all relevant HTML, CSS, JavaScript, TypeScript, React components, configuration files, and supporting source files. Identify the existing AI integration and how API requests are handled. Examine the current conversation system and personality configuration. Inspect the current memory implementation and determine whether it uses localStorage, IndexedDB, a backend, or another mechanism. Examine all voice input, text-to-speech, audio playback, and speech synchronization code. Inspect the avatar system, including VRM/GLB loading, Three.js rendering, facial expressions, animation controllers, and camera positioning. Identify offline AI functionality, imported model handling, and model initialization logic. Inspect existing settings, menus, buttons, event listeners, and user interaction flows. Examine Supabase integration if present. Identify broken features, incomplete implementations, runtime errors, security problems, and unnecessary dependencies. Determine which features are functional, partially implemented, or missing. 

If ZIP extraction or source inspection is not supported by the current environment, clearly explain the limitation instead of claiming that you inspected the archive.

Do not assume that filenames, documentation, or comments accurately describe the current implementation. Verify the actual code.

After analysis, prepare a concise internal implementation plan and begin development.

Do not unnecessarily stop at the planning stage.

3. PROJECT IDENTITY 

The new application must be called:

ISABELLA

Use Isabella consistently throughout the application's title, settings, branding, configuration, and relevant interface elements.

Remove the Alicia Elswarth name from the new application's visible branding where appropriate.

However, do not blindly delete useful code or configuration simply because it contains the old name.

Preserve working functionality and carefully migrate the necessary project identity.

The finished product should feel like a polished, personal AI companion rather than a generic software dashboard.

4. CORE OBJECTIVE 

Build Isabella as a multimodal, personalized AI companion with these capabilities:

Natural conversational interaction. A consistent, configurable personality. Persistent conversation history. Long-term memory with user control. Gemini-powered online AI. An optional locally running offline language model. User-importable VRM avatars. Three-dimensional avatar rendering. Text-to-speech responses. Optional voice input. Conversation subtitles. Natural avatar animations when supported. Responsive mobile interface. Persistent user preferences. Optional Supabase synchronization. Reliable error handling and recovery. 

All major features must be connected to the actual application logic.

Do not implement buttons that merely look functional.

5. CONVERSATIONAL PERSONALITY SYSTEM 

Create a dedicated, editable personality configuration for Isabella.

The personality should support:

Friendly conversation. Natural language rather than robotic responses. Context-aware replies. Appropriate humor. Empathy and emotional awareness. Consistent conversational behavior. Awareness of relevant information the user previously shared. Adjustable response length and conversational style. 

The personality should remain consistent across conversations without repeatedly introducing herself or unnecessarily describing her own personality.

Implement the personality as a reusable system prompt or configuration object.

Allow the user to edit the personality through a settings interface.

Do not hardcode the entire personality into unrelated UI components.

The system should distinguish between:

Temporary conversation context. Persistent user preferences. Explicitly saved memories. Automatically generated memory suggestions. 

Users must be able to review, edit, and delete saved memories.

Never claim that Isabella remembers information permanently unless that information has actually been saved and can be retrieved.

6. ONLINE AI BRAIN — GEMINI INTEGRATION 

Integrate the online AI brain using the currently supported official Gemini SDK.

Requirements:

Use a dedicated AI provider module. Keep API configuration separate from presentation components. Support configurable model selection where available. Send conversation context appropriately. Include the active personality configuration. Retrieve relevant saved memories when appropriate. Handle loading states. Handle network failures. Handle rate limits and quota errors. Handle invalid API credentials. Handle malformed responses. Prevent duplicate submissions. Allow the user to retry failed requests. Display helpful error messages. Prevent failed requests from silently appearing successful. 

Provide a settings interface for configuring the online AI provider.

For production deployments, protect secret credentials through an appropriate backend or server-side integration.

Never expose a privileged API key in public frontend code.

Do not invent API keys or claim that a Gemini connection has been tested when it has not.

If an API key must be supplied by the user, explain the setup process.

7. OFFLINE AI BRAIN 

Implement a separate offline AI provider interface.

The user should be able to import a compatible local language model when supported by the browser and device.

The offline system should include:

Model selection. Model import or loading. Loading progress when available. Model initialization status. Inference status. Memory limitations and error handling. Model compatibility checks. Cancellation or recovery from failed initialization. A clear indication of whether the online or offline brain is active. 

Do not assume every GGUF model can run directly inside a browser.

Use a compatible local inference engine or adapter appropriate for the selected model format.

If a model requires WebGPU, WASM, a native runtime, or another dependency, check whether the current environment supports it.

Allow the application to switch between online and offline providers.

If offline inference fails, show the reason and offer the user the choice to retry or switch providers.

Do not silently send private conversations to an online provider when offline mode is selected.

Do not claim that offline AI is working until the model has loaded successfully and can generate a response.

Optimize for resource-constrained Android devices.

Avoid loading unnecessarily large models into memory.

8. PERSISTENT MEMORY SYSTEM 

Implement a reliable local-first memory architecture.

Use IndexedDB for larger structured local data and localStorage for small preferences.

The application should support:

Conversation history. Saved memories. Personality preferences. Model settings. Voice settings. Avatar preferences. Theme settings. User-controlled memory editing. Data export. Data deletion. 

Memory requirements:

Save conversation messages consistently. Restore previous conversations after refreshing the page. Prevent duplicate messages during retries. Retrieve relevant context without sending the entire conversation history every time. Keep persistent memories separate from temporary context. Allow users to delete individual conversations. Allow users to clear all locally stored conversation data. Handle corrupted or unavailable storage gracefully. 

If a backend is connected, synchronize data only according to the user's configured preferences.

Use proper user authentication and database access policies.

Do not store API secrets in ordinary localStorage.

Clearly distinguish local memory from cloud-synchronized memory.

9. THREE-DIMENSIONAL AVATAR SYSTEM 

The application must allow the user to import their own avatar.

Prioritize VRM avatar support.

Support GLB/GLTF only where the implementation can handle the relevant format correctly.

Requirements:

Import avatar files through a file picker. Validate supported file types. Display a helpful error for unsupported files. Load the avatar into a Three.js scene. Display loading progress where possible. Provide appropriate camera framing. Keep the avatar centered. Allow zooming and repositioning. Support mobile touch interactions. Handle resizing and device orientation. Dispose of unused rendering resources. Recover from avatar loading failures. Save avatar preferences persistently. 

For imported VRM avatars, use the model's available facial-expression and humanoid-rig capabilities.

Do not replace the user's imported avatar with a permanently hardcoded character.

If a model is unavailable, display a clean placeholder rather than crashing the application.

Persist avatar files locally using an appropriate browser storage mechanism when feasible.

Do not assume that a local object URL will remain valid after the page is refreshed.

10. VOICE SYSTEM 

Implement a dedicated voice subsystem.

Support text-to-speech using compatible browser capabilities or an explicitly configured speech service.

Requirements:

Voice selection. Speech rate control. Volume control. Pitch control when supported. Automatic playback of Isabella's responses when enabled. Play and stop controls. Subtitle display. Graceful handling of unavailable voices. Recovery from interrupted speech. Protection against multiple overlapping playback requests. Audio state synchronization with the conversation interface. 

Use browser speech synthesis where appropriate.

Do not assume every browser provides the same voices.

Do not promise a specific voice quality unless the selected speech provider supports it.

If the chosen voice is unavailable, offer another compatible voice.

Provide a dedicated voice settings section so the user can configure speech independently of avatar settings.

11. AVATAR ANIMATION AND SPEECH SYNCHRONIZATION 

Create a modular animation controller.

Support the following where the imported model permits:

Idle animation. Blinking. Looking toward the camera. Talking animation. Facial-expression changes. Head movement. Subtle body movement. Listening animation. Thinking animation. Smooth transitions between animation states. 

If compatible VRM facial-expression controls exist, use them appropriately.

If speech timing or phoneme data is available, synchronize mouth movement with the speech.

If phoneme information is unavailable, use a lightweight approximation while speech is playing.

Do not claim accurate lip synchronization if only approximate mouth movement is implemented.

Do not assume that every uploaded model supports every expression or gesture.

Detect supported capabilities and gracefully disable unsupported animations.

Avoid excessive animation loops that waste CPU or battery power.

12. MAIN CHAT INTERFACE 

Create a clean conversation interface that prioritizes Isabella's avatar and the user's messages.

Include:

Conversation history. User message bubbles. Isabella response bubbles or subtitles. Message input. Send button. Optional voice input button. Stop-generation button where supported. Clear loading indicators. Error messages. Retry controls. Conversation creation and selection. Clear conversation controls. Scroll-to-latest-message behavior. 

The interface must remain usable on small Android screens.

Use responsive layouts rather than fixed desktop dimensions.

Keep important controls accessible without covering the avatar.

Allow the user to hide or show the avatar panel when useful.

Preserve conversations across page reloads.

Do not create fake AI responses to make the interface appear functional.

13. OPTIONAL SUPABASE BACKEND 

If Supabase is already configured in the uploaded project, inspect and preserve the existing configuration where appropriate.

Otherwise, provide an optional integration that can be enabled by supplying the required project configuration.

Potential capabilities:

Authentication. User profiles. Conversation synchronization. Saved-memory synchronization. User preferences. Avatar metadata. Storage for user-authorized assets. 

Requirements:

Use the official Supabase client. Organize database operations in a separate service layer. Apply Row Level Security to user-specific tables. Ensure users cannot access other users' private data. Handle offline operation without requiring Supabase. Handle expired sessions and network errors. Avoid overwriting local data unexpectedly. Explain any required database schema or migration. Keep privileged service-role credentials off the frontend. Do not assume a successful connection merely because environment variables exist. 

Local operation must remain possible when Supabase is unavailable.

14. SETTINGS AND CONFIGURATION 

Create a functional settings interface with separate sections.

AI Settings Online/offline provider selection. Gemini model configuration. API connection status. Offline model import. Model status. AI response preferences. Voice Settings Voice selection. Speech rate. Volume. Pitch where supported. Automatic speech toggle. Speech playback controls. Avatar Settings Import avatar. Replace avatar. Save current avatar selection. Zoom controls. Animation preferences. Reset avatar positioning. Memory Settings View saved memories. Edit memories. Delete memories. View conversation history. Export local data. Clear local data. General Settings Light/dark theme. Interface preferences. Privacy settings. Backend synchronization preferences. Application information. 

Every control must perform its intended action.

15. PERFORMANCE AND MOBILE OPTIMIZATION 

The application must be designed for mobile browsers, including devices with limited RAM.

Optimize:

Initial application loading. Three.js rendering. Avatar loading. Texture memory. Animation loops. IndexedDB operations. Audio playback. AI request handling. Offline model initialization. 

Use lazy loading where appropriate.

Pause or reduce rendering when the application is hidden.

Avoid unnecessary component rerenders.

Dispose of Three.js resources when replacing avatars.

Avoid keeping multiple large models in memory simultaneously.

Do not automatically download large language models without the user's explicit action.

Display model size and relevant hardware requirements when known.

Never promise compatibility with a device without testing it.

16. SECURITY AND PRIVACY 

Treat user conversations, memories, and uploaded assets as private data.

Requirements:

Never hardcode real API credentials into source files. Never expose Supabase service-role keys. Validate uploaded files. Avoid unsafe HTML rendering. Sanitize user-controlled content where necessary. Protect private database records through authentication and access policies. Avoid transmitting local conversations without the configured provider requiring it. Clearly disclose when a conversation is sent to an online AI service. Make cloud synchronization optional where feasible. Provide local data deletion controls. 

Do not place real secrets in the generated ZIP, public repository, or client-side source code.

17. PROJECT STRUCTURE AND CODE QUALITY 

Organize the code into logical modules.

Possible structure:

src/ components/ Chat/ Avatar/ Voice/ Settings/ Layout/ services/ ai/ voice/ memory/ avatar/ supabase/ hooks/ stores/ utils/ styles/ config/ types/

Adapt this structure to the actual project framework.

Do not duplicate existing modules unnecessarily.

Do not introduce dependencies without a clear reason.

Keep AI providers, memory operations, voice functionality, avatar rendering, and presentation components separate.

Use clear naming, consistent error handling, and maintainable TypeScript types where applicable.

18. TESTING REQUIREMENTS 

Test all feasible workflows.

Conversation Send a message. Receive a genuine AI response. Handle a failed request. Retry a failed request. Restore conversation history. Online AI Configure the provider. Handle missing credentials. Handle quota errors. Handle network failures. Offline AI Import a compatible model. Display loading progress where available. Generate a response. Recover from model initialization failure. Switch providers. Memory Save a conversation. Reload the application. Restore saved messages. Edit and delete memories. Clear local data. Avatar Import a compatible VRM. Render the avatar. Adjust camera framing. Test touch controls. Replace the avatar. Handle invalid files. Voice Select an available voice. Play a response. Stop speech. Display subtitles. Handle missing voices. Prevent overlapping playback. Deployment Build the production application. Inspect console errors. Verify environment configuration. Check direct page reloads. Verify API requests use the correct endpoint and configuration. 

Fix discovered problems rather than merely listing them.

Do not mark a test as passed unless it was actually executed or otherwise verified.

19. FINAL DELIVERABLES 

Deliver the following:

The complete Isabella source code. All necessary frontend components. Integrated online AI provider. Offline model integration where supported. Persistent local memory. Avatar import and rendering. Voice selection and speech output. Avatar animation integration. Functional settings. Optional Supabase integration. Required configuration examples without real secrets. A README containing setup and deployment instructions. A list of required environment variables. Instructions for configuring the Gemini API. Instructions for importing offline models. Instructions for connecting Supabase. A summary of completed features. A transparent list of features that remain incomplete and why. 

If the environment supports creating downloadable project archives, package the finished source code into a ZIP archive.

Do not claim to have created a downloadable ZIP if the environment has not actually generated one.

20. ABSOLUTE DEVELOPMENT RULES Read the uploaded ZIP before making architectural decisions. Preserve useful existing functionality. Do not overwrite working code without a clear reason. Do not produce a superficial prototype when a functional implementation is possible. Do not leave fake buttons or disconnected settings. Do not invent successful API responses. Do not hardcode API secrets. Do not silently remove offline capabilities. Do not replace user-imported avatars with a hardcoded character. Do not claim unsupported model compatibility. Do not conceal build errors. Do not stop after producing an implementation plan. Do not ask me to repeat information that can be discovered by inspecting the uploaded files. If an essential detail is missing, make a reasonable, documented decision and continue. If an external service requires credentials, implement the integration and explain the necessary setup. If a feature is impossible in the current environment, explain the limitation and implement the best supported alternative. FINAL OBJECTIVE 

Transform the uploaded Alicia Elswarth source project into a functional AI companion named ISABELLA.

Use the uploaded project to understand its existing implementation, preserve the useful features, repair problems where feasible, and develop the closest technically achievable reproduction of its intended experience.

Start by inspecting the uploaded ZIP archive.

Then implement the project, verify the integration, and prepare the final deliverables.

Prioritize actual functionality, reliability, privacy, and maintainability over appearance alone.



