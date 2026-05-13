# MongoDB CLI Commands

Essential commands for the `mongosh` shell.

## Connection Commands

```bash
# Connect to local instance
mongosh

# Connect with URI
mongosh "mongodb://localhost:27017"

# Connect with user/pass
mongosh -u <user> -p <pass> --authenticationDatabase admin
```
## Database Commands

```bash
show dbs             # List databases
use my_db            # Switch database
db                   # Show current database
db.dropDatabase()    # Delete current database
```
## Collection Commands

```bash
show collections               # List collections
db.createCollection("users")    # Create collection
db.users.drop()                 # Delete collection
```
## Administrative Commands

```bash
db.getUsers()                   # List users
db.stats()                      # Database statistics
db.serverStatus()               # Server status
db.currentOp()                  # List current operations
```
## Import / Export

```bash
# Export collection to JSON
mongoexport --db=my_db --collection=users --out=users.json

# Import JSON to collection
mongoimport --db=my_db --collection=users --file=users.json
```
## Useful Shortcuts

- `cls`: Clear screen in mongosh.
- `it`: Iterate through cursor results.
- `Tab`: Auto-complete commands and collection names.


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
