---
date: '2020/3/23 10:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Filtering Data
---

filtering data 

<!-- more -->

For data filtering, we'll use query parameters. This will allow clients to fetch all tasks, just the complete tasks, or just the incomplete tasks.

### Filtering Data

The `completed` query parameter is on the task documents of MongoDB. This query parameter can be set to `true` or `false`. This will prevent clients from fetching unnecessary data tha they don't plan on using.

First up, create an object to store the search criteria.
```
const match = {}
```

From there, check if the query parameter was provided. The provided value should be parsed into a boolean and stored on `match.completed`.

```
if (req.query.completed) {
  match.completed = req.query.completed === 'true'
}
```

Last up, `match` can be added onto `populate` to fetch just the users that match the search criteria.

```
await req.user.populate({
  path: 'tasks',
  match
}).exexPopulate()
```
<br>

```
// READ USER'S TASKS
// GET /tasks?completed=true
// GET /tasks?limit=10&skip=10
// GET /tasks?sortBy=createdAt:desc
router.get('/tasks', auth, async (req, res) => {
    const match = {}
    const sort = {}

    if (req.query.completed) {
        match.completed = req.query.completed === 'true'
    }

    if (req.query.sortBy) {
        const parts = req.query.sortBy.split(':')
        sort[parts[0]] = parts[1] === 'desc' ? -1 : 1
    }

    try {
        await req.user.populate({
            path: 'tasks',
            match,
            options: {
                limit: parseInt(req.query.limit),
                skip: parseInt(req.query.skip),
                sort
            }
        }).execPopulate();
        res.send(req.user.tasks);

    } catch (e) {
        res.status(500).send();
    }
})
```


출처 : NodeJS course on Udemy by Andrew Mead