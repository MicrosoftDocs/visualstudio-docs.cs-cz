---
description: Tato funkce Určuje nadřazenou cestu projektu zadaného projektu.
title: Funkce SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 305f226117bbb9cf906231a0b9bbaa24c1d87a8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063978"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath – funkce
Tato funkce Určuje nadřazenou cestu projektu zadaného projektu. Tato funkce se volá, když uživatel přidá projekt sady Visual Studio do správy zdrojových kódů.

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

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Uživatelské jméno (až do SCC_USER_SIZE, včetně ukončovacího znaku NULL).

 lpProjPath

pro Řetězec identifikující cestu k projektu (až do SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

 lpAuxProjPath

[in, out] Pomocný řetězec identifikující projekt (až do SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

 lpParentProjPath

[in, out] Výstupní řetězec identifikující cestu nadřazeného projektu (až do SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Cesta k nadřazenému projektu se úspěšně získala.|
|SCC_E_INITIALIZEFAILED|Projekt se nepovedlo inicializovat.|
|SCC_E_INVALIDUSER|Uživatel se nemohl přihlásit do modulu plug-in správy zdrojových kódů.|
|SCC_E_UNKNOWNPROJECT|Projekt není pro modul plug-in správy zdrojových kódů známý.|
|SCC_E_INVALIDFILEPATH|Neplatná nebo nepoužitelná cesta k souboru.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_PROJSYNTAXERR|Neplatná syntaxe projektu.|
|SCC_E_CONNECTIONFAILURE|Potíže s připojením k úložišti|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Tato funkce vrací kód úspěchu nebo selhání a v případě úspěchu vyplní proměnnou `lpParentProjPath` úplnou cestou projektu k určenému projektu.

 Tato funkce vrací nadřazenou cestu projektu existujícího projektu. U kořenového projektu funkce vrátí cestu k projektu, který byl předán (tj. stejná cesta kořenového projektu). Všimněte si, že cesta projektu je řetězec, který je smysluplný pouze pro modul plug-in správy zdrojových kódů.

 Integrované vývojové prostředí (IDE) je připravené také pro příjem změn `lpUser` `lpAuxProjPath` parametrů a. Rozhraní IDE zachová tyto řetězce a předá je [SccOpenProject](../extensibility/sccopenproject-function.md) , když uživatel otevře tento projekt v budoucnu. Tyto řetězce proto poskytují způsob, jak modul plug-in správy zdrojových kódů sleduje informace, které potřebuje k přidružení k projektu.

 Tato funkce je podobná [SccGetProjPath](../extensibility/sccgetprojpath-function.md), s tím rozdílem, že nevyzve uživatele k výběru projektu. Nikdy také nevytvoří nový projekt, ale funguje pouze s existujícím projektem.

 Při `SccGetParentProjectPath` volání hodnoty `lpProjPath` a nebude `lpAuxProjPath` prázdné a bude odpovídat platnému projektu. Tyto řetězce jsou obvykle přijímány rozhraním IDE z předchozího volání `SccGetProjPath` funkce.

 `lpUser`Argument je uživatelské jméno. Rozhraní IDE předáte stejné uživatelské jméno, které dříve přijalo z `SccGetProjPath` funkce, a modul plug-in správy zdrojových kódů by měl použít název jako výchozí. Pokud už uživatel má otevřené připojení s modulem plug-in, pak se modul plug-in pokusí odstranit všechny výzvy a ujistit se, že funkce funguje tiše. Pokud se ale přihlášení nepovede, musí modul plug-in uživateli požádat o přihlášení a při přijetí platného přihlašovacího jména předat jméno zpátky `lpUser` . Vzhledem k tomu, že modul plug-in může tento řetězec změnit, rozhraní IDE vždy přidělí velikost vyrovnávací paměti ( `SCC_USER_LEN` + 1). Pokud je řetězec změněn, musí být nový řetězec platným přihlašovacím jménem (alespoň jako starý řetězec).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technické poznámky k SccCreateSubProject a SccGetParentProjectPath
 Přidání řešení a projektů do správy zdrojových kódů bylo zjednodušeno v aplikaci Visual Studio, aby bylo možné minimalizovat počet výzev uživatele k výběru umístění v systému správy zdrojů. Tyto změny jsou aktivovány v aplikaci Visual Studio, pokud modul plug-in správy zdrojových kódů podporuje obě nové funkce, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) a `SccGetParentProjectPath` funkci. Následující položku registru lze však použít k zakázání těchto změn a návratu k předchozímu chování sady Visual Studio (modul plug-in správy zdrojových kódů rozhraní API verze 1,1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Pokud tato položka registru neexistuje nebo je nastavená na DWORD: 00000000, Visual Studio se pokusí použít nové funkce `SccCreateSubProject` a `SccGetParentProjectPath` .

 Pokud je položka registru nastavena na hodnotu DWORD: 00000001, sada Visual Studio se nepokouší používat tyto nové funkce a operace přidávání do správy zdrojových kódů stejně jako v předchozích verzích sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
