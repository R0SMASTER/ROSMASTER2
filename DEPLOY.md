# Деплой ROSMASTER на GitHub Pages + подключение домена

## Вариант А — за 3 минуты (рекомендую)

### 1. Создай репозиторий на GitHub
1. Зайди на https://github.com/new
2. Название: `ROSMASTER2`
3. Сделай **Public**, **не ставь** галочку "Add README"
4. Нажми **Create repository**

### 2. Залей файлы (выполни в терминале в папке проекта)

```bash
git init
git add .
git commit -m "feat: ROSMASTER VK style"
git branch -M main
git remote add origin https://github.com/USERNAME/ROSMASTER2.git
git push -u origin main
```
> Замени `USERNAME` на свой логин GitHub!
> Если спросит логин/пароль — используй Personal Access Token (Settings → Developer settings → Tokens).

### 3. Включи GitHub Pages
1. В репозитории зайди: **Settings → Pages**
2. В блоке **Build and deployment**:
   - Source: `Deploy from a branch`
   - Branch: `main` → `/ (root)` → **Save**
3. Через 1-2 минуты появится ссылка: `https://USERNAME.github.io/ROSMASTER2/`

### 4. Подключи свой домен rosmaster.ru
#### Если хочешь `rosmaster.ru` (без www):
У регистратора домена (REG.RU, Beget, Timeweb, Nic.ru) добавь 4 A-записи:

```
@   A   185.199.108.153
@   A   185.199.109.153
@   A   185.199.110.153
@   A   185.199.111.153
www CNAME USERNAME.github.io.
```

#### Если хочешь `www.rosmaster.ru`:
```
www CNAME USERNAME.github.io.
```

#### В GitHub:
1. Снова **Settings → Pages**
2. В поле **Custom domain** впиши: `rosmaster.ru` → **Save**
3. Поставь галочку **Enforce HTTPS** (появится через 5-30 минут после проверки DNS)

> Файл `CNAME` уже в репозитории, GitHub подхватит домен автоматически.

### 5. Проверка
- Подожди 5-30 минут (DNS)
- Открой https://rosmaster.ru — должен открыться сайт
- Проверь HTTPS (замок в браузере)

---

## Вариант Б — через GitHub Desktop (без терминала)
1. Скачай GitHub Desktop
2. File → Add Local Repository → выбери папку
3. Publish repository → выбери `ROSMASTER2` → Publish
4. Далее шаг 3 и 4 как выше.

---

## Частые проблемы

**404 на GitHub Pages?**
- Убедись что ветка `main` и папка `/ (root)`
- Подожди 2 минуты и обнови

**Домен не подключается?**
- Проверь A-записи (должно быть 4 штуки на 185.199.10x.153)
- Удали старые A-записи
- Пропиши CNAME для www

**HTTPS не включается?**
- Подожди до 1 часа, GitHub выпускает LetsEncrypt сертификат
- Убедись что DNS уже прорезолвился: `dig rosmaster.ru +short` должен показать 185.199...

**Нужно поменять домен?**
- Отредактируй файл `CNAME` (одна строка — твой домен)
- Закоммить и запушить: `git add CNAME && git commit -m "change domain" && git push`

---

## Что дальше?
- Поменять телефон: найди в `index.html` `+7 (495) 123-45-67` → замени на свой (4 места)
- Поменять почту: `info@masters-chas.ru`
- Подключить заявки: Telegram бот / Email (скажи — добавлю за 5 минут)
