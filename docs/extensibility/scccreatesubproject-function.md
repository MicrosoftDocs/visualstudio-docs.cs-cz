---
title: Funkce SccCreateSubProject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701042"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject
Tato funkce vytvoří dílčí projekt s daným názvem pod `lpParentProjPath` existujícím nadřazeným projektem určeným argumentem.

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
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 lpUživatel

[dovnitř, ven] Uživatelské jméno (až SCC_USER_SIZE, včetně zakončení NULL).

 lpParentProjPath

[v] Řetězec identifikující cestu nadřazeného projektu (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

 lpSubProjName

[v] Navrhovaný název dílčího projektu (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

 lpAuxProjPath

[dovnitř, ven] Pomocný řetězec identifikující projekt (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

 lpSubProjPath

[dovnitř, ven] Výstupní řetězec identifikující cestu pro dílčí projekt (až SCC_PRJPATH_SIZE, včetně zakončení NULL).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dílčí projekt byl úspěšně vytvořen.|
|SCC_E_INITIALIZEFAILED|Nadřazený projekt nelze inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit do systému správy zdrojového kódu.|
|SCC_E_COULDNOTCREATEPROJECT|Dílčí projekt nelze vytvořit.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_UNKNOWNPROJECT|Nadřazený projekt není znám modulu plug-in správy zdrojového kódu.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_CONNECTIONFAILURE|Došlo k potížím s připojením modulu plug-in správy zdrojového kódu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Pokud dílčí projekt s názvem již existuje, funkce může změnit výchozí název a vytvořit tak\<jedinečný název, například přidáním "_ číslo>". Volající musí být připraven přijmout `lpUser` `lpSubProjPath`změny `lpAuxProjPath`v , a . `lpSubProjPath` Argumenty`lpAuxProjPath` a jsou pak použity ve volání [SccOpenProject](../extensibility/sccopenproject-function.md). Neměly by být změněny volajícím po návratu. Tyto řetězce poskytují způsob, jak modul plug-in správy zdrojového kódu sledovat informace, které potřebuje přidružit k projektu. IDE volajícího nezobrazí tyto dva parametry při návratu, protože modul plug-in můžete použít formátovaný řetězec, který nemusí být vhodné pro zobrazení. Funkce vrátí kód úspěchu nebo selhání a v `lpSubProjPath` případě úspěchu vyplní proměnnou úplnou cestou projektu k novému projektu.

 Tato funkce je podobná [SccGetProjPath](../extensibility/sccgetprojpath-function.md), s tím rozdílem, že tiše vytvoří projekt, spíše než výzvu uživateli vybrat jeden. Když `SccCreateSubProject` je funkce `lpParentProjName` volána a `lpAuxProjPath` nebude prázdná a bude odpovídat platnému projektu. Tyto řetězce jsou obvykle přijímány ide z `SccGetProjPath` předchozího volání funkce nebo [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Argument `lpUser` emituje uživatelské jméno. Rozhraní IDE předá stejné uživatelské jméno, které `SccGetProjPath`dříve obdrželo od aplikace , a modul plug-in správy zdrojového kódu by měl použít název jako výchozí. Pokud uživatel již má otevřené připojení k modulu plug-in, pak modul plug-in by se měl pokusit odstranit všechny výzvy, aby se ujistil, že funkce funguje tiše. Pokud se však přihlášení nezdaří, modul plug-in by měl vyzvat uživatele k přihlášení a `lpUser`při přijetí platného přihlášení předat jméno zpět do aplikace . Vzhledem k tomu, že modul plug-in může tento řetězec změnit, ide bude vždy přidělit vyrovnávací paměť velikosti (SCC_USER_LEN +1 nebo SCC_USER_SIZE, který obsahuje místo pro zakončení null). Pokud se řetězec změní, nový řetězec musí být platné přihlašovací jméno (alespoň stejně platné jako starý řetězec).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technické poznámky pro SccCreateSubProject a SccGetParentProjectPath
 Přidání řešení a projektů do správy zdrojového kódu bylo v sadě Visual Studio zjednodušeno, aby se minimalizoval počet zobrazení výzvy uživatele k výběru umístění v systému správy zdrojového kódu. Tyto změny jsou aktivovány visual studio, pokud modul plug-in `SccCreateSubProject` `SccGetParentProjectPath`správy zdrojového kódu podporuje obě nové funkce a . Následující položku registru však lze zakázat tyto změny a vrátit se k předchozí Visual Studio (Source Control Plug-in API verze 1.1) chování:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Pokud tato položka registru neexistuje nebo je nastavena na dword:00000000, Visual `SccCreateSubProject` `SccGetParentProjectPath`Studio se pokusí použít nové funkce a .

 Pokud je položka registru nastavena na dword:00000001, Visual Studio se nepokusí použít tyto nové funkce a operace přidání do správy zdrojového kódu fungují stejně jako v předchozích verzích sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
