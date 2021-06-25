---
title: Pole a rozhraní okna Vlastnosti | Microsoft Docs
description: Přečtěte si o výběru, který určuje, které informace se zobrazí v okno Vlastnosti na základě okna, které se zaměřuje na Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a74e82480d1a4c71179c0e0b0671bac4ae97191
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899625"
---
# <a name="properties-window-fields-and-interfaces"></a>Pole a rozhraní okna Vlastnosti
Model pro výběr k určení, které informace se zobrazí v **okně Vlastnosti,** je založen na okně, které má fokus v integrovaném vývojovém prostředí( IDE). Každé okno a objekt ve vybraném okně mohou mít svůj objekt kontextu výběru odsunuté do globálního kontextu výběru. Když má toto okno fokus, prostředí aktualizuje kontext globálního výběru hodnotami z rámce okna. Když se fokus změní, změní se i kontext výběru.

## <a name="tracking-selection-in-the-ide"></a>Sledování výběru v integrovaném vývojovém prostředí
 Rámec okna nebo web, který vlastní integrované vývojové prostředí, má službu s názvem <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Následující kroky ukazují, jak se implementuje změna výběru způsobená změnou fokusu na jiné otevřené okno nebo výběrem jiné položky projektu v **Průzkumník řešení**, aby se změnil obsah zobrazený v **okně** Vlastnosti.

1. Objekt vytvořený vaším balíčekem VSPackage, který je v lokalitě vybraného okna, volá <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> metodu , která <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> vyvolala <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Kontejner výběru, který je poskytován vybraným oknem, vytvoří vlastní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objekt. Když se výběr změní, VSPackage zavolá, aby naslouchaly na změnu, včetně okna Vlastnosti, a oznámí tak všechny <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> naslouchací objekty v  prostředí. Poskytuje také přístup k informacím o hierarchii a položkách souvisejících s novým výběrem.

3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a předání vybraných položek hierarchie v `VSHPROPID_BrowseObject` parametru naplní objekt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

4. Objekt odvozený z [rozhraní IDispatch je](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) vrácen pro [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) požadované položky a prostředí ji zabalí do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (viz následující krok). Pokud volání selže, prostředí provede druhé volání metody , které mu předá kontejner `IVsHierarchy::GetProperty` výběru [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) kterou položka hierarchie nebo položky dodávají.

    Balíček VSPackage vašeho projektu se nevytváří, protože balíček VSPackage dodaného prostředím, který ho implementuje (například Průzkumník řešení ), jeho jménem <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> sestaví.

5. Prostředí vyvolá metody pro získání objektů na základě rozhraní pro <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `IDispatch` vyplnění **okna** Vlastnosti.

   Když se hodnota v **okně Vlastnosti** změní, implementují se balíčky VSPackages a pro nahlášení změny na `IVsTrackSelectionEx::OnElementValueChangeEx` hodnotu `IVsTrackSelectionEx::OnSelectionChangeEx` elementu. Prostředí pak vyvolá nebo , aby se informace zobrazené v okně Vlastnosti synchronizovaly <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> s hodnotami vlastností.  Další informace najdete v tématu [Aktualizace hodnot vlastností v okně Vlastnosti.](#updating-property-values-in-the-properties-window)

   Kromě výběru jiné položky projektu v nástroji **Průzkumník řešení** k zobrazení vlastností souvisejících s tuto položkou můžete také zvolit jiný objekt z okna formuláře nebo dokumentu pomocí rozevíracího seznamu, který je k dispozici v **okně** Vlastnosti. Další informace najdete v tématu [Seznam objektů okna vlastností.](../../extensibility/internals/properties-window-object-list.md)

   Způsob zobrazení informací v mřížce  okna Vlastnosti můžete změnit z abecedy na kategorický, a pokud je k dispozici, můžete také otevřít stránku vlastností pro vybraný objekt kliknutím na příslušná tlačítka v **okně** Vlastnosti. Další informace najdete v tématu [Tlačítka okna Vlastností](../../extensibility/internals/properties-window-buttons.md) a [Stránky vlastností](../../extensibility/internals/property-pages.md).

   Nakonec dolní část okna **Vlastnosti** obsahuje také popis pole vybraného v **mřížce okna** Vlastnosti. Další informace najdete v tématu [Získání popisů polí z okna Vlastnosti.](#getting-field-descriptions-from-the-properties-window)

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Aktualizace hodnot vlastností v okně Vlastnosti
Existují dva způsoby synchronizace okna **Vlastnosti** se změnami hodnot vlastností. Prvním je volání rozhraní, které poskytuje přístup k základním funkcím pro vytváření oken, včetně přístupu k oknu nástrojů a dokumentů poskytovaným prostředím a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> vytváření těchto oken. Následující kroky popisují tento proces synchronizace.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizace hodnot vlastností pomocí IVsuiShellu

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aktualizace hodnot vlastností pomocí rozhraní IVsUIShell

1. Volejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby) pokaždé, když balíčky VSPackage, projekty nebo editory potřebují vytvořit nebo vytvořit výčet oken nástrojů nebo dokumentů.

2. Implementujte pro synchronizaci okna Vlastnosti se změnami vlastností projektu (nebo jakéhokoli jiného vybraného objektu, který prochází okno Vlastnosti) bez implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> a   <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> aktivace událostí.

3. Implementujte metody a pro vytvoření a zakázání klientských oznámení událostí hierarchie bez nutnosti implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> hierarchii <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .

### <a name="updating-property-values-using-iconnection"></a>Aktualizace hodnot vlastností pomocí IConnection
 Druhým způsobem, jak udržovat okno **Vlastnosti** synchronizované se změnami hodnot vlastností, je implementovat u připojitelného objektu, aby se indikuje existence `IConnection` odchozích rozhraní. Pokud chcete název vlastnosti lokalizovat, odvodte objekt z <xref:System.ComponentModel.ICustomTypeDescriptor> . Implementace <xref:System.ComponentModel.ICustomTypeDescriptor> může upravit popisovače vlastností, které vrací, a změnit název vlastnosti. Pokud chcete popis lokalizovat, vytvořte atribut, který je odvozený z vlastnosti Description a <xref:System.ComponentModel.DescriptionAttribute> přepíše ji.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekty implementace rozhraní IConnection

1. `IConnection` poskytuje přístup k dílčímu objektu enumerátoru pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraní . Poskytuje také přístup ke všem dílčím objektům spojovacího bodu, z nichž každý implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní.

2. Za implementaci události zodpovídá každý objekt <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> procházení. Okno **Vlastnosti** bude radit s událostí nastavenou prostřednictvím `IConnection` .

3. Bod připojení určuje, kolik připojení (jedno nebo více) umožňuje při implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Z metody se může vrátit bod připojení, který umožňuje <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> pouze jedno <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> rozhraní.

4. Klient může volat rozhraní za účelem získání přístupu k dílčímu objektu `IConnection` enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraním. Rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> je pak možné volat k zobrazení výčtu bodů připojení pro každé ID odchozího rozhraní (IID).

5. `IConnection` Lze také volat za účelem získání přístupu k dílčím objektům spojovacího bodu s <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraním pro každé odchozí IID. Prostřednictvím rozhraní klient spustí nebo ukončí smyčku poradenství s připojitelným objektem <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> a vlastní synchronizací klienta. Klient může také volat rozhraní k získání objektu enumerátoru s rozhraním za účelem vytvoření výčtu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> připojení, o které ví.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Získání popisů polí z okna Vlastnosti
V dolní části okna **Vlastnosti** se v oblasti popisu zobrazují informace související s vybraným polem vlastnosti. Tato funkce je ve výchozím nastavení zapnutá. Pokud chcete pole popisu skrýt, klikněte pravým tlačítkem na **okno Vlastnosti** a klikněte na **Popis.** Tím se také v okně nabídky odebere značka zaškrtnutí vedle **názvu** Popis. Pole můžete znovu zobrazit pomocí stejných kroků a znovu **zapnout** popis.

 Informace v poli popis pochází z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Každá metoda, rozhraní, třída typu atd. může mít v knihovně typů nelokalizovaný `helpstring` atribut. Okno **Vlastnosti** načte řetězec z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Určení lokalizovaných řetězců nápovědy

1. Přidejte `helpstringdll` atribut do příkazu knihovny v knihovně typů ( `typelib` ).

   > [!NOTE]
   > Tento krok je volitelný, pokud je knihovna typů v souboru knihovny objektů (.olb).

2. Zadejte `helpstringcontext` atributy pro řetězce. Můžete také zadat `helpstring` atributy.

    Tyto atributy se liší od atributů a , které jsou obsaženy ve skutečných tématech nápovědy k souboru `helpfile` `helpcontext` .chm.

   Pokud chcete načíst informace o popisu, které  se zobrazí pro název zvýrazněné vlastnosti, volá okno Vlastnosti vybranou vlastnost a určí požadovaný atribut <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pro výstupní `lcid` řetězec. Interně vyhledá soubor .dll zadaný v atributu a zavolá na tento soubor .dll s zadaným kontextem a <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> `helpstringdll` `DLLGetDocumentation` `lcid` atributem.

   Podpis a implementace `DLLGetDocumentation` jsou:

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

 Funkce `DLLGetDocumentation` musí být exportem definovaným v souboru .def pro knihovnu DLL.

 Interně se vytvoří soubor .olb, což je ve skutečnosti knihovna DLL. Tato knihovna DLL obsahuje jeden prostředek, soubor knihovny typů (.tlb) a jednu exportované funkce `DLLGetDocumentation` .

 V případě souborů .olb je atribut volitelný, protože se jedná o stejný soubor, který obsahuje samotný soubor `helpstringdll` .tlb.

 Pokud chcete získat řetězce,  které se mají zobrazit v podokně Popisy, musíte proto v knihovně typů zadat `helpstring` atribut . Pokud chcete tyto řetězce lokalizovat, musíte zadat (volitelný) atribut a `helpstringdll` `helpstringcontext` atribut (povinné) a implementovat `DLLGetDocumentation` .

 Při získávání lokalizovaných informací prostřednictvím atributu idl a není potřeba implementovat žádná další `helpstringcontext` `DLLGetDocumentation` rozhraní.

 Dalším způsobem, jak získat lokalizovaný název a popis vlastnosti, je implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Další informace týkající se implementace této metody najdete v tématu Pole a rozhraní [okna vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Viz také

- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
