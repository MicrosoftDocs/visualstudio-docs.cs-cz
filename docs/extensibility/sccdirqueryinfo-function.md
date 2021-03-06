---
description: Tato funkce prověřuje seznam plně kvalifikovaných adresářů pro jejich aktuální stav.
title: Funkce SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da0d42e2ef65aefc03e2813f32189876d0c07da1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220817"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo – funkce
Tato funkce prověřuje seznam plně kvalifikovaných adresářů pro jejich aktuální stav.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parametry
 pContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 nDirs

pro Počet adresářů vybraných k dotazování.

 lpDirNames

pro Pole plně kvalifikovaných cest k adresářům, které mají být dotazovány.

 lpStatus

[in, out] Struktura pole pro modul plug-in správy zdrojových kódů, která vrátí stavové příznaky (podrobnosti viz [kód stavu adresáře](../extensibility/directory-status-code-enumerator.md) ).

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dotaz byl úspěšný.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Funkce vyplní vrácené pole maskou bitů z `SCC_DIRSTATUS` rodiny (viz [stavový kód adresáře](../extensibility/directory-status-code-enumerator.md)), jednu položku pro každý zadaný adresář. Pole stav je přiděleno volajícím.

 Rozhraní IDE používá tuto funkci před přejmenováním adresáře, aby zkontrolovala, zda je adresář pod správou zdrojových kódů pomocí dotazu, zda má odpovídající projekt. Pokud adresář není pod správou zdrojových kódů, rozhraní IDE může poskytnout správné upozornění uživateli.

> [!NOTE]
> Pokud se modul plug-in správy zdrojových kódů rozhodne neimplementovat jednu nebo více hodnot stavu, musí být neimplementovaná bity nastavena na hodnotu nula.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Stavový kód adresáře](../extensibility/directory-status-code-enumerator.md)
