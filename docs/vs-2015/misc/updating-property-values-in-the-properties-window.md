---
title: Aktualizace hodnot vlastností v okně Vlastnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 18ecf0a21c5b2d73bdf8e439d25765b6b275cbd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434186"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aktualizace hodnot vlastností v okně Vlastnosti
Existují dva způsoby, jak udržovat okno **vlastností** synchronizované se změnami hodnoty vlastností. První je zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní, které poskytuje přístup k základním funkcím okna, včetně přístupu k a vytváření nástrojů a oken nástrojů a dokumentů poskytovaných prostředím. Následující kroky popisují tento proces synchronizace.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aktualizace hodnot vlastností pomocí IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aktualizace hodnot vlastností pomocí rozhraní IVsUIShell  
  
1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby), kdykoli, když VSPackage, projekty nebo editory potřebují vytvořit nebo vypsat okna nástrojů nebo dokumentů.  
  
2. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pro zachování okna **vlastností** v synchronizaci se změnami vlastností projektu (nebo jakéhokoli jiného vybraného objektu, který je procházen pomocí okna **vlastností** ) bez implementace <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> a vyvolávání <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> událostí.  
  
3. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> navažte a zakažte klientské upozornění na události v hierarchii bez nutnosti implementovat hierarchii <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
## <a name="updating-property-values-using-iconnection"></a>Aktualizace hodnot vlastností pomocí IConnection  
 Druhý způsob, jak zajistit, aby se okno **vlastnosti** synchronizoval se změnami hodnoty vlastností, je implementace `IConnection` na připojeném objektu pro označení existence odchozích rozhraní. Chcete-li lokalizovat název vlastnosti, odvodit objekt z <xref:System.ComponentModel.ICustomTypeDescriptor> . <xref:System.ComponentModel.ICustomTypeDescriptor>Implementace může upravit popisovače vlastností, které vrátí, a změnit název vlastnosti. Chcete-li lokalizovat popis, vytvořte atribut, který je odvozen z <xref:System.ComponentModel.DescriptionAttribute> a přepište vlastnost Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Pokyny k implementaci rozhraní IConnection  
  
1. `IConnection` poskytuje přístup k dílčímu objektu enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraním. Poskytuje také přístup ke všem dílčím objektům spojovacího bodu, z nichž každý implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní.  
  
2. Každý objekt pro procházení zodpovídá za implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> události. Okno **vlastnosti** poradí pro událost nastavenou prostřednictvím `IConnection` .  
  
3. Bod připojení určuje, kolik připojení (jedna nebo více) umožňuje v rámci své implementace <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Bod připojení, který povoluje pouze jedno rozhraní, může vracet <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.  
  
4. Klient může zavolat `IConnection` rozhraní a získat tak přístup k dílčímu objektu enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>Rozhraní lze potom volat pro zobrazení výčtu přípojných bodů pro každé ID odchozího rozhraní (IID).  
  
5. `IConnection` lze také volat pro získání přístupu k podobjektům spojovacího bodu připojení k <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní pro každý odchozí identifikátor IID. Prostřednictvím <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní klient spustí nebo ukončí poradní smyčku s připojeným objektem a vlastní synchronizací klienta. Klient může také volat <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní a získat tak objekt enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> rozhraním pro vytvoření výčtu připojení, o kterých ví.  
  
## <a name="see-also"></a>Viz také  
 [Oznamuje se sledování výběru okna vlastností.](../misc/announcing-property-window-selection-tracking.md)   
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)