# Tomacco Wiki

The Tomacco Wiki Software - Read optimized wiki, simple to run

## Motivations

- I want to be able to run a wiki without running a server and database
- I want the wiki to be free and extremely cheap to run
- I want the be able view and edit on mobile
- I want the pages to be fast
- I want to be able to optionally edit with a rich text interface
- I want to be able to run a copy of it locally

## Assumptions

- Reads will dominate requests except during a quick succession of edits with will happen over the course of minutes
- It makes sense to serve static HTML that is updated only when the page is edited
- Serving from S3 makes a lot of sense
- S3 (I think) only has atomicity at the level of objects, which means we will need to come up with a mechanism to catch collisions
- Git is the obvious choice for datastore, probably want to use a seperate git repo for each page
- Markdown is the obvious choice for markup language (which Markdown?)
- Will probably need to run some sort of server component for updates but maybe we can make use of AWS Lambda
- Making use of github to serve and store wiki would also make a lot of sense, but no control over cache invalidations
- It might make sense to use time limited urls to allow client to update s3 directly
- Would very much like to edit styled text but it's not a requirement

## Experiments

- Concentrate on editing since that's going to be the hard part
- Find a javascript based markdown or rich text editor
- Have it read from a git repo in the javascript, update it, and send the blob somewhere

## Research

- [MediumEditor](http://yabwe.github.io/medium-editor/) - Rich text, looks like you are editing the webpage, 28k
- [bootstrap-wysiwyg](http://mindmup.github.io/bootstrap-wysiwyg/) - 5k, edit in seperate div
- [Trix](https://trix-editor.org)
- [Squire](http://neilj.github.io/Squire/)
- [Trumbowyg](https://alex-d.github.io/Trumbowyg/)

