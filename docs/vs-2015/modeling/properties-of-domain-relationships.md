---
title: Свойства доменных связей | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ff37703643dc9d1c795fe10b5f24154ee46174af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558626"
---
# <a name="properties-of-domain-relationships"></a>Свойства доменных связей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [свойства доменных связей](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-relationships).  
  
В следующей таблице свойства связаны с доменной связи. Сведения о доменных связей, см. в разделе [Общие сведения о моделях, классах и отношениях](../modeling/understanding-models-classes-and-relationships.md). Дополнительные сведения об использовании этих свойств см. в разделе [Настройка и расширение доменного языка](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Свойство.|Описание|Значение по умолчанию|  
|--------------|-----------------|-------------|  
|Модификатор доступа|Уровень доступа доменной связи (`public` или `internal`).|`public`|  
|Настраиваемые атрибуты|Используется для добавления атрибутов для класса исходного кода, созданный из доменной связи.|\<None >|  
|Создает двойной производным|Если `True`, создается базовый класс и разделяемый класс (для поддержки настройки посредством переопределений). Дополнительные сведения см. в разделе [переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Имеет пользовательский конструктор|Если `True`, означает, что пользовательский конструктор предоставляется в исходном коде. Дополнительные сведения см. в разделе [переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Модификатор наследования|Описывает тип наследования класса исходного кода, созданный из доменной связи (`none`, `abstract` или `sealed`).|\<None >|  
|Разрешены дубликаты|Если `True`, могут быть созданы повторяющиеся ссылки доменной связи между двумя одинаковыми элементами.|`False`|  
|Базовых связей|Если доменная связь является производным, базовая связь доменной связи.|\<None >|  
|Такое внедрение|Если `True`, доменное отношение — встраивающим отношением. Если `False`, связь является ссылочным отношением.|\<Оба >|  
|name|Имя доменной связи.|Текущее имя|  
|Пространство имен|Пространство имен, которое связано с доменной связи.|Текущее пространство имен|  
|Примечания|Неформальные примечания, которые связаны с доменной связи.|\<None >|  
|Описание|Описание, которое используется для документирования кода и используется в пользовательском Интерфейсе созданного конструктора.|\<None >|  
|Отображаемое имя|Имя, которое отображается в созданном конструкторе для доменной связи.|\<None >|  
|Ключевое слово Help|Необязательное ключевое слово, используемое для индексации справки F1 для доменной связи.|\<None >|  
  
## <a name="see-also"></a>См. также  
 [Глоссарий по средствам доменного языка работы](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



