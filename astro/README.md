# Astro, Vite (React) и Next.js

Выбор между Astro, Vite (React) и Next.js зависит от целей проекта: **Astro** идеален для контентных сайтов (быстрый старт, мало JS), **Vite + React** — для SPA и дашбордов, а **Next.js** — для сложных SSR-приложений с SEO. Astro работает на Vite и позволяет использовать React-компоненты. 

**Основные сценарии использования:**

- **[Astro](https://www.google.com/search?q=Astro&mstk=AUtExfDC_BQ8WY-oAjqbmFbE8sFGZ9t3pOB24nzab4LGcKa2nxhysODI4Uc3dr1h7J99T7FX1cb8iyXivIeObrzoz7HmM5ACZgIDGuJxpztv41VQ4Cjn_i-Ayw6Fp_H7pY_Qe1_uIONzm6dc0-eQkwSC5am8YotX9vKWmNJxuQmfUTUyS4g&csui=3&ved=2ahUKEwjZhsnjheuTAxWOkWoFHQQrKhIQgK4QegQIAxAB) (v6+):** Используйте для контентных сайтов, блогов, документации, где критична  скорость загрузки. Astro по умолчанию генерирует статический HTML,  отправляя минимум JS (островная архитектура).
- **[Vite + React](https://www.google.com/search?q=Vite+%2B+React&mstk=AUtExfDC_BQ8WY-oAjqbmFbE8sFGZ9t3pOB24nzab4LGcKa2nxhysODI4Uc3dr1h7J99T7FX1cb8iyXivIeObrzoz7HmM5ACZgIDGuJxpztv41VQ4Cjn_i-Ayw6Fp_H7pY_Qe1_uIONzm6dc0-eQkwSC5am8YotX9vKWmNJxuQmfUTUyS4g&csui=3&ved=2ahUKEwjZhsnjheuTAxWOkWoFHQQrKhIQgK4QegQIAxAD) (v8+):** Идеально для одностраничных приложений (SPA), панелей управления  (dashboard), внутренних инструментов, где не требуется серверный  рендеринг (SSR).
- **[Next.js](https://www.google.com/search?q=Next.js&mstk=AUtExfDC_BQ8WY-oAjqbmFbE8sFGZ9t3pOB24nzab4LGcKa2nxhysODI4Uc3dr1h7J99T7FX1cb8iyXivIeObrzoz7HmM5ACZgIDGuJxpztv41VQ4Cjn_i-Ayw6Fp_H7pY_Qe1_uIONzm6dc0-eQkwSC5am8YotX9vKWmNJxuQmfUTUyS4g&csui=3&ved=2ahUKEwjZhsnjheuTAxWOkWoFHQQrKhIQgK4QegQIAxAF) (v16+):** Лучший выбор для SEO-оптимизированных проектов, e-commerce, сайтов с  частым обновлением данных через SSR, ISR или для полнофункциональных  приложений (Full-stack). 

**Преимущества методов сборки:**

- **Astro:** «Островная архитектура» — статический сайт с возможностью вставки интерактивных компонентов React только там, где нужно.
- **Vite:** Очень быстрая скорость разработки и сборки (Rolldown/Rollup), минимальная настройка.
- **Next.js:** Гибкость (SSR, SSG, ISR), встроенная маршрутизация, API-маршруты. 

*Пример: перенос проекта с Next.js на Astro возможен для ускорения загрузки  контента, тогда как перенос с Vite на Next.js стоит делать, если SPA  вырос в сложный SEO-проект.* 

---



## Установка фреймворка Astro на Debian

Установка фреймворка Astro на Debian требует наличия Node.js. Самый простой способ — использовать [npm create astro@latest](https://docs.astro.build/ru/install-and-setup/) в терминале. Это создаст новый проект, установит зависимости и настроит TypeScript.  Предварительно обновите систему и установите последнюю версию Node.js  для совместимости. 

Пошаговая установка Astro

**Обновите пакеты Debian:**

```
sudo apt update && sudo apt upgrade -y
```

**Установите Node.js (необходимо не ниже v18.14.15):**
Рекомендуется использовать NodeSource для получения свежей версии.

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
```

**Создайте проект Astro:**
Запустите мастер установки в папке, где хотите создать сайт:

```
npm create astro@latest
```

- Следуйте подсказкам (установка зависимостей, TypeScript, Git).

**Запустите проект:**
Перейдите в созданную папку и запустите сервер разработки:

```
cd <имя_вашего_проекта>
npm install
npm run dev
```

После этого ваш сайт будет доступен по адресу `http://localhost:4321`. 



---



## Создание портфолио

https://astro.build/themes/details/portfolio/

Создание портфолио на [Astro](https://www.google.com/search?q=Astro&mstk=AUtExfDN6pvJr8eZ-Z2uVKioZJKU3VFVDAUWSvOgLZcusITWj5m361tT2j8xl_9mxbtvvuoZlF4O10ul_jqSPezJC67bBWjYqhqKB-m7wzH8bYk38OslFqodjwz8aYs2z7AKmntuHPyrjmxwOp0-I6xz2GqS5xosWdc3D6cydSiUb3SlAIRbdxZAl2GNE1k_v6tCcFssqT2q0NMY_yf5jeuqpxtl1U3c22KuRBm3iFquxGNt25iaR4EKZUri8OtU6qCdTCWLsJDEbPCb7lKheq_qDzft&csui=3&ved=2ahUKEwielqe0iuuTAxX4mGoFHXiiFfoQgK4QegQIARAB) — отличный выбор для быстрого и SEO-оптимизированного сайта. Используйте готовые темы из официальной библиотеки [Astro Themes](https://www.google.com/url?sa=i&source=web&rct=j&url=https://astro.build/themes/details/portfolio/&ved=2ahUKEwielqe0iuuTAxX4mGoFHXiiFfoQy_kOegQIARAC&opi=89978449&cd&psig=AOvVaw2CfsU1i6ilj-0c9msC9TAg&ust=1776178430028000), настройте `src/content` для проектов, настройте стили и разверните через [GitHub Pages](https://www.google.com/search?q=GitHub+Pages&mstk=AUtExfDN6pvJr8eZ-Z2uVKioZJKU3VFVDAUWSvOgLZcusITWj5m361tT2j8xl_9mxbtvvuoZlF4O10ul_jqSPezJC67bBWjYqhqKB-m7wzH8bYk38OslFqodjwz8aYs2z7AKmntuHPyrjmxwOp0-I6xz2GqS5xosWdc3D6cydSiUb3SlAIRbdxZAl2GNE1k_v6tCcFssqT2q0NMY_yf5jeuqpxtl1U3c22KuRBm3iFquxGNt25iaR4EKZUri8OtU6qCdTCWLsJDEbPCb7lKheq_qDzft&csui=3&ved=2ahUKEwielqe0iuuTAxX4mGoFHXiiFfoQgK4QegQIARAD) или [Vercel](https://www.google.com/search?q=Vercel&mstk=AUtExfDN6pvJr8eZ-Z2uVKioZJKU3VFVDAUWSvOgLZcusITWj5m361tT2j8xl_9mxbtvvuoZlF4O10ul_jqSPezJC67bBWjYqhqKB-m7wzH8bYk38OslFqodjwz8aYs2z7AKmntuHPyrjmxwOp0-I6xz2GqS5xosWdc3D6cydSiUb3SlAIRbdxZAl2GNE1k_v6tCcFssqT2q0NMY_yf5jeuqpxtl1U3c22KuRBm3iFquxGNt25iaR4EKZUri8OtU6qCdTCWLsJDEbPCb7lKheq_qDzft&csui=3&ved=2ahUKEwielqe0iuuTAxX4mGoFHXiiFfoQgK4QegQIARAE). 

**Пошаговый план создания:**

**Установка Astro:**

```
npm create astro@latest
```

Выберите базовый шаблон или скачайте понравившуюся тему (например, *Accessible Astro Starter*).

**Структура контента:** Используйте [Markdown/MDX](https://www.google.com/search?q=Markdown%2FMDX&mstk=AUtExfDN6pvJr8eZ-Z2uVKioZJKU3VFVDAUWSvOgLZcusITWj5m361tT2j8xl_9mxbtvvuoZlF4O10ul_jqSPezJC67bBWjYqhqKB-m7wzH8bYk38OslFqodjwz8aYs2z7AKmntuHPyrjmxwOp0-I6xz2GqS5xosWdc3D6cydSiUb3SlAIRbdxZAl2GNE1k_v6tCcFssqT2q0NMY_yf5jeuqpxtl1U3c22KuRBm3iFquxGNt25iaR4EKZUri8OtU6qCdTCWLsJDEbPCb7lKheq_qDzft&csui=3&ved=2ahUKEwielqe0iuuTAxX4mGoFHXiiFfoQgK4QegQIAxAF) в папке `src/content/projects/` для добавления описаний работ.

**Настройка темы:** Отредактируйте файлы в `src/pages` и `src/components` для кастомизации под ваш стиль.

**Сборка и Деплой:**

- Залейте проект на GitHub.
- Подключите репозиторий к Vercel или Netlify для автоматического деплоя. 

**Преимущества Astro для портфолио:**

- **Скорость:** Почти 0 JS на клиенте (Astro Islands).
- **SEO:** Идеально для видимости в поисковиках.
- **Удобство:** Легко управлять контентом через Markdown. 

