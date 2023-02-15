<%*
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE WITHOUT ID
		link(file.link, title) AS "Title",
		authors as Authors, join(tags) as Tags, year as Year
	FROM "literature"
	SORT year DESC
`);
tR += te.value;
%>