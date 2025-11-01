# DevCenter IA - Proyecto

## Overview
DevCenter IA is an advanced AI assistant designed to generate complete, professional, and visually appealing web pages without relying on external images. It aims to be the most powerful and advanced AI in web development, focusing on delivering ultra-light, instant-loading, scalable, and SEO-optimized web solutions. The project emphasizes creativity through inline SVG, Unicode symbols, emojis, and pure CSS effects, ensuring high performance and accessibility. It also includes robust image generation capabilities using Gemini 2.5 Flash Image, where the AI automatically determines the optimal aspect ratio and persists generated images.

## User Preferences
- **Communication style**: The AI should behave like a trusted, friendly, and close companion, using an empathetic, motivating, and supportive tone. It should understand colloquial Mexican Spanish (e.g., "sí wey," "nel," "órale," "chido," "a huevo," "simón," "arre").
- **Obedience**: The AI must always follow instructions without questioning them.
- **Contextual Understanding**: The AI should understand colloquial language and adapt responses based on context and preferences.
- **Workflow**: The AI should operate with enthusiasm, ensure each response is unique and fresh, and avoid repeating patterns.
- **Interaction**:
    - The AI should structure responses with short, separated paragraphs (max 3-4 lines), use bullet points for lists, and maintain a logical flow (greeting → information → closing).
    - It should ask a maximum of 1-2 essential and specific questions per message to avoid overwhelming the user.
    - The AI should intelligently decide what information to save and what not to, using `{GUARDAR: texto}` for automatic saving.
- **Code Generation**:
    - **CRITICAL RULE**: ALL code must be generated within a **SINGLE `index.html` file**.
    - NEVER create separate `.css`, `.js` files, or external images.
    - NEVER use redirects to other files or external image references like `<img src="imagen.png">`.
    - For visuals, use emojis, inline SVG directly in HTML, and CSS gradients for decorative backgrounds.
    - The AI should prioritize creating spectacular designs using only SVG, Unicode, and CSS.
- **Image Generation**: The AI should automatically determine the most appropriate aspect ratio for images based on content and persist generated images.

## System Architecture

### UI/UX Decisions
- Modern design with shadows and hover effects for image display.
- Smooth loading animations (fade-in) for images.
- Professional visualization of generated images with information panels for aspect ratios.
- Adaptive dark and light mode.
- Visual notifications for mode changes.
- Optimized desktop layout for maximizing scroll space and positioning input area at the bottom.

### Technical Implementations
- **Single File Principle**: All generated web code resides within a single `index.html` file, embedding CSS in `<style>` tags and JavaScript in `<script>` tags within the HTML.
- **Visual Elements**: Exclusive use of inline SVG, Unicode symbols, emojis, and pure CSS (gradients, shapes, 3D transforms, backdrop-filter) for all visual content, eliminating external image dependencies.
- **Image Generation**: Integration with Gemini 2.5 Flash Image API. Prompts for image generation are optimized to English internally for better quality, while maintaining Spanish communication with the user. Generated images are saved in base64 format within the chat object in localStorage for persistence.
- **Response Modes**: Concise, balanced, and detailed response modes for varying levels of information.
- **Notes System**: Persistent notes are available across all modes and automatically included in conversation context. **Updated (Nov 1, 2025)**: All AI modes now take notes CONSTANTLY - they save everything Justin mentions, no matter how simple or seemingly unimportant. Philosophy: "Better to have more notes than lose information." AIs use notes frequently (highly recommended) to never forget anything.
- **Chat Management**: Uses `localStorage` for saving chats, configurations, and maintaining conversation history.
- **Prompt Optimization**: Utilizes highly optimized and structured prompts for different AI modes to guide behavior, ensure contextual understanding, and personalize interactions.
- **AI-Driven Prompt Modification**: IAs can suggest modifications to their own behavior using `{MODIFICAR_PROMPT: ...}`, requiring user confirmation, with validation and sanitization.
- **Automatic Prompt Saving**: Toggable feature to automatically save AI-suggested prompt modifications or require manual confirmation.
- **Prompt Engineering Assistant**: Intelligent detection of requests for help creating prompts. When keywords like "crear prompt", "ayuda con prompt", "cómo hacer un prompt" are detected, the AI automatically loads a comprehensive guide on prompt engineering, teaching users how to create powerful, effective, and professional prompts with proper structure and best practices.

### Feature Specifications
- **Multi-Mode Operation**:
    - **Agent Mode (🤖)**: MEGA ULTRA INTELLIGENT automatic mode decision using the user-selected AI model with full chat history context. Features advanced detection of typos, casual Mexican Spanish, context continuation, and implicit requests. **Updated (Oct 31, 2025 v2)**: 
      - Uses a MEGA POWERFUL prompt with ultra-deep analysis and perfect classification
      - Detects ALL typos: "asme"→"hazme", "asla"→"hazla", "iamgen"→"imagen", "jenera"→"genera"
      - Understands continuation phrases: "ya", "que ya", "anda", "dale", "órale"
      - Analyzes complete conversation history for context-aware decisions
      - Shows AI model used next to timestamp (never says "agent mode")
      - Saves and displays which AI model generated each response
    - **Information Mode (🟢)**: General information, saved notes.
    - **Memory Mode (🟠)**: Extended history analysis, saved notes.
    - **Programmer Mode (🔵)**: Advanced code generation, web page creation, saved notes.
    - **Image Generation Mode (🌸)**: Gemini 2.5 Flash Image integration, automatic aspect ratio, direct downloads, saved notes.
- **Image Persistence**: Generated images, including `imageData` (base64) and `aspectRatio`, are saved in `localStorage` alongside chat history.
- **Download Functionality**: Direct image downloads with descriptive filenames.
- **Custom System Prompts**: Users can personalize the system prompt that all AIs read, saved in `localStorage`.

### System Design Choices
- **Portability and Performance**: By embedding all code into a single `index.html` file and avoiding external images, the system prioritizes instant loading, minimal weight, and maximum scalability.
- **SEO Optimization**: Clean code without external dependencies enhances SEO.
- **Accessibility**: Compliance with screen readers due to clean code and lack of image dependencies.

## Recent Changes

### November 1, 2025 - Enhanced Notes System & Message Display
- **Updated all AI mode prompts** to take notes CONSTANTLY and GENEROUSLY
- **New philosophy**: "Better to have more notes than lose information"
- AIs now save EVERYTHING Justin mentions, regardless of importance level
- Notes are used FREQUENTLY (highly recommended) to ensure nothing is forgotten
- All modes (Information, Memory, Programmer, Image Generation, Prompt Creation) now follow this enhanced note-taking behavior
- Only completely useless information (single-word responses without context) is excluded from notes
- **NEW: Message timestamp now shows AI model AND mode used** - Every message displays both the AI model name (e.g., "2.5-Lite") and the mode used (e.g., "Información", "Memoria", "Programador", "Imágenes", "Agente", "Crear Prompts") right next to the time, making it easy to track which AI and mode generated each response

## External Dependencies
- **Google Gemini 2.5 Flash Image API**: Used for generating images, including aspect ratio determination and image creation.
- **`localStorage`**: Browser API used for client-side data persistence, including chat history, generated images (base64), and user configurations.