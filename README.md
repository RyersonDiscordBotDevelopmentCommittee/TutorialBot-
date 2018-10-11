# TutorialBot-
This repo features boilerplate code for discord bot development using Java, Discord API and the JDA wrapper.

# What is Gradle?

Before we delve into this TutorialBot utilizing the JDA wrapper for our discord bot. We're going to start of with building this project with Gradle.

Well, what is Gradle in the first place?

Gradle is an advance build toolkit that manages dependencies and allows defining our custom build logic.

It's build automation tool often used for JVM languages such as Java, Groovy or Scala. Gradle can be
configured to run tasks which do things like compile jars, run tests, create documentation and much more.

Let's take a look at the *build.gradle* file. Of course, we'll be using Java for the project but the same
concepts for other languages.

[insert pic]

Gradle build scripts are written in *Groovy* which is a JVM language similar to Java but with a more concise syntax.

# The Groovy Console

We can try out the groovy scripts using the groovy console IntelliJ under *tools -> groovy console*.

In this console area, we can type in any valid Java code:

        System.out.println("Hello Groovy");

Running that snippet of code, we'll see the output in a window underneath:

        hello groovy

Something to note is that we don't need a surrounding class and main method to execute our code.
But we can go further. Groovy automatically imports *System.out* so we can omit that:

        println("Hello Groovy");

Parentheses for single argument method calls and semicolons are also optional in Groovy,
so we can reduce *System.out.println("Hello Groovy");* to:

        println "Hello Groovy"

# Groovy Closures

Now we're moving onto Groovy closures which will really break down whats going on in the *build.gradle* file.
If you've used Java 8's lambdas, groovy closures will feel familiar - they effectively let you treat methods as regular values
(so they can be used as arguments to other methods). Let's have a look at an example:

In the groovy console, we can define a class like this:

        class MyClass {

        }

Let's add a method that takes a closure:

        class MyClass {

            void doSomething(Closure closure) {
                closure.call()
            }

        }

We can "run" whatever code is in the closure with **closure.call()**, but would we use this? We'll create an instance of **MyClass**
and call **doSomething** like so:

         class MyClass {

            void doSomething(Closure closure) {
                closure.call()
            }

         }

         myClass = new MyClass()

         myClass.doSomething {
            println "doing something"
         }


which outputs:

        doing something


Now let's talk about dependencies:

        dependencies {
            testCompile group: 'junit', name: 'junit', version: '4.12'
        }

**Dependencies** is a **method** which takes a "runnable" block of code (a closure). Inside that block we've calld the **testCompile**
method with **group: 'junit'** etc as an argument (the **group, name, version** section is actually shorthand for a grooy **map**,
essentially a list of key-value pairs.