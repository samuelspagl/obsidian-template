---
cssclass: cards-cover, cards-1-1, cards, table-wide
---
 
```ccard
type: folder_brief_live
```
 
```button
name Neue Predigtnotiz
type command
action QuickAdd: Sunday Sermon
templater true
```

```dataview
table without id 
	banner as Image,
	file.link as Title,
	"*Datum:* " + string(Datum) as Datum, 
	"*Pastor:* " + Pastor as Pastor,
	Gemeinde as Gemeinde
from "Glaube/Predigtnotizen"
where file.name != "Predigtnotizen"
where file.name != "template"
sort Datum descending
```


