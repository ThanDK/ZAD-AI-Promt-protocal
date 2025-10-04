```
The AI Director Framework Dynamic Master Version - Corrected & Enhanced

Objective: To guide an LLM through a highly complex software development or refactoring task using an iterative, investigative process. This framework is for situations where the full scope may not be known at the outset, requiring the AI to act as a co-investigator to uncover all necessary components.

Core Philosophy: The AI is a powerful analytical engine. Its primary weakness is making assumptions. This framework forces the AI to become an active investigator, systematically mapping the project's dependencies and logic with the user's guidance before executing a single line of code.

Phase 1: Mission Kickoff & Initial Analysis

Goal: To provide the AI with the core mission and a "beachhead" of initial code. The AI's first task is to perform an immediate analysis and identify the most obvious knowledge gaps, initiating the discovery process from the very first step.

Director's Action: Start with a focused initial briefing.

Example Director Prompt:
"I am initiating a complex refactoring task. We are now in Phase 1: Mission Kickoff.
The Mission Statement: [Clearly state your objective, e.g., 'To refactor our checkout process to use a new, centralized service for handling all payment methods, and to add a new 'Saved Cards' feature to the user's profile page.']
The Technical Specifications: [e.g., 'The application is built with Vue.js and a FastAPI backend.']
Initial Dossier: I have identified these files as the most likely starting points. I may not have all the files. Your first task is to analyze these to build an initial understanding and tell me what's missing.
[--- PASTE FULL CODE FOR Checkout.vue ---]
[--- PASTE FULL CODE FOR payment_handler.py ---]
Your Task:
Confirm you have received and analyzed the initial files and the mission statement.
Perform a preliminary analysis. Based only on the files provided, list the top 1-3 most critical files or components that are imported/referenced but not provided. This is your initial request for more information.
Do not propose a plan. Do not write any code. Await my response."

Phase 2: The Director's Protocol

Goal: To establish the immutable laws of the interaction.

Director's Action: Immediately after the AI's initial analysis, set the protocol.

Example Director Prompt:
"Excellent. I will provide those files shortly. Before we proceed, you must commit to the following protocol for our entire interaction:
The Golden Rule: Never Assume. If any piece of information is missing, if a workflow is ambiguous, or if you are unsure about any aspect, you MUST stop and ask a clarifying question in the Investigation Phase. This is the most important rule.
The Execution Rule: One Step at a Time. You will not proceed to the next step or the next file until I have reviewed and given explicit approval (e.g., 'Approved,' 'Correct, proceed').
The Integrity Rule: Preserve My Standards. You will not alter my existing comments. You will adhere to my existing coding style, formatting, and naming conventions. You will not introduce any new third-party libraries without proposing and receiving explicit permission.
The Completeness Rule: Provide Full Files. When I command you to provide a file, you will provide the full, complete, and final code for that file, not snippets.
Your task: Confirm that you understand and will abide by this protocol without exception."

Phase 3: Deep Investigation & Collaborative Blueprinting

Goal: To iteratively build a complete mental model of the task through a guided Q&A, and then to formalize that understanding into an approved, multi-part plan.

Director's Action: This is a loop. You provide information, and the AI asks questions until it has everything it needs.

Example Director Prompt (Loop Start):
"Protocol confirmed. We now enter Phase 3: Deep Investigation. Here are the files you requested. Now, begin the full Q&A. Your task is to ask all questions and request all files you need to complete the mission without any guesswork. Number your questions sequentially."

AI's Expected Response (Example):
"Investigation initiated. I have analyzed the new files. To proceed, I have the following questions:
Question 1 (Missing File): The Checkout.vue component uses a useStore() function which seems to be a central part of your state management. To understand how data flows, I need to see the full code for stores/main.js.
Question 2 (Missing File): The payment_handler.py references a data model named PaymentRecord. I need to see the file defining this data model.
Question 3 (Logic Clarification): For the 'Saved Cards' feature, what is the desired behavior if a user's card is declined? Should it be automatically removed from their saved cards, or marked as 'invalid'?
Question 4 (UI Clarification): How should errors be displayed on the frontend? Should they be toast notifications, or inline messages next to the form fields?"

(The Director provides files and answers. This loop continues. At any point, the Director can ask for a status update.)

Director's Mid-Investigation Command:
"Status check: What is your current understanding of the task, and what are the key remaining knowledge gaps you are trying to fill?"

(This loop continues until the AI confirms it has no more questions.)

Director's Action (Blueprint Creation):
"Excellent. It appears you have all the information. The Investigation Phase is complete. Now, propose a strategic, multi-part blueprint. Group the steps logically (e.g., 'Part 1: Backend API Changes', 'Part 2: Frontend Component Refactoring'). For each file, briefly state the key changes. Await my approval before proceeding."

Phase 4: Directed Implementation

Goal: To execute the approved blueprint with precision, with the AI explicitly stating its reasoning at each step based on the findings from Phase 3.

Director's Action: A command-execute-review loop.

Example Director Prompt:
"The blueprint is approved. Let's begin with Part 1, Step 1: Create the new PaymentService.py. Provide the full code now."

AI's Expected Response (Example - CORRECTED AND LANGUAGE-AGNOSTIC):
"Acknowledged. Executing Part 1, Step 1.
Reasoning: As discussed in our investigation (Questions #3 and #4), this service will contain the core business logic for processing payments and will handle the 'declined card' scenario by flagging the record instead of deleting it. It is designed to be extensible for future payment methods.
[--- BEGIN FULL CODE FOR services/PaymentService.py ---]
[The full, complete, and well-commented code for the new service, adhering to all established project standards, will be provided here.]
[--- END FULL CODE FOR services/PaymentService.py ---]"

(The Director reviews the code, provides feedback or approval, and commands the next step. This loop continues until the blueprint is complete.)

Phase 4.5: The "Bug Hunt" Sub-Routine

Goal: To systematically diagnose and resolve unexpected bugs, errors, or logical inconsistencies discovered during the implementation phase (Phase 4) without derailing the main blueprint.

Trigger: This sub-routine is initiated by the Director at any point during Phase 4 if the AI's output is incorrect, causes an error, or does not meet the expected outcome.

Director's Action: When a bug is found, immediately halt the main plan and initiate the Bug Hunt.

Example Director Prompt (Initiating a Bug Hunt):
"Halt. A critical bug has been discovered. The code you provided for CartPage.jsx is causing a 400 Bad Request error when submitting the form. We are now entering Phase 4.5: Bug Hunt.

The Incident Report: [Provide a clear, concise description of the bug. Include error messages from the browser console, backend logs, and screenshots if possible. e.g., 'The browser console shows 'Failed to load resource: the server responded with a status of 400 ()'. This happens when I try to submit an order with a new address.']

Your Task:

Acknowledge the bug report.

Re-analyze the last piece of code you delivered in the context of this new error information.

Formulate a hypothesis for the root cause.

Initiate a targeted Investigation Phase by asking for the specific files or information you need to confirm your hypothesis and develop a fix. Do not propose a fix until you have all the necessary information."

AI's Expected Response (Example):
"Bug Hunt initiated. I acknowledge the 400 Bad Request error.

Hypothesis: The 400 error indicates a data validation failure. The payload object being sent from CartPage.jsx likely does not match the structure or validation rules of the backend's CreateOrderRequest.java DTO.

Investigation: To confirm this, I must compare the frontend data structure with the backend's validation rules. Please provide the full code for the following file:

in/project/computers/DTO/order/orderRequest/CreateOrderRequest.java"

(The Director and AI then engage in a focused Q&A loop, identical to Phase 3, but scoped only to the bug. Once the AI confirms it has all the information to solve the bug, the Director commands the fix.)

Director's Action (Commanding the Fix):
"Your analysis is correct. The bug hunt investigation is complete. Now, propose a plan to fix only the affected files. Then, provide the full, corrected code for the first file in your fix-plan."

(The implementation loop from Phase 4 is then used to apply the fix. Once the fix is verified and approved by the Director, the main plan resumes.)

Director's Action (Resuming the Main Blueprint):
"The fix is confirmed and working. The Bug Hunt sub-routine is complete. We will now resume our original blueprint. Proceed with Part 2, Step 1: Rework UserOrders.jsx."

Phase 5: Integration Review & Final Polish

Goal: To perform a final review of all changed components to ensure perfect cohesion and to make any minor adjustments now that the full picture is visible.

Director's Action: Ask for a summary and a final consistency check.

Example Director Prompt:
"We have completed all steps in the blueprint. We now enter Phase 5: Final Review.
Provide a summary of all files created and all files modified.
Now that all pieces are implemented, perform a final analysis. Are there any small inconsistencies or minor adjustments needed in any of the files we've worked on to make them integrate perfectly? For example, a property name that should be updated for clarity, or an API endpoint that needs a slight tweak to better match the frontend's usage. Propose any final polishing touches."
```
***
### **แนวทางการใช้งานกรอบการทำงาน (AI Director Framework)**

**บทนำ**

กรอบการทำงานนี้ถูกออกแบบมาเพื่อเปลี่ยน AI ที่มีประสิทธิภาพสูงแต่ในบางครั้งอาจคาดเดาได้ยาก ให้กลายเป็นคู่หูในการเขียนโค้ดที่แม่นยำและเชื่อถือได้ แนวคิดหลักคือให้ผู้ใช้งานทำหน้าที่เป็น **Director (ผู้ควบคุม)** ผู้มีวิสัยทัศน์ที่ชัดเจน และให้ AI ทำหน้าที่เป็นทีมปฏิบัติการที่มีศักยภาพสูง แต่ต้องการคำสั่งที่ชัดเจนและเป็นระบบในการดำเนินงาน

เอกสารนี้จะอธิบายขั้นตอนการทำงานในแต่ละระยะอย่างละเอียด

---

#### **ระยะที่ 1: การเริ่มต้นภารกิจและการวิเคราะห์เบื้องต้น (Mission Kickoff & Initial Analysis)**

*   **เป้าหมาย:** เพื่อเริ่มต้นโครงการด้วยภารกิจที่ชัดเจนและข้อมูลเบื้องต้น (ไฟล์โค้ด)
*   **ความสำคัญ:** แทนที่จะปล่อยให้ AI คาดเดาจุดเริ่มต้น ผู้ใช้งานจะเป็นผู้กำหนด "จุดเริ่มต้น" ที่ชัดเจน ซึ่งบังคับให้ AI เริ่มต้นกระบวนการด้วยการวิเคราะห์โค้ดที่มีอยู่จริง ไม่ใช่การจินตนาการโครงสร้างโค้ดขึ้นมาเอง ภารกิจแรกของ AI คือการระบุให้ได้ว่าข้อมูลสำคัญส่วนใดที่ยังขาดหายไปจากข้อมูลที่ได้รับ
*   **บทบาทของ Director (ผู้ใช้งาน):**
    1.  ระบุเป้าหมายหลักของภารกิจให้ชัดเจนในหนึ่งหรือสองประโยค
    2.  ส่งไฟล์โค้ดที่เกี่ยวข้องและสำคัญที่สุดหนึ่งถึงสองไฟล์
    3.  ไม่ควรส่งข้อมูลมากเกินไปในครั้งเดียวเพื่อป้องกันความสับสน
*   **บทบาทของ AI (นักวิเคราะห์):**
    1.  รับและทำความเข้าใจภารกิจพร้อมทั้งวิเคราะห์ไฟล์โค้ดที่ได้รับ
    2.  ทำหน้าที่ตรวจสอบและระบุไฟล์หรือส่วนประกอบที่ถูกอ้างอิงถึงแต่ยังไม่ได้รับ เพื่อร้องขอข้อมูลเพิ่มเติม
    3.  ในขั้นตอนนี้ AI จะยังไม่ได้รับอนุญาตให้เสนอการแก้ไขหรือเขียนโค้ดใดๆ ทั้งสิ้น

---

#### **ระยะที่ 2: การกำหนดระเบียบวิธีปฏิบัติ (The Director's Protocol)**

*   **เป้าหมาย:** เพื่อกำหนดชุดกฎเกณฑ์ที่ไม่สามารถเปลี่ยนแปลงได้สำหรับ AI ตลอดทั้งโครงการ
*   **ความสำคัญ:** ขั้นตอนนี้มีความสำคัญอย่างยิ่ง เปรียบเสมือนการสร้างธรรมนูญของโครงการ เพื่อป้องกันไม่ให้ AI ดำเนินการนอกเหนือขอบเขตที่กำหนดไว้ เช่น การคาดเดาข้อมูลเอง (The Golden Rule), การทำงานล่วงหน้าโดยไม่ได้รับการอนุมัติ (The Execution Rule), การแก้ไขรูปแบบโค้ดเดิม (The Integrity Rule), หรือการส่งมอบโค้ดที่ไม่สมบูรณ์ (The Completeness Rule)
*   **บทบาทของ Director:** คัดลอกและวางชุดคำสั่ง Protocol ทั้งหมด และสั่งให้ AI ยืนยันว่าจะปฏิบัติตามอย่างเคร่งครัด
*   **บทบาทของ AI:** ตอบรับว่า "ข้าพเจ้าเข้าใจและจะปฏิบัติตามระเบียบวิธีเหล่านี้โดยไม่มีข้อยกเว้น"

---

#### **ระยะที่ 3: การตรวจสอบเชิงลึกและการสร้างพิมพ์เขียวร่วมกัน (Deep Investigation & Collaborative Blueprinting)**

*   **เป้าหมาย:** ทำงานร่วมกับ AI เพื่อรวบรวมข้อกำหนด, dependency, และตรรกะทั้งหมดที่จำเป็นสำหรับงานให้ครบถ้วน จากนั้นจึงสร้างแผนการทำงานทีละขั้นตอน (พิมพ์เขียว) ที่สมบูรณ์
*   **ความสำคัญ:** ขั้นตอนนี้จะช่วยป้องกันข้อผิดพลาดส่วนใหญ่ที่อาจเกิดขึ้นในอนาคต กระบวนการถาม-ตอบระหว่างผู้ใช้งานและ AI จะช่วยให้ค้นพบรายละเอียดที่อาจถูกลืมหรือมองข้ามไป เมื่อ AI ได้รับข้อมูลครบถ้วนแล้ว พิมพ์เขียวที่สร้างขึ้นจะเป็นข้อตกลงร่วมกันเกี่ยวกับลำดับและขอบเขตของงานทั้งหมด
*   **บทบาทของ Director:**
    1.  ทำหน้าที่เป็น "แหล่งข้อมูลที่ถูกต้องที่สุด" (Source of Truth)
    2.  ตอบคำถามและจัดเตรียมไฟล์ที่ AI ร้องขออย่างครบถ้วน
    3.  เมื่อ AI ยืนยันว่าไม่ต้องการข้อมูลเพิ่มเติมแล้ว ให้สั่งการให้สร้างพิมพ์เขียวของแผนการทำงานทั้งหมด
*   **บทบาทของ AI:**
    1.  ทำหน้าที่สืบสวนอย่างละเอียด โดยการตั้งคำถามเพื่อขอไฟล์ที่ขาดหายไป, ขอความชัดเจนเกี่ยวกับตรรกะทางธุรกิจ (เช่น "จะเกิดอะไรขึ้นหากการชำระเงินล้มเหลว?"), และรายละเอียดอื่นๆ ที่จำเป็น
    2.  เมื่อสิ้นสุดกระบวนการสืบสวน ให้เปลี่ยนบทบาทเป็นสถาปนิกเพื่อนำเสนอแผนการทำงาน (พิมพ์เขียว) ที่มีโครงสร้างเป็นลำดับขั้น เพื่อให้ Director อนุมัติ

---

#### **ระยะที่ 4: การดำเนินงานตามแผนภายใต้การควบคุม (Directed Implementation)**

*   **เป้าหมาย:** เพื่อพัฒนาซอฟต์แวร์ทีละส่วนตามแผนที่ได้รับอนุมัติอย่างเคร่งครัดและแม่นยำ
*   **ความสำคัญ:** เป็นขั้นตอนของการลงมือปฏิบัติงานอย่างมีแบบแผนและควบคุมได้ AI จะไม่เพียงแค่ส่งมอบโค้ด แต่จะต้องระบุ **เหตุผล (Reasoning)** ในการดำเนินการทุกครั้ง โดยอ้างอิงถึงการตัดสินใจที่ได้ตกลงร่วมกันในระยะที่ 3 เพื่อให้มั่นใจว่าสิ่งที่กำลังสร้างนั้นถูกต้องตามวัตถุประสงค์
*   **บทบาทของ Director:**
    1.  สั่งงานตามพิมพ์เขียวทีละขั้นตอน (เช่น "เริ่มดำเนินการส่วนที่ 1 ขั้นตอนที่ 1")
    2.  ตรวจสอบโค้ดที่ AI ส่งมอบ หากถูกต้องให้ตอบกลับว่า "อนุมัติ ดำเนินการขั้นตอนต่อไป"
*   **บทบาทของ AI:**
    1.  รับคำสั่งทีละหนึ่งคำสั่ง
    2.  เขียนโค้ดฉบับสมบูรณ์สำหรับไฟล์นั้นๆ และนำเสนอเพื่อรอการตรวจสอบจาก Director

---

#### **ระยะที่ 5: การทบทวนเพื่อบูรณาการและการขัดเกลาขั้นสุดท้าย (Integration Review & Final Polish)**

*   **เป้าหมาย:** เพื่อตรวจสอบคุณภาพขั้นสุดท้ายของโค้ดที่สร้างและแก้ไขทั้งหมด เพื่อให้แน่ใจว่าทุกส่วนสามารถทำงานร่วมกันได้อย่างสมบูรณ์
*   **ความสำคัญ:** เปรียบเสมือนการตรวจสอบคุณภาพโดยรวมหลังจากประกอบชิ้นส่วนต่างๆ เข้าด้วยกัน เพื่อค้นหาและแก้ไขความไม่สอดคล้องกันเล็กน้อยระหว่างส่วนประกอบต่างๆ
*   **บทบาทของ Director:** สั่งการให้ AI สรุปภาพรวมของไฟล์ทั้งหมดที่ได้ดำเนินการไป และให้ทำการวิเคราะห์เพื่อเสนอ "การขัดเกลาขั้นสุดท้าย"
*   **บทบาทของ AI:**
    1.  ทบทวนงานที่ทำไปทั้งหมด
    2.  ตรวจสอบหารายละเอียดเล็กๆ น้อยๆ เช่น ชื่อตัวแปรที่ไม่ตรงกันระหว่าง frontend และ backend หรือเสนอการปรับปรุงเล็กน้อยเพื่อทำให้โค้ดมีความสมบูรณ์ยิ่งขึ้น
    3.  นำเสนอการเปลี่ยนแปลงเพื่อการขัดเกลาขั้นสุดท้ายให้ Director พิจารณา

การปฏิบัติตามโครงสร้างนี้จะช่วยให้ท่านได้รับผลลัพธ์ที่มีคุณภาพสูงและสามารถคาดการณ์ได้แม่นยำยิ่งขึ้น
