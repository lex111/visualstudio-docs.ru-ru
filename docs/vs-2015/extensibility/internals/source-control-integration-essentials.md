---
title: Источника Essentials Интеграция управления | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37508599b01f2639df416c56181f1c9b8672cd5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563296"
---
# <a name="source-control-integration-essentials"></a>Основные элементы интеграции системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Essentials интеграции управления источника](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-integration-essentials).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает два типа интеграция системы управления версиями: подключаемый модуль источника управления, который предоставляет базовые функциональные возможности и построен с использованием источника управления Plug-in API (прежнее название MSSCCI API) и интеграции решения управления исходный пакет VSPackage, предоставляет функциональные возможности более надежной.  
  
## <a name="source-control-plug-in"></a>Подключаемый модуль системы управления версиями  
 Подключаемый модуль системы управления источника записывается как библиотеку DLL, которая реализует API подключаемых модулей управления источника. Регистрация и источника управления интеграцией предоставляется через API. Этот подход проще в реализации, чем пакет VSPackage системы управления версиями, и он использует [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пользовательский интерфейс (UI) для большинства операций управления версиями.  
  
 Реализация системы управления версиями, подключаемый модуль с помощью API подключаемого модуля управления источника, выполните следующие действия.  
  
1.  Создать библиотеку DLL, который реализует функции, указанные в [подключаемых модулей системы управления версиями](../../extensibility/source-control-plug-ins.md).  
  
2.  Регистрации библиотеки DLL, сделав соответствующие записи в реестр, как описано в разделе [как: установить подключаемый модуль системы управления источника](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Создать вспомогательный объект пользовательского интерфейса и отобразить ее при появлении запроса адаптера пакет системы управления версиями ( [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] компонент, который обрабатывает функции системы управления версиями через подключаемых модулей системы управления версиями).  
  
 Дополнительные сведения см. в разделе [Создание подключаемого модуля управления источника](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Пакет VSPackage управления версиями  
 Реализацию VSPackage системы управления версиями можно разрабатывать настраиваемый заменой [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] система управления версиями пользовательского интерфейса. Такой подход обеспечивает полный контроль над интеграция системы управления версиями, но он требует предоставления элементов пользовательского интерфейса и реализует интерфейсы управления источника, которые в противном случае будет передаваться в метод подключаемого модуля.  
  
 Для реализации пакета VSPackage системы управления версиями, необходимо сделать следующее:  
  
1.  Создать и зарегистрировать свои собственные системы управления версиями VSPackage, как описано в разделе [регистрации и выбора](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Замените настраиваемого пользовательского интерфейса системы управления версиями по умолчанию пользовательского интерфейса. См. в разделе [настраиваемый пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Укажите глифов для использования и обработки **обозревателе решений** события глифа. См. в разделе [элемент управления глифа](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Обрабатывать события изменения запросов и сохранения запроса, как показано в [запроса изменить запрос Сохранить](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Дополнительные сведения см. в разделе [Создание пакета VSPackage управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

