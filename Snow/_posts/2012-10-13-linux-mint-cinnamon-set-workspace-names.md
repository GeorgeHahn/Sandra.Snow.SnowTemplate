---
layout: post
title:  (Linux Mint) Cinnamon Set Workspace Names   
category: linux
---
In Cinnamon 1.6, workspaces in the expo can have custom names applied. However, these names are not carried through to the window right click menu (Move to another workspace ->).

Workspace names in the right click menu are set by the workspace-names key in org.gnome.desktop.wm.preferences.

For example:

	gsettings set org.gnome.desktop.wm.preferences workspace-names "['Entertainment', 'Projects', 'Programming', 'Learning', 'Homework']" 

(Sadly, these names do synchronize with the expo names, so you'll have to set everything twice.) 