## Error note for Github
- - -
#### Initial `git pull` Error
When making new projects in local and remote. <br>
You have to use `git pull` before pushing to remote origin/master using `git push`.<br>
Then the error comes like,

```
$ git pull origin master
-- fatal: refusing to merge unrelated histories
```

Special options are required,
```
$ git pull origin master --allow-unrelated-histories
```

reason of the error

>"git merge" used to allow merging two branches that have no common base by default, which led to a brand new history of an existing project created and then get pulled by an unsuspecting maintainer, which allowed an unnecessary parallel history merged into the existing project. The command has been taught not to allow this by default, with an escape hatch "--allow-unrelated-histories" option to be used in a rare event that merges histories of two projects that started their lives independently.

[ref](http://cpdev.tistory.com/51)

#####
