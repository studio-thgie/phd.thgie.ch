---
created: 2023-08-31T09:43
updated: 2023-08-31T09:44
---
# Choose your own Adventures in Source Code
## Critically reading the Commodore 64 emulator VICE's code base
Adrian Demleitner

Critical code analysis (Marino, 2020) situates source code not only as functional instruction for machines, but also as a cultural artefact, as text written by and for humans. This proposition enables the study of code through literary analysis. The question arises, to what extent can source code be treated as literary text or if it is much closer to the concept of text in Foucauldian discourse, as in, everything is text? The following article is a first foray into this question, by attempting to read into the source code of a Commodore emulator.

Emulators are crucial to studying video games of the past. They re-enact computing platforms and enable access to systems no longer produced and maintained. Most emulator projects are community-driven, with a variety of approaches to accuracy and authenticity. Although being acknowledged as an influencing factor to the experience of video games (Wolf and Perron, 2014). Beyond describing their functionality, only few attempts were made to research them. 

For my case-study I chose the Versatile Commodore Emulator (VICE), an established software project and being in continuous development since 1993. VICE can emulate different Commodore models and configurations, hence the Versatile in its name. In my search for a fitting study object, I found the source code of VICE to be very well documented and commented. Further, VICE has also been written on academically, making it a perfect epistemic object (Höltgen, 2014, 2020) and opening it up to critical analysis. In my own approach, I engaged with VICE through distant and close reading methods. [NOTE 1]

My initial findings suggest that critical code analysis can be a valuable and veritable approach to researching programming code. Nonetheless, there is still work to be done concerning the specific textuality of source code, especially regarding larger code bases.

## I. From afar
The digital humanities are well-equipped with methodologies for corpus analysis, the research on large collections of text. I would argue that the code base of VICE could be described as such. There are close to 3000 text-files amounting to more than 700'000 lines of source code, written in C and GTK+. To prepare the code base, I split it into three distinct corpora through the help of Python scripts. The first being the original code, whereas the other two containing just either functional code or comments.

I continued by throwing these newly created collections at Voyant Tools. Being an application for the lightweight study of text, Voyant Tools is often a first stop in the exploration of a textual corpus. Through text mining, it can produce statistics like word frequencies, but also pointing to relations within the text, like topics or correlations.

Despite my best efforts at configuring Voyant Tools towards this exceptional corpus, as well as getting support by my research colleagues in the digital humanities, I was unable to produce meaningful findings. Looking at the utter mess of an analysis that the application passed back to me, I started to feel sorry for the confusion I must have caused it. I did expect obstacles for this rather unconventional approach, but this clutter pointed towards something entirely different.

Distant reading approaches, as implemented in Voyant Tools, are essentially attempts in finding patterns. No matter if visually, in sound or structurally, patterns depend on at least one vector to appear. In other words, patterns need a certain amount of linearity to be detected, recurring along the line of reading. A good example would be counting a specific word in a corpus of letters sorted chronologically. The usage over time of this specific word can point towards meaningful insights.

My hypothesis is that Voyant Tools has had such a hard time with my corpora because of their non-linearity. Good source code is pragmatically optimized. One of the fundamentals of such a practice is the modularization and reuse of pieces of code. In the C language, the developer can reference another file with code through the `#include` statement. This fragmentation of code is continued by other programming structures, such as functions that can also be reused and referenced. This referentiality leads to a thick network of pointers, links and flows of information. I was unable to produce meaningful insights because I couldn't bring meaningful order into this network, at least not for Voyant Tools. If source code is text, it leans heavily on the side of hypertext, as conceptually outlined by George Landow. 

Being a pioneer in the research of electronic literature, he was also a proponent of visual maps that aid in navigating hypertextual media. I wanted to test my hypothesis through such a mapping, since conceptualizing the entirety of the code base through reading alone was unfeasible. I took the `#include` statement as a pointer of relationality and produced a Python script that translates these aspects into Gephi data. Gephi is an application for visualizing and analysing graphs and other types of networks. My intent was merely visualizing the code base, and I did not venture into graph analysis. The resulting graphic, a distant look at the network and relations of the source code files, showed up as a thick web of threads with a good two dozens central nodes.

It seems that source code could be seen as hypertext, but written at once for machine logic and something in the direction of a "Choose Your own Adventure Book". The relationality of a code base grows from the necessity of optimizing functional instructions for a computer. The optimization fragments a text into discrete units, striking a balance between machinic efficiency and the mental models and communicative units of the developers. 

## II. From up close
To supplement the extensive analysis from a distance, I delved into more subtle material. In my close reading, I employed the heuristic method introduced by Ea Christina Willumsen, which delves into the naming practices of variables and explores microstructures such as the underlying logic within functions (Willumsen, 2016). Furthermore, I examined the paratext surrounding the functional code, namely the comments, to gain deeper insights into the social dimensions of the codebase.

I quickly encountered difficulties when writing the regular expression (regex) pattern, which helped in splitting the code base into files containing just code or just comments. Some of the issues include different applications of block quotes, varied wordings in the licence or mixed ways of author attributions. This kind of diversity is to be expected in such a large and old code base. I was positively surprised by which rigour and exactitude licence, author attribution and comments were applied in this specific project. The beauty and magic of regex is its ability to handle diversity, for example, enabling inclusivity through the application of the asterisk character (*).

The different commenting styles triggered my interest and I started to look at them not only in terms of what they say, but also how they express themselves. The question arose, what intent drives the style of a comment? Of course, brevity and precision, but many comments wouldn’t fit one or the other. Some comments indicate what should happen, or comment the process along the lines of code. Then again, other comments tell little stories or expand an arcane line of code with cryptic numbers, undecipherable to the uninitiated.

```
/* drive speed is 300RPM, that is 300/60=5 revolutions per second
 * reference clock is 16MHz, one revolution has 16MHz/5 reference cycles
 */
clk_ref_per_rev = 16000000 / (300 / 60);
```

Whereas the style of functional code can be enforced and standardized by a style guide or even automation, comments are often more open to interpretation and the intent of the authors. A comment is at once communication as well as documentation towards a more or less defined public and time frame. A comment tries to explain code that is not self-evident and one of the most important aspects of collaborative software projects. The comments in the VICE code base were clear examples of different attempts to explain specific implementations, but also the intentions of the author. In a few examples, social processes became evident, for example the comment of a hacky implementation that could be done better but would not lead to improved results. The author left the better implementation to somebody else and added a smiley face.

```
rf = gcr_read_sector(&image->gcr->tracks[(dadr->track * 2) - 2], buf, (uint8_t)dadr->sector);
/* HACK: if the image has an error map, and the "FDC" did not detect an
error in the GCR stream, use the error from the error map instead.
FIXME: what should really be done is encoding the errors from the
error map into the GCR stream. this is a lot more effort and will
give the exact same results, so i will leave it to someone else :)
*/
```

In numerous instances, the comments also point to another essential point, which is the translation of electronic architecture into software processes (Höltgen, 2014, 2020). This became evident when attempting to read through a specific aspect of the VICE code base, the implementation of the Video Interface Chip II (VIC-II). In my own research, I am moved by questions regarding the interplay of technology and visuality in video games. Which is why I attempted to better understand the graphic capabilities of the Commodore but also the translation of its graphics hardware into the VICE emulator.

The Commodore 64 was specifically built to offer a range of official graphics modes that enable the use of character graphics, bitmap graphics, and sprites in both single and multicolour formats. These modes, powered by the VIC-II, could be seamlessly combined to create diverse visual effects. As users became more acquainted with the VIC-II, they started to explore unofficial methods that yielded enhanced graphical capabilities.

One of these unofficial methods involved the misuse of badlines. A badline refers to a gridline where the VIC-II turns off the processor temporarily to allow for increased memory access. The term badline stems from the disruption it causes to the processor's timing and becoming visible on screen, an early glitch. This can pose challenges and create interferences with various graphic tricks applied in C64 programming. However, there are also techniques that intentionally utilize these badlines for specific purposes [NOTE 2].

I didn't know about this, although I read the reports on how the specificities of hardware also need to be translated into the emulator. Reading the comments as well as the source code closely pointed me down an interesting factuality about the VIC-II. The arcane knowledge of hacking graphic modes on the Commodore 64 got embedded in code and comments. Even more, the code enabled the re-enactment of these unofficial practices. The following remark was found in the function "line_becomes_bad" in the file "vicii-badline.c".

```
/* Line is now bad, so we must switch to display state.
    Anyway, we cannot do it here as the 'ycounter' handling
    must happen in as in idle state.  */
```

I will cross a threshold here briefly, all scientificality aside. This comment is close to a poem and I get reminded of the DeCSS haiku, where a software for removing copyright protection from DVDs was rewritten as a series of haikus [LINK 1].

## III. Discussion
The intent for this exploration was twofold – figuring out what kind of text source code is and using it as the epistemological lense to research a project and its contextuality.

As a final measurement, I briefly researched the VICE developer community as well as its relation to the code base. An interesting view arose when visualizing which developers worked on which files [NOTE 1]. The authors' networked had 2590 nodes and 3390 edges. In contrast to the source code files thick web, this visualization lead to the clear insight, that just a handful of people worked the majority of the code base, with around ten key actors. In a quick check, I could figure out that more than half of the key actors are not listed as “current developers” on the website. It is also these people who mostly collaborated on files.

Using the VICE code base as a point of venture to research the emulator has been fruitful, even in this abbreviated approach. I found socio-cultural traces as well as embedded knowledge. The badline implementation, for instance, is a beautiful example of the need to translate the specificities of hardware into software. The code then becomes an executable documentation of hardware which might one day be no longer, leaving behind an epistemic object to read into the past.

Regarding the textual nature of source code in the context of critical code analysis, I remain undecided. Source code differs from its compiled, interpreted, and executed outputs. Willumsen contends that conventional concepts like "hypotext," "cybertext," or "paratext" inadequately capture the relationship between a game and its underlying code (Willumsen, 2016). Initial explorations using Voyant Tools and Gephi indicate that source code can exhibit characteristics akin to hypertext. Understanding the interplay among fragments of source code may demand the expertise of a skilled reader or assistance from software tools. Similar to Espen Aarseth's concept of cybertext, source code is ergodic, demanding significant effort to read and containing semiotic sequences beyond the scope of linear comprehension (Aarseth, 1997).

Beyond their textual essence, files and functions are enmeshed in multifaceted relationships. These connections span interpreters, compilers, runtimes, integrated development environments (IDEs), programming languages, resulting executed outputs, and, after all, the authors. Pointing to the mental models and communicative units shared among developers, fragments within the source code function as written signifiers, which transform into coherent text during reading. Revisiting the "line_becomes_bad" function exemplifies this. It simultaneously signifies an emulator's internal state, outlines necessary actions in response, and encapsulates insights into the intricate details of the original Commodore 64 hardware, specifically the VIC-II component.

Distant and close reading source code can lead to meaningful insights, but its structure withdraws established approaches for now. How can the digital humanities treat source code, respecting its specific textuality as outlined above? How do we go about close reading highly fragmented cybertexts? What kind of knowledge or insight can be gained from distant reading source code, aside from visualizations?

IV. Bibliography
Aarseth, E.J. (1997) Cybertext: perspectives on ergodic literature  Baltimore, Md: Johns Hopkins University Press.

Höltgen, S. (ed.) (2014) Shift-Restore-Escape: Retrocomputing und Computerarchäologie  Deutsche Erstausgabe, 1. Auflage. Winnenden: CSW-Verlag (Retrotopia, Band 1).

Höltgen, S. (2020) ‘OPEN HISTORY’. Available at: [https://doi.org/10.18452/21165](https://doi.org/10.18452/21165).

Marino, M.C. (2020) Critical code studies  Cambridge, Massachusetts: The MIT Press (Software studies (Cambridge, Mass.)). Available at: [https://mitpress.mit.edu/9780262043656/critical-code-studies/](https://mitpress.mit.edu/9780262043656/critical-code-studies/).

Willumsen, E.C. (2016) ‘Source Code and Formal Analysis: A Hermeneutic Reading of Passage’. Available at: [http://www.digra.org/digital-library/publications/source-code-and-formal-analysis-a-hermeneutic-reading-of-passage/](http://www.digra.org/digital-library/publications/source-code-and-formal-analysis-a-hermeneutic-reading-of-passage/).

Wolf, M.J.P. and Perron, B. (eds) (2014) The routledge companion to video game studies  New York, NY: Routledge (Routledge companions).


NOTE 1: A documentation on this experiment, further readings, visualisations as well as the mentioned Python scripts can be found under [https://phd.thgie.ch/notes/VICE.html](https://phd.thgie.ch/notes/VICE.html)
NOTE 2: An in-depth discussion of this hack can be found under [https://web.archive.org/web/20230518134443/https://bumbershootsoft.wordpress.com/2015/10/18/partial-badlines-glitching-on-purpose](https://web.archive.org/web/20230518134443/https://bumbershootsoft.wordpress.com/2015/10/18/partial-badlines-glitching-on-purpose). Watch closely, as the post explain hacking a video interface chip, hardware, but is able to show the results in the VICE emulator.

LINK 1: [https://en.wikipedia.org/wiki/DeCSS_haiku](https://en.wikipedia.org/wiki/DeCSS_haiku)