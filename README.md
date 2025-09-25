## **AI Callcenter**

| #        | Task                                                                                             | Area    | Status  |
| -------- | ------------------------------------------------------------------------------------------------ | ------- | ------- |
| 1        | AI should remember call history as it from account transcript and offer summarize for each call  | AI      | DONE    |
| 2        | Offer appointment should be confirmed not we have then we don’t have it’s should consistent      | AI      | DONE    |
| 3        | Sort appointments in a human talk way like wait and say also and we have tomorrow talk like that | AI      | DONE    |
| 4        | AI should speak date of birth on a correct way month / day / year                                | AI      | DONE    |
| 5        | AI should not offer any medical advise only create appointment                                   | AI      | DONE    |
| 6        | AI should not use or speak emoticons                                                             | AI      | DONE    |
| 7        | Before cancel or reschedule should ask for confirm                                               | AI      | DONE    |
| 8        | Check why agent can't see opening and doctor is working 24/7                                     | AI      | DONE    |
| 9        | Action for reschule and cancelation don’t send SMS                                               | Backend | DONE    |
| 10       | sometime said executed but from UI it’s not there create/cancel                                  | AI      | DONE    |
| 11       | some time when I call with account agent don’t know my number                                    | AI & Backend | DONE    |
| 12       | sometime say doctor name that doesn’t exits                                                      | AI      | DONE    |
| 13       | should prenaouce doctors name correct every time                                                 | AI      | BLOCKED |
| 14       | If new patient don’t ask if he want anything other than create account (Logic)                   | AI      | DONE    |
| 15       | If exiting patient never ask for create account                                                  | AI      | DONE    |
| 16       | Backup for TTS                                                                                   | AI      | DONE    |
| 17       | Backup for STT                                                                                   | AI      | PENDING |
| 18       | Backup for LLM (OpenAI not supported in region)                                                  | AI      | SKIPPED |
| 19       | We need white noise                                                                              | AI      | DONE    |
| 20       | AI says the available appointments, one by one, take it easy, not this fast now.                 | AI      | PENDING |
| 21       | failsafe switch to human via ringCentral                                                         | Backend | -    |

---

---

## **Office Ally**

| Task                                                                                  | Status |
| ------------------------------------------------------------------------------------- | ------ |
| **Built Agent architecture** using LangGraph + LangChain.                             | DONE   |
| **Integrated LLM (ChatOpenAI)** with custom tools.                                    | DONE   |
| **Implemented tools** for patient/claims operations:                                  | DONE   |
| - Export patient file                                                                 | DONE   |
| - Export visit history                                                                | DONE   |
| - Export claims by provider                                                           | DONE   |
| - Claims by patient IDs                                                               | DONE   |
| - Search claims                                                                       | DONE   |
| - Search visit patient                                                                | DONE   |
| **System prompt** file for consistent AI behavior.                                    | DONE   |
| **Agent function** with trimmed messages (history management).                        | DONE   |
| **Graph flow**: agent → tools → agent (with `tools_condition`).                       | DONE   |
| **Memory management** using thread-based `MemorySaver`.                               | DONE   |
| **FastAPI layer** with endpoints:                                                     | DONE   |
| - `/ai-agent/{chat_id}` → main interaction                                            | DONE   |
| - `/ai-agent/{chat_id}/status` → status check                                         | DONE   |
| **Request/Response models** with Pydantic (`AgentRequest`, `AgentResponse`).          | DONE   |
| **Streamlit UI** for chat interface, connected to API.                                | DONE   |
| **Support for multi-chat sessions** with history.                                     | DONE   |
| **Tested scenarios**: simple chat, tool invocation, file export, failed/stalled jobs. | DONE   |

---

## **Multi-Tool Agent: Implemented APIs and Features**

| Category                             | Details                                                                                                                                                                    | Status |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| **Session Management**               | **Ping API** → check active session.<br>**Delete API** → clears session, removes context, deletes LangGraph checkpoint, cleans up session files.                           | DONE   |
| **Conversation Route**               | Injects system prompt (store/fallback).<br>Supports conversation history replay.<br>Handles attachments (downloads into `data/sessions/{chat_id}` with custom file names). | DONE   |
| **File Downloader**                  | Multiple file downloads.<br>Custom file names.<br>Streaming + chunked writing.                                                                                             | DONE   |
| **Excel Preprocessing & Validation** | Skips empty rows.<br>Ensures correct header row.<br>Validates structure before continuing.<br>Handles malformed headers with warnings.                                     | DONE   |
| **Agent Improvements**               | Smarter tool routing (`excel_query`, `scrape_website`).<br>Clearer error handling.<br>Enhanced Markdown formatting.                                                        | DONE   |

---

## **Seamless App**

| Features                        | Details                  | Status |
| ------------------------------- | ------------------------ | ------ |
| Multiple translation rooms      | Run simultaneously       | DONE   |
| Real-time communication         | Powered by LiveKit       | DONE   |
| Participant management          | With connection tracking | DONE   |
| Dynamic Language Management     | ✔                        | DONE   |
| Multiple speaker voice profiles | (speaker\_id 0–10)       | DONE   |
| VAD                             | Silence filtering        | DONE   |

### GPU Requirements (Streaming / Realtime S2ST)

| GPU           | Mode                      | Streams (SeamlessStreaming/Expressive) | Notes                                   |
| ------------- | ------------------------- | -------------------------------------- | --------------------------------------- | 
| **A100 40GB** | Real-time S2ST            | \~8–12 users                           | Depends on audio length & batching      |
| **A100 80GB** | Real-time S2ST            | \~15–20 users                          | Can pin multiple model instances        |
| **H100 80GB** | Real-time S2ST            | \~25–30 users                          | Higher throughput + faster tensor cores |
| **A100/H100** | Offline batch translation | 100+ audios/min                        | Latency less critical, batching helps   | 
---


---



