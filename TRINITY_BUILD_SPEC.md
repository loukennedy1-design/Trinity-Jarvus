# Trinity AI + Jarvus Unified Build Specification

## Product
Build a fresh unified system named **Trinity AI Command Center** with **Jarvus** as the conversational AI and action/orchestration layer.

## Core goals
- One application, one navigation shell, one data/service architecture.
- Preserve useful functions from the incoming source ZIP/repository.
- Merge duplicate functionality rather than creating parallel modules.
- Base44-compatible during the current phase.
- GitHub is the source of truth.
- Python/FastAPI-ready for the later server migration.

## Major modules
- Command Center
- Trinity AI / Jarvus Chat
- Tasks
- Projects
- Memory
- Knowledge
- Contacts
- Calendar / Events
- Files
- Activity
- Notifications
- Workflows
- Automations
- Action / Approval Queue
- Integrations
- Settings
- Admin

## Architecture
Use a modular frontend and centralized service layer. Do not scatter direct backend calls throughout UI components.

Suggested structure:

```
src/
  app/
  components/
  features/
    trinity/
    jarvus/
    command-center/
    tasks/
    projects/
    memory/
    knowledge/
    workflows/
    automations/
    contacts/
    calendar/
    files/
    notifications/
    admin/
  services/
    apiClient
    authService
    trinityService
    jarvusService
    taskService
    projectService
    memoryService
    knowledgeService
    workflowService
    automationService
    activityService
    notificationService
  config/

base44/
  entities/
  functions/
  agents/
  connectors/

server/
  app/
  api/
  agents/
  services/
  workers/

docs/
```

## Backend abstraction
Create central configuration placeholders:
- API_BASE_URL
- WS_BASE_URL
- USE_EXTERNAL_BACKEND=false
- APPLICATION_ENVIRONMENT

Frontend services should expose stable methods such as:
- getCurrentUser()
- getDashboardData()
- getConversations()
- sendJarvusMessage()
- getTasks()
- createTask()
- updateTask()
- getProjects()
- getMemories()
- saveMemory()
- searchKnowledge()
- createAutomation()
- executeAction()

Initially these can use Base44. Later they can switch to Python APIs without rewriting the UI.

## Core data models
Create/normalize:
- Conversation
- Message
- Memory
- KnowledgeItem
- Task
- Project
- ProjectMember
- Workflow
- WorkflowRun
- Automation
- AutomationRun
- Contact
- Event
- FileAsset
- Activity
- Notification
- ActionRequest
- UserPreference
- SystemSetting

## Jarvus
Jarvus must provide:
- persistent conversations
- conversation history/search
- modes: General Assistant, Command Center, Research, Operations, Planning, Project Manager, Analyst, Developer, Administrator
- contextual access to tasks, projects, memories, knowledge, contacts, workflows, events, files and activity
- action abstractions such as create_task, update_task, create_project, save_memory, search_memory, search_knowledge, create_event, create_contact, run_workflow and retrieve_dashboard_context
- confirmation before destructive actions

## Command Center
Dashboard should include:
- priority/overdue/today tasks
- active projects
- recent activity
- upcoming events
- pending approvals
- workflow status
- system alerts
- AI recommendations
- recent conversations
- quick actions
- Trinity/Jarvus briefing

## Security
- Use authenticated user context.
- Apply row-level access controls where appropriate.
- Personal memories, conversations, notifications and preferences must not be globally readable.
- Admin-only areas must be role-restricted.

## Build phases
1. Foundation: shell, navigation, auth-aware layout, configuration, service abstraction, dashboard, command palette.
2. Jarvus: conversations, messages, chat UI, modes, context panel, AI integration.
3. Core Operations: tasks, projects, contacts, calendar, activity, notifications.
4. Intelligence: memory, knowledge, context assembly, global search.
5. Workflows: workflows, runs, automations, logs, approval queue.
6. System: settings, integrations, admin, security review, responsive polish.
7. Python-ready: external API adapters, WebSocket placeholders and migration documentation.

## Python migration target
Prepare for endpoints such as:
- POST /api/jarvus/chat
- GET /api/context
- GET /api/tasks
- POST /api/tasks
- PATCH /api/tasks/:id
- GET /api/projects
- POST /api/projects
- GET /api/memories
- POST /api/memories
- POST /api/search
- POST /api/workflows/:id/run
- GET /api/activity
- GET /api/notifications
- POST /api/actions/:id/approve

Later backend target may use FastAPI, PostgreSQL, Redis, background workers, vector search and WebSockets.

## Merge rule for incoming code
When source code is added to this repository:
1. Inventory all pages, components, entities, APIs, agents and workflows.
2. Mark every item KEEP / REFACTOR / MERGE / REPLACE / REMOVE.
3. Preserve working functionality unless it conflicts with the unified architecture.
4. Consolidate duplicate models and screens.
5. Route backend access through the service layer.
6. Keep the app runnable after every phase.
7. Do not remove a working feature until its replacement is functioning.

## Acceptance criteria
The combined system must operate as one coherent Trinity AI product with Jarvus as its conversational intelligence layer, remain functional on Base44 during the current phase, live in GitHub as the source of truth, and be ready for incremental migration to a Python server later.
