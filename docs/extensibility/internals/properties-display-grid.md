---
title: Zobrazení mřížky vlastností | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706192"
---
# <a name="properties-display-grid"></a>Zobrazit mřížku vlastností

V okně **vlastnosti** se zobrazí pole v mřížce. Levý sloupec obsahuje názvy vlastností; pravý sloupec obsahuje hodnoty vlastností.

## <a name="work-with-the-grid"></a>Práce s mřížkou

Seznam se dvěma sloupci zobrazuje vlastnosti nezávislé na konfiguraci, které je možné změnit v době návrhu a jejich aktuálním nastavení. Všimněte si, že se nemusí zobrazit všechny vlastnosti. Vlastnost může být nastavena jako skrytá, například implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody. Konkrétně pro skrytí vlastností, které mají podřízené vlastnosti:

1. Nastavte `pfDisplay` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> na `FALSE` .

2. Nastavte `pfHide` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> na `TRUE` .

Chcete-li odeslat informace do okna **vlastnosti** , rozhraní IDE používá <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je volána rozhraními VSPackage pro každé okno, které obsahuje objekty, které lze vybrat, aby se zobrazily v okně **vlastnosti** . **Průzkumník řešení**implementace <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> volání `GetProperty` pomocí [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) v hierarchii projektu získat objekty, které lze procházet v hierarchii.

Pokud VSPackage nepodporuje [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)se IDE pokusí použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> hodnotu [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , že položka hierarchie nebo položky jsou dodávány.

Váš projekt VSPackage není nutné vytvářet <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , protože balíček Window dodaný rozhraním IDE, který ho implementuje (například **Průzkumník řešení**), se vytváří za <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jeho jménem.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se skládá ze tří metod, které jsou volány rozhraním IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> obsahuje počet objektů vybraných pro zobrazení v okně **vlastnosti** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Vrátí `IDispatch` objekty, které jsou vybrány pro zobrazení v okně **vlastnosti** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> umožňuje uživateli vybrat kterýkoli z objektů vrácených <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> uživatelem. To umožňuje VSPackage vizuálně aktualizovat výběr zobrazený uživateli v uživatelském rozhraní.

Okno **vlastnosti** extrahuje informace z `IDispatch` objektů a načte procházené vlastnosti. Prohlížeč vlastností používá `IDispatch` k vyžádání objektu, které vlastnosti podporuje dotazování `ITypeInfo` , které se získá z `IDispatch::GetTypeInfo` . Prohlížeč pak pomocí těchto hodnot naplní okno **vlastnosti** a změní hodnoty pro jednotlivé vlastnosti zobrazené v mřížce. Informace o vlastnostech jsou uchovávány v rámci samotného objektu.

Vzhledem k tomu, že vrácené objekty podporují `IDispatch` , volající může získat informace, jako je název objektu, voláním `IDispatch::Invoke` nebo `ITypeInfo::Invoke` s předdefinovaným identifikátorem odeslání (DISPID), který představuje požadované informace. Deklarované identifikátory DISPID jsou záporné, aby nedošlo ke konfliktu s uživatelsky definovanými identifikátory.

V okně **vlastnosti** se zobrazí různé typy polí v závislosti na atributech specifických vlastností vybraného objektu. Mezi tato pole patří pole pro úpravy, rozevírací seznamy a odkazy na dialogová okna vlastního editoru.

- Hodnoty obsažené v seznamu výčtu jsou načteny <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> dotazem na `IDispatch` . Hodnoty získané z výčtového seznamu lze změnit v mřížce vlastností dvojitým kliknutím na název pole nebo kliknutím na hodnotu a výběrem nové hodnoty z rozevíracího seznamu. V případě vlastností, které mají předdefinované nastavení z výčtu seznamů, dvakrát klikněte na název vlastnosti v seznamu vlastnosti cyklicky dostupné možnosti. U předdefinovaných vlastností, které mají jenom dvě volby, jako je true nebo false, poklikejte na název vlastnosti, který chcete přepínat mezi volbami.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> je `false` , označuje, že hodnota byla změněna, hodnota je zobrazena tučným textem. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> slouží k určení, zda lze hodnotu obnovit na původní hodnotu. Pokud ano, můžete změnit výchozí nastavení tak, že kliknete pravým tlačítkem na hodnotu a v zobrazené nabídce kliknete na **obnovit** . V opačném případě je nutné změnit hodnotu zpět na výchozí hodnotu ručně. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> také umožňuje lokalizovat a skrývat názvy vlastností zobrazených během doby návrhu, ale nemá vliv na názvy vlastností zobrazené během běhu.

- Kliknutím na tlačítko se třemi tečkami (...) se zobrazí seznam hodnot vlastností, ze kterých může uživatel vybrat (například výběr barvy nebo seznam písem). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> poskytuje tyto hodnoty.

## <a name="see-also"></a>Viz také

- [Rozšířené vlastnosti](../../extensibility/internals/extending-properties.md)
