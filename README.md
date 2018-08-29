# Tomacco Wiki

The Tomacco Wiki Software - Read optimized wiki, simple to run

## Motivations

- I want to be able to run a wiki without running a server and database
- I want the wiki to be free and extremely cheap to run
- I want the be able view and edit on mobile
- I want the pages to be fast
- I want to be able to optionally edit with a rich text interface

## Assumptions

- Reads will dominate requests except during a quick succession of edits with will happen over the course of minutes
- It makes sense to serve static HTML that is updated only when the page is edited
- Serving from S3 makes a lot of sense
- S3 (I think) only has atomicity at the level of objects, which means we will need to come up with a mechanism to catch collisions
- Git is the obvious choice for datastore
- Markdown is the obvious choice for markup language (which Markdown?)
- Will probably need to run some sort of server component for updates but maybe we can make use of AWS Lambda
- Making use of github to serve and store wiki would also make a lot of sense, but no control over cache invalidations
