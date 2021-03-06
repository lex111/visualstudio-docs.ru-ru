---
title: '&lt;зависимость&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
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
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 735b37196586f540186a3ca43c9c315ede51d084
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563696"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;зависимость&gt; элемент (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;зависимостей&gt; элемент (развертывание ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/dependency-element-clickonce-deployment).  
  
Определяет версию приложения для установки и расположение манифеста приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `dependency` Элемент является обязательным. Он не имеет атрибутов. Манифест развертывания может иметь несколько `dependency` элементов.  
  
 `dependency` Элемент обычно выражает зависимости для основного приложения для сборок, содержащихся в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Если приложение Main.exe использует сборку DotNetAssembly.dll, этой сборки должны быть перечислены в разделе зависимостей. Зависимость, тем не менее, также можно выразить другие типы зависимостей, такие как зависимость от определенной версии среды CLR, от сборки в глобальный кэш сборок (GAC) или COM-объекта. Так как он является технологией развертывания нет-touch, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] не может инициировать загрузку и установку этих типов зависимостей, но она может помешать выполнению приложения Если один или несколько указанных зависимостей не существует.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Обязательно. Этот элемент содержит `assemblyIdentity` элемент. В следующей таблице показаны атрибуты `dependentAssembly` поддерживает.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`preRequisite`|Необязательный. Указывает, что эта сборка должна уже существовать в глобальном кэше СБОРОК. Допустимые значения: `true` и `false`. Если `true`и указанная сборка не существует в глобальном кэше СБОРОК, приложение не запускается.|  
|`visible`|Необязательный. Определяет идентификатор приложения верхнего уровня, включая все зависимости. Используется внутренне [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] для управления хранилищем приложения и активации.|  
|`dependencyType`|Обязательно. Связь между этой зависимости и приложением. Допустимые значения:<br /><br /> -   `install`. Компонент представляет отдельной установкой из текущего приложения.<br />-   `preRequisite`. Компонент, необходимый для текущего приложения.|  
|`codebase`|Необязательный. Полный путь к манифесту приложения.|  
|`size`|Необязательный. Размер манифеста приложения, в байтах.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательно. Этот элемент является дочерним по отношению к элементу `dependentAssembly`. Содержание `assemblyIdentity` должен быть таким же, как описано в разделе [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. В следующей таблице показаны атрибуты `assemblyIdentity` элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Определяет имя приложения.|  
|`Version`|Обязательно. Указывает номер версии приложения, в следующем формате: `major.minor.build.revision`|  
|`publicKeyToken`|Обязательно. Задает 16-знаковая шестнадцатеричную строку, которая представляет последние 8 байтов хэша SHA-1 открытого ключа, которым подписаны приложение или сборка. Открытый ключ, используемый для входа должно быть 2048 бит или более поздней версии.|  
|`processorArchitecture`|Обязательно. Указание микропроцессора. Допустимые значения: `x86` для 32-разрядной Windows и `IA64` для 64-разрядной Windows.|  
|`Language`|Необязательный. Определяет две части кодов языка сборки. Например EN-US, предназначенную для английского языка (США). Значение по умолчанию — `neutral`. Этот элемент имеет `asmv2` пространства имен.|  
|`type`|Необязательный. Для обеспечения обратной совместимости с Windows side-by-side установить технологии. Единственное допустимое значение — `win32`.|  
  
## <a name="hash"></a>hash  
 `hash` Элемент является необязательного дочернего элемента `file` элемент. `hash` Элемент не имеет атрибутов.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] использует алгоритма хэш всех файлов в приложении как средство проверки безопасности, чтобы убедиться, что ни один из файлов был изменен после развертывания. Если `hash` элемент не включен, эта проверка не выполняется. Таким образом, пропуск `hash` элемента не рекомендуется.  
  
## <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Элемент является обязательным дочерним элементом `hash` элемент. `dsig:Transforms` Элемент не имеет атрибутов.  
  
## <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Элемент является обязательным дочерним элементом `dsig:Transforms` элемент. В следующей таблице показаны атрибуты `dsig:Transform` элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственное значение, используемое [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] является `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Элемент является обязательным дочерним элементом `hash` элемент. В следующей таблице показаны атрибуты `dsig:DigestMethod` элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственное значение, используемое [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] является `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Элемент является обязательным дочерним элементом `hash` элемент. `dsig:DigestValue` Элемент не имеет атрибутов. Его текстовое значение является хэшем для указанного файла.  
  
## <a name="remarks"></a>Примечания  
 Манифесты развертывания обычно имеют один `assemblyIdentity` элемент, который определяет имя и версию манифеста приложения.  
  
## <a name="example"></a>Пример  
 В следующем коде показано в примере `dependency` элемент [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест развертывания.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода определяет зависимость от сборки уже установлены в глобальном кэше СБОРОК.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода указана зависимость от определенной версии среды CLR.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода задает зависимость операционной системы.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<зависимость > элемент](../deployment/dependency-element-clickonce-application.md)



