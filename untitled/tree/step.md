# step

## Шаговое управление \(Step Control\)

Шаговое управление похоже на две кнопки, назначенные одному пин-у. Одна кнопка увеличивает ваше значение на установленный шаг, а другая уменьшает его. Это очень полезно для случаев использования, когда вам нужно точно изменять ваши значения, но вы не можете достичь такой точности с помощью виджета [Cлайдера](https://github.com/blynkkk/blynkkk.github.io/tree/master/mobile/ru/slider.md).

**Отправить шаг \(Send Step\)** опция позволяет вам отправлять на оборудование каждый шаг нвместо фактического значения виджета.

**Зациклить значения \(Loop value\)** опция позволяет сбросить Шаговый виджет на начальное значение при достижении максимального.

Вы можете изменить значение Шагового виджета со стороны оборудования. Например:

```cpp
Blynk.virtualWrite(V1, val);
```

Вы можете изменить описание виджета со стороны оборудования с помощью кода:

```cpp
Blynk.setProperty(V1, "label", "Мой счетчик.");
```

Вы можете изменить шаг виджета со стороны оборудования:

```cpp
Blynk.setProperty(V1, "step", 10);
```

или изменить цвет:

```cpp
//#D3435C - Красный цвет в RGB кодировке
Blynk.setProperty(V1, "color", "#D3435C");
```

Вы также можете получить состояние виджета Шагового управления с сервера в случае, если ваше оборудование отключилось, с помощью функции Blynk.Sync:

```cpp
BLYNK_CONNECTED() {
  Blynk.syncVirtual(V1);
}

BLYNK_WRITE(V1) {
  int stepperValue = param.asInt();
}
```

## Интервал записи \(Write interval\)

Опция позволяет вам передавать значения на ваше оборудование в через определенные интервалы времени. Например, установка интервала записи на 100 мс означает, что при перемещении ползунка на аппаратное обеспечение будет отправлено только 1 значение в течение 100 мс. Эта опция также используется для уменьшения трафика данных на ваше оборудовании.

**Пример кода:** [Базовый пример](https://github.com/blynkkk/blynk-library/blob/master/examples/GettingStarted/BlynkBlink/BlynkBlink.ino)

