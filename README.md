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

This was based on the 'Subtree merging' section of [Git Tools - Advanced
Merging](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging) in Pro Git.

The technique is also explained in [GitHub's
documentation](https://docs.github.com/en/get-started/using-git/about-git-subtree-merges)
and Alex Boffey's blog post [Combining Git repositories with Subtree
Merging](https://alexboffey.co.uk/blog/combining-git-repositories-using-subtree-merging/)
which are a bit more accessible than Pro Git.
