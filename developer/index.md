Developer's Guide 

Quick links for developer's guide
=================================

*   [Tech Stack](#tech-stack)
*   [Getting started](#quickstart)

Tech Stack
----------

This section contains information on the different frameworks used by this project

### yarn

`yarn` serves as the javascript/typescript package manager for the project

### Typescript

The project is written mainly in typescript, augmenting javascript with type checking to improve the robustness of our code.

### NextJS

NextJS is a fullstack framework designed around React, allowing us to develop our project as a single server instead of a separate frontend and backend. It also comes with different integrated components, like `next/router`, saving us the hassle of installing other packages like `react-router`, and optional components, like `next-auth`, which provides authentication.

#### NextAuth

`next-auth` serves as our library for managing authentication, chosen for its integration with NextJS.

### Firebase

To avoid having to hash and store passwords ourselves and thus exposing potential security vulnerabilites, this project utilizes Firebase to manage user accounts

### MongoDB/Mongo Atlas

Our database of choice is MongoDB, hosted by MongoDB's [cloud](https://mongodb.com) services

#### Prisma

Prisma serves as an ORM for the project. Combined with typescript, it allows for rich type checking while making transactions with our database

Getting Started
---------------

### Installing Dependencies

Building the project requires NodeJS and yarn. Download NodeJS 16.15.x from [here](https://nodejs.org/download/release/latest-v16.x/)

Installing yarn is then as simple as running `npm install yarn`, with the `-g` flag if you're installing it globally

#### Visual Studio Code

If you're using Visual Studio Code as your IDE, here's a list of useful extensions that will be really helpful during development:
1. [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) for showing errors alongside your code, instead of just in the Problems window.
1. [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) to display ESLint errors alongside code errors.
1. [Prisma](https://marketplace.visualstudio.com/items?itemName=Prisma.prisma) for better functionality when working with `schema.prisma`.
1. [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag) helps to automatically rename matching `<html>` tags.

### Building the Project

First, clone the repository from [github](https://github.com/lunchhitch/lunchhitch)

Enter the project directory, then run `yarn install`. This should install all the packages that the project requires

### Environment Variables

Before starting the project, the following environment variables need to be set:

*   DATABASE\_URL
*   DATABASE\_USERNAME
*   DATABASE\_PASSWORD

In a development environment, `NEXTAUTH_SECRET` doesn't need to be set, but is required for production builds. More info can be found (here)[https://next-auth.js.org/getting-started/upgrade-v4#missing-secret]

### Initializing Prisma

To make full use of type hinting while working with `@prisma/client`, make sure `schema.prisma` is updated to the appropriate version, then run `yarn db:update`. You may have to restart your IDE for the changes to take effect.

### Repository Structure

The basic repository structure is as follows:
```
.
├── prisma                       // Prisma configuration
│   └── prisma.schema
├── src
│   ├── common                   // Common and reused React components go here
│   ├── pages                    // NextJS will serve these as pages on the webserver
│   │   └── api                  // NextJS API based routes
│   │       └── auth
│   │           └── [...nextauth].ts // NextAuth configuration
│   └── styles                   // CSS and styles go here
├── testing                      // Code used for testing
├── .eslintrc.js                 // eslint configuration
└── .env                         // Configure environment variables

```