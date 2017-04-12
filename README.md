# Swagger Codegen Quickstart Tutorial
This is a VERY quick tutorial on the use of Swagger codegen.  It's intended to help you move quickly from defining your service in Swagger to writing the code for the service.  Using Swagger codegen minimizes coding style differences and promotes readability and reusability of code between development teams.

In this tutorial, we will cover:
* Swagger Definition Basics
* Installing Swagger Codegen
* Scaffolding a Service with Swagger Codegen


## Swagger Definition Basics
Swagger definitions are JSON or YAML representations of an API.  In the definition, you can describe paths, resources, allowed operations and authentication details and more.  For example, take a look at the petshop.yaml file included in this repository.  In this example, we have the Swagger definition of the API for a Pet Shop.  At the top of the definition, the API version and base path (along with other values) are set.  Below that, a resource called "pet" is defined including that resource's allowed operations, authorization requirements, parameters and responses.  For the full details of the Swagger specification, check out the documentation here:  http://swagger.io/specification/

By defining APIs in this way, we capture the requirements of the API.  Annotations can also be applied to each configuration to make the definition easier to read.  Those annotations can be consumed in a later phase to generate documentation AND code comments when the definition is used in conjunction with Swagger codegen.

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

`swagger-codegen generate -i petshop.yaml -l python-flask -o ./petshop`

Let's parse that command:  `generate` is used to invoke the code generation function.  `-i petshop.yaml` specifies the Swagger definition to read.  `-l python-flask` tells the code generator to create a server stub using python & flask.  `-o ./petshop` tells the code generator to create the project structure in the directory "petshop".  Pretty straightforward.  

In real world use, it's not unusual to get parsing errors on definitions you've created.  Usually, it's a formatting issue.  If you run into that problem, the quick way to diagnose the source is to utilize Swagger Online Editor http://swagger.io/swagger-editor/.  You can import your .yaml or .json formatted Swagger definition into the editor and it will show you (in most cases) all the small, silly things in your definition that can cause exceptions in the codegen process.  For this example, the file has already been validated so the code generator shouldn't throw errors or exceptions.  

Once the command has completed, take a look in the "petshop" directory.  You'll notice a new "swagger_server" directory.  If you look in the "swagger_server", directory you'll find the structure for the petshop service!  Let me draw your attention to a couple files to illustrate what the code generator has done.  

First, look at the "models" directory.  You'll see the model for the resource "Pet" we defined in the Swagger definition.  If you explore this file, you'll see the correlation between the the resource "Pet" in the Swagger definition and the class "Pet" created by the code generator.  

Also take a look in the "controllers" directory at the "default_controller.py".  First, You'll notice that all of the Operation IDs that we specified in the Swagger definition have been converted into functions.  You'll also notice several instances of the string "do some magic".  This is where you need to insert the code required to execute the defined operation.  So this is literally "INSERT YOUR CODE HERE".

By following this approach, you can get new services up-and-running quickly, with automatic documentation and a high degree of consistency from developer to developer.  
