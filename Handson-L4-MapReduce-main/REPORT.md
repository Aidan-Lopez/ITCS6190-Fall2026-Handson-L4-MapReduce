# Hands-on L4 — Report

**Name:Aidan Lopez**
**Student ID:801240291**
**Email:alopez@charlotte.edu**

---

## What I ran

The commands you used, in the order you used them. If you deviated from the steps in the
README, say where and why.

```bash

docker compose up -d
  
mvn clean package

docker cp target/WordCountUsingHadoop-0.0.1-SNAPSHOT.jar resourcemanager:/tmp/

docker cp shared-folder/input/data/input.txt resourcemanager:/tmp/

docker exec -it resourcemanager bash
cd /tmp

hadoop fs -mkdir -p /input/data
hadoop fs -put ./input.txt /input/data
hadoop fs -ls /input/data

hadoop jar /tmp/WordCountUsingHadoop-0.0.1-SNAPSHOT.jar \
  com.example.controller.Controller /input/data/input.txt /output

hadoop fs -cat /output/*

hdfs dfs -get /output /tmp/
exit

docker cp resourcemanager:/tmp/output/. shared-folder/output/

docker compose down

```

---

## Input and output

### My input dataset

```
One rainy afternoon, Maya found an old notebook hidden in the back of her grandfather’s closet. The notebook was filled with strange maps, unfinished stories, and notes about a small town that no longer appeared on modern maps. Curious, Maya packed some food, grabbed a flashlight, and followed the directions written on the first page. After several hours of walking through the forest, she discovered an abandoned road covered with leaves and moss. At the end of the road stood a tiny wooden house with a red door. Inside, Maya found hundreds of books stacked from the floor to the ceiling. Every book told a different story about the forgotten town, but the final page of every book was missing. Maya realized that the notebook she carried contained those missing pages. She spent the evening matching each page to the correct book, slowly rebuilding the history of a place that everyone else had forgotten.


```

### The output the job produced

Paste the contents of your output file here.

the	14
Maya	4
with	3
and	3
notebook	3
that	3
she	2
about	2
was	2
page	2
book	2
found	2
road	2
books	1
grabbed	1
matching	1
hours	1
wooden	1
page.	1
from	1
house	1
stood	1
Every	1
After	1
carried	1
realized	1
rainy	1
floor	1
spent	1
some	1
town,	1
leaves	1
packed	1
end	1
filled	1
book,	1
followed	1
modern	1
history	1
back	1
town	1
contained	1
moss.	1
hundreds	1
ceiling.	1
her	1
covered	1
unfinished	1
everyone	1
through	1
old	1
correct	1
else	1
flashlight,	1
several	1
afternoon,	1
closet.	1
final	1
notes	1
small	1
stories,	1
written	1
grandfather’s	1
One	1
pages.	1
food,	1
forgotten.	1
story	1
Inside,	1
The	1
dataset	1
evening	1
door.	1
different	1
place	1
Curious,	1
each	1
hidden	1
every	1
stacked	1
tiny	1
slowly	1
walking	1
first	1
directions	1
appeared	1
input	1
missing	1
missing.	1
but	1
abandoned	1
those	1
discovered	1
own	1
had	1
longer	1
Create	1
She	1
strange	1
told	1
forest,	1
red	1
your	1
maps.	1
forgotten	1
maps,	1
rebuilding	1

```

```

---

## What I observed

A few sentences on what happened while the job was running. Pick whatever you actually
noticed. Some things worth looking at:

- How long the map phase took compared with the reduce phase
- How many DataNodes showed as live at <http://localhost:9870>
- What the ResourceManager at <http://localhost:8088> showed during the run
- Whether the output ordering matched what you expected

While the MapReduce job was running, I observed the progress bar changing.
I also could see the job present, and other jobs from previous runs. When the program finished I saw the word count of each word in the input

---

## Problems and fixes

Anything that went wrong and what resolved it. Paste the actual error message. If nothing
went wrong, say so.


