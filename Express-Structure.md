Taken from: https://www.terlici.com/2014/08/25/best-practices-express-structure.html

## Folder structure
**models/** Represent data, and how to use/fetch the data from the database\
**views/** Templates for rendering\
**controllers/** API routes and logic\
**public/** Static resources eg. Javascript, Images\
**helpers/** Code shared between different parts of the project\
**middleware/** Request pre-processing before handing them out to routes\
**tests/** Tests for every part of the project\
**app.js** Glue everything together\
**server.js** HTTP listener

## Models
- One file for each type of data
- Independant from the outside world
  - No imports to other models
  - Don't know about controllers that use them

## Views
- Subfolder corresponding to each of the models

## Controllers
- Define routes
- Serve views
- Interact with the models
- Routes for the controller should begin with the same prefix (eg. comments/all/)
- Should never directly access a database
- index.js to load controllers (app.use()) and define paths without common prefix

## Middleware
- Extract common controller code to be used on multiple requests (eg. checking auth token)
- Should never directly access the database, instead use models

## Helpers
- Utility code used by Models, Middleware and Controllers, which does not fall under any category

## Public
- Static files only
- Subfolders such as css, libs, img
- Best to be served by nginx or Apache, as they are better at serving static files than Node.

## Tests
- Separate into subfolders
  - controllers
  - helpers
  - models
  - middlewares
  - integration
  - ui
