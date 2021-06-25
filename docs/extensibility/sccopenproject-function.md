---
description: Tato funkce otevře existující projekt správy zdrojového kódu nebo vytvoří nový.
title: Funkce SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1326319b483aa707b77e0d7142d816b01fc7d3b1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902394"
---
# <a name="sccopenproject-function"></a>SccOpenProject – funkce
Tato funkce otevře existující projekt správy zdrojového kódu nebo vytvoří nový.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Jméno uživatele (nesmí přesáhnout SCC_USER_SIZE, včetně ukončovacího znaku NULL).

 lpProjName

pro Řetězec identifikující název projektu.

 lpLocalProjPath

pro Cesta k pracovní složce pro projekt

 lpAuxProjPath

[in, out] Volitelný pomocný řetězec identifikující projekt (nesmí přesahovat SCC_AUXPATH_SIZE, včetně ukončovacího znaku NULL).

 lpComment

pro Komentář k novému projektu, který se vytváří.

 lpTextOutProc

pro Volitelná funkce zpětného volání, která zobrazí textový výstup z modulu plug-in správy zdrojových kódů.

 dwFlags

pro Signalizuje, jestli je potřeba vytvořit nový projekt, pokud je projekt neznámý pro modul plug-in správy zdrojových kódů. Hodnotou může být kombinace a. `SCC_OP_CREATEIFNEW``SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Otevření projektu bylo úspěšné.|
|SCC_E_INITIALIZEFAILED|Projekt se nepovedlo inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit do systému správy zdrojového kódu.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt neexistuje před voláním.  `SCC_OPT_CREATEIFNEW` příznak byl nastaven, ale projekt se nepovedlo vytvořit.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt není známý pro modul plug-in správy zdrojových kódů a `SCC_OPT_CREATEIFNEW` Příznak nebyl nastaven.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECFICERROR|Nespecifická chyba; systém správy zdrojového kódu nebyl inicializován.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE může předat uživatelské jméno ( `lpUser` ) nebo může jednoduše předat ukazatel na prázdný řetězec. Pokud je uživatelské jméno, modul plug-in správy zdrojových kódů by ho měl používat jako výchozí. Pokud se ale nepředali žádný název nebo pokud se přihlášení nezdařilo s daným názvem, modul plug-in by měl uživateli požádat o přihlášení a vrátí platný název v `lpUser` případě, kdy obdrží platné přihlašovací údaje `.` , protože modul plug-in může změnit řetězec uživatelského jména, rozhraní IDE vždy přidělí velikost vyrovnávací paměti ( `SCC_USER_LEN` + 1 nebo SCC_USER_SIZE, která obsahuje místo pro ukončovací znak null).

> [!NOTE]
> První akce, kterou může IDE vyžadovat k provedení, může být volání `SccOpenProject` funkce nebo [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Z tohoto důvodu mají oba atributy stejný `lpUser` parametr.

 `lpAuxProjPath` a `lpProjName` jsou čteny ze souboru řešení nebo jsou vráceny ze volání `SccGetProjPath` funkce. Tyto parametry obsahují řetězce, které modul plug-in správy zdrojových kódů přidruží k projektu a je smysluplný pouze pro modul plug-in. Pokud tyto řetězce nejsou v souboru řešení a uživatel nebyl vyzván k procházení (který by vrátil řetězec prostřednictvím `SccGetProjPath` funkce), rozhraní IDE předává prázdné řetězce pro `lpAuxProjPath` a a `lpProjName` očekává, že tyto hodnoty budou aktualizovány modulem plug-in, když tato funkce vrátí.

 `lpTextOutProc` je ukazatel na funkci zpětného volání poskytovanou rozhraním IDE pro modul plug-in správy zdrojových kódů pro účely zobrazení výstupu výsledku příkazu. Tato funkce zpětného volání je podrobněji popsána v [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Pokud je tento modul plug-in správy zdrojových kódů zamýšlí využít, musí mít nastaven `SCC_CAP_TEXTOUT` příznak v [SccInitialize](../extensibility/sccinitialize-function.md). Pokud tento příznak nebyl nastaven nebo pokud rozhraní IDE tuto funkci nepodporuje, `lpTextOutProc` bude `NULL` .

 `dwFlags`Parametr řídí výsledek v události, že otevřený projekt aktuálně neexistuje. Skládá se ze dvou bitflags `SCC_OP_CREATEIFNEW` a `SCC_OP_SILENTOPEN` . Pokud otevřený projekt již existuje, funkce jednoduše otevře projekt a vrátí `SCC_OK` . Pokud projekt neexistuje a `SCC_OP_CREATEIFNEW` je-li příznak zapnut, modul plug-in správy zdrojového kódu může vytvořit projekt v systému správy zdrojového kódu, otevřít jej a vrátit se změnami `SCC_OK` . Pokud projekt neexistuje a `SCC_OP_CREATEIFNEW` příznak je vypnutý, modul plug-in by pak měl kontrolovat `SCC_OP_SILENTOPEN` příznak. Pokud tento příznak není zapnutý, modul plug-in může uživateli požádat o název projektu. Pokud je tento příznak zapnutý, modul plug-in by se měl jednoduše vrátit `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Pořadí volání
 V běžném průběhu událostí by se [SccInitialize](../extensibility/sccinitialize-function.md) volal jako první pro otevření relace správy zdrojového kódu. Relace může obsahovat volání `SccOpenProject` , následované dalšími voláními funkcí rozhraní API modulu plug-in správy zdrojového kódu a ukončí volání [SccCloseProject](../extensibility/scccloseproject-function.md). Tyto relace se můžou několikrát opakovat předtím, než se zavolá [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Pokud modul plug-in správy zdrojových kódů nastaví `SCC_CAP_REENTRANT` bit v `SccInitialize` , pak se výše uvedená sekvence relace může v paralelním opakování opakovat. Různé `pvContext` struktury sledují různé relace, ve kterých každé `pvContext` je přidruženo k jednomu otevřenému projektu v jednom okamžiku. Na základě `pvContext` parametru může modul plug-in určit, který projekt je odkazován v jakémkoli konkrétním volání. Pokud není bit schopností `SCC_CAP_REENTRANT` nastaven, moduly plug-in nonreentrant správy zdrojového kódu jsou omezené na jejich schopnost pracovat s více projekty.

> [!NOTE]
> `SCC_CAP_REENTRANT`Bit byl představen ve verzi 1,1 rozhraní API modulu plug-in správy zdrojového kódu. Není nastaven nebo se ignoruje ve verzi 1,0 a předpokládá se, že moduly plug-in správy zdrojového kódu verze 1,0 jsou nonreentrant.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
