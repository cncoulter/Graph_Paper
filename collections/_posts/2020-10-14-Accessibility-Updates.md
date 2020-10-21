---
# SPDX-FileCopyrightText: 2020 Cam N. Coulter <cam@cncoulter.com>
# SPDX-License-Identifier: CC-BY-SA-4.0
layout: post
published: true
title: "Accessibility Updates"
date: 2020-10-21 07:26
author: cam # This should be a person's code_name from your people collection
description: Graph Paper has got some accessibility improvements.
categories:
- Graph Paper
tags:
- Accessibility
image: pexels-pixabay-159746.jpg
comments: true
---

Over the summer, I've learned a lot more about web accessibility, and I realized that Graph Paper had some accessibility errors. So I conducted an accessibility audit on the project to the best of my abilities, [logged the issues I found on GitHub](https://github.com/cncoulter/Graph_Paper/issues?q=is%3Aissue+is%3Aclosed), and then went about remediating those issues. Here are the issues I found and the changes I made.

I [replaced a number of `div` elements with semantic sectioning elements](https://github.com/cncoulter/Graph_Paper/commit/ed1ec6a1339487501e6facffe785d2202b7484ad), such as `header`, `nav`, `main`, `section`, and `footer`.

I [updated the focus and hover styles for links](https://github.com/cncoulter/Graph_Paper/commit/03375858ca6a740b40478973180c26cd61ceaf70) so that they are more noticeable and more beautiful.

I [added "skip to main content" links](https://github.com/cncoulter/Graph_Paper/commit/7f4388e3d3b817f4bbeb5c261502a37af6f3bd59) on each page.

I fixed several validation errors that I didn't catch earlier.

I [fixed heading levels](https://github.com/cncoulter/Graph_Paper/commit/f5ebc4dff01c6c41f773acc27e89169fcd79ea3f) on a number of pages. For example, there was one page with multiple `h1` elements, and other pages where I skipped from an `h2` element to an `h4`. I updated these so that there is only one `h1` element per page, headings are used in a logical order, and Graph Paper doesn't skip heading levels. For those places where I wanted an `h2` element styled as an `h4`, I used Bootstrap's h4 class to achieve that styling without confusing the semantic heading levels.

I also changed text colors so that the color contrast between text and it's background is WCAG level AA conformant. By default, the color contrast between Bootstrap's `bg-light` variable and Bootstrap's `primary` variable (used for blue link text) is not WCAG AA conformant (a strange decision on Bootstrap's part, methinks), so [I updated the `primary` variable to a darker shade](https://github.com/cncoulter/Graph_Paper/commit/2a22a31cbc870db40cc57bf7dc97d411ca28a1d8) of blue that is conformant. Additionally, some of the colors used in our syntax highlighting stylesheet lacked sufficient contrast against the light gray background used for code blocks. While I can't claim that I updated the entire syntax highlighting stylesheet to make it WCAG AA conformant, but [I did update a few colors to darker shades](https://github.com/cncoulter/Graph_Paper/commit/99508217c5ab6266bf1dcca501d4eb2730255bb7) so that all the syntax highlighting actually in use on this website has WCAG-conformant color contrast.

If you notice any accessibility issues with Graph Paper, please let me know! You can <a href="https://github.com/cncoulter/Graph-Paper/issues">report accessibility issues</a> via GitHub or send a pull request.

If you're interested in learning more about web accessibility, here are a few resources that I recommend:

* [A11y Coffee](https://a11y.coffee/)
* [The A11y Project](https://www.a11yproject.com/)
* [Web AIM (Accessibility in Mind)](https://webaim.org/)
