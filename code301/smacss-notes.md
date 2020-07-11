# [SMACSS Official Documentation](http://smacss.com/)

## Base
- Base rules are the defaults. 
- They are almost exclusively single element selectors but it could include attribute selectors, pseudo-class selectors, child selectors or sibling selectors. 
- Essentially, a base style says that wherever this element is on the page, it should look like this.
- A Base rule is applied to an ***element*** using an ***element selector***, a ***descendent selector***, or a ***child selector***, along with any ***pseudo-classes***.
- It DOES NOT include any class or ID selectors. 
- It is defining the default styling for how that element should look in all occurrences on the page.
- Base styles include setting heading sizes, default link styles, default font styles, and body backgrounds.
- I highly recommended that you specify a body background. 

## Layout
- Layout rules divide the page into sections. 
- Layouts hold one or more modules together.
- The minor components—such as a callout, or login form, or a navigation item—sit within the scope of major components such as a header or footer. 
  - The minor components are Modules.
  - The major components are referred to as Layout styles.
  - Layout styles can also be divided into major and minor styles based on reuse. 
  - Major layout styles such as ***header and footer*** are traditionally styled using ID selectors but take the time to think about the elements that are common across all components of the page and use class selectors where appropriate.
- Some sites may have a need for a more generalized layout framework (for example, 960.gs). These minor Layout styles will use class names instead of IDs so that the styles can be used multiple times on the page. 
- Generally, a Layout style only has a single selector: a single ID or class name. 
  - However, there are times when a Layout needs to respond to different factors. 
    - For example, you may have different layouts based on user preference. 
    - This layout preference would still be declared as a Layout style and used in combination with other Layout styles.

## Module
- Modules are the reusable, modular parts of our design. 
- They are the callouts, the sidebar sections, the product lists and so on.

## State
- State rules are ways to describe how our modules or layouts will look when in a particular state. 
- Is it hidden or expanded? Is it active or inactive? 
- They are about describing how a module or layout looks on screens that are smaller or bigger. 
- They are also about describing how a module might look in different views like the home page or the inside page.

## Theme
- Theme rules are similar to state rules in that they describe how modules or layouts might look. 
- Most sites don’t require a layer of theming but it is good to be aware of it.