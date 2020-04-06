---
title: Funkce SccGetEvents | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700823"
---
# <a name="sccgetevents-function"></a>SccGetEvents
Tato funkce načte událost stavu ve frontě.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 název lpFileName

[dovnitř, ven] Vyrovnávací paměť, kde modul plug-in správy zdrojového kódu umístí název vráceného souboru (až _MAX_PATH znaků).

 lpStatus

[dovnitř, ven] Vrátí stavový kód (možné hodnoty naleznete v [tématu Stavový kód souboru).](../extensibility/file-status-code-enumerator.md)

 pnEventsZbývající

[dovnitř, ven] Vrátí počet položek zbývajících ve frontě po tomto volání. Pokud je toto číslo velké, volající se může rozhodnout zavolat [SccQueryInfo](../extensibility/sccqueryinfo-function.md) získat všechny informace najednou.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Získat události úspěšné.|
|SCC_E_OPNOTSUPPORTED|Tato funkce není podporována.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce je volána během zpracování nečinnosti, aby se zjistilo, zda byly nějaké aktualizace stavu pro soubory pod správou zdrojového kódu. Modul plug-in správy zdrojového kódu udržuje stav všech souborů, o kterých ví, a kdykoli je modul plug-in zaznamenán změnu stavu, stav a přidružený soubor jsou uloženy ve frontě. Při `SccGetEvents` volání je načíst horní prvek fronty a vrácena. Tato funkce je omezena na vrácení pouze dříve uložených informací v mezipaměti a musí mít velmi rychlý obrat (to znamená, že žádné čtení disku nebo dotazování systému správy zdrojového kódu na stav); v opačném případě může dojít ke snížení výkonu ide.

 Pokud není k dispozici žádná aktualizace stavu sestavy, modul plug-in správy `lpFileName`zdrojového kódu ukládá prázdný řetězec ve vyrovnávací paměti, na kterou se vztahuje aplikace . V opačném případě modul plug-in uloží úplný název cesty souboru, pro který byly změněny informace o stavu, a vrátí příslušný stavový kód (jednu z hodnot popsaných ve [stavovém kódu souboru).](../extensibility/file-status-code-enumerator.md)

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Stavový kód souboru](../extensibility/file-status-code-enumerator.md)
