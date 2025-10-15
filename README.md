#### COMP3104 – Developer Operations


# GitHub Action Status Badge

[![CI](https://github.com/pritamworld/f2025_comp3104/actions/workflows/ci.yml/badge.svg)](https://github.com/pritamworld/f2025_comp3104/actions/workflows/ci.yml)

# Commit Msg Hook (Enforce Commit Message Format)
Ensures commit messages follow a specific pattern.
File: .git/hooks/commit-msg

```
# !/bin/sh
COMMIT_MSG_FILE=$1
COMMIT_MSG=$(cat $COMMIT_MSG_FILE)

if ! echo "$COMMIT_MSG" | grep -Eq "^(feat|fix|docs|style|refactor|test|chore): .+"; then
  echo "Commit message must follow the format: <type>: <description>"
  echo "Example: feat: add user authentication"
  exit 1
fi
```

# Pre-Commit Hook (Lint Code Before Commit)

Ensures that the code is linted before committing.
File: .git/hooks/pre-commit
```
# !/bin/sh
echo "Running pre-commit hook: Linting code..."
node --version
#  npm run lint
if [ $? -ne 0 ]; then
  echo "Linting failed. Fix errors before committing."
  exit 1
```

