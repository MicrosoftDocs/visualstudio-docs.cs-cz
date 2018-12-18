---
title: Důležité informace pro uvolnění a opětovné načtení vnořených projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28c5ba7dffecd73556a5f963c471910bb190f1db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756979"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Důležité informace pro uvolnění a opětovné načtení vnořených projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při implementaci typy vnořených projektů, je nutné provést další kroky při odebrat a znovu načíst projekty. Pokud chcete informovat správně naslouchacích procesů událostí řešení, musíte správně zvýšit `OnBeforeUnloadProject` a `OnAfterLoadProject` události.  
  
 Jedním z důvodů musí vyvolat tyto události tímto způsobem je, že nechcete, aby zdrojového kódu (SCC) k odstranění položek ze serveru a pak je přidat zpět jako něco nového, když je `Get` zamezil operacím SCC. V takovém případě nový soubor budou načteny z SCC a budete muset odebrat a znovu načíst všechny soubory v případě, že se liší. Volání SCC `ReloadItem`. Implementace tohoto volání je odstraňte projekt a znovu je vytvořte znovu implementací `IVsFireSolutionEvents` volat `OnBeforeUnloadProject` a `OnAfterLoadProject`. Při provádění této implementaci SCC je informován, že projekt dočasně odstranila a znovu přidat. Proto SCC nepracuje se projekt jakoby projektu ve skutečnosti odstranila ze serveru a pak znovu přidat.  
  
## <a name="reloading-projects"></a>Opětovné načítání projektů  
 Probíhá opětovné načtení vnořených projektů účelem je implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metoda. Ve vaší implementaci `ReloadItem`, zavřete vnořených projektů a pak je znovu vytvořit.  
  
 Obvykle po opětovném načtení nástroje projekt rozhraní IDE vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> a `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` události. Pro vnořené projekty, které se odstraní a znovu načten, ale nadřazený projekt zahájí proces, není rozhraní IDE. Protože nadřazený projekt nevyvolává události řešení a integrovaného vývojového prostředí nemá žádné informace o inicializaci procesu, události nejsou započteny.  
  
 Pro zpracování tohoto procesu, volání nadřazený projekt `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> rozhraní vypnout <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> rozhraní. `IVsFireSolutionEvents` obsahuje funkce, které sdělení rozhraní IDE, aby se vyvolala `OnBeforeUnloadProject` události uvolněte vnořený projekt a poté `OnAfterLoadProject` na stejný projekt znovu načíst události.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Vnoření projektů](../../extensibility/internals/nesting-projects.md)

