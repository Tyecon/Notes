# Calendar
```calendar
full
```
# Tasks
```dataview
TASK
WHERE !contains(file.tags, "Music")
AND !completed
AND status != "cancelled"
AND status != "idea"
AND status != "-"
```
# Todo
```dataview
LIST FROM #TODO 
WHERE !contains(file.tags, "Music")
AND !contains(file.tags, "Writing")
```
