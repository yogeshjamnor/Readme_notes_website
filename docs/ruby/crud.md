# Ruby CRUD (ActiveRecord style)

Common CRUD patterns (Rails / ActiveRecord).

## CREATE

```rb
user = User.create!(email: \"a@example.com\", name: \"Asha\")
```
## READ

```rb
user = User.find(user_id)
users = User.where(active: true).order(created_at: :desc).limit(20)
```
## UPDATE

```rb
user.update!(name: \"New Name\")
```
## DELETE

```rb
user.destroy!
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
