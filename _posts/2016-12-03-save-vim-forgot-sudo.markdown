---
layout: post
title: "Save a file even when you forget sudo"
subtitle: ""
tags: vim sudo tips
---

If you forget to open a file in vim a sudo/root, you can simply do in vim (sudo needs to be installed):

    ```bash
    :w !sudo tee % 
    ```
