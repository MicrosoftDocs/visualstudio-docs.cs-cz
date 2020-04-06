---
title: Funkce SccGetProjPath | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700694"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath
Tato funkce vyzve uživatele k cestě projektu, což je řetězec, který má smysl pouze pro modul plug-in správy zdrojového kódu. Je volána, když je uživatel:

- Vytvoření nového projektu

- Přidání existujícího projektu do správy verzí

- Pokus o nalezení existujícího projektu správy verzí

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 lpUživatel

[dovnitř, ven] Uživatelské jméno (nepřekračovat SCC_USER_SIZE, včetně zakončení NULL)

 lpProjName

[dovnitř, ven] Název projektu IDE, pracovního prostoru projektu nebo makefile (nesmí překročit SCC_PRJPATH_SIZE, včetně zakončení NULL).

 lpLocalPath

[dovnitř, ven] Pracovní cesta projektu. Pokud `bAllowChangePath` `TRUE`je , modul plug-in správy zdrojového kódu můžete upravit tento řetězec (nesmí překročit _MAX_PATH, včetně null-terminator).

 lpAuxProjPath

[dovnitř, ven] Vyrovnávací paměť pro vrácenou cestu projektu (nesmí překročit SCC_PRJPATH_SIZE, včetně zakončení NULL).

 bAllowChangePath

[v] Pokud je `TRUE`toto , modul plug-in správy `lpLocalPath` zdrojového kódu může vyzvat k zadání a upravit řetězec.

 pbNový

[dovnitř, ven] Přicházející hodnota označuje, zda chcete vytvořit nový projekt. Vrácená hodnota označuje úspěch při vytváření projektu:

|Příchozí|Interpretace|
|--------------|--------------------|
|TRUE|Uživatel může vytvořit nový projekt.|
|FALSE|Uživatel nesmí vytvořit nový projekt.|

|Odchozí|Interpretace|
|--------------|--------------------|
|TRUE|Byl vytvořen nový projekt.|
|FALSE|Byl vybrán existující projekt.|

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Projekt byl úspěšně vytvořen nebo načten.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty.|
|SCC_E_CONNECTIONFAILURE|Při pokusu o připojení k systému správy zdrojového kódu došlo k potížím.|
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované chybě.|

## <a name="remarks"></a>Poznámky
 Účelem této funkce je pro ide získat `lpProjName` `lpAuxProjPath`parametry a . Poté, co modul plug-in správy zdrojového kódu vyzve uživatele k zadání těchto informací, předá tyto dva řetězce zpět do rozhraní IDE. IDE zachová tyto řetězce v souboru řešení a předá je [SccOpenProject](../extensibility/sccopenproject-function.md) vždy, když uživatel otevře tento projekt. Tyto řetězce umožňují modulu plug-in sledovat informace přidružené k projektu.

 Při prvním volání funkce `lpAuxProjPath` je nastavena na prázdný řetězec. `lProjName`může být také prázdný nebo může obsahovat název projektu IDE, který může modul plug-in správy zdrojového kódu použít nebo ignorovat. Když se funkce úspěšně vrátí, modul plug-in vrátí dva odpovídající řetězce. Rozhraní IDE nevytváří žádné předpoklady o těchto řetězcích, nebude je používat a neumožní uživateli je upravit. Pokud uživatel chce změnit nastavení, ide `SccGetProjPath` bude volat znovu, předávání stejné hodnoty, které obdržel předchozí čas. To dává plug-in úplnou kontrolu nad těmito dvěma řetězci.

 Pro `lpUser`rozhraní IDE může předat uživatelské jméno, nebo může jednoduše předat ukazatel na prázdný řetězec. Pokud existuje uživatelské jméno, modul plug-in správy zdrojového kódu by jej měl použít jako výchozí. Pokud však nebylo předáno žádné jméno nebo pokud se přihlášení s daným názvem nezdařilo, modul `lpUser` plug-in by měl vyzvat uživatele k přihlášení a předat jméno zpět, když obdrží platné přihlášení. Vzhledem k tomu, že modul plug-in může tento řetězec`SCC_USER_LEN`změnit, bude ide vždy přidělit vyrovnávací paměť velikosti ( +1).

> [!NOTE]
> První akce, kterou provádí ide může být `SccOpenProject` volání `SccGetProjPath` funkce nebo funkce. Proto oba mají stejný `lpUser` parametr, který umožňuje modul plug-in správy zdrojového kódu pro přihlášení uživatele v obou časech. I v případě, že návrat z funkce označuje selhání, modul plug-in musí vyplnit tento řetězec s platným přihlašovacím jménem.

 `lpLocalPath`je adresář, ve kterém uživatel uchovává projekt. Může to být prázdný řetězec. Pokud není aktuálně definován žádný adresář (jako v případě uživatele, který se pokouší stáhnout `bAllowChangePath` projekt `TRUE`ze systému správy zdrojového kódu) a pokud je , může `lpLocalPath`modul plug-in správy zdrojového kódu vyzvat uživatele k zadání nebo použít jinou metodu k umístění vlastního řetězce do . Pokud `bAllowChangePath` `FALSE`je , modul plug-in by neměl změnit řetězec, protože uživatel již pracuje v zadaném adresáři.

 Pokud uživatel vytvoří nový projekt, který má být umístěn pod správou zdrojového kódu, modul `SccGetProjPath` plug-in správy zdrojového kódu nemusí ve skutečnosti vytvořit v systému správy zdrojového kódu v době, kdy se nazývá. Místo toho předá řetězec spolu s nenulovou hodnotou pro `pbNew`, což znamená, že projekt bude vytvořen v systému správy zdrojového kódu.

 Například pokud uživatel v **průvodci Nový projekt** v sadě Visual Studio přidá svůj projekt do zdrojového kódu, Visual Studio volá tuto funkci a modul plug-in určuje, zda je v pořádku vytvořit nový projekt v systému správy zdrojového kódu obsahovat projekt sady Visual Studio. Pokud uživatel klepne na tlačítko **Storno** před dokončením průvodce, projekt se nikdy nevytvoří. Pokud uživatel klepne na **tlačítko OK**, Visual Studio volá `SccOpenProject`, předávání a `SCC_OPT_CREATEIFNEW`zdroj řízený projekt je vytvořen v té době.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
