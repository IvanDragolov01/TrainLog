# Проект: Мобилно приложение за управление на тренировки

## 1. Характеристики на базата данни (Структура и релации)

### **Основни таблици**
#### **Users (Потребители)**
- `ID` (уникален идентификатор)
- `email` (уникален, задължителен)
- `password` (хеширана парола)
- `full_name`
- `profile_picture`
- `phone`
- `birth_date`
- `weight_history` (ако се съхранява като запис с дати)
- `qualifications`
- `guardian_info` (ако е необходимо за деца)
- `visibility_settings` (определя кой може да вижда определени данни)

#### **Athletes (Трениращи)**
- `UserID` (референция към `Users`)
- `weight_history`
- `rank_history` (ако е бойно изкуство)
- `subscription_type`

#### **Coaches (Треньори)**
- `UserID` (референция към `Users`)
- `qualifications`
- `groups_led`

#### **Groups (Групи)**
- `ID`
- `name`
- `coach_id` (референция към `Coaches`)
- `athlete_list`

#### **Trainings (Тренировки)**
- `ID`
- `group_id` (референция към `Groups`)
- `date`
- `type`
- `participants_list`

#### **Attendance (Присъствия)**
- `ID`
- `athlete_id`
- `training_id`
- `status`

#### **Payments (Плащания)**
- `ID`
- `athlete_id`
- `type` (единично, седмично, месечно)
- `amount`
- `date`

#### **Events (Събития)**
- `ID`
- `name`
- `type`
- `date`
- `participants`

#### **Notifications (Известия)**
- `ID`
- `recipient_id`
- `message`
- `date`

---

## 2. Функционалност на приложението

### **Потребител (User)**
- Създаване и управление на акаунт (регистрация, вход, изход)
- Възстановяване на парола, смяна на имейл
- Настройки на профила
- Видимост на лични данни

### **Трениращ (Athlete)**
- Преглед на календара с тренировки
- Изпращане на заявка за членство в клуб
- Приемане на покани от треньори
- Деактивация при липса на активност (автоматична)
- Различни видове абонаменти (единично, седмично, месечно)
- Генериране на QR код/баркод за влизане в тренировка
- История на посещения и плащания

### **Треньор (Coach)**
- Управление на групи (добавяне/премахване на трениращи)
- Отбелязване на присъствия и плащания
- Повишаване на степен на трениращите
- Създаване на събития (изпити, състезания)
- Известия за неплатени такси
- Генериране на отчети за групи

### **Клубен Мениджър**
- Добавяне на извънредни събития
- Изпращане на важни съобщения
- Промяна на квалификации и степени

### **Собственик на клуб**
- Управление на всички аспекти на клуба

### **Системен Администратор**
- Управление на всички групи, треньори, трениращи
- Промяна на квалификации и роли
- Активиране/деактивиране на акаунти
- Преглед на отчети и статистики
- Управление на автоматични процеси и известия

### **Автоматизации**
- Автоматична деактивация на акаунти без група
- Автоматично отбелязване на валидност при плащане
- Известия за неплатени такси, предстоящи събития
- Напомняне за изтичащи квалификации

---

Така структурата и функционалностите са ясно разделени. 🚀 Ако искаш още подобрения или API endpoints, кажи ми! 😊
