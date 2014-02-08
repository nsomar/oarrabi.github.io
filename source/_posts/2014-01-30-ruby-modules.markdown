---
layout: post
title: "Ruby Modules"
date: 2014-01-30 01:49:26 +0300
comments: true
categories: 
---
# Modules
* `Module` is a subclass of `Object`
* `Module` is what hold classes, variables and methods together

ie:

    module ModuleName
        classes
        instance and module methods
        variables
        globals
    end
{:lang="ruby"}

<!--more-->

* Module is just a holder, it cannot be instantiated

##Including And Extending

###Including
    class MyClass
        include SomeModule
    end
{:lang="ruby"}

Instance method/vars from `module` will be attached to `class` as instance members

###Extending
    obj.extend Module
{:lang="ruby"}

Instance method/vars from `Module` will be attached to that instance as instance members

    obj.class.extend Module
    Class.extend Module
{:lang="ruby"}

Instance method/vars from `Module` will be attached to Class instance as instance members,

Instance members to the Class Instance will be class members

