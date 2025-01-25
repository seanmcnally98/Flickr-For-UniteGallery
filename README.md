# Flickr-For-UniteGallery
Allows UniteGallery to load images from Flickr

## Why does this exist?

Simply, because I needed it to.  I wanted to convert a legacy website that previously used flickrembed.com to create galleries (I wouldn't recommend following that link today, it's been replaced with something that looks rather spammy).  
Well, as it turns out, flickrembed just used UniteGallery as a backend, so I figured if I could get UniteGallery to import Flickr images, everything would work.  And it did!

...sort of.  This requires using the Flickr API, which has seemingly arbitrary rate limits (or at least ones I can't find documentation on).  So, if you're trying to get a huge album or you load a bunch of times in rapid succession, it just plain doesn't work.  If I were to take a guess, some change on Flickr's end might have caused the original flickrembed to shut down.  So, bearing that in mind, if you still want to do this...

## How does it work?

Basically just makes an API call to Flickr, gets a list of image URLs, then adds them to a UniteGallery Gallery
To use this, take a look at the ug-flickr-github.html example file.

## Quick Start Guide

This will get ug-flickr-github.html up and running, just so you can see it working and test it out.

1) Right click ug-flickr-github.html above, Save Link As, download it in a new folder
2) Go to http://unitegallery.net/index.php, click the red download button, extract `unitegallery-master.zip`
3) Go inside your newly extracted folder, and navigate to `unitegallery-master\unitegallery-master\package\`.  Inside THIS folder (package), you'll find a folder called `unitegallery`, that is the folder you actually need.  Everything else can be deleted.  Cut and paste that to the same folder you put `ug-flickr-github.html`.
4) Get a flickr API key from https://www.flickr.com/services/apps/create/.  It's pretty simple, you just put in what you're using it for, and they give you the key right away.
5) Edit `ug-flickr-github.html` in a text editor, and go to line 18.  Replace YOUR-API-KEY with the one you got from the previous step.
6) Open up `ug-flickr-github.html` and you should see a gallery of some island photos load up.
7) If you have that much working, you can change `const albumId = "72157718908695089";` and `const userId = "67995615@N03";` to one of your albums, and using your user ID.  Get these by going to your album on the web, and taking them from the URL - the format is flickr.com/photos/USER ID/albums/ALBUM ID/.  Note that if you have a vanity username (readable text rather than numbers and an @) you'll need to use http://webfx.com/tools/idgettr to get your actual User ID.

## How do I change other things, like the theme and skin?

Check out the [Unite Gallery Documentation](http://unitegallery.net/index.php?page=documentation) for examples on how to change stuff.  For customizations, you'll be changing this part, at line 54
```
gallery.unitegallery({
  gallery_theme:"tiles",
  tiles_type:"nested",
  gallery_enable_loadmore:"true",
	gallery_images_preload_type:"visible",
	lightbox_overlay_opacity:"0.9"
  });
```

For example, you can change `gallery_theme` to something like `"compact"` or `"default"`.  To find all the options for each indivudal theme, go to [Unite Gallery's website](http://unitegallery.net/index.php) on Desktop only, and hover your mouse over the theme name you want at the top of the page, then find the "Including and options" page.

Enjoy!  But...you probably shouldn't use this for anything too important.  It breaks on Flickr's end pretty frequently!
