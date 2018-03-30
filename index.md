---
layout: default
title: "PF4J"
---

<img src="{{ site.baseurl }}/pf4j-logo.svg" width="250"/>

A plugin is a way for a third party to extend the functionality of an application. A plugin implements extension points
declared by application or other plugins. Also a plugin can define extension points.  

**NOTE:** Starting with version 0.9 you can define an extension directly in the application jar (you're not obligated to put the extension in a plugin - you can see this extension as a default/system extension). See [WhazzupGreeting](https://github.com/srbala/srbala/blob/master/demo/app/src/main/java/org/srbala/demo/WhazzupGreeting.java) for a real example.
  
#### Features/Benefits

With PF4J you can easily transform a monolithic java application in a modular application.  
PF4J is an open source (Apache license) lightweight (around __50 KB__) plugin framework for java, with minimal dependencies (only slf4j-api) and very extensible (see PluginDescriptorFinder and ExtensionFinder).   

Practically PF4J is a microframework and the aim is to keep the core simple but extensible. I try to create a little ecosystem (extensions) based on this core with the help of the comunity.  
For now are available these extensions:

- [pf4j-update](https://github.com/srbala/pf4j-update) (update mechanism for PF4J)
- [pf4j-spring](https://github.com/srbala/pf4j-spring) (PF4J - Spring Framework integration)
- [pf4j-web](https://github.com/rmrodrigues/pf4j-web) (PF4J in web applications)
- [wicket-plugin](https://github.com/srbala/wicket-plugin) (Wicket Plugin Framework based on PF4J)

No XML, only Java.

You can mark any interface or abstract class as an extension point (with marker interface ExtensionPoint) and you specified that an class is an extension with @Extension annotation.

Also, PF4J can be used in web applications. For my web applications when I want modularity I use [Wicket Plugin](https://github.com/srbala/wicket-plugin).

#### Components

- **Plugin** is the base class for all plugins types. Each plugin is loaded into a separate class loader to avoid conflicts.
- **PluginManager** is used for all aspects of plugins management (loading, starting, stopping). You can use a built-in implementation as `DefaultPluginManager`, `JarPluginManager` or you can implement a custom plugin manager starting from `AbstractPluginManager` (implement only factory methods).
- **PluginLoader** loads all information (classes) needed by a plugin.
- **ExtensionPoint** is a point in the application where custom code can be invoked. It's a java interface marker.   
Any java interface or abstract class can be marked as an extension point (implements `ExtensionPoint` interface).
- **Extension** is an implementation of an extension point. It's a java annotation on a class.
