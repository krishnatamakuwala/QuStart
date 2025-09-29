# <img src="https://raw.githubusercontent.com/krishnatamakuwala/QuStart/refs/heads/main/logo.png" alt="logo" width="30"/> QuStart

**QuStart** is a distributed task management system that enables teams to run automated tasks (such as data exports, file processing, and system operations) across multiple machines with **real-time visibility** and **minimal setup**.

## Problem Statement
Running long-running tasks directly on API requests creates poor user experiences.  
For example:

- Exporting millions of records to CSV in real time would force users to wait at a loading screen indefinitely.
- While storing pre-generated files on a CDN allows instant downloads, dynamic and variable data often requires fetching, processing, and writing first — making the process slow and resource intensive.
- Even with a dedicated agent, hundreds of concurrent users can overwhelm servers, making instant scalability challenging.

## Solution
Enter **QuStart**.

QuStart is purpose-built to handle these scenarios by allowing teams to:
- Manage distributed microservice agents.
- Scale them **horizontally** (and vertically if needed).
- Monitor agents, job requests, and dashboards via an elegant, minimal UI.

With **end-to-end authentication and authorization**, QuStart provides a secure, scalable, and reliable solution for distributed task execution.

You can watch the first draft video in below YouTube playlist of unlisted videos.

[QuStart - Draft - YouTube](https://youtube.com/playlist?list=PLcAuwLF81BJt_6T_ddVctixhTMwmaozNU&si=deLL6R_Rj2GrDAK8)

> *P.S. I am sorry for poor audio quality and not fluent english.*

## Security
QuStart is designed with **security at its core**:

- Every session and API request is authenticated using **time-based JWT tokens**.
- Agents communicate securely using **API keys**.
- Fine-grained **role-based authorization** allows flexible permission management.
- All connections (PostgreSQL, Redis, RabbitMQ, ELK, etc.) are secured with **TLS encryption** and **public-private key authentication**.

## Technologies
- **Database:** PostgreSQL
- **Cache Server:** Redis
- **Queue System:** RabbitMQ
- **Logging:** ELK Stack
- **Backend API:** Node.js + Express (TypeScript)
- **Frontend UI:** React.js + Next.js (TypeScript)
- **UI Framework:** Material UI
- **Containerization:** Docker
- **Windows Agent:** .NET Core (C#)

## Process Flow
### Job Request Lifecycle
1. User creates a job request for a specific action.
2. Permissions are validated for both the page and the action.
3. The job request is queued in **RabbitMQ** (Work Allocator).
4. The Work Allocator assigns the job to an appropriate agent.
5. The agent executes the task and updates its status.
6. Once completed, the job is marked as **Completed**.

## Future Enhancements
- Incremental updates (update only changed values).
- MongoDB support for user preferences and theming.
- User notifications.
- Enhanced logging and monitoring.
- Agent publishing within the tool itself.
- Parameterized operations (static values at agent registration, dynamic values at job creation).
- Support for sequential job execution.
