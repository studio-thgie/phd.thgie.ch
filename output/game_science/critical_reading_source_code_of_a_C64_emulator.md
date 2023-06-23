# Critical reading source code of a C64 emulator 

## References
- epistemic object by stefan höltgen
- andre fachat and the translation of electronic architecture into software
- aarseths cybertext/ergodic literature mit einbeziehen/auf code anwenden

## Sentence outline
- Intro
	- Emulators are crucial to the research of old video games but, beyond describing their functionality, only few attempts were made to research them
	- [abstract](output/game_science/game_science_abstract.md)
	- stefan höltgen established the concept of emulators as epistemic objects, as in, they are holding the functional description of the systems they emulate; at once readable by machines and humans
	- In my own research I'm interested in the connection between technology and visuality of video games.
	- I'd love to understand emulators better, and will have a first brief look from my perspective in the digital humanities and design research focusing on exploring the processes and implementations around graphics and video
	- two methodologies: both focus on the source code; one is distant reading and one is close, or critical reading
	- summarizing the results
- Distant reading
	- preparation of the corpus to split the files into code and comments
	- throwing the source code at a common corpus analysis suite, such as voyant tools, created a mess
	- ! example: concentrating on comments and looking around a few keywords
	- discussing the problem of creating patterns in a non-linear corpus
	- landow hypertext: Though he was a consistent proponent of visual overviews and navigational maps, he long argued that hypertext navigation is not a problem—that hypertexts are not more difficult to understand than linear texts.
		- as a reaction to this problem I attempted to visualize the source code's relationality through gephi
	- discussion translating the networked structure into a visualisation tool
		- `#include` and source code as hypertext
		- Relation between authors and source files and regarding active and past members
- Close reading
	- at first, i concentrate on the source code's paratext, the comments, or the non-functional text
		- When trying to split the source code into code and comments, i encountered different License versions that I had to accomodate with my regex pattern
		- ! what kind of effect does the different license versioning have to the code base
		- I was also very interested by the different ways code is commented and how those different styles give different access to the knowledge embeded in the code
	- as a last attempt I tried to read the source code of the video and graphic pipeline
		- admitting to not be fluent in C or the C64 architecture
		- see points made in [2023-06-20](journal/2023-06-20.md)
- Discussion
	- i tried to create context and read VICE through it's online available information, having a good look at the project structure, the involved people, the way knowledge is archived and accessed online
	- what did I learn about VICE reading through it's code?
	- how can the digital humanities treat source code aside from close reading, what knowledge is gained from distant reading source code
	- source code as hypertext, source code as cybertext (aarseth)