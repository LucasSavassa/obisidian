- a query is simply text that obeys the sql syntax
- the data is stored in disk
- therefore, the database engine has to solve this problem:

>[!danger] **fundamental problem**
>what is the optimal way to access the disk and retrieve the queried data?

- step 1: parse the query
- step 2: build execution plan
- step 3: execution plan

> [!info] definition
> execution plan is the sequence of disk operations required to fetch the queried data

![](https://www.youtube.com/watch?v=O7AzUDogXsw)

![](https://www.youtube.com/watch?v=BxAj3bl00-o)

