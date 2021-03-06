---
title: Функция SccBeginBatch | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e62074fa30d68e4cd283fb431f0ae64cff957ed4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562103"
---
# <a name="sccbeginbatch-function"></a>Функция SccBeginBatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccBeginBatch](https://docs.microsoft.com/visualstudio/extensibility/sccbeginbatch-function).  
  
Эта функция начинает пакетное последовательность операций системы управления версиями. [SccEndBatch](../extensibility/sccendbatch-function.md) будет вызываться, чтобы завершить работу пакета. Эти пакеты не могут быть вложенными.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Пакет операций успешно начата.|  
|SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Пакеты управления источника используются для выполнения одинаковых операций во всех несколько проектов или в нескольких контекстах. Пакеты можно использовать во избежание избыточных проекта диалоговым окнам от работы во время пакетной операции. `SccBeginBatch` Функции и [SccEndBatch](../extensibility/sccendbatch-function.md) используются как пара функций для определения начала и окончания операции. Они не могут быть вложенными. `SccBeginBatch` Задает флаг, указывающий, что пакетная операция выполняется.  
  
 Пока действует пакетной операции, подключаемый модуль системы управления версиями следует не более одного диалогового окна для вопросов, пользователь получает и применить ответ в этом диалоговом окне для всех последующих операций.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)

