---
title: Přehled okna vlastností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706035"
---
# <a name="properties-window-overview"></a>Přehled okna Vlastnosti
Okno **Vlastnosti** se používá k zobrazení vlastností objektů vybraných ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dvou hlavních typech oken dostupných v integrovaném vývojovém prostředí (IDE). Tyto dva typy oken jsou:

- Okna nástrojů, jako je Průzkumník řešení, zobrazení tříd a prohlížeč objektů

- Okna dokumentů obsahující takové editory a návrháře, jako je návrhář formulářů, editor XML a editor HTML

## <a name="using-the-properties-window"></a>Použití okna Vlastnosti
 Okno **Vlastnosti** zobrazuje vlastnosti jedné nebo více vybraných položek. Pokud je vybráno více položek, zobrazí se průsečík všech vlastností pro všechny vybrané objekty.

 Události související s vybraným objektem v okně návrhu formuláře nebo editoru HTML pomocí metadat modelu COM+ jsou zobrazeny v okně **Vlastnosti.** Můžete například vybrat tlačítko a zobrazit jeho přidružené `OnClick` události, například událost, kterou lze s tímto tlačítkem propojit.

 Události zobrazené v okně **Vlastnosti** se primárně používají s objekty, které jsou vázány na kód. Pokud upravujete formát souboru, který nemá nic společného s kódem, nebudete mít žádné události. Události jsou zobrazeny pouze v okně **Vlastnosti,** pokud je vazba mezi spuštěný kód a určité události spojené s určitými objekty. Příkladem může být kód za vybraný objekt, který se spustí při aktivaci tohoto objektu.

 V následující tabulce jsou uvedena primární rozhraní používaná v okně **Vlastnosti.**

|Název rozhraní|Popis|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Poskytuje seznam kategorií do okna **Vlastnosti** a mapuje každou vlastnost na kategorii.|
|[Rozhraní IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Zpřístupňuje metody a vlastnosti objektu programovacím nástrojům a dalším aplikacím, které podporují automatizaci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Poskytuje tři tečky (...) tlačítka s názvem *stavitelé,* které otevírají modální dialogová okna implementovaná samotným objektem. Používá se v případě, že uživatel do textového pole nelze snadno zadat hodnotu. Může být například použit k otevření výběru barev, který určuje hodnotu RGB pro vás.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Poskytuje přístup k objektům používaným k aktualizaci informací zobrazených v okně **Vlastnosti.** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>implementována vspackages pro každé okno, které obsahuje volitelné objekty se souvisejícími vlastnostmi, které mají být zobrazeny.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Obsahuje informace o typu objektu, například metody rozhraní a pole struktury.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umožňuje VSPackages přijímat oznámení o událostech výběru a načíst informace o aktuální hierarchii projektu, položka, hodnota prvku a příkaz uI kontextu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Poskytuje prostředí přístup k více výběrům.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Slouží k poskytnutí lokalizovaných názvů u některých vlastností zobrazených v okně **Vlastnosti.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Upozorní registrované VSPackages změny aktuální výběr, hodnota prvku nebo příkaz umítek o kontextu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Upozorní prostředí na změnu aktuálního výběru a poskytuje přístup k informacím o hierarchii a položce týkajících se nového výběru.|

 Další informace `IDispatch`o tématu naleznete v knihovně MSDN.

## <a name="see-also"></a>Viz také
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
- [Pole a rozhraní okna Vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md)
