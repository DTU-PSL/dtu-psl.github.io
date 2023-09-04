---
hide:
  - navigation
  - toc
  - nav
---

# Latest publications

These are the latest 50 publication by the group members. The list is automatically generated from the publications available at <https://orbit.dtu.dk/en/>.

```python exec="on"
import feedparser

rss_urls = [
  "https://orbit.dtu.dk/en/persons/andrea-burattin/publications/?format=rss",
  # "https://orbit.dtu.dk/en/persons/ekkart-kindler/publications/?format=rss",
  "https://orbit.dtu.dk/en/persons/hugo-andres-lopez-acosta/publications/?format=rss",
  "https://orbit.dtu.dk/en/persons/giovanni-meroni/publications/?format=rss",
  "https://orbit.dtu.dk/en/persons/andrey-rivkin/publications/?format=rss"
]

items = dict()
for rss_url in rss_urls:
  feed = feedparser.parse(rss_url)
  for i in feed["items"]:
    items[i.guid] = i

items = list(items.values())
items.sort(key=lambda item: item.updated_parsed, reverse=True)

start = "</span></a></h3>"
end = "<p class=\"type\">"
items = list(dict.fromkeys(items))
for item in items[0:50]:
    print("- [" + item.title + "](" + item.link + ")  ")
    print("  " + item.description[item.description.index(start):item.description.index(end)])
```