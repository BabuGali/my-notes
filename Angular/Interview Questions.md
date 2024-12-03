1. How Angular works ?
	- Every Angular app consists of a file named **angular.json**. This file will contain all the configurations of the app. While building the app, the builder looks at this file to find the entry point of the application
	- Inside the build section, the main property of the options object defines the entry point of the application which in this case is **main.ts**.
	- The main.ts file creates a browser environment for the application to run, and, along with this, it also calls a function called **bootstrapModule**, which bootstraps the application.
	- plaintext platformBrowserDynamic().bootstrapModule(AppModule)
	- In the above line of code, **AppModule** is getting bootstrapped.
	- The AppModule is declared in the app.module.ts file. This module contains declarations of all the components.
	- then **AppComponent** is getting bootstrapped.
	- AppComponent component is defined in **app.component.ts** file. This file interacts with the webpage and serves data to it.
	-  Each component is declared with three properties:
	- After this, Angular calls the **index.html** file. This file consequently calls the root component that is **app-root**. The root component is defined in **app.component.ts**. 
2. What are some of the advantages of Angular over other frameworks?
	-  Angular provides a number of built-in features like routing, state management, rxjs library and http servicesstraight out of the box. This means that one does not need to look for the above-stated features separately. They are all provided with angular.
	- **Declarative UI -** Angular uses HTML to render the UI of an application. HTML is a declarative language and is much easier to use than JavaScript.
	- **Long-term Google support**-  Google announced Long-term support for Angular. This means that Google plans to stick with Angular and further scale up its ecosystem.
3.  What are the advantages of Angular over React?
	 ![[react vs angular.png]]
4. How are Angular expressions different from JavaScript expressions?
  - The first and perhaps, the biggest difference is that Angular expressions allow us to write JavaScript in HTML which is not the case when it comes to JavaScript expressions.
  - Next, Angular expressions are evaluated against a **local** scope object whereas JavaScript expressions are against a **global** window object
5. What are single page applications?
  - Single page applications are web based applications that only need to be loaded once, with new functionality consisting of only minor changes to the user interface. It does not load new HTML pages to display the content of the new page, but rather generates it dynamically. This is made feasible by JavaScript's ability to alter DOM components on the current page. A Single Page Application method is speedier, resulting in a more consistent user experience.
6. What are templates in Angular?
  - A template is a kind of HTML that instructs Angular about how to display a component
  - An Angular HTML template, like conventional HTML, produces a view, or user interface, in the browser
  - There are two ways to create Template in Angular
	  - Inline Template
	  - Linked Template
	  - **Inline Template:** The component decorator's template config is used to specify an inline HTML template for a component. The Template will be wrapped inside the single or double quotes.
	  - ![[Pasted image 20240106112534.png]]
	  - **Linked Template:** A component may include an HTML template in a separate HTML file. As illustrated below, the templateUrl option is used to indicate the path of the HTML template file.
	  - ![[Pasted image 20240106112657.png]]
7. What are directives in Angular?
 - A directive is a class in Angular that is declared with a **@Directive** decorator.
 - Every directive has its own behaviour and can be imported into various components of an application.
 - **When to use a directive?**
 - Consider an application, where multiple components need to have similar functionalities. The norm thing to do is by adding this functionality individually to every component but, this task is tedious to perform. In such a situation, one can create a **directive** having the required functionality and then, import the directive to components which require this functionality.
8. Types of Directive?
	1. Component Directive
	2. Structural Directives
	3. Attribute Directives
	- **Structural directives**
		   - These directives are generally used to manipulate DOM elements.
		   - Every structural directive has a ‘ * ’ sign before them.
		   - We can apply these directives to any DOM element.
		   ![[Pasted image 20240106114431.png]]
	- **Attribute Directives**
			   -  These directives are used to change the look and behaviour of a DOM element.
9. How to create a custom directive?
     ![[Pasted image 20240106114920.png]]
10. Explain Components, Modules and Services in Angular?
	 - In Angular, components are the basic building blocks, which control a part of the UI for any application.
	 - A component is defined using the **@Component** decorator. Every component consists of three parts, the template which loads the view for the component, a stylesheet which defines the look and feel for the component, and a class that contains the business logic for the component.
	 - A module is a place where we can group components, directives, services, and pipes. Module decides whether the components, directives, etc can be used by other modules, by exporting or hiding these elements. Every module is defined with a @NgModule decorator.
	 - Services are objects which get instantiated only once during the lifetime of an application. The main objective of a service is to share data, functions with different components of an Angular application. 
11. What is Scope?
     - Scope is **an object that refers to the application model**
     - It is an execution context for expressions. Scopes are arranged in hierarchical structure which mimic the DOM structure of the application. Scopes can watch expressions and propagate events.
 12. What is data binding in Angular?
    - Data binding is one of the most significant and effective elements for creating communication between the DOM and the component. It makes designing interactive apps easier by reducing the need to worry about data pushing and pulling between the component and the template.
    - There are Four types of Data Binding 
	    - Property Binding
	    - Event Binding
	    - String Interpolation
	    - Two way databinding
	    -**Property Binding:** One method of data binding is called property binding. In property binding, we connect a DOM element's property to a field that is a declared property in our TypeScript component code. In reality, Angular transforms string interpolation into property binding internally.
	    **Event Binding:** Using event binding, you may respond to DOM events like button clicks and mouse movements. When a DOM event (such as a click, change, or keyup) occurs, the component's designated method is called.
	    **String Interpolation:** In order to export data from TypeScript code to an HTML template( view ), String Interpolation is a one way data binding approach. The data from the component is shown to the view using the template expression enclosed in double curly braces. The value of a component property is added by using string interpolation
 13. What is two way data binding in Angular?
     - Data sharing between a component class and its template is referred to as two-way data binding. If you alter data in one area, it will immediately reflate at the other end.
     - This happens instantly and automatically, ensuring that the HTML template and TypeScript code are always up to date. Property binding and event binding are coupled in two-way data binding.
14. What are Decorators and their types in Angular?
      - 
15. What are annotations in Angular ?
      
16. Write a code where you have to share data from the Parent to Child Component?
    --
17. Create a TypeScript class with a constructor and a function.
     -
18. Angular by default, uses client-side rendering for its applications? Can one make an angular application to render on the server-side?
   - Yes, angular provides a technology called **Angular Universal**, which can be used to render applications on the server-side.
19.  What is Eager and Lazy loading?
     **Loading:** The eager loading technique is the default module-loading strategy. Eager loading feature modules are loaded before the program begins. This is primarily utilized for small-scale applications.
	 **Lazy Loading:** Lazy loading loads the feature modules dynamically as needed. This speeds up the application. It is utilized for larger projects where all of the modules are not required at the start.
20. What is view encapsulation in Angular?
      View encapsulation specifies if the component's template and styles can impact the entire program or vice versa.

	**Angular offers three encapsulation methods:**

	- **Native:** The component does not inherit styles from the main HTML. Styles defined in this component's @Component decorator are only applicable to this component.
	- **Emulated (Default):** The component inherits styles from the main HTML. Styles set in the @Component decorator are only applicable to this component.
	- **None:** The component's styles are propagated back to the main HTML and therefore accessible to all components on the page. Be wary of programs that have None and Native components. Styles will be repeated in all components with Native encapsulation if they have No encapsulation.
21. What are RxJs in Angular ?
	-
22. How are observables different from promises?
      ![[Pasted image 20240106184138.png]]
23. Explain the concept of Dependency Injection?
     dependencies in angular are nothing but services which have functionality. The functionality of a service, can be needed by various components and directives in an application. Angular provides a smooth mechanism by which we can inject these dependencies into our components and directives.
 24. What is Pipe and parameterised pipe?
      
 26. What are lifecycle hooks in Angular? Explain a few lifecycle hooks.
      - Every component in Angular has a lifecycle, and different phases it goes through from the time of creation to the time it's destroyed. Angular provides **hooks** to tap into these phases and trigger changes at specific phases in a lifecycle.
      - **ngOnChanges( )** This hook/method is called before ngOnInit and whenever one or more input properties of the component change.This method/hook receives a SimpleChanges object which contains the previous and current values of the property.
      -  **ngOnInit( )** This hook gets called once, after the ngOnChanges hook.  It initializes the component and sets the input properties of the component.
      - **ngDoCheck( )** It gets called after ngOnChanges and **ngOnInit** and is used to detect and act on changes that cannot be detected by Angular.
      - **ngAfterContentInit( )** It gets called after the first **ngDoCheck** hook. This hook responds after the content gets projected inside the component.
      - **ngAfterContentChecked( )** It gets called after **ngAfterContentInit** and every subsequent **ngDoCheck**. It responds after the projected content is checked.
      - **ngAfterViewInit( )** It responds after a component's view, or a child component's view is initialized.
      - **ngAfterViewChecked( )** It gets called after **ngAfterViewInit**, and it responds after the component's view, or the child component's view is checked.
      - **ngOnDestroy( )** It gets called just before Angular destroys the component. This hook can be used to clean up the code and detach event handlers.
27. What are router links?
      
28. What exactly is the router state?
     - RouterState is a route tree. This tree's nodes are aware of the "consumed" URL segments, retrieved arguments, and processed data. You may use the Router service and the routerState property to get the current RouterState from anywhere in the application.
29. What does Angular Material means?
	   - Angular Material is a user interface component package that enables professionals to create a uniform, appealing, and fully functioning websites, web pages, and web apps. It does this by adhering to contemporary web design concepts such as gentle degradation and browser probability
30. What are HTTP interceptors ?
      - Using the HttpClient, interceptors allow us to intercept incoming and outgoing HTTP requests. They are capable of handling both HttpRequest and HttpResponse. We can edit or update the value of the request by intercepting the HTTP request, and we can perform some specified actions on a specific status code or message by intercepting the answer.
31. What is AOT compilation? What are the advantages of AOT?
    - Every Angular application consists of components and templates that the browser cannot understand. Therefore, all the Angular applications need to be compiled first before running inside the browser
        Angular provides two types of compilation:
		- JIT(Just-in-Time) compilation
		- AOT(Ahead-of-Time) compilation
		
		The advantages of using AOT compilation are:

- Since the application compiles before running inside the browser, the browser loads the executable code and renders the application immediately, which leads to **faster rendering**.
- In AOT compilation, the compiler sends the external HTML and CSS files along with the application, eliminating separate AJAX requests for those source files, which leads to **fewer ajax requests**.
- Developers can detect and handle errors during the building phase, which helps in **minimizing errors**.
- The AOT compiler adds HTML and templates into the JS files before they run inside the browser. Due to this, there are no extra HTML files to be read, which provide **better security** to the application.

![[Pasted image 20240108120658.png]]
32. What is Change Detection, and how does the Change Detection Mechanism work?
    - The process of synchronizing a model with a view is known as Change Detection. Even when utilizing the ng Model to implement two-way binding, which is syntactic sugar on top of a unidirectional flow. Change detection is incredibly fast, but as an app's complexity and the number of components increase, change detection will have to do more and more work.

		Change Detection Mechanism-moves only ahead and never backward, beginning with the root component and ending with the last component. This is what one-way data flow entails. The tree of components is the architecture of an Angular application. Each component is a child, but the child is not a parent. A $digest loop is no longer required with the one-way flow
33. How does one share data between components in Angular?	
	- **Parent to child using @Input decorator**
	- **Child to parent using @ViewChild decorator**
 34. How do you deal with errors in observables?
      - Instead of depending on try/catch, which is useless in an asynchronous context, you may manage problems by setting an error callback on the observer.
35. What happens when you use the script tag within a template?
     -  
 37. Difference between Java script and Typescript?
    ![[Pasted image 20240109235942.png]]