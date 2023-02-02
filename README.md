# reviews

Мегакорм:

1- Верстка:
-Отсутствует подход "БЭМ", при именовании классов используется CamelCase
-Неправильное использование семантических тегов (header, main, footer, section, article, h1-6, p и тд), а так же неправильная вложенность элементов.
- Изображения не обернуты в тег picture и не имеют альтернативных изображений для браузеров не поддерживающих webp. Так же изоражениям необходимо провести процедуру
  сжатия, например через сервис Squoosh, а так же задать размеры, на случай если файл стилизации не подгрузится.
- Раскоментировать необходимые теги, при отсутствии необходимости их в верстке - удалить.
- Метатеги description, keywords переполнены, необходимо отредактировать описание и ключевые слова для SEO.
- Favicon перевести в форма ico.
- При подключении тега link используется файл css где ведется разработка и минимизированная версия, оставить только сжатую версию.
2. CSS:
- Подлкюченный файл не разбит по компонентам (не минимизированная версия), сложно ориентироваться при необходимости внести исправления в проект.
- Блоки вываливаются из верстки
- Ломается шапка сайта на брейкпоинтах (1843px, 1483px)
- Неправильно подобраны z-index для элементов, блоки и элементы перекрывают друг друга.
- Шрифти подключены из папки fonts, предложил бы рассмотреть вариант cdn при наличии шрифта на google fonts, при отсутствии его там уже подключать ttf или woff2.
  Так как у большинства пользователей браузера не чистится кеш и шрифты могут быть уже подгружены - можно выиграть в скорости загрузки страницы.
- Не все элементы, с которыми может взаимодействовать пользователь имеют курсор pointer
- У большинства элементов отсутствуют состояния: hover и active.
- При стилизации предложил бы рассмотреть вариант не px для подбора размера шрифтов, блоков, элементов и тд, а vw для большей адаптивности контента.
3. JS:
- Удалить лишние выводы информации в консоль
- Добавить проверку наличия элемента на странице, если с ним происходят взаимодействия JS, а именно:
    а) Кнопки, например: if(document.querySelector(".класс кнопки")){слушатель события} - если будут добавлены дополнительные страницы и JS не найдет на второй
    странице эелемента - краш всего JS.
    б) Инпуты
    в) Кастомные селекты и тд.
- В местах, где используется innerHTML рассмотерть возможность замены на textContent, так как последний чуть производительней по скорости и если вывод информации
  производится многократно - можно выиграть в перспективе по скорости.
- У слайдера из библиотеки закоментирован autoplay, насколько помню он не на всех слайдерах этой библиотеки работает корректно, при необходимости можно заменить на:
  setInterval(() => {
      swiper.slideNext();
    }, 6000);
- То что касается анимаций я бы обсуждал предметно, а именно необходимость анимации на странице, например насколько те или иные анимации вообще актуальны и есть
  ли в них потребность.
