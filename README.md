# Guided Project Learning

An agent skill for learning a tech stack by building a small project.

You write the code and run the commands. The agent explains each step, gives examples, and waits for your result before continuing. By the end, you should know how to run the project, follow data through its parts, make a small change, and find the right log when something breaks.

## Install

Using the [Skills CLI](https://skills.sh/docs):

```bash
npx skills add wangweifeng0808/guided-project-learning --skill guided-project-learning
```

Choose your agent and installation scope when prompted. The CLI requires Node.js and npm.

For a fresh manual installation in Codex:

```bash
git clone https://github.com/wangweifeng0808/guided-project-learning.git "${CODEX_HOME:-$HOME/.codex}/skills/guided-project-learning"
```

For other agents, use their skill installer or add this folder to their skills directory. The instructions are in [`SKILL.md`](SKILL.md). [`agents/openai.yaml`](agents/openai.yaml) provides the Codex display name and description.

## Use

In Codex:

```text
$guided-project-learning

I know Python and can manage my dependencies. I want to get a practical feel
for FastAPI and PostgreSQL over two evenings. Guide me through a small project.
I will do the work myself. Give me one goal at a time and wait for my result.
```

Use the same prompt with another stack, such as Docker Compose, React, or a framework you have just started using. The agent teaches in the language you use, unless you ask for another.

## How it works

Start with one thing that works from beginning to end: submit a form, save its data, and show the saved result, for example. Agree on where to stop before adding more features.

Each turn gives you one task, the code or commands you need, and an explanation. Run it and share what happened. If it fails, fix that step before moving on. Once the parts work together, try a small change to see how they affect one another.

Skip setup you already know. Ask for a complete example when you need one. Quizzes are optional.

You edit files, install packages, and run the app. The agent can read relevant code or logs to help, and you can ask it to take over a specific task. Notes and progress files are saved only when requested.

The [backend example](references/backend-todo.md) uses FastAPI, SQLite, and plain HTML/JavaScript. It gives a possible route and some debugging examples, rather than a finished app. If you want to learn PostgreSQL, the project should use PostgreSQL.

## Files

```text
guided-project-learning/
  SKILL.md                    Teaching instructions
  agents/openai.yaml          Codex display name and description
  references/backend-todo.md  Backend example
  README.md                   Installation and usage
  LICENSE                     MIT license
```

## Contributing

For changes to the teaching instructions, include a sample learner request and show how the response should change.

## License

[MIT](LICENSE). Copyright (c) 2026 wangweifeng0808.
