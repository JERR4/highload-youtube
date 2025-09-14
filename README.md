# Проектирование высоконагруженных приложений

## 1. Тема и целевая аудитория
YouTube — это видеохостинг для загрузки, хранения, просмотра и распространения видеороликов, а также один из крупнейших сервисов для обмена контентом и взаимодействия с аудиторией.

### Функционал MVP

- Загрузка видео  
- Просмотр видео  
- Поиск видео  
- Комментирование видео  
- Оценка видео  
- Подписка на автора видео (канал)  
- Получение списка рекомендаций  

### Целевая аудитория

По данным на июнь 2025 года платформа имеет 2,7 млрд пользователей в месяц (MAU) [[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025).

Распределение целевой аудитории в зависимости от местоположения представлено в таблице:

| Страна    | MAU, млн                              |
| --------- | ------------------------------------- |
| Индия     | 491                                   |
| США       | 253                                   |
| Бразилия  | 144                                   |
| Индонезия | 143                                   |
| Мексика   | 83,6                                  |
| Япония    | 78,7                                  |
| Германия  | 65,5                                  |
| Вьетнам   | 62,3                                  |
| Филиппины | 57,7                                  |
| Турция    | 57,5                                  |

## 2. Расчет нагрузки

### Продуктовые метрики
| Метрика | Значение | Источник |
|---------|----------|----------|
|Месячная аудитория (MAU)|2,7 млрд|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Дневная аудитория (DAU)|122 млн|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Среднее время использования в день|48,7 минут|[[3]](https://www.shopify.com/blog/social-media-marketing-statistics)|
|Среднее время, проведённое в сервисе за 1 сессию|24 минуты|[[2]](https://www.semrush.com/seo/26309235)|
|Средняя продолжительность видео|11,7 минут|[[6]](https://www.statista.com/statistics/1026923/youtube-video-category-average-length/)|
|Общее количество видео| 5,1 млрд|[[7]](https://seo.ai/blog/how-many-videos-are-on-youtube)|
|Количество просмотров страниц за посещение|6,95-8,83|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025) [[2]](https://www.semrush.com/seo/26309235)
|Доля трафика с мобильных устройств|63%|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025) [[2]](https://www.semrush.com/seo/26309235)|
|Объём новых видео за день|720 млн часов|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Общее время просмотров за день|1 млрд часов|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Суммарное количество поисков за день|3,5 млрд|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Среднее соотношение комментариев к просмотрам|0,5%|[[4]](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them) [[5]](https://tubularlabs.com/blog/3-metrics-youtube-success/)|
|Среднее соотношение лайков к просмотрам|4%|[[4]](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them) [[5]](https://tubularlabs.com/blog/3-metrics-youtube-success/)|
|Среднее соотношение подписок к просмотрам|0,3–0,5%|[[4]](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them)|

### Технические метрики

#### Хранилище
#### Видео
В таблице выше представлено,что общее количество видео на платформе: 5,1 млрд, cредняя продолжительность видео: 11,7 минут.
Средний битрейт зависит от качества [[8]](https://support.google.com/youtube/answer/1722171?hl=en).
На основании полученных данных произведем расчет размера видео разного качества:

| Разрешение | Битрейт видео | Битрейт аудио | Суммарный битрейт | Размер видео (11,7 мин) |
|------------|---------------|---------------|-----------------|------------------------|
| 2160p (4K) | 40 Mbps       | 0,384 Mbps    | 40,384 Mbps     | ~5,61 ГБ               |
| 1440p (2K) | 16 Mbps       | 0,384 Mbps    | 16,384 Mbps     | ~2,27 ГБ               |
| 1080p      | 8 Mbps        | 0,384 Mbps    | 8,384 Mbps      | ~1,16 ГБ               |
| 720p       | 5 Mbps        | 0,384 Mbps    | 5,384 Mbps      | ~0,74 ГБ               |
| 480p       | 2,5 Mbps      | 0,384 Mbps    | 2,884 Mbps      | ~0,40 ГБ               |
| 360p       | 1 Mbps        | 0,384 Mbps    | 1,384 Mbps      | ~0,19 ГБ               |

  


## Источники
1. [Пользователи и демография YouTube 2025](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)
2. [Аналитика трафика YouTube — SEMrush](https://www.semrush.com/seo/26309235)
3. [Статистика использования соцсетей — Shopify](https://www.shopify.com/blog/social-media-marketing-statistics)
4. [Ключевые метрики YouTube-каналов — Pixel Valley Studio](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them)
5. [Три метрики успеха на YouTube — Tubular Labs](https://tubularlabs.com/blog/3-metrics-youtube-success/)
6. [Статистика продолжительности видео](https://www.statista.com/statistics/1026923/youtube-video-category-average-length/)
7. [Статистика количества видео по годам](https://seo.ai/blog/how-many-videos-are-on-youtube)
8. [Рекомендации по загружвемым видео](https://support.google.com/youtube/answer/1722171?hl=en)
