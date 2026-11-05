# Backend and database example: a todo app

This example builds a small todo app with Python, FastAPI, SQLite, and plain HTML/JavaScript. The learner adds a task from a page, saves it, and sees it in the list. Use their existing environment setup.

Use PostgreSQL or another requested component when that is what the learner wants to learn. SQLite is the default only when no database has been chosen.

## Plan the work

Start with the backend, connect the page, then try one small change if it fits the agreed plan. Check that saved tasks survive a restart. A useful change or bug already worked through can count as practice.

The table below is a possible route. Combine familiar preparation rather than spending a turn on every row. Editing an endpoint, starting it, and making one request can be one step. Connect the parts before adding more CRUD operations.

## Possible steps

| Step | What to check | Main concept |
|---|---|---|
| Establish the project location | The learner confirms the working directory and file locations | Project root and terminal working directory |
| Small HTTP endpoint | A browser receives JSON from `/` | Uvicorn, FastAPI routing, function return values |
| Initialize storage | A script creates the required table successfully | SQLite library, database file, connection, SQL |
| Query endpoint | `GET /tasks` returns `[]` for an empty table | SELECT, result rows, JSON lists |
| Create endpoint | `POST /tasks` returns 201 and a new task | Request body, Pydantic, parameterized SQL, commit |
| Connect writing and reading | A separate GET reads the newly added task | Returning a new object versus querying it again |
| Persist across restarts | A fresh request still finds the task after restarting the server | Process memory and disk storage lifecycles |
| Serve a page | `/` displays HTML | FileResponse and browser rendering |
| Load tasks in the page | The page displays tasks from the database | fetch, JSON parsing, DOM lists |
| Add tasks from the page | Submitting the form updates the task list | submit, POST, then another GET |

Split or combine steps to match the learner. If editing and testing happen in separate turns, say which part has been checked so far.

## What each part does

| Part | Responsibility here | First place to investigate |
|---|---|---|
| HTML/JavaScript in the browser | Collect input, send requests, render JSON as a list | Request path, method, body, actual response, event handler |
| Uvicorn and FastAPI | Run the app, select routes, validate input, call handlers, return responses | Server terminal, route handler, project line named by an exception |
| SQLite | Store and query committed task data through SQL | Actual database path, SQL, parameters, transaction commit |

Refer to these roles when connecting a new part. There is no need to repeat the whole table each turn.

## Try a small change

Once the app works, change `ORDER BY id` to `ORDER BY id DESC` to put newer tasks first. Point to the backend query, then let the learner edit it and refresh the page. This shows how the SQL order passes through the API to the list on screen.

If input validation is more useful, add one constraint and try a valid and an invalid request instead. Choose one change that fits the current code. A similar change already made is enough; there is no need to add both.

## Files

```text
project/
  main.py       # Application, routes, request handling
  init_db.py    # One-off table initialization script
  tasks.db      # SQLite database file
  index.html    # Page structure and necessary JavaScript
```

This is enough to start. Add layers, an ORM, a frontend framework, or containers when the learning goal or the code needs them. Keep an existing reasonable structure.

If an initialization script executes code at the top level, do not import it into the app just to reuse a path. Temporarily constructing the same path in both files is acceptable; extract a module without import-time effects when useful.

## Things to explain along the way

- `Path(__file__).resolve().parent / "tasks.db"` calculates the database path beside the script. Connecting can create a missing database file. Ensure the application and initialization script point to the same file.
- SQLite lets the application read and write a database file without a separate service. PostgreSQL and MySQL normally run as separate services, on the same machine as the backend or on another machine.
- An existing database file establishes only that the file exists. Successful initialization and table queries establish that the required table is available.
- `conn.row_factory = sqlite3.Row` determines how newly created cursors on that connection wrap result rows. Rows support both column-name and positional access; `dict(row)` produces a regular dictionary. This setting does not change the schema.
- `INSERT ... VALUES (?)` with a parameter tuple keeps SQL and input data separate. A single-element tuple is written `(task.title,)`.
- Commit a write transaction so later connections can read the saved data. Close connections with `finally` or another suitable mechanism.
- `GET /tasks` and `POST /tasks` share a path but have different methods. Address-bar navigation normally sends GET. Use `/docs` or page JavaScript to send POST.
- In `/docs`, **Server response** shows the actual request result. The **Responses** section and its 201/422 examples describe the API; they are not the status of the request just sent.
- Serving HTML and the API from the same backend lets the page use `fetch("/tasks")`. Page loading first retrieves HTML, then JavaScript retrieves JSON.
- A successful page submission sends POST `/tasks` to write, then `loadTasks()` sends GET `/tasks` to retrieve and render the latest list. Insert user text into list items with `textContent`.

## Common debugging examples

### A query returns `null` instead of `[]`

JSON `null` commonly represents Python `None`. Inspect the route handler for a missing or unexecuted `return`.

```python
result = [dict(row) for row in rows]
return result
```

Explain assignment versus return. Check the actual function before prescribing a change; `null` alone does not establish a single cause.

### A create request returns 500

Read the end of the exception and the line that points into project code. For example:

```text
sqlite3.OperationalError: near "INSTERT": syntax error
```

Here, `INSERT` was misspelled. Correct the keyword and retry the request. Other 500 responses need their own logs checked.

### The file location differs from the startup directory

Check the locations in the screenshot, terminal, or files you are allowed to read. Move files only if their locations affect imports, database paths, or which project they belong to. After a move, restart the application from the appropriate directory.

## When the local app works

Once adding, querying, persistence, page interaction, and the agreed small change work, finish the introduction. If the learner wants deployment next, explain the difference between access from their own machine, a LAN, a remote server, and a hosting service. Cover the processes, network settings, storage, and configuration needed for that choice. Check external access separately from local requests.
