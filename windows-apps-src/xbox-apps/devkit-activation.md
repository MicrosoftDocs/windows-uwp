---
title: Xbox One Developer Mode activation
description: How to activate Developer Mode so you can switch between Retail Mode and Developer Mode.
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: ade80769-17ae-46e9-9c2f-bf08ae5a51ee
ms.localizationpriority: medium
---
# Xbox One Developer Mode activation

## How Developer Mode works
This article only applies to Xbox One and Xbox Series X|S consoles acquired through retail channels. For development kit HW acquired via a managed development program, see the note at the end of the article.

Xbox retail consoles can have two modes, Retail Mode (1) and Developer Mode (2). In Retail Mode, the console is in its normal state: you can play games and run apps acquired through the Xbox store. In Developer Mode, you can develop and test software for the console, but you cannot play retail games or run retail apps.

Developer Mode can be enabled on any retail Xbox console, via the “Retail to Dev Kit conversion” app found in the Xbox store. After Developer Mode is enabled on your retail console, you can switch back and forth between Retail (2a) and Developer Mode (2b).

> [!NOTE]
> Do not run this conversion app on any Xbox development hardware acquired through an Xbox managed program (for example, ID@Xbox) or you may introduce errors and delays while developing your game. If you're a managed partner, you can get more information on activating development hardware. Go to https://developer.microsoft.com/en-us/games/xbox/docs/gdk/provisioning-role.

<br></br>

![Xbox One modes](images/dev-mode-flow.png)

## Activate Developer Mode on your retail Xbox console

1.	Start your Xbox console.

2.	Make sure your console have the latest Xbox system update installed. For more information, please visit [About system updates on Xbox Series X|S and Xbox One](https://support.xbox.com/en-us/help/hardware-network/settings-updates/system-update-overview)

3.	Go to **Settings** > **System** > **Console info**.

    ![Xbox System Console info](images/xbox-settings-console-info.png)

4.	On your controller, press **LB**, **RB**, **LT**, **RT**. The Developer settings menu entry will be shown.

    ![Xbox Developer settings menu entry](images/xbox-developer-settings-menu-entry.png)

5.	Go to **Developer settings** > Check **Developer mode** > **Continue**. Your Xbox console will restart.

    ![Xbox Developer settings](images/xbox-developer-settings.png)
    
6.	After restarting, your Xbox will be in Developer Mode.

    ![Xbox Dev Home](images/xbox-dev-home.png)

## Switch back to Retail Mode
After Developer Mode has been enabled on your console, to switch back to Retail Mode, under **Quick actions**, select **Leave Dev Mode**. This will restart your console in Retail Mode.    

  ![Leave Dev Mode](images/xbox-leave-dev-mode.png)
  
## See also
- [UWP on Xbox One](index.md)
