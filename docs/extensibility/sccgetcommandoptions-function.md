---
title: Funkce SccGetCommandOptions | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700824"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions
Tato funkce vyzve uživatele k upřesňujícím možnostem pro daný příkaz.

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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 Icommand

[v] Příkaz, pro který jsou požadovány rozšířené možnosti (možné hodnoty naleznete v [části Kód příkazu).](../extensibility/command-code-enumerator.md)

 ppvMožnosti

[v] Option struktura (může `NULL`být také ).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch|
|SCC_I_ADV_SUPPORT|Modul plug-in správy zdrojového kódu podporuje rozšířené možnosti příkazu.|
|SCC_I_OPERATIONCANCELED|Uživatel zrušil dialogové okno **Možnosti** modulu plug-in správy zdrojového kódu.|
|SCC_E_OPTNOTSUPPORTED|Modul plug-in správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ISCHECKEDOUT|Tuto operaci nelze provést u souboru, který je aktuálně rezervován.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 IDE volá tuto funkci poprvé `ppvOptions` = `NULL` s k určení, pokud modul plug-in řízení zdrojového kódu podporuje rozšířené možnosti funkce pro zadaný příkaz. Pokud modul plug-in podporuje funkci pro tento příkaz, ide volá tuto funkci znovu, když **Advanced** uživatel požaduje rozšířené možnosti (obvykle implementovány jako `ppvOptions` rozšířené tlačítko `NULL` v dialogovém okně) a poskytuje ukazatel bez null pro tento ukazatel odkazuje na ukazatel. Modul plug-in ukládá všechny rozšířené možnosti určené uživatelem v soukromé struktuře a vrátí ukazatel na tuto strukturu v aplikaci `ppvOptions`. Tato struktura je pak předána všem ostatním funkcím rozhraní API modulu plug-in správy zdrojového kódu, které o ní potřebují vědět, včetně následných `SccGetCommandOptions` volání funkce.

 Příklad může pomoci objasnit tuto situaci.

 Uživatel zvolí příkaz **Získat** a rozhraní IDE zobrazí dialogové okno **Získat.** IDE volá `SccGetCommandOptions` funkci `iCommand` s `SCC_COMMAND_GET` nastavenou a `ppvOptions` nastavenou na `NULL`. To je interpretováno modul plug-in správy zdrojového kódu jako otázka "Máte nějaké rozšířené možnosti pro tento příkaz?" Pokud se modul `SCC_I_ADV_SUPPORT`plug-in vrátí , ide zobrazí **tlačítko Upřesnit** v dialogovém okně **Získat.**

 Při prvním kliknutí uživatele na tlačítko **Upřesnit** ide `SccGetCommandOptions` znovu volá funkci, tentokrát`NULL``ppvOptions` s non- který odkazuje na `NULL` ukazatel. Modul plug-in zobrazí vlastní dialogové okno **Získat možnosti,** vyzve uživatele k zadání informací, vloží tyto `ppvOptions`informace do vlastní struktury a vrátí ukazatel na tuto strukturu v aplikaci .

 Pokud uživatel klepne na tlačítko **Upřesnit** znovu ve stejném `SccGetCommandOptions` dialogovém `ppvOptions`okně, ide volá funkci znovu beze změny , takže struktura je předána zpět do modulu plug-in. To umožňuje modulu plug-in znovu inicializovat jeho dialogové okno na hodnoty, které uživatel dříve nastavil. Plug-in upravuje strukturu na místě před návratem.

 Nakonec, když uživatel klepne na **tlačítko OK** v dialogovém okně **Získat** rozhraní IDE, ide volá [SccGet](../extensibility/sccget-function.md), předávání struktury vrácené v, `ppvOptions` který obsahuje rozšířené možnosti.

> [!NOTE]
> Příkaz `SCC_COMMAND_OPTIONS` se používá, když rozhraní IDE zobrazí dialogové okno **Možnosti,** které umožňuje uživateli nastavit předvolby, které řídí, jak integrace funguje. Pokud chce modul plug-in správy zdrojového kódu zadat vlastní dialogové okno předvoleb, může jej zobrazit z tlačítka **Upřesnit** v dialogovém okně předvoleb ide. Modul plug-in je výhradně zodpovědný za získání a uchování těchto informací. ide nepoužívá ani upravovat.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Příkazový kód](../extensibility/command-code-enumerator.md)
