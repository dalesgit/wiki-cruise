---
created: 2025-04-29T07:58:01 (UTC -07:00)
tags: []
source: https://www.xda-developers.com/replaced-google-photos-drive-docs/
author: Adam Conway
---

# I replaced Google Photos, Drive, and Docs with these free self-hosted services — and they're better, too

> ## Excerpt
> If you want to de-Google your life, then these are some of the best services to get started.

---
Yes, there are some downsides, but there are some surprising upsides, too. These are the tools I use to de-Google my life as much as I can, and they're really easy for anyone to set up and use.

## Prerequisites

### These bring it all together

    ![Running the TrueNAS Scale web UI on Brave](https://static1.xdaimages.com/wordpress/wp-content/uploads/wm/2024/10/truenas-scale-web-ui.jpg)

Before I talk about each of the individual services, there are two requirements that I personally use to make it all possible. The first is [TrueNAS](https://www.xda-developers.com/build-your-own-nas-using-truenas-scale/); I turned an old PC into a home server quite a while ago, and it runs the majority of my self-hosted services. I use Tailscale to enable connecting to all of my services, and I use Nginx Proxy Manager to configure a bunch of reverse proxies so that I can access my services with simple, human-readable domain names. You don't need to use TrueNAS Scale specifically; you just need somewhere to run all of the services.

While you don't _need_ a backup service, I strongly recommend it if you're looking to replace your Google ecosystem with self-hosted alternatives. Otherwise, you leave yourself at risk of losing all of your data.

## Nextcloud is the ultimate Google Drive replacement

### It even has a Google suite of apps, too

-       ![nextcloud-calendar-app](https://static1.xdaimages.com/wordpress/wp-content/uploads/wm/2025/03/nextcloud-calendar-app.png)

If you're looking for a [Google Drive replacement](https://www.xda-developers.com/how-build-google-drive-alternative-nextcloud/), look no further than Nextcloud. It provides essentially everything that Google Drive does, and more, but with the crucial advantage of giving you complete control over your data. Nextcloud allows you to store files, photos, and documents securely on your own hardware, meaning you're no longer at the mercy of Google's privacy policies. You can even automatically synchronize files and folders from your devices, with native programs and apps for every major platform.

There's no tracking when it comes to Nextcloud, and with a robust set of add-ons, you can make it better than Google's own offerings. Nextcloud Office is also fantastic, and while it may take getting used to, it'll ultimately give you the same result as you'd get from Google's own services. It pairs well with other tools on top of that, and you can even back up to BackBlaze from _within_ Nextcloud if you wish, simply by adding it as an external storage option.

    [![The Nextcloud UI displayed on a Poco M6 Pro, with a PC in the background](https://static1.xdaimages.com/wordpress/wp-content/uploads/wm/2024/07/nextcloud-1.jpg)](https://www.xda-developers.com/nextcloud-apps-get-most-out-self-hosted-cloud/)

Related

##### [5 amazing apps you should run on your self-hosted Nextcloud server](https://www.xda-developers.com/nextcloud-apps-get-most-out-self-hosted-cloud/ "5 amazing apps you should run on your self-hosted Nextcloud server")

If you're hosting your own Nextcloud instance, you should use these plugins to make it even better.

## Immich is my Google Photos alternative of choice

### And I use PhotoPrism sometimes, too

-       ![Running Immich on an SBC](https://static1.xdaimages.com/wordpress/wp-content/uploads/wm/2024/10/immich.jpg)

Even better, both of these services use local AI to add features you might be used to from Google, so you don't need to worry about losing much. You'll get face tagging, and you can even search for descriptive terms. For example, I can search "plane" in either service, and see photos of planes that I've taken, and the same goes for other objects and even locations. The only downside is that you won't have native photo editing, which people _do_ like about Google Photos. Still, to many, that's a small price to pay for total control of your images.

To ensure that my photos are safe, I also include the Photos dataset in my BackBlaze backup. That way, when disaster strikes, I can still pull all of my images down and access them.

## There are so many Google Suite alternatives

### You can pick anything here

-       ![Screenshot of OnlyOffice displaying an Excel spreadsheet](https://static1.xdaimages.com/wordpress/wp-content/uploads/wm/2024/12/onlyoffice-spreadsheets-2.png)

When it comes to self-hosting a Google Suite alternative, you have so many options. Nextcloud Office, based on Collabora, is pretty good, but OnlyOffice is the go-to for many who want to self-host their own alternative through the OnlyOffice document server. It's very close to what both Google and Microsoft offer with their own office suites, with a ribbon-style UI, and all of the tabs are very similar. Generally speaking, the same options are also available and presented in a way that you're used to as well.

If you're looking to de-Google your life and you want to replace Google's Suite of services, OnlyOffice is a fantastic option. If you specifically only care about replacing Docs functionality, you can look at tools like Outline or the appropriately named [Docs](https://www.xda-developers.com/docs-self-hosted-collaborative-note-taking-notion/). Finally, there's [CryptPad](https://www.xda-developers.com/reasons-cryptpad-best-privacy-focused-alternative-google/) for a more privacy-focused alternative, too.
