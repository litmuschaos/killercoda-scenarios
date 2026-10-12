# LitmusChaos Interactive Scenarios

Hands-on, browser-based tutorials for learning chaos engineering with LitmusChaos. Each scenario runs in a throwaway sandbox cluster — nothing is installed on your machine.

[**Start the scenarios on Killercoda →**](https://killercoda.com/litmuschaos)

## Available Scenarios

| Scenario | What you'll do |
| --- | --- |
| [`getting-started-with-litmus`](getting-started-with-litmus/) | Install LitmusChaos, deploy a target application, and run your first pod-delete chaos experiment end to end. |

## Scenario Layout

Each scenario is a directory containing:

| File | Purpose |
| --- | --- |
| `index.json` | Scenario definition — title, difficulty, estimated time, and the ordered list of steps |
| `intro.md` | The opening screen a learner sees |
| `step1.md` … `stepN.md` | One file per step |
| `finish.md` | The closing screen |
| `*.sh` | Helper scripts invoked by the steps |

Shared images live in [`assets/`](assets/).

## Contributing

New scenarios and fixes to existing ones are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for the structure to follow and how to check your work before opening a pull request.

## Community

- [Slack](https://slack.litmuschaos.io) — `#litmus` for questions, `#litmus-dev` for development
- [Documentation](https://docs.litmuschaos.io)
- [Main repository](https://github.com/litmuschaos/litmus)

## Security

To report a vulnerability, see [SECURITY.md](SECURITY.md). Please do not open a public issue for security problems.

## License

Apache License 2.0 — see [LICENSE](LICENSE).
