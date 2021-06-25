---
description: Tato funkce vyzve uživatele k zadání rozšířených možností pro daný příkaz.
title: SccGetCommandOptions – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7972d874668649b8bb86adc15008880c5fc4152e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903928"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions – funkce
Tato funkce vyzve uživatele k zadání rozšířených možností pro daný příkaz.

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
 pvContext (Kontext pv)

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 Icommand

[v] Příkaz, pro který se požaduje upřesňující možnosti (možné [hodnoty najdete v části](../extensibility/command-code-enumerator.md) Příkazový kód).

 ppvOptions

[v] Struktura možností (může být také `NULL` ).

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch.|
|SCC_I_ADV_SUPPORT|Modul plug-in správy zdrojového kódu podporuje upřesňující možnosti pro příkaz .|
|SCC_I_OPERATIONCANCELED|Uživatel zrušil dialogové okno Možnosti modulu plug-in správy **zdrojového** kódu.|
|SCC_E_OPTNOTSUPPORTED|Modul plug-in správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ISCHECKEDOUT|Tuto operaci nelze provést u aktuálně rezervování souboru.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Integrované vývojové prostředí tuto funkci poprvé volá pomocí , aby určilo, jestli modul plug-in správy zdrojového kódu podporuje funkci rozšířených možností `ppvOptions` = `NULL` pro zadaný příkaz. Pokud modul plug-in podporuje funkci pro tento příkaz, volá integrované vývojové prostředí tuto funkci  znovu, když uživatel požaduje upřesňující možnosti (obvykle implementované jako tlačítko Upřesnit v dialogovém okně) a předá ukazatel, který nemá hodnotu NULL, aby odkazoval `ppvOptions` na `NULL` ukazatel. Modul plug-in ukládá všechny upřesňující možnosti zadané uživatelem v privátní struktuře a vrací ukazatel na strukturu v `ppvOptions` . Tato struktura se pak předá všem ostatním funkcím rozhraní API modulu plug-in správy zdrojového kódu, které o ní potřebují vědět, včetně následných volání `SccGetCommandOptions` funkce.

 S objasněním této situace vám může pomoct příklad.

 Uživatel zvolí příkaz **Get** a integrované vývojové prostředí (IDE) zobrazí **dialogové okno** Získat. Integrované vývojové prostředí volá funkci s nastavenou na a `SccGetCommandOptions` `iCommand` `SCC_COMMAND_GET` `ppvOptions` nastavenou na `NULL` . To modul plug-in správy zdrojového kódu interpretuje jako otázku: "Máte pro tento příkaz nějaké pokročilé možnosti?" Pokud modul plug-in vrátí , integrované vývojové prostředí `SCC_I_ADV_SUPPORT` (IDE) **zobrazí v dialogovém okně** **Získat** tlačítko Upřesnit.

 Když uživatel poprvé klikne na tlačítko **Upřesnit,** rozhraní IDE znovu zavolá funkci, tentokrát s hodnotou mimo, která odkazuje `SccGetCommandOptions` `NULL``ppvOptions` na `NULL` ukazatel. Modul plug-in zobrazí  vlastní dialogové okno Získat možnosti, vyzve uživatele k zadání informací, tyto informace zadá do vlastní struktury a vrátí ukazatel na strukturu v `ppvOptions` nástroji .

 Pokud uživatel ve stejném dialogovém **okně** znovu klikne na Upřesnit, volá integrované vývojové prostředí funkci znovu beze změny , aby se struktura předal zpět do `SccGetCommandOptions` modulu `ppvOptions` plug-in. To modulu plug-in umožňuje znovu inicializovat dialogové okno na hodnoty, které uživatel nastavil dříve. Modul plug-in před vrácením upraví strukturu.

 Nakonec, když uživatel v dialogovém okně  Získat v integrovaném vývojovém prostředí klikne na **OK,** zavolá integrované vývojové prostředí [(IDE) SccGet](../extensibility/sccget-function.md)a předá strukturu vrácenou v , která obsahuje `ppvOptions` pokročilé možnosti.

> [!NOTE]
> Příkaz se používá, když integrované vývojové prostředí (IDE) zobrazí dialogové okno Možnosti, které umožňuje uživateli nastavit předvolby, které řídí, `SCC_COMMAND_OPTIONS` jak integrace funguje.  Pokud modul plug-in správy zdrojového kódu chce zadat vlastní  dialogové okno předvoleb, může ho zobrazit z tlačítka Upřesnit v dialogovém okně předvoleb integrovaného vývojového prostředí. Modul plug-in zodpovídá výhradně za získání a uchování těchto informací. Integrované vývojové prostředí (IDE) ho nebude používat ani upravovat.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Kód příkazu](../extensibility/command-code-enumerator.md)
