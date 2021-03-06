---
title: 'Практическое: изменение пространства имен доменного языка | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1407b0ca77ea6f19bc6f6f165d5524c305b69d0f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592705"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Практическое руководство. Изменение пространства имен доменного языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: изменение пространства имен доменного языка](https://docs.microsoft.com/visualstudio/modeling/how-to-change-the-namespace-of-a-domain-specific-language).  
  
Вы можете изменить пространство имен доменного языка. Необходимо внести изменения в **обозреватель DSL**в свойствах проекта Dsl и в сведениях о сборке.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Чтобы изменить пространство имен доменного языка  
  
1.  В **обозреватель DSL**, нажмите кнопку **Dsl** узла.  
  
2.  В **свойства** измените **пространства имен** свойство.  
  
3.  Сохраните решение и преобразования шаблонов.  
  
4.  На **проекта** меню, щелкните **Dsl свойства**.  
  
     Отобразятся свойства проекта.  
  
5.  Перейдите на вкладку **Приложение** .  
  
6.  Изменение **пространство имен по умолчанию** свойство на новое имя пространства имен.  
  
7.  Если требуется, чтобы изменить имя сборки, измените **свойство имени сборки.**  
  
8.  Если вы изменили имя сборки, откройте DslPackage\Package.tt и обновите следующую строку:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Если вы написали ни строчки кода, не забудьте заменить ссылки на пространство имен и класс в файлах кода.  
  
10. Сброс Visual Studio экспериментального экземпляра.  
  
    1.  Удалить **\Users\\**_{имя}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  В Windows **запустить** меню, выберите **все программы**, **Microsoft Visual Studio 2010 SDK**, **средства**, **сброса Экспериментальный экземпляр**.  
  
11. На **построения** меню, выберите **Перестроить решение**.  
  
## <a name="see-also"></a>См. также  
 [Глоссарий по средствам доменного языка работы](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



