## StackCred

StackCred is a Clarity smart-contract project for decentralized education credentials and peer assessment on the Stacks blockchain. The contract supports user registration, skill definitions, assessment requests, and assessor reputation management.

This repository contains the Clarity contract, Clarinet configuration, and unit tests (Vitest + Clarinet environment) used to validate behavior.

## Repository layout

- `contracts/StackCred.clar` — main Clarity contract (skills, assessments, reputations).
- `tests/StackCred.test.ts` — project tests (Vitest + Clarinet test environment).
- `Clarinet.toml` — Clarinet configuration.
- `settings/Devnet.toml` — devnet settings for local runs.
- `package.json` — repository scripts and dependencies.

## Requirements

- Node.js (recommended: 16+ or latest LTS)
- npm
- Clarinet (for local Clarity contract checks and devnet runs) — see https://github.com/hirosystems/clarinet for install instructions

Note: Tests use `vitest` and the `vitest-environment-clarinet` adapter to run Clarity tests. Make sure Clarinet is installed and available on your PATH when running Clarinet-specific commands.

## Quick start

1. Install JavaScript dependencies:

```bash
npm install
```

2. Run the unit tests (Vitest):

```bash
npm test
```

3. Run Clarinet contract checks (requires Clarinet installed):

```bash
clarinet check
```

If you prefer the project tasks, there are tasks you can run via your editor or task runner. The repository includes a Clarinet configuration (`Clarinet.toml`) and a `settings/Devnet.toml` for local devnet settings.

## Contract overview

Key public functions in `contracts/StackCred.clar`:

- `register-user` — register an account as a user in the system.
- `add-skill` — (owner-only) add a new skill with name, description, required assessments, and category.
- `request-assessment` — request a peer assessment for a particular skill.

The contract also maintains maps for user data, skill metadata, assessments, and skill-specific reputation. Statistical helpers calculate mean and (integer) standard deviation of assessor scores and reputation adjustments.

## Tests

- Unit tests are located in `tests/`. They use `vitest` with the Clarinet test environment adapter. The main test file is `tests/StackCred.test.ts`.
- Run the full test suite with `npm test`.

## Development notes

- The repository uses `@hirosystems/clarinet-sdk` and `vitest-environment-clarinet` to call and test Clarity contract behaviors from TypeScript tests.
- When adding new skills or tests, keep the string length limits in the contract in mind (name: 50, description: 200, category: 50).

## Contributing

If you'd like to contribute:

1. Open an issue describing the change or bug.
2. Create a feature branch and a focused PR with tests covering new behavior.

## License

This repository currently has no license declared in the README. Check `package.json` for the declared license (if any) and include a LICENSE file in the repo if you intend to make this project open source.

## Contact

If you need help running tests or using Clarinet in this project, include the output of `npm test` and `clarinet check` when opening an issue.
