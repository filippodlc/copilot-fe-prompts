# Conventional Commits Prompt

## Commit Structure

Each commit message should follow the Conventional Commits format to ensure clarity and consistency in the project's history. The structure is as follows:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Fields

- **`<type>`**: Specifies the type of change being made (e.g., feature, fix, documentation).
- **`[optional scope]`**: A short, optional description of the section of the codebase affected (e.g., `auth`, `api`). The scope MUST be a noun describing a section of the codebase surrounded by parentheses.
- **`<description>`**: A concise summary of the change (imperative mood, lowercase). The description MUST immediately follow the colon and space after the type/scope prefix.
- **`[optional body]`**: Provides additional context or reasoning for the change. The body MUST begin one blank line after the description and may consist of multiple paragraphs.
- **`[optional footer(s)]`**: Includes metadata such as breaking changes or issue references. Each footer MUST consist of a word token, followed by either a `:<space>` or `<space>#` separator, followed by a string value.

### Types

- **feat**: A new feature that introduces functionality to the codebase. This correlates with a MINOR version in Semantic Versioning.
- **fix**: A bug fix that resolves an issue in the code. This correlates with a PATCH version in Semantic Versioning.
- **docs**: Changes to documentation only (e.g., README updates, inline comments).
- **style**: Code style changes that do not affect functionality (e.g., formatting, linting).
- **refactor**: Code changes that improve structure or readability without altering behavior.
- **perf**: Changes that enhance performance (e.g., optimizing algorithms, reducing memory usage).
- **test**: Adding or updating tests to ensure code reliability.
- **build**: Changes to the build process or dependencies (e.g., updating npm packages, modifying build scripts).
- **ci**: Updates to CI/CD configuration or scripts (e.g., GitHub Actions, Jenkins pipelines).
- **chore**: Miscellaneous tasks that do not modify source or test files (e.g., updating dependencies).
- **revert**: Reverts a previous commit, undoing its changes.

### Breaking Changes

Breaking changes MUST be indicated in one of the following ways:

1. By appending a `!` after the type/scope: `feat(api)!: change authentication protocol`
2. By including a `BREAKING CHANGE:` footer with a description:

   ```
   feat(api): change authentication protocol

   BREAKING CHANGE: The authentication protocol has been completely redesigned
   ```

Breaking changes correlate with a MAJOR version in Semantic Versioning, regardless of the commit type.

### Examples

#### Feature

```
feat(auth): add login functionality
```

Adds a new login feature to the authentication module.

#### Bug Fix

```
fix(api): resolve issue with data fetching
```

Fixes a bug where the API was not returning the correct data.

#### Documentation

```
docs(readme): update installation instructions
```

Improves the README by clarifying the steps for installation.

#### Refactor

```
refactor(core): simplify data processing logic
```

Refactors the core module to improve code readability and maintainability.

#### Breaking Change Examples

```
feat(api)!: change authentication protocol
```

Introduces a breaking change in the API's authentication protocol.

```
fix(auth): resolve token expiration issue

BREAKING CHANGE: The authentication token format has been updated.
```

Indicates a breaking change in the authentication token format, requiring updates in dependent systems.

#### Commit with Description and Breaking Change Footer

```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

#### Revert Commit Example

```
revert: feat(shipping): send an email to customers when a product is shipped

This reverts commit 676104e15534f7325a16ec3db8501908f02d73f2.
```

### Correcting Commit Mistakes

If you make a mistake with your commit type:

1. Before merging/releasing: Use `git rebase -i` to edit the commit history.
2. For a type that's in the spec but incorrect (e.g., using `fix` instead of `feat`): Follow your team's process for correction.
3. For a type not in the spec (e.g., `feet` instead of `feat`): Follow your team's process for correction.

### Benefits of Using Conventional Commits

- Automatically generates changelogs
- Automatically determines semantic version bumps
- Communicates the nature of changes to teammates and stakeholders
- Triggers build and publish processes
- Makes it easier for people to contribute to projects with a structured commit history
