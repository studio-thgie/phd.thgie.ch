---
author: Adrian Demleitner
tags: Notes, Method, Corpus
updated: 2023-11-17T13:52
created: 2023-08-14T16:15
---
# Image Corpus 

- [Outline](#outline)
- [Considerations](#considerations)
- [Corpus generation](#corpus-generation)
	- [Parameters](#parameters)
	- [Collection process](#collection-process)
	- [Additional strategies](#additional-strategies)
- [Ontology](#ontology)
- [Aiding scripts](#aiding-scripts)
	- [Extracting Colours](#extracting-colours)
	- [Scrapping Images](#scrapping-images)

## Outline
The image corpus is built following a strategy to include as much material as is necessary to fully represent a games' visuality (aesthetics and content). Next to formal and semiotic elements and paratextual material, the Game FAVR model of categorisation for the visuality of a digital game is applied to collect material. Since building a corpus of images retrieved from digital games can be a considerable effort regarding having to play entire games[^1], additional collecting strategies are considered.

The [FAVR](notes/FAVR.md) is clear in outline and scope and is mostly considered with the macro and material perspective on the image in digital games. Formal and semiotic elements can vary in their scope and focus towards the micro level of a game. Decisions will have to be made with each game, slightly adjusting what is collected. If needed, I'll expand the outlined parameters below. The approach follows loosely along compositional analysis, whereas the FAVR takes over the spatial components and semiotic elements over content.

The paratextual material is restricted to what was issued by the developing and publishing actants to keep the analysis within the intentions and meaning production of the agencies directly involved.

## Considerations
*Ergodicity*

The production of screenshots from a video game is a regress from ergodic media to static images. The gameness or dimension of gameplay is lost in this process and only traces of it are present in the final product. Sebastian Möring calls the screenshot's dependency on the source game conditional cyberimage. The loss of this aspect in the screenshots need to be considered when analysing the visual material.

- what can we analyse then, and what to we lose? #todo

*Screencasts*

Screencasts would solve the problem of the loss of ergodicity only partially, while introducing other problems. I exclude videos from my analysis as of now, since they introduce new technical considerations and research problematics, such as the analysis of progression in time, the storage of the collected media or how to properly code (label) videos. This aspect will stay problematic for now, as some objects only reveal themselves in animations, for example special effects that indicate a change of game state.

*Image Quality*

Another consideration is the balance between quantity and quality, as in, complete visual representation of a game versus the quality of the collected images. Producing all the screenshots oneself will reduce the amount of treated games because of the needed effort. On the other hand, screenshots of play-throughs or scrapping produce lower quality images regarding their resolution, having compression artefacts or faulty colour spaces. If scrapping can be automated, I will include the material either way and mark it as such.

## Corpus generation
### Parameters
- [FAVR](notes/FAVR.md): Visual modes, ocularizations, framing mechanisms, construction of tangible space
- Formal Elements: Colours, textures, shapes, composition and layout, typography, etc.
- Semiotic Elements: Characters, objects, levels, interactive elements, etc.[^2]
- Relevant paratexts: Box art, manuals, advertisement, etc.

### Collection process
1. Attempt to gain an overview of scope through rudimentary game play
2. Collect towards FAVR's four relevant aspects
3. Meanwhile, create a checklist for the formal and semiotic elements
4. Collect screenshots of listed elements through playing yourself
5. If necessary, expand with screenshots of play-throughs or scrapped material
6. Collect paratextual material

### Additional strategies
- Screenshots of videos of play-throughs
- Scraping popular databases for image material regarding the relevant games
- [Assembling Auras](literature/guay-belangerAssemblingAurasMethodology2022.md) to collect visual material that seems relevant but is not coming from the game directly

## Ontology
I use [Tropy](https://www.tropy.org/) to collect, maintain and label the image material. To simplify this processes, I built an ontology based on FAVR. The ontology's repository also holds onto the Tropy templates I created. The repository can be found under

- [https://github.com/thgie/favr-ontology](https://github.com/thgie/favr-ontology)
- [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8158800.svg)](https://doi.org/10.5281/zenodo.8158800)

## Aiding scripts
### Extracting Colours
For a specific aspect of formal analysis, I will extract the dominant colours per image.
```bash
sample=PATH_TO_IMAGE
area=$(magick $sample -format "%[fx:w*h]" info:)
magick $sample -kmeans 8 -format "%c" histogram:info:  | sed 's/://g' | awk -v area=$area '{print 100*$1/area, "%|", $3, ","}' | sed 's/ *//g' | sort -nr -k1,1 -t ","
```
Via https://stackoverflow.com/questions/70397629/imagemagick-extract-dominant-colors-from-an-image-in-hex-and-percentages

### Scrapping Images
*Screens from Hall of Light*

The following Javascript snippets, pasted to the developer console while being on a page with screenshots, results in a properly formatted list of image URLs.

```js
let screens = ''
document.querySelectorAll('.screenshot_thumbnail').forEach(el => {
	let src = el.src
	src = src.replace('_preview/', '/')
	src = src.replace('_preview', '_screen')
	screens += src + '\n';
})
console.log(screens)
```

HOL is probably blocking `wget` requests. But automating the scrapping would look like this. Save console message as text file, then execute:

```bash
wget -i images.txt
```

*Mobygames with HTTrack*

Command generated through WebHTTrack and adjusted.
```bash
httrack -q -%i -w 'https://www.mobygames.com/game/1618/commando/' -O "/Users/dna4/Downloads/Scrapping/Commando2" -n -%P -N0 -s2 -p7 -D -a -K0 -c10 -%k -A25000 -F "Mozilla/4.5 (compatible; HTTrack 3.0x; Windows 98)" '-*.webp' '-*.css' '-*.js' '-*.xml' '+*.png' '+*.gif' '+*.jpg' '+*.jpeg' -%s -%u
```

[^1]: One needs to know the entire game to know if all relevant material has been collected.
[^2]: Classifications of semiotic signs in video games is a difficult topic since at least the 90ies (Espen, 1997). I'll follow a reflexive approach that documents choices and thoughts made towards the corpus.