---
title: Удаление сведений системы управления версиями из. Proj и. SLN-файлов | Документация Майкрософт
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
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c6709d7808eba229455805ecb2b4a8d0c8af525
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572818"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Удаление сведений системы управления версиями из файлов PROJ и SLN
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [удаления из сведений системы управления версиями из. Proj и. SLN-файлов](https://docs.microsoft.com/visualstudio/extensibility/internals/removal-of-source-control-information-from-dot-proj-and-dot-sln-files).  
  
В версии 1.2 API подключаемых модулей управления источника SCC хранится в MSSCCPRJ. Файл SCC. Преимущество MSSCCPRJ. Файл SCC —, которое SCC сведения не исходные - контролируется, как в файлов proj и SLN.  
  
## <a name="version-12-changes"></a>Изменения в версии 1.2  
 В исходный элемент управления подключаемые модули, основанные на API подключаемых модулей управления исходной версии 1.1 сведения о системе управления версиями, хранится в проекта (.proj) и файлов решения (SLN). AuxPath указывается расположение базы данных сведений системы управления версиями, и конкретное расположение в базе данных задается ProjName. Это поведение может вызывать проблемы после ветви, разветвление или операций копирования, так как ProjName обычно будет недопустимым после любой из этих операций.  
  
 В API подключаемых модулей управления исходной версии 1.1, интегрированной среды разработки используется ~ SAK-файлов для обнаружения, если подключаемый модуль поддерживается MSSCCPRJ. Метод SCC хранения информация системы управления версиями. API подключаемых модулей управления исходной версии 1.2 предоставляет новую возможность для обнаружения поддержка MSSCCPRJ. Файл SCC без использования ~ SAK-файл. Дополнительные сведения см. в разделе [Устранение ~ SAK-файлов](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

