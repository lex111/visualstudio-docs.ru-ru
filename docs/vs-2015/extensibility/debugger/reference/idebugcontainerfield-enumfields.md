---
title: IDebugContainerField::EnumFields | Документация Майкрософт
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
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a1fb33a65fb0bb86d3c043dd250b60b1533fed4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563275"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugContainerField::EnumFields](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield-enumfields).  
  
Создает перечислитель для полей контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwKindFilter`  
 [in] Сочетание [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) константы, выберите поля, которые необходимо перечислить. Типы полей можно описать типы хранилища, например класса или примитивных или определенные сведения, такие как local, параметра или указатель «this».  
  
 `dwModifiersFilter`  
 [in] Сочетание [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) константы, выберите поля, которые необходимо перечислить. Модификаторы поля могут быть разрешения на доступ, такие как public, private или хранения сведения, такие как виртуальные, статическими или окончательными.  
  
 `pszNameFilter`  
 [in] Имя поля, которые необходимо перечислить. Это может быть значение null, если все поля должны быть возвращены.  
  
 `nameMatch`  
 [in] Значение из [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) перечисление, управляет ли поиск с учетом регистра, или нет.  
  
 `ppEnum`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список полей. Возвращает значение null, если нет полей.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK или S_FALSE, если нет полей. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `dwKindFilter`, `dwModifiersFilter`, И `pszNameFilter` параметры можно объединить, например, чтобы выбрать все публичные виртуальные методы, с именем «MyMethod».  
  
## <a name="see-also"></a>См. также  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)

