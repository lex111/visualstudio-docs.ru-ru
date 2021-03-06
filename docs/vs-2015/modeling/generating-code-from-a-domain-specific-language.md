---
title: Создание кода из доменного языка | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3fbe7e40a277174eb556a61b50eb88279adebfb2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570850"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Создание кода из доменного языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [создание кода из доменного языка](https://docs.microsoft.com/visualstudio/modeling/generating-code-from-a-domain-specific-language).  
  
Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] предоставляет эффективный способ создания кода, документов, файлов конфигурации и другие артефакты из данных, представленных в модели. С помощью [!INCLUDE[dsl](../includes/dsl-md.md)], можно создать набор классов, представляющих данные и вы можете использовать текстовые шаблоны в классах, имена и свойства отражают эти данные.  
  
 Например Fabrikam имеется файл XML, имена заказчиков и адресов электронной почты. Разработчики создать модель, в котором клиент — это класс, с помощью свойства name и e-mail. Они создания нескольких текстовых шаблонов для обработки данных, включая этот фрагмент, который создает таблицу из всех клиентов как часть HTML-страницу:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 При обработке базы данных клиента в хранилище моделей считывается XML-файле. Объект *процессора директив*, созданный с помощью [!INCLUDE[dsl](../includes/dsl-md.md)], классу "Customer" делает доступными в код текстового шаблона. Многие текстовые шаблоны можно выполнять то же хранилище.  
  
 Текстовые шаблоны имеют большое значение для [!INCLUDE[dsl](../includes/dsl-md.md)]. Они используются для создания исходного кода для элементов модели домена, а также VSPackage и элементы управления, которые используются для интеграции средств с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 В этом разделе рассматриваются некоторые из способов создания, изменения и отладки текстовых шаблонов, используемых в [!INCLUDE[dsl](../includes/dsl-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обращение к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md)  
  
 Содержит основные сведения о ссылке на предметно ориентированного языка в текстовых шаблонах.  
  
 [Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 В этой статье описывается устранение неполадок и отладка в текстовый шаблон, который ссылается на предметно ориентированного языка.  
  
 [Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 В этой статье описывается подключение пользовательского ведущего приложения с генерируемым обработчиком директив.  
  
 [Команда DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Описывает командный файл, который выполняет TextTransform исполняемого файла в командной строке для текстовых шаблонов, которые ссылаются на предметно ориентированных языков.  
  
## <a name="reference"></a>Ссылка  
 [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)  
  
 Предоставляет синтаксис директивы текстовых шаблонов и блоках управления.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Описание процесса преобразования текстового шаблона.  
  
 [Создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md)  
  
 В этом разделе, при создании файлов из доменного языка на сервере сборки.



