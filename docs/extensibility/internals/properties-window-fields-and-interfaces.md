---
title: Pole a rozhraní okna vlastností | Microsoft Docs
description: Přečtěte si o výběru, který určuje, jaké informace se zobrazí v okno Vlastnosti na základě okna, které má fokus v integrovaném vývojovém prostředí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21bc3a7f1d46a1afe579a67afa09097fd04458ff
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875762"
---
# <a name="properties-window-fields-and-interfaces"></a>Pole a rozhraní okna Vlastnosti
Model pro výběr, který určuje, jaké informace se zobrazí v okně **vlastnosti** , je založen na okně, které se zaměřuje na integrované vývojové prostředí (IDE). Každé okno a objekt v rámci vybraného okna může mít svůj kontextový objekt výběru vložen do kontextu globálního výběru. Prostředí aktualizuje kontext globálního výběru hodnotami z rámce okna, když má toto okno fokus. V případě změny fokusu provede kontext výběru.

## <a name="tracking-selection-in-the-ide"></a>Sledování výběru v integrovaném vývojovém prostředí
 V rámci rámce okna nebo webu, který vlastní rozhraní IDE, je volána služba <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Následující kroky ukazují, jak se změna výběru vyvolala v případě, že uživatel změní fokus na jiné otevřené okno nebo když v **Průzkumník řešení** vyberete jinou položku projektu, je implementováno pro změnu obsahu zobrazeného v okně **vlastnosti** .

1. Objekt vytvořený rozhraním VSPackage, který je umístěn ve vybraném okně, volá volání metody <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Kontejner výběru poskytnutý vybraným oknem vytvoří svůj vlastní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objekt. Když se změní výběr, volání VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> upozorní na všechny posluchače v prostředí, včetně okna **vlastností** změny. Poskytuje také přístup k informacím o hierarchii a položkách, které souvisejí s novým výběrem.

3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a předání vybraným položkám hierarchie v `VSHPROPID_BrowseObject` parametru naplní <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objekt.

4. Pro __VSHPROPID je vrácen objekt odvozený od [rozhraní IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) [. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) pro požadovanou položku a prostředí je zabalí do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (viz následující krok). Pokud se volání nepovede, prostředí vytvoří druhé volání do `IVsHierarchy::GetProperty` a předá ho kontejneru výběru [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , že položka hierarchie nebo položky jsou dodávány.

    Váš projekt VSPackage se nevytvoří <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , protože rozhraní VSPackage v prostředí, které ho implementuje (například **Průzkumník řešení**), sestaví <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jeho jménem.

5. Prostředí vyvolá metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pro získání objektů na základě `IDispatch` rozhraní k vyplnění v okně **vlastnosti** .

   Když je změněna hodnota v okně **vlastnosti** , sady VSPackage implementují `IVsTrackSelectionEx::OnElementValueChangeEx` a, `IVsTrackSelectionEx::OnSelectionChangeEx` aby nahlásila změnu hodnoty elementu. Prostředí pak vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> nebo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> zachová informace zobrazené v okně **vlastnosti** synchronizované s hodnotami vlastností. Další informace naleznete v tématu [aktualizace hodnot vlastností v okně Vlastnosti](#updating-property-values-in-the-properties-window).

   Kromě výběru jiné položky projektu v **Průzkumník řešení** pro zobrazení vlastností souvisejících s touto položkou můžete také zvolit jiný objekt v rámci formuláře nebo okna dokumentu pomocí rozevíracího seznamu, který je k dispozici v okně **vlastnosti** . Další informace naleznete v části [seznam objektů okna vlastnosti](../../extensibility/internals/properties-window-object-list.md).

   Můžete změnit způsob zobrazení informací v mřížce okna **vlastnosti** z abecedy na kategorií a pokud je k dispozici, můžete také otevřít stránku vlastností pro vybraný objekt kliknutím na příslušná tlačítka v okně **vlastnosti** . Další informace najdete v tématu [tlačítka okna vlastnosti](../../extensibility/internals/properties-window-buttons.md) a [stránky vlastností](../../extensibility/internals/property-pages.md).

   Nakonec dolní část okna **vlastností** obsahuje také popis pole vybraného v mřížce okna **vlastnosti** . Další informace najdete v tématu [získání popisů polí z okna vlastnosti](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Aktualizace hodnot vlastností v okně Vlastnosti
Existují dva způsoby, jak udržovat okno **vlastností** synchronizované se změnami hodnoty vlastností. První je zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní, které poskytuje přístup k základním funkcím okna, včetně přístupu k a vytváření nástrojů a oken nástrojů a dokumentů poskytovaných prostředím. Následující kroky popisují tento proces synchronizace.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizace hodnot vlastností pomocí IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aktualizace hodnot vlastností pomocí rozhraní IVsUIShell

1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby), kdykoli, když VSPackage, projekty nebo editory potřebují vytvořit nebo vypsat okna nástrojů nebo dokumentů.

2. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pro zachování okna **vlastností** v synchronizaci se změnami vlastností projektu (nebo jakéhokoli jiného vybraného objektu, který je procházen pomocí okna **vlastností** ) bez implementace <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> a vyvolávání <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> událostí.

3. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> navažte a zakažte klientské upozornění na události v hierarchii bez nutnosti implementovat hierarchii <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .

### <a name="updating-property-values-using-iconnection"></a>Aktualizace hodnot vlastností pomocí IConnection
 Druhý způsob, jak zajistit, aby se okno **vlastnosti** synchronizoval se změnami hodnoty vlastností, je implementace `IConnection` na připojeném objektu pro označení existence odchozích rozhraní. Chcete-li lokalizovat název vlastnosti, odvodit objekt z <xref:System.ComponentModel.ICustomTypeDescriptor> . <xref:System.ComponentModel.ICustomTypeDescriptor>Implementace může upravit popisovače vlastností, které vrátí, a změnit název vlastnosti. Chcete-li lokalizovat popis, vytvořte atribut, který je odvozen z <xref:System.ComponentModel.DescriptionAttribute> a přepište vlastnost Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Pokyny k implementaci rozhraní IConnection

1. `IConnection` poskytuje přístup k dílčímu objektu enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraním. Poskytuje také přístup ke všem dílčím objektům spojovacího bodu, z nichž každý implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní.

2. Každý objekt pro procházení zodpovídá za implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> události. Okno **vlastnosti** poradí pro událost nastavenou prostřednictvím `IConnection` .

3. Bod připojení určuje, kolik připojení (jedna nebo více) umožňuje v rámci své implementace <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Bod připojení, který povoluje pouze jedno rozhraní, může vracet <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.

4. Klient může zavolat `IConnection` rozhraní a získat tak přístup k dílčímu objektu enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>Rozhraní lze potom volat pro zobrazení výčtu přípojných bodů pro každé ID odchozího rozhraní (IID).

5. `IConnection` lze také volat pro získání přístupu k podobjektům spojovacího bodu připojení k <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní pro každý odchozí identifikátor IID. Prostřednictvím <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní klient spustí nebo ukončí poradní smyčku s připojeným objektem a vlastní synchronizací klienta. Klient může také volat <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní a získat tak objekt enumerátoru s <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> rozhraním pro vytvoření výčtu připojení, o kterých ví.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Získání popisů polí z okna vlastností
V dolní části okna **vlastnosti** se v oblasti popis zobrazí informace související s vybraným polem vlastností. Tato funkce je ve výchozím nastavení zapnutá. Chcete-li skrýt pole Popis, klikněte pravým tlačítkem myši na okno **vlastnosti** a klikněte na položku **Popis**. Tím se také zruší zaškrtnutí vedle nadpisu **Popis** v okně nabídky. Toto pole můžete znovu zobrazit podle stejného postupu, abyste mohli **Popis** znovu zapnout.

 Informace v poli Popis pocházejí z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Každá metoda, rozhraní, třída typu coclass a podobně může mít nemístní `helpstring` atribut v knihovně typů. Okno **vlastnosti** načte řetězec z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Určení lokalizovaných řetězců v nápovědě

1. Přidejte `helpstringdll` atribut do příkazu Library v knihovně typů ( `typelib` ).

   > [!NOTE]
   > Tento krok je nepovinný, pokud se knihovna typů nachází v souboru knihovny objektů (. olb).

2. Zadejte `helpstringcontext` atributy pro řetězce. Můžete také zadat `helpstring` atributy.

    Tyto atributy jsou odlišné od `helpfile` atributů a `helpcontext` , které jsou obsaženy v tématech nápovědy k souboru skutečných souborů. chm.

   Chcete-li načíst informace o popisu, který má být zobrazen pro zvýrazněný název vlastnosti, okno **vlastností** vyvolá <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> vlastnost, která je vybrána, a určí požadovaný `lcid` atribut pro výstupní řetězec. Interně <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> nalezne soubor. dll zadaný v `helpstringdll` atributu a volání `DLLGetDocumentation` daného souboru. dll se zadaným kontextem a `lcid` atributem.

   Signatura a implementace nástroje `DLLGetDocumentation` jsou:

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

 `DLLGetDocumentation`Funkce musí být export definovaný v souboru. def pro knihovnu DLL.

 Interně se vytvoří soubor. olb, který je ve skutečnosti knihovnou DLL. Tato knihovna DLL obsahuje jeden prostředek, soubor knihovny typů (. tlb) a jednu exportovanou funkci `DLLGetDocumentation` .

 V případě souborů. olb `helpstringdll` je atribut volitelný, protože se jedná o stejný soubor, který obsahuje samotný soubor. tlb.

 Chcete-li získat řetězce, které se mají zobrazit v podokně **popisy** , tak minimum, které musíte udělat, je určit `helpstring` atribut v knihovně typů. Pokud chcete, aby byly tyto řetězce lokalizovány, je nutné zadat `helpstringdll` atribut (volitelné) a `helpstringcontext` atribut (Required) a implementovat `DLLGetDocumentation` .

 Neexistují žádná další rozhraní, která je nutné implementovat při získávání lokalizovaných informací prostřednictvím `helpstringcontext` atributu IDL a `DLLGetDocumentation` .

 Dalším způsobem získání lokalizovaného názvu a popisu vlastnosti je implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Další informace o implementaci této metody naleznete v části [pole a rozhraní okna vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Viz také

- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
