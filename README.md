# Способ установки вручную в пробирку

Приведенные манипуляции верны *только* текущей версии edx (Ginkgo).

1. Найдя за пределами пробирки директорию `themes` (непосредственно под той директорией где живет `Vagrantfile`) отправляемся туда и командуем:

        git clone https://github.com/kursitet/mccme2 mccme2

    В результате, все файлы которые считаются частью темы и могут быть отредактированы и отправлены наверх, будут жить в `themes/mccme2`.
    
2. Войдя в пробирку, открываем файл `/edx/app/edxapp/lms.env.json` и вносим в него следующие изменения:

        "COMPREHENSIVE_THEME_DIRS": [
	    "/edx/app/edxapp/themes"
        ],
        "ENABLE_COMPREHENSIVE_THEMING": true,

    Эти строки в файле уже есть, их надо изменить.

3. Запускам lms, переходим по адресу нашего сайта http://{our_URL}/admin.
   Напротив вкладки *Site themes*, нажимаем кнопку *добавить*.
   В выпадающем списке *Site*, выбираем доступный вариант.
   В поле *Theme dir name* выставляем *mccme2*
   Нажимаем кнопку *Сохранить*.

## Дополнительные сведения

1. Директорией `css` не пользуемся, только `sass`. Весь css применяемый внутри должен соответствовать правилам [SASS](http://sass-lang.com/) и будет скомпилирован по результатам, поэтому мы по крайней мере точно знаем что все sass-файлы загруженные из `lms/static/sass/_overrides.scss` загружаются в последнюю очередь и перебьют все остальное что они там понарисовали.
2. Редактируем шаблоны очень осторожно, потому что на них висит неприлично много функционала, и с каждым обновлением нам все придется переносить в новую версию. В идеале, все изменения вообще должны быть реализованы без изменений в html, хотя это конечно мечты.

