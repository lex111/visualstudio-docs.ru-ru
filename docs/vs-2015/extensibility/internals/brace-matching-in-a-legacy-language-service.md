---
title: Парные фигурные скобки в языковой службе прежних версий | Документация Майкрософт
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
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a2267805681b092c7a48537e72e5f0ca0b3ecb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559041"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Парные фигурные скобки в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [парные фигурные скобки в языковой службе прежних версий](https://docs.microsoft.com/visualstudio/extensibility/internals/brace-matching-in-a-legacy-language-service).  
  
Парные фигурные скобки позволяет разработчику отслеживать языковые элементы, которые должны применяться вместе, таких как круглые и фигурные скобки. Когда разработчик вводит закрывающую фигурную скобку, выделяется открывающей фигурной скобки.  
  
 Можно сопоставить два или три встречающиеся элементы (пары ") и триад. Триад — это набор из трех элементов, встречающиеся. Например, в C# `foreach` инструкции forms тройку: "`foreach()`«,»`{`«, и"`}`«. Все три элемента выделяются при вводе закрывающей фигурной скобки.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать парные фигурные скобки, см. в разделе [Пошаговое руководство: отображение парных фигурных скобок](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс поддерживает оба пары и позволяющая утроить с <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> и <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> методы.  
  
## <a name="implementation"></a>Реализация  
 Служба языка необходимо определить все соответствующие элементы на языке, а затем найдите все совпадающие пары. Обычно это выполняется путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> обнаружить соответствующий язык, а затем использовав <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод для сопоставления элементов.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод вызывает сканер для маркировки строке и возвращает токен, прямо перед курсором. Средство проверки указывает, что языковой пары элемент найден, задав значение маркера триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> на текущий маркер. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы методов <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод, который в свою очередь вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> метод со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> найти соответствующий элемент языка. Если найден соответствующий элемент языка, выделяются оба элемента.  
  
 Полное описание как вводить фигурную скобку активирует Выделение скобок, см. в разделе «Пример анализа Operation» в разделе [средства синтаксического анализа службы языка для прежних версий и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Включение поддержки парные фигурные скобки  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Можно задать атрибут `MatchBraces`, `MatchBracesAtCaret`, и `ShowMatchingBrace` именованные параметры, которые задать соответствующие свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Свойства предпочтения языка также могут задаваться пользователем.  
  
|Запись реестра|Свойство.|Описание|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Включает парные фигурные скобки|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Перемещает включает парные фигурные скобки, где находится курсор.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Выделяет соответствующую скобку.|  
  
## <a name="matching-conditional-statements"></a>Сопоставление условные операторы  
 Можно сопоставить условные операторы, такие как `if`, `else if`, и `else`, или `#if`, `#elif`, `#else`, `#endif`, в так же, как парные разделители. Вы можете подкласс <xref:Microsoft.VisualStudio.Package.AuthoringSink> класса и предоставить распространяется на метод, который можно добавить текст, а также разделителей внутренний массив соответствующих элементов.  
  
## <a name="setting-the-trigger"></a>Настройка триггера  
 Приведенный ниже показано, как обнаружить соответствующий круглые скобки, фигурные скобки и квадратные скобки и задание триггера для него в сканер. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод <xref:Microsoft.VisualStudio.Package.Source> класс определяет триггер и вызывает средство синтаксического анализа для поиска соответствующей пары (см. в разделе «Поиск Match» этой статьи). Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` идентификации и возвращает токены из строки текста.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="matching-the-braces"></a>Парные фигурные скобки  
 Ниже приведен упрощенный пример для сопоставления {} элементов языка, () и [] и добавление их диапазоны для <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта. Этот подход не является рекомендуемым для анализа исходного кода; Это только для иллюстративных целей.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Функции службы устаревшего языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

