# spring_project
ІПЗ-22 Лєвшов Олександр
# Dean's Office System

## Функціональні вимоги

1. **Аутентифікація та авторизація користувачів:**
   - Користувачі (викладачі/співробітники та студенти) повинні мати можливість входити в систему за допомогою своїх облікових даних.
   - Система повинна розрізняти різні ролі користувачів (викладач/співробітник, студент) та надавати доступ відповідно до цих ролей.

2. **Подання запитів:**
   - Студенти повинні мати можливість подавати запити до деканату, вказуючи тип запиту, дату та опис.

3. **Управління запитами:**
   - Викладачі/співробітники повинні мати можливість переглядати, оновлювати та керувати запитами студентів.
   - Викладачі/співробітники можуть оновлювати статус запиту (наприклад, очікує, в процесі, вирішено).

4. **Відстеження журналу запитів:**
   - Система повинна вести журнал всіх дій, виконаних з запитом, включаючи співробітника, який обробляв запит, та результат запиту.

5. **Запит та видача сертифікатів:**
   - Студенти повинні мати можливість запитувати різні сертифікати через систему.
   - Викладачі/співробітники повинні мати можливість обробляти та видавати сертифікати, оновлюючи систему датою видачі та деталями сертифіката.

6. **Система сповіщень:**
   - Студенти повинні отримувати сповіщення, коли статус їхнього запиту змінюється.
   - Викладачі/співробітники повинні отримувати сповіщення про нові запити або запити на сертифікати.

7. **Управління профілем:**
   - Користувачі повинні мати можливість оновлювати інформацію свого профілю (контактні дані тощо).

8. **Звіти та аналітика:**
   - Система повинна генерувати звіти про кількість та типи запитів та виданих сертифікатів, а також про показники продуктивності викладачів/співробітників.

9. **Управління документами:**
   - Система повинна дозволяти студентам та співробітникам завантажувати та керувати документами, пов’язаними з запитами та сертифікатами.

10. **Аудит та історія:**
    - Система повинна зберігати повну історію всіх дій, пов’язаних із запитами та сертифікатами, для аудиторських цілей.

## REST API

| HTTP Метод | URL | Опис | Параметри запиту | Приклад відповіді |
|------------|-----|------|------------------|-------------------|
| **POST** | `/api/login` | Вхід користувача | `{ "username": "string", "password": "string" }` | `{ "token": "jwt_token", "role": "student/faculty" }` |
| **POST** | `/api/logout` | Вихід користувача | `{ "token": "jwt_token" }` | `{ "message": "Вихід успішний" }` |
| **POST** | `/api/inquiries` | Подання запиту | `{ "studentId": "string", "inquiryType": "string", "description": "string", "date": "YYYY-MM-DD" }` | `{ "inquiryId": "string", "status": "pending" }` |
| **GET** | `/api/inquiries` | Отримання запитів студента | `{ "studentId": "string" }` | `[ { "inquiryId": "string", "inquiryType": "string", "date": "YYYY-MM-DD", "status": "string" } ]` |
| **GET** | `/api/inquiries/{inquiryId}` | Отримання деталей запиту | None | `{ "inquiryId": "string", "studentId": "string", "inquiryType": "string", "description": "string", "date": "YYYY-MM-DD", "status": "string", "logs": [ { "logId": "string", "staffId": "string", "processingDate": "YYYY-MM-DD", "actions": "string", "result": "string" } ] }` |
| **PUT** | `/api/inquiries/{inquiryId}` | Оновлення статусу запиту | `{ "status": "string" }` | `{ "message": "Запит успішно оновлено" }` |
| **POST** | `/api/inquiries/{inquiryId}/log` | Додавання запису до журналу запиту | `{ "staffId": "string", "actions": "string", "result": "string", "processingDate": "YYYY-MM-DD" }` | `{ "logId": "string" }` |
| **POST** | `/api/certificates` | Запит на сертифікат | `{ "studentId": "string", "certificateType": "string", "details": "string" }` | `{ "certificateId": "string", "status": "pending" }` |
| **GET** | `/api/certificates` | Отримання сертифікатів студента | `{ "studentId": "string" }` | `[ { "certificateId": "string", "certificateType": "string", "issueDate": "YYYY-MM-DD", "status": "string" } ]` |
| **PUT** | `/api/certificates/{certificateId}` | Видача сертифіката | `{ "issueDate": "YYYY-MM-DD", "content": "string" }` | `{ "message": "Сертифікат успішно видано" }` |
| **POST** | `/api/notifications` | Надсилання сповіщення | `{ "userId": "string", "message": "string" }` | `{ "notificationId": "string" }` |
| **GET** | `/api/profile` | Отримання профілю користувача | `{ "userId": "string" }` | `{ "firstName": "string", "lastName": "string", "contactInfo": "string" }` |
| **PUT** | `/api/profile` | Оновлення профілю користувача | `{ "userId": "string", "firstName": "string", "lastName": "string", "contactInfo": "string" }` | `{ "message": "Профіль успішно оновлено" }` |
| **GET** | `/api/reports/inquiries` | Звіти про запити | `{ "startDate": "YYYY-MM-DD", "endDate": "YYYY-MM-DD" }` | `[ { "inquiryType": "string", "count": "number" } ]` |
| **GET** | `/api/reports/certificates` | Звіти про сертифікати | `{ "startDate": "YYYY-MM-DD", "endDate": "YYYY-MM-DD" }` | `[ { "certificateType": "string", "count": "number" } ]` |
| **POST** | `/api/documents` | Завантаження документу | `{ "relatedId": "string", "type": "inquiry/certificate", "document": "file" }` | `{ "documentId": "string", "uploadDate": "YYYY-MM-DD" }` |
| **GET** | `/api/documents/{relatedId}` | Отримання документів | None | `[ { "documentId": "string", "uploadDate": "YYYY-MM-DD", "fileUrl": "string" } ]` |
