---
title: Enumerátory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204569"
---
# <a name="enumerators"></a>Enumerátory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část obsahuje seznam typů dat enumerátorů v rozhraní API modulu plug-in správy zdrojových kódů, o kterých musí modul plug-in správy zdrojových kódů doznat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kód příkazu](../extensibility/command-code-enumerator.md)  
 Vytvoří výčet možností pro funkce [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
 [Zpráva](../extensibility/message-enumerator.md)  
 Vytvoří výčet příznaků používaných pro zpětné volání tisku, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)  
 Obsahuje pojmenované konstantní hodnoty, které určují stav souboru pod správou zdrojových kódů.  
  
 [Kód stavu adresáře](../extensibility/directory-status-code-enumerator.md)  
 Obsahuje pojmenované konstantní hodnoty, které určují stav adresáře pod správou zdrojových kódů.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definuje sadu SDK modulu plug-in správy zdrojových kódů a popisuje zahrnuté prostředky.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Vyzve uživatele k zadání pokročilých možností pro daný příkaz.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Prověřuje seznam souborů pro jejich aktuální stav. Kromě toho `pfnPopulate` funkce používá funkci pro upozorňování volajícího, když soubor neodpovídá kritériím pro `nCommand` .  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Popisuje funkci zpětného volání, která je používána [SccOpenProject](../extensibility/sccopenproject-function.md) k zobrazení zpráv z modulu plug-in správy zdrojových kódů prostřednictvím integrovaného vývojového prostředí (IDE).  
  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)  
 Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.
