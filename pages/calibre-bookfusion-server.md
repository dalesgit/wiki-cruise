---
created: 2025-04-22T22:04:55 (UTC -10:00)
tags: []
source: https://www.howtogeek.com/i-gave-up-on-kindle-and-built-my-own-ebook-server-with-calibre/
author: Patrick Campanale
---

# I Gave Up on Kindle and Built My Own eBook Server With Calibre

> ## Excerpt
> Because “purchase” shouldn’t come with an asterisk.

---
### Summary

-   Calibre allows self-hosting of eBooks easily, categorizing, and serving with no subscription fees.
-   Setting up Calibre takes a few steps, and it's best to remember to keep the database local to avoid issues.
-   Calibre Web provides a user-friendly interface to browse, read, upload, and even integrate with Kindle for your eBooks.

Have you been searching for a way to ditch Kindle and build your own eBook library? I have, and Calibre makes it easy to self-host your eBooks, read them anywhere, and even still send them to your Kindle—no subscription required.

## Why I Ditched Kindle

Amazon recently decided that they would remove a feature from Kindle that many people loved—the ability to download eBooks to read on your own devices. This anti-consumer practice is among the latest in moves that show us digital content we buy isn't actually ours, we're just simply [gaining access that can be revoked at any time](https://www.howtogeek.com/403769/what-happens-to-your-digital-property-when-a-company-goes-out-of-business/).

While Kindle doesn't allow you to download eBook files anymore, there are [still many legal sources for free eBooks](https://www.howtogeek.com/legal-ways-to-get-free-ebooks/). The only issue is reading them easily. Of course, Amazon integrates its own services with its own hardware well, but it's not always the simplest solution if you want to supply the eBooks on your own.

   ![A person taking a Kindle from a bookshelf full of books.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/01/a-person-taking-a-kindle-from-a-bookshelf-full-of-books-1.jpg)

Lucas Gouveia/How-To Geek | fast-stock/[Shutterstock](https://www.shutterstock.com/image-photo/closeup-black-male-students-hand-he-2414494353)

That's what I wanted to do: read eBooks without the overreaching hand of Amazon. That's where Calibre comes in.

## Discovering Calibre

Instead of using the Kindle service to read eBooks, I decided to give Calibre a shot. I've heard a lot about it, and know several people who self-host it, but now it's my turn.
    ![A stack of books with a Kindle eReader on top of them.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/a-stack-of-books-with-a-kindle-ereader-on-top-of-them.jpg)

Dan Helyer / How-To Geek

[Calibre](https://calibre-ebook.com/) is a self-hosted tool that handles your eBooks. While Calibre itself only handles the database side of things, you can connect to it through quite a few apps. [BookFusion](https://www.bookfusion.com/) is available on both [iPhone](https://apps.apple.com/us/app/bookfusion/id1141834096) and [Android](https://www.anrdoezrs.net/links/3607085/type/dlg/sid/UUhtgUeUpU2012216/https://play.google.com/store/apps/details?id=com.bookfusion.android.reader), and [works natively with Calibre](https://www.bookfusion.com/reading/calibre).

Once you get your books into Calibre, it handles everything else for you. It'll categorize stuff, serve out the books, and more. The best part is Calibre is 100% free and open source, so there are no fees to use the service.

If you can source the books you want to read in EPUB, PDF, or any number of other formats, then Calibre can make them available for you to enjoy.

## Setting Up Calibre Wasn't Easy

Calibre is self-hosted, which means that you're on your own to install and configure it. I used Portainer to install it on my Docker host, and the primary installation was pretty straightforward.

There are three ports that need to be forwarded to the container, two volumes to mount, and just a few environmental variables to set. Overall, as far as Docker containers go, it was a pretty simple deployment.

 ![The Portainer admin interface with the settings needed to launch the Calibre Docker container.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/04/screenshot-2025-04-17-155221.png)

Patrick Campanale / How-To Geek

My Docker server is a separate computer from my storage server. I do this to keep services separate, but also to avoid downtime if I have to service one server and not the other.
    [![ Docker logo placed over a laptop computer keyboard.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/08/shutterstock_2428013233.jpg)](https://www.howtogeek.com/733522/docker-for-beginners-everything-you-need-to-know/)

Related

##### [Docker for Beginners: Everything You Need to Know](https://www.howtogeek.com/733522/docker-for-beginners-everything-you-need-to-know/ "Docker for Beginners: Everything You Need to Know")

Learn to use this incredibly popular development tool.

Because of this, I typically store persistent data (that will continue to grow over time) on the storage server, not the Docker server. I mount the storage server over both NFS and CIFS, depending on which is more reliable at the time.

When I first set up Calibre, I configured it to store the database on my NAS over the network share so that way, as my eBook collection grew, it wouldn't take up space on the apps server. I couldn't get Calibre to work at all, and it took me a while to troubleshoot. However, once I moved the database to local storage to the Docker server and not the network share, Calibre set up just fine.
    ![The Calibre backend interface showing several books imported into the library.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/04/screenshot-2025-04-17-154904.png)

Patrick Campanale / How-To Geek

Moral of the story: keep your Calibre database local to avoid headaches.

## Why Calibre Web Changed Everything

 ![The Calibre Web interface on a desktop showing several books available to be read.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/04/screenshot-2025-04-17-155307.png)

Patrick Campanale / How-To Geek

That's where [Calibre Web](https://hub.docker.com/r/linuxserver/calibre-web) comes in. This is a separate Docker container that connects to your Calibre server, allowing you to interface with your library in a much more user-friendly way. With Calibre Web, you're able to use things like a reverse proxy to access the library outside of your network in any browser. It also allows you to easily upload eBooks with just a few clicks of a button.

The Calibre Web UI is clean and makes browsing your eBook library a simple task. Because it's a self-hosted website, and not a VNC viewer into a container, it works natively how you'd expect on any device. Whether I was using my phone, laptop, iPad, or desktop, the Calibre Web interface scaled well and was easy to use overall.

![Reading a book in the Calibre Web interface.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/04/screenshot-2025-04-17-161204.png)

Patrick Campanale / How-To Geek

The biggest thing that Calibre Web does, for me, is allows me to upload books easily to my library. While I'm technically able to do it through the Calibre VNC remote, there are a lot more steps involved there.

Clicking the upload button allows you to choose all compatible file formats to upload, and Calibre Web then handles the rest from there. You can manually edit the metadata of a book, or fetch metadata from places like Google Books or Kindle to populate descriptions, authors and titles, the cover photo, and more.

![Calibre Web upload function being enabled.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/04/screenshot-2025-04-17-160651.png)

Patrick Campanale / How-To Geek

Where Calibre Web really changed things for me, however, is with its Send to Kindle integration.

## Send to Kindle Still Works—Here’s How

While I might be ditching Kindle as a means of purchasing books, I'm still keeping my (aging) Kindle Voyage around as long as it continues to work.

![Calibre Web Send EPUB to eReader function enabled at the top.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/04/screenshot-2025-04-17-160633.png)

Patrick Campanale / How-To Geek

Amazon still offers its Send to Kindle functionality, which gives your Kindle devices unique email addresses where eBooks can be sent. Calibre Web natively integrates with this once you have an SMTP or OAuth email account set up.

I personally went the route of SMTP with an app password for my Google account. OAuth just wasn't working for me in the Docker container, and that seems to actually be something relatively common—so SMTP it was.

Once you have an email account configured for sending mail, you're able to simply click "Send EPUB to Reader" and Calibre Web will handle the rest behind the scenes. For myself, it typically took a few minutes before the eBook was on my Kindle, but it worked every time I used it.

This will allow me to source my own eBooks elsewhere besides the Kindle store, host them myself, and still read them on my Kindle. It's truly the best of all worlds.
