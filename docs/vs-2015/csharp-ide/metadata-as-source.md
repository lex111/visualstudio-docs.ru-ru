---
title: Метаданные как исходный код | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eeebb2e84c7724002b82be68a73f471ca1bcabf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560698"
---
# <a name="metadata-as-source"></a>Метаданные как исходный код
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функция "метаданные как исходный код" позволяет просматривать метаданные в виде исходного кода на языке C# в предназначенном только для чтения буфере. Это дает возможность просматривать объявления типов и членов (без реализации). Метаданные можно просмотреть в виде исходного кода, запустив команду **Перейти к определению** для типов и членов, исходный код которых не доступен из проекта или решения.  
  
> [!NOTE]
>  При попытке выполнить команду **Перейти к определению** для типов или членов, помеченных как внутренние, интегрированная среда разработки не позволит просмотреть их метаданные в виде исходного кода, даже если сборка, к которой осуществляется обращение, является дружественной.  
  
 Метаданные можно просматривать как исходный код в редакторе кода или в окне **Определение кода** .  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Просмотр метаданных в виде исходного кода в редакторе кода  
 При запуске команды **Перейти к определению** для элемента, исходный код которого недоступен, в редакторе кода открывается документ с вкладками, содержащий представление метаданных этого элемента в виде исходного кода. Имя типа, после которого следует текст **[из метаданных]**, будет показано на вкладке документа.  
  
 Например, при выполнении команды **Перейти к определению** для типа <xref:System.Console>метаданные типа <xref:System.Console> будут показаны в редакторе кода в виде исходного кода на языке C#, напоминающего объявление этого типа, но без реализации.  
  
 ![Метаданные в виде исходного кода](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Просмотр метаданных в виде исходного кода в окне "Определение кода"  
 Если окно **Определение кода** является активным и видимым, то интегрированная среда разработки автоматически выполняет команду **Перейти к определению** для элементов, находящихся под курсором в редакторе кода, и для элементов, выделенных в окне **Представление классов** или **Обозреватель объектов**. Если исходный код для этого элемента недоступен, то интегрированная среда разработки отображает метаданные в виде исходного кода в окне **Определение кода** .  
  
 Например, если в редакторе расположить курсор в пределах слова <xref:System.Console> , то метаданные типа <xref:System.Console> будут показаны в виде исходного кода в окне **Определение кода** . Исходный код напоминает объявление типа <xref:System.Console> , но не содержит его реализации.  
  
 Если вы хотите просмотреть объявление элемента, который присутствует в окне **Определение кода** , щелкните правой кнопкой мыши этот элемент и выберите команду **Перейти к определению**.