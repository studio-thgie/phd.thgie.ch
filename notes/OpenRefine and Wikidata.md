---
tags: [Notes, Methods]
---
# OpenRefine and Wikidata
This entry is a work in progress and will be expanded in the future.

I worked extensively with OpenRefine in order to import the CH-part of our [list of digital games from the German-speaking countries](https://spielkult.hypotheses.org/3999) into Wikidata. OpenRefine feels a bit like a batch-tool for spreadsheets. It's main purpose is to cleanup and transform spreadsheet data. It also has this fantastic connection to Wikidata, enabling the user to reconciliate (compare and link) spreadsheet data to entries on Wikidata. After cleanup and reconciliation you then can import your data to Wikidata.

This [OpenRefine Beginners Tutorial](https://www.youtube.com/watch?v=wfS1qTKFQoI) gave me a good verview on the basics of OpenRefine.

After some tryouts, my process looked like this:

1. Import prepared Google spreadsheet into OpenRefine
2. Split columns where necessary, ie if the platform or developer column contained several comma-separated values. For the reconciliation, a column can only contain one value.
3. Reconciliate the data you want to import. Most importantly the game title column. This one links your row of information to the entry on Wikidata.
4. Built your Wikidata schema of the things you want to import. This is a crucial step and can be messy, ie you have the game developer attribute, but not all the developers in your data exist on Wikidata yet. That might lead to the creation of said developers on Wikidata, but their not automatic reconciliated in your local data. If you don't reconciliate and import again, the developer might be created again and you have a duplicate on Wikidata.
5. Import your data. That works mostly fine, but I run into a problem when trying to import some new attributes to already existing entries. When no single value was present in a row and it tried to import it anyway, OpenRefine got stuck.

Especially the fourth step is very important to take care of. I organised it such that all linked entries are created first. If I have the attribute developers in my video game scheme, I see that all the mentioned developers exist already on Wikidata. That means that before the main import, you might want to build and import a developing people schema first.

