---
title: Vlastnosti Okenní pole a rozhraní | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706162"
---
# <a name="properties-window-fields-and-interfaces"></a>Pole a rozhraní okna Vlastnosti
Model pro výběr k určení, jaké informace se zobrazí v okně **Vlastnosti** je založena na okno, které má fokus v rozhraní IDE. Každé okno a objekt ve vybraném okně mohou mít objekt kontextu výběru posunutdo kontextu globálního výběru. Prostředí aktualizuje kontext globálního výběru hodnotami z okna, když má toto okno fokus. Když se změní fokus, tak se kontext výběru.

## <a name="tracking-selection-in-the-ide"></a>Sledování výběru v ide
 Rámec okna nebo web, vlastněný ide, má <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>službu s názvem . Následující kroky ukazují, jak je implementována změna výběru způsobená uživatelem, který buď změní fokus na jiné otevřené okno, nebo vybere jinou položku projektu v **Průzkumníku řešení**, pro změnu obsahu zobrazeného v okně **Vlastnosti.**

1. Objekt vytvořený vspackage, který je umístěn ve <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> vybraném <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>okně volání vyvolat .

2. Kontejner výběru, který poskytuje vybrané okno, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> vytvoří svůj vlastní objekt. Když se změní výběr, VSPackage volá <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> upozornit všechny posluchače v prostředí, včetně okna **Vlastnosti,** změny. Poskytuje také přístup k informacím o hierarchii a položce souvisejících s novým výběrem.

3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a předání vybraných položek `VSHPROPID_BrowseObject` hierarchie v <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> parametru naplní objekt.

4. Objekt odvozený z [rozhraní IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) je vrácen [a __VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) pro požadovanou položku a prostředí <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ji zabalí do (viz následující krok). Pokud volání selže, prostředí provede druhé `IVsHierarchy::GetProperty`volání , předání kontejneru výběru [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) které položka hierarchie nebo položky poskytují.

    Váš projekt VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nevytvoří, protože okno dodané prostředím VSPackage, který jej <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> implementuje (například **Průzkumník řešení**) vytvoří jeho jménem.

5. Prostředí vyvolá metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> získání objektů na základě `IDispatch` rozhraní k vyplnění okna **Vlastnosti.**

   Při změně hodnoty v okně **Vlastnosti** VSPackages implementovat `IVsTrackSelectionEx::OnElementValueChangeEx` a `IVsTrackSelectionEx::OnSelectionChangeEx` hlásit změnu na hodnotu prvku. Prostředí pak vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> nebo zachovat informace zobrazené v okně **Vlastnosti** synchronizovány s hodnotami vlastností. Další informace naleznete [v tématu Aktualizace hodnot vlastností v okně Vlastnosti](#updating-property-values-in-the-properties-window).

   Kromě výběru jiné položky projektu v **Průzkumníku řešení** pro zobrazení vlastností souvisejících s uvedenou položkou můžete také zvolit jiný objekt z okna formuláře nebo dokumentu pomocí rozevíracího seznamu dostupného v okně **Vlastnosti.** Další informace naleznete v [tématu Properties Window Object List](../../extensibility/internals/properties-window-object-list.md).

   Způsob zobrazení informací v **mřížce** okna Vlastnosti můžete změnit z abecední na kategorickou, a pokud je k dispozici, můžete také otevřít stránku vlastností vybraného objektu klepnutím na příslušná tlačítka v okně **Vlastnosti.** Další informace naleznete v [tématu Tlačítka oken vlastností a](../../extensibility/internals/properties-window-buttons.md) [Stránky vlastností](../../extensibility/internals/property-pages.md).

   Nakonec v dolní části okna **Vlastnosti** také obsahuje popis pole vybraného v mřížce okna **Vlastnosti.** Další informace naleznete v [tématu Získání popisů polí z okna Vlastnosti](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Aktualizace hodnot vlastností v okně Vlastnosti
Okno **Vlastnosti** lze synchronizovat se změnami hodnoty vlastnosti dvěma způsoby. Prvním z nich <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> je volání rozhraní, které poskytuje přístup k základním funkcím oken, včetně přístupu a vytváření oken nástrojů a dokumentů poskytovaných prostředím. Následující kroky popisují tento proces synchronizace.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizace hodnot vlastností pomocí prostředí IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aktualizace hodnot vlastností pomocí rozhraní IVsUIShell

1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby) kdykoli VSPackages, projekty nebo editory potřebují vytvořit nebo výčet nástrojů nebo oken dokumentů.

2. Implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zachovat **vlastnosti** okna v synchronizaci se změnami vlastností pro projekt (nebo jakýkoli <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> jiný vybraný objekt procházet okno **vlastnosti)** bez implementace a vypalování <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> událostí.

3. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> a zavést a zakázat, respektive klienta oznámení událostí <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>hierarchie bez nutnosti hierarchie k implementaci .

### <a name="updating-property-values-using-iconnection"></a>Aktualizace hodnot vlastností pomocí připojení IConnection
 Druhým způsobem, jak zachovat **vlastnosti** okna v synchronizaci se změnami hodnoty vlastností je implementovat `IConnection` na připojitelný objekt k označení existence odchozí rozhraní. Pokud chcete lokalizovat název vlastnosti, odvodit objekt z <xref:System.ComponentModel.ICustomTypeDescriptor>. Implementace <xref:System.ComponentModel.ICustomTypeDescriptor> můžete změnit popisovače vlastností, které vrátí a změnit název vlastnosti. Chcete-li lokalizovat popis, vytvořte <xref:System.ComponentModel.DescriptionAttribute> atribut, který je odvozen od vlastnosti Description a přepište ji.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Důležité informace o implementaci rozhraní IConnection

1. `IConnection`poskytuje přístup k podobjektu čítače s rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Poskytuje také přístup ke všem dílčím objektům spojovacího <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> bodu, z nichž každý implementuje rozhraní.

2. Každý objekt procházení je zodpovědný <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> za implementaci události. Okno **Vlastnosti** bude poskytovat poradenství `IConnection`pro událost nastavenou prostřednictvím .

3. Spojovací bod určuje, kolik připojení (jeden nebo více) <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>umožňuje v jeho implementaci . Spojovací bod, který umožňuje pouze <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jedno <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> rozhraní může vrátit z metody.

4. Klient může volat `IConnection` rozhraní získat přístup k podobjektu čítače s rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> pak může být voláno k výčetu spojovacích bodů pro každé ID odchozí rozhraní (IID).

5. `IConnection`lze také volat získat přístup k dílčím <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> objektům spojovacího bodu s rozhraním pro každé odchozí ID. Prostřednictvím <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní klient spustí nebo ukončí poradní smyčku s připojitelný objekt a vlastní synchronizaci klienta. Klient může také <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> volat rozhraní získat objekt enumerator s rozhraním <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> výčet připojení, které ví o.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Získání popisů polí z okna Vlastnosti
V dolní části okna **Vlastnosti** se v oblasti popisu zobrazí informace související s vybraným polem vlastností. Tato funkce je ve výchozím nastavení zapnutá. Pokud chcete pole popisu skrýt, klepněte pravým tlačítkem myši na okno **Vlastnosti** a klepněte na příkaz **Popis**. Tím také odeberete zaškrtnutí vedle názvu **popis** v okně nabídky. Pole můžete znovu zobrazit podle stejných kroků, abyste mohli **přepnout zpět na Popis.**

 Informace v poli popisu <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>pocházejí z . Každá metoda, rozhraní, coclass a tak dále `helpstring` může mít nelokalizovaný atribut v knihovně typů. Okno **Vlastnosti** načte <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>řetězec z aplikace .

### <a name="to-specify-localized-help-strings"></a>Určení lokalizovaných řetězců nápovědy

1. Přidejte `helpstringdll` atribut do příkazu knihovny`typelib`v knihovně typů ( ).

   > [!NOTE]
   > Tento krok je volitelný, pokud je knihovna typů v souboru knihovny objektů (.olb).

2. Zadejte `helpstringcontext` atributy pro řetězce. Můžete také `helpstring` zadat atributy.

    Tyto atributy se `helpfile` liší `helpcontext` od atributů a, které jsou obsaženy v tématech nápovědy k souboru CHM.

   Chcete-li načíst informace o popisu, které mají být <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> zobrazeny pro zvýrazněný název vlastnosti, zavolá okno `lcid` **Vlastnosti** vybranou vlastnost a určí požadovaný atribut pro výstupní řetězec. Interně <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> vyhledá soubor DLL zadaný `helpstringdll` v `DLLGetDocumentation` atributu a zavolá tento soubor `lcid` DLL se zadaným kontextem a atributem.

   Podpis a provádění `DLLGetDocumentation` jsou:

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

 Funkce `DLLGetDocumentation` musí být export definovaný v souboru .def pro dll.

 Interně je vytvořen soubor .olb, který je ve skutečnosti DLL. Tato knihovna DLL obsahuje jeden prostředek, soubor knihovny typů (.tlb) a jednu exportovnou funkci `DLLGetDocumentation`.

 V případě souborů OLB je `helpstringdll` atribut volitelný, protože se jedná o stejný soubor, který obsahuje samotný soubor .tlb.

 Chcete-li získat řetězce, které se zobrazí v podokně **Popisy,** `helpstring` je tedy nutné zadat atribut v knihovně typů. Pokud chcete, aby tyto řetězce byly lokalizovány, musíte `helpstringdll` zadat `helpstringcontext` (volitelný) atribut `DLLGetDocumentation`a (povinný) atribut a implementovat .

 Neexistují žádné další rozhraní, které je třeba implementovat při získávání `helpstringcontext` lokalizované informace prostřednictvím atributu idl a `DLLGetDocumentation`.

 Dalším způsobem získání lokalizovaného názvu a popisu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>vlastnosti je implementace . Další informace týkající se implementace této metody naleznete v [tématu Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Viz také

- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
