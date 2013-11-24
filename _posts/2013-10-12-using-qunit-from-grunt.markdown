---
layout: post
title: "Using qunit from grunt"
date: 2013-10-12 15:53
comments: true
categories: testing, automation
---

When poking around in the [jquery](http://jquery.com) and [jquery ui](http://jqueryui.com) codebases I noticed an extensive use of [qunit](http://qunitjs.com) from [grunt](http://gruntjs.com). I get it that the jquery guys also did qunit - so this makes sense. But why grunt? I remember the earlier versions just used makefiles.

#[Grunt](http://gruntjs.org) and [npm](http://npmjs.org) replaces [make](http://www.gnu.org/software/make/), [autoconf](http://www.gnu.org/software/autoconf/) and [apt](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool) for javascript projects

I remember Makefiles as simple - just as long as you got the use of tabs right and kept them simple. It was just "the other tools"  that made the experience bad for me. Remember [automake](http://www.gnu.org/software/automake/) and [m4 scripting](http://en.wikipedia.org/wiki/M4_\(computer_language\))? Not to mention [cmake](http://www.cmake.org/). Tools like Make or ant are simple tools in themselves - they started getting complicated when the tradition to use associated tools arose - like Makefiles tend to assume that dependencies are handled using [automake](http://www.gnu.org/software/automake/) and m4 scripts and ant buildfiles retrieve dependencies with tools like [ivy](http://ant.apache.org/ivy/). When I consider the complexity I know from existing build toolchains on linux, then grunt starts to look simple. The simplicity of grunt comes from how easy it is to combine grunt plugins as compared to how complex the build situation using other tools has become.  Using grunt it is now possible to build using only javascript based tools.

#Installing [grunt](http://gruntjs.org) and [npm](http://npmjs.org).

To be able to use grunt you will need [nodejs](http://nodejs.org) and [npm](http://npmjs.org).  You can find a nodejs installer for most platforms at [nodejs.org](http://nodejs.org) - this will include npm. When you install you should make sure that the "node" and "npm" commands are available on your commandline via your "PATH" environment variable. (For my less commandline-savvy friends there are some detailed instructions for windows 7 [here](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx))

You can install grunt globally from the commandline like this: 

{% highlight bash %}
npm install grunt-cli
{% endhighlight %}

To take your newly installed grunt for a spin, you could try it out with building [jquery-ui](https://github.com/jquery/jquery-ui). To checkout jquery-ui you could do this:

{% highlight bash %}
git clone http://github.com/jquery/jquery-ui
cd jquery-ui
npm install
grunt --force
{% endhighlight %}
	
This should take you through an example of using grunt on an existing project. If all goes well then  all the tests should pass and a new jquery-ui build should be avaible to you inside the "dist" folder.

#Scaffolding a grunt project that supports qunit

The major strength of grunt is its strong tradition for [plugins](http://gruntjs.com/plugins) - but  when starting up it can also be a major drawback.  you need to setup   some plugins to be able to start working. It does not help that the grunt-init command has been separated out in a plugin in version 0.4 (most of the existing blog entries just refers to it as being inside grunt) . See The [Project scaffolding](http://gruntjs.com/project-scaffolding) section in docs for more information. 

To be able to run grunt-init you need to install the grunt-init plugin and grab a working template to start working: 

{% highlight bash %}
npm install -g grunt-init
cd c:\users\jacob\.grunt-init
git clone https://github.com/gruntjs/grunt-init-gruntfile.git ~/.grunt-init/gruntfile gruntfile
{% endhighlight %}

Note that my username is "jacob" and that I am on windows here. You will probably have to insert another directory.

Now I could run "grunt-init gruntfile" and answer a couple of questions:

{% highlight bash %}
D:\Sites\2>grunt-init gruntfile --force
Running "init:gruntfile" (init) task
This task will create one or more files in the current directory, based on the
environment and the answers to a few questions. Note that answering "?" to any
question will show question-specific help and answering "none" to most questions

will leave its value blank.

Warning: Existing files may be overwritten! Used --force, continuing.

"gruntfile" template notes:
This template tries to guess file and directory paths, but you will most likely
need to edit the generated Gruntfile.js file before running grunt. If you run
grunt after generating the Gruntfile, and it exits with errors, edit the file!

Please answer the following:
[?] Is the DOM involved in ANY way? (Y/n)
[?] Will files be concatenated or minified? (Y/n)
[?] Will you have a package.json file? (Y/n)

{% endhighlight %}

After hitting Enter three times I got this file "Gruntfile.js":

{% highlight JavaScript %}
/*global module:false*/
module.exports = function(grunt) {

  // Project configuration.
  grunt.initConfig({
    // Metadata.
    pkg: grunt.file.readJSON('package.json'),
    banner: '/*! <%= pkg.title || pkg.name %> - v<%= pkg.version %> - ' +
      '<%= grunt.template.today("yyyy-mm-dd") %>\n' +
      '<%= pkg.homepage ? "* " + pkg.homepage + "\\n" : "" %>' +
      '* Copyright (c) <%= grunt.template.today("yyyy") %> <%= pkg.author.name %>;' +
      ' Licensed <%= _.pluck(pkg.licenses, "type").join(", ") %> */\n',
    // Task configuration.
    concat: {
      options: {
        banner: '<%= banner %>',
        stripBanners: true
      },
      dist: {
        src: ['lib/<%= pkg.name %>.js'],
        dest: 'dist/<%= pkg.name %>.js'
      }
    },
    uglify: {
      options: {
        banner: '<%= banner %>'
      },
      dist: {
        src: '<%= concat.dist.dest %>',
        dest: 'dist/<%= pkg.name %>.min.js'
      }
    },
    jshint: {
      options: {
        curly: true,
        eqeqeq: true,
        immed: true,
        latedef: true,
        newcap: true,
        noarg: true,
        sub: true,
        undef: true,
        unused: true,
        boss: true,
        eqnull: true,
        browser: true,
        globals: {}
      },
      gruntfile: {
        src: 'Gruntfile.js'
      },
      lib_test: {
        src: ['lib/**/*.js', 'test/**/*.js']
      }
    },
    qunit: {
      files: ['test/**/*.html']
    },
    watch: {
      gruntfile: {
        files: '<%= jshint.gruntfile.src %>',
        tasks: ['jshint:gruntfile']
      },
      lib_test: {
        files: '<%= jshint.lib_test.src %>',
        tasks: ['jshint:lib_test', 'qunit']
      }
    }
  });

  // These plugins provide necessary tasks.
  grunt.loadNpmTasks('grunt-contrib-concat');
  grunt.loadNpmTasks('grunt-contrib-uglify');
  grunt.loadNpmTasks('grunt-contrib-qunit');
  grunt.loadNpmTasks('grunt-contrib-jshint');
  grunt.loadNpmTasks('grunt-contrib-watch');

  // Default task.
  grunt.registerTask('default', ['jshint', 'qunit', 'concat', 'uglify']);

};

{% endhighlight %}

To be able to run this Gruntfile you need to install the necessary plugins. If you append "--save-dev" to the installation commands then installation info will inserted into package.json:

{% highlight bash %}
npm install grunt-contrib-jshint --save-dev
npm install grunt-contrib-qunit --save-dev
npm install grunt-contrib-watch --save-dev
npm install grunt-contrib-concat --save-dev
npm install grunt-contrib-uglify --save-dev
{% endhighlight %}

This will retrieve the plugins and place them inside the node_modules and add them inside the devDependencies section of package.json . As you might have noticed the Grunt files are a bit verbose but they support easy composition of plugins - e.g. if you would like to another target , using another plugin , then you could do this pretty easily. The grunt files are written in javascript, so if you wish to insert custom logic in the build files, then it should be pretty easy to do so (Without worrying about tabs and spaces  ).

Note that once you have created package.json describing your dependencies, then you can simple write "npm install" to install your dependencies. There is no need to store the "node_modules" folder in your version control system.

#[Qunit](http://qunitjs.org) replaces [junit](http://junit.org) and [phpunit](http://phpunit.de/manual/current/en/index.html) on the frontend.

After installing  grunt-contrib-qunit and enabling it your gruntfile you now have the option of writing automated [qunit](http://qunitjs.com/) tests that can be run  directly from grunt. grunt-contrib-qunit uses [phantomjs](http://phantomjs.org/) behind the scenes to enable you run your tests directly from grunt (without opening a browser). This should make it easier to automate your tests.

I think that best way to learn qunit is to look at existing tests. The [button core test in jquery ui](https://github.com/jquery/jquery-ui/blob/master/tests/unit/button/button_core.js) is a good place to start.

The essential functionality in qunit is :

* ok (truthy [,message]) 
* assert ( value, expected [,message])
* expect ( number of assertions)

Combining these let's you write a test like the check for [#7534 in jquery ui](http://bugs.jqueryui.com/ticket/7534):

{% highlight JavaScript %}

test( "#7534 - Button label selector works for ids with \":\"", function() {
  expect( 1 );
  var group = $( "<span><input type='checkbox' id='check:7534'> <label for='check:7534'>Label</label></span>" );
  group.find( "input" ).button();
  ok( group.find( "label" ).is( ".ui-button" ), "Found an id with a :" );
});
{% endhighlight %}

Here we expect 1 assertion to be run.

There are more advanced options in qunit that you can explore - feel free to take a look at the documentation on [qunitjs.com](http://qunitjs.com/) - or be inspired by the existing tests in [jquery-ui](https://github.com/jquery/jquery-ui/tree/master/tests/unit)
