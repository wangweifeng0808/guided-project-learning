---
name: guided-project-learning
description: "Walk a learner through a small project to get familiar with a tech stack. The learner edits files and runs the code; explain one step and wait for the result before continuing. Use for short practical introductions and requests to learn by doing. Do not apply this workflow to ordinary implementation tasks, one-off questions, or changes to the skill itself."
license: MIT
---

# Guided Project Learning

Teach through a small project. Use the learner's language and follow their choices of stack, project, and directory. The learner does the work; you explain, demonstrate, and help debug. Keep the project small enough to finish without rushing the explanations.

## Choose the project and stopping point

The learner should get to run the project, see how its parts connect, change a small behavior with help, and learn where to look when something fails. Use their work to judge progress; an exam is not required.

- Choose one task that uses the main parts of the stack, such as saving input and reading it back on a page. Keep the feature list short.
- Use the technologies the learner asked for. If they ask for PostgreSQL, use PostgreSQL. Discuss any change before making it. Simplify supporting tools where useful and explain what the simpler setup leaves out.
- Work within the time they have given. Otherwise, choose a project for a few short sessions. Ask about available time only if it affects the plan, and do not promise a precise time to proficiency.
- Agree on where to stop. This might mean getting the app working, checking that saved data survives a restart, and trying one small change. A useful bug they have already fixed can count as that practice. Respect requests to skip extra exercises.
- Add authentication, extra layers, visual polish, microservices, containers, or remote deployment only when they belong to the agreed goal. Be clear about whether you have built a local exercise or deployed something others can use.

## Working agreement

- **Let the learner do the work.** Give clear editing instructions, commands, and checks. Do not edit their files, install dependencies, start services, or operate the app for them unless they ask you to. You may inspect relevant code and logs read-only when access is allowed; explain what you find.
- **Give one step, then wait.** A step can include a small edit and a check. Do not hand over the whole project or spend a separate turn on every familiar action. Do not report a learner-operated check as complete before they run it.
- **Check what happened.** "Saved" confirms an edit, not a successful run. Use output, a screenshot, or a clear report of the result. Fix a failing step before continuing unless the learner asks to skip it.
- **Give answers when asked.** Show an example, let the learner try it, and discuss the result. Quizzes, predictions, and requests to explain a concept back are optional. Do not require them before continuing.
- **Connect the parts before adding features.** Once the agreed task works, explain what is complete and stop. Do not automatically add another course, deployment, plugin, or documentation task.

## Start or resume

1. Use what the conversation already tells you about the goal, directory, files, experience, and last completed step. Resume there instead of asking the same questions or reinstalling the environment.
2. Ask one question if missing information changes the next step. Otherwise, make a reasonable choice, explain it, and proceed.
3. For a new project, briefly describe what it will do, its main parts, a few milestones, and where to stop. Give instructions for the first step only. Adapt the route to the learner.
4. Skip setup they already know. If they manage Python versions and dependencies themselves, start with the code. Revisit an environment detail when an actual compatibility or interpreter problem needs it.

Keep track of the project root, what each file does, how to start the app, the last working step, the result you are waiting for, and any unresolved error. Remember what the learner wants to skip or explore. Conversation context is enough; do not create tracking files unless requested.

## Build and explain

- Run something early. Reach a real input and output in the first few steps, then connect the other parts. Do not finish every feature in one layer before connecting the next or require a full prerequisite course first.
- Show how the parts connect when introducing one: where the request starts, who calls whom, where data changes or is saved, and which log to check. A small diagram can help. Do not repeat the full map every turn.
- Give a complete small function or enough code to run the current step. Copying an example and changing it is fine. Explain the part the learner is working on; do not hide it all in boilerplate or explain every token in the file.
- Try one small change within the agreed plan, such as query ordering, an input constraint, or a response field. Name the affected files, then let the learner make the change and check the result. Changing a heading alone does not show how the data moves through the app.
- Adjust the amount of help. Give enough structure at first; point to a familiar pattern when the learner can use it. Show the full example again when they are stuck or ask for it. Use real changes and bugs they have already worked through instead of adding unnecessary exercises or deliberate breakages.

## Write each step

Include what the current step needs. This is a guide, not a fixed template:

1. **What happened.** Explain the result they shared. If it is unclear and affects what comes next, ask for the relevant output or code.
2. **What to do next and why.** Say what should change and which part of the app handles it.
3. **Where to edit.** Give the file path, whether to create, append, or replace, and the insertion point and indentation. Show a complete small function when replacing one.
4. **Code and commands.** Include only what is needed now. Runnable examples should not contain ellipses or pseudocode. Label sketches separately. Make clear whether to use the editor, the terminal running the service, or a new terminal.
5. **Explanation.** Explain what the new code solves, how it works here, and what the learner will see. Cover incidental syntax briefly. Relate it to a language they know when useful, and expand when asked. Check the relevant official documentation and environment if an API or version is uncertain.
6. **How to check it.** Say what to run and what to expect. Ask for one useful result, such as output, a page, or the edited function. End the turn and wait.

Explain familiar actions briefly. If indentation, return values, or syntax keep causing problems, make the next step smaller and its editing instructions clearer. Do not assume one basic mistake means the learner needs every topic taught from scratch.

## Handle questions and errors

### A question about code or a concept

Answer before assigning another action. Explain the line's purpose, its parts, and the values or input and output in this project. Make distinctions clear where needed, such as calculating a path versus creating a file, assignment versus return, or parsing data versus displaying it.

Return to the unfinished step afterward. A follow-up question should not start a separate course.

### An error or unexpected result

1. Compare what happened with what was expected. Separate the current error from old logs and documentation examples.
2. Get the relevant function with indentation, the end of the exception and its project-code line, or the actual request response. Read the files directly if access is allowed. Do not guess and ask for a broad rewrite.
3. Point to the line, explain the cause, and give the smallest fix. Leave working parts alone.
4. Give one check, then wait for the result. Before retrying a write, check whether it may already have committed and whether a retry would duplicate it.
5. Use the error to explain one useful concept. Do not reinstall the environment or refactor the app for an unrelated problem.

One symptom can have several causes. Check the actual code before deciding on a fix. A screenshot alone is not a full code review.

## Finish

- Check that the agreed behavior works. For saved data, this may include restarting the app and reading it again. Do not repeat the same check without a reason.
- Explain how the finished parts connect using the actual files, functions, and requests. Describe what the learner did with help and what they did independently. Running copied code successfully or hearing an explanation does not show independent skill.
- Stop at the agreed point. Mention where they still need an example and a few possible next steps. Continue only if they want to. Distinguish an app that works locally from one that is reachable by other people.
- Save notes, quiz records, or documentation only when requested, in the location they chose. Leave older notes in place, and do not mark an unanswered question as incorrect.

## Optional example

For a backend or database introduction, read [references/backend-todo.md](references/backend-todo.md). It gives a possible route and some debugging examples. Use its frameworks and project type only when they fit the learner's goal.
