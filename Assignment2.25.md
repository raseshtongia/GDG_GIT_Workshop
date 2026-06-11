# Assignment 2.25 - Git Log And Branch Inspection

> Complete Assignment 2 before starting this. You already know how to create branches, commit, push, and raise PRs. This assignment teaches you how to inspect your work before you make bigger Git decisions.

## Goal

Learn one inspection command at a time. For every command, you will:

1. Ask a specific question.
2. Run the command.
3. Paste the command and output.
4. Write what you understood from that output.

Do not worry if the output looks noisy at first. The goal is to learn what to look for.

## Part 2.25.1 - Create Branches To Inspect

1. Checkout `develop` and pull the latest changes.
2. Create a branch named `inspection-practice` from `develop`.
3. Create a folder named `inspection` at the root.
4. Create `inspection/notes.md`.
5. Add a level 2 heading `Inspection Notes`.
6. Add these exact bullet points:
   - This file was created on the inspection-practice branch.
   - I will use Git commands to compare this branch with develop.
   - I will learn how to inspect commits before changing history.
7. Stage only `inspection/notes.md`.
8. Commit with message `add inspection practice notes`.
9. Push the `inspection-practice` branch.
10. **Do not raise a PR for `inspection-practice` yet. Do not merge it.** For this assignment, pushing only means sending the branch to GitHub so that we can inspect local and remote branches later.
11. Checkout `develop` again.
12. Create another branch named `inspection-extra` from `develop`.
13. Create `inspection/extra.md`.
14. Add a level 2 heading `Extra Inspection Notes`.
15. Add these exact bullet points:
   - This file was created on the inspection-extra branch.
   - This branch has a different file than inspection-practice.
   - I will inspect this branch before merging it.
16. Stage only `inspection/extra.md`.
17. Commit with message `add extra inspection notes`.
18. Push the `inspection-extra` branch.
19. **Do not raise a PR for `inspection-extra` yet. Do not merge it yet.** You will raise and merge the PR only in Part 2.25.4 after completing the inspection worksheet.

## Part 2.25.2 - Create Your Inspection Worksheet

1. Stay on the `inspection-extra` branch.
2. Create `inspection/history.md`.
3. Add this structure:

````md
## 1. Current State

### Question
Which branch am I on, and is my working tree clean?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 

## 2. Local Branches

### Question
Which branches exist on my machine?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 

## 3. Remote Branches

### Question
Which branches exist on GitHub remote?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 

## 4. Recent Commits

### Question
What commits happened recently on this branch?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 

## 5. Branch Graph

### Question
How do my branches relate to each other?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 

## 6. Difference From develop

### Question
What changed on inspection-extra compared to develop?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 

## 7. Inspect One Commit

### Question
What exactly did one specific commit change?

### Command And Output
```bash
paste command and output here
```

### My Answer
- 
````

> If Markdown code blocks inside the template feel confusing, create the headings first, then paste each command output under the matching heading.

## Part 2.25.3 - Answer Each Question With Commands

### 1. Current State

Question: Which branch am I on, and is my working tree clean?

Run:

```bash
git status
```

Paste the command and output under `## 1. Current State`.

Your answer should mention:

- current branch name
- whether there are untracked, modified, or staged files
- whether Git says the working tree is clean

### 2. Local Branches

Question: Which branches exist on my machine?

Run:

```bash
git branch
```

Paste the command and output under `## 2. Local Branches`.

Your answer should mention:

- which branch has the `*` symbol
- whether `develop`, `inspection-practice`, and `inspection-extra` are visible locally

### 3. Remote Branches

Question: Which branches exist on GitHub remote?

Run:

```bash
git branch -r
```

Paste the command and output under `## 3. Remote Branches`.

Your answer should mention:

- whether `origin/develop` is visible
- whether `origin/inspection-practice` and `origin/inspection-extra` are visible

### 4. Recent Commits

Question: What commits happened recently on this branch?

Run:

```bash
git log --oneline
```

Paste the command and output under `## 4. Recent Commits`.

Your answer should mention:

- the latest commit hash
- the latest commit message
- whether you can see your `add extra inspection notes` commit

### 5. Branch Graph

Question: How do my branches relate to each other?

Run:

```bash
git log --oneline --decorate --graph --all
```

Paste the command and output under `## 5. Branch Graph`.

Your answer should mention:

- whether multiple branch names appear in the graph
- whether `inspection-practice` and `inspection-extra` point to different commits
- why this graph is more useful than plain `git log --oneline`

### 6. Difference From develop

Question: What changed on `inspection-extra` compared to `develop`?

Run:

```bash
git diff develop..inspection-extra
```

Paste the command and output under `## 6. Difference From develop`.

Your answer should mention:

- which file was added or changed
- one line that Git shows as added
- why this command is useful before raising a PR

Now compare the other branch:

```bash
git diff develop..inspection-practice
```

Below your first answer, add one more bullet explaining how the `inspection-practice` diff is different from the `inspection-extra` diff.

### 7. Inspect One Commit

Question: What exactly did one specific commit change?

1. Pick the commit hash for `add extra inspection notes` from `git log --oneline`.
2. Run:

```bash
git show <commit-hash>
```

Paste the command and output under `## 7. Inspect One Commit`.

Your answer should mention:

- which commit hash you inspected
- which file the commit changed
- whether the output shows added lines with `+`

## Part 2.25.4 - PR And Merge

1. Stage only `inspection/history.md`.
2. Commit with message `record git inspection command outputs`.
3. Push the `inspection-extra` branch.
4. Raise a PR from `inspection-extra` to `develop`.
5. Merge only the `inspection-extra` PR into `develop`.
6. Do not merge `inspection-practice` yet.

## Expected Final State

- Branches `inspection-practice` and `inspection-extra` exist.
- `inspection-extra` has been merged into `develop`.
- `inspection-practice` is still unmerged.
- `inspection/history.md` contains all 7 question sections.
- Each section contains command output and a `My Answer` subsection.
- You can explain what `git status`, `git branch`, `git log`, `git diff`, and `git show` helped you inspect.

## Concepts Practiced

- `git status`
- `git branch`
- `git branch -r`
- `git log --oneline`
- `git log --oneline --decorate --graph --all`
- `git diff branch1..branch2`
- `git show <commit-hash>`
- Inspecting before changing history
