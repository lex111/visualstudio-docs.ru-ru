---
title: 'Пошаговое руководство: Создание специализированного редактора | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9110e1c2ac6c39898f7dbbd6f9f4412ebcba278
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497441"
---
# <a name="walkthrough-create-a-custom-editor"></a>Пошаговое руководство: Создание пользовательского редактора
Шаблон проекта VSPackage можно создать простой пользовательский редактор в C++. Шаблон проекта VSPackage больше не поддерживает проекты C# или Visual Basic. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти **новый проект** диалоговое окно, в разделе **C++ расширяемости** папки.  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Чтобы создать VSPackage с помощью шаблона пакета Visual Studio  
  
1.  Создайте проект с помощью шаблона пакета Visual Studio.  
  
2.  Выберите **специализированного редактора** и нажмите кнопку **Далее**. **Параметры редактора** появится страница.  
  
3.  Введите имя редактора в **имя редактора** поле. Введите расширение файла, которое вы хотите иметь связанное с редактором в **расширение файла** поле. В редакторе доступна для файлов с этим расширением. Расширение файла регистрируется для Visual Studio, не для Windows. Введите имя файла по умолчанию для новых документов, создаваемых с помощью редактора в **имя файла по умолчанию** поле.  
  
4.  Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.  
  
### <a name="to-test-your-custom-editor"></a>Чтобы проверить пользовательский редактор  
  
1.  На **файл** последовательно выберите пункты **New** и нажмите кнопку **файл**.  
  
2.  В **установленные шаблоны** области **новый файл** диалоговом окне выберите файл шаблона, то файл типа вы зарегистрированы.  
  
3.  Нажмите кнопку **откройте** для просмотра и редактирования документа.  
  
     Редактор поддерживает операции вырезания и вставки, поиска и замены и открытым и нагрузки.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)