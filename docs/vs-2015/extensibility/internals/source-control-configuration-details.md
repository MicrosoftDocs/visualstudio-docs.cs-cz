---
title: Podrobnosti o konfiguraci ovládacího prvku zdroje | Dokumentace Microsoftu
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
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55e2364ca096b5329369e51ccdadf07f191720e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753714"
---
# <a name="source-control-configuration-details"></a>Podrobnosti konfigurace správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kvůli implementaci správy zdrojového kódu, musíte správně nakonfigurovat systém projektu nebo editor provést následující kroky:  
  
-   Požádat o oprávnění k přechodu na změny stavu  
  
-   Požádat o oprávnění k uložení souboru  
  
-   Požádat o oprávnění, které chcete přidat, odebrat nebo přejmenovat soubory v projektu  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Požádat o oprávnění k přechodu na změny stavu  
 Projekt nebo editor musí požádat o oprávnění k přechodu na změny stavu (dirty) voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Každý editor, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> musí volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a schválení změna dokumentu z prostředí před vrácením `True` pro `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Projekt je v podstatě editor pro soubor projektu a proto má stejnou odpovědnost za implementace změnil stav sledování pro soubor projektu jako textového editoru pro jeho soubory. Prostředí zpracovává změny stavu řešení, ale je třeba ošetřit změna stavu libovolného objektu, odkazuje na řešení, ale neukládá, jako je soubor projektu nebo jeho položek. Obecně platí Pokud projekt nebo editor zodpovídá za správu trvalosti pro položku, pak je zodpovědná za implementace změnil stav sledování.  
  
 V reakci `IVsQueryEditQuerySave2::QueryEditFiles` volání, prostředí můžete dělat tyto věci:  
  
- Odmítnutí volání, chcete-li změnit, v takovém případě musí zůstat editor nebo projekt v nezměněném stavu (čisté).  
  
- Označuje, že data dokument znovu načíst. Pro projekt prostředí se znovu načte data pro projekt. Editor musí znovu načíst data z disku prostřednictvím jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementace. V obou případech se může změnit kontext v projektu nebo v editoru při opětovném načtení nástroje data.  
  
  Je složitá a obtížná úloh pozměnění odpovídající `IVsQueryEditQuerySave2::QueryEditFiles` volání na existující kódové základně. V důsledku toho má tato volání integrovat během vytváření projektu nebo editoru.  
  
## <a name="request-permission-to-save-a-file"></a>Požádat o oprávnění k uložení souboru  
 Předtím, než projekt nebo editor uloží soubor, musí volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Pro soubory projektu jsou řešení, které ví, kdy se má uložit soubor projektu automaticky dokončit těchto volání. Editory zodpovídají za provedení těchto volání, pokud editor provádění `IVsPersistDocData2` používá pomocnou funkci <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Pokud editor implementuje `IVsPersistDocData2` v tímto způsobem, pak volání `IVsQueryEditQuerySave2::QuerySaveFile` nebo `IVsQueryEditQuerySave2::QuerySaveFiles` se provádí za vás.  
  
> [!NOTE]
>  Vždy provádět tyto volání preventivně – to znamená, že v době, kdy je schopný přijímat zrušení editoru.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Požádat o oprávnění, které chcete přidat, odebrat nebo přejmenovat soubory v projektu  
 Před projektu můžete přidat, přejmenovat nebo odstranit soubor nebo adresář, musí volat odpovídající `IVsTrackProjectDocuments2::OnQuery*` metody k žádosti o oprávnění z prostředí. Pokud je povoleno, pak projektu musíte dokončit operaci a poté zavolejte odpovídající `IVsTrackProjectDocuments2::OnAfter*` metoda oznámit prostředí, operace se dokončila. Projekt musí volat metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> rozhraní pro všechny soubory (například speciální) a ne jenom nadřazených souborů. Volání souboru jsou povinné, ale volání adresáře jsou volitelné. Pokud váš projekt obsahuje informace o adresáři, pak by měly volat odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody, ale pokud tyto informace nemusí, pak prostředí se odvodit informace o adresář.  
  
 Projekt by neměl volat metody `IVsTrackProjectDocuments2` v projektu otevřít nebo zavřít. Naslouchací procesy, které mají tyto informace při spuštění může čekat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> událostí a iteraci v rámci řešení najít informace, které potřebují. Při vypnutí není potřeba tyto informace. `IVsTrackProjectDocuments2` je k dispozici z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Pro každou přidat, přejmenovat a akce odebrat, je `OnQuery*` metoda a `OnAfter*` metoda. Volání `OnQuery*` metoda požádat oprávnění k přidávání, přejmenování nebo odeberte soubor nebo adresář. Volání `OnAfter*` metoda po souboru nebo adresáře přidat, přejmenován nebo odebrat a nový stav odráží stav projektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)

