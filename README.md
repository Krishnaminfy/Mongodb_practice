# Mongodb_practice

# pasting all the commands, I used to make the todo list and jira


# all the commands with data



C:\Users\Minfy.ADITYAREDDYDARA>mongosh<br>
Current Mongosh Log ID: 6836cadc2229accdf06c4bcf<br>
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.5.1<br>
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
test> show dbs<br>
admin           132.00 KiB<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
test> use local<br>
switched to db local<br>
local> use new_data<br>
switched to db new_data<br>
new_data> db.records.insertOne({name:"krishna", age: 22})<br>
{<br>
todo><br>
  insertedId: ObjectId('6836ccb82229accdf06c4bd0')<br>
}<br>
new_data> show dbs<br>
admin           132.00 KiB<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
new_data         40.00 KiB<br>
new_data> use test<br>
switched to db test<br>
test> show connections<br>
MongoshInvalidInputError: [COMMON-10001] 'connections' is not a valid argument for "show".<br>
test> show collections<br>
<br>
test> use new_data<br>
switched to db new_data<br>
new_data> db.records.insertOne({name:"Suryatop", age: 21})<br>
{<br>
  acknowledged: true,<br>
  insertedId: ObjectId('6836cd2c2229accdf06c4bd1')<br>
}<br>
test> use todo<br>
switched to db todo<br>
todo> db.todos.insertMany([<br>
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
todo> db.list.insertMany([<br>
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
...<br>
... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836e1ed2229accdf06c4bd4'),<br>
    '1': ObjectId('6836e1ed2229accdf06c4bd5')<br>
  }<br>
}<br>
todo> db.todo.find().pretty()<br>
<br>
todo> db.find()<br>
TypeError: db.find is not a function<br>
todo> use test<br>
switched to db test<br>
test> db.todo.find().pretty()<br>
<br>
test> use todo<br>
switched to db todo<br>
todo> db.list.find().pretty()<br>
[<br>
  {<br>
    _id: ObjectId('6836e1ed2229accdf06c4bd4'),<br>
    title: 'Finish MongoDB setup',<br>
    description: 'Install MongoDB server, configure authentication, and connect via Compass.',<br>
    dueDate: '2025-06-01T18:00:00Z',<br>
    priority: 'high',<br>
    completed: false,<br>
    tags: [ 'mongodb', 'setup' ],<br>
    createdAt: '2025-05-28T12:00:00Z'<br>
  },<br>
  {<br>
    _id: ObjectId('6836e1ed2229accdf06c4bd5'),<br>
    title: 'Write Jenkins deployment pipeline',<br>
    description: 'Create a scripted Jenkins pipeline to build and deploy the app.',<br>
    dueDate: '2025-06-03T15:00:00Z',<br>
    priority: 'medium',<br>
    completed: false,<br>
    tags: [ 'jenkins', 'ci/cd' ],<br>
    createdAt: '2025-05-28T12:30:00Z'<br>
  }<br>
]<br>
todo> db.list.find()<br>
[<br>
  {<br>
    _id: ObjectId('6836e1ed2229accdf06c4bd4'),<br>
    title: 'Finish MongoDB setup',<br>
    description: 'Install MongoDB server, configure authentication, and connect via Compass.',<br>
    dueDate: '2025-06-01T18:00:00Z',<br>
    priority: 'high',<br>
    completed: false,<br>
    tags: [ 'mongodb', 'setup' ],<br>
    createdAt: '2025-05-28T12:00:00Z'<br>
  },<br>
  {<br>
    _id: ObjectId('6836e1ed2229accdf06c4bd5'),<br>
    title: 'Write Jenkins deployment pipeline',<br>
    description: 'Create a scripted Jenkins pipeline to build and deploy the app.',<br>
    dueDate: '2025-06-03T15:00:00Z',<br>
    priority: 'medium',<br>
    completed: false,<br>
    tags: [ 'jenkins', 'ci/cd' ],<br>
    createdAt: '2025-05-28T12:30:00Z'<br>
  }<br>
]<br>
...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean<br>
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });<br>
... });<br>
<br>
...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean<br>
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });<br>
... });<br>
<br>
...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean<br>
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });<br>
... });<br>
<br>
...     let boolValue = !!doc.completed; // force any value to true/false<br>
...     db.list.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });<br>
... });<br>
<br>
test> use todo<br>
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
todo> db.list.find().forEach((doc) => { print("Type of completed:", typeof doc.completed, "| Value:", doc.completed); })<br>
Type of completed: boolean | Value: false<br>
Type of completed: boolean | Value: false<br>
<br>
todo> db.list.updateOne(<br>
...   { _id: ObjectId("6836e1ed2229accdf06c4bd5") },<br>
...   { $set: { status: true } }<br>
... )<br>
{<br>
  acknowledged: true,<br>
  insertedId: null,<br>
  matchedCount: 1,<br>
  modifiedCount: 0,<br>
  upsertedCount: 0<br>
}<br>
todo> db.list.updateOne(<br>
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
jira> use test<br>
switched to db test<br>
test> use jira<br>
switched to db jira<br>
jira> show dbs<br>
admin           132.00 KiB[COMMON-10001] 'db' is not a valid argument for "show".<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
new_data         72.00 KiB<br>
todo             56.00 KiB<br>
test> show dbs<br>
admin           132.00 KiB<br>
config          108.00 KiB<br>
local            40.00 KiB<br>
minfy-training    8.00 KiB<br>
new_data         72.00 KiB<br>
todo             56.00 KiB<br>
test> use jira<br>
switched to db jira<br>
jira> db.user.insertMany([<br>
...   {<br>
...     _id: ObjectId(),<br>
...     username: "alice",<br>
...     fullName: "Alice Johnson",<br>
...     email: "alice@example.com",<br>
...     role: "developer",<br>
...     active: true,<br>
...     createdAt: new Date()<br>
...   },<br>
...   {<br>
...     _id: ObjectId(),<br>
...     username: "bob",<br>
...     fullName: "Bob Smith",<br>
...     email: "bob@example.com",<br>
...     role: "project_manager",<br>
...     active: true,<br>
...     createdAt: new Date()<br>
...   },<br>
...   {<br>
...     _id: ObjectId(),<br>
...     username: "carol",<br>
...     fullName: "Carol Lee",<br>
...     email: "carol@example.com",<br>
...     role: "tester",<br>
...     active: true,<br>
...     createdAt: new Date()<br>
...   }<br>
... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836eadc2229accdf06c4bd7'),<br>
    '1': ObjectId('6836eadc2229accdf06c4bd8'),<br>
    '2': ObjectId('6836eadc2229accdf06c4bd9')<br>
  }<br>
}<br>
jira><br>
<br>
jira><br>
<br>
jira> db.projects.insertMany([<br>
...   {<br>
...     _id: ObjectId(),<br>
...     name: "Website Redesign",<br>
...     description: "Revamp the company website with new branding and responsive design.",<br>
...     startDate: new Date("2025-06-01"),<br>
...     endDate: new Date("2025-09-30"),<br>
...     status: "active",<br>
...     createdBy: "bob",  // username of PM<br>
...     createdAt: new Date()<br>
...   },<br>
...   {<br>
...     _id: ObjectId(),<br>
...     name: "Mobile App",<br>
...     description: "Develop a mobile app for iOS and Android platforms.",<br>
...     startDate: new Date("2025-07-15"),<br>
...     endDate: new Date("2025-12-31"),<br>
...     status: "planning",<br>
...     createdBy: "bob",<br>
...     createdAt: new Date()<br>
...   }<br>
... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836eb832229accdf06c4bda'),<br>
    '1': ObjectId('6836eb832229accdf06c4bdb')<br>
  }<br>
}<br>
jira><br>
<br>
jira> db.tasks.insertMany([<br>
...   {<br>
...     _id: ObjectId(),<br>
...     projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
...     title: "Design homepage",<br>
...     assignedTo: "alice",<br>
...     status: "in_progress",<br>
...     dueDate: new Date("2025-06-15"),<br>
...     createdAt: new Date()<br>
...   },<br>
...   {<br>
...     _id: ObjectId(),<br>
...     projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
...     title: "Implement responsive layout",<br>
...     assignedTo: "alice",<br>
...     status: "pending",<br>
...     dueDate: new Date("2025-06-30"),<br>
...     createdAt: new Date()<br>
...   },<br>
...   {<br>
...     _id: ObjectId(),<br>
...     projectId: ObjectId('6836eb832229accdf06c4bdb'),<br>
...     title: "Develop login screen",<br>
...     assignedTo: "carol",<br>
...     status: "pending",<br>
...     dueDate: new Date("2025-08-01"),<br>
...     createdAt: new Date()<br>
...   }<br>
... ])<br>
{<br>
  acknowledged: true,<br>
  insertedIds: {<br>
    '0': ObjectId('6836ebb52229accdf06c4bdc'),<br>
    '1': ObjectId('6836ebb52229accdf06c4bdd'),<br>
    '2': ObjectId('6836ebb52229accdf06c4bde')<br>
  }<br>
}<br>
jira><br>
<br>
jira> db.tasks.find({ assignedTo: "alice" }).pretty()<br>
[<br>
  {<br>
    _id: ObjectId('6836ebb52229accdf06c4bdc'),<br>
    projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
    title: 'Design homepage',<br>
    assignedTo: 'alice',<br>
    status: 'in_progress',<br>
    dueDate: ISODate('2025-06-15T00:00:00Z'),<br>
    createdAt: ISODate('2025-05-28T06:00:00Z')<br>
  },<br>
  {<br>
    _id: ObjectId('6836ebb52229accdf06c4bdd'),<br>
    projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
    title: 'Implement responsive layout',<br>
    assignedTo: 'alice',<br>
    status: 'pending',<br>
    dueDate: ISODate('2025-06-30T00:00:00Z'),<br>
    createdAt: ISODate('2025-05-28T06:00:00Z')<br>
  }<br>
]<br>
jira> db.tasks.updateOne(<br>
...   { _id: ObjectId('6836ebb52229accdf06c4bdc') },<br>
...   { $set: { status: "completed" } }<br>
... )<br>
{<br>
  acknowledged: true,<br>
  insertedId: null,<br>
  matchedCount: 1,<br>
  modifiedCount: 1,<br>
  upsertedCount: 0<br>
}<br>
jira> db.tasks.find({ assignedTo: "alice" }).pretty()<br>
[<br>
  {<br>
    _id: ObjectId('6836ebb52229accdf06c4bdc'),<br>
    projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
    title: 'Design homepage',<br>
    assignedTo: 'alice',<br>
    status: 'completed',<br>
    dueDate: ISODate('2025-06-15T00:00:00Z'),<br>
    createdAt: ISODate('2025-05-28T06:00:00Z')<br>
  },<br>
  {<br>
    _id: ObjectId('6836ebb52229accdf06c4bdd'),<br>
    projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
    title: 'Implement responsive layout',<br>
    assignedTo: 'alice',<br>
    status: 'pending',<br>
    dueDate: ISODate('2025-06-30T00:00:00Z'),<br>
    createdAt: ISODate('2025-05-28T06:00:00Z')<br>
  }<br>
]<br>
jira> db.tasks.deleteOne({ _id: ObjectId('6836ebb52229accdf06c4bdd') })<br>
{<br>
  acknowledged: true,<br>
  deletedCount: 1<br>
}<br>
jira> db.tasks.find().pretty()<br>
[<br>
  {<br>
    _id: ObjectId('6836ebb52229accdf06c4bdc'),<br>
    projectId: ObjectId('6836eb832229accdf06c4bda'),<br>
    title: 'Design homepage',<br>
    assignedTo: 'alice',<br>
    status: 'completed',<br>
    dueDate: ISODate('2025-06-15T00:00:00Z'),<br>
    createdAt: ISODate('2025-05-28T06:00:00Z')<br>
  },<br>
  {<br>
    _id: ObjectId('6836ebb52229accdf06c4bde'),<br>
    projectId: ObjectId('6836eb832229accdf06c4bdb'),<br>
    title: 'Develop login screen',<br>
    assignedTo: 'carol',<br>
    status: 'pending',<br>
    dueDate: ISODate('2025-08-01T00:00:00Z'),<br>
    createdAt: ISODate('2025-05-28T06:00:00Z')<br>
  }<br>
]<br>







