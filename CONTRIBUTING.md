# Contributing to AlgoJudge

AlgoJudge is split across several repositories. Open issues and pull requests
in the one that owns the code:

| Repository | What it holds |
|---|---|
| [AlgoJudge-Client](https://github.com/AlgoJudge/AlgoJudge-Client) | the web application |
| [AlgoJudge-Server](https://github.com/AlgoJudge/AlgoJudge-Server) | the API, stored data, and permissions |
| [AlgoJudge-Runner](https://github.com/AlgoJudge/AlgoJudge-Runner) | compiling, running, and judging submissions |
| [AlgoJudge-External-Runner](https://github.com/AlgoJudge/AlgoJudge-External-Runner) | forwarding submissions to external judging systems |
| [AlgoJudge-Ops](https://github.com/AlgoJudge/AlgoJudge-Ops) | the production Docker Compose stack |
| [AlgoJudge-Docs](https://github.com/AlgoJudge/AlgoJudge-Docs) | the documentation at [docs.algojudge.pl](https://docs.algojudge.pl/) |

If you are not sure which one, pick the closest. An issue can be moved.

Report security vulnerabilities privately, as described in
[SECURITY.md](SECURITY.md).

## Reporting a bug

Use the bug report form. Say what you expected, what happened, and how to
reproduce it, and include the version you run.

## Proposing a change

For anything larger than a small fix, open an issue before you write the code.
Agreeing on the approach first saves you from rewriting it.

Two boundaries are deliberate, and a change that crosses them will not be
merged:

- **The Server never compiles or runs submitted code.** Running code is the
  Runner's job.
- **Adding a problem type does not change the Server.** A new type needs a
  renderer in the Client and a handler in the Runner.

## Opening a pull request

- Branch from `main` and target `main`.
- Keep one subject per pull request.
- Describe what changes and why. The pull request template lists the checks
  the repository expects.
- CI must pass. Each repository's README explains how to build and test it.
- Write code, comments, commit messages, and documentation in English.

## License

By contributing, you agree that your work is licensed under the license of the
repository you contribute to. Code is MIT. The documentation in AlgoJudge-Docs
and AlgoJudge-Ops is CC BY 4.0.

Everyone taking part is expected to follow the
[code of conduct](CODE_OF_CONDUCT.md).
