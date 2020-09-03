---
title: QUERYCHANGESFUNC | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701637"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Toto je funkce zpětného volání, kterou používá operace [SccQueryChanges](../extensibility/sccquerychanges-function.md) k vytvoření výčtu kolekce názvů souborů a určení stavu jednotlivých souborů.

 `SccQueryChanges`Funkci je uveden seznam souborů a ukazatel na `QUERYCHANGESFUNC` zpětné volání. Modul plug-in správy zdrojových kódů se v daném seznamu vyčísluje a poskytuje stav (prostřednictvím tohoto zpětného volání) pro každý soubor v seznamu.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

pro `pvCallerData` Parametr předaný volajícím (IDE) do [SccQueryChanges](../extensibility/sccquerychanges-function.md). Modul plug-in správy zdrojových kódů by neměl vytvářet žádné předpoklady o obsahu této hodnoty.

 pChangesData

pro Ukazatel na strukturu [struktury QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) popisující změny v souboru.

## <a name="return-value"></a>Vrácená hodnota
 Rozhraní IDE vrátí příslušný kód chyby:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pokračovat ve zpracování.|
|SCC_I_OPERATIONCANCELED|Zastavit zpracování.|
|SCC_E_xxx|Jakákoli vhodná chyba SCC by měla zastavit zpracování.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Struktura QUERYCHANGESDATA
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

 nenulového dwSize funkci velikost této struktury (v bajtech).

 lpFileName původní název souboru pro tuto položku.

 dwChangeType kód označující stav souboru:

|Kód|Popis|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nelze zjistit, co se změnilo.|
|`SCC_CHANGE_UNCHANGED`|Pro tento soubor se nezměnily žádné názvy.|
|`SCC_CHANGE_DIFFERENT`|Soubor s jinou identitou, ale stejný název v databázi existuje.|
|`SCC_CHANGE_NONEXISTENT`|Soubor neexistuje buď v databázi, nebo lokálně.|
|`SCC_CHANGE_DATABASE_DELETED`|Soubor se odstranil v databázi.|
|`SCC_CHANGE_LOCAL_DELETED`|Soubor se místně odstranil, ale soubor v databázi stále existuje. Pokud tuto hodnotu nelze určit, vraťte se `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Soubor byl přidán do databáze nástroje, ale neexistuje místně.|
|`SCC_CHANGE_LOCAL_ADDED`|Soubor v databázi neexistuje a je to nový místní soubor.|
|`SCC_CHANGE_RENAMED_TO`|Soubor byl přejmenován nebo přesunut v databázi jako `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Soubor byl přejmenován nebo přesunut z databáze `lpLatestName` . Pokud je pro sledování příliš nákladné, vraťte jiný příznak, například `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName aktuální název souboru pro tuto položku.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Kódy chyb](../extensibility/error-codes.md)
