# Task 12

### Данные 
Датасет номер 2+2.1

### Дедлайн 
2022-12-07 00:00:00

### Количество баллов

140

### Задание 

**Внимание**. Эта задача очень приближена к реальной, поэтому, пожалуйста, воспользуйтесь логикой :)

Давайте теперь посмотрим на поведение инвесторов. Как мы знаем, деньги инвесторов не бесконечны, а еще инвесторы - тоже люди, и тоже иногда поддаются эмоциям. Но они все же более серьезные и систематичные ребята, чем кто-либо другой, поэтому они действуют, как правило, по определенной системе:

* В некоторых случаях, когда инвесторы дают кредит компании, они ставят для нее дедлайн. Впрочем, иногда они оказываются очень заняты, и просят помочь своих помощнииков, а те, как ни странно, совершают кучу ошибок.

* Когда инвестор дает компании кредит - мы считаем, что он начал в нее инвестировать, и будет это делать до тех пор, пока какая-то компания его не расстроит.

* В самом начале каждый инвестор, полный надежд, "вступает в игру" - то есть его `hope=100`.

* Инвестор может торговать на свои деньги - и на деньги компании. Это по факту разные счета, поэтому нас интересуют только траты инвестора - то есть все кредиты на сумму меньше 20000000.

* Когда инвестор выдает кредит, он возлагает на него какие-то надежды, и дальше есть варианты: 

 1. В случае, если кредит выплачивают в полной мере (или больше) в срок, инвестор получает эти очки надежды себе в плюс (к `hope`, конечно).
 2. Если кредит возвращают в срок, но номиналом меньше, чем брали, инвестор так же расстраивается и теряет половину от заявленных очков надежды. Так же, инвестор пугается, и перестает инвестирировать в самую дешевую на "старте игры" компанию из тех, в которые он когда-то решил инвестировать.
 3. Если кредит вовремя не выплачивают, инвестор очень расстраивается, и теряет двойное количество очков надежды. Помимо этого, инвестор очень сильно пугается и перестает инвестировать в компанию, в которую начал инвестировать раньше всех. 
 4. Если уже после дедлайна компания таки решается выплатить кредит, инвестор снова радуется, и получает половину от заявленных очков надежды (их уже даже сумма не волнует).

Само собой, есть общие правила на игру:

* Количество очков надежды не может быть меньше 0 - при нулевом значении инвестор покидает игру, и все его последующие инвестиции считаются ошибкой помощника (или ошибкой базы).

* Количество очков надежды так же не может быть больше 100.

* Инвесторы не всегда хотят ставить компании дедлайн - в таком случае работают только пункты 1 и 2 с `hope=5`. Такое же условие работает для транзакций, на которые нет записей в `credit_outcome`.

* Иногда помощники все путают, и заносят какую-то совсем не валидную информацию о дедлайнах (или о транзакциях в целом). Невалидной считается та информация, при которой выполнение условий кредита никак не возможно. Условия кредита могут быть выполнены только если:
 * Дата выдачи кредита меньше, чем срок его оплаты.
 * Срок оплаты находится хотя бы в нашем веке.
 
 Такие записи стоит игнорировать и считать соответствующие транзакции без дедлайна.

В конце концов, когда торги закончились, и записи перестали лететь в таблицу, не обанкротившихся инвесторов осталось не много. Ваша задача - узнать топ-3 инвесторов, у которых все все еще много надежды.

Формат ответа: "топ10 инвестор"-"количество компаний в которые он инвестирует в конце","топ11 инвестор"-"количество компаний в которые он инвестирует в конце","топ12 инвестор"-"количество компаний в которые он инвестирует в конце" 

Например:`11-24,142-31,115-2`
