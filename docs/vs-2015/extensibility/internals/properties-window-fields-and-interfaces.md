---
title: Pole a rozhraní okna vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700825"
---
# <a name="properties-window-fields-and-interfaces"></a>Pole a rozhraní okna Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model pro výběr, který určuje, jaké informace se zobrazí v okně **vlastnosti** , je založen na okně, které se zaměřuje na integrované vývojové prostředí (IDE). Každé okno a objekt v rámci vybraného okna může mít svůj kontextový objekt výběru vložen do kontextu globálního výběru. Prostředí aktualizuje kontext globálního výběru hodnotami z rámce okna, když má toto okno fokus. V případě změny fokusu provede kontext výběru.  
  
## <a name="tracking-selection-in-the-ide"></a>Sledování výběru v integrovaném vývojovém prostředí  
 V rámci rámce okna nebo webu, který vlastní rozhraní IDE, je volána služba <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Následující kroky ukazují, jak se změna výběru vyvolala v případě, že uživatel změní fokus na jiné otevřené okno nebo když v **Průzkumník řešení**vyberete jinou položku projektu, je implementováno pro změnu obsahu zobrazeného v okně **vlastnosti** .  
  
1. Objekt vytvořený rozhraním VSPackage, který je umístěn ve vybraném okně, volá volání metody <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Kontejner výběru poskytnutý vybraným oknem vytvoří svůj vlastní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objekt. Když se změní výběr, volání VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> upozorní na všechny posluchače v prostředí, včetně okna **vlastností** změny. Poskytuje také přístup k informacím o hierarchii a položkách, které souvisejí s novým výběrem.  
  
3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a předání vybraným položkám hierarchie v `VSHPROPID_BrowseObject` parametru naplní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objekt.  
  
4. Objekt odvozený z [rozhraní IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) je vrácen pro <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> požadovanou položku a prostředí je zabalí do objektu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (viz následující krok). Pokud se volání nepovede, prostředí vytvoří druhé volání do `IVsHierarchy::GetProperty` a předá ho kontejneru výběru <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , který položka hierarchie nebo položky dodá.  
  
    Váš projekt VSPackage se nevytvoří <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , protože rozhraní VSPackage v prostředí, které ho implementuje (například **Průzkumník řešení**), sestaví <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jeho jménem.  
  
5. Prostředí vyvolá metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pro získání objektů na základě `IDispatch` rozhraní k vyplnění v okně **vlastnosti** .  
  
   Když je změněna hodnota v okně **vlastnosti** , sady VSPackage implementují `IVsTrackSelectionEx::OnElementValueChangeEx` a, `IVsTrackSelectionEx::OnSelectionChangeEx` aby nahlásila změnu hodnoty elementu. Prostředí pak vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> nebo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> zachová informace zobrazené v okně **vlastnosti** synchronizované s hodnotami vlastností. Další informace naleznete v tématu [aktualizace hodnot vlastností v okně Vlastnosti](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Kromě výběru jiné položky projektu v **Průzkumník řešení** pro zobrazení vlastností souvisejících s touto položkou můžete také zvolit jiný objekt v rámci formuláře nebo okna dokumentu pomocí rozevíracího seznamu, který je k dispozici v okně **vlastnosti** . Další informace naleznete v části [seznam objektů okna vlastnosti](../../extensibility/internals/properties-window-object-list.md).  
  
   Můžete změnit způsob zobrazení informací v mřížce okna **vlastnosti** z abecedy na kategorií a pokud je k dispozici, můžete také otevřít stránku vlastností pro vybraný objekt kliknutím na příslušná tlačítka v okně **vlastnosti** . Další informace najdete v tématu [tlačítka okna vlastnosti](../../extensibility/internals/properties-window-buttons.md) a [stránky vlastností](../../extensibility/internals/property-pages.md).  
  
   Nakonec dolní část okna **vlastností** obsahuje také popis pole vybraného v mřížce okna **vlastnosti** . Další informace najdete v tématu [získání popisů polí z okna vlastnosti](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
