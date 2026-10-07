# BASE44 MASTER BUILD COMMAND — TRINITY AI + JARVUS

Build the production application **TRINITY AI COMMAND CENTER** as one unified full-stack Base44 system.

This is not two apps connected together. It is one coherent product.

**Trinity AI** is the parent intelligence and operations platform.
**Jarvus** is Trinity AI's primary conversational assistant, tool operator, context interface, and action orchestration layer.

The source-of-truth repository is:

**GitHub: loukennedy1-design/Trinity-Jarvus**

The repository includes:
- `TRINITY_BUILD_SPEC.md`
- `trinity-bizai.zip`

Treat the uploaded Trinity ZIP/code as source material to preserve useful working functionality from, but rebuild/refactor it into the unified architecture below. Do not preserve duplicate application shells, duplicate AI assistants, duplicate dashboards, duplicate data models, obsolete navigation, dead code, mock-only features, or hard-coded backend dependencies.

## PRIMARY BUILD RULE

For every useful incoming feature, classify it internally as:

- **KEEP** — working unique functionality that fits the target system.
- **REFACTOR** — useful functionality that must be moved into the new architecture.
- **MERGE** — overlapping functionality that belongs in a canonical unified module.
- **REPLACE** — functionality whose implementation conflicts with the target architecture.
- **REMOVE** — duplicate, obsolete, mock-only, insecure, dead, or superseded functionality.

Never remove a working feature until its replacement is functioning.

Build and verify in phases. Keep the app runnable at the end of every phase.

---

# 1. PRODUCT IDENTITY

Product name:

**TRINITY AI COMMAND CENTER**

Primary AI operator:

**JARVUS**

Trinity AI is the system.
Jarvus is the conversational intelligence and action interface into the system.

The product must feel like one enterprise-grade AI command center, not several apps stitched together.

The final system should allow authenticated users to:

- converse with Jarvus
- maintain persistent conversation history
- create and manage tasks
- create and manage projects
- store and retrieve memory
- maintain a knowledge base
- manage contacts
- manage calendar events
- upload and associate files
- review recent activity
- receive notifications
- create workflows
- create automations
- approve or reject AI/workflow actions
- use global search
- use a global command palette
- manage settings
- use integrations
- access an admin area when authorized

---

# 2. TARGET APPLICATION ARCHITECTURE

Use a modular architecture.

Do not build giant page components.
Do not scatter direct Base44 SDK calls throughout UI components.

Organize the frontend conceptually as:

```
src/
  app/
    AppShell
    Router
    AuthProvider
    CommandPalette

  components/
    navigation/
    cards/
    tables/
    forms/
    dialogs/
    feedback/

  features/
    command-center/
    trinity/
    jarvus/
    tasks/
    projects/
    memory/
    knowledge/
    contacts/
    calendar/
    files/
    activity/
    notifications/
    workflows/
    automations/
    approvals/
    integrations/
    settings/
    admin/

  services/
    apiClient
    authService
    trinityService
    jarvusService
    contextService
    taskService
    projectService
    memoryService
    knowledgeService
    contactService
    eventService
    fileService
    activityService
    notificationService
    workflowService
    automationService
    approvalService
    integrationService

  config/
```

Base44 resources should conceptually live under:

```
base44/
  entities/
  functions/
  agents/
  connectors/
```

Prepare a future backend boundary:

```
server/
  README.md
  app/
  api/
  agents/
  services/
  workers/
```

Do not attempt to run the Python server inside the Base44 frontend now.
The `server/` structure is a future migration boundary.

---

# 3. BACKEND ABSTRACTION — MANDATORY

Create a centralized configuration layer with:

- `API_BASE_URL`
- `WS_BASE_URL`
- `USE_EXTERNAL_BACKEND`
- `APPLICATION_ENVIRONMENT`

Default:

```
USE_EXTERNAL_BACKEND = false
```

During the Base44 phase, services use Base44 entities/functions/agents.

Later, the same services must be able to call an external Python backend without rewriting the UI.

Frontend code should call methods like:

- `getCurrentUser()`
- `getDashboardData()`
- `getConversations()`
- `createConversation()`
- `sendJarvusMessage()`
- `getTasks()`
- `createTask()`
- `updateTask()`
- `getProjects()`
- `createProject()`
- `getMemories()`
- `saveMemory()`
- `searchMemory()`
- `searchKnowledge()`
- `getContacts()`
- `getEvents()`
- `getActivity()`
- `getNotifications()`
- `createWorkflow()`
- `runWorkflow()`
- `createAutomation()`
- `executeAction()`
- `approveAction()`

Do not bind screens directly to backend-specific implementation details.

---

# 4. APPLICATION SHELL

Build a responsive application shell.

Desktop:
- persistent left navigation
- top command/status bar
- central workspace
- optional right context panel

Mobile/tablet:
- collapsible navigation
- responsive cards
- touch-friendly controls
- Jarvus always easy to access

Primary navigation:

1. Command Center
2. Jarvus
3. Tasks
4. Projects
5. Memory
6. Knowledge
7. Contacts
8. Calendar
9. Files
10. Activity
11. Notifications
12. Workflows
13. Automations
14. Approvals
15. Integrations
16. Settings
17. Admin

Admin must only appear for authorized admin users.

Use a professional dark command-center visual system:
- strong hierarchy
- clean typography
- dark neutral surfaces
- restrained accent colors
- subtle glass/transparency only where useful
- readable tables/forms
- consistent spacing
- responsive layouts

Do not make the interface gimmicky or excessively science-fiction themed.

---

# 5. COMMAND CENTER

Create the main operational dashboard.

Include:

- current user greeting
- current date
- Trinity/Jarvus system status
- Jarvus daily briefing
- priority tasks
- overdue tasks
- tasks due today
- active projects
- upcoming events
- pending approvals
- workflow status
- automation health
- recent activity
- notifications
- recent conversations
- AI recommendations
- system alerts
- quick actions

Quick actions:

- Ask Jarvus
- Create Task
- Create Project
- Add Memory
- Add Knowledge
- Add Contact
- Create Event
- Create Workflow
- Create Automation
- Upload File

If the incoming Trinity code contains useful dashboard widgets, merge them into this Command Center instead of keeping multiple competing home dashboards.

---

# 6. JARVUS AI

Jarvus is the main conversational intelligence interface.

Build:

- new conversation
- conversation history
- searchable conversation list
- persistent messages
- timestamps
- conversation titles
- rename
- pin
- archive
- delete with confirmation
- markdown rendering
- code blocks
- copy actions
- retry/regenerate
- loading states
- error states
- responsive chat UI

Jarvus modes:

- General Assistant
- Command Center
- Research
- Operations
- Planning
- Project Manager
- Analyst
- Developer
- Administrator

Store the selected mode with the conversation.

Add a context panel capable of showing:

- relevant memories
- related tasks
- related projects
- relevant knowledge
- related contacts
- relevant files
- pending actions
- suggested next steps

Jarvus must be structured to use tools/actions such as:

- `create_task`
- `update_task`
- `create_project`
- `save_memory`
- `search_memory`
- `search_knowledge`
- `create_event`
- `create_contact`
- `run_workflow`
- `create_automation`
- `retrieve_dashboard_context`

Destructive, external, high-impact, or irreversible actions must require confirmation or go through the approval queue.

If incoming Trinity code contains AI chat functionality, merge useful prompt behavior, tools, history, context handling, and UI into Jarvus. Do not keep a second competing assistant.

---

# 7. CONTEXT ENGINE

Create a centralized context assembly service/function.

For a Jarvus request, retrieve only relevant information.

Potential context sources:

- authenticated user
- current conversation
- recent conversation messages
- pinned memories
- high-importance memories
- relevant memories
- active tasks
- relevant projects
- relevant knowledge
- contacts
- events
- files
- pending action requests
- system instructions

Do not dump entire databases into every AI call.

Design the system for future retrieval-based and semantic search.

---

# 8. CANONICAL BASE44 DATA ENTITIES

Create or normalize the following entities:

## Conversation
Fields:
- title
- user_id
- mode
- status
- pinned
- archived
- last_message_at
- created_date
- updated_date

## Message
Fields:
- conversation_id
- user_id
- role
- content
- metadata
- status
- created_date

Roles:
- user
- assistant
- system
- tool

## Memory
Fields:
- title
- content
- type
- importance
- tags
- related_project_id
- related_contact_id
- source_conversation_id
- status
- last_accessed
- access_count

Memory types:
- preference
- person
- organization
- project
- decision
- fact
- instruction
- process
- objective
- context
- custom

Importance:
- low
- normal
- high
- critical

## KnowledgeItem
Fields:
- title
- content
- summary
- category
- tags
- source_type
- source_url
- file_reference
- related_project_id
- status

## Task
Fields:
- title
- description
- status
- priority
- due_date
- start_date
- completed_date
- owner
- assigned_to
- project_id
- parent_task_id
- tags
- source
- created_from_conversation_id
- estimated_duration
- progress
- notes

Task statuses:
- inbox
- planned
- in_progress
- blocked
- waiting
- completed
- cancelled

Priorities:
- low
- normal
- high
- urgent
- critical

## Project
Fields:
- name
- description
- status
- priority
- owner
- start_date
- target_date
- progress
- objectives
- notes
- tags

Project statuses:
- proposed
- planning
- active
- paused
- completed
- cancelled

## ProjectMember
Fields:
- project_id
- user_id
- role
- status

## Contact
Fields:
- first_name
- last_name
- display_name
- organization
- title
- email
- phone
- website
- notes
- tags
- relationship
- status

## Event
Fields:
- title
- description
- start_time
- end_time
- all_day
- location
- status
- project_id
- contact_ids
- source
- external_id

## FileAsset
Fields:
- filename
- display_name
- file_url
- mime_type
- size
- category
- tags
- project_id
- uploaded_by

## Activity
Fields:
- event_type
- title
- description
- actor
- entity_type
- entity_id
- metadata
- severity
- timestamp

## Notification
Fields:
- user_id
- title
- message
- type
- priority
- read
- related_entity_type
- related_entity_id
- action_url

## Workflow
Fields:
- name
- description
- status
- trigger_type
- steps
- owner
- related_project_id
- tags
- execution_count
- last_run

Statuses:
- draft
- active
- paused
- archived

Trigger types:
- manual
- scheduled
- entity_event
- future_api_event

Supported logical step types:
- create_task
- update_record
- send_notification
- call_jarvus
- call_function
- future_api_request
- wait
- condition

## WorkflowRun
Fields:
- workflow_id
- status
- started_at
- completed_at
- result
- error
- metadata

## Automation
Fields:
- name
- description
- status
- trigger
- trigger_config
- action_type
- action_config
- last_run
- next_run
- run_count
- failure_count

Statuses:
- active
- paused
- error
- disabled

## AutomationRun
Fields:
- automation_id
- status
- started_at
- completed_at
- result
- error

## ActionRequest
Fields:
- title
- description
- requested_action
- payload
- source
- status
- requested_by
- approval_required
- resolved_date

Statuses:
- pending
- approved
- rejected
- executed
- failed

## UserPreference
Fields:
- user_id
- default_jarvus_mode
- theme
- timezone
- notification_preferences
- dashboard_preferences
- ai_preferences

## SystemSetting
Fields:
- key
- value
- category
- description
- restricted

If incoming Trinity code uses overlapping entities such as Todo, Job, Lead, Note, AssistantThread, AIMessage, ProjectTask, Customer, Reminder, or similar models, merge or map them into these canonical entities unless their meaning is genuinely distinct.

---

# 9. TASKS

Build complete CRUD task management.

Views:
- My Tasks
- Today
- Upcoming
- Overdue
- Inbox
- Completed
- All Tasks

Include:
- search
- filters
- sorting
- task details
- subtasks
- project relationship
- status updates
- progress
- priority
- due dates

Jarvus must be able to create and update tasks through approved tool actions.

---

# 10. PROJECTS

Build:

- card view
- list/table view
- project detail

Project detail tabs/sections:

- Overview
- Tasks
- Activity
- Notes
- Memories
- Knowledge
- Files
- Milestones
- Jarvus Conversations

---

# 11. MEMORY

Create dedicated memory management.

Support:

- create
- edit
- archive
- delete
- pin
- search
- filter
- tagging
- related projects
- related contacts
- save memory from Jarvus conversations

Jarvus should use relevant memory context, not all memory.

---

# 12. KNOWLEDGE

Create persistent knowledge management.

Support:

- notes
- procedures
- documentation
- project knowledge
- company knowledge
- source URLs
- file references
- categories
- tags
- search

Use the best Base44-supported search approach now.

Design `knowledgeService.search()` so it can later switch to Python/vector search.

---

# 13. CONTACTS

Build CRUD contacts.

Allow contacts to relate to:

- tasks
- projects
- memories
- conversations
- events
- activity

---

# 14. CALENDAR / EVENTS

Build internal event management.

Include:

- upcoming events
- agenda view
- event details
- create/edit/delete
- project associations
- contact associations

Keep the service architecture ready for Google Calendar integration later.

---

# 15. FILES

Build a File Assets area.

Allow files to associate with:

- projects
- tasks
- knowledge
- conversations

Provide clear upload, list, metadata, and linking experiences.

---

# 16. ACTIVITY

Record meaningful system events including:

- task created
- task completed
- project created
- project changed
- memory saved
- conversation created
- workflow executed
- automation executed
- contact created
- event created
- file uploaded
- system event

Display recent activity on Command Center and a full Activity page.

---

# 17. NOTIFICATIONS

Build an internal notification system with:

- header notification bell
- unread count
- read/unread
- priority
- related entity
- navigation/action URL

---

# 18. WORKFLOWS

Build reusable workflow definitions and workflow-run history.

Start with a practical builder/editor, not an overengineered graphical node editor.

Users must be able to:

- create
- edit
- activate
- pause
- archive
- manually run
- inspect run history

The data structure must support future Python execution.

---

# 19. AUTOMATIONS

Build automations separately from workflow definitions.

Support:

- manual/scheduled/entity-event trigger concepts
- Base44-supported execution now
- run history
- next run
- failures
- status
- pause/resume

Keep automation execution behind `automationService` so scheduling can later move to Python/Celery or another worker platform.

---

# 20. APPROVAL QUEUE

Build a centralized action approval queue.

Jarvus, workflows, and automations should use this when an action requires user permission.

Users must be able to:

- review requested action
- inspect payload/context
- approve
- reject
- see execution result
- see failures

Show pending requests on Command Center.

---

# 21. GLOBAL SEARCH

Create global search across:

- conversations
- tasks
- projects
- memories
- knowledge
- contacts

Group results by type.

Abstract search behind a service so semantic/vector search can replace or augment it later.

---

# 22. COMMAND PALETTE

Add Ctrl/Cmd + K command palette.

Commands:

- Ask Jarvus
- Create Task
- Create Project
- Add Memory
- Search Knowledge
- Add Contact
- Create Event
- Open Command Center
- Open Tasks
- Open Projects
- Open Jarvus
- Open Settings

---

# 23. SETTINGS

Build sections for:

- Profile
- Jarvus
- Notifications
- Appearance
- Integrations
- Security
- System

Allow user preferences for:

- display name
- avatar
- default Jarvus mode
- theme
- timezone
- notifications
- dashboard preferences
- AI behavior preferences

---

# 24. ADMIN

Admin-only area.

Include where Base44 capabilities allow:

- user management
- system metrics
- entity counts
- recent activity
- automation health
- AI/Jarvus usage summaries
- configuration
- integration status
- system logs

Do not render admin controls to non-admin users.

---

# 25. SECURITY

Use authenticated user context.

Apply row-level security where appropriate.

Personal entities should be user-scoped by default, especially:

- Conversation
- Message
- Memory
- Notification
- UserPreference
- personal Tasks

Never rely only on hiding UI for authorization.

Do not hard-code user IDs.

Do not expose secrets in frontend code.

Do not place provider API keys directly in browser-visible code.

Use Base44 secrets/backend functions for sensitive integrations.

---

# 26. ERROR HANDLING

Every major page/module must have:

- loading state
- empty state
- permission-denied state
- error state
- retry action where useful

Do not expose raw implementation errors to normal users.

---

# 27. PERFORMANCE

Do not load all entities at startup.

Load data by route/module.

Use reasonable query limits and pagination where needed.

Avoid unnecessary duplicate requests.

Avoid unnecessary AI calls.

Cache/reuse context appropriately when safe.

---

# 28. INCOMING TRINITY ZIP MERGE

Treat `trinity-bizai.zip` as source material.

Preserve:

- unique working Trinity business functionality
- useful reusable UI
- useful forms
- working logic
- useful workflows
- valid data concepts
- good interaction patterns
- relevant AI behavior

Refactor:

- direct backend calls
- monolithic components
- hard-coded config
- inconsistent navigation
- repeated styles
- duplicated state logic
- old API utilities
- tightly coupled AI calls

Merge:

- duplicate chat systems into Jarvus
- duplicate dashboards into Command Center
- overlapping tasks into Task
- overlapping projects into Project
- notes/context into Memory or KnowledgeItem as appropriate
- people/customers into Contact when semantically correct
- workflow/automation concepts into canonical modules

Replace:

- conflicting application shells
- competing assistant interfaces
- insecure auth patterns
- direct frontend secret usage
- backend-specific calls embedded in pages
- duplicate routers/navigation
- mock-only core functionality where working Base44 functionality can be used

Remove only after replacement works:

- dead routes
- dead components
- obsolete branding
- duplicate screens
- duplicate models
- fake/demo-only logic not needed
- unused packages
- legacy application shells

---

# 29. BASE44 IMPLEMENTATION

Use Base44 for the current functioning backend:

- authentication
- entities
- backend functions
- agents
- automations
- connectors
- hosting

Use Base44 entity schemas for canonical data.

Use Base44 backend functions for operations requiring server-side logic or secrets.

Use a Base44 agent configuration for Jarvus where appropriate.

Jarvus agent tools should have only the entity/function permissions required for their work.

Use Base44 automations for scheduled/entity-triggered behavior supported now.

Do not hardwire the application so these cannot later be moved to Python.

---

# 30. FUTURE PYTHON API CONTRACT

Prepare services to later support endpoints such as:

- `POST /api/jarvus/chat`
- `GET /api/context`
- `GET /api/tasks`
- `POST /api/tasks`
- `PATCH /api/tasks/:id`
- `GET /api/projects`
- `POST /api/projects`
- `GET /api/memories`
- `POST /api/memories`
- `POST /api/search`
- `POST /api/workflows/:id/run`
- `GET /api/activity`
- `GET /api/notifications`
- `POST /api/actions/:id/approve`

Prepare architecture for later:

- FastAPI
- PostgreSQL
- Redis
- vector search
- WebSockets
- background workers
- external integrations
- server-side AI orchestration

Do not make the current Base44 build depend on these future services.

---

# 31. BUILD PHASES

Execute in this order.

## PHASE 1 — FOUNDATION
Build:
- app shell
- navigation
- auth-aware layout
- config
- centralized service layer
- shared components
- Command Center
- command palette

Verify all navigation and responsive behavior.

## PHASE 2 — JARVUS
Build:
- Conversation
- Message
- chat UI
- conversation history
- Jarvus modes
- context panel
- Base44 agent/AI integration
- tool/action interfaces

Verify persistent conversation behavior.

## PHASE 3 — CORE OPERATIONS
Build:
- Tasks
- Projects
- Contacts
- Events
- Files
- Activity
- Notifications

Verify CRUD and relationships.

## PHASE 4 — INTELLIGENCE
Build:
- Memory
- Knowledge
- context engine
- Jarvus context retrieval
- global search

Verify that Jarvus gets selective relevant context.

## PHASE 5 — WORKFLOWS
Build:
- Workflow
- WorkflowRun
- Automation
- AutomationRun
- ActionRequest
- approval queue

Verify execution logging and approval behavior.

## PHASE 6 — SYSTEM
Build:
- Settings
- UserPreference
- Integrations
- Admin
- security pass
- responsive polish
- error handling

## PHASE 7 — PYTHON-READY BOUNDARY
Verify:
- all frontend backend access goes through services
- Base44 adapter is isolated
- external API configuration exists
- future API adapter placeholders exist
- WebSocket configuration exists
- migration documentation exists

---

# 32. QUALITY RULES

Do not create major placeholder pages saying only "Coming Soon."

Major requested modules must be functional.

Do not create broken links.

Do not create duplicate sources of truth.

Do not duplicate entities unnecessarily.

Do not create two competing AI assistants.

Do not put direct Base44 calls throughout the UI.

Do not remove working incoming functionality until its replacement works.

Do not ship raw secrets.

Do not use hard-coded users.

Keep components modular.

Keep naming consistent.

Keep the system responsive.

Keep the app runnable at every phase.

---

# 33. ACCEPTANCE TEST

The build is complete only when:

1. The system presents itself as **TRINITY AI COMMAND CENTER**.
2. Jarvus functions as Trinity AI's primary conversational and action interface.
3. Users have persistent Jarvus conversations.
4. Tasks work.
5. Projects work.
6. Memory works.
7. Knowledge works.
8. Contacts work.
9. Events work.
10. Files work.
11. Activity tracking works.
12. Notifications work.
13. Workflows work.
14. Automations have a functioning architecture and logs.
15. Approval queue works.
16. Global search works.
17. Command palette works.
18. Settings work.
19. Admin controls are role-restricted.
20. User-scoped information is protected.
21. Existing valuable Trinity functionality from the incoming code has been preserved or deliberately replaced.
22. Duplicate legacy systems have been consolidated.
23. Base44 provides a functioning backend now.
24. Frontend backend access is isolated behind services.
25. A future Python backend can replace Base44 domain-by-domain without rebuilding the frontend.

After implementation, test:
- navigation
- authentication
- CRUD
- Jarvus conversations
- permissions
- entity relationships
- responsive layouts
- workflow execution
- approval flow
- errors
- empty states
- loading states

Finish with one coherent, working application — not a prototype and not a collection of disconnected pages.
