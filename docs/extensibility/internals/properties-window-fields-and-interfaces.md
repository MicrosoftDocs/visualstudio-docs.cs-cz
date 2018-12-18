---
title: Vlastnosti pole a rozhraní okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 149c02918ec909c03c1102a5fc0f1643b79fb46d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883403"
---
# <a name="properties-window-fields-and-interfaces"></a>Pole a rozhraní okna Vlastnosti
Model pro výběr k určení, které informace se zobrazují v **vlastnosti** okna je založen na okně, které má fokus v integrovaném vývojovém prostředí. Každé okno a objekt v rámci vybrané okno může mít objekt kontextu jeho výběr do kontextu globálního výběru. Prostředí aktualizuje kontext globálního výběru s hodnotami z okna rámce, když je toto okno fokus. Při změně fokusu zločinců se stejně kontext výběru.  
  
## <a name="tracking-selection-in-the-ide"></a>Výběr sledování v integrovaném vývojovém prostředí  
 Rámeček okna nebo webu, vlastní rozhraní IDE má služby zvané <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Následující kroky ukazují, jak se změna ve výběru, způsobené uživateli změnit fokus na další otevřete okno nebo výběrem jiné položce v **Průzkumníka řešení**, je implementováno s cílem změnit obsah zobrazený v  **Vlastnosti** okna.  
  
1. Objekt vytvořený pomocí vašeho balíčku VSPackage, která je umístěna ve voláních vybrané okno <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> mít <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> vyvolat <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Zásobník pro výběr poskytované vybrané okno vytvoří vlastní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objektu. Když změny výběru sady VSPackage volá <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> upozornit všechny moduly pro naslouchání v prostředí, včetně **vlastnosti** okna změny. Poskytuje také přístup k informacím o hierarchii a položky související s nový výběr.  
  
3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a předají se jí položky vybrané hierarchie `VSHPROPID_BrowseObject` naplní parametr <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objektu.  
  
4. Objekt odvozený od [rozhraní IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) se vrátí <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> pro požadované položky a prostředí zabalí jej do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (viz následující krok). Pokud selže volání prostředí volá druhé `IVsHierarchy::GetProperty`, předají se jí zásobník pro výběr <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , zadejte hierarchie položky nebo položek.  
  
    Váš projekt se nevytvoří VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> vzhledem k tomu, že v okně prostředí poskytované VSPackage, která ho implementuje (například **Průzkumníka řešení**) vytvoří <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> svým jménem.  
  
5. Prostředí volá metody pro <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> získat objekty na základě `IDispatch` rozhraní vyplnit **vlastnosti** okna.  
  
   Když je hodnota v **vlastnosti** okno se změní, implementujte rozšíření VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` a `IVsTrackSelectionEx::OnSelectionChangeEx` informuje změna hodnoty prvku. Potom se vyvolá prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> nebo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> zachovat informace zobrazené v **vlastnosti** okno Synchronizovat s hodnotami vlastností. Další informace najdete v tématu [aktualizuje hodnoty vlastností v okně Vlastnosti](#updating-property-values-in-the-properties-window).  
  
   Kromě výběru jiné položky projektu v **Průzkumníka řešení** k zobrazení vlastností souvisejících s danou položku, můžete také zvolit jiný objekt z v rámci okna formuláře nebo dokumentu pomocí rozevíracího seznamu k dispozici na **Vlastnosti** okna. Další informace najdete v tématu [seznam objektů okna vlastnosti](../../extensibility/internals/properties-window-object-list.md).  
  
   Můžete změnit způsob zobrazením informací **vlastnosti** mřížky okna okno z abecedního do kategorií, a pokud je k dispozici, můžete otevřít stránku vlastnosti pro vybraný objekt také kliknutím na odpovídající tlačítko na  **Vlastnosti** okna. Další informace najdete v tématu [tlačítka okna vlastnosti](../../extensibility/internals/properties-window-buttons.md) a [stránky vlastností](../../extensibility/internals/property-pages.md).  
  
   Nakonec dolní části **vlastnosti** okno obsahuje také popis vybraném v poli **vlastnosti** mřížky okna okno. Další informace najdete v tématu [získávání popisy pole v okně Vlastnosti](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a> Aktualizuje hodnoty vlastností v okně Vlastnosti
Existují dva způsoby, jak zachovat **vlastnosti** okno, které jsou synchronizované s změně hodnoty vlastnosti. První je pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní, které poskytuje přístup k základní oddílová funkce, včetně přístupu k a vytvoření oken nástrojů a dokumentu poskytovaných prostředím. Následující kroky popisují proces synchronizace.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Aktualizuje hodnoty vlastností pomocí IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Chcete-li aktualizovat pomocí rozhraní IVsUIShell hodnoty vlastností  
  
1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby) kdykoli VSPackages, projekty, nebo editory musíte vytvořit nebo výčet nástroj nebo dokumentu.  
  
2.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zachovat **vlastnosti** okno, které jsou synchronizované s změny vlastností pro projekt (nebo vybraný objekt prochází se jím podle **vlastnosti** okno) bez implementace <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> MSMQEvent_Arrived; <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> události.  
  
3.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> k zahájení a zakázat, klientské oznámení událostí hierarchii bez nutnosti hierarchii k implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Aktualizuje se pomocí připojení IConnection hodnoty vlastností  
 Druhý způsob, jak uchovávat **vlastnosti** je okno, které jsou synchronizované s změně hodnoty vlastnosti k implementaci `IConnection` umožňující připojení k objektu k označení existenci odchozí rozhraní. Pokud chcete lokalizovat název vlastnosti, jsou odvozeny z objektu <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Implementace můžete upravit vlastnosti popisovače vrátí a změnit název vlastnosti. Chcete-li lokalizovat popis, vytvořit atribut, který je odvozen od <xref:System.ComponentModel.DescriptionAttribute> a přepsat vlastnost Popis.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Důležité informace při implementaci rozhraní připojení IConnection  
  
1.  `IConnection` poskytuje přístup k enumerátoru dílčí objekt se <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraní. Také poskytuje přístup ke všem připojení bodu dílčí objektům, každý z která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní.  
  
2.  Libovolný objekt procházet zodpovídá za implementace <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> událostí. **Vlastnosti** okno vás upozorní, události nastavený prostřednictvím `IConnection`.  
  
3.  Spojovací bod určuje, kolik připojení (jeden nebo více) povoluje v jeho provádění <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Spojovací bod, který umožňuje pouze jedno rozhraní můžou vrátit <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.  
  
4.  Klient může volat `IConnection` rozhraní se získat přístup k enumerátoru dílčí objekt se <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraní. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Rozhraní může být volána pro výčet spojovacích bodů pro každou odchozí ID rozhraní (IID).  
  
5.  `IConnection` Můžete také volat získat přístup k připojení bodu podřízených objektů s <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pro každou odchozí identifikátor IID rozhraní. Až <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní, klient spustí nebo ukončí advisory smyčky s umožňující připojení k objektu a klienta vlastní synchronizaci. Klient může také volat <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní získat objekt enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> rozhraní pro připojení, která ví o zobrazení výčtu.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> Získávání popisy pole z okna Vlastnosti
V dolní části **vlastnosti** okně oblasti popisu zobrazí informace související s vybranou vlastnost pole. Tato funkce je ve výchozím nastavení zapnutá. Pokud chcete skrýt pole Popis, klikněte pravým tlačítkem myši **vlastnosti** okno a klikněte na tlačítko **popis**. Tím také odstraněn znak zaškrtnutí vedle položky **popis** title v nabídce okno. Pole lze zobrazit znovu pomocí stejných kroků, chcete-li přepnout **popis** zpět na.  
  
 Informace v poli popisu pocházejí z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Každá metoda, rozhraní, coclass a tak dále může mít nelokalizované `helpstring` atribut v knihovně typů. **Vlastnosti** okno načte řetězec z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Chcete-li zadat řetězce lokalizované nápovědy  
  
1. Přidat `helpstringdll` atribut příkaz library v knihovně typů (`typelib`).  
  
   > [!NOTE]
   >  Tento krok je volitelný, pokud knihovna typů nachází v objektový soubor knihovny (.olb).  
  
2. Zadejte `helpstringcontext` atributy pro řetězce. Můžete také určit `helpstring` atributy.  
  
    Tyto atributy se liší od `helpfile` a `helpcontext` atributy, které jsou obsaženy ve skutečné chm témata nápovědy souboru.  
  
   Načíst informace o popisu, který se má zobrazit jako název zvýrazněný vlastnost **vlastnosti** volání okno <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pro vlastnost, která je vybrána, zadáte požadované `lcid` atribut pro výstupní řetězec. Interně <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> Vyhledá zadaný v souboru .dll `helpstringdll` atribut a volání `DLLGetDocumentation` na tento soubor .dll pomocí zadaného kontextu a `lcid` atribut.  
  
   Signatura a implementace `DLLGetDocumentation` jsou:  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` Funkce musí být definovaný v souboru .def knihovny DLL export.  
  
 Interně je vytvořen soubor olb, což je ve skutečnosti knihovny DLL. Tato knihovna DLL obsahuje jeden prostředek, souboru typu knihovna (.tlb) a jeden exportované funkce `DLLGetDocumentation`.  
  
 V případě .olb soubory `helpstringdll` atribut je volitelný, protože je stejný soubor, který obsahuje samotný soubor .tlb.  
  
 Chcete-li získat řetězců se zobrazí v **popisy** podokno, tedy minimální, je nutné provést je zadejte `helpstring` atribut v knihovně typů. Pokud chcete tyto řetězce lokalizaci, budete muset zadat `helpstringdll` (volitelné) atribut a `helpstringcontext` atribut (povinné) a implementujte `DLLGetDocumentation`.  
  
 Nejsou žádná další rozhraní, které je třeba k implementaci při získávání lokalizovaných informací prostřednictvím vaší idl `helpstringcontext` atribut a `DLLGetDocumentation`.  
  
 Jiný způsob, jak získat lokalizovaný název a popis vlastnosti je implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Další informace týkající se implementace této metody naleznete v tématu [vlastností pole a rozhraní okna](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)