---
title: Funkce SccOpenProject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700569"
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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 lpUživatel

[dovnitř, ven] Jméno uživatele (nesmí překročit SCC_USER_SIZE, včetně zakončení NULL).

 lpProjName

[v] Řetězec identifikující název projektu.

 lpLocalProjPath

[v] Cesta k pracovní složce projektu.

 lpAuxProjPath

[dovnitř, ven] Volitelný pomocný řetězec identifikující projekt (nepřekračovat SCC_AUXPATH_SIZE, včetně zakončení NULL).

 lpKomentář

[v] Komentář k novému projektu, který je vytvářen.

 lpTextOutProc

[v] Volitelná funkce zpětného volání pro zobrazení textového výstupu z modulu plug-in správy zdrojového kódu.

 dwFlags

[v] Signalizuje, zda je třeba vytvořit nový projekt, pokud projekt není znám modulu plug-in správy zdrojového kódu. Hodnota může být `SCC_OP_CREATEIFNEW` kombinací`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch při otevření projektu.|
|SCC_E_INITIALIZEFAILED|Projekt nelze inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit do systému správy zdrojového kódu.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt před voláním neexistoval.  příznak `SCC_OPT_CREATEIFNEW` byl nastaven, ale projekt nelze vytvořit.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt není znám modulu plug-in správy `SCC_OPT_CREATEIFNEW` zdrojového kódu a příznak nebyl nastaven.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECFICERROR|Nespecifické selhání; systém správy zdrojového kódu nebyl inicializován.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE může předat uživatelské`lpUser`jméno ( ), nebo může jednoduše předat ukazatel na prázdný řetězec. Pokud existuje uživatelské jméno, modul plug-in správy zdrojového kódu by jej měl použít jako výchozí. Pokud však nebylo předáno žádné jméno nebo pokud přihlášení s daným názvem selhalo, modul plug-in `lpUser` by měl vyzvat`.` uživatele k přihlášení a vrátí platný název, když obdrží platné přihlášení`SCC_USER_LEN`Protože modul plug-in může změnit řetězec uživatelského jména, ide vždy přidělí vyrovnávací paměť o velikosti (+1 nebo SCC_USER_SIZE, která obsahuje místo pro zakončení null).

> [!NOTE]
> První akce IDE může být požadováno k provedení `SccOpenProject` může být volání funkce nebo [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Z tohoto důvodu mají oba `lpUser` stejný parametr.

 `lpAuxProjPath`a`lpProjName` jsou čteny ze souboru řešení nebo jsou `SccGetProjPath` vráceny z volání funkce. Tyto parametry obsahují řetězce, které modul plug-in správy zdrojového kódu přidružuje k projektu a jsou smysluplné pouze pro modul plug-in. Pokud žádné takové řetězce jsou v souboru řešení a uživatel nebyl vyzván k procházení `SccGetProjPath` (což by vrátilřetězec prostřednictvím `lpAuxProjPath` `lpProjName`funkce), ide předá prázdné řetězce pro oba a a očekává, že tyto hodnoty budou aktualizovány modul plug-in, když tato funkce vrátí.

 `lpTextOutProc`je ukazatel na funkci zpětného volání poskytovanou ide na modul plug-in správy zdrojového kódu pro účely zobrazení výstupu výsledku příkazu. Tato funkce zpětného volání je podrobně popsána v [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Pokud modul plug-in správy zdrojového kódu má v `SCC_CAP_TEXTOUT` úmyslu využít této výhody, musí mít nastaven příznak v [SccInitialize](../extensibility/sccinitialize-function.md). Pokud tento příznak nebyl nastaven nebo pokud ide nepodporuje tuto funkci, `lpTextOutProc` bude `NULL`.

 Parametr `dwFlags` řídí výsledek v případě, že projekt, který je otevíraný, v současné době neexistuje. Skládá se ze dvou `SCC_OP_CREATEIFNEW` bitových vlajek a `SCC_OP_SILENTOPEN`. Pokud projekt, který se otevírá, již existuje, `SCC_OK`funkce jednoduše otevře projekt a vrátí . Pokud projekt neexistuje a `SCC_OP_CREATEIFNEW` je zapnutý příznak, modul plug-in správy zdrojového kódu může vytvořit projekt `SCC_OK`v systému správy zdrojového kódu, otevřít jej a vrátit . Pokud projekt neexistuje a `SCC_OP_CREATEIFNEW` pokud je příznak vypnutý, modul plug-in `SCC_OP_SILENTOPEN` by měl příznak zkontrolovat. Pokud tento příznak není zapnutý, může modul plug-in vyzvat uživatele k zadání názvu projektu. Pokud je tato vlajka zapnutá, `SCC_E_UNKNOWNPROJECT`modul plug-in by se měl jednoduše vrátit .

## <a name="calling-order"></a>Pořadí volání
 V normálním průběhu událostí [sccInitialize](../extensibility/sccinitialize-function.md) by být volána jako první otevřít relaci správy zdrojového kódu. Relace se může skládat `SccOpenProject`z volání do aplikace následované dalšími voláními funkce rozhraní API modulu plug-in správy zdrojového kódu a bude ukončena voláním [projektu SccCloseProject](../extensibility/scccloseproject-function.md). Tyto relace mohou být opakovány několikrát před [SccUninitialize](../extensibility/sccuninitialize-function.md) je volána.

 Pokud modul plug-in správy `SCC_CAP_REENTRANT` zdrojového kódu nastaví bit v `SccInitialize`, může být výše uvedená sekvenci relace opakována mnohokrát paralelně. Různé `pvContext` struktury sledovat různé relace, `pvContext` ve kterém každý je přidružen k jeden otevřený projekt najednou. Na základě`pvContext` parametru může modul plug-in určit, na který projekt se odkazuje v konkrétním volání. Pokud bit `SCC_CAP_REENTRANT` schopnosti není nastavena, nonreentrant moduly plug-in správy zdrojového kódu jsou omezeny v jejich schopnost pracovat s více projekty.

> [!NOTE]
> Bit `SCC_CAP_REENTRANT` byl představen ve verzi 1.1 rozhraní plug-in správy zdrojového kódu. Není nastavena nebo je ignorována ve verzi 1.0 a všechny moduly plug-in správy zdrojového kódu verze 1.0 jsou považovány za neopakované.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
