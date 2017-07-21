# Webpack interview questions (EARLY DRAFT VERSION)


## Table of Contents

* [Concepts](#concepts)
* [Config file](#config-file)
* [Loaders](#loaders)
* [Plugins](#plugins)
* [Debugging](#debugging)
* [Optimization](#optimization)
* [Migration](#migration)
* [Advanced-questions](#advanced-questions)


#### Concepts
* What is webpack?
* What is the main difference between webpack and other build tools like gulp and
* What is bundle in webpack?
* In which environment webpack works?

#### Config file
* Describe webpack configuration files
* What is `entry` point?

#### Loaders
* What is loader in webpack
* Do loaders work in synchronous or asynchronous way?
 
#### Plugins
* Describe plugin in webpack
* What is difference between loader and plugin
* Name plugins you think are very important and helpful

#### Debugging

#### Optimization
* Briefly describe long-term caching and how to achieve it using webpack?
* What is difference between
  
    ```javascript
       ...
       output: {
        filename: "[name].[hash].js"
       }
       ...
   ```
        and
   ```javascript
      ...
       output: {
        filename: "[name].[chunkhash].js"
       }
       ...
    ```
* Describe CommonsChunkPlugin
* What analyzes tools you use to inspect your webpack bundle?

#### Migration

#### Advanced questions


### Answers

  A: webpack is a module bundler for javascript applications. Webpack recursively builds every module in your application, then packages all of those modules into a small number of bundles.


  A: node.js
  
  A: Loaders are transformations that are applied on the source code of a module. webpack supports modules written in a variety of languages and preprocessors, via loaders. Loaders describe to webpack how to process non-javaScript modules and include these dependencies into your bundles.

  A: Both. Loaders can work synchronous or asynchronous.
  
  A: webpack plugin is -

  A: raw-loader, url-loader, html-loader, file-loader, style-loader, css-loader, script-loader, babel-loader, loaders for typescript, coffescript, less, sass, pug, markdown, etc.
  A: CommonsChunkPlugin, DefinePlugin, HtmlWebpackPlugin, ExtractTextWebpackPlugin, CompressionWebpackPlugin

  A:  Browsers should cache static assets to save traffic and users time. But after each change or bugfix, browser have to download newer version of files. The most easy way to achieve this is changing file name. It could be buildId or unique hash in the end of file's name like
    
   ```javascript
       app.js?build=1
       app.js?build=2
    ```  
   or 

    ```javascript
     app.js.2a6c1fee4b5b0d2c9285.js
     app.js.70b594fe8b07bcedaa98.js
     ```
  
    To achieve this using webpack simple configuration should be done
  
  
    ```javascript
      module.exports = {
       ...
       output: {
        filename: "[name].[hash].js"
       }
       ...
      }
    ```

   A: [hash] will generate unique hash for each build and use it for all chunks. Replace `[hash]` with `[chunkhash]` to generate unique hashes for each chunk. This is useful when you dont want to re-download vendors (dependencies) file but you have changes in your application code and want to update it.

    
 A: webpack-bundle-analyzer plugin, official webpack analyze tool, webpack visualizer, webpack chart
    
