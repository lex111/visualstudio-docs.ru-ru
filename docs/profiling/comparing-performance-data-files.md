---
title: Сравнение файлов данных о производительности | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20324a3026f5c32fcc1525f1c5afcd20b1b62332
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690735"
---
# <a name="compare-performance-data-files"></a>Сравнение файлов данных о производительности
Функция сравнения файлов данных средств профилирования позволяет выбрать два файла отчетов (*VSP* или *VSPS*) и создать отчет, в котором будут показаны различия и случаи снижения и повышения производительности в двух последовательных сеансах профилирования.  
  
 В отчете о сравнении файлов данных средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сравниваются результаты анализа в одном файле данных профилирования с базовыми результатами анализа в другом файле данных. Оба файла данных необходимо создавать с помощью одного и того же метода профилирования. Отчет о таком сравнении сохраняется в *VSPS*-файле.  
  
 В отчете о сравнении измененные данные представляются в табличном виде. В таблице показаны изменившиеся данные или отклонение от базового значения. Это отклонение вычисляется на основе разности между старым (базовым) значением и результатом нового анализа.  
  
 Сравнение данных профилирования может выполняться на основе функций кода, модулей приложения, строк, указателей инструкций и типов.  
  
 Доступные для сравнения данные профилирования включают сведения, отображаемые в столбцах. Определения имен этих столбцов см. в статье [Performance report views](../profiling/performance-report-views.md) (Представления отчетов о производительности).  
  
 Для снижения шума и фильтрации данных в строках таблицы сравнения, которые не изменились по сравнению с указанным значением, можно установить порог.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Практическое руководство. Сравнение файлов данных о производительности](../profiling/how-to-compare-performance-data-files.md)