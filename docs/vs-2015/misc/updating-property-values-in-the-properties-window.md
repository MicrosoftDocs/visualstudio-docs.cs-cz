---
title: Aktualizuje hodnoty vlastností v okně Vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 8db48e1f746afa8f8f219935555815587ce5823c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290482"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aktualizuje hodnoty vlastností v okně Vlastnosti
Existují dva způsoby, jak zachovat **vlastnosti** okno, které jsou synchronizované s změně hodnoty vlastnosti. První je pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní, které poskytuje přístup k základní oddílová funkce, včetně přístupu k a vytvoření oken nástrojů a dokumentu poskytovaných prostředím. Následující kroky popisují proces synchronizace.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aktualizuje hodnoty vlastností pomocí IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Chcete-li aktualizovat pomocí rozhraní IVsUIShell hodnoty vlastností  
  
1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby) kdykoli VSPackages, projekty, nebo editory musíte vytvořit nebo výčet nástroj nebo dokumentu.  
  
2.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zachovat **vlastnosti** okno, které jsou synchronizované s změny vlastností pro projekt (nebo vybraný objekt prochází se jím podle **vlastnosti** okno) bez implementace <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> MSMQEvent_Arrived; <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> události.  
  
3.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> k zahájení a zakázat, klientské oznámení událostí hierarchii bez nutnosti hierarchii k implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Aktualizuje se pomocí připojení IConnection hodnoty vlastností  
 Druhý způsob, jak uchovávat **vlastnosti** je okno, které jsou synchronizované s změně hodnoty vlastnosti k implementaci `IConnection` umožňující připojení k objektu k označení existenci odchozí rozhraní. Pokud chcete lokalizovat název vlastnosti, jsou odvozeny z objektu <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Implementace můžete upravit vlastnosti popisovače vrátí a změnit název vlastnosti. Chcete-li lokalizovat popis, vytvořit atribut, který je odvozen od <xref:System.ComponentModel.DescriptionAttribute> a přepsat vlastnost Popis.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Důležité informace při implementaci rozhraní připojení IConnection  
  
1.  `IConnection` poskytuje přístup k enumerátoru dílčí objekt se <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraní. Také poskytuje přístup ke všem připojení bodu dílčí objektům, každý z která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní.  
  
2.  Libovolný objekt procházet zodpovídá za implementace <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> událostí. **Vlastnosti** okno vás upozorní, události nastavený prostřednictvím `IConnection`.  
  
3.  Spojovací bod určuje, kolik připojení (jeden nebo více) povoluje v jeho provádění <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Spojovací bod, který umožňuje pouze jedno rozhraní můžou vrátit <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.  
  
4.  Klient může volat `IConnection` rozhraní se získat přístup k enumerátoru dílčí objekt se <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraní. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Rozhraní může být volána pro výčet spojovacích bodů pro každou odchozí ID rozhraní (IID).  
  
5.  `IConnection` Můžete také volat získat přístup k připojení bodu podřízených objektů s <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pro každou odchozí identifikátor IID rozhraní. Až <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní, klient spustí nebo ukončí advisory smyčky s umožňující připojení k objektu a klienta vlastní synchronizaci. Klient může také volat <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní získat objekt enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> rozhraní pro připojení, která ví o zobrazení výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Oznamujeme vydání výběr vlastností okna Sledování](../misc/announcing-property-window-selection-tracking.md)   
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)