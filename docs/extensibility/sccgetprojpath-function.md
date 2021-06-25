---
description: Tato funkce vyzve uživatele k zadání cesty k projektu, což je řetězec, který má smysl pouze pro modul plug-in správy zdrojového kódu.
title: SccGetProjPath – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93266464249b8de037a618bab55ede31988384cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901068"
---
# <a name="sccgetprojpath-function"></a>Funkce SccGetProjPath
Tato funkce vyzve uživatele k zadání cesty k projektu, což je řetězec, který má smysl pouze pro modul plug-in správy zdrojového kódu. Volá se, když uživatel:

- Vytvoření nového projektu

- Přidání existujícího projektu do ovládacího prvku verzí

- Pokus o vyhledání existujícího projektu pro řízení verzí

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

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Uživatelské jméno (nesmí překročit SCC_USER_SIZE, včetně ukončovací znak NULL)

 lpProjName

[in, out] Název projektu IDE, pracovního prostoru projektu nebo souboru pravidel (nesmí překročit SCC_PRJPATH_SIZE včetně ukončovacího znaku NULL).

 lpLocalPath

[in, out] Pracovní cesta projektu. Pokud je , modul plug-in správy zdrojového kódu může tento řetězec upravit (nesmí překročit `bAllowChangePath` `TRUE` _MAX_PATH, včetně ukončovací znak null).

 lpUProjPath

[in, out] Vyrovnávací paměť pro vrácenou cestu projektu (nesmí překročit SCC_PRJPATH_SIZE včetně ukončovací znaky NULL).

 bAllowChangePath

[v] Pokud je to , může modul plug-in správy zdrojového `TRUE` kódu zobrazit výzvu k zadání a úpravě `lpLocalPath` řetězce.

 pbNew

[in, out] Přidaná hodnota určuje, jestli se má vytvořit nový projekt. Vrácená hodnota označuje úspěch vytvoření projektu:

|Příchozí|Interpretace|
|--------------|--------------------|
|TRUE|Uživatel může vytvořit nový projekt.|
|FALSE|Uživatel nemusí vytvořit nový projekt.|

|Odchozí|Interpretace|
|--------------|--------------------|
|TRUE|Vytvořil se nový projekt.|
|FALSE|Byl vybrán existující projekt.|

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Projekt se úspěšně vytvořil nebo načítá.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit.|
|SCC_E_CONNECTIONFAILURE|Při pokusu o připojení k systému správy zdrojového kódu došlo k problému.|
|SCC_E_NONSPECIFICERROR|Došlo k neurčené chybě.|

## <a name="remarks"></a>Poznámky
 Účelem této funkce je, aby integrované vývojové prostředí získalo parametry a `lpProjName` `lpAuxProjPath` . Jakmile modul plug-in správy zdrojového kódu vyzve uživatele k zadání těchto informací, předá tyto dva řetězce zpět do integrovaného vývojového prostředí. Integrované vývojové prostředí tyto řetězce uchová v souboru řešení a předá je [projektu SccOpenProject](../extensibility/sccopenproject-function.md) pokaždé, když uživatel otevře tento projekt. Tyto řetězce umožňují modulu plug-in sledovat informace související s projektem.

 Při prvním volání funkce se `lpAuxProjPath` nastaví prázdný řetězec. `lProjName` může být také prázdná nebo může obsahovat název projektu IDE, který může modul plug-in správy zdrojového kódu používat nebo ignorovat. Po úspěšném vrácení funkce vrátí modul plug-in dva odpovídající řetězce. Integrované vývojové prostředí (IDE) nevynechá žádné předpoklady o těchto řetězcích, nebude je používat a neumožní uživateli je upravovat. Pokud chce uživatel změnit nastavení, integrované vývojové prostředí (IDE) zavolá znovu a předá stejné hodnoty, které získal `SccGetProjPath` dříve. Modul plug-in tak má nad těmito dvěma řetězci úplnou kontrolu.

 Pro může integrované vývojové prostředí (IDE) předat uživatelské jméno nebo může jednoduše `lpUser` předat ukazatel na prázdný řetězec. Pokud existuje uživatelské jméno, měl by ho modul plug-in správy zdrojového kódu použít jako výchozí. Pokud ale nebylo předáno žádné jméno nebo pokud se přihlášení nezdařilo s daným jménem, měl by modul plug-in vyzvat uživatele k přihlášení a po přijetí platného přihlášení ho předat `lpUser` zpět. Vzhledem k tomu, že modul plug-in může tento řetězec změnit, integrované vývojové prostředí vždy přidělí vyrovnávací paměť o velikosti ( `SCC_USER_LEN` +1).

> [!NOTE]
> První akcí, kterou integrované vývojové prostředí provádí, může být volání `SccOpenProject` funkce nebo `SccGetProjPath` funkce. Proto oba mají identický parametr, který modulu plug-in správy zdrojového kódu umožňuje přihlášení `lpUser` uživatele v obou případech. I v případě, že návrat z funkce indikuje selhání, musí modul plug-in vyplnit tento řetězec platným přihlašovacím jménem.

 `lpLocalPath` je adresář, ve kterém uživatel uchovává projekt. Může to být prázdný řetězec. Pokud aktuálně není definovaný žádný adresář (jako v případě, že se uživatel pokouší stáhnout projekt ze systému správy zdrojového kódu) a pokud je , modul `bAllowChangePath` plug-in správy zdrojového kódu může uživatele vyzvat k zadání vstupu nebo použít jinou metodu k umístění vlastního řetězce do `TRUE` `lpLocalPath` . Pokud `bAllowChangePath` je , modul plug-in by neměl změnit řetězec, protože uživatel už pracuje v `FALSE` zadaném adresáři.

 Pokud uživatel vytvoří nový projekt, který se má umístit do správy zdrojového kódu, nemusí ho modul plug-in správy zdrojového kódu v době volání ve skutečnosti vytvořit v `SccGetProjPath` systému správy zdrojového kódu. Místo toho předá zpět řetězec spolu s nenulovou hodnotou pro , což znamená, že projekt bude vytvořen `pbNew` v systému správy zdrojového kódu.

 Pokud například uživatel v  průvodci novým projektem v nástroji Visual Studio přidá svůj projekt do správy zdrojového kódu, zavolá Visual Studio tuto funkci a modul plug-in určí, jestli je v pořádku vytvořit nový projekt v systému správy zdrojového kódu tak, aby obsahoval projekt Visual Studio. Pokud uživatel před dokončením **průvodce** klikne na Zrušit, projekt se nikdy nevytvoní. Pokud uživatel klikne na **OK,** Visual Studio , předá a projekt řízený zdrojem `SccOpenProject` se vytvoří v tomto `SCC_OPT_CREATEIFNEW` okamžiku.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
