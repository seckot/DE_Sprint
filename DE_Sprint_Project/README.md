**Проект № 1.**

Анализ публикуемых новостей

	Общая задача: создать ETL-процесс формирования витрин данных для анализа публикаций новостей.

## Подробное описание задачи:

### Разработать скрипты загрузки данных в 2-х режимах:
	1. Инициализирующий – загрузка полного слепка данных источника
	2. Инкрементальный – загрузка дельты данных за прошедшие сутки


### Организовать правильную структуру хранения данных
	- Сырой слой данных
	- Промежуточный слой
	- Слой витрин

### В качестве результата работы программного продукта необходимо написать скрипт, который формирует витрину данных следующего содержания:

	- Суррогатный ключ категории
	- Название категории
	- Общее количество новостей из всех источников по данной категории за все время
	- Количество новостей данной категории для каждого из источников за все время
	- Общее количество новостей из всех источников по данной категории за последние сутки
	- Количество новостей данной категории для каждого из источников за последние сутки
	- Среднее количество публикаций по данной категории в сутки
	- День, в который было сделано максимальное количество публикаций по данной новости
	- Количество публикаций новостей данной категории по дням недели

### Источники:
- [https://lenta.ru/rss/](https://lenta.ru/rss/ "https://lenta.ru/rss/")
- [https://www.vedomosti.ru/rss/news](https://www.vedomosti.ru/rss/news "https://www.vedomosti.ru/rss/news")
- [https://tass.ru/rss/v2.xml](https://tass.ru/rss/v2.xml "https://tass.ru/rss/v2.xml")


### Обновление новостей производиться раз в сутки, с помощью bat файла и планировщика задач в ОС Windows:

- [https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/bat/cron.bat](https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/bat/cron.bat "https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/bat/cron.bat")
	- В Планировщике заданий наводим мышкой на Библиотеку планировщика и кликаем правой кнопкой мыши, чтобы появилось меню. Там выбираем пункт: Создать простую задачу…
	- В появившемся окне зададим имя скрипту. После чего кликаем на кнопку Далее.
	- В следующем окне выберем как часто хотим запускать наш скрипт, в нашем случае выберем ежедневно. И вновь жамкаем на кнопку Далее.
	- На следующем шаге укажем время, в которое хотим запускать наш python-скрипт.
	- Выберем какую задачу хотим выполнить, в нашем примере — это Запустить программу.
	- В следующем окне укажем, расположение созданного нами файл с расширением .bat.

### Иницилизация новостей и загрузка первичных данных происходит с помощью py скрипта.
- [https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/initiating_download_news.py](https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/initiating_download_news.py "https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/initiating_download_news.py")
#### Слой сырых данных представлен в csv файле
- [https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/out/raw_news_data.csv](https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/out/raw_news_data.csv "https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/out/raw_news_data.csv")
### Обновление новостей и обновление первичных данных происходит с помощью py скрипта.
- [https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/news_updater.py](https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/news_updater.py "https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/news_updater.py")
#### Слой Инкрементальных данных представлен в csv файле
- [https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/out/news_intermediate_layer.csv](https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/out/news_intermediate_layer.csv "https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/out/news_intermediate_layer.csv")
### Формирование витрины данных с помощью py скрипта
- [https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/data_mart.py](https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/data_mart.py "https://github.com/seckot/DE_Sprint/blob/main/DE_Sprint_Project/src/data_mart.py")
