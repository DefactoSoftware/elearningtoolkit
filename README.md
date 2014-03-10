Defacto Elearning toolkit (Prototype)
================

This is a prototype for html/css/js-based e-learning Authoring using Middleman. The ultimate goal is to come up with a strong and modern 
authoring environment that combines the power of the newest web technologies with user-friendly authoring. Eg. [Markdown](https://help.github.com/articles/markdown-basics) meets git.
Some of the apparent advantages will hopefully be: 

* Easier to create responsive designs.
* Easier to create mobile-ready e-learning content.
* Ability to use the newest in CSS, HTML & JavaScript.
* Ability to let designers create templates with familiar technologies.
* Ability to let authors write in markdown.
* Multi-Language without any hassle.
* Automated deploys to staging and production environments.
* Version control (near impossible with authoring tools that output large binaries).
* Online collaboration (pull-request workflow, line comments, issue tracking, branches, milestones, releases).

What we are not (yet) doing: 
* SCORM support, ~~probably never gonna happen.~~ _edit: oops, it happened again_
* Providing a simple client-side multiple choice quiz option, worth lookin into :)
* ...suggestions?

## Some possibly attainable awesome goals: 
- Creating a "Starter" repository that authors can fork to kickstart their e-learning development
- Creating a Middleman template + extension so anybody can run something like `middleman generate "Projectname" --elearning`

## Dependencies
* Git, obviously
* Ruby (install with [rbenv](https://github.com/sstephenson/rbenv))
* Rubygems
* Bundler (`gem install bundler`)
* [Middleman](middlemanapp.com)
 
### Open Source libraries used
* [Middleman Deploy GEM](https://github.com/tvaughan/middleman-deploy) to deploy, currently to Github Pages
* [Bourbon](http://bourbon.io/)
* [Bitters](https://github.com/thoughtbot/bitters)
* [Neat](http://neat.bourbon.io/)
* https://github.com/kylefox/jquery-modal 
* This [SCORM GEM](https://github.com/mindset/scorm) to generate and budnle the necessary SCORM stuff. 
* The [Pipwerks SCORM Api wrapper is included in the project](https://github.com/pipwerks/scorm-api-wrapper/)

I'm actually not a 100% sure if compass is still playing a significant role in all this, but it comes with Middleman, so...
N.b. I am abusing the s*** out of Middleman's [YAML](http://en.wikipedia.org/wiki/YAML) [Frontmatter](http://middlemanapp.com/basics/frontmatter/). 

## Getting it to work 
1. clone this repository (`git clone git@github.com:DefactoSoftware/elearningtoolkit.git`)
2. run `bundle install`
3. run `middleman server`
4. go to localhost:4567
5. ask me why it's not working

## Deploying
This prototype is configured to deploy to Github pages through the gh-pages branch of this repository. 
This can be conveniently used as staging / demo environment. 
Run the following to deploy to http://defactosoftware.github.io/elearningtoolkit/

```
$ middleman build 
$ middleman deploy 
```

## Authoring
This prototype is supports authoring a specific type of e-learning module. Therefore form & function are very mixed up.
In /source you will find a bunch of .markdown.erb files. These files contain the content of the demo module (http://defactosoftware.github.io/elearningtoolkit/), 
partially in markdown and partially in YAML frontmatter. You can edit these to see what happens (but create a new branch when pushing to origin).
Images and videos are found in source/images, placing files there and referring to them in the frontmatter does the trick. But only if that specific lay-out uses images of course :)

## SCORM support: 
1. Build your project using `middleman build`.
2. Use `scorm create build` to generate the necessary SCORM files.
3. Go to `/build` and add all resources to `imsmanifest.xml` (see `sample.imsmanifest.xml` for what you should include and syntax)
4. run `scorm bundle` in the build folder.
5. locate `build.zip` in your build folder, there you go.

