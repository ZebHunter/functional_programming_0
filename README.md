# Функциональное программирование lab0

- Выполнил: Рогачев М. С. P34082
- Преподаватель: Пенской А. В.
***

- Язык: OCaml
- Компилятор: ocamlopt
- Lint: [Merlin](https://ocaml.org/p/merlin/latest)
- Tool for formatting OCaml code: [OCamlFormat](https://ocaml.org/p/ocamlformat/latest)
- Система сборки: [dune](https://github.com/ocaml/dune)
- Тестирование: [ounit](https://ocaml.org/p/ounit2/latest)
- Книга: [Real World OCaml](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/052E4BCCB09D56A0FE875DD81B1ED571/9781009125802AR.pdf/Real_World_OCaml__Functional_Programming_for_the_Masses.pdf?event-type=FTLA)

## Введение
Чтобы получить сбалансированную оценку, почему я выбрал OCaml, нужно выделить несколько пунктов

1. Какими преимуществами обладает Ocaml

2. Что могут предложить другие функциональные языки

Но картина может оказаться неполной, поэтому к предыдущему списку стоит добавить еще один пункт

3. Какие недостатки при реализации задачи могут возникнуть, если писать ее на OCaml

Ну что ж, когда мы определились с целями, давайте начнем ресерч

## Часть 1 - OCaml

<div style="text-align: right"> 
<i>Programming languages matter. They affect the reliability, security, and efficiency of the code you write, as well as how easy it is to read, refactor, and extend. The languages you know can also change how you think, influencing the way you design software even when you’re not using them.
</i>
</div>


<div style="text-align: right"> 
 -- OCaml Documentation 
</div>

***

Чтобы не растягивать эту главу, давайте напишем основные особенности OCaml в формате перечисления:

- Производительность
- Строгая статическая типизация
- type inference
- Алгебраические типы данных и паттерн-матчинг
- Параметрические модули
- Возможность писать "грязно"

Читая материалы по OCaml, а в частности какие-никакие сравнения различных функциональных языков (насколько целесообразно вообще такие материалы читать, не имея конкретной области применения), можно придти к выводу, что основное преимущество OCaml - производительность (разработчики на OCaml говорят о невероятной производительности, сопоставимой с C, мы им конечно же верим)

Также я думаю, что в этом разделе нужно описать книги, которые можно использовать для изучения языка: 
1. "Real World OCaml" - весьма подробное, как мне показалось, описание возможностей языка с конкретными примерами. Для изучения я выбрал ее. Но есть еще варианты

2. "OCaml Programming: Correct + Efficent + Beautiful" - руководство для обучению OCaml в университетах, в котором довольно кратко описаны многие концепции с небольшими примерами. Эту книгу можно использовать для быстрого старта, поскольку темы описаны достаточно лаконично + примеры из данной книги представлены для обучения и старта на официальном сайте OCaml


## Часть 2 - Сравнение с другими языками

<div style="text-align: right"><i> Кто хочет стать водителем людей, должен в течение доброго промежутка времени слыть среди них их опаснейшим врагом.
</i>
</div>


<div style="text-align: right">
-- Ф. Ницше
</div>

***

Чтобы не плодить лишнего текста (ха-ха, все посмеялись), разобьем языки по условным семействам, которые будут +- характеризовать область их применения и характерные особенности

 ### OCaml vs Lisp-family
 - семейство lisp обладает весьма специфическим синтаксисом, представляющим огромное количество скобок и фактически описывают выражение как ast. Данный пункт является субъективным (как и все в данном эссе в принципе) 
 - динамическая типизация в lisp-подобных языках - по моему мнению это влечет за собой большее время дебага
 - Производительность - по синтетическим тестам и некоторым бенчмаркам OCaml превосходит в производительности Lisp

 ### OCaml vs Erlang & Elixir
 - Опять же Erlang является динамически типизированным языком, поэтому нет смысла повторяться
 - Эффективная система распараллеливания и отказоустойчивость Erlang. Поскольку я не предполагаю разрабатывать распределенные системы на OCaml, то данный пункт является достаточно проходным в плане сравнения, но показательным для особенностей языка ( также стоит упомянуть о фреймворке JoCaml, который предоставляет библиотеку для создания распределенных систем)
 - Стандартный пункт про производительность, опять же OCaml на бумаге быстрее

 ### OCaml vs Haskell
 - Во многом OCaml и Haskell схожи, например в строгой типизации, type inference. Одним из главных отличий является тот факт, что Haskell - pure-functional язык, т.е. не предполагает ухода от функциональной парадигмы, в отличие от OCaml, который предоставляет программисту возможность писать в разных стилях, что в некоторых случаях, возможно, дает OCaml дополнительную гибкость и возможность оптимизаций
 - Haskell обладает ленивой семантикой
 - Экосистема и сообщество. Haskell обладет большим сообществом => имеет более развитую экосистему. OCaml остается достаточно нишевым языком => меньшее количество библиотек и развитие языка происходит гораздо медленнее
 - Мое любимое - прозводительность. Тут вопрос более неоднозначный, поскольку данная тема уже более холиварная. Если судить по рассуждениям на форумах - программисты чаще в плане производительности отдают голос OCaml, в том числе на основе бенчмарков, но Haskell программисты оспаривают это решение
 
<b>Заключение по сравнению:</b> Из всего вышеописанного можно сделать вывод - выбор зависит от той предметной области и задачи, которая будет реализована. OCaml более ориентирован на эффективные однопоточные вычисления (возможно с версией 5.0 что-то изменилось за счет добавления многоядерности, но найти интересных примеров не удалось). Отсюда в этой нише возникают 2 языка - Haskell и OCaml. Если судить сугубо по производительности - OCaml побеждает на синтетических бенчмарках (опять же все зависит от программиста, написавшего код).

<b>P.S.</b>
 Сравнивать с языками типа Coq, Agda и Idris не вижу смысла, поскольку они имеют специфическую область применения и в рамках данного курса мне просто не интересны

## Часть 3 - Недостатки OCaml
<div style="text-align: right">
<i>"Можно прославиться и единственным недостатком" - успокаивали Ахиллеса коллеги"
</i>
</div>


<p style="text-align: right;">
-- цитата из Интернетов
</p>

***

OCaml не имеет встроенной поддержки многопоточности и параллельных вычислений. Это ограничивает возможности разработчиков при работе над высокопроизводительными задачами (насколько я знаю, начиная с OCaml 5.0 проблема многопоточности начала решаться)

Экосистема OCaml относительно небольшая по сравнению с популярными языками программирования. Это может ограничить выбор инструментов и библиотек для разработки


## Эпилог (лабораторная работа 4)

Есть идея написать эмулятор какой-нибудь старенькой платформы типа NES или Gameboy. Или же можно реализовать компилятор/транслятор и т.д. OCaml может подойти для данной задачи засчет высокой эффективности, паттерн-матчинга и алгебраических типов данных

### Источники
- https://ocaml.org
- [OCaml Programming: Correct + Efficent + Beautiful](https://cs3110.github.io/textbook/cover.html)
- https://www.haskell.org
- https://ru.wikipedia.org/wiki/Haskell
- https://en.wikipedia.org/wiki/Lisp_(programming_language)
- https://eax.me/haskell-vs-ocaml/
- https://gitlab.se.ifmo.ru/functional-programming/main/-/blob/master/slides/01-introduction.md
- https://www.cs.ubc.ca/~murphyk/Software/Ocaml/why_ocaml.html
- https://readmedium.com/evaluating-the-performance-of-ocaml-haskell-and-lisp-88e39ae602d7
- https://stackoverflow.com/questions/1310114/erlang-vs-ocaml-best-niche-to-fit
- https://ocaml.org/manual/5.2/api/Lazy.html
- https://www.linux.org.ru/forum/development/17691690/page1
- https://zeemly.com/compare/lisp-vs-ocaml
- https://dev.to/chshersh/8-months-of-ocaml-after-8-years-of-haskell-in-production-h96
- https://ocaml.org/p/ounit2/2.2.3/doc/index.html

