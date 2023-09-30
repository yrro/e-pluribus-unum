# Monorepo

We're going to merge the histories of three other projects into the `main`
branch of this new monorepo.

`project-a`'s history was combined with `main` like so:

```
$ git status
On branch main
nothing to commit, working tree clean

$ git merge -s ours --no-commit --allow-unrelated-histories project-a 
Automatic merge went well; stopped before committing as requested

$ git read-tree --prefix=project-a -u project-a

$ git status
On branch main
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
	modified:   README.md
	new file:   project-a/README.md
	new file:   project-a/project-a.sh

$ git commit -m 'Merge in project-a'
[main 0abcdef] Merge in project-a
```

Then the same was done for `project-b` and `project-c`.
