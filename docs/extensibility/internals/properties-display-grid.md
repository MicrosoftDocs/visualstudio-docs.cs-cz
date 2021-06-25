---
title: Vlastnosti – zobrazení mřížky | Microsoft Docs
description: Zjistěte, kde se v mřížce v tabulce nacházejí názvy vlastností a hodnoty vlastností a okno Vlastnosti jak pracovat s mřížkou při rozšiřování vlastností.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee3d7d8d6277f9cfa0352cb4961644e4860b46bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899651"
---
# <a name="properties-display-grid"></a>Mřížka zobrazení vlastností

V **okně** Vlastnosti se zobrazují pole v mřížce. Levý sloupec obsahuje názvy vlastností. Pravý sloupec obsahuje hodnoty vlastností.

## <a name="work-with-the-grid"></a>Práce s mřížkou

Seznam se dvěma sloupci zobrazuje vlastnosti nezávislé na konfiguraci, které je možné změnit v době návrhu a jejich aktuální nastavení. Všimněte si, že se nemusí zobrazit všechny vlastnosti. Vlastnost lze nastavit jako skrytou, například implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody . Konkrétně pro skrytí vlastností, které mají podřízené vlastnosti:

1. Nastavte `pfDisplay` parametr v na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE` .

2. Nastavte `pfHide` parametr v na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE` .

K nabízení informací do **okna Vlastnosti** integrované vývojové prostředí používá <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je volána balíčky VSPackage pro každé okno, které obsahuje objekty s možností výběru se souvisejícími vlastnostmi, které se mají **zobrazit v okně** Vlastnosti. **Průzkumník řešení** implementace volání pomocí <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) v hierarchii projektu k získání procházetelných objektů v hierarchii.

Pokud váš balíček VSPackage nepodporuje [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)se integrované vývojové prostředí (IDE) pokusí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> použít hodnotu pro [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) kterou položka hierarchie nebo položky dodávají.

Váš projekt VSPackage nemusí vytvářet, protože balíček okna dodaného rozhraním IDE, který ho implementuje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (například **Průzkumník řešení**) vytváří jeho <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jménem.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se skládá ze tří metod, které jsou volány rozhraním IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> obsahuje počet objektů vybraných k zobrazení v **okně** Vlastnosti.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> vrací `IDispatch` objekty, které se mají zobrazit v **okně** Vlastnosti.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> umožňuje uživateli vybrat kterýkoli z objektů <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> vrácených uživatelem. To umožňuje sadě VSPackage vizuálně aktualizovat výběr zobrazený uživateli v uživatelském rozhraní.

Okno **Vlastnosti** extrahuje informace z `IDispatch` objektů, aby se načítaly procházené vlastnosti. Prohlížeč Vlastnosti se pomocí dotazu na objekt zeptá, jaké vlastnosti podporuje, a to dotazem `IDispatch` `ITypeInfo` získaným z `IDispatch::GetTypeInfo` . Prohlížeč pak tyto hodnoty použije k naplnění **okna Vlastnosti** a změně hodnot jednotlivých vlastností zobrazených v mřížce. Informace o vlastnostech se udržují v samotném objektu.

Vzhledem k tomu, že vrácené objekty podporují , volající může získat informace, jako je název objektu voláním nebo s předdefinovaným identifikátorem volání `IDispatch` `IDispatch::Invoke` (DISPID), který představuje `ITypeInfo::Invoke` požadované informace. Deklarované identifikátory DISPID jsou záporné, aby se zajistilo, že nebudou v konfliktu s identifikátory definovanými uživatelem.

V **okně** Vlastnosti se zobrazují různé typy polí v závislosti na atributech konkrétních vlastností vybraného objektu. Tato pole zahrnují textová pole, rozevírací seznamy a odkazy na dialogová okna vlastního editoru.

- Hodnoty obsažené ve výčtu seznamu se načítá <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> dotazem na `IDispatch` . Hodnoty získané z výčtového seznamu můžete změnit v mřížce vlastností poklikáním na název pole nebo kliknutím na hodnotu a výběrem nové hodnoty z rozevíracího seznamu. U vlastností, které mají předdefinovaná nastavení z výčtových seznamů, poklikáním na název vlastnosti v seznamu Vlastnosti projdete dostupnými volbami. U předdefinovaných vlastností, které mají jenom dvě volby, například true/false, poklikejte na název vlastnosti a přepněte mezi volbami.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> je hodnota , což `false` znamená, že hodnota byla změněna, zobrazí se tato hodnota tučně. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> se používá k určení, jestli je možné hodnotu obnovit na původní hodnotu. Pokud ano, můžete se vrátit k výchozímu nastavení tak, že na hodnotu kliknete pravým tlačítkem a v zobrazené nabídce zvolíte Resetovat.  V opačném případě je nutné ručně změnit hodnotu zpět na výchozí hodnotu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> také umožňuje lokalizovat a skrýt názvy vlastností zobrazených během návrhu, ale nemá vliv na názvy vlastností zobrazené za běhu.

- Kliknutím na tlačítko se třemi tečkami (...) se zobrazí seznam hodnot vlastností, ze kterých může uživatel vybrat (například výběr barvy nebo seznam písem). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> tyto hodnoty poskytuje.

## <a name="see-also"></a>Viz také

- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
