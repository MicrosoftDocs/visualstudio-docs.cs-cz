---
title: Úprava izolovaného prostředí pomocí. Soubor vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194230"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Úprava izolovaného prostředí pomocí souboru .Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekt uživatelského rozhraní pro projekt izolovaného prostředí sady Visual Studio obsahuje soubor. vsct, který umožňuje určit, které skupiny aplikací a jednotlivé příkazy jsou v aplikaci k dispozici. Následuje ukázka z neupraveného souboru. vsct.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Ve výchozím nastavení jsou součástí většina příkazů a skupin příkazů. Pokud chcete vyloučit příkaz nebo skupinu příkazů, jednoduše Odkomentujte tento příkaz nebo skupinu.  
  
 Chcete-li například odebrat příkazy pro další podokno a předchozí podokno, odkomentujte `No_PaneNextPaneCommand` `No_PanePrevPaneCommand` položky a:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Podrobnější příklad těchto přizpůsobení najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Odkazované soubory  
 Výchozí soubor. vsct pro aplikaci odkazuje na následující soubory. Tyto soubory jsou umístěny v podadresáři \VisualStudioIntegration\Common\Inc\ instalačního adresáře sady Visual Studio SDK.  
  
|Soubor|Popis|  
|----------|-----------------|  
|wbids. h|Identity uživatelského rozhraní balíčku pro procházení webu|  
|AppIDCmdUsed. vsct|Tabulka příkazů pro primární prvky uživatelského rozhraní sady Visual Studio|  
|EmulatorCmdUsed. vsct|Tabulka příkazů pro prvky uživatelského rozhraní pro emulaci (Emacs) a krátkého editoru|  
|Vsdebugguids. h|Definuje identifikátory GUID pro příkazy, stránky možností a další funkce ladicího programu sady Visual Studio.|  
|VsDbgCmdUsed. vsct|Tabulka příkazů pro ladicí program|  
  
 Soubor AppIDCmdUsed. vsct obsahuje prvky uživatelského rozhraní sady Visual Studio založené na symbolech definovaných v souboru Application. vsct.  
  
 Další informace najdete v tématu [návrh tabulky příkazů XML (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) a referenční dokumentace [schématu vsct XML](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Viz také  
 [Izolované prostředí sady Visual Studio](../extensibility/visual-studio-isolated-shell.md)
