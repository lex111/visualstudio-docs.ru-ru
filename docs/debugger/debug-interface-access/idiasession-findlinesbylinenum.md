---
title: IDiaSession::findLinesByLinenum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d0cfcda8a48278abd8420e2c23954f5f7a22203
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464629"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
Определяет единицу компиляции, которая указанный номер строки в файле исходного кода находится в пределах или рядом с числом строк.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findLinesByLinenum (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `compiland`  
 [in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий компилируемого объекта, в котором выполняется поиск для номеров строк. Этот параметр не может быть `NULL`.  
  
 `file`  
 [in] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , представляющий исходный файл для поиска. Этот параметр не может быть `NULL`.  
  
 `linenum`  
 [in] Указывает номер строки с единицы.  
  
> [!NOTE]
>  Ноль нельзя использовать для указания всех строк (используйте [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) метод, чтобы найти все строки).  
  
 `column`  
 [in] Указывает номер столбца. Используйте ноль для указания всех столбцов. Столбец содержит смещение байтов в строку.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) получить objta со списком номеров строк.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как открыть исходный файл, перечислять компилируемые объекты, добавленные в этот файл и найдите номера строки в исходном файле, с которой начинается каждую единицу компиляции.  
  
```C++  
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)  
{  
    IDiaEnumSourceFiles* pEnum;  
    IDiaSourceFile*      pFile;  
    DWORD                celt;  
  
    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );  
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file  
    {  
        IDiaEnumSymbols* pEnumCompilands;  
        IDiaSymbol* pCompiland;  
  
        pFile->get_compilands ( &pEnumCompilands );  
        // for each compiland  
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )  
        {  
            IDiaEnumLineNumbers* pEnum;  
            // Find first compiland closest to line 1 of the file.  
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)  
            {  
                IDiaLineNumber *pLineNumber;  
                DWORD lineCount;  
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)  
                {  
                     DWORD lineNum;  
                     if (pLineNumber->get_line(&lineNum) == S_OK)  
                     {  
                          printf("compiland starts in source at line number = %lu\n",lineNum);  
                     }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)