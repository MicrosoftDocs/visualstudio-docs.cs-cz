---
title: Zobrazení mřížky vlastností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706192"
---
# <a name="properties-display-grid"></a>Mřížka zobrazení vlastností

Okno **Vlastnosti** zobrazuje pole v mřížce. Levý sloupec obsahuje názvy vlastností; pravý sloupec obsahuje hodnoty vlastností.

## <a name="work-with-the-grid"></a>Práce s mřížkou

Seznam dvou sloupců zobrazuje vlastnosti nezávislé na konfiguraci, které lze změnit v době návrhu a jejich aktuální nastavení. Všimněte si, že všechny vlastnosti nemusí být zobrazeny. Vlastnost může být nastavena jako skryté, například implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody. Konkrétně chcete skrýt vlastnosti, které mají podřízené vlastnosti:

1. Nastavte `pfDisplay` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> v `FALSE`.

2. Nastavte `pfHide` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> v `TRUE`.

Chcete-li nabízení informací do okna <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> **Vlastnosti,** používá rozhraní IDE . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>je volána VSPackages pro každé okno, které obsahuje volitelné objekty se souvisejícími vlastnostmi, které mají být zobrazeny v okně **Vlastnosti.** **Implementace** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> volání aplikace `GetProperty` Průzkumník řešení pomocí [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) v hierarchii projektu získat procházet objekty v hierarchii.

Pokud váš VSPackage nepodporuje [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)se ide pokusí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> použít hodnotu pro [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) které položka hierarchie nebo položky poskytují.

Projekt VSPackage není nutné <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> vytvořit, protože balíček okna dodané rozhraním IDE, který <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jej implementuje (například **Průzkumník řešení**) vytvoří jeho jménem.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>se skládá ze tří metod, které jsou volány IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>obsahuje počet objektů vybraných k zobrazení v okně **Vlastnosti.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>vrátí `IDispatch` objekty, které mají být zobrazeny v okně **Vlastnosti.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>umožňuje, aby byl některý z <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> vrácených objektů vybrán uživatelem. To umožňuje VSPackage vizuálně aktualizovat výběr zobrazený uživateli v uživatelském rozhraní.

Okno **Vlastnosti** extrahuje `IDispatch` informace z objektů k načtení vlastností, které procházejí. Prohlížeč Vlastnosti `IDispatch` používá k dotazování objektu, `ITypeInfo`jaké vlastnosti `IDispatch::GetTypeInfo`podporuje dotazem , který je získán z . Prohlížeč pak použije tyto hodnoty k naplnění okna **Vlastnosti** a ke změně hodnot pro jednotlivé vlastnosti zobrazené v mřížce. Informace o vlastnostech jsou udržovány v rámci samotného objektu.

Vzhledem k `IDispatch`tomu, že vrácené objekty podporují , může `IDispatch::Invoke` `ITypeInfo::Invoke` volající získat informace, jako je například název objektu, voláním nebo s předdefinovaným identifikátorem odeslání (DISPID), který představuje požadované informace. Deklarované identifikátory DISPID jsou záporné, aby se zajistilo, že nejsou v konfliktu s identifikátory definovanými uživatelem.

Okno **Vlastnosti** zobrazuje různé typy polí v závislosti na atributech určitých vlastností vybraného objektu. Tato pole zahrnují editační pole, rozevírací seznamy a odkazy na vlastní dialogová okna editoru.

- Hodnoty obsažené ve výčtovém seznamu jsou <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> načteny `IDispatch`dotazem do aplikace . Hodnoty získané ze seznamu výčtu lze změnit v mřížce vlastností poklepáním na název pole nebo klepnutím na hodnotu a výběrem nové hodnoty z rozevíracího seznamu. U vlastností, které mají předdefinovaná nastavení ze seznamu výčtu, poklepáním na název vlastnosti v seznamu Vlastnosti cyklicky prochází tečit dostupné volby. U předdefinovaných vlastností s pouze dvěma možnostmi, například true/false, poklepejte na název vlastnosti a přepnete mezi volbami.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`je , označující, že hodnota byla změněna, hodnota se zobrazí tučným písmem. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>se používá k určení, zda lze hodnotu obnovit na původní hodnotu. Pokud ano, můžete změnit zpět na výchozí kliknutím pravým tlačítkem myši na hodnotu a výběrem **možnosti Obnovit** ze zobrazené nabídky. V opačném případě budete muset změnit hodnotu zpět na výchozí ručně. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Také umožňuje lokalizovat a skrýt názvy vlastností zobrazených během návrhu, ale nemá vliv na názvy vlastností zobrazené za běhu.

- Kliknutím na tlačítko tři tečky (...) se zobrazí seznam hodnot vlastností, ze kterých může uživatel vybrat (například výběr barvy nebo seznam písem). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>tyto hodnoty.

## <a name="see-also"></a>Viz také

- [Rozšířit vlastnosti](../../extensibility/internals/extending-properties.md)
