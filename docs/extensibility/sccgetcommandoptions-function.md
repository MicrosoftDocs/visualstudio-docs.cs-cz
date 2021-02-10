---
title: Funkce SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1f465e6709932cd89794c5c0558d608fadd2a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965197"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions – funkce
Tato funkce vyzve uživatele k upřesnění možností pro daný příkaz.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 iCommand

pro Příkaz, pro který jsou požadovány upřesňující možnosti (možné hodnoty naleznete v [kódu příkazu](../extensibility/command-code-enumerator.md) ).

 ppvOptions

pro Struktura možnosti (může také být `NULL` ).

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch.|
|SCC_I_ADV_SUPPORT|Modul plug-in správy zdrojových kódů podporuje rozšířené možnosti pro příkaz.|
|SCC_I_OPERATIONCANCELED|Uživatel zrušil dialogové okno **Možnosti** modulu plug-in správy zdrojových kódů.|
|SCC_E_OPTNOTSUPPORTED|Modul plug-in správy zdrojových kódů tuto operaci nepodporuje.|
|SCC_E_ISCHECKEDOUT|Tuto operaci nelze provést u souboru, který je aktuálně rezervován.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE volá tuto funkci poprvé s `ppvOptions` = `NULL` cílem zjistit, zda modul plug-in správy zdrojových kódů podporuje funkci rozšířené možnosti pro zadaný příkaz. Pokud modul plug-in podporuje funkci pro tento příkaz, rozhraní IDE tuto funkci volá znovu, když si uživatel vyžádá rozšířené možnosti (obvykle implementované jako **Rozšířené** tlačítko v dialogovém okně) a zadá ukazatel `ppvOptions` , který není null, pro tento bod na `NULL` ukazatel. Modul plug-in ukládá jakékoli pokročilé možnosti zadané uživatelem v soukromé struktuře a vrací ukazatel na tuto strukturu v `ppvOptions` . Tato struktura je pak předána do všech ostatních funkcí rozhraní API modulu plug-in správy zdrojového kódu, které o nich musí mít informace, včetně následných volání `SccGetCommandOptions` funkce.

 Příkladem může být vyjasnění této situace.

 Uživatel zvolí příkaz **Get** a IDE zobrazí dialogové okno **získat** . Rozhraní IDE volá `SccGetCommandOptions` funkci s `iCommand` nastavenou na `SCC_COMMAND_GET` a `ppvOptions` nastavenou na `NULL` . Toto je interpretováno modulem plug-in správy zdrojových kódů jako otázka "máte nějaké rozšířené možnosti pro tento příkaz?" Pokud se modul plug-in vrátí `SCC_I_ADV_SUPPORT` , rozhraní IDE zobrazí v dialogovém okně **získat** tlačítko **Upřesnit** .

 Když uživatel poprvé klikne na tlačítko **Upřesnit** , IDE znovu zavolá `SccGetCommandOptions` funkci, tentokrát s neexistujícími `NULL``ppvOptions` body na `NULL` ukazatel. Modul plug-in zobrazí vlastní dialogové okno **získat možnosti** , vyzve uživatele k zadání informací, vloží tyto informace do vlastní struktury a vrátí ukazatel na tuto strukturu v `ppvOptions` .

 Pokud uživatel klikne na tlačítko **Upřesnit** znovu ve stejném dialogovém okně, rozhraní IDE volání `SccGetCommandOptions` funkce znovu zavolá beze změny `ppvOptions` , takže se struktura předává zpět do modulu plug-in. Díky tomu může modul plug-in znovu inicializovat své dialogové okno na hodnoty, které uživatel dříve nastavil. Modul plug-in upraví strukturu na místě před vrácením.

 Nakonec, pokud uživatel klikne na **tlačítko OK** v dialogovém okně **získat** rozhraní IDE, rozhraní IDE volá [SccGet](../extensibility/sccget-function.md), který předává strukturu vrácenou v `ppvOptions` , která obsahuje pokročilé možnosti.

> [!NOTE]
> Příkaz `SCC_COMMAND_OPTIONS` se používá, když rozhraní IDE zobrazí dialogové okno **Možnosti** , které umožňuje nastavit předvolby pro uživatele, které určují, jak integrace funguje. Pokud modul plug-in správy zdrojových kódů chce dodat dialogové okno vlastní předvolby, může jej zobrazit v dialogovém okně Předvolby  rozhraní IDE. Modul plug-in je výhradně zodpovědný za získání a uchování těchto informací; rozhraní IDE je nepoužije ani ho nemění.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Kód příkazu](../extensibility/command-code-enumerator.md)
