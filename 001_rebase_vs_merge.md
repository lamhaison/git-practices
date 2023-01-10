Demo instruction
Merging is a safe option that preserves the entire history of your repository, while rebasing creates a linear history by moving your feature branch onto the tip of main .

# 1 - 001_rebase_vs_merge (main branch)
```
git pull origin main
git checkout -b 001_rebase_vs_merge

touch 001_rebase_vs_merge.txt
echo "m1" >> 001_rebase_vs_merge.txt
git add 001_rebase_vs_merge.txt
git commit -m 'm1'
git push origin 001_rebase_vs_merge



echo "m2" >> 001_rebase_vs_merge.txt
git add 001_rebase_vs_merge.txt
git commit -m 'm2'
git push origin 001_rebase_vs_merge
```

# 2 - feature-branch

```
git push origin -d 001_rebase_vs_merge_feature
git branch -D 001_rebase_vs_merge_feature
git checkout -b 001_rebase_vs_merge_feature

echo "f1" >> 001_rebase_vs_merge_feature.txt
git add 001_rebase_vs_merge_feature.txt
git commit -m 'f1'
git push origin 001_rebase_vs_merge_feature
```

# 3 - 001_rebase_vs_merge (main branch)
```
git checkout 001_rebase_vs_merge
echo "m3" >> 001_rebase_vs_merge.txt
git add 001_rebase_vs_merge.txt
git commit -m 'm3'
git push origin 001_rebase_vs_merge
```


# 4 -feature-branch
```
git checkout 001_rebase_vs_merge_feature

echo "f2" >> 001_rebase_vs_merge_feature.txt
git add 001_rebase_vs_merge_feature.txt
git commit -m 'f2'
git push origin 001_rebase_vs_merge_feature
```


# 5 - 001_rebase_vs_merge_combined (merge with --squash)
```
git checkout 001_rebase_vs_merge
git checkout -b 001_rebase_vs_merge_combined
git push origin 001_rebase_vs_merge_combined

git merge --squash 001_rebase_vs_merge_feature
# Squash commit -- not updating HEAD
# Automatic merge went well; stopped before committing as requested
git commit -m '[update] - 001_rebase_vs_merge_combined and 001_rebase_vs_merge_feature merged'


git push origin 001_rebase_vs_merge_combined

commit b106943b8312c8a9ab219911555eeed22df42e69 (HEAD -> 001_rebase_vs_merge_combined, origin/001_rebase_vs_merge_combined)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 14:11:09 2023 +0700

    [update] - 001_rebase_vs_merge_combined and 001_rebase_vs_merge_feature merged

commit 977d8e3c1198b1e0504f096ebc8ebb641daf8b30 (origin/001_rebase_vs_merge, 001_rebase_vs_merge)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:48:44 2023 +0700

    m3

commit 0c80910222d12034710f9ea58e598b9cb555044f
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:43 2023 +0700

    m2

commit 13d18075859e5cee71be840bb2fa38ce42503170
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:01 2023 +0700

    m1

commit 4c8cbb1d3e281e80b1b6fbd1a73f0328e89db04c
Author: Son Lam <lamhaison@gmail.com>
Date:   Tue Jan 10 13:09:21 2023 +0700

    Initial commit

```

# 6 - 001_rebase_vs_merge_combined-with-merge (merge without squash)
```
git checkout 001_rebase_vs_merge
git checkout -b 001_rebase_vs_merge_combined-with-merge
git merge 001_rebase_vs_merge_feature
git push origin 001_rebase_vs_merge_combined-with-merge

admin@MacBook-Pro-cua-Admin git-practice % git log -10
commit b9a3f9a886a10ded1279e9deccbe7f2fb102a57f (HEAD -> 001_rebase_vs_merge_combined-with-merge, origin/001_rebase_vs_merge_combined-with-merge)
Merge: 977d8e3 9f445b9
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 14:21:44 2023 +0700

    Merge branch '001_rebase_vs_merge_feature' into 001_rebase_vs_merge_combined-with-merge

commit 9f445b91193c8a3f242ca4994bb892df5a94400a (origin/001_rebase_vs_merge_feature, 001_rebase_vs_merge_feature)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:51:06 2023 +0700

    f2

commit 977d8e3c1198b1e0504f096ebc8ebb641daf8b30 (origin/001_rebase_vs_merge, 001_rebase_vs_merge)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:48:44 2023 +0700

    m3

commit a7c3c2669c450e33a0e31298b96f42fb94f6ef2e
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:45:52 2023 +0700

    f1

commit 0c80910222d12034710f9ea58e598b9cb555044f
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:43 2023 +0700

    m2

commit 13d18075859e5cee71be840bb2fa38ce42503170
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:01 2023 +0700

    m1

commit 4c8cbb1d3e281e80b1b6fbd1a73f0328e89db04c
Author: Son Lam <lamhaison@gmail.com>
Date:   Tue Jan 10 13:09:21 2023 +0700

    Initial commit
    
```

# 7 - 6 - 001_rebase_vs_merge_combined-with-rebase

```
git push origin -d 001_rebase_vs_merge_combined-with-rebase
git branch -D 001_rebase_vs_merge_combined-with-rebase

git checkout 001_rebase_vs_merge_feature
git checkout -b 001_rebase_vs_merge_combined-with-rebase
git push origin 001_rebase_vs_merge_combined-with-rebase

git log -10
admin@MacBook-Pro-cua-Admin git-practice % git log -4
commit 9f445b91193c8a3f242ca4994bb892df5a94400a (HEAD -> 001_rebase_vs_merge_combined-with-rebase, origin/001_rebase_vs_merge_feature, origin/001_rebase_vs_merge_combined-with-rebase, 001_rebase_vs_merge_feature)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:51:06 2023 +0700

    f2

commit a7c3c2669c450e33a0e31298b96f42fb94f6ef2e
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:45:52 2023 +0700

    f1

commit 0c80910222d12034710f9ea58e598b9cb555044f
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:43 2023 +0700

    m2

commit 13d18075859e5cee71be840bb2fa38ce42503170
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:01 2023 +0700

    m1


git rebase 001_rebase_vs_merge

git log -10
admin@MacBook-Pro-cua-Admin git-practice % git log -10
commit cea7f1efa9d8db50e4131a3605f5dc4fb3ba2b01 (HEAD -> 001_rebase_vs_merge_combined-with-rebase)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:51:06 2023 +0700

    f2

commit 0409fb7c1c8d677cefc4c006ac95d88b0ea31d7e
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:45:52 2023 +0700

    f1

commit 977d8e3c1198b1e0504f096ebc8ebb641daf8b30 (origin/001_rebase_vs_merge, 001_rebase_vs_merge)
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:48:44 2023 +0700

    m3

commit 0c80910222d12034710f9ea58e598b9cb555044f
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:43 2023 +0700

    m2

commit 13d18075859e5cee71be840bb2fa38ce42503170
Author: Admin <lamhaison@gmail.com>
Date:   Tue Jan 10 13:41:01 2023 +0700

    m1

commit 4c8cbb1d3e281e80b1b6fbd1a73f0328e89db04c
Author: Son Lam <lamhaison@gmail.com>
Date:   Tue Jan 10 13:09:21 2023 +0700

    Initial commit



```

