<%*
const dv = app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`
	TABLE join(system) as System, genre as Genre, year as Year, join(agents) as Agents, studio as Studio
	FROM "games"
	SORT finished DESC
`);
tR += te.value;
%>