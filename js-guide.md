JavaScript Writing Guide
========================

**NOTICE: This document is prone to change after convincing arguments.**

This guide is the required style of writing JavaScript for my related projects.

Immediate Notes
---------------

*   Do not use transpilers.
*   Do not use minifiers, use gzip instead and comment strippers.
*   Method names should be self explanatory.
*   Do not use single letter variable names, execpt for iterators.
*   Use camel casing for all variable and method names. Dictionaries and remote  
    data sources need not apply.
*   Do not use semi-colons `;`.
*   Constant variables should be declared with `const` and in uppercase.
*   Use returns to escape if statement fatigue.
*   Never write more than one callback scope. If you need to chain use a library.
*   Use expansion loading for including methods instead of requiring entire  
    libraries.
*   Never return multiple types from a function.
*   When writing tools always use an argparse library.

Spacing
-------

*   Use **spaces** instead of tab characters.
*   Use **2 spaces per tab**.
*   Use a space between operators.
*   Use a space or newline between brace content.
*   Do not use a space between parenthesis.
*   Use a space before and after method parenthesis.
*   Use a space before and after if and switch statement parenthesis.
*   Do not use single line if statements

Anonymous Functions
-------------------

*   Only use arrow (`=>`) anonymous functions.
*   Should be inline or single line.
*   If you need an anonymous function make it a regular named function in the  
    appropriate scope or make it a higher level method. This will save you from  
    tracking down anonymous function debug calls.

Error Handling
--------------

*   Always handle errors.
*   Never use try/catch unless it's for a native API call or an unmodifiable  
    library.
*   If your method needs to return more than one type for the error return the  
    values as an array where the first value is always an error or null and the  
    rest are the possible results. Use destructuring expansion to pull values.

**Example**

    /**
     * Safely divide or return an error!
     *
     * @param {Number} a
     * @param {Number} b
     *
     * @return {[Error, Number]} results
     */
    function divide (a, b) {
      if (b == 0)
        return [Error("Parameter \"b\" can't be zero!")]
      return [null, a / b]
    }
    
    let [err, result] = divide(1, 0)
    if (err) {
      console.log("It didn't work: ", err.message)
    } else {
      console.log("It worked:", result)
    }

Quoting
-------

Use double quotes (") for text, grave accent (`) for multi line text,  
otherwise single quote (').

Packages
--------

*   Only install packages from git repositories with a hashed URL.
*   Use packages that do not have a lot of dependencies.
*   Copy and paste simple methods instead of downloading as a package. Add  
    documentation of where you found it.
*   Do not install packages that require native build-able dependencies.
*   Do not use global packages for projects.
*   Do not use unnecessary build tools such as Gulp, WebPack, Browserify, etc.

Documentation
-------------

Use JSDocs formating and document every named method.

*   If you can't imply what a function does by it's name then write a  
    description.
*   Do not include the method name in the documentation.
*   Always include parameters and return data types if any.

Example
-------

    const IS_ON = true
    const MEANINGFUL_DATE = 1516853925696
    
    /**
     * An example of a method for the purpose of this example.
     *
     */
    function startMyApp () {
      if (IS_ON)
        print("Hi there.")
    
      if ((new Date()).getTime() > MEANINGFUL_DATE) {
        print("Oh hey!")
      } else {
        print("Oh no!")
        return
      }
    
      let arrPlusOne = [1, 2, 3].map(x => x + 1)
    }
    
    /**
     * Outputs the string to stdout.
     *
     * @param {String} str
     */
    function print (str) {
      console.log(str)
    }
