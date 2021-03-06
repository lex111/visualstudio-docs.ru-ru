---
title: '&lt;fileAssociation&gt; элемент (приложение ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 3a3589387b00eb1ade9c9b60b0845bc2421b3486
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557919"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; элемент (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;fileAssociation&gt; элемент (приложение ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/fileassociation-element-clickonce-application).  
  
Определяет расширение файла, нужно связать с приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `fileAssociation` является необязательным. Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`extension`|Обязательно. Расширение файла, которое требуется связать с приложением.|  
|`description`|Обязательно. Описание типа файла для использования в оболочке.|  
|`progid`|Обязательно. Имя, однозначно определяющее тип файла.|  
|`defaultIcon`|Обязательно. Указывает значок, используемый для файлов с этим расширением. Файл значка должен быть указан с помощью [ \<файл > элемент](../deployment/file-element-clickonce-application.md) в [ \<сборки > элемент](../deployment/assembly-element-clickonce-application.md) , содержащий этот элемент.|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент необходимо включить ссылку на пространство имен XML для «urn: schemas-microsoft-com:clickonce.v1». Если `<fileAssociation>` элемент используется, он должен следовать после `<application>` элемент в его родительском объекте [ \<сборки > элемент](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] не перезаписывает существующие сопоставления файлов. Тем не менее приложения ClickOnce можно переопределить расширение файла для только для текущего пользователя. После удаления этого приложения ClickOnce, ClickOnce удаляет сопоставления файлов для пользователя и ассоциации на уровне компьютера является активным.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `fileAssociation` элементы в приложении манифеста для приложения редактор текста, развернутых с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Этот пример кода также включает [ \<файл > элемент](../deployment/file-element-clickonce-application.md) с требованиями `defaultIcon` атрибута.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)



