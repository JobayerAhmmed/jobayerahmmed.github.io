---
layout: post
title:  "VS Code & Extensions"
permalink: /vscode-extensions/
---

Visual Studio Code is a popular and easy to use code editor that many developers use. As a developer, you should know your tools properly. Writing code in VS Code can be more fun if we can use appropriate extensions. Today, I will talk about some popular extensions that can make our developer life easier. I normally work in Angular and Java, so I will focus on these two stacks along with git.

<a href="https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens" target="_blank">**GitLens**</a>  
GitLens provides many features, but I use this extension mainly for one interesting feature - `blame`. If you put the cursor in a line, GitLens will show the commit and author who last modified the line of the file.

<a href="https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig" target="_blank">**EditorConfig**</a>  
This plugin attempts to override user/workspace settings with settings found in `.editorconfig` files. If you want your file should be indented by 4 spaces instead of 2 spaces, you can specify that in the `.editorconfig` file for specific languages. For example, the `.ts` file normally indent by 2 spaces in the VS Code. But if you want indentation by 4 space, you need to tell that in the `.editorconfig` file.

<a href="https://marketplace.visualstudio.com/items?itemName=jbockle.jbockle-format-files" target="_blank">**Format Files**</a>  
Sometimes we write code and format the files by hand which costs our time and energy. We can reconcile this problem by using the `Format Files` extension. After finished writing your code, you right-click anywhere in the file, select `Format Document`, and `Format Files` will do the work. This extension has a dependency. To let `Format Files` do its work, you need to add one or more formatters, i.e. 
<a href="https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig" target="_blank">EditorConfig</a>.

<a href="https://marketplace.visualstudio.com/items?itemName=redhat.java" target="_blank">**Language Support for Java(TM) by Red Hat**</a>  
To format Java files by the `Format Files` extension, `Language Support for Java(TM) by Red Hat` needs to be added in VS Code. Besides, this extension provides many other features like IntelliSense, code navigation, etc.

<a href="https://marketplace.visualstudio.com/items?itemName=michelemelluso.code-beautifier" target="_blank">**Beautify css/sass/scss/less**</a>  
To format and beautify CSS files using the `Format Files` extension, you need to add this extension in VS Code.


