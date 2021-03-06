---
title: Фрагменты кода для R
description: Фрагменты кода R в Visual Studio позволяют быстро вставлять блоки кода произвольной длины, помогая избежать повторного ввода одинакового кода снова и снова.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 0c9db243b3903ddcbaa310bbf5ba3fd911eee7fc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35667734"
---
# <a name="code-snippets"></a>Фрагменты кода

Фрагменты кода в Visual Studio позволяют быстро вставлять блоки кода произвольной длины, помогая избежать повторного ввода одинакового кода снова и снова. В инструментах R для Visual Studio (RTVS) имеется множество полезных фрагментов кода R, которые дополняют коллекцию фрагментов кода Visual Studio.

Чтобы вставить фрагмент, введите сокращенное название фрагмента (поддерживается технология IntelliSense), а затем нажмите клавишу **TAB** для вставки.

Вот несколько простых примеров.

- Введите `=`, затем нажмите клавишу TAB, после чего RTVS предложит оператор присваивания `<-`.
- Введите `>`, затем нажмите клавишу TAB, после чего RTVS предложит оператор конвейера `%>%`.

Фрагменты кода могут быть намного большим, чем просто завершение символов. Фрагмент кода для чтения файла CSV с помощью функции `read.csv`, например, может освободить вас от необходимости запоминать имена параметров:

![Анимации использования фрагмента кода для вставки вызова read.csv](media/code-snippet-expansion.gif)

В этом случае при вводе `readc` IntelliSense отображает список завершения. При выборе этого варианта в раскрывающемся списке и нажатии клавиши **TAB** выбирается вариант `readc`, а при повторном нажатии клавиши **TAB** фрагмент кода снова расширяется. (По этой причине расширение фрагмента кода зачастую рассматривается как "ввод фрагмента кода и двойное нажатие клавиши TAB".) В большинстве случаев при первом нажатии клавиши TAB завершается выбор варианта, предложенного IntelliSense, а при втором нажатии TAB запускается развертывание.

Чтобы просмотреть все доступные фрагменты кода, выберите **Сервис** > **Диспетчер фрагментов кода** (или нажмите клавиши **CTRL**+**K**, **B**) и выберите **R** для параметра **Язык**. Разверните группы и выберите отдельные фрагменты кода, чтобы ознакомиться с описанием и ярлыком.

![Диалоговое окно "Диспетчер фрагментов кода" для R](media/code-snippet-dialog.png)

Сведения о создании настраиваемых фрагментов кода см. в разделе [Пошаговое руководство. Создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md). В конечном счете фрагмент кода предоставляет собой лишь XML-файл. Например, ниже приведен фрагмент кода для оператора конвейера (ярлык `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

XML-файлы для всех фрагментов кода устанавливаются вместе с RTVS; путь указан в поле **Расположение** в диалоговом окне **Диспетчер фрагментов кода**. Их также можно найти в исходном коде RTVS на сайте GitHub в разделе [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
