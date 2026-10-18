# CSS Roadmap: From Zero to Beautiful, Responsive Pages

This roadmap takes you from zero to designing beautiful, responsive web pages in 18 sessions (3 weeks, about 57 hours). CSS is the language that controls how a page looks: colours, fonts, spacing, layout and animation. It stands alone: a short HTML primer below gives you everything you need, so you do not have to do the HTML roadmap first (though doing it makes day 1 easier). By the end you can turn any design into a page that works on phones and laptops, and you will have built a portfolio page with dark mode.

## Start here

**Setup (30 minutes, once):** install VS Code and the Live Server extension. Use Chrome or Edge and learn to open DevTools with F12; the Elements and Styles panels are your best teacher. Make a folder css-roadmap with day01, day02 and so on, each holding index.html and style.css.

**HTML primer (10 minutes).** HTML is the content; CSS styles it. You only need this to start:

\<!DOCTYPE html\>  
\<html\>  
\<head\>  
\<title\>My page\</title\>  
\<link rel="stylesheet" href="style.css"\>  
\</head\>  
\<body\>  
\<h1\>Hello\</h1\>  
\<p class="intro"\>My first styled page.\</p\>  
\</body\>  
\</html\>

A tag like \<p\> makes a paragraph and class="intro" gives it a name that CSS can target. Save this as index.html, add an empty style.css beside it, and you are ready.

**How one session works (about 3 hours):**

| Minutes | Step     | What you do                                                             |
|---------|----------|-------------------------------------------------------------------------|
| 10      | Start    | Re-write from memory one rule you learned last session.                 |
| 40      | Learn    | Read the listed source and try every example live in DevTools.          |
| 90      | Build    | Style the day's page without copying.                                   |
| 30      | Break it | Change one value wildly (margin: 500px) and explain what moved and why. |
| 10      | Save     | Journal: 3 lines on what worked and what confused you.                  |

The 6th session each week is a 4-hour project and review. A session is done when the page looks right at both phone width and laptop width and you can explain every rule.

## Week 1 (days 1-6): selectors, the box model, colour and text

| Day | Learn                                                                                                                                                                                      | Build                                                                              | Done when                                                |
|-----|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------------------------------------|
| 1   | What CSS is. Rule anatomy: selector, property, value. Three ways to add CSS (inline, \<style\>, external file). Element selectors.                                                         | Style a plain page: background, text colour, font size.                            | Your rules live in style.css, not inline.                |
| 2   | Classes and IDs, grouping selectors, descendant and child selectors, pseudo-classes (:hover, :focus, :first-child).                                                                        | A link list that changes colour on hover.                                          | You can say why a class beats an ID for styling.         |
| 3   | The cascade: inheritance, specificity, rule order, !important (and why to avoid it).                                                                                                       | Fix a page where two rules fight, using DevTools to find the winner.               | You can predict which rule wins before you look.         |
| 4   | The box model: content, padding, border, margin, box-sizing: border-box, margin collapse, units (px, %, rem, em, vw).                                                                      | A card component with spacing and a border.                                        | Every gap on the card is something you set deliberately. |
| 5   | Colour and backgrounds: named, hex, rgb(), hsl(), opacity, gradients, background images, border-radius, box-shadow. Fonts: font-family, Google Fonts, weight, line-height, letter-spacing. | A hero banner with a gradient, a web font and readable text.                       | Text contrast passes the DevTools contrast check.        |
| 6   | **Project and review.**                                                                                                                                                                    | Style the HTML-primer page into a landing page: header, hero, three cards, footer. | It looks intentional, not default. Commit it.            |

**Break it (daily):** set \* { margin: 0 } and watch the page change, set width: 100% plus padding without border-box, make two classes clash.

## Week 2 (days 7-12): layout with Flexbox and Grid

| Day | Learn                                                                                                             | Build                                                                   | Done when                                                       |
|-----|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|-----------------------------------------------------------------|
| 7   | display: block, inline, inline-block, none. Normal document flow. overflow, min- and max-width.                   | A centred 800px-wide article column.                                    | It stays centred at any window width.                           |
| 8   | Positioning: static, relative, absolute, fixed, sticky, z-index.                                                  | A sticky header and a badge placed in a card corner.                    | You can explain what absolute is positioned against.            |
| 9   | Flexbox part 1: display: flex, flex-direction, justify-content, align-items, gap.                                 | A navigation bar with logo left and links right.                        | Items stay aligned when you add a link.                         |
| 10  | Flexbox part 2: flex-wrap, flex: 1, flex-grow/shrink/basis, align-self, order.                                    | A row of pricing cards that wrap on small screens.                      | Cards share width evenly and wrap, no fixed pixel widths.       |
| 11  | Grid: display: grid, grid-template-columns, fr, repeat(), minmax(), gap, grid-area. When to pick Grid vs Flexbox. | A photo gallery and a full page layout (header, sidebar, main, footer). | You can say in one sentence why each part uses Grid or Flexbox. |
| 12  | **Project and review.** Play Flexbox Froggy and Grid Garden to the end, then build.                               | Recreate a real site's layout (a blog home page) from a screenshot.     | It is within a few pixels of the screenshot. Commit it.         |

**Break it (daily):** delete display: flex from a parent and see what falls apart; give a grid item more columns than the grid has.

## Week 3 (days 13-18): responsive design, motion and polish

| Day | Learn                                                                                                                                                                                       | Build                                                          | Done when                                                                              |
|-----|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| 13  | Responsive basics: the viewport meta tag, mobile-first thinking, fluid images (max-width: 100%), media queries (@media (min-width: ...)).                                                   | Make last week's landing page work at 360px, 768px and 1280px. | No horizontal scrolling at any width.                                                  |
| 14  | Modern units and sizing: clamp(), min(), max(), aspect-ratio, object-fit, rem typography scales.                                                                                            | A fluid heading that scales smoothly with the screen.          | No media query needed for the heading size.                                            |
| 15  | CSS variables (--brand-colour, var()), organising a stylesheet, naming (BEM basics), a CSS reset.                                                                                           | Move all colours and spacing of your page into variables.      | Changing one variable restyles the whole page.                                         |
| 16  | Transitions and transforms: transition, transform (translate, scale, rotate), hover effects. @keyframes animations, animation. Respect prefers-reduced-motion.                              | A button with a smooth hover and a loading spinner.            | Animations are smooth and stop if reduced motion is set.                               |
| 17  | Dark mode with prefers-color-scheme and variables. Pseudo-elements (::before, ::after), :is(), :has(), :root. A short look at Sass and Tailwind: what they are and when you will want them. | Add a working dark mode to your page.                          | It follows your system setting.                                                        |
| 18  | **Capstone.** Build a responsive portfolio page: header with nav, hero, projects grid, contact section, dark mode, one animation. Publish free on GitHub Pages or Netlify.                  | Your portfolio, live.                                          | Lighthouse scores 90+ for Accessibility, and it looks right on your phone. Tag css-v1. |

**Break it (daily):** open DevTools device mode and drag the width from 320px to 1920px. Fix everything that looks wrong.

## Checkpoints

Do not move on until you pass the gate. If you fail, redo the weak day, not the whole week.

**Checkpoint 1 (day 6).** In 45 minutes, from a plain HTML page and no copy-paste, style a card with padding, border, radius, shadow, a web font and a hover effect. Pass: you can explain every number in the box model of that card.

**Checkpoint 2 (day 12).** Without notes, build a nav bar with Flexbox and a 3-column gallery with Grid. Pass: both work, and you can explain when you would choose each.

**Checkpoint 3 (day 18).** Build a responsive page from a screenshot in 2 hours. Pass: it matches at 360px and 1280px, uses variables, and has dark mode.

**What you can do now.** Make any page look professional on any screen. What is missing is behaviour: menus that open, forms that submit (JavaScript roadmap).

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource                                                                                                              | Use it for                                              | Cost |
|-----------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|------|
| [MDN: CSS first steps and layout](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics) | The main learning path and property reference.          | Free |
| [web.dev Learn CSS](https://web.dev/learn/css)                                                                        | Clear lessons on the cascade, box model, Flexbox, Grid. | Free |
| [Flexbox Froggy](https://flexboxfroggy.com/) and [Grid Garden](https://cssgridgarden.com/)                            | Games that teach layout.                                | Free |
| [CSS-Tricks guides to Flexbox and Grid](https://css-tricks.com/)                                                      | Visual cheat sheets for later.                          | Free |
| [Google Fonts](https://fonts.google.com/)                                                                             | Web fonts for your pages.                               | Free |
| [Coolors](https://coolors.co/)                                                                                        | Picking a colour palette.                               | Free |
| Chrome DevTools                                                                                                       | Live editing of any site's CSS.                         | Free |
