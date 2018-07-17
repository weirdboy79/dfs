
Debian
====================
This directory contains files used to package dfsd/dfs-qt
for Debian-based Linux systems. If you compile dfsd/dfs-qt yourself, there are some useful files here.

## dfs: URI support ##


dfs-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install dfs-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your dfsqt binary to `/usr/bin`
and the `../../share/pixmaps/dfs128.png` to `/usr/share/pixmaps`

dfs-qt.protocol (KDE)

