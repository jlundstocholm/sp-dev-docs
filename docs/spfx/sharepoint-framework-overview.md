---
title: Overview of the SharePoint Framework (SPFx)
description: SPFx is a page and web part model that provides full support for client-side SharePoint development, easy integration with SharePoint data, and support for open source tooling.
ms.date: 01/08/2018
ms.prod: sharepoint
---


# Overview of the SharePoint Framework

The SharePoint Framework (SPFx) is a page and web part model that provides full support for client-side SharePoint development, easy integration with SharePoint data, and support for open source tooling. With the SharePoint Framework, you can use modern web technologies and tools in your preferred development environment to build productive experiences and apps that are responsive and mobile-ready from day one. The SharePoint Framework works for SharePoint Online and also for on-premises (SharePoint 2016 Feature Pack 2 and SharePoint 2019).
 
Key features of the SharePoint Framework include the following:

* It runs in the context of the current user and connection in the browser. There are no iFrames for the customization (JavaScript is embedded directly to the page).
* The controls are rendered in the normal page DOM.
* The controls are responsive and accessible by nature.
* It enables the developer to access the lifecycle in addition to **render**, **load**, **serialize** and **deserialize**, **configuration changes**, and more.
* It is framework-agnostic. You can use any JavaScript framework that you like: React, Handlebars, Knockout, Angular, and more.
* The toolchain is based on common open source client development tools such as npm, TypeScript, Yeoman, webpack, and gulp.
* Performance is reliable.
* End users can use SPFx client-side solutions that are approved by the tenant administrators (or their delegates) on all sites, including self-service team, group, or personal sites. 
* SPFx web parts can be added to both classic and modern pages.
 
The runtime model improves on the Script Editor web part. It includes a robust client API, an HttpClient object that handles authentication to SharePoint and Office 365, contextual information, easy property definition and configuration, and more. 

If you work primarily with C#, you want to learn more about client-side JavaScript development. Most of your existing JavaScript knowledge related to SharePoint, however, is completely transferable, as the data models have not changed, and you’ll use the same [REST services](https://msdn.microsoft.com/en-us/library/office/jj860569.aspx) or [JavaScript Object Model (JSOM)](https://msdn.microsoft.com/en-us/library/office/jj193034.aspx), depending on your requirements. If you are a C# developer, TypeScript is a nice transition into the JavaScript world. The choice of IDE is up to you. Many developers like to use the cross-platform IDE Visual Studio Code. Many developers also use products like Sublime and ATOM. Use what works best for you.

## Why the SharePoint Framework?

SharePoint was launched as an on-premises product in 2001. Over time, a large developer community has extended and shaped it in many ways. For the most part, the developer community followed the same patterns and practices that the SharePoint product development team used, including web parts, SharePoint feature XML, and more. Many features were written in C#, compiled to DLLs, and deployed to on-premises farms.
 
That architecture worked well in environments with only one enterprise, but it didn’t scale to the cloud, where multiple tenants run side-by-side. As a result, we introduced two alternative models: client-side JavaScript injection, and SharePoint Add-ins. Both of these solutions have pros and cons. 

### JavaScript injection

One of the most popular web parts in SharePoint Online is the Script Editor. You can paste JavaScript into the Script Editor web part and have that JavaScript execute when the page renders. It’s simple and rudimentary, but effective. It runs in the same browser context as the page, and is in the same DOM, so it can interact with other controls on the page.  It is also relatively performant, and simple to use. 

There are a few downsides to this approach, however. First, while you can package your solution so that end users can drop the control onto the page, you can't easily provide configuration options. Also, the end user can edit the page and modify the script, which can break the web part. Another big problem is that the Script Editor web part is not marked as **"Safe For Scripting"**.  Most self-service site collections (my-sites, team sites, group sites) have a feature known as **"NoScript"** enabled. Technically, it is the removal of the Add/Customize Pages (ACP) permission in SharePoint. This means that the Script Editor web part will be blocked from executing on these sites.  

### SharePoint Add-in model

The current option for solutions that run in NoScript sites is the add-in/app-part model. This implementation creates an **iFrame** where the actual experience resides and executes. The advantage is that because it's external to the system and has no access to the current DOM/connection, it's easier for information workers to trust and deploy. End users can install add-ins on NoScript sites. 

There are some downsides to this approach as well. First, they run in an **iFrame**. iFrames are slower than the Script Editor web part, because it requires a new request to another page. The page has to go through authentication and authorization, make its own calls to get SharePoint data, load various JavaScript libraries, and more. A Script Editor web part might typically take, for example, 100 milliseconds to load and render, while an app part might take 2 seconds or more. Additionally, the **iFrame** boundary makes it more difficult to create responsive designs and inherit CSS and theming information. iFrames do have stronger security, which can be useful for you (your page is inaccessible by other controls on the page) and for the end user (the control has no access to their connection to Office 365).


### SharePoint Framework 

Historically, we created web parts as full trust C# assemblies that were installed on the cloud servers. However, current development models for the most part involve JavaScript running in a browser making REST API calls to the SharePoint and Office 365 back-end workloads. C# assemblies don’t work in this world. We needed a new development model. The SharePoint Framework is the next evolution in SharePoint development.

## What's next?

SharePoint Framework web parts and extensions have now reached General Availability (GA). We continue to provide updates and refinements over time based on your feedback and experiences. For any additional SharePoint Framework capabilities that are first launched in preview mode, you might experience occasional breaking changes around API names, flows, and more. Future updates to the SharePoint Framework will be backward-compatible so that your solutions continue to work.

## SharePoint Framework License

The SharePoint Framework components are licensed under this [Microsoft EULA](https://github.com/SharePoint/sp-dev-docs/blob/master/LICENSE.md).

## Questions?

If you have any questions, post them on [SharePoint StackExchange](https://sharepoint.stackexchange.com/). Tag your questions and comments with [#spfx](https://sharepoint.stackexchange.com/tags/spfx/), [#spfx-webparts](https://sharepoint.stackexchange.com/tags/spfx-webparts/), and [#spfx-tooling](https://sharepoint.stackexchange.com/tags/spfx-tooling/). 

You can also post issues, questions, or feedback about the docs or the SharePoint Framework in our [GitHub repo](https://github.com/SharePoint/sp-dev-docs/issues).

## See also

- [Overview of SharePoint client-side web parts](./web-parts/overview-client-side-web-parts.md)
- [Overview of SharePoint Framework Extensions](./extensions/overview-extensions.md)
- [SharePoint development](https://docs.microsoft.com/en-us/sharepoint/dev/)
- [SharePoint glossary](../general-development/sharepoint-glossary.md) 
