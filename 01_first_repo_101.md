# First Repo 101

### How'd this page get here?

![Image 01_create_repo.png](/images/01_create_repo.png)

![Image 02_create_repo.png](/images/02_create_repo.png)

```bash
$ mkdir git-guide

$ cd git-guide/

git-guide $ echo "# git-guide" >> README.md

git-guide $ git init

Initialized empty Git repository in /git-guide/.git/
git-guide $ git add README.md

git-guide $ git commit -m "first commit"
[master (root-commit) 9d900c5] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

git-guide $ git remote add origin https://paentgit01.aaa-acg.net/ACG/git-guide.git

git-guide $ git push -u origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 224 bytes | 224.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://paentgit01.aaa-acg.net/ACG/git-guide.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

![Image 03_create_repo.png](/images/03_create_repo.png)

### If you found this page helpful, please read this next

- [GitHub 101](03_github_101.md) ( 03_github_101.md )