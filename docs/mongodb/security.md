# MongoDB Security Checklist

Essential security practices for MongoDB databases.

## 1. Authentication & Authorization
- [ ] **Enable Auth**: Ensure `--auth` is enabled in `mongod.conf`.
- [ ] **Strong Passwords**: Use complex passwords for all users.
- [ ] **RBAC**: Create specific users with limited roles (e.g., `readWrite`, `dbAdmin`).

## 2. Network Security
- [ ] **Bind IP**: Only bind to internal network interfaces (e.g., `127.0.0.1` or internal LAN).
- [ ] **Default Port**: Change the default port (27017) to something less common if possible.
- [ ] **TLS/SSL**: Encrypt all traffic between the application and the database.
- [ ] **IP Whitelisting**: Use firewalls or MongoDB Atlas whitelisting to restrict access.

## 3. Data Protection
- [ ] **Encryption at Rest**: Use encrypted storage engines (WiredTiger supports this).
- [ ] **Field Level Encryption**: Encrypt sensitive fields (like SSNs) before storing them.

## 4. Monitoring & Auditing
- [ ] **Enable Auditing**: Track operations and authentication attempts.
- [ ] **Profiling**: Monitor for suspicious slow queries.

## 5. Security Tools & Commands
```javascript
// Check for users and their roles
use admin
db.getUsers()

// Audit system status
db.hostInfo()
```
## 6. Atlas Security (Cloud)
- [ ] **MFA**: Enable Multi-Factor Authentication for the Atlas dashboard.
- [ ] **VPC Peering**: Connect your app cluster to the DB cluster securely.

> [!CAUTION]
> Never expose your MongoDB instance directly to the public internet without a firewall and strong authentication.


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
## Extra security notes (copy‑ready)

### Enable auth + use least privileges
```javascript
// mongosh (conceptual)
use admin;
// Create user with only required roles for the app database
```
### Avoid operator injection
- Never pass untrusted JSON directly into query filters
- Validate/whitelist allowed fields and operators


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
