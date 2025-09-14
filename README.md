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
|Общее количество каналов| 113,9 млн | [[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Количество просмотров страниц за посещение|6,95-8,83|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025) [[2]](https://www.semrush.com/seo/26309235)
|Доля трафика с мобильных устройств|63%|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025) [[2]](https://www.semrush.com/seo/26309235)|
|Объём новых видео за день|720 млн часов|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Общее время просмотров за день|1 млрд часов|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Суммарное количество поисков за день|3,5 млрд|[[1]](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)|
|Среднее соотношение комментариев к просмотрам|0,5%|[[4]](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them) [[5]](https://tubularlabs.com/blog/3-metrics-youtube-success/)|
|Среднее соотношение лайков к просмотрам|4%|[[4]](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them) [[5]](https://tubularlabs.com/blog/3-metrics-youtube-success/)|
|Среднее соотношение подписок к просмотрам|0,3–0,5%|[[4]](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them)|
|Среднее количество просмотров на видео|5 594|[[12]](https://tubularlabs.com/blog/average-youtube-views/)

### Технические метрики

#### Хранилище
#### Видео
В таблице выше представлено,что cредняя продолжительность видео: 11,7 минут.
Средний битрейт зависит от качества [[8]](https://support.google.com/youtube/answer/1722171?hl=en).
На основании полученных данных произведем расчет размера видео разного качества в соответствии с формулой:

$$
\text{Размер видео (ГБ)} = \frac{\text{Битрейт (Mbps)} \times \text{Длительность (сек)}}{8000}
$$

То есть для видео качеством 360p:

$$
\text{Размер видео (ГБ)} = \frac{\text{1 (Mbps)} \times \text{702 (сек)}}{8 \times 1024} ≈ \text{0,088 (ГБ)}
$$

Проведем аналогичные вычисления и для других форматов и представим полученный результат в виде таблицы:

| Разрешение | Битрейт видео (Mbps) | Размер видео (11,7 мин)(Гб) |
|------------|----------------------|-----------------------------|
| 2160p (4K) | 40                   | 3,43                        |
| 1440p (2K) | 16                   | 1,371                      |
| 1080p      | 8                    | 0,685                       |
| 720p       | 5                    | 0,428                       |
| 480p       | 2,5                  | 0,214                       |
| 360p       | 1                    | 0,086                       |

Самым популярным разрешением видео на сегодняшний день является 1080p [[9]](https://www.descript.com/blog/article/the-ultimate-guide-to-youtube-video-sizes). Будем производить расчет относительно него:

$$
\text{Общий размер всех видео}  = \text{0,685 (ГБ)} \times \text{5,1 (млрд)} ≈ \text{3,5 ЭБ}
$$

Чтобы учесть наличие более низких и более высоких разрешений (360p–4K), усредняем:

- видео в 480p / 720p занимают меньше места (0,3–0,6 от базового 1080p),

- видео в 1440p / 2160p (4K) занимают больше (2–5 от базового).

В среднем итоговый объём будет в 1,2–1,3 раза больше базового расчёта.

$$
\text{Итоговый общий объём} ≈ \text{4,5 ЭБ}
$$

#### Миниатюры

На YouTube существует возможность добавлять превью (миниатюры) к видео размером до 2 МБ [[10]](https://support.google.com/youtube/answer/72431?hl=en&co=GENIE.Platform%3DAndroid#zippy=%2Cimage-size-resolution). По официальной информации 90% видео имеют превью [[11]]. Таким образом:

$$
\text{Общий размер всех превью} = 2 \text{ МБ} \times 5,1 \text{ млрд видео} \times 0,9
$$

#### Комментарии

Среднее соотношение комментариев к просмотрам - 0,3–0,5%. Примем среднее значение - 0,4%. Среднее количество просмотров - 5 594. Значит, в среднем 1 видео имеет:

$$
\text{Количество комментариев на одно видео} = 5 594 \times 0,004 = 22,376
$$

Примем средний размер комментария за 250 байт. Тогда:

$$
\text{Общий размер всех комментариев} = 22,376 \times 250\text{ Б} \times 5,1 \text{ млрд видео} ≈ \text{25,9 ТБ}
$$

#### Каналы

На сегодняшний день существует приблизительно 115 млн каналов. Допустим, что:

- Баннер канала 6 МБ
- Логотип канала 1 МБ

Тогда:

$$
\text{Общий объем данных каналов} = 7\text{ МБ} \times 115 \text{ млн} ≈ \text{0,75 ПБ}
$$

Полученные результаты представим в сводной таблице:

#### Сводная таблица объёмов хранилища YouTube

| Тип данных | Количество | Средний размер | Общий объём | Общий объём (ПБ) |
|------------|------------|----------------|-------------|-----------------------|
| Видео (усреднённо, базовое 1080p + коррекция на другие разрешения) | 5,1 млрд | 0,685 ГБ | ~4,5 ЭБ | ~4608 ПБ |
| Превью (миниатюры, 90% видео, до 2 МБ) | 5,1 млрд | 2 МБ × 0,9 | ~8,5 ПБ | ~8,5 ПБ |
| Комментарии (среднее количество на видео 22, размер 250 Б) | 114 млрд | 250 Б | ~25,9 ТиБ | ~0,025 ПБ |
| Каналы (баннер + логотип) | 115 млн | 7 МБ | ~0,75 ПБ | ~0,75 ПБ |





## Источники
1. [Пользователи и демография YouTube 2025](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country_2025)
2. [Аналитика трафика YouTube — SEMrush](https://www.semrush.com/seo/26309235)
3. [Статистика использования соцсетей — Shopify](https://www.shopify.com/blog/social-media-marketing-statistics)
4. [Ключевые метрики YouTube-каналов — Pixel Valley Studio](https://pixelvalleystudio.com/pmf-articles/4-key-youtube-channel-statistics-and-how-to-calculate-them)
5. [Три метрики успеха на YouTube — Tubular Labs](https://tubularlabs.com/blog/3-metrics-youtube-success/)
6. [Статистика продолжительности видео](https://www.statista.com/statistics/1026923/youtube-video-category-average-length/)
7. [Статистика количества видео по годам](https://seo.ai/blog/how-many-videos-are-on-youtube)
8. [Рекомендации по загружвемым видео](https://support.google.com/youtube/answer/1722171?hl=en)
9. [Информация по размерам видео](https://www.descript.com/blog/article/the-ultimate-guide-to-youtube-video-sizes)
10. [Размеры ревью к видео](https://support.google.com/youtube/answer/72431?hl=en&co=GENIE.Platform%3DAndroid#zippy=%2Cimage-size-resolution)
11. [Советы по превью](https://support.google.com/youtube/answer/12340300?hl=en)
12. [Информация о среднем количестве просмотров](https://tubularlabs.com/blog/average-youtube-views/)
