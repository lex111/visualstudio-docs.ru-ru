---
title: Практическое руководство. Инструментирование динамически скомпилированного веб-приложения ASP.NET и сбор профилировщиком подробных данных о времени с помощью командной строки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c140ae2-ecdd-48c7-bd89-3dc1b88e19b0
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e815170640b57a667b71aac3e9e3526e2fe8b275
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592524"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Практическое руководство. Инструментирование динамически скомпилированного веб-приложения ASP.NET и сбор профилировщиком подробных данных о времени с помощью командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: инструментирование динамически скомпилированные веб-приложения ASP.NET и Сбор подробных данных о времени с Profiler с помощью командной строки](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line).  
  
В этой статье описывается, как с помощью средств профилирования командной строки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] собрать подробные данные о времени для динамически скомпилированного приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], используя метод профилирования с инструментированием.  
  
> [!NOTE]
>  Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь к программам в переменную среды PATH окна командной строки или в саму команду. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Чтобы собрать данные о производительности из веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], следует изменить файл web.config для этого приложения, разрешив использование средства [VSInstr.exe](../profiling/vsinstr.md) для инструментирования динамически компилируемых файлов приложения. После этого с помощью средства [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) нужно задать соответствующие переменные среды на веб-сервере, которые включат профилирование, и перезагрузить компьютер.  
  
 Запустите профилировщик, а затем — нужное приложение. Когда профилировщик будет подключен к приложению, можно будет приостанавливать и возобновлять сбор данных. Завершив сеанс профилирования, закройте приложение и рабочий процесс служб Internet Information Services (IIS), затем завершите работу профилировщика. Когда работа по профилированию будет завершена, восстановите исходное состояние файла web.config и настроек веб-сервера.  
  
## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Настройка веб-приложения ASP.NET и веб-сервера  
  
#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Процедура настройки веб-приложения ASP.NET и веб-сервера  
  
1.  Измените файл web.config для целевого приложения. См. статью [How to: Modify Web.Config Files to Instrument and Profile Dynamically Compiled ASP.NET Web Applications](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md) (Практическое руководство. Изменение файлов Web.Config для инструментирования и профилирования динамически скомпилированных веб-приложений ASP.NET).  
  
2.  Откройте окно командной строки.  
  
3.  Инициализируйте переменные среды профилирования. Тип:  
  
     **VSPerfClrEnv /globaltraceon**  
  
    -   Параметр **/globaltraceon** включает профилирование с использованием метода инструментирования.  
  
4.  Перезагрузите компьютер.  
  
## <a name="running-the-profiling-session"></a>Запуск сеанса профилирования  
  
#### <a name="to-profile-the-web-application"></a>Процесс профилирования веб-приложения  
  
1.  Откройте окно командной строки.  
  
2.  Запуск профилировщика. Тип:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   Параметр **/start:trace** инициализирует профилировщик.  
  
    -   Параметр **/output**`OutputFile` является обязательным при использовании параметра **/start**. `OutputFile` указывает имя и расположение файла данных профилирования (VSP-файла).  
  
     С параметром **/start:trace** можно использовать любой из следующих параметров.  
  
    > [!NOTE]
    >  Параметры **/user** и **/crosssession** обычно являются обязательными для приложений ASP.NET.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Указывает домен и имя пользователя учетной записи, которая является владельцем рабочего процесса ASP.NET. Этот параметр является обязательным, если процесс выполняется от имени пользователя, отличного от пользователя, вошедшего в систему. Владелец процесса указан в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.|  
    |[/crossession](../profiling/crosssession.md)|Включает профилирование процессов в других сеансах входа. Этот параметр является обязательным, если приложение ASP.NET выполняется в другом сеансе. Идентификатор сеанса указан в столбце "Идентификатор сеанса" на вкладке "Процессы" в диспетчере задач Windows. **/CS** можно указать как краткую версию **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Запускает профилировщик в состоянии приостановки сбора данных. Используйте параметр [/globalon](../profiling/globalon-and-globaloff.md) для возобновления профилирования.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Собирает данные от счетчика производительности процессора, указанного в `Config`. Сведения о счетчике добавляются в данные, собранные для каждого события профилирования.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Задает счетчик производительности Windows, данные которого будут собираться во время профилирования.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Используется с только с параметром **/wincounter**. Указывает время (в миллисекундах) между событиями сбора счетчика производительности Windows. Значение по умолчанию — 500 мс.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Задает события трассировки событий для Windows (ETW), собираемые во время профилирования. События трассировки событий Windows собираются в отдельный ETL-файл.|  
  
3.  Запустите приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] обычным образом.  
  
## <a name="controlling-data-collection"></a>Управление сбором данных  
 Пока выполняется целевое приложение, вы можете управлять сбором данных, останавливая и возобновляя процесс записи данных в файл данных профилировщика с помощью параметров **VSPerfCmd.exe**. Управление сбором данных позволяет собирать данные на конкретных этапах выполнения программы, например при запуске или завершении работы приложения.  
  
#### <a name="to-start-and-stop-data-collection"></a>Запуск и остановка сбора данных  
  
-   Следующие пары параметров запускают и останавливают сбор данных. Каждый параметр необходимо указывать в отдельной командной строке. Сбор данных можно включать и отключать несколько раз.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Запускает (**/globalon**) или останавливает (**/globaloff**) сбор данных для всех процессов.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Запускает (**/processon**) или останавливает (**/processoff**) сбор данных для процесса с указанным идентификатором процесса (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Запускает (**/threadon**) или останавливает (**/threadoff**) сбор данных для потока с указанным идентификатором потока (`TID`).|  
  
-   Можно также использовать параметр **VSPerfCmd.exe**[/mark](../profiling/mark.md) для добавления метки профилирования в файл данных. Команда **/mark** добавляет идентификатор, отметку времени и необязательную определяемую пользователем текстовую строку. Метки можно использовать для фильтрации данных в представлениях отчетов и данных профилировщика.  
  
## <a name="ending-the-profiling-session"></a>Завершение сеанса профилирования  
 Чтобы завершить сеанс профилирования, закройте целевое веб-приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], сбросьте параметры IIS для остановки профилируемого процесса, затем завершите работу профилировщика.  
  
#### <a name="to-end-a-profiling-session"></a>Завершение сеанса профилирования  
  
1.  Закройте веб-приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Закройте рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], сбросив Internet Information Services (IIS). Тип:  
  
     **IISReset /stop**  
  
3.  Завершите работу профилировщика. Тип:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
4.  Перезапустите IIS. Тип:  
  
     **IISReset /start**  
  
## <a name="restoring-the-application-and-computer-configuration"></a>Восстановление конфигурации приложения и компьютера  
 Завершив все запланированные сеансы профилирования, восстановите прежнюю версию файла web.config, очистите переменные среды, установленные для профилирования, и перезагрузите компьютер, чтобы сервер и приложение вернулись в то состояние, в котором они работали до профилирования.  
  
#### <a name="to-restore-the-application-and-computer-configuration"></a>Восстановление конфигурации приложения и компьютера  
  
1.  Замените файл web.config копией исходного файла.  
  
2.  Очистите переменные среды, установленные для профилирования. Тип:  
  
     **VSPerfCmd /globaloff**  
  
3.  Перезагрузите компьютер.  
  
## <a name="see-also"></a>См. также  
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Представление данных метода инструментирования](../profiling/instrumentation-method-data-views.md)



