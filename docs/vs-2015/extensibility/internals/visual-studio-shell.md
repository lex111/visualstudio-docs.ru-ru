---
title: Оболочка Visual Studio | Документация Майкрософт
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
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d96d4204e105324a9c209f74f9aee160c3eddde
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560137"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [оболочки Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/internals/visual-studio-shell).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Оболочки является основным агентом интеграции в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Оболочка предоставляет необходимые функции для выполнения пакетов VSPackage для совместного использования общих служб. Поскольку архитектуры цель [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] — vest основные функциональные возможности в пакеты VSPackage, оболочки — это платформа для предоставляют основные функциональные возможности и поддержки взаимодействия между его компонента пакетов VSPackage.  
  
## <a name="shell-responsibilities"></a>Обязанности оболочки  
 Оболочка имеет следующие ключевые обязанности:  
  
-   Поддержка (через COM-интерфейсы) основные элементы пользовательского интерфейса (UI). К ним относятся стандартных меню и панелей инструментов, рамок окна документа или дочерних окон интерфейса несколькими документами (MDI) и рамки окон инструментов и поддержку закрепления.  
  
-   Поддержание работающей список всех открытых документов в таблице выполняющихся документов (RDT), чтобы координировать сохранение документов и гарантирует, что для этого конкретного документа не удается открыть в более чем одним способом или несовместимые способами.  
  
-   Поддержка интерфейса маршрутизации команд и обработка команд, `IOleCommandTarget`.  
  
-   Загрузка пакетов VSPackage в нужное время. Отложенная загрузка VSPackage необходима для повышения производительности оболочки.  
  
-   Управление определенные общие службы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, который предоставляет функциональность базовая оболочка и <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, который предоставляет базовой функциональности окон.  
  
-   Управление файлами решения (SLN). Решения содержат группы связанных проектов, аналогичную файлам рабочей области (DSW) в Visual C++ 6.0.  
  
-   Выбор отслеживания всей оболочки, контекст и валюты. Оболочка отслеживает следующие элементы:  
  
    -   Текущий проект  
  
    -   Текущий элемент проекта или ItemID текущего <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   Текущее выделение для **свойства** окна или `SelectionContainer`  
  
    -   Контекст пользовательского интерфейса, идентификаторы или CmdUIGuids, управлять видимостью этих команд, меню и панелей инструментов  
  
    -   В настоящее время активных элементов, например активного окна, документа и диспетчер отмены  
  
    -   Атрибуты контекста пользователя, которые управляют Динамическая справка  
  
 Оболочка также включается в процесс взаимодействия между установленных пакетов VSPackage и текущей службы. Он поддерживает все базовые функции оболочки и делает их доступными для всех пакетов VSPackage, интегрированных в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Эти основные возможности включают следующее:  
  
-   **О** диалоговое окно и на заставку экрана  
  
-   **Добавление новых и добавить существующий элемент** диалоговые окна  
  
-   **Представление классов** окна и **обозревателя объектов**  
  
-   **Ссылки на** диалоговое окно  
  
-   **Структура документа** окно  
  
-   **Динамическая справка** окно  
  
-   **Найти** и **замените**  
  
-   **Откройте проект** и **открыть файл** диалоговых окон на **New** меню  
  
-   **Параметры** диалоговое окно на **средства** меню  
  
-   Окно **Свойства**  
  
-   **Обозреватель решений**  
  
-   **Список задач** окно  
  
-   **Панель элементов**  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)

