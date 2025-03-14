# Манифест по сигналам

:warning: Исправления по названиям сигналов больше не принимаются.

Соединения внутри чипов производятся металлическими проводами, а иногда полисиликоновыми дорожками. Между собой соединения мы называем "сигналы", "шнурки", "шланги" или "тентакли".

В данном разделе находится разная информация по данной предметной области.

## Соглашения по названию

Названия сигналам давались в разное время, иногда даже когда ещё не совсем понятны были работы схем.

Поэтому иногда могут встречаться названия типа `LOL`, `MILF`, `WTF` и проч. Со временем мы стараемся дать сигналам нормальные названия.

Теперь немного про названия:
- Инверсную логику (там где она точно известна) отражает черточка в названии сигнала `/`, например `/T0`, `/ready`
- Иногда вместо черточки используется символ `#`, например `#PCL/PCL`
- Соединение двух частей схемы иногда обозначается как `A/B`, например `X/SB`
- Если сигнал является частью шины, то в конце указывается разряд, например `DB0`

Но в целом практика наименований довольно хаотичная, поэтому будьте готовы, например к такому, что `I/OAM2` означает не "соединить I и OAM2", а "init OAM2".

## Трудности с инверсией

Иногда не сразу понятно, что сигнал в инверсной логике. Поэтому, например, хотя сигнал и называется `SPR0HIT` - на самом деле он должен называться `/SPR0HIT` (в инверсной логике), но переименовывать его во всех местах уже не очень хочется, поэтому там где про него упоминается - дополнительно указывается, что на самом деле он в инверсной логике.

Также названия с символами `/` и `#` не подходят для Verilog, поэтому в Verilog вместо них используется приставка `n_`, например `n_ready`, `n_T0`.

## Процедура переименования

Нужно поменять по возможности все места, где упоминается переименуемый сигнал:

- Векторные маски из фотошопа
- Схемы для Logisim
- Странички BreakingNES Wiki (учесть также переводы на разные языки)

## 6502

Возникли вопросы по сигналу `BRK7`. Из описания 6502 - BRK-последовательность состоит из тактов T0-T6, поэтому из названия сигнала может показаться что откуда-то взялся цикл T7. Но нет, это просто аббревиатура `BRK7` :)

|Было|Стало|
|---|---|
|T5|T6 (RMW)|
|T6|T7 (RMW)|
|SBXY|#SBXY (инверсная полярность)|
|TRESX|#TRESX (инверсная полярность)|

## PPU

История исправлений:

|Было|Стало|
|---|---|
|BAKA|0/FIFO|
|MILF|OAMCTR2|
|WTF|SPR_OV|
|LOL|I2SEV|
|OMFG|Чтобы не переименовывать сигнал для аббревиатуры OMFG была придумана расшифровка - "OAM Mode Four". Определяет режим работы счётчика OAM (+1 / +4)|
|ASAP|Пока не понятно назначение сигнала|
|SH5, SH7|Были перепутаны|
|EXT0-3 OUT|/EXT0-3 OUT|
|SH2, SH3, SH5, SH7|/SH2, /SH3, /SH5, /SH7|
|CLK, /CLK|Были перепутаны|
|ZCOL0, ZCOL1|/ZCOL0, /ZCOL1|
|ZPRIO|/ZPRIO|
|SPR0HIT|/SPR0HIT|
|FVO0-2|/FVO0-2|
|CB/DB|#CB/DB (инверсная полярность)|
|DB/CB|#DB/CB (инверсная полярность)|
|DB/OB|OB/OAM|
|THZ,THZB|Попарно переименованы (THZ -> THZB, THZB -> THZ)|
|TVZ,TVZB|Попарно переименованы (TVZ -> TVZB, TVZB -> TVZ)|
|/OE|/WE (OAM Buffer Control)|
|F/NT|#F/NT (инверсная полярность)|
|PICTURE|/PICTURE (инверсная полярность)|
|x/EN|#x/EN (инверсная полярность), OAM FIFO|
|x/COL0, x/COL1|#x/COL0, #x/COL1 (инверсная полярность), OAM FIFO|
|Tx|/Tx (инверсная полярность), OAM FIFO|
|0/H|#0/H (инверсная полярность), OAM FIFO|
|0/FIFO|PD/FIFO|
|M4_OVZ|COPY_OVF|
|DDD|COPY_STEP|
|/I2|DO_COPY|
|I2SEV|/SPR0_EV|
|CLPB|/CLPB (инверсная полярность)|
|EVAL|/EVAL (инверсная полярность)|
|P123|PBLACK (Phase Shifter)|
|ROW,COL (OAM)|ROW -> COL, COL -> ROW (были перепутаны)  (#1343)|

## APU

|Было|Стало|
|---|---|
|FLOAD,FSTEP,SLOAD,SSTEP|DFLOAD,DFSTEP,DSLOAD,DSSTEP (DPCM)|
|FLOAD,FSTEP,LOAD,STEP,ERES,ESTEP|NFLOAD,NFSTEP,NLOAD,NSTEP,NERES,NESTEP (noise)|
|ENV0..3,VOL0..3,V0..3,ENVEN,ENVDIS|NENV0..3,NVOL0..3,NV0..3,NENVEN,NENVDIS (noise)|
|F0..3,NF0..10,RELOAD,ECO|NF0..3,NNF0..10,NRELOAD,NECO (noise)|
|FLOAD,FSTEP,LOAD,STEP,TSTEP|TFLOAD,TFSTEP,TLOAD,TSTEP,TTSTEP (triangle)|
|/ACLK2|/ACLK3A (square0)|
|/ACLK2|/ACLK3B (square1)|
|NOUT|/NOUT|
|MUTE|RNDOUT|
|LOAD|RLOAD (Square decay rate counter)|
|SWCTRL|SW_OVF (Sweep Unit)|
|SWEEP|SW_UVF (Sweep Unit)|
|ADDOUT|DO_SWEEP (Sweep Unit)|
|ACLK|/ACLK2|
|/ACLK|ACLK1|
|/ACLK2|ACLK2|
|/ACLK3|ACLK3|
|/ACLK4|ACLK4|
|/ACLK5|ACLK5|
