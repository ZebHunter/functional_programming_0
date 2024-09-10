# Функциональное программирование lab0

- Выполнил: Рогачев М. С. P34082
- Преподаватель: Пенской А. В.
***

- Язык: OCaml
- Компилятор: ocamlc
- Lint: [comby](https://github.com/comby-tools/comby)
- Tool for formatting OCaml code: [ocamlformat](https://ocaml.org/p/ocamlformat/latest)
- Система сборки: [dune](https://github.com/ocaml/dune)
- Тестирование: [ounit2](https://ocaml.org/p/ounit2/latest)
- Книга: [Real World OCaml](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/052E4BCCB09D56A0FE875DD81B1ED571/9781009125802AR.pdf/Real_World_OCaml__Functional_Programming_for_the_Masses.pdf?event-type=FTLA)

## Причина выбора

Я считаю, что сравнить каждый язык друг с другом задача неподъемная, тем более в короткие сроки, поэтому я начал выбирать методом исключения. Erlang и Elixir я откинул сразу, поскольку был небольшой опыт работы с ними и не хотелось снова в них погружаться. Coq, Agda и Idris я откинул из-за специфичной предметной области. Насчет Lisp-подобных языков: мне не очень нравится их синтаксис, поэтому, по большому счету, все свелось к 2 языкам - Haskell и OCaml. Я подумал, что много людей выберут Haskell и решил выбрать OCaml, поскольку когда если не сейчас попробовать что-то новое для себя в рамках учебного курса.


## Про 4 лабораторную работу

Есть идея написать эмулятор какой-нибудь старенькой платформы типа NES или Gameboy. OCaml может подойти для данной задачи засчет высокой эффективности (исходя из того, что прочитал про этот язык)


