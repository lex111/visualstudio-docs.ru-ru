---
title: 'CA2103: Проверьте императивную безопасность | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6aa27379c7fc505c1eddf8ad0518693f5e9930a0
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47573547"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: проверьте императивную безопасность
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2103: Проверьте императивную безопасность](https://docs.microsoft.com/visualstudio/code-quality/ca2103-review-imperative-security).

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод использует принудительную безопасность и может обеспечить создание разрешения с помощью сведений о состоянии или возвращаемых значений, которые могут измениться в период активности требования.

## <a name="rule-description"></a>Описание правила
 Принудительная безопасность использует управляемые объекты для задания разрешений и действия по обеспечению безопасности во время выполнения кода, по сравнению с декларативной безопасности, которое использует атрибуты для хранения разрешений и действий в метаданных. Принудительная безопасность обладает большой гибкостью, поскольку можно задать для состояния объекта разрешения и выбрать действия по обеспечению безопасности, используя информацию, которая недоступна до времени выполнения. Вместе с, гибкость риск того, что сведения среды выполнения, используемом для определения состояния разрешения не остаются без изменений до тех пор, пока действует действие.

 Поэтому по возможности следует использовать декларативную безопасность. Декларативные требования легче понять.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Просмотрите требования принудительной безопасности, чтобы убедиться в том, что состояние разрешения не полагается на сведения, которые можно изменить до тех пор, пока используется разрешение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если разрешение не зависит от изменения данных. Тем не менее рекомендуется изменить принудительное требование в его эквивалент в декларативной.

## <a name="see-also"></a>См. также
 [Правила написания безопасного кода](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [данные и моделирование](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



