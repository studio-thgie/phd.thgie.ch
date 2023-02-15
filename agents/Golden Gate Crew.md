## Games
```dataview
TABLE join(system) as System, genre, year, join(agents) as Agents
FROM "games"
WHERE studio="Golden Gate Crew"
SORT finished DESC
```

## Sources
- https://swissgames.garden/studios/golden-gate-crew