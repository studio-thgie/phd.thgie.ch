---
updated: 2023-08-08T11:27
---
<%*
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE join(system) as System, genre as Genre, year as Year, join(actants) as Actants, developer as Developer, publisher as Publisher, wikidata
	FROM "games"
	SORT year DESC
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