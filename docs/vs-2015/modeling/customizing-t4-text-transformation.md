---
title: Настройка преобразования текста T4 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e304b38979b80c1d67d3f88accdbfa584406c9cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572125"
---
# <a name="customizing-t4-text-transformation"></a>Настройка преобразования текста T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Настройка преобразования текста T4](https://docs.microsoft.com/visualstudio/modeling/customizing-t4-text-transformation).  
  
Текстовые шаблоны — это компонент [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , которые позволяют создавать программный код или другие текстовые файлы посредством процесса преобразования. С помощью [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], процесс преобразования шаблона по умолчанию можно расширить, настроив процессор директив текстового шаблона или основное приложение текстовых шаблонов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md)  
 Описывает, как работает преобразование текста и роль узла шаблона и процессоры директив.  
  
 [Создание пользовательских обработчиков директив для текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Процессор директив имеет дело с директивы в шаблоне, такие как `<#@template#>.` он выполняется в процессе компиляции шаблона и может загружать сборки и другие ресурсы. Его можно также добавить код, который будет загружать ресурсы во время выполнения. Определив процессор директив, можно уменьшить сложность шаблонов.  
  
 [Вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Если вы создаете [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширение, например меню команды или обработчика событий, расширение может использовать службы текстовых шаблонов для преобразования любого текстового шаблона. Вы можете передать данные параметра в шаблон с помощью объекта сеанса и получить значения из шаблона с помощью `<#@parameter#>` директива.  
  
 [Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 При выполнении кода текстового шаблона узел предоставляет доступ к внешние файлы и состояние приложения. Например, узел, который выполняется преобразование текста в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно предоставлять доступ к обозревателю решений. Она также отображает ошибки в окне сообщений об ошибках. Если вы хотите выполнить преобразования текста в другом контексте, можно определить собственный узел, который предоставляет доступ к службам, доступным в этом контексте.  
  
 Если вы создаете [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения, рассмотрите возможность использования имеющейся службой преобразования текста вместо того чтобы писать собственный узел. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Ссылка  
 [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)  
  
 Предоставляет синтаксис директивы текстовых шаблонов и блоках управления.



