# AlgoJudge

AlgoJudge is open-source, self-hosted software for programming contests and
courses, with automatic evaluation of submitted solutions.

It is built for the range of activities a department actually runs — contests,
courses, laboratories, training sessions — rather than for one of them.

- Information site: **[algojudge.pl](https://algojudge.pl)**
- Target application domain: **[algojudge.app](https://algojudge.app)**, which
  currently redirects to the information site

## What we are trying to do differently

Most online judges fix one kind of activity and one kind of problem in the core.
AlgoJudge separates three concerns and holds the line between them:

- the **Client** renders an activity or problem type,
- the **Runner** executes and evaluates a submission in isolation,
- the **Server** stores a shared, versioned data envelope and never interprets
  what a type means, nor compiles or runs any submitted code.

The goal is that **adding a problem type needs a Client renderer and a Runner
handler, not a change to the Server**. That is tested rather than asserted, twice:

- a second problem type, `output-only@1`, where the participant uploads answers
  instead of a program, lives entirely in the Runner and appears nowhere in the
  Server's source or in its OpenAPI document;
- a second Runner implementation, which judges nothing and forwards submissions
  to an external judging system, registers, claims and reports over the same
  contract as the first — which is the point of having a contract.

## Repositories

| Repository | Role |
|---|---|
| [AlgoJudge-Server](https://github.com/AlgoJudge/AlgoJudge-Server) | Persistent state, REST API, WebSocket and authorization. ASP.NET Core on .NET 10 with PostgreSQL |
| [AlgoJudge-Client](https://github.com/AlgoJudge/AlgoJudge-Client) | Web frontend for participants, activity managers and administrators. React, TypeScript, Vite and Mantine |
| [AlgoJudge-Runner](https://github.com/AlgoJudge/AlgoJudge-Runner) | Isolated execution and evaluation of submitted solutions. Rust, sibling containers, cgroup v2 |
| [AlgoJudge-External-Runner](https://github.com/AlgoJudge/AlgoJudge-External-Runner) | A second Runner that judges nothing: it forwards submissions to external judging systems and reports their verdicts |
| [AlgoJudge-Ops](https://github.com/AlgoJudge/AlgoJudge-Ops) | The production Docker Compose stack for a self-hosted installation, and the update, backup and restore scripts around it |
| [AlgoJudge-Docs](https://github.com/AlgoJudge/AlgoJudge-Docs) | The public documentation site, in English and Polish |

## Status

**No release has been cut.** No repository carries a `v*` tag and nothing has
been pushed to the container registry, so a `docker pull` instruction in any of
these repositories describes the path a release will take rather than one that
works today. The documentation site is built and not yet published.

What exists is the product. The Server holds the domain model, the permission
model, the API and the operator surface; the Client is wired to it throughout,
in Polish and English; the Runner compiles, runs and marks real submissions under
isolation, with an adversarial suite that gates every merge. The deployment
target is a **self-hosted Docker Compose stack**, which `AlgoJudge-Ops` is.

We would rather say where we are than overstate it — but the Runner is no longer
a document describing an intention, and this page said it was until today.

## Licence

The code is **MIT**. The documentation pages in `AlgoJudge-Docs` and
`AlgoJudge-Ops` are **CC BY 4.0**, with the code samples on them staying MIT so
that pasting a command obliges nobody.
