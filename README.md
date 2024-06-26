# A/B-контест от Samokat.tech

Решение попало в ТОП-20 лучших по результатам контеста 😀

## Постановка проблемы

Одна из проблем при привлечении продавцов на площадку маркетплейса — это регистрация неблагонадежных продавцов-мошенников.

Распространённая и самая известная на рынке схема мошенничества: мошенник берёт данные ИНН из открытых источников, регистрирует на него компанию на площадке маркетплейса. Далее выставляет ходовой товар на продажу, например iPhone 14, на 50% дешевле рынка. Когда покупатель оформляет заказ на маркетплейсе, продавец пишет покупателю, что у него есть другой сайт, где можно купить товар ещё дешевле. Покупатель соглашается и оплачивает заказ по ссылке продавца в обход площадки. После этого продавец пропадает. Покупатель остается без товара. Такие продавцы очень сильно портят репутацию маркетплейса, и необходимо их выявлять как можно быстрее, лучше всего в процессе регистрации.

Для этого ML-команда предложила к использованию модель по автоопределению продавцов-мошенников, которую нам предлагается внедрить в процесс регистрации продавца.

Мы хотим ввести новый функционал, но как data-driven компания не можем это сделать без тестирования и проверки качества новой функциональности через A/B-тест.

[Лендинг контеста](https://abcontest.matemarketing.ru/)

## Задачи

1. Описать методологию и дизайн теста: определить основную метрику (дополнительные метрики), принцип разделения на группы и рассчитать, какой эффект можно статистически значимо отследить.
2. Ответить на следующие вопросы:
   - Как определить, какой продавец мошенник, а какой — нет? Какие ещё могут быть схемы мошенничества?
   - Какие продуктовые фичи могут помочь нашим клиентам избежать неприятных ситуаций с мошенничеством?
   - Через какую механику мошенник узнает контакты покупателя? Что можем сделать, чтобы усложнить жизнь фродерам?

## Описание данных

- `registration_date` - дата регистрации (дата получения `merchant_id`, продавец зарегистрировался на площадке)
- `activation_date` - дата активации (продавец прошел все этапы регистрации и может продавать)
- `merchant_id` - id продавца
- `type` - форма организации бизнеса (IE — Индивидуальный предприниматель, LLC — Общество с ограниченной ответственностью)
- `ind_frod` - индекс мошенника (1 — мошенник, 0 — добросовестный продавец)

## Стек

Python (pandas, numpy, seaborn, matplotlib, scipy.stats, requests, urllib.parse), A/B-тестирование

## Результаты

- Провела EDA, обнаружила аномалии в данных и очистила датасет от них
- Задизайнила A/B-тест (обозначила метрики и гипотезы, стат. критерии, уровень значимости, мощность, длительность, размер выборки, MDE и провела А/А-тест)
- Определила то, как можно идентифицировать фродера, основные схемы мошенничества, какие продуктовые фичи можно внедрить и определила способы того, как мошенник может узнать контакты покупателя
