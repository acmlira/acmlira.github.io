---
layout: post
author: Allan César
tags: ["TotalCross"]
---
Hey guys let's take back a few months ago when `totalcross` became an open source project.
>This text was written to be a `TotalCross/totalcross` issue a few months ago.

![image](https://media1.tenor.com/images/cc0861c13322fc1f71736128811d5a14/tenor.gif?itemid=4584294)


# Purpose 

As a product developer I saw our movement together very similar to the movement that Linus Torvalds made in the early years of the Kernel, we want people to see what we've been up to:

> And what happened is ... the project grows and becomes something you want to show off to people. Really, this is more of a, "Wow, look at what I did!" And trust me -- it was not that great back then. I made it publicly available, and it wasn't even open source at that point. At that point it was source that was open, but there was no intention behind using the kind of open-source methodology that we think of today to improve it. It was more like, "Look, I've been working on this for half a year, I'd love to have comments.
>
> Linus Torvalds in [The Mind Behind Linux](https://www.ted.com/talks/linus_torvalds_the_mind_behind_linux/transcript?language=pt-br).

But that's not all, we want people to contribute to what we have done:

> No matter how many smart people we hire inside the company, there’s always smarter people on the outside. We find it is worth it to us to open source and share our code with the outside world in exchange for getting some great advice from people on the outside who have expertise and are willing to share back with us.
>
> Jared Smith (Open Source Community Manager, Capital One) in [Starting an Open Source Project](https://www.linuxfoundation.org/resources/open-source-guides/starting-open-source-project/#1).

And these were the same reasons for the emergence of several software and foundations that today regulate and assist the community of open source projects. Among them the GNU project, the Linux Foundation and the Open Source Initiative as main exponents. They help to establish the basic requirements for an open source project, as example, for GNU:

> ### The four essential freedoms
> A program is free software if the program's users have the four essential freedoms:
> - The freedom to run the program as you wish, for any purpose (freedom 0).
> - The freedom to study how the program works, and change it so it does your computing as you wish (freedom 1). Access to the source code is a precondition for this.
> - The freedom to redistribute copies so you can help others (freedom 2).
> - The freedom to distribute copies of your modified versions to others (freedom 3). By doing this you can give the whole community a chance to benefit from your changes. Access to the source code is a precondition for this.
>
> Overview of the GNU System in [gnu.org](https://www.gnu.org/gnu/gnu-history.en.html)

For Open Source Initiative:

> ### The Criteria
> To comply with the Open Standards Requirement, an "open standard" must satisfy the following criteria. If an "open standard" does not meet these criteria, it will be discriminating against open source developers.
>
> 1. No Intentional Secrets: The standard MUST NOT withhold any detail necessary for interoperable implementation. As flaws are inevitable, the standard MUST define a process for fixing flaws identified during implementation and interoperability testing and to incorporate said changes into a revised version or superseding version of the standard to be released under terms that do not violate the OSR.
> 2. Availability: The standard MUST be freely and publicly available (e.g., from a stable web site) under royalty-free terms at reasonable and non-discriminatory cost.
> 3. Patents: All patents essential to implementation of the standard MUST:
>     1. be licensed under royalty-free terms for unrestricted use, or
>     2. be covered by a promise of non-assertion when practiced by open source software
> 4. No Agreements: There MUST NOT be any requirement for execution of a license agreement, NDA, grant, click-through, or any other form of paperwork to deploy conforming implementations of the standard.
> 5. No OSR-Incompatible Dependencies: Implementation of the standard MUST NOT require any other technology that fails to meet the criteria of this Requirement.
>
> Open Standards Requirement for Software in [opensource.org](https://opensource.org/osr)

With that in mind and our experience so far, we may be doing something wrong.

![image](https://64.media.tumblr.com/a6f123f76173681b72a9c44a61d11657/tumblr_mv2btgBQJ11sfc6p7o1_500.gif)

# Current workflow

First let's understand a little bit of our development in this flow:

![diagram](https://user-images.githubusercontent.com/30937401/96493653-9c433800-121b-11eb-901f-a5a65ef4f820.png)

We can see that our process, today, involves little the user and we see a clear division of roles (contributor != user). Some considerations need to be made, from top to bottom:
1. The first level depicts the quality of our repository, it is something that we have been working on for some time and we have made many changes about it. It is not the main point;
2. The second one it's the most complicated. I've been part of the team for almost 2 years and I'm not sure how the SDK build and launch procedure works. By SDK I mean the artifacts that we deliver to users and not what is easily confused with Java API:
    1. Not all are generated in the same way or during the same build process;
    2. They need specific tools that are not clearly described;
    3. The iOS build is **completely private** since it is necessary to have access to TotalCross developer accounts;
    4. There is no description or automation that allows the construction of the final SDK package. In other words, there is no way for anyone to build their own application from sources.
3. At the third level, we distribute binaries and we have no tests or automations at the present time that prevent corruption or mistakes;
4. In the following (4th level), provisioning is manual and the resource servers are private, not using public tools like GitHub itself;
5. 5th level without problems;
6. The last level (6th) the most complicated of all is that we are installing fragile binaries on **embedded systems**. This type of non-deterministic system is extremely sensitive to this stuff.

Knowing a little from the developer's point of view I think it is already clear what the problems are.

![image](https://mrwgifs.com/wp-content/uploads/2013/06/Marty-McFly-Confused-In-Back-To-The-Future-Gif.gif)

# The main issue

In view of the arguments presented in the previous section and the summary made in the previous sections, we can conclude that:

### We are not yet completely open source

It was very hard to write this 😢 

![image](https://64.media.tumblr.com/fca1d359f09ff083c50adda63500a1fa/tumblr_p9ih6jOCfg1x6m6njo1_400.gifv)

And because I said that let's get to the facts here:
1. You can't build TotalCross iOS stuff as 'anyone';
2. You can't create TotalCross SDK .zip file only with sources;
3. Secrets in SDK packaging (it is not clear how all files are generated);
4. We are delivering black boxes to the end user (embedded systems);
5. We have separate roles between contributors and users, but everyone should be 'anyone'.

Not only of problems if the human being lives, we are looking for some solution!

# My sugestion

I want to start the discussion with this issue and I leave here the motto that I think we should follow:

> ## Everyone like anyone

I hope that the largest number of contributors and stakeholders will contribute, agree or disagree with this issue. I feel that we need to work on this to avoid new version delays and issues like these: #165 and #167.

![image](https://31.media.tumblr.com/faeb7b11831fa6bde0ee7d493c33d882/tumblr_mrrx9p63OI1svkxo8o1_500.gif)
