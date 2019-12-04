## gtk2-filechooser-icon-view
This is a personal fork of GTK2 with the intention of the solving the infamous [filechooser bug](https://bugzilla.gnome.org/show_bug.cgi?id=141154&). gtk2-filechooser-icon-view provides an alternative icon view for the filechooser dialog. This shows proper, resizable thumbnails in the dialog for any type of file that has thumbnails stored in ``~/.cache/thumbnails/``. A version for GTK3 also exists [here](https://github.com/Dudemanguy/gtk/tree/gtk3-filechooser-icon-view). 


GNOME developers have stated that no big new features will be added to gtk2, so this is my personal branch to keep up with gtk2 maintenance. The AUR package, [gtk2-patched-filechooser-icon-view](https://aur.archlinux.org/packages/gtk2-patched-filechooser-icon-view/) is also maintained by me and follows Arch's [gtk2](https://www.archlinux.org/packages/extra/x86_64/gtk2/) package. For those that are not on Arch and want to build their own packages to match their own distribution's version of gtk2, a patch file is available [here](https://gist.github.com/Dudemanguy/d70734d5bdf82e79cbfb22894fac8a1b).

## Preview
![image](https://raw.githubusercontent.com/Dudemanguy/gtk/gtk2-filechooser-icon-view/gtk2iconview.png)

## glib-thumbnailer
Another patch that may be of interest is the [glib-thumbnailer](https://gist.github.com/Dudemanguy/d199759b46a79782cc1b301649dec8a5) patch. On its own, gtk3 is not capable of generating any thumbnails. This must be done using thumbnail generators such as ``tumbler``. So if the filechooser dialog is opened and thumbnails for the images were not already generated through some other means (such as opening the directory in your file manager), only the stock gtk image icon will be displayed. 

To address this, the glib-thumbnailer patch sends a signal to dbus to generate thumbnails while the filechooser dialog is open. Note that in some applications, the thumbnail generation does not work when opening the dialog due to some mysterious dbus error (chromium is known to fail). An AUR [package](https://aur.archlinux.org/packages/glib2-patched-thumbnailer/) is also available.
