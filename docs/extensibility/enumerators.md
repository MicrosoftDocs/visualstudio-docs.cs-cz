---
title: Enumerátory | Microsoft Docs
description: Seznamte se s datovými typy enumerátoru v rozhraní API modulu plug-in správy zdrojového kódu, včetně kódu příkazu, zprávy, souboru stavového kódu a stavového kódu adresáře.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bdc42901cbdad3b30bb6739ec93b8979b0d56ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075273"
---
# <a name="enumerators"></a>Enumerátory
Tato část obsahuje seznam typů dat enumerátorů v rozhraní API modulu plug-in správy zdrojových kódů, o kterých musí modul plug-in správy zdrojových kódů doznat.

## <a name="in-this-section"></a>V této části
- [Kód příkazu](../extensibility/command-code-enumerator.md) Vytvoří výčet možností pro funkce [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

- [Zpráva](../extensibility/message-enumerator.md) Vytvoří výčet příznaků používaných pro zpětné volání tisku, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Kód stavu souboru](../extensibility/file-status-code-enumerator.md) Obsahuje pojmenované konstantní hodnoty, které určují stav souboru pod správou zdrojových kódů.

- [Stavový kód adresáře](../extensibility/directory-status-code-enumerator.md) Obsahuje pojmenované konstantní hodnoty, které určují stav adresáře pod správou zdrojových kódů.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md) Definuje sadu SDK modulu plug-in správy zdrojových kódů a popisuje zahrnuté prostředky.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Vyzve uživatele k zadání pokročilých možností pro daný příkaz.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Prověřuje seznam souborů pro jejich aktuální stav. Kromě toho `pfnPopulate` funkce používá funkci pro upozorňování volajícího, když soubor neodpovídá kritériím pro `nCommand` .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Popisuje funkci zpětného volání, která je používána [SccOpenProject](../extensibility/sccopenproject-function.md) k zobrazení zpráv z modulu plug-in správy zdrojových kódů prostřednictvím integrovaného vývojového prostředí (IDE).

- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md) Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.
