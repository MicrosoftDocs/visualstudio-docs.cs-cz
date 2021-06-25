---
description: Tato funkce vytvoří podprojekt s daným názvem v rámci existujícího nadřazeného projektu určeného argumentem lpParentProjPath.
title: SccCreateSubProject – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6df7a801d282113b530f24472419a9735256702
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904679"
---
# <a name="scccreatesubproject-function"></a>Funkce SccCreateSubProject
Tato funkce vytvoří podprojekt s daným názvem v rámci existujícího nadřazeného projektu určeného `lpParentProjPath` argumentem .

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parametry
 pContext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Uživatelské jméno (až do SCC_USER_SIZE včetně ukončovací znak NULL).

 lpParentProjPath

[v] Řetězec identifikující cestu nadřazeného projektu (až do SCC_PRJPATH_SIZE včetně ukončovací znak null).

 lpSubProjName

[v] Navrhovaný název podprojektu (až do SCC_PRJPATH_SIZE včetně ukončovacího znaku NULL).

 lpUProjPath

[in, out] Pomocný řetězec identifikující projekt (až SCC_PRJPATH_SIZE včetně ukončovací funkce NULL).

 lpSubProjPath

[in, out] Výstupní řetězec identifikující cestu k dílčímu projektu (až do SCC_PRJPATH_SIZE včetně ukončovací znaky NULL).

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Podprojekt se úspěšně vytvořil.|
|SCC_E_INITIALIZEFAILED|Nadřazený projekt se neinicializoval.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit k systému správy zdrojového kódu.|
|SCC_E_COULDNOTCREATEPROJECT|Podprojekt není možné vytvořit.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_UNKNOWNPROJECT|Nadřazený projekt není pro modul plug-in správy zdrojového kódu známý.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_CONNECTIONFAILURE|Došlo k problému s připojením modulu plug-in správy zdrojového kódu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Pokud už existuje podprojekt s názvem , funkce může změnit výchozí název a vytvořit tak jedinečný projekt, například přidáním "_ \<number> " do něj. Volající musí být připravený přijmout změny `lpUser` , `lpSubProjPath` a `lpAuxProjPath` . Argumenty `lpSubProjPath` a se pak používají ve volání `lpAuxProjPath` [SccOpenProject](../extensibility/sccopenproject-function.md). Po vrácení by je volající neměl upravovat. Tyto řetězce poskytují způsob, jak může modul plug-in správy zdrojového kódu sledovat informace, které potřebuje přidružit k projektu. Integrované vývojové prostředí volajícího po vrácení tyto dva parametry nezobrazí, protože modul plug-in může použít formátovaný řetězec, který nemusí být vhodný pro zobrazení. Funkce vrátí kód úspěchu nebo neúspěchu a v případě úspěchu vyplní proměnnou úplnou cestou k projektu `lpSubProjPath` nového projektu.

 Tato funkce se podobá [SccGetProjPath](../extensibility/sccgetprojpath-function.md)s tím rozdílem, že bezobslužně vytvoří projekt místo toho, aby uživatele vyzve k jeho výběru. Při volání funkce nebude funkce `SccCreateSubProject` `lpParentProjName` `lpAuxProjPath` prázdná a bude odpovídat platnému projektu. Tyto řetězce obvykle přijímá integrované vývojové prostředí z předchozího volání funkce `SccGetProjPath` nebo [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Argumentem `lpUser` je uživatelské jméno. Integrované vývojové prostředí předá stejné uživatelské jméno, které dříve přijalo z , a modul plug-in správy zdrojového kódu by měl jako výchozí `SccGetProjPath` název používat. Pokud už má uživatel otevřené připojení k modulu plug-in, měl by se modul plug-in pokusit o odstranění všech výtek, aby se ujistil, že funkce funguje bezobslužně. Pokud se ale přihlášení nezdaří, měl by modul plug-in vyzvat uživatele k přihlášení a po přijetí platného přihlášení předat jméno zpět do `lpUser` . Vzhledem k tomu, že modul plug-in může tento řetězec změnit, přidělí integrované vývojové prostředí vždy vyrovnávací paměť o velikosti (SCC_USER_LEN+1 nebo SCC_USER_SIZE, která zahrnuje místo pro ukončovací znak null). Pokud se řetězec změní, nový řetězec musí být platným přihlašovacím jménem (alespoň tak platným jako starý řetězec).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technické poznámky pro SccCreateSubProject a SccGetParentProjectPath
 Přidávání řešení a projektů do správy zdrojového kódu bylo Visual Studio, aby se minimalizoval počet výtek uživatele k výběru umístění v systému správy zdrojového kódu. Tyto změny jsou aktivovány Visual Studio, pokud modul plug-in správy zdrojového kódu podporuje jak nové funkce, tak `SccCreateSubProject` `SccGetParentProjectPath` . Následující položku registru ale můžete použít k zakázání těchto změn a návratu k předchozímu chování Visual Studio (rozhraní API modulu plug-in správy zdrojového kódu verze 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Pokud tato položka registru neexistuje nebo je nastavená na hodnotu dword:00000000, Visual Studio pokusí použít nové funkce a `SccCreateSubProject` `SccGetParentProjectPath` .

 Pokud je položka registru nastavená na dword:00000001, Visual Studio se nepokusí použít tyto nové funkce a operace přidání do správy zdrojového kódu fungují stejně jako v předchozích verzích Visual Studio.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
