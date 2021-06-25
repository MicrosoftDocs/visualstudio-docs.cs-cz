---
title: Funkce zpětného volání implementované rozhraním IDE | Microsoft Docs
description: Seznamte se s funkcemi zpětného volání, které může modul plug-in volat ve vhodných časech během operace správy zdrojového kódu a předávat informace integrovanému vývojovému prostředí(IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 78ce3a9cdd183cff0518ee3c6da9326c63297a85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899144"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkce zpětného volání implementované rozhraním IDE
Aby integrace s integrovaným vývojovým prostředím (IDE) byla co nejjednoduchá a poskytovala jednotné prostředí pro koncové uživatele, může modul plug-in správy zdrojového kódu používat funkce zpětného volání, které jsou implementované integrovaným vývojovým prostředím. Modul plug-in může tyto funkce volat ve vhodných časech během operace správy zdrojového kódu a předávat informace integrovanému vývojovému prostředí. Integrované vývojové prostředí (IDE) pak může tyto informace zobrazit jako vložené prvky v nativním uživatelském rozhraní. Uživatel má v tomto scénáři méně fragmentované prostředí, než kdyby modul plug-in využíval vlastní uživatelské rozhraní.

 Požadovaný soubor hlaviček je *scc.h*. Výchozí umístění je *\Program Files\VSIP 8.0\EnvSDK\common\inc \\*. Je také ve složce VSIP, která obsahuje ukázku modulu plug-in správy zdrojového kódu ve složce *\Program Files\VSIP 8.0\MSSCCI. \\*

## <a name="in-this-section"></a>V této části
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Popisuje funkci zpětného volání, kterou [používá SccOpenProject](../extensibility/sccopenproject-function.md) k zobrazení zpráv z modulu plug-in správy zdrojového kódu prostřednictvím integrovaného vývojového prostředí.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Popisuje funkci zpětného volání, kterou [používá SccPopulateList,](../extensibility/sccpopulatelist-function.md) pokud integrované vývojové prostředí nemá úplný přístup k informacím, které jsou k dispozici pouze pro modul plug-in správy zdrojového kódu, například úplný seznam souborů ve řízení verzí.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Popisuje funkci zpětného volání, která je používána operací [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Popisuje funkci zpětného volání, kterou používá [operace SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Popisuje funkci zpětného volání nastavenou voláním [možnosti SccSetOption,](../extensibility/sccsetoption-function.md) která umožňuje modulu plug-in správy zdrojového kódu sdělovat změny názvů zpět do integrovaného vývojového prostředí.

## <a name="related-sections"></a>Související oddíly
- [Projekt SccOpenProject](../extensibility/sccopenproject-function.md) Otevře projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Zkontroluje aktuální stav souborů v seznamu. Kromě toho používá funkci k oznámení volajícímu v případě, že soubor neodpovídá `pfnPopulate` kritériím pro `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Prozkoumá seznam adresářů a souborů v projektu nebo projektech, které jsou ve zdrojovém kódu. Každý nalezený název adresáře a souboru se předá funkci zpětného volání.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Zkontroluje změny názvů, které byly provedeny v seznamu souborů. Každý název souboru je předán funkci zpětného volání spolu se stavem změny.

- [SccSetOption](../extensibility/sccsetoption-function.md) Nastaví širokou škálu možností. Každá možnost začíná na a `SCC_OPT_xxx` má vlastní definovanou sadu hodnot.

- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md) Popisuje obsah referenční části sady SDK modulu plug-in správy zdrojového kódu.
