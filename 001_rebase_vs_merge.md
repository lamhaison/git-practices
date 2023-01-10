Demo instruction

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
```

# 6 - 001_rebase_vs_merge_combined-with-merge (merge without squash)
```
git checkout -b 001_rebase_vs_merge_combined-with-merge
```
