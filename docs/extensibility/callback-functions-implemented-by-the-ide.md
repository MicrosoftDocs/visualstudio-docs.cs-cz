---
title: Funkce zpětného volání implementované rozhraním IDE | Microsoft Docs
description: Přečtěte si o funkcích zpětného volání, které modul plug-in může zavolat během příslušné doby během operace správy zdrojových kódů k předání informací do IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42d7c02f2beb24aa92c0a3319c44cce3c8b325b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911259"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkce zpětného volání implementované rozhraním IDE
Pro zajištění bezproblémové integrace s integrovaným vývojovým prostředím (IDE) a zajištěním jednotného prostředí koncového uživatele může modul plug-in správy zdrojových kódů používat funkce zpětného volání, které jsou implementovány rozhraním IDE. Modul plug-in může zavolat tyto funkce v příslušné době během operace správy zdrojových kódů, aby předávala informace prostředí IDE. rozhraní IDE pak může tyto informace zobrazit jako vložené prvky v jeho nativním uživatelském rozhraní. V tomto scénáři má uživatel méně fragmentovaných prostředí, než kdyby byl modul plug-in zaměstnán vlastním uživatelským rozhraním.

 Požadovaný hlavičkový soubor je *SCC. h*. Výchozí umístění je *\Program Files\VSIP 8.0 \ EnvSDK\common\inc \\*. Je také ve složce VSIP, která obsahuje ukázku modulu plug-in správy zdrojových kódů v *\Program Files\VSIP 8.0 \ MSSCCI \\*.

## <a name="in-this-section"></a>V této části
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Popisuje funkci zpětného volání, která je používána [SccOpenProject](../extensibility/sccopenproject-function.md) k zobrazení zpráv z modulu plug-in správy zdrojových kódů prostřednictvím integrovaného vývojového prostředí (IDE).

- [POPLISTFUNC](../extensibility/poplistfunc.md) Popisuje funkci zpětného volání, která je používána službou [SccPopulateList](../extensibility/sccpopulatelist-function.md) , pokud rozhraní IDE nemá úplný přístup k informacím, které jsou k dispozici pouze pro modul plug-in správy zdrojových kódů, jako je například úplný seznam souborů v rámci správy verzí.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Popisuje funkci zpětného volání, která je používána operací [SccQueryChanges](../extensibility/sccquerychanges-function.md) .

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Popisuje funkci zpětného volání, která je používána operací [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) .

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Popisuje funkci zpětného volání nastavenou voláním metody [SccSetOption](../extensibility/sccsetoption-function.md) , která umožňuje, aby modul plug-in správy zdrojových kódů komunikoval změny názvu zpět do rozhraní IDE.

## <a name="related-sections"></a>Související oddíly
- [SccOpenProject](../extensibility/sccopenproject-function.md) Otevře projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Prověřuje seznam souborů pro jejich aktuální stav. Kromě toho `pfnPopulate` funkce používá funkci pro upozorňování volajícího, když soubor neodpovídá kritériím pro `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Prověřuje seznam adresářů a souborů v projektu nebo projektech, které jsou pod správou zdrojových kódů. Každý nalezený adresář a název souboru se předává funkci zpětného volání.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Kontroluje změny názvů, které byly provedeny v seznamu souborů. Každý název souboru je předán funkci zpětného volání spolu se stavem změny.

- [SccSetOption](../extensibility/sccsetoption-function.md) Nastaví širokou škálu možností. Každá možnost začíná `SCC_OPT_xxx` a má svou vlastní definovanou sadu hodnot.

- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md) Popisuje obsah oddílu reference v sadě SDK modulu plug-in správy zdrojového kódu.
