---
layout: post
title: "Goodbye (and good riddance) Bookmarks"
excerpt_separator: <!--more-->
---

I hop browsers. I admit it, readily. I find no shame in it; I'm not "flip-flopping"; I'm looking for the best tool for the job, and when it comes to web browsers, they are still rapidly evolving. This habit, though, is not without drawbacks.

<!--more-->

Even the definition of what a browser should do is evolving; 20 years ago, your browser was either part of a comprehensive application for all things "online", or itself a complete suite of online tools... think _[AOL](https://discover.aol.com/products-and-services/aol-desktop-for-windows)_ or [Netscape Communicator](https://www.youtube.com/watch?v=RyGu0LE4cxM) (which included a browser, mail client, news reader, a WYSIWYG HTML editor...). Today, the browser is more of an application framework (think [Electron](https://electronjs.org/) - which is based on [chromium](https://www.chromium.org/Home)), and increasingly a tool for managing personal data (e.g. "privacy"). Both [Mozilla](https://developer.mozilla.org/en-US/docs/Archive/B2G_OS) and [Google](https://www.google.com/chromebook/) have built operating systems based, primarily, on hosting a web browser. Features like Chrome's [Incognito](https://support.google.com/chrome/answer/95464?co=GENIE.Platform%3DDesktop&hl=en) mode, and browsers like [Brave](https://brave.com/), [Iridium](https://iridiumbrowser.de/), and [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en) focus on limiting how you are tracked online, and how your information is shared (or preferably not shared). [Opera](https://www.opera.com/computer/features/free-vpn) and [Epic](https://www.epicbrowser.com/our-key-features.html) boast built-in support for VPNs. As we've moved from 'gateway' to 'platform', superfluous features have been stripped out, and browser development has turned towards performance, consistency, and stability: Google's [V8](https://developers.google.com/v8/) Javascript engine is at the core of Electron and [Node.js](https://nodejs.org/api/v8.html#v8_v8), and the [GNOME Desktop](https://wiki.gnome.org/JavaScript) is built on Mozilla's [Spidermonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey); Firefox's [Quantum](https://blog.mozilla.org/blog/2017/11/14/introducing-firefox-quantum/) release boasted a massive rewrite of the rendering engine into new multi-threaded model. The downside is, that all the browsers move at their own speed, so it's impossible to say, after any release, that there is a Lord of the Browsers, one browser to rule them all. Some releases are huge steps forward, some are shocking steps backwards.

The problem is, browsers are still clinging to some 'gateway' features, some unhealthy attachment to bygones that haven't been clearly replaced by better, independent products, or so I thought. Bookmarks, password managers, start page content... _blech_. All these things are still carried around in every browser, and no browser handles them well, _because they're not the core function_. They're afterthoughts now, and they _don't play nice with each other_. These appendices, this cruft, is what makes switching browsers harder than it ought to be.

My problem with this, simply, is I have a lot of bookmarks. Not a big heap of bookmarks, but carefully curated folders of folders of entries I use on a regular and daily basis. Hundreds of them. I maintain my bookmarks; I curate them. They keep my work organized, and I pay back the favor... you get the idea. Yet, every time I switch browsers, I end up fixing things up again. Firefox offers to import your bookmarks... into the "From [some other browser]" [folder](https://support.mozilla.org/en-US/kb/import-bookmarks-google-chrome). Chrome [relegates](https://support.google.com/chrome/answer/96816?hl=en) them to some position that's not displayed on the bookmarks bar. God forbid you try using a few browsers together... the only plugin that made any earnest effort to keep things in sync was [XMarks](https://news.slashdot.org/story/18/04/27/1924210/bookmark-syncing-service-xmarks-closes-for-good-on-may-1), and it's been relegated to the trash heap. This is just on the desktop... I've not even touched on the mess that is getting those bookmarks to work on some mobile browser. _Shudder_.

Well, I _had_ a lot of bookmarks. I couldn't deal with the back and forth anymore. It's enough just to keep the bookmarks neat and functional; trying to get browsers to play nice was just more than I was ready to deal with.

> Side Note:
> I am actually pursuing a side project that will make those damn browsers play nice... but it's a _long way off_...

Well, I'm a developer. I make software, and I'd like to think I'm fairly good at it. So, I decided to look at this like any software problem... and the clear solution was to _refactor my bookmarks_; abstract them away from the browsers in a way that maintained usability. So... here we go... "[Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)" meets "bookmark hell":

### 1. There are two kinds of bookmarks. Applications one uses, and media one experiences (documents to read, videos to watch, you get the idea). Separate them.

### 2. Application bookmarks are redundant... with your password manager. So make use of it.

I work with public clouds, so I ~~have~~ had a top-level bookmark folder of all the cloud provider portals. But all the credentials for those unique portals are in my [Lastpass](https://lastpass.com) vault as well, _including the URL_. It turns out most password managers have built-in [functionality](https://support.logmeininc.com/lastpass/help/organize-your-vault-with-folders-lp040010) for sorting/grouping entries... this is a perfect place to keep _all_ your application URLs. I duplicated my bookmark folder structure into Lastpass, and proceeded to delete all the bookmarks that are redundant. Lastpass plugs into every browser I care to use, from Firefox to Brave, and maintains it's own sync behind the scenes. You may prefer another password manager, but I'm sure you'll find that if it integrates with browsers, it integrates with almost all browsers; or it doesn't integrate at all, and that's exactly how you want it... you Luddite.

### 3. Media can be further subdivided into things you keep for reference, and things you just want to consume but haven't had time for. Further sort these into two piles. This also a great time to reflect on all those blog posts you bookmarked four years ago, but never got around to reading. Discard what is obviously no longer relevant.

Now, there are two paths you can go down here... and I ended up going down both.

Pick out a "pinboard" app, if you don't have one already. I decided to go with [Pocket](https://getpocket.com), and again it plays nicely with every browser I care to use and syncs nicely. [Tags](https://help.getpocket.com/article/938-tagging-in-pocket-on-your-computer) took the place of folders here, but that's fine, it's still searchable, and if _one good thing_ has come out of Gmail, it's that tags and folders can be [interchangeable](https://askleo.com/how-do-gmail-labels-relate-to-folders/). Those docs you want to keep for reference? Favorite them. Star them. Make a 'reference' tag. Whatever.

I found I also had a few documents I wanted quicker access to than with Pocket... so I added those to Lastpass as favorites as well. Now, whether I start searching in Lastpass, or Pocket, I always have my [Circus Music youtube video](https://youtu.be/m5csNO3oMrQ?t=21s) readily accessible.

### 4. Hide your bookmarks, and test things out.

You may find that your password manager isn't making searches easy, or that your pinboard just takes too long to load. Fine tune your folders & tags until you find and arrangement that works. If you're trying out a new tool and it's not working out, try another one before you get too invested! I ended up flattenning things a bit in Lastpass, to make navigation easier, and made my Pocket index my "home" page and "new tab" page, so things were quickly within reach.

### 5. When it works, _delete your bookmarks_.

Avoid the temptation to go back and get stuck in that rat trap again. Delete all your bookmarks in each browser, and hide the bookmarks bar as far away as you can. Disable the feature if you can. Make sure you're living in your new bookmarkless world for real. (It's okay to keep that backup you made before you started. You _did_ make a backup, right?)

### 6. Bonus: win at mobile!

I found, as a bonus, that it was now easier than ever to also do things on my smartphone, when I needed to. The tradeoff there was relatively simple; I just needed to stop trying to use a _single_ browser on my phone, and accept the browser component built into apps. Lastpass on Android lets me add fingerprint security, and still get to things quickly (and wipe out my sessions when I'm done.) Pocket makes it super easy to read some of those blog posts I'd been sitting on when I'm otherwise just sitting.

Vice versa, when some app wants me to register, I can generate the credentials in Lastpass, instead of resorting to "that one password I can remember" - it will also fill them in again after I wipe the data out. That site I want to check out mentioned in a podcast? Pocket'ed... for reading later.

### Final thoughts.

So here I am, a month into _not having bookmarks_, and I'm just as happy with the decision as the moment I figured out it would work; all the trepidation about deleting my bookmarks.html files is gone, and I'm not looking back. What I am looking at is why I'm seeing some rendering glitches in Brave that I don't see in Chromium; Google Chrome (and it's weird relationship with [online ads](https://www.wired.com/story/google-chrome-ad-blocker-change-web/)) are just handling those janky DRM-laden media sites, and Firefox 61 has solved most of the performance issues I saw in early Quantum releases. Multi-browser living is easy!
