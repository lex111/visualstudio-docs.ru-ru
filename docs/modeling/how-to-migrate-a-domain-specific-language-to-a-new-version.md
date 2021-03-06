---
title: Практическое руководство. Перенос доменного языка в новую версию
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6a238eabbcba4f28b12f899de5b2d4eae30cfef9
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858773"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Практическое руководство. Перенос доменного языка в новую версию
Вы можете перенести проекты, определение и использование предметно ориентированного языка для [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] из версии [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , включенного в состав [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Средство миграции предоставляется как часть [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Средство преобразует проекты и решения, использующих или определите средства доменного языка Visual Studio.

 Необходимо запустить средство миграции явным образом: она не запускается автоматически при открытии решения в Visual Studio. Средства и подробные руководства можно найти по этому пути:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Перед переносом проекты DSL
 Средство миграции изменяет файлы проекта Visual Studio (**.csproj**) и файлы решений (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Для подготовки к миграции проектов.

-   Убедитесь, что **.csproj** и **.sln** файлы могут быть записаны. Если они находятся в системе управления версиями, убедитесь, что они будут извлечены.

-   Создайте копию папки, которые планируется перенести.

## <a name="migrating-a-collection-of-projects"></a>Перенос коллекции проектов

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Чтобы перенести проекты DSL и решения в Visual Studio 2010

1.  Запустите средство миграции DSL.

    -   Дважды щелкните средство в проводнике Windows (или проводника) или запустите средство из командной строки. Средство находится в этом расположении:

         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2.  Выберите папку, содержащую решения и проекты, которые требуется преобразовать.

    -   Введите путь в поле в верхней части инструмента, или нажмите кнопку **Обзор**.

     Средство миграции дерево проектов, которые определяют или использовать DSL. Дерево включает в себя каждого проекта, использующего **Microsoft.VisualStudio.Modeling.Sdk** или **TextTemplating** сборки.

3.  Просмотрите дерево проектов и снимите флажок проекты, которые вы не хотите преобразовать.

    -   Выберите проект или решение, чтобы просмотреть список изменений, это средство максимально.

        > [!NOTE]
        >  Флажки, которые отображаются рядом с имена папок не оказывают влияния. Необходимо развернуть все папки, чтобы проверять проекты и решения.

4.  Преобразуйте проекты.

    1.  Нажмите кнопку **преобразовать**.

         До преобразования каждый файл проекта, копии _проекта_**.csproj** сохраняется как _проекта_**. vs2008.csproj**

         Копию каждого _решение_**.sln** сохраняется как _решение_**. vs2008.sln**

    2.  Исследуйте любой сбой преобразования, включенные в отчет.

         Ошибки выводятся в текстовом окне. Кроме того в представлении дерева отображаются красный флаг на каждом узле, который не удалось преобразовать. Можно щелкнуть узел, чтобы получить дополнительные сведения об этой ошибке.

5.  **Преобразовать все шаблоны** в решениях, содержащий успешно преобразовать проекты.

    1.  Откройте решение.

    2.  Нажмите кнопку **преобразовать все шаблоны** кнопку в заголовке обозревателя решений.

        > [!NOTE]
        >  Это можно сделать ненужные. Дополнительные сведения см. в разделе [как автоматизировать преобразовать все шаблоны](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6.  Обновите пользовательский код в преобразованные проекты.

    -   Попытка построить проекты и исследовать все ошибки.

    -   Проверьте конструктор.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>См. также

- [Связанные записи в блогах](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)