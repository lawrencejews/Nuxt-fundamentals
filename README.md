# Nuxt 3 Fundamentals

### Set Up
Project start `npm run dev`

### Options API
The Options API is centered around the concept of a "component instance", which typically aligns better with a class-based mental model for users coming from OOP language backgrounds. Go with Options API if you are not using build tools, or plan to use Vue primarily in low-complexity scenarios, e.g. progressive enhancement.
#### NOTE - basic constructs
- Properties returned from data() become reactive state and will be exposed on `this`.
- Methods are functions that mutate state and trigger updates. They can be bound as event listeners in templates.
- Lifecycle hooks are called at different stages of a component's lifecycle.

### Composition API
The Composition API is centered around declaring reactive state variables directly in a function scope and composing state from multiple functions together to handle complexity. Go with Composition API + Single-File Components if you plan to build full applications with Vue.
#### NOTE - basic constructs
- Reactive state.
- Functions that mutate state and trigger updates.
- Lifecycle hooks.



<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.