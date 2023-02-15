<%*
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE join(affiliation) as Affiliati
	FROM "actants"
	SORT finished DESC
`);
tR += te.value;
%>