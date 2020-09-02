---
title: 'IDiaSession:: findInlineeLinesByLinenum | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d16bc6f3e2e8f190e3a26023407237509984cece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804230"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo v zadaném zdrojovém souboru a čísle řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compiland`  
 pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje kompilantu, ve kterém chcete vyhledat čísla řádků. Tento parametr nemůže být `NULL` .  
  
 `file`  
 pro Objekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , který představuje zdrojový soubor, ve kterém se má hledat. Tento parametr nemůže být `NULL` .  
  
 `linenum`  
 pro Určuje číslo řádku založené na jednom čísle.  
  
> [!NOTE]
> Hodnotu nula nelze použít k určení všech řádků (k vyhledání všech řádků použijte metodu [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) ).  
  
 `column`  
 pro Určuje číslo sloupce. K určení všech sloupců použijte nulu. Sloupec je posun bajtů na řádek.  
  
 `ppResult`  
 mimo Vrátí objekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , který obsahuje seznam čísel řádků, které byly načteny.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Výčet SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
