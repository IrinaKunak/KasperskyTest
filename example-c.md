# Интерфейс компонента ServerStatRequester: #

```c++
namespace stat_requester
{
using StatisticType = std::string;
using StatisticTypes = std::vector<StatisticType>;
struct RawJsonStatistic
{
    // Название типа статистики, например, "TrendingThreats".
    StatisticType type;
    // Время, в течении которого данная статистика остается актуальной.
    std::chrono::hours timeToLive;
    // Содержимое статистики в JSON формате. Например:
    // {"top3": ["Clop Ransomware", "Cyborg Ransomware", "Zeus Gameover"]}
    std::string jsonContents;
};
using JsonStatisticsPacket = std::vector<RawJsonStatistic>;
using IpAddress = std::array<uint16_t, 8>;
struct IServerStatRequester
{
    using CompletionCallback =
std::function<void(uint32_t statusCode, JsonStatisticsPacket&& statistics)>;
    // Отправляет на сервер асинхронный запрос статистики. Когда приходит
ответ - вызывает callback на отдельном потоке.
    // В случае ошибки также вызывается callback, с соответствующим
statusCode.
    virtual void SendRequestAsync(IpAddress serverAddress, const StatisticTypes
& types, CompletionCallback&& callback) = 0;
};
}
```
