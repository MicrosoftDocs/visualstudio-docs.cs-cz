---
title: Funkce SccGet | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700889"
---
# <a name="sccget-function"></a>SccGet
Tato funkce načte kopii jednoho nebo více souborů pro prohlížení a kompilaci, ale ne pro úpravy. Ve většině systémů jsou soubory označeny jen pro čtení.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 nSoubory

[v] Počet souborů zadaných `lpFileNames` v poli.

 lpNázev souboru

[v] Pole plně kvalifikovaných názvů souborů, které mají být načteny.

 fMožnosti

[v] Příkazové`SCC_GET_ALL`příznaky `SCC_GET_RECURSIVE`( , ).

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch operace.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod smělou směřovač zdroj.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_FILEISCHECKEDOUT|Soubor, který uživatel aktuálně odhlásil, nelze získat.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NOSPECIFIEDVERSION|Zadaná neplatná verze nebo datum a čas.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání; soubor nebyl synchronizován.|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|

## <a name="remarks"></a>Poznámky
 Tato funkce je volána s počtem a pole názvy souborů, které mají být načteny. Pokud ide předá `SCC_GET_ALL`příznak , to `lpFileNames` znamená, že položky v nejsou soubory, ale adresáře a že všechny soubory pod správou zdrojového kódu v daných adresářích mají být načteny.

 Příznak `SCC_GET_ALL` lze kombinovat s `SCC_GET_RECURSIVE` příznakem načíst všechny soubory v daných adresářů a všechny podadresáře stejně.

> [!NOTE]
> `SCC_GET_RECURSIVE`by nikdy neměla být předána bez `SCC_GET_ALL`. Všimněte si také, že pokud adresáře *C:\A* a *C:\A\B* jsou předány na rekurzivní get, *C:\A \B* a všechny jeho podadresáře budou skutečně načteny dvakrát. Je odpovědností ide – a nikoli modul plug-in správy zdrojového kódu – ujistěte se, že duplikáty, jako je tento, jsou uchovávány mimo pole.

 Nakonec i v případě, že modul `SCC_CAP_GET_NOUI` plug-in správy zdrojového kódu zadal příznak při inicializaci, což znamená, že nemá uživatelské rozhraní pro příkaz Get, může být tato funkce stále volána rozhraním IDE k načtení souborů. Příznak jednoduše znamená, že ide nezobrazí get položku nabídky a že modul plug-in se neočekává, že poskytovat žádné ui.

## <a name="rename-files-and-sccget"></a>Přejmenování souborů a SccGet
 Situace: Uživatel rezervuje soubor, například *a.txt*, a upraví jej. Před *vrácením souboru a.txt* přejmenuje druhý uživatel *soubor a.txt* na *b.txt* v databázi správy zdrojového kódu, rezervuje *soubor b.txt*, provede některé změny v souboru a vrátí soubor se změnami. První uživatel chce změny provedené druhým uživatelem, aby první uživatel přejmenoval svou místní verzi souboru *a.txt* na *b.txt* a získal soubor. Místní mezipaměť, která sleduje čísla verzí, si však stále myslí, že první verze *souboru a.txt* je uložena místně, a proto správa zdrojového kódu nemůže vyřešit rozdíly.

 Existují dva způsoby, jak vyřešit tuto situaci, kdy místní mezipaměti verze správy zdrojového kódu stane nesynchronizované s databází správy zdrojového kódu:

1. Nepovolit přejmenování souboru v databázi správy zdrojového kódu, která je aktuálně rezervována.

2. Proveďte ekvivalent "odstranit staré" následovaný "přidat nové". Následující algoritmus je jedním ze způsobů, jak toho dosáhnout.

    1. Volání [SccQueryChanges](../extensibility/sccquerychanges-function.md) funkce se dozvíte o přejmenování *a.txt* na *b.txt* v databázi správy zdrojového kódu.

    2. Přejmenujte místní *soubor a.txt* na *b.txt*.

    3. Volání `SccGet` funkce pro *a.txt* a *b.txt*.

    4. Vzhledem k tomu, že soubor *a.txt* v databázi správy zdrojového kódu neexistuje, je místní mezipaměť verzí vymazána z chybějících informací o verzi *a.txt.*

    5. Zasazený soubor *b.txt* je sloučen s obsahem místního souboru *b.txt.*

    6. Aktualizovaný soubor *b.txt* lze nyní zkontrolovat.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Bitové příznaky používané určitými příkazy](../extensibility/bitflags-used-by-specific-commands.md)
