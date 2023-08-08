---
updated: 2023-08-08T11:34
---
<%*
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE WITHOUT ID
		link(file.link, title) AS "Title",
		join(tags) as Tags
	FROM "notes"
	WHERE contains(tags, "Glossary") 
	SORT title ASC
`);

// replace wikilinks with markdown links
let table = te.value.replace(/\[\[([^|]+)\\\|([^|]+)\]\]/gm, "[$2]($1)");

// clean up markdown link
var reg = /(\(.*\))/g;
var result;
while((result = reg.exec(table)) !== null) {
	table = table.replace(result[0], result[0].replaceAll(' ', '%20'));
}

tR += table;
%>