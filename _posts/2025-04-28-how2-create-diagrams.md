---
layout: post # Specifies which layout file to use (_layouts/post.html)
title:  "how2: create Post with Diagrams"
date:   2025-04-28 10:00:00 +0000 # Optional: specific time/timezone
categories: jekyll update # Optional: categories for organization
---

<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
<script>
  document.addEventListener("DOMContentLoaded", function() {
    mermaid.initialize({ startOnLoad: true });
  });
</script>

# My Post Content

Here's a diagram:

<div class="mermaid">
graph TD
    A[Start] --> B[Process]
    B --> C[End]
</div>
