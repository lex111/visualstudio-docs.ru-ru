---
title: Приступая к работе с шаблоном проекта VSIX | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28aa6c6e2b7aca671b1f1ac9d9be7f34261b867b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499443"
---
# <a name="get-started-with-the-vsix-project-template"></a>Начало работы с шаблоном проекта VSIX
Шаблон проекта VSIX можно использовать для создания расширения или для упаковки существующего расширения для развертывания. Шаблон проекта VSIX имеет версий Visual Basic и Visual C# и устанавливается как часть Visual Studio SDK.  
  
 Шаблон проекта VSIX состоит только из *source.extension.vsixmanifest* файл, содержащий сведения о расширении и ресурсы, выпускаемая.  
  
 Чтобы найти шаблон проекта VSIX, необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Развертывание пользовательского шаблона проекта, с помощью шаблона проекта VSIX  
 Ниже показано, как использовать проект VSIX для упаковки шаблон проекта, который можно использовать совместно с другими разработчиками или отправить в коллекцию Visual Studio.  
  
1.  Создание шаблона проекта.  
  
    1.  Откройте проект, из которого необходимо создать шаблон. Этот проект может быть любого типа проекта.  
  
    2.  В меню **Проект** выберите команду **Экспорт шаблона**. Следуйте инструкциям мастера.  
  
         Объект *ZIP-файл* файл создается в *%USERPROFILE%\My Documents\Visual Studio \<версия > \My Exported Templates\\*.  
  
2.  Создание пустого проекта VSIX.  
  
     В меню **Файл** последовательно выберите пункты **Создать** и **Проект**. Выберите либо **Visual Basic** или **Visual C#**. Выбранный узел и выберите **расширяемости**, а затем выберите **проект VSIX**.  
  
3.  Добавить *ZIP-файл* файл в проект. Задайте его **Копировать в выходной каталог** свойства `Copy Always`.  
  
4.  В **обозревателе решений**, дважды щелкните *source.extension.vsixmanifest* файл, чтобы открыть его в **конструктор манифеста VSIX**, а затем внесите следующие изменения:  
  
    -   Задайте **название продукта** поле **Мой проект шаблона**.  
  
    -   Задайте **идентификатор продукта** поле **MyProjectTemplate - 1**.  
  
    -   Задайте **автор** поле **Fabrikam**.  
  
    -   Задайте **описание** поле **шаблон проекта**.  
  
    -   В **активы** добавьте **Microsoft.VisualStudio.ProjectTemplate** введите и ему присвоено имя пути к *ZIP-файл* файл.  
  
5.  Сохраните и закройте *source.extension.vsixmanifest* файл.  
  
6.  Выполните построение проекта.  
  
7.  В выходном каталоге, дважды щелкните *.vsix* файл.  
  
8.  Объект **установщик VSIX** появится окно сообщения. Следуйте инструкциям для установки расширения.  
  
9. Закройте Visual Studio и повторно откройте его.  
  
10. Выберите **расширения и обновления** (на **средства** меню) и выберите **шаблоны** категории. Один из доступных расширений должен быть **Мой проект шаблона**.  
  
11. Новый шаблон проекта отображается в **новый проект** диалоговое окно в той же позиции, что исходный шаблон проекта. Например, если вы создали шаблон с именем **VB консоли** из консольного приложения Visual Basic, **VB консоли** появляется в той же области, как Visual Basic **консольное приложение**шаблона.  
  
### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Чтобы указать расположение шаблона в диалоговое окно нового проекта  
  
1.  Шаблон папки находятся в *\Common7\IDE\ProjectTemplates {путь установки Visual Studio}* и * \Common7\IDE\ItemTemplates {путь установки Visual Studio}} каталоги. Имена верхнего уровня разделов в **новый проект** диалоговое окно, не совпадают имена папок шаблона. Там, где они различаются, используйте имя папки шаблона.  
  
     Изменение *.vsix* расширение для файла *ZIP-файл*, а затем откройте файл.  
  
2.  Создайте новую папку с тем же именем, что в разделе **новый проект** шаблон должен отображаться в диалоговом окне.  
  
3.  Если шаблон будет отображаться в подраздел, создайте вложенную папку с тем же именем.  
  
4.  Переместить шаблон *ZIP-файл* файл в новую папку.  
  
5.  Изменение *ZIP-файл* расширение *.vsix*.  
  
6.  Откройте манифест VSIX.  
  
7.  В манифесте VSIX, обновите **активов** путь к шаблону, чтобы он указывал на корневой каталог дерева, содержащий файл шаблона. Например, если шаблон находится в *\CSharp\Windows*, должна указывать ссылка *\CSharp*.