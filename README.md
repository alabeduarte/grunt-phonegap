# grunt-phonegap

> Local build tasks for [Phonegap](http://phonegap.com/) applications

`grunt-phonegap` integrates Phonegap development with [Grunt](http://gruntjs.com/)-based workflows
by wrapping the Phonegap 3.0 command line interface.

Rather than polluting the top-level of your project, `grunt-phonegap` copies your files into a
subdirectory containing the Phonegap project, which gets regenerated every build.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-phonegap --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-phonegap');
```

### Overview
In your project's Gruntfile, add a section named `phonegap` to the data object passed into `grunt.initConfig()`.

Point `phonegap.config.root` to the output of your other build steps. At the very least, it should contain your
[config.xml](http://docs.phonegap.com/en/3.0.0/config_ref_index.md.html) and `index.html` files.

`phonegap.config.cordova` should be the `.cordova` directory that is generated by `phonegap create`. It must
contain a `config.json` file or your app cannot be built.

### Options

```js
grunt.initConfig({
  phonegap: {
    config: {
      root: 'www',
      config: 'www/config.xml',
      cordova: '.cordova',
      path: 'phonegap',
      plugins: ['/local/path/to/plugin', 'http://example.com/path/to/plugin.git'],
      platforms: ['android'],
      verbose: false
    }
  }
})
```

### Tasks

#### phonegap:build

Running `phonegap:build` with no arguments will...

* Purge your `phonegap.config.path`
* Copy your `phonegap.config.cordova` and `phonegap.config.root` files into it
* Add any plugins listed in `phonegap.config.plugins`
* ..and then generate a Phonegap build for all platforms listed in `phonegap.config.platforms`

#### phonegap:run[:platform][:device]

After a build is complete, the `phonegap:run` grunt task can be used to launch your app
on an emulator or hardware device. It accepts two optional arguments, `platform` and `device`.

Example: `grunt phonegap:run:android:emulator`

If you are using the Android platform, you can see the list of connected devices by running `adb devices`.

The platform argument will default to the first platform listed in `phonegap.config.platforms`.

The device argument will default to "device", the default name for the first Android device connected to your machine.

## What's next

* Creating signed releases (`phonegap:release`)

## Contributing

Fork the repo on Github and open a pull request. Note that the files in `tasks/` and `test/` are the output of
CoffeeScript files in `src/`, and will be overwritten if edited by hand.

## Release History

#### 0.2.0

  * Adds 'config' option for specifying a custom path to 'config.xml'.

#### 0.1.0

  * Initial release


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/logankoester/grunt-phonegap/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

