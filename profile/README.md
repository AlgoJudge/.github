# AlgoJudge

Open-source software for organising activities built around programming tasks —
contests, courses, laboratories, training sessions — and for automatically
running, testing and evaluating submitted solutions.

- Information site: **[algojudge.pl](https://algojudge.pl)**
- Target application domain: **[algojudge.app](https://algojudge.app)**, which
  currently redirects to the information site

## What we are trying to do differently

Most online judges fix one kind of activity and one kind of task in the core.
AlgoJudge separates the three concerns:

- the **Client** renders an activity or task type,
- the **Runner** evaluates it in isolation,
- the **Server** stores a shared, versioned data envelope and never interprets
  what a type means, nor compiles or runs any submitted code.

The goal is that adding a new activity or task type needs a Client renderer and
a Runner handler — **not a change to the Server**.

## Repositories

| Repository | Role | State |
|---|---|---|
| [AlgoJudge-Client](https://github.com/AlgoJudge/AlgoJudge-Client) | Web frontend for participants, managers and administrators. React, TypeScript, Vite, Mantine. | early development |
| [AlgoJudge-Server](https://github.com/AlgoJudge/AlgoJudge-Server) | REST API and persistent state. ASP.NET Core on .NET 8, PostgreSQL. | early development |
| [AlgoJudge-Runner](https://github.com/AlgoJudge/AlgoJudge-Runner) | Isolated execution and evaluation of submitted solutions. | **not implemented yet** |

## Status

Early development, and we would rather say so than overstate it. The interface
exists largely as working templates, the Server holds the domain model and a
small API, and the Runner has not been built — its repository currently
documents the intended architecture and security requirements.

Nothing here is ready to run a real contest yet.
