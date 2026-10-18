# HTML Roadmap: From Zero to Your First Real Web Pages

This roadmap takes you from zero to building real, well-structured web pages in 18 sessions (3 weeks, about 57 hours). It assumes you know nothing: not what a tag is, not how a browser works. It stands alone, so you can start it on any day. HTML is the skeleton of every website; CSS and JavaScript (separate roadmaps) are built on top of it. By the end you can write a multi-page personal site with a navigation menu, images, a table and a form, and publish it for free.

## Start here

**Setup (30 minutes, once):**

1.  Install **VS Code** from code.visualstudio.com.

2.  In VS Code, install the extension **Live Server**. It refreshes the browser every time you save.

3.  Use **Chrome or Edge**. Press F12 to open Developer Tools; you will use the Elements tab every day.

4.  Create a folder html-roadmap with one folder per day inside it: day01, day02 and so on. Each holds an index.html.

5.  Optional: make a free GitHub account so you can publish your site on day 12.

**How one session works (about 3 hours):**

| Minutes | Step     | What you do                                                                    |
|---------|----------|--------------------------------------------------------------------------------|
| 10      | Start    | Re-type from memory one thing you learned last session.                        |
| 40      | Learn    | Read the listed source, typing every example yourself.                         |
| 90      | Build    | Make the day's page without copying.                                           |
| 30      | Break it | Delete a closing tag or misspell an attribute and watch what the browser does. |
| 10      | Save     | Write 3 lines in a journal: what worked, what confused you.                    |

A session is done only when the page opens in the browser and you can explain every line of it. The 6th session each week is a 4-hour project and review.

## Week 1 (days 1-6): pages, text, links and images

| Day | Learn                                                                                                                                     | Build                                                                     | Done when                                                      |
|-----|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|----------------------------------------------------------------|
| 1   | How the web works: browser, server, URL, request. What HTML is. The skeleton: \<!DOCTYPE html\>, \<html\>, \<head\>, \<body\>, \<title\>. | A page that says your name and one sentence about you.                    | It opens via Live Server and the tab shows your title.         |
| 2   | Text: headings \<h1\>-\<h6\>, \<p\>, \<br\>, \<strong\>, \<em\>, comments. Tags, attributes and nesting.                                  | A one-page biography with a heading hierarchy.                            | Headings go in order, no skipped levels.                       |
| 3   | Links: \<a href\>, absolute vs relative paths, target, anchors (#id) that jump within a page, mailto:.                                    | A 3-page mini site (home, about, hobbies) linked together.                | Every link works, and you can go back to home from every page. |
| 4   | Images: \<img src alt\>, file formats (JPG, PNG, SVG, WebP), width/height, folders for assets.                                            | Add a photo and a logo to your site with proper alt text.                 | Images still load if you move the project folder.              |
| 5   | Lists: \<ul\>, \<ol\>, \<li\>, nested lists, description lists \<dl\>. Using lists for menus.                                             | A favourite-recipe or study-plan page using all three list types.         | You can explain when to use \<ul\> vs \<ol\>.                  |
| 6   | **Project and review.** Validate with validator.w3.org and fix every error.                                                               | A "digital CV" page: heading, photo, skills list, links to your accounts. | Zero validator errors. Commit the folder to Git or zip it.     |

**Break it (daily):** remove a closing tag, nest a \<p\> inside a \<p\>, use a wrong file path. Look at the Elements panel to see how the browser repairs your mistakes.

## Week 2 (days 7-12): structure, tables, forms and publishing

| Day | Learn                                                                                                                                                                                                  | Build                                                                                   | Done when                                                                       |
|-----|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| 7   | Semantic layout: \<header\>, \<nav\>, \<main\>, \<section\>, \<article\>, \<aside\>, \<footer\>. Why it beats \<div\> everywhere.                                                                      | Rebuild your digital CV with semantic tags only.                                        | No \<div\> used where a semantic tag fits.                                      |
| 8   | Tables: \<table\>, \<tr\>, \<th\>, \<td\>, \<thead\>, \<tbody\>, colspan, rowspan, \<caption\>. When NOT to use a table.                                                                               | A weekly timetable for your college classes.                                            | Merged cells line up and headers are \<th\>.                                    |
| 9   | Forms part 1: \<form\>, \<input\> types (text, email, password, number, date), \<label for\>, \<button\>.                                                                                              | A sign-up form with 5 fields and labels.                                                | Clicking a label focuses its input.                                             |
| 10  | Forms part 2: \<select\>, \<textarea\>, radio and checkbox groups, \<fieldset\>, required, pattern, placeholder.                                                                                       | A feedback form with built-in validation.                                               | The browser blocks an empty required field.                                     |
| 11  | Media and embeds: \<audio\>, \<video\>, \<iframe\>, \<figure\>. Accessibility basics: alt, aria-label, heading order, keyboard tab order. SEO basics: \<meta\> description, viewport, Open Graph tags. | Add a video and meta tags to your site. Run Lighthouse (in DevTools) for Accessibility. | Lighthouse accessibility score is 90 or more.                                   |
| 12  | **Capstone.** Plan, build and publish a 4-page personal site: home, about, projects, contact form. Publish free on GitHub Pages or Netlify.                                                            | Your own site with a public link.                                                       | The link opens on your phone, and the validator shows zero errors. Tag html-v1. |

Forms in this roadmap only lay out the page; they do not send data anywhere yet. Making them work needs JavaScript or a server, which the JavaScript roadmap covers.

## Week 3 (days 13-18): going deeper, accessible, findable and fast

This week turns "I can write pages" into "I can write pages a professional would ship". You can stop after day 12 and come back; the later roadmaps do not depend on this week.

| Day | Learn                                                                                                                                                                                                                     | Build                                                               | Done when                                                                      |
|-----|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------|
| 13  | Advanced forms: more input types (tel, url, range, color, file), autocomplete, \<datalist\>, \<output\>, \<progress\>, \<meter\>, min/max/step, validation attributes.                                                    | A booking form with date, time, number of guests and a file upload. | Every field has a label and a sensible type.                                   |
| 14  | Accessibility in depth: landmarks, skip links, focus order and tabindex, ARIA roles only when HTML cannot do it, aria-describedby for error text, writing good alt text, accessible tables.                               | Fix a deliberately broken page that has 10 accessibility faults.    | You can use the whole page with the keyboard only.                             |
| 15  | Test with a screen reader: install the free **NVDA** (Windows) or use VoiceOver (Mac), and listen to your own site. Colour contrast rules (WCAG AA).                                                                      | Run NVDA on your day 12 site and write down 5 things to fix.        | You fixed all 5 and re-tested.                                                 |
| 16  | SEO and performance: \<title\> and meta description, canonical, Open Graph and Twitter cards, JSON-LD structured data (intro), robots.txt, sitemap.xml, loading="lazy", srcset and \<picture\>, image compression.        | Add all of these to your personal site.                             | Lighthouse SEO and Best Practices both 90 or more.                             |
| 17  | **Project 1:** a 5-page business site (home, services, pricing table, about, contact form) for a made-up cafe or tuition centre.                                                                                          | The site, with shared header and footer copied across pages.        | Validates with zero errors, and every page has a unique title and description. |
| 18  | **Project 2 and Checkpoint 3:** a blog layout. An index page listing articles, and an article page with \<article\>, \<time\>, \<figure\>, \<blockquote\>, \<code\>, \<details\> and a \<dialog\>. Publish both projects. | A blog with 3 articles.                                             | Both sites are public. Tag html-v2.                                            |

**Break it (daily):** unplug your mouse and use only Tab and Enter; zoom the browser to 200 percent; turn images off and see whether the page still makes sense.

## Checkpoints

Do not move on until you pass the gate. If you fail, redo the weak day, not the whole week.

**Checkpoint 1 (day 6).** With no notes and no copy-paste, in 45 minutes build a 2-page site: a heading, two paragraphs, a list, an image with alt, and links between the pages. Pass: it validates with zero errors.

**Checkpoint 2 (day 12).** Without looking, write from memory: a semantic page skeleton, a table with a merged cell, and a form with a label, a required email field and a submit button. Then explain out loud what alt, href and \<label for\> do. Pass: you do all of it without searching.

**Checkpoint 3 (day 18).** Without looking, build a semantic article page with a figure, a form with proper labels and a \<meta\> description, then check it with Lighthouse and with the keyboard only. Pass: Lighthouse Accessibility and SEO are both 90 or more, and you can reach every control with Tab.

**What you can do now.** Build any static page. What is missing is how it looks (CSS roadmap) and how it behaves (JavaScript roadmap).

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource                                                                                                      | Use it for                                              | Cost |
|---------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|------|
| [MDN Web Docs: HTML](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content) | The main learning path and the reference for every tag. | Free |
| [web.dev Learn HTML](https://web.dev/learn/html)                                                              | Short lessons on semantics, forms and accessibility.    | Free |
| [freeCodeCamp Responsive Web Design](https://www.freecodecamp.org/learn)                                      | Guided practice with in-browser exercises.              | Free |
| [W3C Markup Validator](https://validator.w3.org/)                                                             | Checking your pages for errors.                         | Free |
| [HTML Dog](https://htmldog.com/)                                                                              | Plain short tutorials as a second explanation.          | Free |
| Chrome DevTools and Lighthouse                                                                                | Inspecting pages and checking accessibility and SEO.    | Free |
