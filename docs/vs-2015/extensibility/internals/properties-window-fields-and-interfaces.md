---
title: Vlastnosti pole a rozhraní okna | Dokumentace Microsoftu
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
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b9e7705af131bdc8c81b6cbeeac3ed4dda80aa4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721035"
---
# <a name="properties-window-fields-and-interfaces"></a>Pole a rozhraní okna Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model pro výběr k určení, které informace se zobrazují v **vlastnosti** okna je založen na okně, které má fokus v integrovaném vývojovém prostředí. Každé okno a objekt v rámci vybrané okno může mít objekt kontextu jeho výběr do kontextu globálního výběru. Prostředí aktualizuje kontext globálního výběru s hodnotami z okna rámce, když je toto okno fokus. Při změně fokusu zločinců se stejně kontext výběru.  
  
## <a name="tracking-selection-in-the-ide"></a>Výběr sledování v integrovaném vývojovém prostředí  
 Rámeček okna nebo webu, vlastní rozhraní IDE má služby zvané <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Následující kroky ukazují, jak se změna ve výběru, způsobené uživateli změnit fokus na další otevřete okno nebo výběrem jiné položce v **Průzkumníka řešení**, je implementováno s cílem změnit obsah zobrazený v  **Vlastnosti** okna.  
  
1. Objekt vytvořený pomocí vašeho balíčku VSPackage, která je umístěna ve voláních vybrané okno <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> mít <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> vyvolat <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Zásobník pro výběr poskytované vybrané okno vytvoří vlastní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objektu. Když změny výběru sady VSPackage volá <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> upozornit všechny moduly pro naslouchání v prostředí, včetně **vlastnosti** okna změny. Poskytuje také přístup k informacím o hierarchii a položky související s nový výběr.  
  
3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a předají se jí položky vybrané hierarchie `VSHPROPID_BrowseObject` naplní parametr <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objektu.  
  
4. Objekt odvozený od [rozhraní IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) se vrátí <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> pro požadované položky a prostředí zabalí jej do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (viz následující krok). Pokud selže volání prostředí volá druhé `IVsHierarchy::GetProperty`, předají se jí zásobník pro výběr <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , zadejte hierarchie položky nebo položek.  
  
    Váš projekt se nevytvoří VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> vzhledem k tomu, že v okně prostředí poskytované VSPackage, která ho implementuje (například **Průzkumníka řešení**) vytvoří <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> svým jménem.  
  
5. Prostředí volá metody pro <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> získat objekty na základě `IDispatch` rozhraní vyplnit **vlastnosti** okna.  
  
   Když je hodnota v **vlastnosti** okno se změní, implementujte rozšíření VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` a `IVsTrackSelectionEx::OnSelectionChangeEx` informuje změna hodnoty prvku. Potom se vyvolá prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> nebo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> zachovat informace zobrazené v **vlastnosti** okno Synchronizovat s hodnotami vlastností. Další informace najdete v tématu [aktualizuje hodnoty vlastností v okně Vlastnosti](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Kromě výběru jiné položky projektu v **Průzkumníka řešení** k zobrazení vlastností souvisejících s danou položku, můžete také zvolit jiný objekt z v rámci okna formuláře nebo dokumentu pomocí rozevíracího seznamu k dispozici na **Vlastnosti** okna. Další informace najdete v tématu [seznam objektů okna vlastnosti](../../extensibility/internals/properties-window-object-list.md).  
  
   Můžete změnit způsob zobrazením informací **vlastnosti** mřížky okna okno z abecedního do kategorií, a pokud je k dispozici, můžete otevřít stránku vlastnosti pro vybraný objekt také kliknutím na odpovídající tlačítko na  **Vlastnosti** okna. Další informace najdete v tématu [tlačítka okna vlastnosti](../../extensibility/internals/properties-window-buttons.md) a [stránky vlastností](../../extensibility/internals/property-pages.md).  
  
   Nakonec dolní části **vlastnosti** okno obsahuje také popis vybraném v poli **vlastnosti** mřížky okna okno. Další informace najdete v tématu [získávání popisy pole v okně Vlastnosti](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)

