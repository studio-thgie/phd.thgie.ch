<%*
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE WITHOUT ID
		link(file.link, title) AS "Title",
		date as Date, join(tags) as Tags
	FROM "journal"
	SORT date DESC
`);
tR += te.value;
%>