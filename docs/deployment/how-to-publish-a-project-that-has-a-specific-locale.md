---
title: 'Практическое: публикация проекта, имеющего конкретный языковый стандарт | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26e96116ca03cad074639c5753a8cb076dc70adf
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281979"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Практическое: публикация проекта, имеющего конкретный языковый стандарт
Приложения нередко содержат компоненты с разными языковыми стандартами. В данном сценарии вы создадите решение, включающее несколько проектов, а затем опубликуете отдельные проекты для каждого языкового стандарта. Эта процедура показывает, как использовать макрос для публикации первого проекта в решении, на примере языкового стандарта "en". Если вы хотите выполнить данную процедуру с другим языковым стандартом, выберите в макросе соответствующее значение `localeString` (например, "de" или "de-DE").  
  
> [!NOTE]
>  При использовании данного макроса расположение публикации должно быть выражено действительным URL-адресом или UNC-путем к общей папке. Также на компьютере должны быть установлены службы IIS. Установка служб IIS, в **запустить** меню, щелкните **панели управления**. Дважды щелкните **Установка и удаление программ**. В **Установка и удаление программ**, нажмите кнопку **Установка и удаление компонентов Windows**. В **мастер компонентов Windows**выберите **Internet Information Services (IIS)** флажок в **компоненты** списка. Нажмите кнопку **Готово** чтобы закрыть мастер.  
  
### <a name="to-create-the-publishing-macro"></a>Создание макроса публикации  
  
1.  Чтобы открыть обозреватель макросов, в **средства** последовательно выберите пункты **макросы**, а затем нажмите кнопку **обозреватель макросов**.  
  
2.  Создайте макромодуль. В обозревателе макросов выберите **MyMacros**. На **средства** последовательно выберите пункты **макросы**, а затем нажмите кнопку **макромодуль**. Присвойте модулю имя **PublishSpecificCulture**.  
  
3.  В обозревателе макросов разверните **MyMacros** узел, а затем откройте **PublishAllProjects** модуля, дважды щелкнув его (или из **средства** последовательно выберите пункты **Макросы**, а затем нажмите кнопку **IDE для макросов**).  
  
4.  В интегрированной среде разработки макросов добавьте в модуль следующий код после операторов `Import`:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certficate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Закройте интегрированную среду разработки макросов. После этого вы вернетесь в Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Публикация проекта для отдельного языкового стандарта  
  
1.  Создание проекта приложения Windows в Visual Basic, на **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **проекта**.  
  
2.  В **новый проект** выберите **приложения Windows** из **Visual Basic** узла. Назовите проект *проект PublishLocales*.  
  
3.  Откройте форму 1. В **свойства** окна в разделе **разработки**, изменить **языка** свойства из **(по умолчанию)** для **Английский**. Изменение **текст** свойства формы **MyForm**.  
  
     Обратите внимание, что локализованные источники DLL не создаются, пока в них возникает необходимость. Например, они создаются в случае изменении текста формы или одного из элементов управления после того, как будет указан новый языковой стандарт.  
  
4.  Публикация *проект PublishLocales* с помощью Visual Studio IDE.  
  
     В **обозревателе решений**выберите *проект PublishLocales*. На **проекта** меню, выберите **свойства**. В конструкторе проектов на **публикации** укажите расположение для публикации **http://localhost/PublishLocales**, а затем нажмите кнопку **Опубликовать сейчас**.  
  
     Когда откроется веб-страница публикации, закройте ее. (Для этого шага необходимо только опубликовать проект, установка не требуется.)  
  
5.  Публикация *проект PublishLocales* еще раз, вызвав макрос в окне командной строки Visual Studio. Чтобы открыть окно командной строки на **представление** последовательно выберите пункты **Other Windows** и нажмите кнопку **командное окно**, или нажмите клавишу **Ctrl** + **Alt**+**объект**. В окне командной строки введите `macros`; автоматическое завершение будет предоставлен список доступных макросов. Выберите следующий макрос и нажмите клавишу ВВОД:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  После успешного завершения процесса публикации, он создаст сообщение «Публикация успешно завершена для *макроса publishlocales\publishlocales.vbproj успешно завершена*. Язык публикации: en". Нажмите кнопку **ОК** в окне сообщения. Когда откроется веб-страница публикации, щелкните **установить**.  
  
7.  Искать в *C:\Inetpub\wwwroot\PublishLocales\en*. Вы увидите установленные файлы, такие как манифесты, *setup.exe*и файл публикации веб-страницы, в дополнение к библиотеке DLL локализованных ресурсов. (По умолчанию ClickOnce добавляет *.deploy* расширение EXE и DLL; это расширение можно удалить после развертывания.)  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Среда разработки макросов](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))   
 [Обозреватель макросов-окно](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))   
 [Способы: измените и программным способом создать макросы](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))