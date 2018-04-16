# JavaScript Writing Guide

**NOTICE: This document is prone to change after convincing arguments.**

## Project Guide

 * Follow the projects .eslint file
 * Do not use transpilers
 * Do not use minifiers, use gzip instead and comment strippers
 * Use argparse over environment variables
 * Do not use unnessary build tools, shell scripts do 99% of what they can do

### Packages

 * Install from git repo URL with hash
 * Look for stable packages without any or many dependencies
 * Copy and paste code if you only require small sections or snippets,
   provide link back to origin
 * Do not install packages which require native building

## Writing Guide

 * Method and variable names should be self explanatory and not hide intentions
 * Do not use single letter variable names, exception for iterators
 * Use async libraries and break down your methods to escape callback hell
 * Use expansion loading of library methods when possible

### Anonymous Functions

 * Use arrow functions or don't be anonymous (name it)
 * Use for quick and easy such as array mapping, filter, etc. or request callbacks
 * Binding arguments is preferred over long anonymous functions that require scope variables

### Error Handling

 * Always handle errors
 * Only use throwing & try, catch when need be
 * Instead of throwing an error you can return an array or object which can be destructured.
   This allows similar style of multiple return value handling such as in golang or python

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

### Strings

Use (\`) over (") over ('). Other than that it will be okay.

### Documentation

 * Use JSDocs
 * All exported methods should be documented
 * If you can't imply everything a method does by it's name, describe it
 * Always include parameters and return types, undefined is assumed

**Example**

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
