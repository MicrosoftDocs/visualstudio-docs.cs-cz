---
title: Funkce SccCreateSubProject | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701042"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject – funkce
Tato funkce vytvoří dílčí projekt se zadaným názvem v rámci existujícího nadřazeného projektu určeného `lpParentProjPath` argumentem.

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

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Uživatelské jméno (až do SCC_USER_SIZE, včetně ukončovacího znaku NULL).

 lpParentProjPath

pro Řetězec identifikující cestu nadřazeného projektu (až do SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

 lpSubProjName

pro Navrhovaný název dílčího projektu (až do SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

 lpAuxProjPath

[in, out] Pomocný řetězec identifikující projekt (až do SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

 lpSubProjPath

[in, out] Výstupní řetězec identifikující cestu pro dílčí projekt (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dílčí projekt byl úspěšně vytvořen.|
|SCC_E_INITIALIZEFAILED|Nadřazený projekt nešlo inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit do systému správy zdrojového kódu.|
|SCC_E_COULDNOTCREATEPROJECT|Nelze vytvořit dílčí projekt.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_UNKNOWNPROJECT|Nadřazený projekt není pro modul plug-in správy zdrojových kódů známý.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_CONNECTIONFAILURE|Došlo k potížím s připojením modulu plug-in správy zdrojového kódu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Pokud dílčí projekt s tímto názvem již existuje, funkce může změnit výchozí název a vytvořit tak jedinečného, například přidáním "_ \<number> " do něj. Volající musí být připravený, aby přijímal změny `lpUser` v, `lpSubProjPath` a `lpAuxProjPath` . `lpSubProjPath`Argumenty a `lpAuxProjPath` se pak použijí při volání do [SccOpenProject](../extensibility/sccopenproject-function.md). Nesmí je měnit volajícím při návratu. Tyto řetězce poskytují způsob, jak má modul plug-in správy zdrojových kódů sledovat informace, které je potřeba přidružit k projektu. Volající rozhraní IDE nebude po návratu tyto dva parametry zobrazit, protože modul plug-in může použít formátovaný řetězec, který nemusí být vhodný pro zobrazení. Funkce vrátí kód úspěchu nebo selhání a v případě úspěchu vyplní proměnnou `lpSubProjPath` úplnou cestou projektu k novému projektu.

 Tato funkce je podobná [SccGetProjPath](../extensibility/sccgetprojpath-function.md), s tím rozdílem, že v tichém pokusu vytvoří projekt, ale nevyzve uživatele k výběru některého z nich. Když `SccCreateSubProject` je funkce volána a nebude `lpParentProjName` `lpAuxProjPath` prázdná a bude odpovídat platnému projektu. Tyto řetězce jsou obvykle přijímány rozhraním IDE z předchozího volání `SccGetProjPath` funkce nebo [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 `lpUser`Argument je uživatelské jméno. Rozhraní IDE předáte stejné uživatelské jméno, ze kterého bylo dříve přijato `SccGetProjPath` , a modul plug-in správy zdrojových kódů by měl používat název jako výchozí. Pokud už uživatel má otevřené připojení s modulem plug-in, pak se modul plug-in pokusí odstranit všechny výzvy a ujistit se, že funkce funguje tiše. Pokud se ale přihlášení nepovede, musí modul plug-in uživateli požádat o přihlášení a při přijetí platného přihlašovacího jména předat jméno zpátky `lpUser` . Vzhledem k tomu, že modul plug-in může tento řetězec změnit, rozhraní IDE vždy přidělí velikost vyrovnávací paměti (SCC_USER_LEN + 1 nebo SCC_USER_SIZE, která obsahuje místo pro ukončovací znak null). Pokud je řetězec změněn, musí být nový řetězec platným přihlašovacím jménem (alespoň jako starý řetězec).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technické poznámky k SccCreateSubProject a SccGetParentProjectPath
 Přidání řešení a projektů do správy zdrojových kódů bylo zjednodušeno v aplikaci Visual Studio, aby bylo možné minimalizovat počet výzev uživatele k výběru umístění v systému správy zdrojů. Tyto změny jsou aktivovány v aplikaci Visual Studio, pokud modul plug-in správy zdrojových kódů podporuje obě nové funkce `SccCreateSubProject` a `SccGetParentProjectPath` . Následující položku registru lze však použít k zakázání těchto změn a návratu na předchozí verzi sady Visual Studio (modul plug-in správy zdrojových kódů rozhraní API verze 1,1):

 **[HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Pokud tato položka registru neexistuje nebo je nastavená na DWORD: 00000000, Visual Studio se pokusí použít nové funkce `SccCreateSubProject` a `SccGetParentProjectPath` .

 Pokud je položka registru nastavena na hodnotu DWORD: 00000001, sada Visual Studio se nepokouší používat tyto nové funkce a operace přidávání do správy zdrojových kódů stejně jako v předchozích verzích sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
