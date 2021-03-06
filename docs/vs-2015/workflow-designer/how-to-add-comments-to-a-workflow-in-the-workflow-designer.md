---
title: 'Практическое: добавлять комментарии в рабочий процесс в конструкторе рабочих процессов | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f70f8ba1a30d5adcaffe7e693fcc711d08a28baf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561581"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Как добавлять комментарии в рабочий процесс в конструкторе рабочих процессов
Чтобы упростить создание более сложных рабочих процессов большего размера, [!INCLUDE[net_v45](../includes/net-v45-md.md)] дает разработчикам возможность добавлять заметки к следующим типам элементов в конструкторе.  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Классы, производные от <xref:System.Activities.Statements.FlowNode>.  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  Содержимое заметки сохраняется в виде обычного текста в файле XAML, связанном с рабочим процессом, и потенциально может быть прочитано другими. Избегайте добавлять в заметку конфиденциальные сведения.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Добавление заметки к действию в конструкторе  
  
1.  В конструкторе рабочих процессов, щелкните правой кнопкой мыши на элемент в рабочем процессе конструктора и выберите **заметки**, **добавить заметку**.  
  
2.  Добавьте текст заметки в предоставленное для этого место.  
  
3.  На элементе появится значок заметки. Если навести курсор мыши на значок заметки, отобразится текст заметки.  
  
     ![Последовательность действий с примечанием](../workflow-designer/media/annotation.png "заметки")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Отображение заметки в конструкторе действия  
  
1.  С конструктором операций, имеющая заметки, отображение за пределами действия, нажмите кнопку **ПИН-код** значок заметки декоративного элемента.  
  
2.  Заметка будет отображаться в конструкторе действия. На снимке экрана ниже заметка «Запуск действия в рабочем процессе» отображается в конструкторе действия.  
  
     ![Примечание, отображаемое в конструкторе действий](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Для отображения заметки за пределами конструктора действий, наведите указатель мыши на область заметки в конструкторе действия и нажмите кнопку **изъять** значок  
  
     ![Примечание, отображаемое за пределами конструктора действия](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Отображение или скрытие всех заметок  
  
1.  Щелкните правой кнопкой мыши действие, которое имеет заметку. Выберите **заметки**, **Показать все заметки**.  
  
2.  Все заметки будут отображены в конструкторах действий.  
  
3.  Для отображения всех заметок вне конструкторов действий, щелкните правой кнопкой мыши на действие и выберите **заметки**, **скрыть все заметки**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Изменение или удаление заметки для действия  
  
1.  Щелкните правой кнопкой мыши действие, которое имеет заметку.  
  
2.  Выберите **заметки**, **изменить заметку** или **удалить заметку**.  
  
3.  Заметка будет открыта для редактирования или удалена.  
  
4.  Чтобы удалить все заметки одновременно, щелкните правой кнопкой мыши конструктор рабочих процессов и выберите **заметки**, **удалить все заметки**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Добавление, изменение и удаление заметки для переменной или аргумента.  
  
1.  Щелкните правой кнопкой мыши переменную или аргумент, затем выберите «Добавить заметку».  
  
2.  Введите текст заметки. Переменная или аргумент будут отображаться со значком заметки.  
  
3.  Щелкните правой кнопкой мыши переменную или аргумент с заметкой. Выберите «Изменить заметку».  
  
4.  Заметка будет открыта для изменения.  
  
5.  Щелкните правой кнопкой мыши переменную или аргумент с заметкой. Выберите «Удалить заметку».  
  
6.  Заметка будет удалена.