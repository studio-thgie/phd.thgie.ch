---
created: 2023-09-25T10:19
updated: 2023-09-25T17:41
author: Adrian Demleitner
---
# Working with Amiga Floppy Disks in Historical Video Game Research
![](IMG_3130.jpeg)

Like most humanists and historians, we work with historical materials that we compile into a corpus. How does this approach apply to researching digital-born media, such as video games designed for the Amiga computing system?

When inquiring older digital games, the question of authenticity quickly arises. Playing a game is an integral part of investigating it. There is virtually no way to avoid this principle. However, when dealing with games designed for deprecated or obsolete hardware, you must consider the impact of the playing environment on your research. Is it crucial to experience the game with the original joystick? Is it acceptable to run the game on an emulator, viewing it through a 3.5" display? What role did the materiality of the original hardware play, including the sounds it produced, in shaping the player's experience?

Playing a game on an emulator is far more time-efficient. Many digital games have already been copied from their physical media, such as floppy disks, and archived on informal online platforms. It's a simple matter of matching the appropriate emulator software with the downloaded game files, and you're ready to go. Working with the original hardware is considerably more resource-intensive. You need to locate the appropriate hardware, purchase it (hoping it still functions), transport it, and find storage space, not to mention the ongoing maintenance.

## Amiga
We recently acquired a complete Amiga set, with a monitor, joysticks, and hundreds of floppy disks, primarily containing games. More information can be found in this [Mastodon post](https://hcommons.social/@thgie@post.lurk.org/110899431776662399). The Amiga was an immensely popular home computing system in the 1980s and 1990s, particularly for gaming. Among the games in this acquisition, two are relevant to our research project: an original version of [Ringside](https://swissgames.garden/games/ringside) (1989) and a demo version of [Rolling Ronny](https://swissgames.garden/games/rolling-ronny) (1991). Most of the other games we found in this disk collection are available online on the aforementioned informal archives and are currently of lesser importance to us.

Having an Amiga available in our game lab at the University of Bern inspired us to play some of the games from our corpus on the actual machine. We aren't necessarily focused on reviving questions of authenticity, but it's undeniably enjoyable to explore different playing setups. All we needed were a USB-powered floppy drive and some blank floppy disks—or so we thought.

In a brief search for software to read or write Amiga floppy disks, we discovered that the challenge lies at the hardware level. At that point, we already had a "modern" USB-driven floppy drive, which was rendered useless for our purposes. Different floppy drive systems employ distinct methods of encoding data on the disk, involving varying reading and writing patterns. This process is controlled by hardware and cannot be altered by software.

What we required was old hardware capable of connecting to new hardware...

## Greaseweazle
Fortunately, we were not the first to confront this issue. Several existing projects tackle the problem. Established examples that address reading and writing old computing system floppies include [KryoFlux](https://en.wikipedia.org/wiki/KryoFlux) and [Pauline](https://wernli.pages.in2p3.fr/pauline-doc/en/). We opted for [Greaseweazle](https://github.com/keirf/greaseweazle), which appeared to be a popular and readily accessible choice within the Amiga enthusiast community. Greaseweazle is a compact circuit board that connects older floppy drives to modern computers running contemporary operating systems via USB. We swiftly ordered the device from an online shop specializing in spare parts and extensions for the Amiga system.

Acquiring an older floppy drive proved to be somewhat more challenging. Greaseweazle can accommodate numerous different drives, from those used in the Commodore 64 and Amiga to those found in desktop towers running Windows or a Unix derivative. These drives are not ubiquitous on the second-hand market, but at least relatively common and affordable, typically priced around 10.- CHF. To establish a functional setup, we also needed power and data cables, which is when most of the sellers we contacted started to ghost us. We didn't just want the drive; we also needed the necessary cables. Many sellers either didn't possess these cables or were unwilling to expend the effort to locate them, at least not at the price they were offering the drives. Scouring various second-hand stores and cash converters yielded no results either.

Finally, we located a seller in the opposite corner of Switzerland who was willing to provide both the drive and the cables.

![](IMG_3129.jpeg)
![](IMG_3132.jpeg)

## Key Takeaways
Once we assembled all the necessary components, the rest proceeded smoothly. Installing the required command-line tools for macOS was straightforward, thanks to the well-documented [Greaseweazle Wiki](https://github.com/keirf/greaseweazle/wiki). I would like to delve further into this aspect, but a simple `gw read filename.adf` sufficed to create a dump of a diskette that I could later verify in an Amiga emulator. Writing a dump I had downloaded from the internet to a floppy disk was accomplished with `gw write filename.adf`, and that concluded the process. While there are more specific commands and options available, I didn't require them at this point.

What intrigued me more was the minor ordeal I underwent to obtain the appropriate hardware, despite it not being excessively old. It began with the realization that a newer USB-driven floppy drive wouldn't suffice and extended to visiting every second-hand shop in my area. Floppy disks still exist, but there are only a few individuals who truly care about this technology, aside from specialized archivists and enthusiasts.

For our research project, this technology is invaluable. We rely on it to extract data from floppy disks, preserve them, and share them with our fellow researchers. Additionally, it allows us to play dumped games on the original hardware. Consequently, we need to acquire the necessary knowledge and infrastructure to set up and maintain such systems. Maintenance will be a journey for another day. For now, I enjoy the ease of use that the current setup brings to our research process.

## Sources
- [Floppy Disk Preservation Project](https://diskpreservation.com/dp.php?pg=floppyhow)
- [Home · keirf/greaseweazle Wiki · GitHub](https://github.com/keirf/greaseweazle/wiki/)