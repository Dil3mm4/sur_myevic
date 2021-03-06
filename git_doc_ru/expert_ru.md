### Меню Эксперт

Настройки, требующие понимания, что, зачем и когда их нужно менять.  
Отвечать за последствия только вам самим.
Обозначение иконок этого меню: 
++++            ++++++++++++++++++++++++++++++++

  * __BVO__

    Меню напряжения батарей.  
    Рекомендуется откалибровать показания перед использованием мода с программным контролем заряда (все много-батарейные моды и Pico 25).

    В зависимости от модели мода и характеристик схемы, измеренное модом напряжение батарей может отличаться от реального.
    Это может привести к неверным результатам при работе: 
    - мод может раньше времени заблокировать парение, когда в батарейке еще есть заряд;
    - может перезапускаться при реальной просадке батарейки (однобатарейные моды), не зная точного состояния аккума;
    - может пытаться продолжать заряжать батарею, когда она уже полностью заряжена (только в модах с программным контролем заряда);

    Полность зарядите батарейки во внешнем зарядном устройстве. Используя мультиметр выполните измерения напряжений на банках. 
    Вставьте батарейки в бокс и выполните корректировку, если требуется.  
    Для модов со встроенными батарейками затруднительно узнать их реальное напряжение, без вскрытия мода.
    При разряде аккумов их показания могут плавать друг относительно друга, с этим ничего не поделаешь.

    Пределы корректировки каждого из установленных аккумов +-1.00 Вольт с шагом 10 мВ.  

  * __X32__
    
    Он же LXT, 32768 Hz генератор.
    Включить или выключить поддержку этого точного генератора.  
    Для некоторых глюкавых боксов с аппаратными часами выключение этого генератора спасало от фризов.  
    Если бокс не может использовать этот кристалл для часов реального времени, то эта настройка выключится и включится режим Легкого сна (LSL).  
    *Эта опция бесполезна и выключается, если в боксе физически отсутствует данный гернератор.*  

  * __LSL__
  
    Режим легкого сна.  
    *Этот режим бесполезен и по умолчанию выключен, если в боксе есть поддержка X32 генератора. И по умолчанию включен, если поддержки нет.*  
    В этом режиме часы реального времени будут всегда поддерживаться достаточно точным генератором HIRC ( 12 MHz ) вместо не точного внутреннего LIRC генератора (10 kHz), в не зависимости спит мод или нет.  
    Подстройка скорости хода часов (Speed) в этом режиме не требуется. Но потребление вырастет на примерно 50 mAh в сутки.  
    Точность часов в этом режиме сравнима с точностью у боксов со встроенными часами (LXT генератор). Но часы сбрасываются при вынимании батареек, так как нет резервного питания на плате.

  * __SHR__
  
    Подстройка шунта  
    *Предупреждение: Неправильная установка данного пункта чревато для жизни вашего бокса. Может привести к превышению тока через атомайзер и выгоранию схемы.*  
    Шунт используется в схеме для вычисления (через напряжение на нем) тока, сопротивления и мощности атомайзера.  
    Программе указывается сопротивление шунта и в данном пункте его можно изменить. Это делается для более точной подгонки вычисленного сопротивления атомайзера.
    Показания на экране при этом - текущее сопротивление атомайзера. Не меняйте этот параметр сильно и только при крайней необходимости.  
    Для сброса шунта по умолчанию для данного мода - долгое удерживание кнопки Пуск (2сек).

  * __UCH__

    Зарядка по USB.  
    *Только для многобатарейных модов и Пико 25.*  
    Включает/выключает возможность зарядки мода по USB.
    Однобатарейные моды имеют отдельную от общей схемы зарядку на плате и не дают возможность её как то контролировать.  
    USB продолжает работать в обычном режиме для прошивки, мониторинга итд.  
    Рекомендуется произвести подстройку BVO перед зарядкой мода через USB.  

  * __BAT__

    Модель батарей (профиль батарей).  
    Прошивка пересчитывает напряжение на батарейке в проценты. За то, как это будет сделано и отвечает данная настройка.
    На выбор предлагается несколько предустановленных типов пересчета для разных батарей: 25R, 30Q, HG2, HE4, VTC4, VTC5, VTC6. Они точнее чем GEN и с установленным ограничением по току для каждой (по результатам тестов Mooch).
    "GEN" - универсальная батарейка, принятая по умолчанию от производителя мода. Используйте её в боксах со встроенными аккумами.

    Пользовательская батарейка (CUS):  
    Это особая батарейка, значения пересчета для которой вы можете изменить прямо на моде, в меню CUS. По умолчанию показания процентов соответствуют разряду аккума при парении около 30-ти Ватт.  


  * __USB__

    Режим по умолчанию HID, это основной режим работы и работает всегда, для связи с ПК, прошивки или мониторинга.
    Дополнительный режим COM для USB. Создается интерфейс виртуального COM-порта для использования терминальной программы на ПК, в основном для проверочных целей программиста.

  * __Temp__

    Позволяет подстроить показания внутреннего датчика температуры платы ближе к реальным.
    Дайте моду поспать (остыть) около домашнего градусника температуры в комнате. Затем быстро установите это значение на моде.
    
  * __CUS__

    Меню изменения таблицы пересчета напряжения аккума (всегда используется акк с наименьшим напряжением) в показания в процентах для пользовательской батарейки.
    По умолчанию примерно соответствует показаниям токового аккума 18650 при парении на 30-ти Ваттах. При этом проценты будут более реально отражать возможности батареи на данной мощности.
    0% и 100% - неизменяемые, они должны быть такими всегда. Другие проценты и все напряжения можно изменить в сторону увеличения от предыдущего значения.
    После проверки на валидность таблица запишется в энергонезависимую память параметров (dataflash).
    
  * __MAX__

    Данное меню позволяет установить максимальные допустимые значения для:
    - мощности на атомайзер
    - напряжения на атомайзер
    - ток зарядки по USB (для модов, где управление зарядом поддерживается)
    - температуры платы

-----

← Предыдущая страница: [Меню интерфейса](interface_ru.md) --  Следующая страница: [Как скомпиллировать](howtobuild_ru.md)→
