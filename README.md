# File Sharing App

This repository contains the source code for a file sharing application built using Node.js, Express, Multer, Mongoose, and EJS templates. The tutorial followed is based on a YouTube video series that guides you through creating this web application from scratch.

## Getting Started

To get started with this project, clone the repository and install the dependencies:

- `git clone https://github.com/dimaliwatkent/file-sharing-nodejs.git`
- `cd file-sharing-nodejs`
- `npm install`

Make sure you have Node.js installed on your system. This project uses npm scripts to manage the server.

## Application Structure

The application consists of the following main components:

- Models: Define the structure of the data in MongoDB using Mongoose models.
- Views: EJS templates for rendering HTML pages.
- Server: Express server setup and route handlers.

## Database Model

The File model is defined in models/File.js. It has the following schema:

- path: The location of the file on the server.
- originalName: The original name of the uploaded file.
- password: An optional field for setting a password to restrict access.
- downloadCount: A counter for tracking how many times the file has been downloaded.

## Views

There are two views:

- index.ejs: Displays a form for uploading files and a link to the uploaded file if one exists.
- password.ejs: Renders a form where users can enter a password to download protected files.

## Server Setup

The `server.js` file sets up the Express server and includes middleware for handling form submissions and serving static files.

- It imports necessary modules such as express, multer, mongoose, dotenv, and bcrypt.
- The server listens on the port specified by the environment variable PORT or defaults to 3000.

## Handling File Uploads and Downloads

The server handles file uploads via the `/upload` endpoint, which uses Multer to store the uploaded files temporarily. After successful upload, the server creates a new File document in MongoDB and renders the index view with a link to the uploaded file.

Downloading files is handled by the `/file/:id` route. If a password is set for the file, the user must provide the correct password either via GET or POST request. Upon successful authentication, the server increments the download count and sends the file to the client.

## Environment Variables

The .env file should contain the following variables:

- DATABASE_URL: The connection string to your MongoDB database.
- PORT: The port on which the server will run.

## Running the Application

To start the server, run:

`npm run dev`

The server will listen on the specified port, and you can access the application in your browser.

## Additional Resources

For a visual walkthrough of the development process, check out the YouTube tutorial that inspired this project:

[File Sharing App Tutorial Video](https://youtu.be/AHXFMu8xVsc?si=B0roN2_yWdHBjkfU)
