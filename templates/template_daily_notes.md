---
excercise: null
mood: null
work_mood: null
meeting_people: null
alcohol: null
making_music: null
read_bible: null
banner: "https://source.unsplash.com/random"
---
# <% tp.date.now(format="YYYY-MM-DD") %>
```button
name 🔙🏠 Home
type command
action Homepage: Open homepage
templater true
```

## Zitat des Tages
<% tp.web.daily_quote() %>

## MORNING RITUAL

- [ ] Aufstehen
- [ ] Tee kochen
- [ ] 1 Kapitel in der Bibel lesen
	- [ ] Schreib dir auf, was du siehst
- [ ] Computer anschließen
- [ ] 1 min durchatmen

## Bible Journaling
```button
name Neuer Eintrag / Editieren
type command
action QuickAdd: bible-journal
templater true
```

> [!quote] Bible Journaling
> ```dataviewjs
> const today = dv.current().file.name
> const file_path = "Glaube/Tägliches Bibellesen/" + today
> const page = dv.page(file_path)
> const noteText = await dv.io.load(page.file.path)
> let regexPattern = new RegExp("#{1,6}\\s(" + today + ")\\n(.+?)(?:\\n#{1,6}|$)", "sg");
> let matches = regexPattern.exec(noteText)
> dv.el('span', noteText)
> ```


## Heutige Notizen (Hinzugefügt / Bearbeitet)

```dataview
table without id
	file.link as Titel,
	file.cday as Hinzugefügt,
	file.mday as Bearbeitet
where file.mday >= date(<% tp.date.now(format="YYYY-MM-DD") %>) OR file.cday >= date(<% tp.date.now(format="YYYY-MM-DD") %>)
```

## Heutige Aufgaben

```tasks
created today
```
