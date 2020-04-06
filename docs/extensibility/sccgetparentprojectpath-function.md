---
title: Funkce SccGetParentProjectPath | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700719"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath
Tato funkce určuje cestu nadřazeného projektu určeného projektu. Tato funkce je volána, když uživatel přidává projekt sady Visual Studio do správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parametry
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 lpUživatel

[dovnitř, ven] Uživatelské jméno (až SCC_USER_SIZE, včetně zakončení NULL).

 lpProjPath

[v] Řetězec identifikující cestu k projektu (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

 lpAuxProjPath

[dovnitř, ven] Pomocný řetězec identifikující projekt (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

 lpParentProjPath

[dovnitř, ven] Výstupní řetězec identifikující cestu nadřazeného projektu (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Cesta nadřazeného projektu byla úspěšně získána.|
|SCC_E_INITIALIZEFAILED|Projekt nelze inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit k modulu plug-in správy zdrojového kódu.|
|SCC_E_UNKNOWNPROJECT|Modul plug-in správy zdrojového kódu není znám.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_CONNECTIONFAILURE|Problém s připojením k úložišti.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce vrátí kód úspěchu nebo selhání a `lpParentProjPath` v případě úspěchu vyplní proměnnou úplnou cestou projektu k zadanému projektu.

 Tato funkce vrátí cestu nadřazeného projektu existujícího projektu. Pro kořenový projekt funkce vrátí cestu projektu, která byla předána (to znamená, že stejná cesta kořenového projektu). Všimněte si, že cesta projektu je řetězec, který má smysl pouze pro modul plug-in správy zdrojového kódu.

 IDE je připraven přijmout změny `lpUser` `lpAuxProjPath` a parametry také. IDE bude zachovat tyto řetězce a předat je [SccOpenProject](../extensibility/sccopenproject-function.md) při uživatel otevře tento projekt v budoucnu. Tyto řetězce proto poskytují způsob, jak modul plug-in správy zdrojového kódu sledovat informace, které potřebuje přidružit k projektu.

 Tato funkce je podobná [SccGetProjPath](../extensibility/sccgetprojpath-function.md), s tím rozdílem, že nevyzve uživatele k výběru projektu. Také nikdy nevytvoří nový projekt, ale pracuje pouze s existujícím projektem.

 Kdy `SccGetParentProjectPath` je `lpProjPath` volána a `lpAuxProjPath` nebude prázdná a bude odpovídat platnému projektu. Tyto řetězce jsou obvykle přijímány ide z `SccGetProjPath` předchozího volání funkce.

 Argument `lpUser` emituje uživatelské jméno. Rozhraní IDE předá stejné uživatelské jméno, které `SccGetProjPath` dříve obdrželz funkce a modul plug-in správy zdrojového kódu by měl použít název jako výchozí. Pokud uživatel již má otevřené připojení k modulu plug-in, pak modul plug-in by se měl pokusit odstranit všechny výzvy, aby se ujistil, že funkce funguje tiše. Pokud se však přihlášení nezdaří, modul plug-in by měl vyzvat uživatele k přihlášení a `lpUser`při přijetí platného přihlášení předat jméno zpět do aplikace . Vzhledem k tomu, že modul plug-in může tento řetězec`SCC_USER_LEN`změnit, bude ide vždy přidělit vyrovnávací paměť velikosti ( +1). Pokud se řetězec změní, nový řetězec musí být platné přihlašovací jméno (alespoň stejně platné jako starý řetězec).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technické poznámky pro SccCreateSubProject a SccGetParentProjectPath
 Přidání řešení a projektů do správy zdrojového kódu bylo v sadě Visual Studio zjednodušeno, aby se minimalizoval počet zobrazení výzvy uživatele k výběru umístění v systému správy zdrojového kódu. Tyto změny jsou aktivovány Visual Studio, pokud modul plug-in správy zdrojového kódu `SccGetParentProjectPath` podporuje obě nové funkce, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) a funkce. Následující položku registru však lze zakázat tyto změny a vrátit se k předchozí Visual Studio (Source Control Plug-in API verze 1.1) chování:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Pokud tato položka registru neexistuje nebo je nastavena na dword:00000000, Visual `SccCreateSubProject``SccGetParentProjectPath`Studio se pokusí použít nové funkce a .

 Pokud je položka registru nastavena na dword:00000001, Visual Studio se nepokusí použít tyto nové funkce a operace přidání do správy zdrojového kódu fungují stejně jako v předchozích verzích sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
