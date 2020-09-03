---
title: Předpoklady pro uvolnění a opětovné načtení vnořených projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197002"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Důležité informace pro uvolnění a opětovné načtení vnořených projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při implementaci vnořených typů projektů je nutné provést další kroky při uvolňování a opětovném načtení projektů. Pro správné upozornění posluchačů na události řešení je nutné správně vyvolat `OnBeforeUnloadProject` události a `OnAfterLoadProject` .  
  
 Jedním z důvodů, proč je nutné tyto události vyvolat tímto způsobem je, že nechcete, aby Správa zdrojového kódu (SCC) odstranila položky ze serveru, a pak je přidat zpátky jako něco nového, pokud existuje `Get` operace z SCC. V takovém případě by byl nový soubor načten z SCC a vy budete muset uvolnit a znovu načíst všechny soubory pro případ, že se liší. SCC volání `ReloadItem` . Vaše implementace tohoto volání je odstranit projekt a znovu ho vytvořit implementací `IVsFireSolutionEvents` volání `OnBeforeUnloadProject` a `OnAfterLoadProject` . Při provádění této implementace je SCC informován o tom, že se projekt dočasně odstranil a znovu přidal. Proto SCC v projektu nepracuje, jako kdyby byl projekt skutečně odstraněn ze serveru a pak znovu přidán.  
  
## <a name="reloading-projects"></a>Opětovné načítání projektů  
 Pro podporu opětovného načtení vnořených projektů implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodu. V implementaci nástroje `ReloadItem` zavřete vnořené projekty a pak je znovu vytvořte.  
  
 Obvykle při opětovném načtení projektu rozhraní IDE vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` události a. Pro vnořené projekty, které budou odstraněny a znovu načteny, však nadřazený projekt zahájí proces, nikoli rozhraní IDE. Vzhledem k tomu, že nadřazený projekt nevyvolává události řešení a rozhraní IDE neobsahuje žádné informace o inicializaci procesu, události nejsou vyvolány.  
  
 Pro zpracování tohoto procesu nadřazený projekt volá rozhraní od `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> rozhraní. `IVsFireSolutionEvents` má funkce, které instruují rozhraní IDE, aby vyvolalo `OnBeforeUnloadProject` událost pro uvolnění vnořeného projektu, a poté vyvolá `OnAfterLoadProject` událost pro opětovné načtení stejného projektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
