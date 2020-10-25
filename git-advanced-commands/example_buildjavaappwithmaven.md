---
layout: documentation
title: Build a Java app with Maven
section: doc
---

## Add a new heading

This tutorial shows you how to use Jenkins to orchestrate building a simple Java application with [Maven](https://maven.apache.org).

Adding another sentence.

If you are a Java developer who uses Maven and who is new to CI/CD concepts, or
you might be familiar with these concepts but don't know how to implement
building your application using Jenkins, then this tutorial is for you.

The simple Java application (which you'll obtain from a sample repository on
GitHub) outputs the string "Hello world!" and is accompanied by a couple of unit
tests to check that the main application works as expected. The results of these
tests are saved to a JUnit XML report.

*Duration:* This tutorial takes 20-40 minutes to complete (assuming you've
already met the <<prerequisites,prerequisites>> below). The exact duration will
depend on the speed of your machine and whether or not you've already
<<run-jenkins-in-docker,run Jenkins in Docker>> from link:..[another tutorial].

You can stop this tutorial at any point in time and continue from where you left
off.

If you've already run through link:..[another tutorial], you can skip the
<<prerequisites,Prerequisites>> and <<run-jenkins-in-docker,Run Jenkins in
Docker>> sections below and proceed on to <<fork-sample-repository,forking the
sample repository>>. (Just ensure you have
link:https://git-scm.com/downloads[Git] installed locally.) If you need to
restart Jenkins, simply follow the restart instructions in
<<stopping-and-restarting-jenkins,Stopping and restarting Jenkins>> and then
proceed on.

include::doc/tutorials/_prerequisites.adoc[]
** link:https://git-scm.com/downloads[Git] and optionally
   link:https://desktop.github.com/[GitHub Desktop].

include::doc/book/installing/_run-jenkins-in-docker.adoc[]

### Fork and clone the sample repository on GitHub

Obtain the simple "Hello world!" Java application from GitHub, by forking the
sample repository of the application's source code into your own GitHub account
and then cloning this fork locally.

. Ensure you are signed in to your GitHub account. If you don't yet have a
  GitHub account, sign up for a free one on the https://github.com/[GitHub
  website].
. Fork the
  https://github.com/jenkins-docs/simple-java-maven-app[`simple-java-maven-app`]
  on GitHub into your local GitHub account. If you need help with this process,
  refer to the https://help.github.com/articles/fork-a-repo/[Fork A Repo]
  documentation on the GitHub website for more information.
. Clone your forked `simple-java-maven-app` repository (on GitHub) locally to
  your machine. To begin this process, do either of the following (where
  `<your-username>` is the name of your user account on your operating system):
** If you have the GitHub Desktop app installed on your machine:
.. In GitHub, click the green *Clone or download* button on your forked
   repository, then *Open in Desktop*.
.. In GitHub Desktop, before clicking *Clone* on the *Clone a Repository* dialog
   box, ensure *Local Path* for:
*** macOS is `/Users/<your-username>/Documents/GitHub/simple-java-maven-app`
*** Linux is `/home/<your-username>/GitHub/simple-java-maven-app`
*** Windows is `C:\Users\<your-username>\Documents\GitHub\simple-java-maven-app`
** Otherwise:
.. Open up a terminal/command line prompt and `cd` to the appropriate directory
   on:
*** macOS - `/Users/<your-username>/Documents/GitHub/`
*** Linux - `/home/<your-username>/GitHub/`
*** Windows - `C:\Users\<your-username>\Documents\GitHub\` (although use a Git
    bash command line window as opposed to the usual Microsoft command prompt)
.. Run the following command to continue/complete cloning your forked repo: +
   `git clone \https://github.com/YOUR-GITHUB-ACCOUNT-NAME/simple-java-maven-app` +
   where `YOUR-GITHUB-ACCOUNT-NAME` is the name of your GitHub account.

=== Create your Pipeline project in Jenkins

. Go back to Jenkins, log in again if necessary and click *create new jobs*
  under *Welcome to Jenkins!* +
  *Note:* If you don't see this, click *New Item* at the top left.
. In the *Enter an item name* field, specify the name for your new Pipeline
  project (e.g. `simple-java-maven-app`).
. Scroll down and click *Pipeline*, then click *OK* at the end of the page.
. ( _Optional_ ) On the next page, specify a brief description for your Pipeline
  in the *Description* field (e.g. `An entry-level Pipeline demonstrating how to
  use Jenkins to build a simple Java application with Maven.`)
. Click the *Pipeline* tab at the top of the page to scroll down to the
  *Pipeline* section.
. From the *Definition* field, choose the *Pipeline script from SCM* option.
  This option instructs Jenkins to obtain your Pipeline from Source Control
  Management (SCM), which will be your locally cloned Git repository.
. From the *SCM* field, choose *Git*.
. In the *Repository URL* field, specify the directory path of your locally
  cloned repository <<fork-sample-repository,above>>,
  which is from your user account/home directory on your host machine, mapped to
  the `/home` directory of the Jenkins container - i.e.

* For macOS - `/home/Documents/GitHub/simple-java-maven-app`
* For Linux - `/home/GitHub/simple-java-maven-app`
* For Windows - `/home/Documents/GitHub/simple-java-maven-app`
. Click *Save* to save your new Pipeline project. You're now ready to begin
  creating your `Jenkinsfile`, which you'll be checking into your locally cloned
  Git repository.
