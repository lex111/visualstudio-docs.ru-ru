---
title: 'CA1726: Используйте предпочтительные термины | Документация Майкрософт'
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
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b13c43a563a158a2eeb8484e29810c5b91d110aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559505"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: используйте предпочтительные термины
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA1726: используйте предпочитаемые термины](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — для сборок<br /><br /> Не критическое — при возникновении в параметрах типов|  
  
## <a name="cause"></a>Причина  
 Имя видимого снаружи идентификатора включает термин, для которого существует другой предпочтительный термин. Кроме того имя содержит термин Flag или Flags.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило выполняет синтаксический анализ идентификатора в токены. Каждая отдельная лексема и каждая последовательность двух лексем сравнивается с условиями, встроенные в правило и в разделе не рекомендуемые к использованию всех пользовательских словарей. В следующей таблице показаны условия, которые встроены в правило и их предпочтительный альтернатив.  
  
|Устаревшее название|Предпочтительный термин|  
|-------------------|--------------------|  
|не|Не|  
|Отменено|Отменено|  
|Не удается|Не удается|  
|ComPlus|EnterpriseServices|  
|Тестовых|Невозможно|  
|Didnt|DidNot|  
|Doesnt|Не|  
|Запрет|Не подключать|  
|Flag или Flags|Есть слово для замены. Не используется.|  
|не|HadNot|  
|Не|HasNot|  
|еще не|HaveNot|  
|Индексы|Indexes|  
|не|IsNot|  
|Имя входа|Вход в систему|  
|Выход из системы|Выход из системы|  
|Shouldnt|ShouldNot|  
|Единого входа|Для входа|  
|Утверждения|Выход|  
|Wasnt|WasNot|  
|не были|WereNot|  
|Не|WillNot|  
|Wouldnt|WouldNot|  
|Для записи|Для записи|  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, замените термин предпочтительный термин для альтернативных.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, только в том случае, если имя идентификатора является преднамеренным и посвящен исходный термин вместо предпочтительный термин.  
  
## <a name="related-rules"></a>Связанные правила  
 [Предупреждения именования](../code-quality/naming-warnings.md)

