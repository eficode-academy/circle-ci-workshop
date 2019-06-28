# CircleCI workshop

CircleCI is a continuous integration and build Software as a Service (SaaS).

This workshop will go through the basic steps in their system, making you able to make CI builds in the end.

> Note: at the time of writing, CircleCI have a free 2,5 build hours per week, which should be enough for this exercise. But it's not an "all you can eat" buffet :)

## Coding Assignment

While the purpose is to learn CircleCI, this will be a coding assignment. It is made just to give you some tangible code to work with:
Remember, this is not a programming exercise, but a CI one; code is only there so you have something to build :)

This repository comes with a maven based java project from the start, but any language can be used. If you want to, just replace the java code with one of the other languages from (this repository)[https://github.com/emilybache/GildedRose-Refactoring-Kata].

The description of the application can be read [here](gildedrose.md), but is not necessary yet.

## Tasks

### Fork the repository

You need to have your own repository with the code in order for CircleCI to work, and for you to merge in changes without anybody else conflicting with you.

### Set up the CircleCI configuration

Setting up your repository is fairly simple;

* [login to the website](https://circleci.com/vcs-authorize/)
* Add your forked repository to the CircleCI dashboard: ![add project](img/add-project.png)
* Leave the browser open and go back to the repository on your computer.
* Create a folder named .circleci and add a fileconfig.yml (so that the filepath be in .circleci/config.yml). In the terminal you can do it like this:

```bash
mkdir .circleci
touch .circleci/config.yml
```

Now we have the basis to run a basic `hello world` build in CircleCI

### Making "hello world"

CircleCI is configured through the YAML file we just created.
In order for us to make the first `hello world` script, examine the following example:

```yaml
version: 2.0
jobs:
  build:
    docker:
      - image: alpine:3.7
    steps:
      - run:
          name: The First Step
          command: |
            echo 'Hello World!'
            echo 'This is the delivery pipeline'
```

The CircleCI config syntax is very straight forward. The trickiest part is typically indentation. Make sure your indentation is consistent. This is the single most common error in config. Let’s go over the nine lines in details

* Line 1: This indicates the version of the CircleCI platform you are using. 2.0 is the most recent version.
* Line 2-3: The jobs level contains a collection of arbitrarily named children. build is the first named child in the jobs collection. In this case build is also the only job.
* Line 6-7: The steps collection is an ordered list of run directives. Each run directive is executed in the order in which it was declared.
* Line 8: The name attribute provides useful organizational information when returning warnings, errors, and output. The name should be meaningful to you as an action within your build process
* Line 9-11: This is the magic. The command attribute is a list of shell commands that represent the work you want done. The initial pipe, |, indicates that there will be more than one line of shell commands. Here line 10 will print out Hello World! in your build shell and line 11 will print out This is the delivery pipeline

Paste the example into `.circleci/config.yml` and click `start building` in the CI dashboard.

You should see something like this in the logs of CircleCI:

```bash
#!/bin/sh -eo pipefail
echo 'Hello World!'
echo 'This is the delivery pipeline'

Hello World!
This is the delivery pipeline
```

### Making a real pipeline

Up untill now, we have only made sure that CircleCI can reach the configuration file, but not really made it clone down our repository.

tasks:

* replace the image from `alpine:3.7` to s

### add gradle test step

### Run a few iterations on the code

### Adding the PR feature

### Pointing towards multiple test