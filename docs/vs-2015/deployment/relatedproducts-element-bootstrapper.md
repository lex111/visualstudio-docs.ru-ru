---
title: '&lt;RelatedProducts&gt; элемент (загрузчик) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee65c4e4cacd4680256e34583559d74935a89e3b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559024"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; элемент (установщик)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;RelatedProducts&gt; элемент (загрузчик)](https://docs.microsoft.com/visualstudio/deployment/relatedproducts-element-bootstrapper).  
  
`RelatedProducts` Элемент определяет другие продукты, которые зависят от или включены в текущий продукт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `RelatedProducts` Элемент является дочерним элементом `Product` элемент. Он не имеет атрибутов.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct` Элемент указывает, что текущий продукт зависит от данного продукта, и что данного продукта должно быть установлено перед текущим объектом. Он является дочерним элементом `RelatedProducts` элемент. Объект `RelatedProducts` элемент может иметь один или несколько `DependsOnProduct` элементов.  
  
 `DependsOnProduct` содержит следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Code`|Кодовое имя включенного продукта, в соответствии с `ProductCode` атрибут `Product` элемента. Дополнительные сведения см. в разделе [ \<продукта > элемент](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts` Элемент определяет ноль или более `DependsOnProduct` элементов, и не имеет атрибутов. По крайней мере один `DependsOnProduct` в рамках этого курса необходимо установить перед текущего продукта. Объект `RelatedProducts` элемент может иметь ноль или более `EitherProducts` элементов.  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct` Элемент указывает, что продукт входит в состав текущей установки и не требует отдельной установки. Он является дочерним элементом `RelatedProducts` элемент. Объект `RelatedProducts` элемент может иметь один или несколько `IncludesProduct` элементов.  
  
 `IncludesProduct` содержит следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Code`|Кодовое имя включенного продукта, в соответствии с `ProductCode` атрибут `Product` элемента. Дополнительные сведения см. в разделе [ \<продукта > элемент](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Пример  
 В следующем примере кода указывает, что установщик Microsoft устанавливается вместе с [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]и поэтому не требует отдельной установки.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>См. также  
 [\<Продукт > элемент](../deployment/product-element-bootstrapper.md)



