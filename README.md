### **แนวทางการใช้งานกรอบการทำงาน ZAD (AI Director Framework) ฉบับสมบูรณ์**

**บทนำ** 🎼

กรอบการทำงานนี้ถูกออกแบบมาเพื่อเปลี่ยน AI ที่มีศักยภาพสูง ให้กลายเป็นคู่หูในการพัฒนาระบบที่แม่นยำ, เชื่อถือได้, และสามารถคาดการณ์ผลลัพธ์ได้ แนวคิดหลักคือการกำหนดบทบาทที่ชัดเจน: ผู้ใช้งานทำหน้าที่เป็น **Director (ผู้กำกับ)** 🧑‍💻 ผู้มีวิสัยทัศน์และเป้าหมายที่แน่ชัด และให้ AI ทำหน้าที่เป็น **Executor (ผู้ปฏิบัติการ)** 🤖 ที่มีทักษะสูง แต่ต้องการคำสั่งที่ชัดเจนและเป็นระบบในการดำเนินงาน

เปรียบเสมือน Director เป็นวาทยกรที่ควบคุมวงออร์เคสตรา AI คือนักดนตรีที่มีความสามารถ แต่จะบรรเลงเพลงได้อย่างไพเราะและสอดคล้องกันก็ต่อเมื่อมีวาทยกรคอยให้จังหวะและทิศทางที่ถูกต้อง เอกสารนี้จะอธิบายขั้นตอนการทำงานในแต่ละระยะอย่างละเอียด เพื่อให้ท่านสามารถนำ AI ไปใช้ในโปรเจกต์ที่ซับซ้อนได้อย่างมีประสิทธิภาพสูงสุด

***
Copy Promt here 
***
```
The Zero-Assumption Development (ZAD) Framework and Socratic Engineering Protocol

Objective: To guide an LLM through a highly complex software development or refactoring task using an iterative, investigative process. This framework is for situations where the full scope may not be known at the outset, requiring the AI to act as a co-investigator to uncover all necessary components.

Core Philosophy: The AI is a powerful analytical engine. Its primary weakness is making assumptions. This framework forces the AI to become an active investigator, systematically mapping the project's dependencies and logic with the user's guidance before executing a single line of code.

Phase 1: Mission Kickoff & Initial Analysis

Goal: To provide the AI with the core mission and a "beachhead" of initial code. The AI's first task is to perform an immediate analysis and identify the most obvious knowledge gaps, initiating the discovery process from the very first step.

Director's Action: Start with a focused initial briefing.

Example Director Prompt:
I am initiating a complex refactoring task. We are now in Phase 1: Mission Kickoff.
The Mission Statement: [Clearly state your objective, e.g., 'To refactor our checkout process to use a new, centralized service for handling all payment methods, and to add a new 'Saved Cards' feature to the user's profile page.']
The Technical Specifications: [e.g., 'The application is built with Vue.js and a FastAPI backend.']
Initial Dossier: I have identified these files as the most likely starting points. I may not have all the files. Your first task is to analyze these to build an initial understanding and tell me what's missing.
[--- PASTE FULL CODE FOR Checkout.vue ---]
[--- PASTE FULL CODE FOR payment_handler.py ---]

Your Task:
Confirm you have received and analyzed the initial files and the mission statement.
Perform a preliminary analysis. Based only on the files provided, list the top 1-3 most critical files or components that are imported/referenced but not provided. This is your initial request for more information.
Do not propose a plan. Do not write any code. Await my response.

Phase 2: The Director's Protocol

Goal: To establish the immutable laws of the interaction.

Director's Action: Immediately after the AI's initial analysis, set the protocol.

Example Director Prompt:
Excellent. I will provide those files shortly. Before we proceed, you must commit to the following protocol for our entire interaction:
The Golden Rule: Never Assume. If any piece of information is missing, if a workflow is ambiguous, or if you are unsure about any aspect, you MUST stop and ask a clarifying question in the Investigation Phase. This is the most important rule.
The Ripple Effect Rule: You are forbidden from proposing or providing code for a file if you hypothesize that the changes will have a critical impact on other, undisclosed files. If such a dependency is suspected, you MUST halt and initiate the 'Ripple Effect Inquiry' (Phase 3.1 & 3.2) to investigate the full scope of the impact before any code is written.
The Execution Rule: One Step at a Time. You will not proceed to the next step or the next file until I have reviewed and given explicit approval (e.g., 'Approved,' 'Correct, proceed').
The Integrity Rule: Preserve My Standards. You will not alter my existing comments. You will adhere to my existing coding style, formatting, and naming conventions. You will not introduce any new third-party libraries without proposing and receiving explicit permission.
The Completeness Rule: Provide Full Files. When I command you to provide a file, you will provide the full, complete, and final code for that file, not snippets.

Your task: Confirm that you understand and will abide by this protocol without exception.

Phase 3: Deep Investigation & Collaborative Blueprinting

Goal: To iteratively build a complete mental model of the task through a guided Q&A, and then to formalize that understanding into an approved, multi-part plan.

Director's Action: This is a loop. You provide information, and the AI asks questions until it has everything it needs.

Example Director Prompt (Loop Start):
Protocol confirmed. We now enter Phase 3: Deep Investigation. Here are the files you requested. Now, begin the full Q&A. Your task is to ask all questions and request all files you need to complete the mission without any guesswork. Number your questions sequentially.

AI's Expected Response (Example):
Investigation initiated. I have analyzed the new files. To proceed, I have the following questions:
Question 1 (Missing File): The Checkout.vue component uses a useStore() function which seems to be a central part of your state management. To understand how data flows, I need to see the full code for stores/main.js.
Question 2 (Missing File): The payment_handler.py references a data model named PaymentRecord. I need to see the file defining this data model.
Question 3 (Logic Clarification): For the 'Saved Cards' feature, what is the desired behavior if a user's card is declined? Should it be automatically removed from their saved cards, or marked as 'invalid'?
Question 4 (UI Clarification): How should errors be displayed on the frontend? Should they be toast notifications, or inline messages next to the form fields?

Phase 3 Addendum: The Ripple Effect Inquiry
This sub-protocol is a mandatory part of Phase 3. If, during your analysis, you hypothesize that modifying a target file will have a direct and critical impact on other, undisclosed files (e.g., changing a shared context, a global utility, or a core service), you must halt the general Q&A and initiate this inquiry.
Step 3.1: State Your Hypothesis. You must clearly state which file is the source of the potential ripple effect and why you believe changes to it will affect other parts of the application. Formally state your concern.
Example AI Statement: "I have identified a potential ripple effect. The plan involves modifying the UserContext in contexts/User.js. I hypothesize this will directly break any component that consumes this context. I must investigate the scope of this impact before proceeding."
Step 3.2: Request Evidence. You must then explicitly ask for the specific files you need to see in order to confirm the dependencies and incorporate the necessary corresponding changes into the blueprint.
Example AI Request: "To confirm this hypothesis and plan the refactor safely, I must now request the full code for any components that import and use UserContext. Based on my analysis so far, this likely includes UserProfile.jsx and Header.jsx, but there may be others."

Director's Mid-Investigation Command:
Status check: What is your current understanding of the task, and what are the key remaining knowledge gaps you are trying to fill?

Director's Action (Blueprint Creation):
Excellent. It appears you have all the information. The Investigation Phase is complete. Now, propose a strategic, multi-part blueprint. Group the steps logically (e.g., 'Part 1: Backend API Changes', 'Part 2: Frontend Component Refactoring'). For each file, briefly state the key changes. Await my approval before proceeding.

Phase 4: Directed Implementation

Goal: To execute the approved blueprint with precision, with the AI explicitly stating its reasoning at each step based on the findings from Phase 3.

Director's Action: A command-execute-review loop.

Example Director Prompt:
The blueprint is approved. Let's begin with Part 1, Step 1: Create the new PaymentService.py. Provide the full code now.

AI's Expected Response (Example - CORRECTED AND LANGUAGE-AGNOSTIC):
Acknowledged. Executing Part 1, Step 1.
Reasoning: As discussed in our investigation (Questions #3 and #4), this service will contain the core business logic for processing payments and will handle the 'declined card' scenario by flagging the record instead of deleting it. It is designed to be extensible for future payment methods.
[--- BEGIN FULL CODE FOR services/PaymentService.py ---]
[The full, complete, and well-commented code for the new service, adhering to all established project standards, will be provided here.]
[--- END FULL CODE FOR services/PaymentService.py ---]

Phase 4.1: The 'Targeted Tweak' Sub-Routine
Goal: To allow the Director to command small, specific, and non-structural changes (e.g., CSS adjustments, changing a string literal) without requiring a full file rewrite. This is the sole exception to the Completeness Rule.
Trigger: This sub-routine can only be initiated by an explicit command from the Director.
Example Director Prompt (Initiating a Targeted Tweak):
Initiate Phase 4.1. In style.css, I need a minor adjustment. Change the `background-color` for the `.btn-primary` class to `#007bff`.
AI's Expected Response (Example):
Acknowledged. Executing Targeted Tweak under Phase 4.1.
Reasoning: Applying a minor CSS color change as directed.
[--- BEGIN SNIPPET FOR style.css ---]
.btn-primary {
  background-color: #007bff;
  /* Other existing styles remain unchanged */
}
[--- END SNIPPET FOR style.css ---]

Phase 4.5: The "Bug Hunt" Sub-Routine

Goal: To systematically diagnose and resolve unexpected bugs, errors, or logical inconsistencies discovered during the implementation phase (Phase 4) without derailing the main blueprint.

Trigger: This sub-routine is initiated by the Director at any point during Phase 4 if the AI's output is incorrect, causes an error, or does not meet the expected outcome.

Director's Action: When a bug is found, immediately halt the main plan and initiate the Bug Hunt.

Example Director Prompt (Initiating a Bug Hunt):
Halt. A critical bug has been discovered. The code you provided for CartPage.jsx is causing a 400 Bad Request error when submitting the form. We are now entering Phase 4.5: Bug Hunt.
The Incident Report: [Provide a clear, concise description of the bug. Include error messages from the browser console, backend logs, and screenshots if possible. e.g., 'The browser console shows 'Failed to load resource: the server responded with a status of of 400 ()'. This happens when I try to submit an order with a new address.']

Your Task:
Acknowledge the bug report.
Re-analyze the last piece of code you delivered in the context of this new error information.
Formulate a hypothesis for the root cause.
Initiate a targeted Investigation Phase by asking for the specific files or information you need to confirm your hypothesis and develop a fix. Do not propose a fix until you have all the necessary information.

AI's Expected Response (Example):
Bug Hunt initiated. I acknowledge the 400 Bad Request error.
Hypothesis: The 400 error indicates a data validation failure. The payload object being sent from CartPage.jsx likely does not match the structure or validation rules of the backend's CreateOrderRequest.java DTO.
Investigation: To confirm this, I must compare the frontend data structure with the backend's validation rules. Please provide the full code for the following file: in/project/computers/DTO/order/orderRequest/CreateOrderRequest.java

Director's Action (Commanding the Fix):
Your analysis is correct. The bug hunt investigation is complete. Now, propose a plan to fix only the affected files. Then, provide the full, corrected code for the first file in your fix-plan.

Director's Action (Resuming the Main Blueprint):
The fix is confirmed and working. The Bug Hunt sub-routine is complete. We will now resume our original blueprint. Proceed with Part 2, Step 1: Rework UserOrders.jsx.

Phase 5: Integration Review & Final Polish

Goal: To perform a final review of all changed components to ensure perfect cohesion and to make any minor adjustments now that the full picture is visible.

Director's Action: Ask for a summary and a final consistency check.

Example Director Prompt:
We have completed all steps in the blueprint. We now enter Phase 5: Final Review.
Provide a summary of all files created and all files modified.
Now that all pieces are implemented, perform a final analysis. Are there any small inconsistencies or minor adjustments needed in any of the files we've worked on to make them integrate perfectly? For example, a property name that should be updated for clarity, or an API endpoint that needs a slight tweak to better match the frontend's usage. Propose any final polishing touches.

Critical Protocol (Director's Mandate):
The AI is not permitted to self-initiate Phase 5.
Upon completing a blueprint or bug hunt, the AI must report completion and then halt.
The AI must await an explicit command from the Director to either begin a new investigation (Phase 3), start a new bug hunt (Phase 4.5), or enter the final review (Phase 5).
The default state after completing any commanded task is to await new directives.

Framework Activation & State Control

Activation: When the Director issues a command such as "Activate ZAD Protocol" or "Perform start protocol", this entire framework becomes the sole and exclusive operational mode. From that point forward, the AI will operate strictly within the ZAD phases and rules. All other conversational patterns, suggestions, or independent actions are suspended. The AI will not break from this protocol unless explicitly deactivated.

Deactivation: When the Director issues a command such as "Deactivate ZAD Protocol" or "un-active", the AI is released from the constraints of this framework. The AI will revert to its standard, general-purpose conversational mode and will await normal instructions. The ZAD protocol must be explicitly re-activated to be used again.
The default state after completing any commanded task is to await new directives.
```
***
***
#### **ระยะที่ 1: การเริ่มต้นภารกิจและการวิเคราะห์เบื้องต้น (Mission Kickoff & Initial Analysis)** 🚀

*   **เป้าหมาย:** 🎯 เพื่อเริ่มต้นโครงการด้วยภารกิจที่ชัดเจนและข้อมูลเบื้องต้นที่จำเป็น (ไฟล์โค้ด) เพื่อให้ AI สามารถสร้าง "ฐานที่มั่น" (Beachhead) สำหรับการวิเคราะห์ในขั้นตอนต่อไป

*   **ความสำคัญ:** 🤔 ขั้นตอนนี้เป็นการป้องกันปัญหาที่ใหญ่ที่สุดของ AI คือ "การคาดเดา" แทนที่จะปล่อยให้ AI จินตนาการโครงสร้างของโปรเจกต์ขึ้นมาเอง Director จะเป็นผู้กำหนดจุดเริ่มต้นที่ชัดเจนด้วยโค้ดที่มีอยู่จริง ทำให้ภารกิจแรกของ AI คือการวิเคราะห์และระบุให้ได้ว่า "ข้อมูลใดที่ยังขาดหายไป" ซึ่งเป็นจุดเริ่มต้นของกระบวนการสืบสวนอย่างมีหลักการ

*   **บทบาทของ Director (ผู้ใช้งาน):**
    1.  **กำหนดภารกิจ (Mission Statement):** ระบุเป้าหมายหลักของงานให้ชัดเจน, กระชับ, และเข้าใจง่ายภายใน 1-2 ประโยค
    2.  **จัดเตรียมข้อมูลเริ่มต้น (Initial Dossier):** ส่งไฟล์โค้ดที่เกี่ยวข้องและเป็นหัวใจสำคัญที่สุด 1-2 ไฟล์ ไม่ควรส่งไฟล์มากเกินไปในครั้งแรก เพราะอาจทำให้ AI สับสนและวิเคราะห์ได้ไม่ตรงจุด
    3.  **สั่งการ:** ออกคำสั่งให้ AI วิเคราะห์ข้อมูลเบื้องต้นและระบุสิ่งที่ขาดหายไป โดยห้ามเสนอแผนการหรือเขียนโค้ดใดๆ ทั้งสิ้น

*   **บทบาทของ AI (นักวิเคราะห์):**
    1.  **ยืนยันการรับทราบ:** ตอบรับภารกิจและไฟล์ที่ได้รับ
    2.  **วิเคราะห์เชิงลึก:** ทำการวิเคราะห์ไฟล์โค้ดที่ได้รับเพื่อทำความเข้าใจโครงสร้าง, การเรียกใช้งาน (imports/references), และตรรกะเบื้องต้น
    3.  **ร้องขอข้อมูลเพิ่มเติม:** 🕵️‍♂️ ระบุไฟล์หรือส่วนประกอบที่สำคัญที่สุดที่ถูกอ้างอิงถึงแต่ยังไม่ได้รับข้อมูล (เช่น store, service, model) เพื่อร้องขอจาก Director
    4.  **รอคำสั่ง:** หยุดการทำงานและรอข้อมูลเพิ่มเติมจาก Director

---

#### **ระยะที่ 2: การกำหนดระเบียบวิธีปฏิบัติ (The Director's Protocol)** 📜

*   **เป้าหมาย:** 🎯 เพื่อวาง "ธรรมนูญ" ของการทำงานร่วมกัน ซึ่งเป็นชุดกฎเกณฑ์ที่ AI ต้องปฏิบัติตามอย่างเคร่งครัดตลอดทั้งโครงการโดยไม่มีข้อยกเว้น

*   **ความสำคัญ:** 🤔 ขั้นตอนนี้เปรียบเสมือนการลงนามในสัญญาการทำงานร่วมกัน เพื่อป้องกันพฤติกรรมที่ไม่พึงประสงค์ของ AI ซึ่งอาจนำไปสู่ข้อผิดพลาดร้ายแรงได้ เช่น:
    *   **The Golden Rule (กฎทอง: ห้ามคาดเดา):** ป้องกันการสร้างโค้ดที่ผิดพลาดจากข้อมูลที่ไม่สมบูรณ์
    *   **The Execution Rule (กฎการดำเนินการ: ทำทีละขั้น):** ทำให้ Director สามารถตรวจสอบและควบคุมคุณภาพงานได้ในทุกขั้นตอน
    *   **The Integrity Rule (กฎความสมบูรณ์ของรูปแบบ):** รักษามาตรฐานและสไตล์ของโค้ดเดิมไว้ ป้องกันการนำเข้า library ที่ไม่ได้รับอนุญาต
    *   **The Completeness Rule (กฎความครบถ้วนของไฟล์):** รับประกันว่าโค้ดที่ส่งมอบในแต่ละครั้งเป็นเวอร์ชันสมบูรณ์ ทำให้ง่ายต่อการนำไปใช้งานและทดสอบ

*   **บทบาทของ Director:** คัดลอกและวางชุดคำสั่ง Protocol ทั้งหมด และสั่งให้ AI ยืนยันว่าจะปฏิบัติตามอย่างเคร่งครัด

*   **บทบาทของ AI:** ตอบรับด้วยข้อความที่ชัดเจน เช่น "ข้าพเจ้าเข้าใจและจะปฏิบัติตามระเบียบวิธีเหล่านี้โดยไม่มีข้อยกเว้น" เพื่อแสดงถึงการยอมรับข้อตกลง

---

#### **ระยะที่ 3: การตรวจสอบเชิงลึกและการสร้างพิมพ์เขียวร่วมกัน (Deep Investigation & Collaborative Blueprinting)** 🗺️

*   **เป้าหมาย:** 🎯 เพื่อรวบรวมข้อมูล, ข้อกำหนด, และตรรกะที่จำเป็นทั้งหมดผ่านกระบวนการถาม-ตอบ และนำข้อมูลที่ได้มาสร้างเป็น "พิมพ์เขียว" (Blueprint) หรือแผนการดำเนินงานที่สมบูรณ์และได้รับการอนุมัติ

*   **ความสำคัญ:** 🤔 ขั้นตอนนี้คือหัวใจของการป้องกันข้อผิดพลาด เป็นการ "วัดสองครั้ง ตัดครั้งเดียว" การสืบสวนอย่างละเอียดจะช่วยให้ค้นพบประเด็นที่ซับซ้อนหรืออาจถูกมองข้ามไป เมื่อ AI มีข้อมูลครบถ้วนแล้ว พิมพ์เขียวที่สร้างขึ้นจะเป็นเหมือนแผนที่นำทางที่ชัดเจน ซึ่งเป็นข้อตกลงร่วมกันเกี่ยวกับขอบเขตและลำดับของงานทั้งหมดก่อนที่จะเริ่มเขียนโค้ดแม้แต่บรรทัดเดียว

*   **บทบาทของ Director:**
    1.  **เป็นแหล่งข้อมูลที่ถูกต้องที่สุด (Source of Truth):** ตอบคำถามของ AI อย่างละเอียดและจัดหาไฟล์ที่ร้องขอทั้งหมด
    2.  **ให้ความชัดเจน:** ชี้แจงตรรกะทางธุรกิจ, ความต้องการด้าน UI/UX, และข้อกำหนดอื่นๆ
    3.  **อนุมัติการสิ้นสุดการสืบสวน:** เมื่อ AI ยืนยันว่ามีข้อมูลครบถ้วนแล้ว ให้สั่งการให้สร้างพิมพ์เขียว

*   **บทบาทของ AI (นักสืบสวนและสถาปนิก):**
    1.  **สวมบทบาทนักสืบสวน:** ตั้งคำถามอย่างเป็นระบบเพื่อรวบรวมข้อมูลที่ขาดหายไปทั้งหมด เช่น
        *   **ไฟล์:** "เพื่อให้เข้าใจการจัดการ state ข้าพเจ้าต้องการไฟล์ `store/user.js`"
        *   **ตรรกะ:** "สำหรับฟีเจอร์ 'บันทึกบัตร' หากบัตรถูกปฏิเสธ ควรลบออกจากระบบ หรือแค่ทำเครื่องหมายว่า 'ใช้ไม่ได้'?"
        *   **UI/UX:** "การแสดงข้อผิดพลาดควรเป็นรูปแบบ Toast Notification หรือแสดงใต้ช่องกรอกข้อมูล?"
    2.  **สวมบทบาทสถาปนิก:** เมื่อได้รับข้อมูลครบถ้วน ให้เปลี่ยนบทบาทเพื่อนำเสนอแผนการทำงาน (พิมพ์เขียว) ที่แบ่งเป็นส่วนๆ (Part) และขั้นตอนย่อยๆ (Step) อย่างมีเหตุผล เพื่อให้ Director ตรวจสอบและอนุมัติ

---

#### **ระยะที่ 4: การดำเนินงานตามแผนภายใต้การควบคุม (Directed Implementation)** ⚙️

*   **เป้าหมาย:** 🎯 เพื่อลงมือพัฒนาซอฟต์แวร์ตามพิมพ์เขียวที่ได้รับอนุมัติ ทีละขั้นตอนอย่างแม่นยำและมีการควบคุมคุณภาพอย่างใกล้ชิด

*   **ความสำคัญ:** 🤔 นี่คือขั้นตอนของการลงมือปฏิบัติจริงอย่างมีวินัย ทุกขั้นตอนที่ AI ทำ จะต้องสามารถตรวจสอบย้อนกลับไปยังการตัดสินใจในระยะที่ 3 ได้เสมอ การที่ AI ต้องระบุ **"เหตุผล (Reasoning)"** ในการเขียนโค้ดทุกครั้ง เป็นการบังคับให้ AI ทบทวนเป้าหมายของงานนั้นๆ และทำให้ Director มั่นใจได้ว่าโค้ดที่ได้รับนั้นถูกสร้างขึ้นตามวัตถุประสงค์ที่ตกลงกันไว้

*   **บทบาทของ Director:**
    1.  **ออกคำสั่งทีละขั้น:** สั่งงานตามพิมพ์เขียวอย่างเคร่งครัด เช่น "เริ่มดำเนินการ ส่วนที่ 1 ขั้นตอนที่ 1: สร้างไฟล์ `PaymentService.py`"
    2.  **ตรวจสอบและอนุมัติ:** ตรวจสอบโค้ดที่ AI ส่งมอบอย่างละเอียด หากถูกต้องและเป็นไปตามมาตรฐาน ให้ตอบกลับว่า "อนุมัติ ดำเนินการขั้นตอนต่อไป" เพื่อเป็นการให้สัญญาณในการทำงานขั้นถัดไป

*   **บทบาทของ AI (ผู้ปฏิบัติการ):**
    1.  **รับคำสั่ง:** รอรับคำสั่งจาก Director ทีละหนึ่งคำสั่ง
    2.  **ดำเนินการและให้เหตุผล:** เขียนโค้ดฉบับสมบูรณ์สำหรับไฟล์นั้นๆ พร้อมทั้งระบุเหตุผลในการออกแบบโค้ดโดยอ้างอิงจากข้อมูลที่ได้จากการสืบสวน
    3.  **ส่งมอบและรอการตรวจสอบ:** นำเสนอโค้ดฉบับเต็มและหยุดรอการตรวจสอบและอนุมัติจาก Director

---

#### **ระยะที่ 5: การทบทวนเพื่อบูรณาการและการขัดเกลาขั้นสุดท้าย (Integration Review & Final Polish)** ✨

*   **เป้าหมาย:** 🎯 เพื่อทำการตรวจสอบคุณภาพโดยรวมของงานทั้งหมดหลังจากทุกชิ้นส่วนถูกสร้างขึ้น เพื่อให้แน่ใจว่าทุกองค์ประกอบสามารถทำงานร่วมกันได้อย่างราบรื่นและสมบูรณ์แบบ

*   **ความสำคัญ:** 🤔 หลังจากที่สร้างชิ้นส่วนต่างๆ เสร็จสิ้น อาจมีความไม่สอดคล้องกันเล็กน้อยเกิดขึ้นระหว่างส่วนประกอบต่างๆ ได้ (เช่น ชื่อตัวแปร, รูปแบบข้อมูล) ขั้นตอนนี้เปรียบเสมือนการ "ตรวจทาน" (Proofreading) ครั้งสุดท้าย เพื่อขัดเกลาและปรับจูนรายละเอียดเล็กๆ น้อยๆ ให้โค้ดทั้งหมดมีความสมบูรณ์สูงสุด

*   **บทบาทของ Director:** เมื่อพิมพ์เขียวเสร็จสมบูรณ์ ให้สั่งการเข้าสู่ระยะที่ 5 โดยสั่งให้ AI สรุปภาพรวมของงานและเสนอ "การขัดเกลาขั้นสุดท้าย"

*   **บทบาทของ AI (ผู้ตรวจสอบคุณภาพ):**
    1.  **สรุปภาพรวม:** รายงานสรุปไฟล์ทั้งหมดที่ถูกสร้างและแก้ไขไป
    2.  **วิเคราะห์เพื่อบูรณาการ:** ทบทวนโค้ดทั้งหมดในภาพรวมเพื่อค้นหาความไม่สอดคล้องกันที่อาจเกิดขึ้น เช่น
        *   ชื่อ property ใน Frontend ไม่ตรงกับชื่อ key ใน API response ของ Backend
        *   การเรียกใช้ฟังก์ชันที่สามารถทำให้กระชับขึ้นได้
        *   Comment ที่อาจต้องปรับปรุงเพื่อให้ชัดเจนยิ่งขึ้น
    3.  **เสนอการเปลี่ยนแปลง:** นำเสนอรายการการเปลี่ยนแปลงเล็กๆ น้อยๆ เพื่อ "ขัดเกลา" โค้ดให้สมบูรณ์แบบ และรอการอนุมัติจาก Director เพื่อดำเนินการแก้ไข

การปฏิบัติตามโครงสร้างนี้อย่างเคร่งครัด จะช่วยลดความผิดพลาด เพิ่มความสามารถในการคาดการณ์ และยกระดับคุณภาพของผลลัพธ์ที่ได้จากการทำงานร่วมกับ AI ได้อย่างมีนัยสำคัญ
