---
title: Переход по отношениям с помощью UML API | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3ae6da2980c55df6eb58686fcdb2c364b9147779
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560987"
---
# <a name="navigate-relationships-with-the-uml-api"></a>Переход по отношениям с помощью UML API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [переход по отношениям с помощью UML API](https://docs.microsoft.com/visualstudio/modeling/navigate-relationships-with-the-uml-api).  
  
Модель состоит из элементов, связанных друг с другом разными видами отношений. В этом разделе описывается переход по модели в коде программы.  
  
## <a name="traversing-relationships"></a>Обход отношений  
  
### <a name="any-relationship"></a>Любое отношение  
 Используйте `GetRelatedElements<T>()` для поиска всех элементов, подключенных к указанному элементу. Либо задайте для `T` значение `IRelationship`, чтобы выполнить обход всех видов отношений, либо используйте более конкретный тип, такой как `IAssociation`, чтобы выполнить обход только этого типа отношений.  
  
```  
IElement anElement;  
// Select all elements related to anElement.  
Context.CurrentDiagram.SelectShapes (  
   anElement.GetRelatedElements<IRelationship>()  
    .SelectMany(e=>e.Shapes()).ToArray());  
  
```  
  
 Используйте `GetRelatedLinks<T>()` для поиска всех отношений, связанных с элементом.  
  
```  
// Process all relationships connected to an element.  
foreach (IRelationship relationship in   
   anElement.GetRelatedLinks<IRelationship>())  
{  
  Debug.Assert(relationship.SourceElement == anElement  
      || relationship.TargetElement == anElement);  
}  
  
```  
  
### <a name="association"></a>Ассоциация  
 Ассоциация — это отношение между двумя свойствами, каждое из которых принадлежит к классификатору.  
  
```  
IClassifier classifier; // class, interface, component, actor, ...  
// Get all the associations sourced from this classifier  
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())  
{  
  // p represents the end further end of an association.  
  IType oppositeElement = p.Type;   
    // The type to which this association connects classifier  
  
  IProperty oppositeProperty = p.Opposite;  
    // The nearer end of the association.  
  Debug.Assert(oppositeProperty.Type == classifier);  
  IAssociation association = p.Association;  
  Debug.Assert(association.MemberEnds.Contains(p)  
     && association.MemberEnds.Contains(oppositeProperty));  
}  
```  
  
### <a name="generalization-and-realization"></a>Обобщение и реализация  
 Получите доступ к обобщению с обоих концов:  
  
```  
foreach (IClassifier supertype in classifier.Generals) {…}  
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}  
Access the relationship itself:  
foreach (IGeneralization gen in classifier.Generalizations)   
{ Debug.Assert(classifier == gen.Specific); }  
```  
  
```  
  
/// InterfaceRealization:  
IEnumerable<IInterface> GetRealizedInterfaces  
    (this IBehavioredClassifier classifier);  
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers  
    (this IInterface interface);  
  
```  
  
### <a name="dependency"></a>Зависимость  
  
```  
/// Returns the elements depending on this element  
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);   
/// Returns the elements this element depends on  
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);  
  
```  
  
### <a name="activity-edge"></a>Граница действия  
  
```  
/// Returns the nodes targeted by edges outgoing from this one  
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);  
/// Returns the nodes sourcing edges incoming to this one  
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);  
  
```  
  
### <a name="connector-assembly-and-delegation"></a>Соединитель (сборка и делегирование)  
  
```  
/// Returns the elements connected via assembly   
/// or delegation to this one  
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);  
  
```  
  
### <a name="messages-and-lifelines"></a>Сообщения и линии жизни  
  
```  
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);   
// both from lifeline and execution occurrences  
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);  
ILifeline GetSourceLifeline(this IMessage message);   
    // may return null for found messages  
ILifeline GetTargetLifeline(this IMessage message);    
    // may return null for lost messages  
  
```  
  
### <a name="package-import"></a>Импорт пакета  
  
```  
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);  
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);  
  
```  
  
### <a name="use-case-extend-and-include"></a>Расширение и включение варианта использования  
  
```  
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);  
```  
  
## <a name="enumerating-relationships"></a>Перечисление отношений  
 Все свойства модели UML, которые возвращают несколько значений, соответствующих интерфейсу IEnumerable<>. Это означает, что можно использовать [выражения запросов Linq](http://go.microsoft.com/fwlink/?LinkId=168834) и методы расширения, определенные в **System.Linq** пространства имен.  
  
 Пример:  
  
```  
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()  
where shape.Color == System.Drawing.Color.Red  
select shape.Element  
  
```  
  
## <a name="see-also"></a>См. также  
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Навигация по модели UML](../modeling/navigate-the-uml-model.md)



