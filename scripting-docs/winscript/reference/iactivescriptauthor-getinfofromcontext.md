---
title: 'Iactivescriptauthor –:: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 457b2ad1bda3226caf3604e3ccd6b976f01bca83
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576216"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Vrátí informace o typu a pozice ukotvení pro daný znak v bloku kódu. Poskytuje informace pro členské technologie IntelliSense, globální seznamy a popisy parametrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 pro Adresa řetězce bloku kódu použitého k vygenerování výsledků informací.  
  
 `cchCode`  
 pro Délka bloku kódu.  
  
 `ichCurrentPosition`  
 pro Pozice znaku relativní vzhledem k začátku bloku  
  
 `dwListTypesRequested`  
 pro Požadované typy seznamu. Může být kombinací následujících hodnot:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Žádný seznam.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Seznam členů.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Seznam výčtu.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Seznam parametrů metody volání.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Globální seznam.|  
  
 Typ SCRIPT_CMPL_GLOBALLIST se považuje za výchozí položku dokončení, kterou lze kombinovat pomocí operátoru OR s dalšími položkami dokončení. Modul pro vytváření skriptů se nejprve pokusí naplnit informace o typu pro ostatní položky seznamu dokončení. Pokud se to nepovede, modul naplní pro SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 mimo Zadaný typ seznamu.  
  
 `pichListAnchorPosition`  
 mimo Počáteční index kontextu, který obsahuje aktuální pozici. Počáteční index je relativní vzhledem k začátku bloku.  
  
 Tato hodnota se naplní jenom v případě, že `dwListTypesRequested` zahrnuje SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST nebo SCRIPT_CMPL_GLOBALLIST. U ostatních požadovaných typů seznamů není výsledek definován.  
  
 `pichFuncAnchorPosition`  
 mimo Počáteční index volání funkce, který obsahuje aktuální pozici. Počáteční index je relativní vzhledem k začátku bloku.  
  
 Tato hodnota je naplněna pouze v případě, že kontext obsahující aktuální pozici je volání funkce a když `dwListTypesRequested` zahrnuje SCRIPT_CMPL_PARAMLIST. V opačném případě není výsledek definován.  
  
 `pmemid`  
 mimo MEMBERID funkce, jak je definováno typem v parametru `IProvideMultipleClassInfo``ppunk` out.  
  
 Tato hodnota se naplní jenom v případě, že `dwListTypesRequested` zahrnuje SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 mimo Index parametru, který obsahuje aktuální pozici. Pokud je aktuální pozice na názvu funkce, vrátí se – 1.  
  
 Hodnota `piCurrentParameter` je naplněna pouze v případě, že `dwListTypesRequested` zahrnuje SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Informace o typu, které jsou k dispozici ve formě objektu `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IProvideMultipleClassInfo](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)  
 [IActiveScriptAuthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)