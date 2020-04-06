---
title: Funkce SccDirQueryInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700953"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo
Tato funkce zkoumá seznam plně kvalifikovaných adresářů pro jejich aktuální stav.

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
 pKontext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 nDirs

[v] Počet adresářů vybraných k dotazování.

 názvy lpDir

[v] Pole plně kvalifikované cesty adresářů, které mají být dotazován.

 lpStatus

[dovnitř, ven] Struktura pole pro modul plug-in správy zdrojového kódu pro vrácení stavových příznaků (podrobnosti naleznete v [tématu Stavový kód adresáře).](../extensibility/directory-status-code-enumerator.md)

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dotaz byl úspěšný.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Funkce vyplní návratové pole bitovou maskou `SCC_DIRSTATUS` bitů z rodiny (viz [Stavový kód adresáře](../extensibility/directory-status-code-enumerator.md)), jedna položka pro každý daný adresář. Pole stavu je přiděleno volajícím.

 Rozhraní IDE používá tuto funkci před přejmenováním adresáře ke kontrole, zda je adresář pod správou zdrojového kódu dotazem, zda má odpovídající projekt. Pokud adresář není pod správou zdrojového kódu, ide může poskytnout správné upozornění pro uživatele.

> [!NOTE]
> Pokud se modul plug-in správy zdrojového kódu rozhodne neimplementovat jednu nebo více hodnot stavu, neimplementované bity by měly být nastaveny na nulu.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Stavový kód adresáře](../extensibility/directory-status-code-enumerator.md)
