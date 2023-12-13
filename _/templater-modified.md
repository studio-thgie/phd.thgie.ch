## Wiki Changelog
<%*
let last_modified_date = await tp.system.prompt("Modified since…")
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE WITHOUT ID
		link(file.link, title) AS "Title",
		dateformat(updated,"yyyy-MM-dd") as Date, join(tags) as Tags
	FROM "notes"
	WHERE updated >= date(`+last_modified_date+`)
	WHERE tags
	SORT updated DESC
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