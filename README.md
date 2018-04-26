## gtk3-filechooser-icon-view
This is a personal fork of GTK3 with the intention of the solving the infamous [filechooser bug](https://bugzilla.gnome.org/show_bug.cgi?id=141154&). gtk3-filechooser-icon-view provides an alternative icon view for the filechooser dialog. This shows proper, resizable thumbnails in the dialog for any type of file that has thumbnails stored in ``~/.cache/thumbnails/``. A version for GTK2 also exists [here](https://github.com/Dudemanguy/gtk/tree/gtk2-filechooser-icon-view). 


Since GNOME developers likely will not be satisfied with the state of this branch anytime soon, this is my personal branch to follow upstream gtk3 development. The AUR package, [gtk3-patched-filechooser-icon-view](https://aur.archlinux.org/packages/gtk3-patched-filechooser-icon-view/) is also maintained by me and follows Arch's [gtk3](https://www.archlinux.org/packages/extra/x86_64/gtk3/) package. For those that are not on Arch and want to build their own packages to match their own distribution's version of gtk3, a patch file is available [here](https://gist.github.com/Dudemanguy/c172394e30e1e7d0f477ad15c719bc71).

## Preview
![image](https://raw.githubusercontent.com/Dudemanguy/gtk/gtk3-filechooser-icon-view/gtk3iconview.png)

## glib-thumbnailer
Another patch that may be of interest is the [glib-thumbnailer](https://gist.github.com/Dudemanguy/d199759b46a79782cc1b301649dec8a5) patch. On its own, gtk3 is not capable of generating any thumbnails. This must be done using thumbnail generators such as ``tumbler``. So if the filechooser dialog is opened and thumbnails for the images were not already generated through some other means (such as opening the directory in your file manager), only the stock gtk image icon will be displayed. 

To address this, the glib-thumbnailer patch sends a signal to dbus to generate thumbnails while the filechooser dialog is open. Note that in some applications, the thumbnail generation does not work when opening the dialog due to some mysterious dbus error (chromium is known to fail). An AUR [package](https://aur.archlinux.org/packages/glib2-patched-thumbnailer/) is also available.
