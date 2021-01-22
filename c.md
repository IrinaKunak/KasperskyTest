# KasperskyTest

## СТРУКТУРА ДЛЯ ЗАДАЧИ

Например, для «OnlineUsers» структура может выглядеть так

```c++
struct OnlineUsers: public StatisticBase
{
    uint64_t totalUsers;
    uint64_t onlineUsersNow;
    uint64_t onlineUsersAverage;
    //... other members/methods
};
```

## ПРИМЕР КОДА ДЛЯ ЗАДАЧИ

Соответственно, может быть написан такой код

```c++
OnlineUsers GetOnlineUsers(StatisticsProvider &provider)
{
    OnlineUsers stat;
    provider.GetStatistics(stat);
    return stat;
}
```
