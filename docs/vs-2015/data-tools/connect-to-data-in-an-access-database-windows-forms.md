---
title: Подключение к данным в базе данных Access (Windows Forms) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ddab545909730a4fe7f94adf59c6cee74c86409
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569791"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Подключение к данным в базе данных Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [подключение к данным в базе данных Access (Windows Forms)](https://docs.microsoft.com/visualstudio/data-tools/connect-to-data-in-an-access-database-windows-forms).  
  
  
Можно подключиться к базе данных (MDF-файла или ACCDB-файла) с помощью Visual Studio. После определения соединения, данные отображаются в **источников данных** окна. Здесь можно перетаскивать таблицы и представления на формы. Если вы хотите понять, как система проектов в Visual Studio управляет эти файлы локальной базы данных, см. в разделе [как: управление локальные файлы данных, в проект](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для использования этих процедур требуется проект приложения Windows Forms и базы данных Access (ACCDB-файл) или базе данных Access 2000 – 2003 (MDB-файл). Выполните процедуру, соответствующую типу файла.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Создание набора данных для ACCDB-файла  
 Можно подключиться к базам данных, созданных с помощью Access 2013, Office 365, Access 2010 или Access 2007, используя следующую процедуру.  
  
#### <a name="to-create-the-dataset"></a>Создание набора данных  
  
1.  Откройте приложение Windows Forms, к которому требуется подключение к данным.  
  
2.  На **представление** меню, выберите **Other Windows** > **источников данных**.  
  
     ![Просмотр других источников данных Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  В окне **Источники данных** выберите **Добавить новый источник данных**.  
  
     ![Добавить новый источник данных](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  Выберите **базы данных** на **Выбор типа источника данных** странице, а затем выберите **Далее**.  
  
5.  Выберите **набора данных** на **Выбор модели базы данных** странице, а затем выберите **Далее**.  
  
6.  На **Выбор подключения базы данных** выберите **новое подключение** для настройки нового подключения к данным.  
  
7.  Изменение **источника данных** для **поставщик данных .NET Framework для OLE DB**.  
  
     ![Изменить поставщика данных для OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  Несмотря на то что источник **файл базы данных Microsoft Access (OLE DB)** выглядит как правильный выбор, используйте этот тип источника данных только для MDB-файлы базы данных.  
  
8.  В **поставщик OLE DB**выберите **поставщик Microsoft Office 12.0 Access базы данных ядра OLE DB**.  
  
     ![OLE DB поставщика Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. В **имя сервера или файла**, укажите путь и имя ACCDB-файла, к которому вы хотите подключиться, а затем выберите **ОК**.  
  
    > [!NOTE]
    >  Если файл базы данных имя пользователя и пароль, укажите их, прежде чем выбрать **ОК**.  
  
10. Выберите **Далее** на **Выбор подключения базы данных** страницы.  
  
11. Выберите **Далее** на **сохранение подключения в файле конфигурации приложения** страницы.  
  
12. Разверните **таблиц** узел на **Выбор объектов базы данных** страницы.  
  
13. Выберите любой таблицы или представления в наборе данных и затем выберите **Готово**.  
  
     Набор данных добавляется в проект, а таблицы и представления отображаются в **источников данных** окна.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Создание набора данных для MDB-файл  
 Создайте набор данных, выполнив **мастер настройки источника данных**.  
  
#### <a name="to-create-the-dataset"></a>Создание набора данных  
  
1.  Откройте приложение Windows Forms, к которому требуется подключение к данным.  
  
2.  На **представление** меню, выберите **Other Windows** > **источников данных**.  
  
     ![Просмотр других источников данных Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  В окне **Источники данных** выберите **Добавить новый источник данных**.  
  
4.  Выберите **базы данных** на **Выбор типа источника данных** странице, а затем выберите **Далее**.  
  
5.  Выберите **набора данных** на **Выбор модели базы данных** странице, а затем выберите **Далее**.  
  
6.  На **Выбор подключения базы данных** выберите **новое подключение** для настройки нового подключения к данным.  
  
7.  Если источник данных не является **файл базы данных Microsoft Access (OLE DB)** выберите **изменение** открыть **изменение источника данных** и установите **Microsoft Доступ к файлу базы данных**, а затем выберите **ОК**.  
  
8.  В **имя файла базы данных**, укажите путь и имя MDB-файлу, к которому вы хотите подключиться, а затем выберите **ОК**.  
  
     ![Добавление подключения к файлу базы данных](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Выберите **Далее** на **Выбор подключения базы данных** страницы.  
  
10. Выберите **Далее** на **сохранение подключения в файле конфигурации приложения** страницы.  
  
11. Разверните **таблиц** узел на **Выбор объектов базы данных** страницы.  
  
12. Выберите любой таблицы или представления в наборе данных и затем выберите **Готово**.  
  
     Набор данных добавляется в проект, а таблицы и представления отображаются в **источников данных** окна.  
  
## <a name="security"></a>Безопасность  
 Хранение конфиденциальных сведений (например, пароля) может повлиять на безопасность приложений. Использование проверки подлинности Windows (также называемой встроенными средствами безопасности) — более безопасный способ управления доступом к базе данных. Дополнительные сведения см. в разделе [Защита сведений о подключении](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Следующие шаги  
 Набор данных, который вы только что создали, теперь доступна в **источников данных** окна. Теперь можно выполнять следующие задачи:  
  
-   Выберите элементы из **источников данных** окно и перетащите их на форму (см. в разделе [управляет привязки Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
-   Откройте этот источник данных в [конструктор наборов данных](../data-tools/creating-and-editing-typed-datasets.md) для добавления или изменения объектов, составляющих набор данных.  
  
-   Добавьте логику проверки <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> событий таблиц данных в наборе данных (см. в разделе [проверки данных в наборах данных](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>См. также  
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)

