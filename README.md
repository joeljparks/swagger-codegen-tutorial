# Swagger Codegen Quickstart Tutorial
This is a VERY quick tutorial on the use of Swagger codegen.  It's intended to help you move quickly from defining your service in Swagger to writing the code for the service.  Using Swagger codegen minimizes coding style differences and promotes readability and reusability of code between development teams.

In this tutorial, we will cover:
* Swagger Definition Basics
* Installing Swagger Codegen
* Scaffolding a Service with Swagger Codegen


## Swagger Definition Basics
Swagger definitions are JSON or YML representations of an API.  In the definition, you can describe paths, resources, allowed operations and authentication details.  For example, take a look at the petshop.yml file included in this repository.  In this example, we have the Swagger definition of the API for a Pet Shop.  At the top of the definition, the API version and base path (along with other values) are set.  Below that, a resource called "pet" is defined including that resource's allowed operations, authorization requirements, parameters and responses.  For the full details of the Swagger specification, check out the documentation here:  http://swagger.io/specification/

By defining APIs in this way, we capture the requirements of the API.  Annotations can also be applied to each configuration to make the definition easier to read.  Those annotations can be consumed in a later phase to generate documentation OR code comments when the definition is used in conjunction with Swagger codegen.

Swagger codegen is used to read a Swagger definition (such as the Pet Shop example above) and generate boilerplate code to speed up the development process.  The generation of boilerplate code is often referred to as "Scaffolding".  By defining the API in Swagger and creating the scaffolding using Swagger codegen, we minimize the differences in coding styles between teams.  This promotes readability as well as reusablility to code between teams in addition to shortening the development cycle.  All you have to do is "fill in the blanks" with the code that should be executed by each method defined.

Let's assume for this tutorial that you created the Pet Shop Swagger definition.  You now need to build the Pet Shop service to that specification.  Let's walk through the steps necessary to scaffold the petshop service using Swagger codegen.  

## Installing Swagger Codegen
First things first:  If you don't already have it, you'll need to install Swagger codegen.  Won't do you much good if you can't run it.  :)

The full installation documentation (for many platforms) is located here:  https://github.com/swagger-api/swagger-codegen/#prerequisites

## Scaffolding a Service with Swagger Codegen

Now that you have Swagger codegen installed, let's verify that it's working.  Run the command:

`swagger-codegen version`

You should get a response.  In my case (running on OSX), Homebrew installed v2.2.2.  If you don't get a response or get a 'command not found' check the troubleshooting section on the installation document in the previous section.

Now that your installation is up and running, you have to decide what language you'd like to implement the Pet Shop service in.  Swagger codegen currently supports a large number of languages.  You can find the full list here:  https://github.com/swagger-api/swagger-codegen/#overview or by typing:

`swagger-codegen`

The default output of the command lists the languages supported by your version.  For this example, let's assume that you're most comfortable with Python and Flask.  So how do we generate the scaffolding for the Pet Shop service in Python using Swagger codegen?  It's as simple as:

`swagger-codegen generate -i petshop.yaml -l python-flash -o ./petshop`

If you look in the "petshop" directory, you'll now see the scaffolding for your service!  
