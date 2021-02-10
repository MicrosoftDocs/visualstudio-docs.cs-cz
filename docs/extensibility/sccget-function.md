---
title: Funkce SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50281ffdd233debd3c10672868e9debd4b1f395f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965210"
---
# <a name="sccget-function"></a>SccGet – funkce
Tato funkce načte kopii jednoho nebo více souborů pro zobrazení a kompilování, ale nikoli pro úpravy. Ve většině systémů jsou soubory označeny jako jen pro čtení.

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 nFiles

pro Počet souborů, které jsou zadány v `lpFileNames` poli.

 lpFileNames

pro Pole plně kvalifikovaných názvů souborů, které mají být načteny.

 fOptions

pro Příznaky příkazu ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

pro Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch operace Get|
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_FILEISCHECKEDOUT|Nelze získat soubor, který aktuálně rezervoval uživatel.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NOSPECIFIEDVERSION|Zadali jste neplatnou verzi nebo datum/čas.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba; soubor nebyl synchronizován.|
|SCC_I_OPERATIONCANCELED|Operace se zrušila před dokončením.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|

## <a name="remarks"></a>Poznámky
 Tato funkce je volána s počtem a polem názvů souborů, které mají být načteny. Pokud rozhraní IDE předává příznak `SCC_GET_ALL` , znamená to, že položky v `lpFileNames` nejsou soubory, ale adresáře a že mají být načteny všechny soubory pod správou zdrojových kódů v daných adresářích.

 `SCC_GET_ALL`Příznak lze kombinovat s `SCC_GET_RECURSIVE` příznakem pro načtení všech souborů v daných adresářích a také ve všech podadresářích.

> [!NOTE]
> `SCC_GET_RECURSIVE` Nikdy by neměl být předán bez `SCC_GET_ALL` . Všimněte si také, že pokud se adresáře *C:\a* a *C:\A\B* předávají na rekurzivní Get, *C:\A\B* a všechny jeho podadresáře budou skutečně načteny dvakrát. Je to zodpovědnost IDE – a ne modul plug-in správy zdrojového kódu, aby se zajistilo, že tyto duplicitní hodnoty jsou z pole zachované.

 Nakonec i v případě, že modul plug-in správy zdrojových kódů zadal `SCC_CAP_GET_NOUI` příznak při inicializaci, což značí, že nemá uživatelské rozhraní pro příkaz Get, může být tato funkce stále volána rozhraním IDE pro načtení souborů. Příznak jednoduše znamená, že rozhraní IDE nezobrazuje položku nabídky získat a že modul plug-in neočekává, že by poskytoval žádné uživatelské rozhraní.

## <a name="rename-files-and-sccget"></a>Přejmenování souborů a SccGet
 Situace: uživatel rezervuje soubor, například *a.txt*, a upraví ho. Než bude možné *a.txt* vrátit se změnami, druhý uživatel přejmenuje *a.txt* na *b.txt* v databázi správy zdrojů, zkontroluje *b.txt*, provede některé úpravy souboru a zkontroluje soubor v. První uživatel požaduje změny provedené druhým uživatelem, aby první uživatel přejmenoval svou místní verzi *a.txt* souboru na *b.txt* a soubor získá. Místní mezipaměť, která uchovává údaje o číslech verzí, však stále popřemýšleje o tom, že první verze *a.txt* je uložená místně, takže Správa zdrojového kódu nemůže tyto rozdíly vyřešit.

 Existují dva způsoby, jak tuto situaci vyřešit, protože místní mezipaměť verzí správy zdrojového kódu se nesynchronizuje s databází správy zdrojů:

1. Nepovolujte přejmenování souboru v databázi správy zdrojů, která je aktuálně rezervována.

2. Proveďte ekvivalent příkazu "odstranit starý" následovaný výrazem "Přidat nový". To lze provést jedním z následujících způsobů:

    1. Voláním funkce [SccQueryChanges](../extensibility/sccquerychanges-function.md) se dozvíte, jak přejmenovat *a.txt* na *b.txt* v databázi správy zdrojů.

    2. Přejmenujte místní *a.txt* na *b.txt*.

    3. Zavolejte `SccGet` funkci pro *a.txt* i *b.txt*.

    4. Vzhledem k tomu, že *a.txt* neexistuje v databázi správy zdrojových kódů, je mezipaměť místní verze vyprázdněna z informací o chybějících *a.txtch* verzích.

    5. Soubor *b.txt* , který je rezervován, je sloučen s obsahem místního souboru *b.txt* .

    6. Aktualizovaný soubor *b.txt* se teď dá vrátit se změnami.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
