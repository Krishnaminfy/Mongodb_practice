# Mongodb_practice

# pasting all the commands, I used to make the todo list and jira


# all the commands with data



C:\Users\Minfy.ADITYAREDDYDARA&gt;mongosh<br>
Current Mongosh Log ID: 6836cadc2229accdf06c4bcf<br>
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&amp;serverSelectionTimeoutMS=2000&amp;appName=mongosh+2.5.1<br>
Using MongoDB:          8.0.9<br>
Using Mongosh:          2.5.1<br>
<br>
For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/<br>
<br>
------<br>
   The server generated these startup warnings when booting<br>
   2025-05-28T11:51:28.416+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted<br>
------<br>
<br>
test&gt; show dbs<br>
admin           132.00 KiB<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
test&gt; use local<br>
switched to db local<br>
local&gt; use new_data<br>
switched to db new_data<br>
new_data&gt; db.records.insertOne({name:"krishna", age: 22})<br>
{<br>
todo&gt;<br>
  insertedId: ObjectId('6836ccb82229accdf06c4bd0')<br>
}<br>
new_data&gt; show dbs<br>
admin           132.00 KiB<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
new_data         40.00 KiB<br>
new_data&gt; use test<br>
switched to db test<br>
test&gt; show connections<br>
MongoshInvalidInputError: [COMMON-10001] 'connections' is not a valid argument for "show".<br>
test&gt; show collections<br>
<br>
test&gt; use new_data<br>
switched to db new_data<br>
new_data&gt; db.records.insertOne({name:"Suryatop", age: 21})<br>
{<br>
  acknowledged: true,<br>
  insertedId: ObjectId('6836cd2c2229accdf06c4bd1')<br>
}<br>
test&gt; use todo<br>
switched to db todo<br>
todo&gt; db.todos.insertMany([<br>
...   { /* item 1 */ },<br>
...   { /* item 2 */ }<br>
... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836e1c12229accdf06c4bd2'),<br>
    '1': ObjectId('6836e1c12229accdf06c4bd3')<br>
  }<br>
}<br>
todo&gt; db.list.insertMany([<br>
...   {<br>
...     "title": "Finish MongoDB setup",<br>
...     "description": "Install MongoDB server, configure authentication, and connect via Compass.",<br>
...     "dueDate": "2025-06-01T18:00:00Z",<br>
...     "priority": "high",<br>
...     "completed": false,<br>
...     "tags": ["mongodb", "setup"],<br>
...     "createdAt": "2025-05-28T12:00:00Z"<br>
...   },<br>
...   {<br>
...     "title": "Write Jenkins deployment pipeline",<br>
...     "description": "Create a scripted Jenkins pipeline to build and deploy the app.",<br>
...     "dueDate": "2025-06-03T15:00:00Z",<br>
...     "priority": "medium",<br>
...     "completed": false,<br>
...     "tags": ["jenkins", "ci/cd"],<br>
...     "createdAt": "2025-05-28T12:30:00Z"<br>
...   }<br>
... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836e1ed2229accdf06c4bd4'),<br>
    '1': ObjectId('6836e1ed2229accdf06c4bd5')<br>
  }<br>
}<br>
todo&gt; db.todo.find().pretty()<br>
<br>
todo&gt; db.find()<br>
TypeError: db.find is not a function<br>
todo&gt; use test<br>
switched to db test<br>
test&gt; db.todo.find().pretty()<br>
<br>
test&gt; use todo<br>
switched to db todo<br>
todo&gt; db.list.find().pretty()<br>
... (document output skipped for brevity)<br>
todo&gt; db.list.find()<br>
... (document output skipped for brevity)<br>
...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean<br>
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });<br>
... });<br>
<br>
...     let boolValue = !!doc.completed; // force any value to true/false<br>
...     db.list.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });<br>
... });<br>
test&gt; use todo<br>
switched to db todo<br>
...     print("Type of completed:", typeof doc.completed, "| Value:", doc.completed)<br>
... })<br>
Type of completed: boolean | Value: false<br>
Type of completed: boolean | Value: false<br>
<br>
...   { _id: ObjectId("6836e1ed2229accdf06c4bd5") },<br>
...   { $set: { status: true } }<br>
... )<br>
{<br>
  acknowledged: true,<br>
  insertedId: null,<br>
  matchedCount: 1,<br>
  modifiedCount: 1,<br>
  upsertedCount: 0<br>
}<br>
todo&gt; db.list.find().forEach((doc) =&gt; { print("Type of completed:", typeof doc.completed, "| Value:", doc.completed); })<br>
Type of completed: boolean | Value: false<br>
Type of completed: boolean | Value: false<br>
<br>
todo&gt; db.list.updateOne(<br>
...   { _id: ObjectId("6836e1ed2229accdf06c4bd5") },<br>
...   { $set: { completed: true } }<br>
... )<br>
{<br>
  acknowledged: true,<br>
  insertedId: null,<br>
  matchedCount: 1,<br>
  modifiedCount: 1,<br>
  upsertedCount: 0<br>
}<br>
...   { _id: ObjectId("6836e1ed2229accdf06c4bd4") },<br>
...   { $set: { completed: true } }<br>
... )<br>
{<br>
  acknowledged: true,<br>
  insertedId: null,<br>
  matchedCount: 1,<br>
  modifiedCount: 1,<br>
  upsertedCount: 0<br>
}<br>
jira&gt; use test<br>
switched to db test<br>
test&gt; use jira<br>
switched to db jira<br>
jira&gt; show dbs<br>
admin           132.00 KiB[COMMON-10001] 'db' is not a valid argument for "show".<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
new_data         72.00 KiB<br>
todo             56.00 KiB<br>
test&gt; show dbs<br>
admin           132.00 KiB<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
new_data         72.00 KiB<br>
todo             56.00 KiB<br>
test&gt; use jira<br>
switched to db jira<br>
jira&gt; db.user.insertMany([ ... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836eadc2229accdf06c4bd7'),<br>
    '1': ObjectId('6836eadc2229accdf06c4bd8'),<br>
    '2': ObjectId('6836eadc2229accdf06c4bd9')<br>
  }<br>
}<br>
jira&gt; db.projects.insertMany([ ... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': Object






