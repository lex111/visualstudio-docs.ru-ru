---
title: Шаблоны нагрузки для нагрузочного тестирования в Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 431fea97c0dcca0407f2b0627e6b2d9def774799
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179444"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Изменение шаблонов нагрузки для моделирования действий виртуальных пользователей

Свойства шаблонов нагрузки определяют способ регулировки смоделированной пользовательской нагрузки во время нагрузочного теста. В Visual Studio имеется три встроенных шаблона нагрузки: постоянный, пошаговый и на базе целей. Следует выбрать шаблон нагрузки и настроить свойства до значений, соответствующих целям нагрузочного теста.

Шаблон нагрузки является компонентом сценария. Сценарии вместе со своими шаблонами нагрузки составляют нагрузочный тест.

> [!NOTE]
> Во всех шаблонах нагрузки нагрузка, создаваемая Visual Studio, представляет собой смоделированную нагрузку виртуальных пользователей.

## <a name="load-patterns"></a>Шаблоны нагрузки

### <a name="constant"></a>Константа

 Шаблон постоянной нагрузки используется для моделирования нагрузки, создаваемой пользователями, число которых не изменяется во время нагрузочного теста. Например, при выполнении теста состояния для веб-приложения может потребоваться установить небольшую постоянную нагрузку, создаваемую 10 пользователями.

#### <a name="constant-load-pattern-considerations"></a>Особенности шаблона постоянной нагрузки

 Шаблон постоянной нагрузки используется для применения одинаковой нагрузки, создаваемой пользователями, в ходе выполнения нагрузочного теста. Следует с осторожностью применять шаблон постоянной нагрузки при использовании большого числа пользователей, поскольку в этом случае в начале нагрузочного теста может возникнуть неразумная и нереалистичная нагрузка на серверы. Например, если нагрузочный тест содержит веб-тест, начинающийся с запроса к домашней странице, и для этого нагрузочного теста задана постоянная нагрузка в 1000 пользователей, он максимально быстро отправит первые 1000 запросов к домашней странице. Это может не отражать реального распределения запросов к веб-сайту. Чтобы обойти эту проблему, рассмотрите возможность использования шаблона пошаговой нагрузки, в котором число пользователей постепенно увеличивается до 1000, или указания периода прогрева в параметрах запуска нагрузочного теста. Если задан период прогрева, в ходе этого периода нагрузка автоматически постепенно увеличивается. Дополнительные сведения см. в статье [Настройка задержки начала сценария в нагрузочных тестах](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Шаг

 Шаблон пошаговой нагрузки используется для моделирования нагрузки, создаваемой пользователями, число которых постепенно возрастает до определенного максимума. Для пошаговых нагрузок требуется указать значения **Начальное число пользователей**, **Максимальное число пользователей**, **Длительность шага (секунд)** и **Число пользователей на шаге**.

 Например, пошаговая нагрузка с **начальным числом пользователей**, равным 1, **максимальным числом пользователей**, равным 100, **длительностью шага (в секундах)**, равной 10, и **числом пользователей на шаге**, равным 1, создает шаблон пользовательской нагрузки, который начинается с 1 пользователя и увеличивается на 1 каждые 10 секунд, пока не достигнет значения 100 пользователей.

> [!NOTE]
> Если общая продолжительность теста короче времени, необходимого для достижения максимального числа пользователей, то тест завершается по истечении его продолжительности, не достигнув **максимального числа пользователей**.


 Пошаговый шаблон можно использовать для увеличения нагрузки до тех пор, пока сервер не достигнет точки, при которой наблюдается значительное снижение производительности. По мере возрастания нагрузки сервер постепенно исчерпает свои ресурсы. Пошаговая нагрузка предоставляет удобный способ определения количества пользователей, при котором это происходит. Кроме того, с помощью пошаговой нагрузки можно внимательно отслеживать ресурсы агента, чтобы проверить возможность агента создавать требуемую нагрузку.

 Чтобы получить точные показатели для заданной нагрузки, как правило, требуется выполнить несколько запусков с различными значениями длительности шага и числа пользователей на шаге. С помощью пошаговых нагрузок часто можно увидеть начальные скачки, возникающие на каждом шаге при добавлении пользователей. Поддержание нагрузки на этом уровне позволяет измерить производительность системы, восстановившейся после начального скачка.

#### <a name="step-load-pattern-considerations"></a>Особенности шаблона пошаговой нагрузки

 Шаблон пошаговой нагрузки можно использовать для повышения нагрузки на сервер или серверы в ходе выполнения тестов, чтобы отслеживать изменение производительности с увеличением создаваемой пользователями нагрузки. Например, чтобы увидеть, как один или несколько серверов работают при увеличении нагрузки до 2000 пользователей, можно запустить 10-часовй нагрузочный тест с шаблоном пошаговой нагрузки, имеющим следующие свойства.

-   **Начальное число пользователей**: 100

-   **Максимальное число пользователей**: 2000

-   **Длительность шага (секунд)**: 1800

-   **Время увеличения шага (секунд)**: 20

-   **Число пользователей на шаге**: 100

 При этих параметрах нагрузочный тест будет выполняться 30 минут (1800 секунд) при нагрузках в 100, 200, 300 и до 2000 пользователей. Свойство **Время увеличения шага** заслуживает отдельного упоминания, так как это единственное свойство, недоступное для выбора в **мастере тестовой нагрузки**. Это свойство позволяет плавно, а не резко, увеличивать нагрузку между шагами (например, от 100 до 200 пользователей). В этом примере нагрузка будет увеличиваться от 100 до 200 в течение 20 секунд (по пять пользователей в секунду). Дополнительные сведения см. в статье [Практическое руководство. Указание времени увеличения шага для пошагового шаблона нагрузки](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>На базе целей

 Шаблон нагрузки на базе целей напоминает пошаговый шаблон, однако вместо периодического изменения нагрузки в нем моделируется увеличение числа пользователей на основе порогов счетчиков производительности. Ниже перечислены различные задачи, в решении которых удобно использовать нагрузки на базе целей.

-   Максимальное увеличение выходных данных агентов: измерение ключевых ограничивающих показателей для агента, чтобы максимально увеличить выходные данные агентов. Обычно это относится к ЦП, но может относиться и к памяти.

-   Достижение некоторого целевого уровня ресурсов (как правило, ЦП) на целевом сервере и последующее измерение пропускной способности на этом уровне. Это позволяет сравнивать пропускную способность в разных тестовых запусках, во время которых удерживается один уровень использования ресурсов на сервере.

-   Достижение целевого уровня пропускной способности на сервере.

 В следующей таблице показан пример шаблона на базе целей со следующими параметрами свойств:

|Группа свойств|Свойство.|Значение|
|--------------------|--------------|-----------|
|Счетчик производительности|Категория|Процессор|
|Счетчик производительности|Компьютер|ContosoServer1|
|Счетчик производительности|Счетчик|% загруженности процессора|
|Счетчик производительности|Экземпляр|_Total|
|Целевой диапазон счетчика производительности|Верхний предел|90|
|Целевой диапазон счетчика производительности|Нижний предел|70|
|Пределы числа пользователей|Начальное число пользователей|1|
|Пределы числа пользователей|Максимальное число пользователей|100|
|Пределы числа пользователей|Максимальный декремент счетчика пользователей|5|
|Пределы числа пользователей|Максимальный инкремент счетчика пользователей|5|
|Пределы числа пользователей|Минимальное число пользователей|1|

 В результате установки этих параметров **анализатор тестовой нагрузки** изменяет число пользователей от 1 до 100 в течение тестового запуска таким образом, чтобы **Счетчик** `% Processor Time` на сервере WebServer01 находился в диапазоне от `70%` до `90%.`

 Величина коррекции пользовательской нагрузки на каждом шаге определяется параметрами **Максимальный инкремент счетчика пользователей** и **Максимальный декремент счетчика пользователей**. Пределы числа пользователей зависят от свойств **Максимальное число пользователей** и **Минимальное число пользователей**.

#### <a name="goal-based-load-pattern-considerations"></a>Особенности шаблона нагрузки на базе целей

 Шаблон нагрузки на основе целей удобно использовать, если требуется определить число пользователей, которое может поддерживаться системой, прежде чему будет достигнут определенный уровень использования ресурсов. Этот вариант лучше всего применять, если уже определен самый дефицитный ресурс системы (т. е. ее узкое место).

 Предположим, что дефицитным ресурсом является процессор сервера баз данных, и нам требуется узнать, сколько пользователей может поддерживать система, если уровень загрузки процессора сервера баз данных составляет приблизительно 75 процентов. Можно воспользоваться шаблоном нагрузки на основе целей, для которого установлена цель поддерживать значение счетчика "% загруженности процессора" в диапазоне от 70 до 80 процентов.

 Также необходимо следить за тем, не ограничивается ли производительность системы каким либо-другим ресурсом. В этом случае может оказаться, что заданный шаблоном целевой показатель никогда не будет достигнут. Кроме того, пользовательская нагрузка будет увеличиваться, пока не будет достигнуто значение **Максимальное число пользователей**. Такая нагрузка обычно является нежелательной, поэтому следует с осторожностью выбирать счетчик производительности для шаблона нагрузки на основе целей.

## <a name="tasks"></a>Задачи

|Задачи|Связанные разделы|
|-----------|-----------------------|
|**Задание начального шаблона нагрузки для нагрузочного теста**. При создании нагрузочного теста с помощью **мастера тестовой нагрузки** вы выбираете шаблон нагрузки.|-   [Изменение шаблона нагрузки](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Изменение шаблона нагрузки для нагрузочного теста**. После создания нагрузочного теста шаблон нагрузки можно изменить, используя **редактор тестовой нагрузки**.|-   [Практическое руководство. Указание времени увеличения шага для пошагового шаблона нагрузки](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Задание того, должны ли виртуальные пользователи в сценарии тестовой нагрузки включать данные веб-кэша**. Можно изменить свойство **Процент новых пользователей**, чтобы повлиять на имитацию веб-кэширования, которое выполняется веб-браузером для виртуальных пользователей в рамках нагрузочного теста.|-   [Практическое руководство. Задание процента виртуальных пользователей, которые могут использовать данные веб-кэша](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Задание времени увеличения шага для шаблона пошаговой нагрузки**. Свойство **Время увеличения шага** позволяет сразу увеличивать нагрузку между шагами (например, от 100 пользователей до 200) или делать это постепенно.|-   [Практическое руководство. Указание времени увеличения шага для пошагового шаблона нагрузки](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Изменение шаблона нагрузки

 После создания нагрузочного теста с помощью **мастера тестовой нагрузки** можно использовать **Редактор тестовой нагрузки**, чтобы изменить связанные со сценарием свойства шаблона нагрузки в соответствии с целями тестирования.

> [!NOTE]
> Полный список свойств сценария тестовой нагрузки и их описание см. в разделе [Свойства сценария тестовой нагрузки](../test/load-test-scenario-properties.md).


 Шаблон нагрузки определяет количество виртуальных пользователей, активных во время нагрузочного теста, и скорость добавления новых пользователей. Существует три шаблона: пошаговый, постоянный и на основе целей. Дополнительные сведения см. в статье [Изменение шаблонов нагрузки для моделирования действий виртуальных пользователей](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Для программного изменения свойств нагрузки служит подключаемый модуль нагрузочного теста. Дополнительные сведения см. в статье [Практическое руководство. Создание подключаемого модуля нагрузочных тестов](../test/how-to-create-a-load-test-plug-in.md).


### <a name="to-change-the-load-pattern"></a>Изменение шаблона нагрузки

1.  Откройте нагрузочный тест.

2.  В папке *Сценарии* области **Редактор тестовой нагрузки** разверните сценарий, для которого нужно изменить шаблон нагрузки, и выберите подходящий шаблон нагрузки.

    > [!NOTE]
    > Название узла шаблона нагрузки в том виде, как оно отображается в дереве сценариев, отражает профиль нагрузки, выбранный при создании нагрузочного теста. Это может быть **Профиль постоянной нагрузки** или **Профиль пошаговой нагрузки**.

3.  Нажмите клавишу **F4**, чтобы открыть окно **Свойства**.

     В окне **Свойства** отображаются категории **Шаблон нагрузки** и **Параметры**.

4.  Измените свойство **Шаблон** в категории **Шаблон нагрузки** (необязательно).

     Для свойства **Шаблон** имеются следующие варианты: **пошаговый**, **постоянный** и **на базе целей**. Дополнительные сведения о типах шаблонов нагрузки см. в статье [Изменение шаблонов нагрузки для моделирования действий виртуальных пользователей](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  Измените значения в категории **Параметры** (необязательно).

    > [!NOTE]
    > Значения для категории **Параметры** задаются в соответствии со значением, выбранным для свойства **Шаблон**.

6.  По завершении изменения свойств выберите команду **Сохранить** в меню **Файл**. После этого нагрузочный тест можно выполнять с новым шаблоном нагрузки.

## <a name="see-also"></a>См. также

- [Изменение сценариев тестовой нагрузки](../test/edit-load-test-scenarios.md)
- [Практическое руководство. Задание процента виртуальных пользователей, которые могут использовать данные веб-кэша](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Практическое руководство. Указание времени увеличения шага для пошагового шаблона нагрузки](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)