---
title: QUERYCHANGESFUNC | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701637"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Toto je funkce zpětného volání používaná operací [SccQueryChanges](../extensibility/sccquerychanges-function.md) k vytvoření výčtu kolekce názvů souborů a určení stavu každého souboru.

 Funkce `SccQueryChanges` je uveden seznam souborů a ukazatel `QUERYCHANGESFUNC` na zpětné volání. Modul plug-in správy zdrojového kódu obsahuje výčet přes daný seznam a poskytuje stav (prostřednictvím tohoto zpětného volání) pro každý soubor v seznamu.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[v] Parametr `pvCallerData` předaný volajícím (IDE) [sccQueryChanges](../extensibility/sccquerychanges-function.md). Modul plug-in správy zdrojového kódu by neměl provádět žádné předpoklady o obsahu této hodnoty.

 pChangesData

[v] Ukazatel na strukturu [struktury QUERYCHANGESDATA popisující](#LinkQUERYCHANGESDATA) změny v souboru.

## <a name="return-value"></a>Návratová hodnota
 Rozhraní IDE vrátí odpovídající kód chyby:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pokračujte ve zpracování.|
|SCC_I_OPERATIONCANCELED|Zastavit zpracování.|
|SCC_E_xxx|Jakékoli příslušné chyby SCC by měl zastavit zpracování.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA Struktura
 Struktura předaná pro každý soubor vypadá takto:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize Velikost této struktury (v bajtů).

 lpFileName Původní název souboru pro tuto položku.

 dwChangeType Kód označující stav souboru:

|kód|Popis|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nelze říci, co se změnilo.|
|`SCC_CHANGE_UNCHANGED`|Pro tento soubor se nezměnilo žádné názvy.|
|`SCC_CHANGE_DIFFERENT`|Soubor s jinou identitou, ale stejný název existuje v databázi.|
|`SCC_CHANGE_NONEXISTENT`|Soubor neexistuje ani v databázi, ani místně.|
|`SCC_CHANGE_DATABASE_DELETED`|Soubor odstraněn v databázi.|
|`SCC_CHANGE_LOCAL_DELETED`|Soubor odstraněn místně, ale soubor stále existuje v databázi. Pokud to nelze určit, vraťte `SCC_CHANGE_DATABASE_ADDED`.|
|`SCC_CHANGE_DATABASE_ADDED`|Soubor byl přidán do databáze, ale neexistuje místně.|
|`SCC_CHANGE_LOCAL_ADDED`|Soubor neexistuje v databázi a je nový místní soubor.|
|`SCC_CHANGE_RENAMED_TO`|Soubor přejmenován nebo přesunut `lpLatestName`v databázi jako .|
|`SCC_CHANGE_RENAMED_FROM`|Soubor přejmenován nebo přesunut `lpLatestName`v databázi z ; Pokud je to příliš nákladné sledovat, vrátí `SCC_CHANGE_DATABASE_ADDED`jiný příznak, například .|

 lpLatestName Aktuální název souboru pro tuto položku.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Kódy chyb](../extensibility/error-codes.md)
