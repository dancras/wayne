# Meet Wayne

Wayne is a dependency injection container.

Wayne thinks service configuration should describe how an application works as
well as code describes how an object works.

Here is a short overview of Wayne's service configuration options:

```js
{
    /*
     * Definition for a service named "app". There are several ways to access
     * this service described in the docs.
     */
    "app": {

        /*
         * The path of the module to be loaded. There is a simple requirejs
         * module loading adapter available, but you can easily create your
         * own for whatever style your prefer to use.
         */
        "module": "project/app",

        /*
         * The type tells Wayne how to initialise your module; either with the
         * new operator, calling it as a function, or simply returning it as
         * defined.
         */
        "type": "constructor" || "function" || "object",

        /*
         * Args are passed to the service at creation. Special notations can be
         * used for any values defined in the container. Shown here are:
         * 
         *   @myService : Load a service from the container named "myService"
         *
         *   %myParameter : Load a parameter named "myParameter"
         *
         *   5 : A specific value
         *
         * Creating or replacing notations is simple.
         */
        "args": ["@myService", "%myParameter", 5],

        /*
         * Scope tells Wayne how long to keep using the same instance of a
         * service. When falsy, Wayne will create a new instance everytime a
         * service is requested. When set to a string, Wayne will remember an
         * instance until the scope of that name is cleared.
         */
        "scope": false || "nameOfScope",

        /*
         * Tags provide a way of applying repeated configuration or behaviour
         * to your services by intercepting them at various points in their
         * lifecycle. Liberal use of tags will help you to identify new
         * abstractions in your application and reduce grubby boilerplate code.
         */
        "tags": {
            "logged": { methods: ["run"] },
            "profiled": { methods: ["run"] },
        }
    }
}
```
