# Advanced React: Design System, Design Patterns, Performance

**in-complete**

## Design Patterns: Layout Components

### What are design patterns?

- _effective_ solutions for common challenges
    - some approaches can lead to brittle code, decreased performance and reduced maintainability (aka anti-patterns)

### Introduction

#### Layout Components

- focus on organizing other components with in a web page

#### Layout Component Patterns

![layout component patterns](layout_component_patterns.jpg)

#### The Concept of Layout Components

- typically when we develop a component, we tend to involve both HTML structure (ex. div elements) and associated styles
  with in the component
- layout components, we adopt a different approach

```HTML

<Navbar style="{...}">
    <h3>Components code...</h3>
</Navbar>
```

```HTML

<LayoutComponent style="{...}">
    <SideNavbar/>
</LayoutComponent>
```

- separate the actual layout styles into a dedicated component and only insert the specific component
- this separation allows us to decouple the components logic from its specific placement on teh page granting us greater
  flexibility in the future
- main advantage
    - the core content components of hte page should be unaware and unconcerned about their precise location with in the
      page structure

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
