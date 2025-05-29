# Mongodb_practice

# pasting all the commands, I used to make the todo list and jira


C:\Users\Minfy.ADITYAREDDYDARA>mongosh
Current Mongosh Log ID: 6836cadc2229accdf06c4bcf
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.5.1
Using MongoDB:          8.0.9
Using Mongosh:          2.5.1

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/

------
   The server generated these startup warnings when booting
   2025-05-28T11:51:28.416+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

test> show dbs
admin           132.00 KiB
config          108.00 KiB
local            40.00 KiB
minfy-training    8.00 KiB
test> use local
switched to db local
local> use new_data
switched to db new_data
new_data> db.records.insertOne({name:"krishna", age: 22})
{
todo>
  insertedId: ObjectId('6836ccb82229accdf06c4bd0')
}
new_data> show dbs
admin           132.00 KiB
config          108.00 KiB
local            40.00 KiB
minfy-training    8.00 KiB
new_data         40.00 KiB
new_data> use test
switched to db test
test> show connections
MongoshInvalidInputError: [COMMON-10001] 'connections' is not a valid argument for "show".
test> show collections

test> use new_data
switched to db new_data
new_data> db.records.insertOne({name:"Suryatop", age: 21})
{
  acknowledged: true,
  insertedId: ObjectId('6836cd2c2229accdf06c4bd1')
}
test> use todo
switched to db todo
todo> db.todos.insertMany([
...   { /* item 1 */ },
...   { /* item 2 */ }
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6836e1c12229accdf06c4bd2'),
    '1': ObjectId('6836e1c12229accdf06c4bd3')
  }
}
todo> db.list.insertMany([
...   {
...     "title": "Finish MongoDB setup",
...     "description": "Install MongoDB server, configure authentication, and connect via Compass.",
...     "dueDate": "2025-06-01T18:00:00Z",
...     "priority": "high",
...     "completed": false,
...     "tags": ["mongodb", "setup"],
...     "createdAt": "2025-05-28T12:00:00Z"
...   },
...   {
...     "title": "Write Jenkins deployment pipeline",
...     "description": "Create a scripted Jenkins pipeline to build and deploy the app.",
...     "dueDate": "2025-06-03T15:00:00Z",
...     "priority": "medium",
...     "completed": false,
...     "tags": ["jenkins", "ci/cd"],
...     "createdAt": "2025-05-28T12:30:00Z"
...   }
...
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6836e1ed2229accdf06c4bd4'),
    '1': ObjectId('6836e1ed2229accdf06c4bd5')
  }
}
todo> db.todo.find().pretty()

todo> db.find()
TypeError: db.find is not a function
todo> use test
switched to db test
test> db.todo.find().pretty()

test> use todo
switched to db todo
todo> db.list.find().pretty()
[
  {
    _id: ObjectId('6836e1ed2229accdf06c4bd4'),
    title: 'Finish MongoDB setup',
    description: 'Install MongoDB server, configure authentication, and connect via Compass.',
    dueDate: '2025-06-01T18:00:00Z',
    priority: 'high',
    completed: false,
    tags: [ 'mongodb', 'setup' ],
    createdAt: '2025-05-28T12:00:00Z'
  },
  {
    _id: ObjectId('6836e1ed2229accdf06c4bd5'),
    title: 'Write Jenkins deployment pipeline',
    description: 'Create a scripted Jenkins pipeline to build and deploy the app.',
    dueDate: '2025-06-03T15:00:00Z',
    priority: 'medium',
    completed: false,
    tags: [ 'jenkins', 'ci/cd' ],
    createdAt: '2025-05-28T12:30:00Z'
  }
]
todo> db.list.find()
[
  {
    _id: ObjectId('6836e1ed2229accdf06c4bd4'),
    title: 'Finish MongoDB setup',
    description: 'Install MongoDB server, configure authentication, and connect via Compass.',
    dueDate: '2025-06-01T18:00:00Z',
    priority: 'high',
    completed: false,
    tags: [ 'mongodb', 'setup' ],
    createdAt: '2025-05-28T12:00:00Z'
  },
  {
    _id: ObjectId('6836e1ed2229accdf06c4bd5'),
    title: 'Write Jenkins deployment pipeline',
    description: 'Create a scripted Jenkins pipeline to build and deploy the app.',
    dueDate: '2025-06-03T15:00:00Z',
    priority: 'medium',
    completed: false,
    tags: [ 'jenkins', 'ci/cd' ],
    createdAt: '2025-05-28T12:30:00Z'
  }
]
...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });
... });

...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });
... });

...     let boolValue = !!doc.completed; // converts any truthy/falsy value to Boolean
...     db.todos.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });
... });

...     let boolValue = !!doc.completed; // force any value to true/false
...     db.list.updateOne({ _id: doc._id }, { $set: { completed: boolValue } });
... });

test> use todo
switched to db todo
...     print("Type of completed:", typeof doc.completed, "| Value:", doc.completed)
... })
Type of completed: boolean | Value: false
Type of completed: boolean | Value: false

...   { _id: ObjectId("6836e1ed2229accdf06c4bd5") },
...   { $set: { status: true } }
... )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.list.find().forEach((doc) => { print("Type of completed:", typeof doc.completed, "| Value:", doc.completed); })
Type of completed: boolean | Value: false
Type of completed: boolean | Value: false

todo> db.list.updateOne(
...   { _id: ObjectId("6836e1ed2229accdf06c4bd5") },
...   { $set: { status: true } }
... )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 0,
  upsertedCount: 0
}
todo> db.list.updateOne(
...   { _id: ObjectId("6836e1ed2229accdf06c4bd5") },
...   { $set: { completed: true } }
... )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
...   { _id: ObjectId("6836e1ed2229accdf06c4bd4") },
...   { $set: { completed: true } }
... )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
jira> use test
switched to db test
test> use jira
switched to db jira
jira> show dbs
admin           132.00 KiB[COMMON-10001] 'db' is not a valid argument for "show".
config          108.00 KiB
local            40.00 KiB
minfy-training    8.00 KiB
new_data         72.00 KiB
todo             56.00 KiB
test> show dbs
admin           132.00 KiB
config          108.00 KiB
local            40.00 KiB
minfy-training    8.00 KiB
new_data         72.00 KiB
todo             56.00 KiB
test> use jira
switched to db jira
jira> db.user.insertMany([
...   {
...     _id: ObjectId(),
...     username: "alice",
...     fullName: "Alice Johnson",
...     email: "alice@example.com",
...     role: "developer",
...     active: true,
...     createdAt: new Date()
...   },
...   {
...     _id: ObjectId(),
...     username: "bob",
...     fullName: "Bob Smith",
...     email: "bob@example.com",
...     role: "project_manager",
...     active: true,
...     createdAt: new Date()
...   },
...   {
...     _id: ObjectId(),
...     username: "carol",
...     fullName: "Carol Lee",
...     email: "carol@example.com",
...     role: "tester",
...     active: true,
...     createdAt: new Date()
...   }
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6836eadc2229accdf06c4bd7'),
    '1': ObjectId('6836eadc2229accdf06c4bd8'),
    '2': ObjectId('6836eadc2229accdf06c4bd9')
  }
}
jira>

jira>

jira> db.projects.insertMany([
...   {
...     _id: ObjectId(),
...     name: "Website Redesign",
...     description: "Revamp the company website with new branding and responsive design.",
...     startDate: new Date("2025-06-01"),
...     endDate: new Date("2025-09-30"),
...     status: "active",
...     createdBy: "bob",  // username of PM
...     createdAt: new Date()
...   },
...   {
...     _id: ObjectId(),
...     name: "Mobile App",
...     description: "Develop a mobile app for iOS and Android platforms.",
...     startDate: new Date("2025-07-15"),
...     endDate: new Date("2025-12-31"),
...     status: "planning",
...     createdBy: "bob",
...     createdAt: new Date()
...   }
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6836eadc2229accdf06c4bda'),
    '1': ObjectId('6836eadc2229accdf06c4bdb')
  }
}
jira>

jira>

jira> db.tasks.insertMany([
...   {
...     _id: ObjectId(),
...     title: "Design new homepage",
...     description: "Create wireframes and mockups for the new homepage.",
...     project: "Website Redesign",
...     assignedTo: "alice",
...     status: "in_progress",
...     priority: "high",
...     dueDate: new Date("2025-06-15"),
...     completed: false,
...     createdAt: new Date(),
...     comments: []
...   },
...   {
...     _id: ObjectId(),
...     title: "Set up CI/CD pipeline",
...     description: "Automate build and deployment processes for faster releases.",
...     project: "Mobile App",
...     assignedTo: "alice",
...     status: "todo",
...     priority: "medium",
...     dueDate: new Date("2025-08-01"),
...     completed: false,
...     createdAt: new Date(),
...     comments: []
...   },
...   {
...     _id: ObjectId(),
...     title: "Test login feature",
...     description: "Test login with valid and invalid credentials.",
...     project: "Website Redesign",
...     assignedTo: "carol",
...     status: "todo",
...     priority: "high",
...     dueDate: new Date("2025-06-20"),
...     completed: false,
...     createdAt: new Date(),
...     comments: []
...   }
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6836eadc2229accdf06c4bdc'),
    '1': ObjectId('6836eadc2229accdf06c4bdd'),
    '2': ObjectId('6836eadc2229accdf06c4bde')
  }
}
jira> use todo
switched to db todo
todo> db.list.updateOne( { _id: ObjectId("6836e1ed2229accdf06c4bd4") }, { $set: { completed: false } } )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.list.updateMany(
...   { completed: false },
...   { $set: { dueDate: new Date("2025-08-01") } }
... )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
todo>
todo> db.list.updateMany( { completed: false }, { $set: { dueDate: new Date("2026-08-01") } } )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
todo> db.list.countDocuments()
2
todo> db.list.updateMany(
...   {}, // matches all documents
...   {
...     $set: {
...       completed: false,
...       dueDate: new Date()
...     }
...   }
... )
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
todo>
  upsertedCount: 0
}
todo> const start = new Date();

todo> start.setHours(0, 0, 0, 0);
1748370600000
todo>

todo> const end = new Date();

todo> end.setHours(23, 59, 59, 999);
1748456999999
todo>

todo> // Query documents with dueDate within today's range

todo> db.list.find({
...   dueDate: {
...     $gte: start,
...     $lte: end
...   }
... }).pretty();
[
  {
    _id: ObjectId('6836e1ed2229accdf06c4bd4'),
    title: 'Finish MongoDB setup',
    description: 'Install MongoDB server, configure authentication, and connect via Compass.',
    dueDate: ISODate('2025-05-28T11:20:09.791Z'),
    priority: 'high',
    completed: false,
    tags: [ 'mongodb', 'setup' ],
    createdAt: '2025-05-28T12:00:00Z'
  },
  {
    _id: ObjectId('6836e1ed2229accdf06c4bd5'),
    title: 'Write Jenkins deployment pipeline',
    description: 'Create a scripted Jenkins pipeline to build and deploy the app.',
    dueDate: ISODate('2025-05-28T11:20:09.791Z'),
    priority: 'medium',
    completed: false,
    tags: [ 'jenkins', 'ci/cd' ],
    createdAt: '2025-05-28T12:30:00Z'
  }
]
todo> const now = new Date();

todo> const twentyMinutesAgo = new Date(now.getTime() - 20 * 60 * 1000);

todo>

todo> db.list.find({
...   createdAt: { $gte: twentyMinutesAgo }
... }).pretty();

todo> const twentyMinutesAgo = new Date(now.getTime() - 60 * 60 * 1000);

todo> db.list.find({ createdAt: { $gte: twentyMinutesAgo } }).pretty();

todo> const twentyMinutesAgo = new Date(now.getTime() - 100 * 60 * 1000);

todo> db.list.find({ createdAt: { $gte: twentyMinutesAgo } }).pretty();
