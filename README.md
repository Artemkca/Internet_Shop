Завдання: Створення системи керування замовленнями для інтернет-магазину
Опис бізнес-потреби:

Компанія, що займається роздрібною торгівлею, прагне автоматизувати процеси обробки замовлень та взаємодії з клієнтами через сучасну та гнучку систему. Важливим є впровадження архітектури, яка може масштабуватись, щоб підтримати зростаючу базу користувачів та продуктів, з можливістю додавати нові функціональні можливості без значного впливу на інші частини системи.

Щоб забезпечити це, було вирішено реалізувати мікросервісну архітектуру, що дозволить обробляти різні бізнес-операції через незалежні сервіси.

Вимоги до рішення:
Потрібно розробити систему, що складатиметься з трьох мікросервісів:

UserService (Сервіс користувачів)

Керує інформацією про користувачів, включаючи реєстрацію, перегляд профілів і обробку запитів на отримання даних.
Повинен надавати можливість запитувати інформацію про конкретного користувача за його ID.
ProductService (Сервіс продуктів)

Керує каталогом продуктів, що доступні для замовлення. Включає функціонал для перегляду доступних продуктів та їх деталей (назва, ціна тощо).
Повинен дозволяти отримання інформації про конкретний продукт за його ID.
OrderService (Сервіс замовлень)

Обробляє замовлення, що роблять користувачі, включаючи створення замовлення, перегляд замовлень та перевірку наявності користувача й продукту.
Під час створення замовлення система повинна здійснювати запити до UserService для перевірки існування користувача, та до ProductService для підтвердження наявності продукту й його ціни.
Бізнес-процеси:
Клієнт оформлює замовлення:

Клієнт вибирає продукти з каталогу.
Клієнт підтверджує замовлення через інтерфейс замовлень.
OrderService перевіряє, чи існує користувач у системі через UserService, та чи доступний продукт через ProductService.
Якщо дані коректні, замовлення створюється і зберігається у базі даних.
Адміністратор переглядає замовлення:

Адміністратори можуть переглядати замовлення користувачів, перевіряти їх статус і змінювати стан обробки.
Адміністратори також можуть керувати каталогом продуктів та користувачами через відповідні мікросервіси.
Архітектурні вимоги:
Кожен мікросервіс повинен бути незалежним і взаємодіяти з іншими через HTTP-запити.
Мікросервіси мають бути здатні розширюватись та масштабуватись незалежно один від одного.
Усі сервіси мають логувати операції, щоб забезпечити прозорість у разі виникнення помилок або необхідності аудиту дій.
Можливість майбутнього розширення, наприклад, додавання сервісу для обробки платежів або керування доставкою.
Технічна реалізація:
UserService:

Забезпечує CRUD операції для користувачів.
API: GET /api/user/{id} для отримання даних користувача.
ProductService:

Керує списком продуктів, надає доступ до деталей продукту.
API: GET /api/product/{id} для отримання деталей продукту.
OrderService:

Керує замовленнями користувачів.
API: POST /api/order для створення замовлення.
Використовує HTTP-клієнт для отримання даних з UserService та ProductService.
Мета:
Запропоноване рішення дозволить компанії ефективно обробляти великі обсяги замовлень, забезпечуючи надійну інтеграцію між різними бізнес-функціями (робота з клієнтами, продукти та замовлення). Завдяки мікросервісній архітектурі, компанія зможе легко додавати нові функції, масштабувати сервіси і підтримувати безперервну роботу системи без значного впливу на інші її частини.
