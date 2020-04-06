---
title: Čítači | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711857"
---
# <a name="enumerators"></a>Enumerátory
V této části jsou uvedeny datové typy enumeratoru v rozhraní API modulu plug-in správy zdrojového kódu, o kterém musí modul plug-in správy zdrojového kódu vědět.

## <a name="in-this-section"></a>V tomto oddílu
- [Příkazový kód](../extensibility/command-code-enumerator.md) Vytvoří výčet možností pro funkce [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Zpráva](../extensibility/message-enumerator.md) Výčet příznaky používané pro zpětné volání tisku, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Stavový kód souboru](../extensibility/file-status-code-enumerator.md) Obsahuje pojmenované konstantní hodnoty, které určují stav souboru pod smělou správě zdrojového kódu.

- [Stavový kód adresáře](../extensibility/directory-status-code-enumerator.md) Obsahuje pojmenované konstantní hodnoty, které určují stav adresáře pod shodou zdrojového kódu.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md) Definuje sadu Plug-in source Control SDK a popisuje zahrnuté prostředky.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Zobrazí uživateli výzvu k zadání rozšířených možností pro daný příkaz.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Zkontroluje seznam souborů pro jejich aktuální stav. Kromě toho používá `pfnPopulate` funkci upozornit volajícího, pokud soubor neodpovídá `nCommand`kritériím pro .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Popisuje funkci zpětného volání, kterou používá [SccOpenProject](../extensibility/sccopenproject-function.md) k zobrazení zpráv z modulu plug-in správy zdrojového kódu prostřednictvím ide.

- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md) Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.
