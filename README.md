# Описание работы:
Первое знакомство с графовыми БД и языком запросов Cypher. <br>
Работа выполнена за 3 дня. <br> 
В `Readme.md` представлено поэтапное выполнение работы в виде анимации, также можно посмотреть видео по [ссылке.](https://cloud.mail.ru/public/VNEb/mbcg4hm47) (Не забудьте переключить качество). <br><br>
![anime-work](https://github.com/legion088/working-graph-databases/blob/main/presents/animation.gif)<br><br>
**Примененные запросы:**

```html
MATCH (n)
DETACH DELETE n

UNWIND $props as user 
MERGE(p1:  Participants1 {name: user.fullname1, id_event: user.id_event })
MERGE(p2:  Participants2 {name: user.fullname2, id_event: user.id_event })
MERGE(e: Event {name: user.id_event})

MATCH (n:Participants1) RETURN n LIMIT 100
MATCH (n:Event) RETURN n LIMIT 100
MATCH (n:Participants2) RETURN n LIMIT 100

MATCH (p1:Participants1), (p2:Participants2), (e:Event) 
WHERE p1.id_event = p2.id_event = e.name
CREATE 
(p1)-[:LINK]->(e),
(p2)-[:LINK]->(e)

MATCH p=()-[r:LINK]->() RETURN p LIMIT 100

MATCH (properties: Participants1 | Participants2)
WHERE properties.name = $name
RETURN properties ```
```
**Ссылки на документацию (не все):**<br>
https://neo4j.com/docs/cypher-manual<br>
https://neo4j.com/docs/python-manual/current/<br>
https://habr.com/ru/post/650623/<br>
https://www.tutorialspoint.com/neo4j/neo4j_cql_creating_relationship.htm<br>
