---
layout: post
title:  "Utilize Git Stash"
permalink: /utilize-git-stash/
---

While working on a project, we sometimes encounter a situation where we need to change multiple files to build the project for multiple target environments. For example, to build and run a project for a local development environment, we need to change some files according to the local environment like changing properties of the server, database, and other configuration files. But while committing, we should not push those changes without commenting those out, because normally we want to keep our project consistent for a particular environment like production or test environment.

We can save ourselves from this situation by utilizing `git stash`. This command saves your local modifications away and goes back to a clean working directory. Let's see how we can achieve this through the following example.

Suppose you need to change files for three different environments. One is when you work in your local development environment, another for the test, and the last one for the production environment. For this example, I will use two files that normally exist in angular and spring project. Though `git stash` has nothing to do with angular and spring.

File 1: _`environment.prod.ts`_

```js
...

/** PRODUCTION SERVER */
// baseUrl: 'https://server.production.com',
// fileServerUrl: 'https://file.production.com'

/** TEST SERVER */
baseUrl: 'https://server.production.com',
fileServerUrl: 'https://file.production.com'

/** LOCAL DEVELOPMENT */
// baseUrl: 'http://localhost:4200',
// fileServerUrl: 'http://localhost:4201'

...
```

File 2: _`application.properties`_

```
...

# ------------------ PRODUCTION SERVER -------------------------------
# spring.datasource.url=jdbc:mysql://localhost:3306/prod_db
# spring.datasource.username=produser
# spring.datasource.password=prodpass

# ---------------------- TEST SERVER ---------------------------------
spring.datasource.url=jdbc:mysql://localhost:3306/test_db
spring.datasource.username=testuser
spring.datasource.password=testpass

# ------------------ LOCAL DEVELOPMENT -------------------------------
# spring.datasource.url=jdbc:mysql://localhost:3306/local_db
# spring.datasource.username=localuser
# spring.datasource.password=localpass

...
```

So I am considering these two files ready for TEST SERVER and they are kept in this state in GitHub or your code hosting provider. Now, if a developer needs to build the project for PRODUCTION SERVER, s/he needs to change these two files by commenting the TEST SERVER sections and uncommenting the PRODUCTION SERVER sections. It may seem to you that there are only two files and there is not so much to change. But I am only using two files for example. There may be more files or more lines of code in your project that need to be changed. Again, whenever a developer starts working on the project, s/he needs to comment and uncomment the sections for LOCAL DEVELOPMENT, least s/he should not be able to run and test locally.

So let's see how can we use `git stash` and relieve ourselves from this comment/uncomment hassle. We will change these files according to the different environments and stash them with different names. I will show for only PRODUCTION SERVER. 

1. Comment TEST SERVER sections, uncomment PRODUCTION SERVER sections, and save the files.

2. We will use `git stash push` command to stash the changed files under a specific name.  

```
git stash push -m production_server relative_path\environment.prod.ts relative_path\application.properties
```

Here we are stashing these two files under the name `production_server` so that when you see the list of stash, you can identify which one you want to use. Don't forget to change `relative_path` by your file's path. Repeat these steps by commenting/uncommenting for LOCAL DEVELOPMENT also. Also, don't forget to change the name `production_server` to `local_development` or whatever name you like for the stash.

Now let's list stashes and see them. 

```
git stash list
```

You will see the following result.

```
stash@{0}: On branch_name: local_development
stash@{1}: On branch_name: production_server
```

Here `0` is for `local_development` and `1` is for `production_server`. Now we will use `git stash apply` instead of `git stash pop` because `pop` will discard the stashed changes.

```
git stash apply 0
```

After executing this command, if you check the two files, you will see that the files have changed according to the LOCAL DEVELOPMENT environment.

That's it. You do not need to comment/uncomment those files anymore. From now on, you will just use `git stash apply 0/1` according to your need.

You can find the example code <a href="https://github.com/JobayerAhmmed/jobayerahmmed.github.io/tree/master/examples/utilize-git-stash" target="_blank">here</a>.