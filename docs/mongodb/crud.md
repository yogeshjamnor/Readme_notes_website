# MongoDB CRUD Operations

Basic data operations in the MongoDB shell (`mongosh`).

## 1. CREATE

```javascript
// Insert one document
db.users.insertOne({
  name: "Alice",
  age: 25,
  email: "alice@example.com"
})

// Insert many documents
db.users.insertMany([
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 35 }
])
```
## 2. READ

```javascript
// Find all documents
db.users.find()

// Find with filter
db.users.find({ name: "Alice" })

// Find with comparison ($gt, $lt, $gte, $lte)
db.users.find({ age: { $gt: 25 } })

// Find one document
db.users.findOne({ email: "alice@example.com" })

// Sorting and Limiting
db.users.find().sort({ age: -1 }).limit(5)
```
## 3. UPDATE

```javascript
// Update one document
db.users.updateOne(
  { name: "Alice" },
  { $set: { age: 26 } }
)

// Update many documents
db.users.updateMany(
  { age: { $lt: 30 } },
  { $set: { status: "young" } }
)

// Upsert (Insert if not found)
db.users.updateOne(
  { name: "Dave" },
  { $set: { age: 40 } },
  { upsert: true }
)
```
## 4. DELETE

```javascript
// Delete one document
db.users.deleteOne({ name: "Alice" })

// Delete many documents
db.users.deleteMany({ status: "young" })
```
## Indexes

```javascript
// Create index for performance
db.users.createIndex({ email: 1 }, { unique: true })
```
## Code Examples

### Find with projection + sort
```javascript
// mongosh
use mydb;

db.users
  .find({ status: "active" }, { name: 1, email: 1 })
  .sort({ createdAt: -1 })
  .limit(20);
```
### Basic aggregation
```javascript
db.orders.aggregate([
  { $match: { status: "paid" } },
  { $group: { _id: "$userId", total: { $sum: "$amount" } } },
  { $sort: { total: -1 } },
]);
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
