# DevOps and Deployment

Developer Operations (DevOps) is part of the software development process in which as part of working on the project, we have tools, scripts and utilities that assist with monitoring, testing and deploying the application.

## Continuous Integration and Continuous Delivery

Depending on the service you are using to store your projects. You may have access to an automated workflow system within it. Within `Github`, they allow you to enact workflows that are described using a `.yml` file and exist with `.github/workflows` folder within the repository.

The workflow below mixes both continuous integration and delivery into one. The integraton is the part where the features of the project are integrated into `main` and that the test cases and builds are automated and uploaded to github releases.

### Workflow

By leveraging a workflow, we are able to create a workflow that will automatically trigger when a particular branch is comitted it.

To define a workflow, you can start with the following snippet.

```yml
name: Build Preview

on:
  # Runs on pushes targeting the default branch
  push:
    branches: ['main']

# Sets the GITHUB_TOKEN permissions to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Setup Node
        uses: actions/setup-node@v6
        with:
          node_version: lts/*
          cache: 'npm'
      - name: Install Dependencies
        run: |
          npm install
      - name: Run Tests
        run: |
          npm run test
      - name: Build Preview
        run: |
          npm run build
      - name: Upload Preview
        uses: actions/upload-artifact@v6
        with:
          name: Preview
          path: ./dist
        

```

There is a lot going on with the above but the workflow is designed to have steps broken down logically and be usable with any existing vite project with a default configuration.

Here is the breakdown of the workflow above.

1. `name` is used to describe the workflow

2. `on` and `push` describe when this workflow will be triggered and the kind of git action it is expecting it on. It also specifies the `main` branch.

3. `permission` describe the permissions used as part of this workflow.

4. `jobs` are the tasks that the workflow will perform

5. `build` is the kind of job that is to be performed in which the following steps are performed.
 * Sets up node and uses a LTS build
 * Installs the dependency for the project
 * Runs the tests as part of the build itself
 * Builds the project so it is ready to be distributed
 * Uploads the preview to the releases on github

Without needing to do these actions specifically everytime, we are able to describe the process and specify the commands to execute within it to achieve the effect.



## Deployment

Deployment can come in different forms, while the CI/CD component does handle that to some degree, we also need to consider how we can manually deploy a website.

### Deploying using ssh

This part assumes you have VPS and a domain name associated or an equivalent setup. You are able to deploy to a a virtual private server (VPS) if as a user by logging into it.

`ssh` is a very power command that allows you login to a remote server and interact with it via the shell.

To simply copy a file, compressed as it were, we are able to use `scp` to achieve this task as well.

However, two simple methods to achieve setting up your server with the files necessary.

* Using `curl` or `wget` to retrieve the build from Github Releases or an equivalent.

* Using `scp`, `rsync` or `sftp` to copy the data from your own pc to the remote server. Simply put with `scp` you can do: `scp dist.zip username@domain:~/`

The `scp` snippet will copy the file over to the remote server.

When using `ssh`, you can `unzip` the file within the directory. Depending on the setup, you may want to move the contents of `dist` to `/var/www` for the relevant `webserver` such as `apacahe` or `nginx` to start using those files.

The copying method may require `root` priviledges in your situation.
