ode-hw-01-cli
1. Отримуємо і виводимо весь список контактів у вигляді таблиці
Команда в терміналі: node index.js --action="list"

Приклад результату: https://monosnap.com/file/JSAZzEQsh4KWgaj2JYH5yNtKBrJ3W0

2. Отримуємо контакт по id
Команда в терміналі: node index.js --action="get" --id 05olLMgyVQdWRwgKfg5J6

Приклад результату: https://monosnap.com/file/x0pZH9YWyxL9wo4ntUkmKYOCE6ds1L

3. Додаємо контакт
Команда в терміналі: node index.js --action="add" --name Mango --email mango@gmail.com --phone 322-22-22

Приклад результату: https://monosnap.com/file/a4CcVqXeHsqIOtig9zGeoXO4a2IIIu

4. Видаляємо контакт
Команда в терміналі: node index.js --action="remove" --id qdggE76Jtbfd9eWJHrssH

Приклад результату: https://monosnap.com/file/RmoFtRIavFhpjAx8PdpzHj9sGpkQm7

5. Викликані всі команди в терміналі
Приклад результату: https://monosnap.com/file/Z1E27c8Y1i0bu7lPLbIs2uHWpfZRr5

Умови для виконання:
Крок 1
Ініціалізується npm в проекті
В корені проекту створи файл index.js
Постав пакет nodemon як залежність розробки (devDependencies)
В файлі package.json додай "скрипти" для запуску index.js
Скрипт start який запускає index.js за допомогою node
Скрипт dev який запускає index.js за допомогою nodemon
Крок 2
У корені проекту створи папку db. Для зберігання контактів завантаж і використовуй файл contacts.json, поклавши його в папку db.

У корені проекту створи файл contacts.js.

Зроби імпорт модулів fs і path для роботи з файловою системою
Створи змінну contactsPath і запиши в неї шлях до файлу contacts.json. Для складання шляху використовуй методи модуля path.
Додай функції для роботи з колекцією контактів. У функціях використовуй модуль fs та його методи readFile() і writeFile()
Зроби експорт створених функцій через module.exports
/*
 * Розкоментуйте і запиши значення
 * const contactsPath = ;
 */

// TODO: задокументувати кожну функцію
function listContacts() {
  // ...твій код
}

function getContactById(contactId) {
  // ...твій код
}

function removeContact(contactId) {
  // ...твій код
}

function addContact(name, email, phone) {
  // ...твій код
}
Крок 3
Зроби імпорт модуля contacts.js в файлі index.js та перевір працездатність функції для роботи з контактами.

Крок 4
В файлі index.js імпортується пакет yargs для зручного парса аргументів командного рядка. Використовуй готову функцію invokeAction() яка отримує тип виконуваної дії і необхідні аргументи. Функція викликає відповідний метод з файлу contacts.js передаючи йому необхідні аргументи.

// index.js
const argv = require("yargs").argv;

// TODO: рефакторить
function invokeAction({ action, id, name, email, phone }) {
  switch (action) {
    case "list":
      // ...
      break;

    case "get":
      // ... id
      break;

    case "add":
      // ... name email phone
      break;

    case "remove":
      // ... id
      break;

    default:
      console.warn("\x1B[31m Unknown action type!");
  }
}

invokeAction(argv);
Так само, ви можете використовувати модуль commander для парсинга аргументів командного рядка. Це більш популярна альтернатива модуля yargs

const { Command } = require("commander");
const program = new Command();
program
  .option("-a, --action <type>", "choose action")
  .option("-i, --id <type>", "user id")
  .option("-n, --name <type>", "user name")
  .option("-e, --email <type>", "user email")
  .option("-p, --phone <type>", "user phone");

program.parse(process.argv);

const argv = program.opts();

// TODO: рефакторить
function invokeAction({ action, id, name, email, phone }) {
  switch (action) {
    case "list":
      // ...
      break;

    case "get":
      // ... id
      break;

    case "add":
      // ... name email phone
      break;

    case "remove":
      // ... id
      break;

    default:
      console.warn("\x1B[31m Unknown action type!");
  }
}

invokeAction(argv);
Крок 5
Запусти команди в терміналі і зроби окремий скріншот результату виконання кожної команди.

# Отримуємо і виводимо весь список контактів у вигляді таблиці (console.table)
node index.js --action="list"

# Отримуємо контакт по id
node index.js --action="get" --id=5

# Додаємо контакт
node index.js --action="add" --name="Mango" --email="mango@gmail.com" --phone="322-22-22"

# Видаляємо контакт
node index.js --action="remove" --id=3
Крок 6 - Здача домашнього завдання.
Скріншоти виконання команд, можна залити на будь-який безкоштовний хмарний сервіс зберігання картинок (Приклад: monosnap, imgbb.com) і відповідні посилання необхідно додати в файл README.md. Створіть цей файл в корені проекту.

Критерії прийому
Створено репозиторій з домашнім завданням — CLI додаток
Код відповідає технічному завданню проекту
При виконанні коду не виникає необроблених помилок
Назва змінних, властивостей і методів починається з малої літери і записуються в нотації CamelCase. Використовуються англійські іменники
Назва функції або методу містить дієслово
У коді немає закоментованих ділянок коду
Проект коректно працює з актуальною LTS-версією Node