# Ruby Security

Security practices for Ruby web applications.

## 1. Dependencies

```bash
bundle audit check --update
```
## 2. CSRF (Rails)
- Keep CSRF protection enabled for browser sessions.

## 3. Strong parameters (Rails)
- Whitelist fields instead of mass-assigning everything.

## Code Examples

### Strong params pattern
```rb
def user_params
  params.require(:user).permit(:email, :name)
end
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
