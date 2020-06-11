## Git Hooks
Git hooks are scripts that Git executes before or after events such as: **commit**, **push**, and **receive**. Please read the [documentation](https://githooks.com/) to know more about Git Hooks

### Husky
We use Husky to implement Git Hook easily

Hook script that we used:
- **pre-commit**
- **pre-commit-msg**
- **commit-msg**
- **pre-push**

You can skip that hooks with `--no-verify`

Example:
``` bash
$ git commit -m 'messages' --no-verify
```
