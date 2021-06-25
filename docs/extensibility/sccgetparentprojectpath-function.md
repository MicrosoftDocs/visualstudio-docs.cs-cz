---
description: Tato funkce určuje cestu nadřazeného projektu zadaného projektu.
title: SccGetParentProjectPath – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a0a77808004c7bc8f408bbf34a3ed4f0715b36
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900132"
---
# <a name="sccgetparentprojectpath-function"></a>Funkce SccGetParentProjectPath
Tato funkce určuje cestu nadřazeného projektu zadaného projektu. Tato funkce se volá, když uživatel přidává projekt Visual Studio do správy zdrojového kódu.

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
 pContext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Uživatelské jméno (až do SCC_USER_SIZE, včetně ukončovací znak NULL).

 lpProjPath

[v] Řetězec identifikující cestu projektu (až do SCC_PRJPATH_SIZE včetně ukončovací znaky NULL).

 lpUProjPath

[in, out] Pomocný řetězec identifikující projekt (až SCC_PRJPATH_SIZE včetně ukončovací funkce NULL).

 lpParentProjPath

[in, out] Výstupní řetězec identifikující cestu nadřazeného projektu (až SCC_PRJPATH_SIZE včetně ukončovací znaky NULL).

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Cesta k nadřazenému projektu byla úspěšně získána.|
|SCC_E_INITIALIZEFAILED|Projekt se neinicializoval.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit k modulu plug-in správy zdrojového kódu.|
|SCC_E_UNKNOWNPROJECT|Modul plug-in správy zdrojového kódu nezná projekt.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_CONNECTIONFAILURE|Problém s připojením k obchodu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce vrátí kód úspěchu nebo neúspěchu a v případě úspěchu vyplní proměnnou úplnou cestou projektu `lpParentProjPath` k zadanému projektu.

 Tato funkce vrátí cestu nadřazeného projektu existujícího projektu. Pro kořenový projekt vrátí funkce cestu projektu, která byla předána (to znamená stejná cesta ke kořenovému projektu). Všimněte si, že cesta k projektu je řetězec, který má smysl pouze pro modul plug-in správy zdrojového kódu.

 Integrované vývojové prostředí (IDE) je připravené přijímat také `lpUser` změny `lpAuxProjPath` parametrů a . Integrované vývojové prostředí tyto řetězce zachová a předá je projektu [SccOpenProject,](../extensibility/sccopenproject-function.md) když uživatel tento projekt otevře v budoucnu. Tyto řetězce proto poskytují způsob, jak může modul plug-in správy zdrojového kódu sledovat informace, které potřebuje k projektu přidružit.

 Tato funkce se podobá [SccGetProjPath](../extensibility/sccgetprojpath-function.md)s tím rozdílem, že nevyzýlí uživatele k výběru projektu. Také nikdy nevytváří nový projekt, ale funguje pouze s existujícím projektem.

 Když je volána hodnota a `SccGetParentProjectPath` nebude `lpProjPath` `lpAuxProjPath` prázdná a bude odpovídat platnému projektu. Tyto řetězce obvykle přijímá integrované vývojové prostředí (IDE) z předchozího volání `SccGetProjPath` funkce.

 Argumentem `lpUser` je uživatelské jméno. Integrované vývojové prostředí předá stejné uživatelské jméno, které dříve přijalo z funkce, a modul plug-in správy zdrojového kódu by měl jako výchozí `SccGetProjPath` název používat. Pokud už má uživatel otevřené připojení k modulu plug-in, měl by se modul plug-in pokusit o odstranění všech výtek, aby se ujistil, že funkce funguje bezobslužně. Pokud se ale přihlášení nezdaří, měl by modul plug-in vyzvat uživatele k přihlášení a po přijetí platného přihlášení předat jméno zpět do `lpUser` . Vzhledem k tomu, že modul plug-in může tento řetězec změnit, integrované vývojové prostředí vždy přidělí vyrovnávací paměť o velikosti ( `SCC_USER_LEN` +1). Pokud se řetězec změní, nový řetězec musí být platným přihlašovacím jménem (alespoň tak platným jako starý řetězec).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technické poznámky pro SccCreateSubProject a SccGetParentProjectPath
 Přidávání řešení a projektů do správy zdrojového kódu bylo Visual Studio, aby se minimalizoval počet výtek uživatele k výběru umístění v systému správy zdrojového kódu. Tyto změny jsou aktivovány Visual Studio, pokud modul plug-in správy zdrojového kódu podporuje obě nové funkce, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) a `SccGetParentProjectPath` funkci . Následující položku registru ale můžete použít k zakázání těchto změn a návratu k předchozímu chování rozhraní VISUAL STUDIO (rozhraní API modulu plug-in správy zdrojového kódu verze 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Pokud tato položka registru neexistuje nebo je nastavená na hodnotu dword:00000000, Visual Studio pokusí použít nové funkce a `SccCreateSubProject` `SccGetParentProjectPath` .

 Pokud je položka registru nastavená na dword:00000001, Visual Studio se nepokusí použít tyto nové funkce a operace přidání do správy zdrojového kódu fungují stejně jako v předchozích verzích Visual Studio.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
