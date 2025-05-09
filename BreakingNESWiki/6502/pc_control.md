# Управление счётчиком инструкций (PC)

![6502_locator_pc_control](/BreakingNESWiki/imgstore/6502/6502_locator_pc_control.jpg)

Схема управления счётчиком инструкций (PC) предназначена для формирования [команд управления](context_control.md) для обмена значением PC и внутренних шин ADL, ADH и DB.

Рядом находится схема инкремента PC, которая рассматривается в другом разделе, посвященном [диспатчеру](dispatch.md).

Транзисторная схема для получения промежуточных сигналов:

![pc_control_trans](/BreakingNESWiki/imgstore/6502/pc_control_trans.jpg)

Выходные защёлки и команды управления:

![pc_control_commands_tran](/BreakingNESWiki/imgstore/6502/pc_control_commands_tran.jpg)

Входные сигналы:

|Сигнал|Описание|
|---|---|
|BR0|Декодер X73. Дополнительно модифицирован сигналом /PRDY|
|BR2|Декодер X80|
|BR3|Декодер X93|
|T0|Приходит со счётчика циклов коротких инструкций|
|T1|Приходит со схемы инкремента PC (см. [диспатчер](dispatch.md))|
|ABS/2|Декодер X83. Дополнительно модифицирован сигналом Push/Pull (X129)|
|RTS/5|Декодер X84|
|JSR/5|Декодер X56|
|/ready|Глобальный внутренний сигнал готовности процессора|

Выходные сигналы:

|Сигнал|Описание|
|---|---|
|DL/PCH|Выходной вспомогательный сигнал для схемы [управления шинами](bus_control.md) DL/ADH|
|PC/DB|Выходной вспомогательный сигнал для схемы RW Control, которая входит в состав диспатчера|

Команды управления:

|Команда|Описание|
|---|---|
|ADH/PCH|Загрузить в защёлку PCHS значение шины ADH|
|PCH/PCH|Если не выполняется ADH/PCH, то выполняется эта команда (рефрешить PCH)|
|PCH/ADH|Записать значение регистра PCH на шину ADH|
|PCH/DB|Записать значение регистра PCH на шину DB|
|ADL/PCL|Загрузить в защёлку PCLS значение шины ADL|
|PCL/PCL|Если не выполняется ADL/PCL, то выполняется эта команда (рефрешить PCL)|
|PCL/ADL|Записать значение регистра PCL на шину ADL|
|PCL/DB|Записать значение регистра PCL на шину DB|

## Логическая схема

![pc_control_logisim](/BreakingNESWiki/imgstore/6502/pc_control_logisim.jpg)

## Оптимизированная логическая схема

![23_pc_control_logisim](/BreakingNESWiki/imgstore/6502/ttlworks/23_pc_control_logisim.png)
