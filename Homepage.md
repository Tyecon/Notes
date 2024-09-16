# Tasks
```dataview
TASK
WHERE !contains(file.tags, "#TODO/Music")
AND !completed
GROUP BY file.link
```
# Todo
```dataview
LIST FROM #TODO 
WHERE !contains(file.tags, "Music")
AND !contains(file.tags, "Writing")
```
