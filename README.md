# twitter

При реализации проекта через html запросы возникла проблема, в ответе на get запрос получал лишь обрывок кода страницы, в которой не было необходимой информации.
Думаю, это связано с тем, что на сайте присустствуют скрипты, которые динамически подгружают страницу по мере необходимости.
Так же в браузере я пытался найти, какие дополнительные запросы отправляются с сайта, чтобы вписать их в скрипт, но найти мне их не удалось.
Поэтому я реализовал парсер не через html запрос, а через selenium.webdriwer, имитируя работу с сайтом через браузер.
Алгоритм прокручивает страницу и улавливает посты как объекты, за тем переходит по ним, откуда берется необходимая информация.

Скрипт достаточно схож с сеансом обычного пользователя.

Так же, есть пара костылей, которые я использовал:
1) метод sleep вместо WebDriverWait для временного бездействия скрипта.
2) Цикл на перебор 10 твиттов по индексу. Из-а этого некоторые твитты могут пролистываться, поскольку твитты, которые ушли далеко вверх в ленте при обновлении 
страницы не загружаются. Эту проблему можно исправить, перехватывая id каждого твита, и проверять все загруженные твитты каждую итерацию цикла, чтобы они были уникальными, 
но на сайте twitter очень тяжело устроен html код, и было достаточно сложно вытащить оттуда данные, поскольку, например, по одному названию класса могут лежать и данные,
которые совершенно не нужны для поставленной задачи. Но эта задача реализуема, и в случае необходимости я готов ее доделать.

Для запуска скрипта запустить файл main.py
Используется браузер Chrome
