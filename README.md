***

### The AI Director Framework (Ready to Copy)

Here is the full text of the framework. You can copy and paste this to start any complex project with an AI.

---

### The AI Director Framework (Dynamic Master Version - Corrected)

**Objective:** To guide an LLM through a highly complex software development or refactoring task using an iterative, investigative process. This framework is for situations where the full scope may not be known at the outset, requiring the AI to act as a co-investigator to uncover all necessary components.

**Core Philosophy:** The AI is a powerful analytical engine. Its primary weakness is making assumptions. This framework forces the AI to become an active investigator, systematically mapping the project's dependencies and logic with the user's guidance before executing a single line of code.

---

#### **Phase 1: Mission Kickoff & Initial Analysis**

**Goal:** To provide the AI with the core mission and a "beachhead" of initial code. The AI's first task is to perform an immediate analysis and identify the most obvious knowledge gaps, initiating the discovery process from the very first step.

**Director's Action:** Start with a focused initial briefing.

**Example Director Prompt:**
"I am initiating a complex refactoring task. We are now in Phase 1: Mission Kickoff.

The Mission Statement: [Clearly state your objective, e.g., 'To refactor our checkout process to use a new, centralized service for handling all payment methods, and to add a new 'Saved Cards' feature to the user's profile page.']

The Technical Specifications: [e.g., 'The application is built with Vue.js and a FastAPI backend.']

Initial Dossier: I have identified these files as the most likely starting points. I may not have all the files. Your first task is to analyze these to build an initial understanding and tell me what's missing.

[--- PASTE FULL CODE FOR Checkout.vue ---]
[--- PASTE FULL CODE FOR payment_handler.py ---]

Your Task:
1.  Confirm you have received and analyzed the initial files and the mission statement.
2.  Perform a preliminary analysis. Based only on the files provided, list the top 1-3 most critical files or components that are imported/referenced but not provided. This is your initial request for more information.
3.  Do not propose a plan. Do not write any code. Await my response."

---

#### **Phase 2: The Director's Protocol**

**Goal:** To establish the immutable laws of the interaction.

**Director's Action:** Immediately after the AI's initial analysis, set the protocol.

**Example Director Prompt:**
"Excellent. I will provide those files shortly. Before we proceed, you must commit to the following protocol for our entire interaction:

1.  **The Golden Rule: Never Assume.** If any piece of information is missing, if a workflow is ambiguous, or if you are unsure about any aspect, you MUST stop and ask a clarifying question in the Investigation Phase. This is the most important rule.
2.  **The Execution Rule: One Step at a Time.** You will not proceed to the next step or the next file until I have reviewed and given explicit approval (e.g., 'Approved,' 'Correct, proceed').
3.  **The Integrity Rule: Preserve My Standards.** You will not alter my existing comments. You will adhere to my existing coding style, formatting, and naming conventions. You will not introduce any new third-party libraries without proposing and receiving explicit permission.
4.  **The Completeness Rule: Provide Full Files.** When I command you to provide a file, you will provide the full, complete, and final code for that file, not snippets.

Your task: Confirm that you understand and will abide by this protocol without exception."

---

#### **Phase 3: Deep Investigation & Collaborative Blueprinting**

**Goal:** To iteratively build a complete mental model of the task through a guided Q&A, and then to formalize that understanding into an approved, multi-part plan.

**Director's Action:** This is a loop. You provide information, and the AI asks questions until it has everything it needs.

**Example Director Prompt (Loop Start):**
"Protocol confirmed. We now enter Phase 3: Deep Investigation. Here are the files you requested. Now, begin the full Q&A. Your task is to ask all questions and request all files you need to complete the mission without any guesswork. Number your questions sequentially."

**(The loop continues until the AI confirms it has no more questions.)**

**Director's Action (Blueprint Creation):**
"Excellent. It appears you have all the information. The Investigation Phase is complete. Now, propose a strategic, multi-part blueprint. Group the steps logically (e.g., 'Part 1: Backend API Changes', 'Part 2: Frontend Component Refactoring'). For each file, briefly state the key changes. Await my approval before proceeding."

---

#### **Phase 4: Directed Implementation**

**Goal:** To execute the approved blueprint with precision, with the AI explicitly stating its reasoning at each step based on the findings from Phase 3.

**Director's Action:** A command-execute-review loop.

**Example Director Prompt:**
"The blueprint is approved. Let's begin with Part 1, Step 1: Create the new PaymentService.py. Provide the full code now."

**AI's Expected Response (Example):**
"Acknowledged. Executing Part 1, Step 1.

Reasoning: As discussed in our investigation (Questions #3 and #4), this service will contain the core business logic for processing payments and will handle the 'declined card' scenario by flagging the record instead of deleting it. It is designed to be extensible for future payment methods.

[--- BEGIN FULL CODE FOR services/PaymentService.py ---]
[The full, complete, and well-commented code will be provided here.]
[--- END FULL CODE FOR services/PaymentService.py ---]"

---

#### **Phase 5: Integration Review & Final Polish**

**Goal:** To perform a final review of all changed components to ensure perfect cohesion and to make any minor adjustments now that the full picture is visible.

**Director's Action:** Ask for a summary and a final consistency check.

**Example Director Prompt:**
"We have completed all steps in the blueprint. We now enter Phase 5: Final Review.

1.  Provide a summary of all files created and all files modified.
2.  Now that all pieces are implemented, perform a final analysis. Are there any small inconsistencies or minor adjustments needed in any of the files we've worked on to make them integrate perfectly? For example, a property name that should be updated for clarity, or an API endpoint that needs a slight tweak to better match the frontend's usage. Propose any final polishing touches."

***
### How to Use the Framework: A Detailed Guide for Your Friend 🧭

Hey! This framework is designed to turn a powerful but sometimes unpredictable AI into a precise and reliable coding partner. Think of yourself as a movie director and the AI as your special effects team. You have the vision; they have the power to create it, but they need crystal-clear instructions. Here’s how it works, step-by-step.

#### **Phase 1: Mission Kickoff & Initial Analysis** 🎬

*   **The Goal:** Start the project with a clear mission and some initial evidence (code files).
*   **Why it's important:** Instead of letting the AI guess where to start, you give it a "beachhead." This forces it to begin by analyzing real code, not imagining what your code *might* look like. Its first job is to tell you what's obviously missing from the puzzle pieces you just handed it.
*   **Your Job (The Director) 🧑‍🏫:** State your main goal in one or two sentences. Give it the one or two files you think are most important. That's it. Don't overwhelm it.
*   **The AI's Job (The Analyst) 🤖:** It will read your mission and analyze the files. Then, it will act like a detective and say, "Okay, to understand this, I can see I'm missing the `user_store.js` file that's imported here." It is NOT allowed to suggest code yet.

#### **Phase 2: The Director's Protocol** 📜

*   **The Goal:** To lock the AI into a set of non-negotiable rules for the entire project.
*   **Why it's important:** This is the most crucial step! It's like setting the constitution for your project. It prevents the AI from making assumptions (The Golden Rule), running ahead without you (The Execution Rule), messing up your coding style (The Integrity Rule), and giving you lazy, incomplete snippets (The Completeness Rule).
*   **Your Job:** Copy and paste the protocol prompt. Demand that the AI commits to it.
*   **The AI's Job:** To simply say, "I understand and will follow these rules."

#### **Phase 3: Deep Investigation & Collaborative Blueprinting** 🕵️➡️🗺️

*   **The Goal:** To work *with* the AI to uncover every single requirement, dependency, and piece of logic needed for the task, and then to create a step-by-step plan (a blueprint).
*   **Why it's important:** This is where you prevent 99% of future errors. By forcing the AI to ask questions, you uncover things you might have forgotten about. This back-and-forth Q&A loop continues until the AI has a complete picture. The final blueprint is your shared agreement on what will be built and in what order.
*   **Your Job:** Be the "Source of Truth." Patiently answer the AI's questions and provide the files it asks for. A few extra minutes here will save you hours of debugging later. When it has no more questions, command it to create the blueprint.
*   **The AI's Job:** Act like a relentless investigator. It will ask for missing files, clarification on business logic ("What should happen if a payment fails?"), and UI details. Once it's satisfied, it will switch hats and become an architect, presenting you with a logical, multi-part plan for your approval.

#### **Phase 4: Directed Implementation** ⚙️

*   **The Goal:** To build the software, one piece at a time, exactly according to the approved plan.
*   **Why it's important:** This is about controlled and precise execution. The AI doesn't just give you code; it first states its **Reasoning**, connecting its code directly to the decisions you both made during the Investigation Phase. This ensures it's building the right thing for the right reason.
*   **Your Job:** Be the foreman. Give one command at a time from the blueprint (e.g., "Okay, do Part 1, Step 1"). Review the code the AI provides. If it's good, say "Approved, proceed to the next step."
*   **The AI's Job:** Be the skilled engineer. It takes one task, writes the full and complete code for that single file, and presents it for review.

#### **Phase 5: Integration Review & Final Polish** ✨

*   **The Goal:** To do a final quality check on all the new and modified code to ensure everything fits together perfectly.
*   **Why it's important:** When you build a car one part at a time, you need a final check to make sure all the doors close properly and the electronics work together. This phase is about looking at the project as a whole and catching any small inconsistencies between the parts.
*   **Your Job:** Be the quality inspector. Ask for a summary of all changes and then ask the AI to perform a final review for any "polishing touches."
*   **The AI's Job:** Review all the work it just completed. It will look for things like mismatched variable names between the frontend and backend, or a small tweak that could make the code cleaner. It will propose these final, minor changes to you.

Good luck! Following this structure will give you much more predictable and high-quality results. 👍
