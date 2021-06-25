---
description: Tato funkce načte kopii jednoho nebo více souborů pro zobrazení a kompilaci, ale ne pro úpravy.
title: SccGet – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 805c19b0c326e8389b4e1905edf370ad042aac92
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904549"
---
# <a name="sccget-function"></a>Funkce SccGet
Tato funkce načte kopii jednoho nebo více souborů pro zobrazení a kompilaci, ale ne pro úpravy. Ve většině systémů jsou soubory označené jako jen pro čtení.

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

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 nFiles

[v] Počet souborů zadaných v `lpFileNames` poli

 lpFileNames

[v] Pole plně kvalifikovaných názvů souborů, které se mají načíst.

 Možnosti fOptions

[v] Příznaky příkazů ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

[v] Možnosti modulu plug-in správy zdrojového kódu

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch operace získání|
|SCC_E_FILENOTCONTROLLED|Soubor není ve zdrojovém kódu.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_FILEISCHECKEDOUT|Nelze získat soubor, který uživatel právě vyhlásil.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_NOSPECIFIEDVERSION|Zadali jste neplatnou verzi nebo datum a čas.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání; soubor nebyl synchronizovaný.|
|SCC_I_OPERATIONCANCELED|Operace se před dokončením zrušila.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|

## <a name="remarks"></a>Poznámky
 Tato funkce se volá s count a polem názvů souborů, které se mají načíst. Pokud integrované vývojové prostředí (IDE) předá příznak , znamená to, že položky v souboru nejsou soubory kromě adresářů a že se mají načíst všechny soubory v rámci správy zdrojového kódu v těchto `SCC_GET_ALL` `lpFileNames` adresářích.

 Příznak lze zkombinovat s příznakem a načíst tak všechny soubory v daném adresáři a také ve všech `SCC_GET_ALL` `SCC_GET_RECURSIVE` podadresářích.

> [!NOTE]
> `SCC_GET_RECURSIVE` By nikdy neměly být předány bez `SCC_GET_ALL` . Všimněte si také, že pokud jsou adresáře *C:\A* a *C:\A\B* předány rekurzivnímu získání, *C:\A\B* a všechny jeho podadresáře se ve skutečnosti načtou dvakrát. Je zodpovědností integrovaného vývojového prostředí (a ne modulů plug-in správy zdrojového kódu) zajistit, aby takové duplicity byly mimo pole.

 A konečně, i když modul plug-in správy zdrojového kódu specifikuje příznak při inicializaci, který indikuje, že nemá uživatelské rozhraní pro příkaz Get, může integrované vývojové prostředí tuto funkci stále volat pro načtení `SCC_CAP_GET_NOUI` souborů. Příznak jednoduše znamená, že integrované vývojové prostředí (IDE) nezobrazí položku nabídky Získat a že modul plug-in neposkytuje žádné uživatelské rozhraní.

## <a name="rename-files-and-sccget"></a>Přejmenování souborů a SccGet
 Situace: Uživatel si rezervuje soubor, například *a.txt*, a upraví ho. Před *a.txt* se změnami druhý uživatel přejmenuje a.txtna *b.txt* v databázi správy zdrojového kódu, zkontroluje *b.txt,* provede v souboru nějaké úpravy a zkontroluje soubor v . První uživatel chce, aby změny provedené druhým uživatelem byly provedeny, takže první  uživatel přejmenuje místní verzi souboru *a.txt* nab.txta dostane se k souboru. Místní mezipaměť, která uchovává informace o číslech verzí, si ale pořád myslí, že první verze *a.txt* je uložená místně, a proto nemůže řízení zdrojového kódu tyto rozdíly vyřešit.

 Existují dva způsoby, jak tuto situaci vyřešit, když se místní mezipaměť verzí správy zdrojového kódu přestane synchronizovat s databází správy zdrojového kódu:

1. Nepovoluje přejmenování souboru v databázi správy zdrojového kódu, který je aktuálně rezervován.

2. Proveďte ekvivalent "delete old" a "add new". Jedním ze způsobů, jak toho dosáhnout, je následující algoritmus.

    1. Voláním [funkce SccQueryChanges](../extensibility/sccquerychanges-function.md) získáte informace o  přejmenovánía.txt, *b.txt* v databázi správy zdrojového kódu.

    2. Přejmenujte místní *a.txt* na *b.txt*.

    3. Volání `SccGet` funkce pro *a.txt* i *b.txt*.

    4. Protože *a.txt* v databázi správy zdrojového kódu neexistuje, místní mezipaměť verzí se vyprázdní z chybějícícha.txt *verzí.*

    5. Soubor *b.txt* se sloučí s obsahem místního souborub.txt *souboru.*

    6. Aktualizovaný *souborb.txt* je teď možné se ohlásil.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflagy používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
