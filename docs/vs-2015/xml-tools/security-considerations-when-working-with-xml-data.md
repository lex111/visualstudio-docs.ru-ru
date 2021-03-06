---
title: Вопросы безопасности при работе с XML-данными | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9acd701c4e279d02cae874768b18a3d89b58203d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562069"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Вопросы безопасности при работе с XML-данными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вопросы безопасности при работе с XML-данными](https://docs.microsoft.com/visualstudio/xml-tools/security-considerations-when-working-with-xml-data).  
  
  
В этом разделе обсуждаются проблемы безопасности, о которых следует знать при работе с редактором XML или отладчиком XSLT.  
  
## <a name="xml-editor"></a>XML-редактор  
 Редактор XML построен на основе текстового редактора Visual Studio. Обработка многих XML-процессов выполняется с помощью классов <xref:System.Xml> и <xref:System.Xml.Xsl> .  
  
-   Преобразования XSLT выполняются в новом домене приложения. Преобразования XSLT выполняются *изолированной*; то есть политики безопасности доступа кода компьютера используется для определения ограниченных разрешений, зависящих от расположения таблицы стилей XSLT, применяется. Например, таблицы стилей из Интернета имеют самые ограниченные разрешения, в то время как скопированные на жесткий диск таблицы стилей работают в режиме полного уровня доверия.  
  
-   Класс <xref:System.Xml.Xsl.XslCompiledTransform> используется для компиляции XSLT в код на языке MSIL для повышения производительности во время выполнения.  
  
-   Схемы, указывающие на внешнее местоположение в файле каталога, автоматически загружаются при первой загрузке редактора XML. Класс <xref:System.Xml.Schema.XmlSchemaSet> используется для компиляции схем. Файл каталога, загружаемый вместе с редактором XML, не содержит ссылок на внешние схемы. Пользователь должен явно добавить ссылки на внешнюю схему, чтобы редактор XML загрузил файл схемы. Загрузка HTTP можно отключить с помощью **различные параметры инструментов** страницы редактора XML.  
  
-   Редактор XML использует классы <xref:System.Net> для загрузки схем.  
  
## <a name="xslt-debugger"></a>Отладчик XSLT  
 Отладчик XSLT использует подсистему управляемой отладки Visual Studio и классы из пространств имен <xref:System.Xml> и <xref:System.Xml.Xsl>.  
  
-   Отладчик XSLT запускает каждое преобразование XSLT в изолированном домене приложения. Для определения ограниченных разрешений, зависящих от расположения таблицы стилей XSLT, применяется политика управления доступом для кода. Например, таблицы стилей из Интернета имеют самые ограниченные разрешения, в то время как скопированные на жесткий диск таблицы стилей работают в режиме полного уровня доверия.  
  
-   Таблица стилей XSLT компилируется с помощью класса <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   Подсистема управляемой отладки загружает средство оценки выражений XSLT. Подсистема управляемой отладки исходит из того, что весь код запускается с пользовательского локального компьютера. Соответственно, класс <xref:System.Xml.Xsl.XslCompiledTransform> загружает файл XSLT на пользовательский локальный компьютер. Вероятность того, что произойдет повышение прав доступа на выполнение, уменьшается путем запуска всех преобразований XSLT в новом домене приложения с ограниченными разрешениями.  
  
## <a name="see-also"></a>См. также  
 [Домены приложений](http://msdn.microsoft.com/en-us/39e57d07-a740-4cd4-ae82-e119ea3856c1)



