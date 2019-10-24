---
title: Funkce SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721045"
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

[in, out] Volitelný pomocný řetězec identifikující projekt (nesmí přesáhnout SCC_AUXPATH_SIZE, včetně ukončovacího znaku NULL).

 lpComment

pro Komentář k novému projektu, který se vytváří.

 lpTextOutProc

pro Volitelná funkce zpětného volání, která zobrazí textový výstup z modulu plug-in správy zdrojových kódů.

 dwFlags

pro Signalizuje, jestli je potřeba vytvořit nový projekt, pokud je projekt neznámý pro modul plug-in správy zdrojových kódů. Hodnota může být kombinací `SCC_OP_CREATEIFNEW` a `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Otevření projektu bylo úspěšné.|
|SCC_E_INITIALIZEFAILED|Projekt se nepovedlo inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit do systému správy zdrojového kódu.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt neexistuje před voláním.  byl nastaven příznak `SCC_OPT_CREATEIFNEW`, ale projekt se nepovedlo vytvořit.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt není známý pro modul plug-in správy zdrojových kódů a příznak `SCC_OPT_CREATEIFNEW` nebyl nastaven.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECFICERROR|Nespecifická chyba; systém správy zdrojového kódu nebyl inicializován.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE může předat uživatelské jméno (`lpUser`) nebo může jednoduše předat ukazatel na prázdný řetězec. Pokud je uživatelské jméno, modul plug-in správy zdrojových kódů by ho měl používat jako výchozí. Pokud se ale nepředali žádný název nebo pokud se přihlášení nezdařilo s daným názvem, modul plug-in by měl uživateli požádat o přihlášení a vrátí platný název v `lpUser`, když obdrží platný přihlašovací `.`, protože modul plug-in může změnit řetězec uživatelského jména. rozhraní IDE vždy přidělí velikost vyrovnávací paměti (`SCC_USER_LEN` + 1 nebo SCC_USER_SIZE, což zahrnuje místo pro ukončovací znak null).

> [!NOTE]
> První akce, kterou může být prostředí IDE nutné provést, může být voláním funkce `SccOpenProject` nebo [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Z tohoto důvodu mají oba parametry stejný `lpUser` parametr.

 `lpAuxProjPath` a `lpProjName` jsou čteny ze souboru řešení nebo jsou vráceny voláním funkce `SccGetProjPath`. Tyto parametry obsahují řetězce, které modul plug-in správy zdrojových kódů přidruží k projektu a je smysluplný pouze pro modul plug-in. Pokud tyto řetězce nejsou v souboru řešení a uživatel nebyl vyzván k procházení (což by vrátilo řetězec prostřednictvím funkce `SccGetProjPath`), rozhraní IDE předává prázdné řetězce pro `lpAuxProjPath` i `lpProjName` a očekává, že tyto hodnoty budou aktualizovány modulem plug-in, když je to th funkce je vrácena.

 `lpTextOutProc` je ukazatel na funkci zpětného volání poskytované rozhraním IDE pro modul plug-in správy zdrojových kódů pro účely zobrazení výstupu výsledku příkazu. Tato funkce zpětného volání je podrobněji popsána v [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Pokud je tento modul plug-in správy zdrojových kódů zamýšlí využít, musí mít nastaven příznak `SCC_CAP_TEXTOUT` v [SccInitialize](../extensibility/sccinitialize-function.md). Pokud tento příznak nebyl nastaven nebo pokud rozhraní IDE tuto funkci nepodporuje, `lpTextOutProc` bude `NULL`.

 Parametr `dwFlags` řídí výsledek v události, že otevřený projekt aktuálně neexistuje. Skládá se ze dvou bitflags `SCC_OP_CREATEIFNEW` a `SCC_OP_SILENTOPEN`. Pokud otevřený projekt již existuje, funkce jednoduše otevře projekt a vrátí `SCC_OK`. Pokud projekt neexistuje a je-li příznak `SCC_OP_CREATEIFNEW` zapnut, modul plug-in správy zdrojového kódu může vytvořit projekt v systému správy zdrojového kódu, otevřít jej a vrátit `SCC_OK`. Pokud projekt neexistuje a pokud je příznak `SCC_OP_CREATEIFNEW` vypnutý, modul plug-in by pak měl kontrolovat příznak `SCC_OP_SILENTOPEN`. Pokud tento příznak není zapnutý, modul plug-in může uživateli požádat o název projektu. Pokud je tento příznak zapnutý, modul plug-in by měl jednoduše vrátit `SCC_E_UNKNOWNPROJECT`.

## <a name="calling-order"></a>Pořadí volání
 V běžném průběhu událostí by se [SccInitialize](../extensibility/sccinitialize-function.md) volal jako první pro otevření relace správy zdrojového kódu. Relace může obsahovat volání `SccOpenProject`, následované dalšími voláními funkcí rozhraní API modulu plug-in správy zdrojového kódu a skončí voláním [SccCloseProject](../extensibility/scccloseproject-function.md). Tyto relace se můžou několikrát opakovat předtím, než se zavolá [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Pokud modul plug-in správy zdrojových kódů nastaví bit `SCC_CAP_REENTRANT` v `SccInitialize`, pak se výše uvedená sekvence relace může v paralelním opakování opakovat. Různé `pvContext` struktury sledují různé relace, ve kterých každé `pvContext` je přidruženo k jednomu otevřenému projektu v jednom okamžiku. Na základě parametru `pvContext` může modul plug-in určit, na který projekt se odkazuje v jakémkoli konkrétním volání. Pokud funkce `SCC_CAP_REENTRANT` bit nonreentrant není nastavená, moduly plug-in správy zdrojového kódu jsou omezené na jejich schopnost pracovat s více projekty.

> [!NOTE]
> @No__t_0 bit byl představen ve verzi 1,1 rozhraní API modulu plug-in správy zdrojového kódu. Není nastaven nebo se ignoruje ve verzi 1,0 a předpokládá se, že moduly plug-in správy zdrojového kódu verze 1,0 jsou nonreentrant.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)