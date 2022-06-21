# Local Tasks

This is where the `local` install task files are kept.

Deployment of task order is important, many packages rely on the O/S having
certain tools installed. `curl` is a good example of this.

To create a new task, simply create a new task file and the add it to the `main.yml`
file in this directory. It will be picked up automatically on the next run.
