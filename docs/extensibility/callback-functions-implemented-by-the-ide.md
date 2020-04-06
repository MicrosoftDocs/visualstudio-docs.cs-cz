---
title: Funkce zpětného volání implementované ide | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739894"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkce zpětného volání implementované ide
Chcete-li, aby integrace s integrovaným vývojovým prostředím (IDE) byla co nejhladší a aby bylo zajištěno jednotné prostředí pro koncové uživatele, může modul plug-in správy zdrojového kódu používat funkce zpětného volání implementované rozhraním IDE. Modul plug-in může volat tyto funkce ve vhodných časech během operace správy zdrojového kódu předat informace do ide; Rozhraní IDE pak může zobrazit tyto informace jako vložené prvky v nativním uživatelském rozhraní. Uživatel má méně fragmentované prostředí v tomto scénáři, než pokud modul plug-in používá vlastní uživatelské rozhraní.

 Požadovaný soubor záhlaví je *scc.h*. Výchozí umístění je *\Program Files\VSIP 8.0\EnvSDK\common\inc\\*. Je také ve složce VSIP, která má ukázku modulu plug-in správy zdrojového kódu na *adrese \Program Files\VSIP 8.0\MSSCCI\\*.

## <a name="in-this-section"></a>V tomto oddílu
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Popisuje funkci zpětného volání, kterou používá [SccOpenProject](../extensibility/sccopenproject-function.md) k zobrazení zpráv z modulu plug-in správy zdrojového kódu prostřednictvím ide.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Popisuje funkci zpětného volání, kterou používá [funkce SccPopulateList,](../extensibility/sccpopulatelist-function.md) pokud rozhraní IDE nemá úplný přístup k informacím, které jsou k dispozici pouze pro modul plug-in správy zdrojového kódu, například úplný seznam souborů pod správou verzí.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Popisuje funkci zpětného volání, která je používána operací [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Popisuje funkci zpětného volání, která je používána operací [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Popisuje funkci zpětného volání nastavenou voláním [sccSetOption,](../extensibility/sccsetoption-function.md) která umožňuje modulu plug-in správy zdrojového kódu komunikovat změny názvů zpět do ide.

## <a name="related-sections"></a>Související oddíly
- [Projekt SccOpen](../extensibility/sccopenproject-function.md) Otevře projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Zkontroluje seznam souborů pro jejich aktuální stav. Kromě toho používá `pfnPopulate` funkci upozornit volajícího, pokud soubor neodpovídá `nCommand`kritériím pro .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Zkontroluje seznam adresářů a souborů v projektu nebo projekty, které jsou pod smytem zdrojového kódu. Každý nalezený adresář a název souboru je předán funkci zpětného volání.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Zkoumá změny názvů, které byly provedeny v seznamu souborů. Každý název souboru je předán funkci zpětného volání spolu s jeho stavem změny.

- [SccSetOption](../extensibility/sccsetoption-function.md) Nastaví širokou škálu možností. Každá možnost `SCC_OPT_xxx` začíná a má vlastní definovanou sadu hodnot.

- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md) Popisuje obsah referenční části sady SDK modulu plug-in správy zdrojového kódu.
