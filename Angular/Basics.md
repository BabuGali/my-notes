- Angular is a TypeScript-based front-end web application framework.
- Its compelling features and performance have made it an essential tool for any web developer to have in their toolbox
- It is maintained by Google, and its primary function is to design single-page applications.
# Components
- It is a key building block of Angular application.
- It is a reusable unit of an Angular application formed by a template and a class that controls a section of the screen.
- Components are used to divide a huge application into smaller, more manageable, and self-contained components. They communicate with one another via inputs, outputs, and services, resulting in a more modular and easy-to-maintain application.
- Angular components are reusable and can be layered inside other components, allowing developers to create sophisticated user interfaces by mixing smaller, simpler components
 #### Parts of an Angular Component
 - **Component Decorator:**
 - **Selector** - The selector is a string that defines the name of the component as it is used in templates.
 - **Template:** The template is a string or a reference to an external file that defines the HTML structure of the component.
 - **Styles:** The styles are a string or a reference to an external file that defines the CSS styles for the component.
 - **Class:** The class is a JavaScript class that defines the properties and methods of the component.
 - **Input properties:** Input properties are properties that are passed from a parent component to a child component. They are defined using the ‘@Input’ decorator and can be used to bind data from the parent component to the child component.
 - **Output properties:** Output properties are properties that are emitted from a child component to a parent component. They are defined using the ‘@Output’ decorator and can be used to notify the parent component of changes in the child component.
 - **Lifecycle hooks:** Lifecycle hooks are methods that are called at specific points during the creation, update, and destruction of a component. They provide a hook into the lifecycle of a component and allow you to perform custom logic at specific times.
 #### Angular Component Lifecycle Events
 - NgOnChanges
 - ngOnInit
 - ngDoCheck
 - ngAfterContentInit
 - ngAfterContentChecked
 - ngAfterViewChecked
 - ngOnDestroy
  #### Angular Styles in component
  - **Inline styles** You can define styles directly in the component’s template using the style attribute. This is the simplest way to add styles to a component, but it can be less maintainable for larger projects.
  - **Component-level styles**  You can define styles for a component in its own ‘.css’ file. These styles will only apply to the component and its child components.
  - **Global styles:** You can define styles in a global ‘.css’ file that will be applied to the entire application
  - **Sass/SCSS styles** -Angular supports Sass/SCSS styles, which provide additional features such as variables, functions, and mixins.
- You can control the scope of the styles applied to a component using the encapsulation property of the component.
- by default, Angular uses “emulated” encapsulation, which means that the component’s styles are scoped to the component and its child components, but are not isolated from the rest of the application.
- To change the encapsulation, you can set the encapsulation property in the component’s metadata to either ‘ViewEncapsulation.None’ or ‘ViewEncapsulation.ShadowDom’. If you set it to ‘ViewEncapsulation.None’, of the component’s styles, will be global and affect the entire application. If you set it to ‘ViewEncapsulation.ShadowDom’, the component’s styles will be scoped to the component and its child components, and will not affect the rest of the application.
  #### How to Implement an Angular Component?
  - **Define the component class**
  - **Define the template**
  - **Define the class**
  - **Register the component**
  - 