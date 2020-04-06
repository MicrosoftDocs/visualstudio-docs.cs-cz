---
title: Rychlé informace ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705933"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Rychlé informace ve službě starší verze jazyka
Rychlé informace technologie IntelliSense zobrazují informace o identifikátoru ve zdroji, když uživatel buď umístí stříšku do identifikátoru, a vybere **rychlé informace** z nabídky **IntelliSense** nebo podrží kurzor myši nad identifikátorem. To způsobí, že tip nástroje se zobrazí s informacemi o identifikátoru. Tyto informace se obvykle skládají z typu identifikátoru. Pokud je ladicí modul aktivní, mohou tyto informace zahrnovat aktuální hodnotu. Ladicí modul dodává hodnoty výrazů , zatímco služba jazyka zpracovává pouze identifikátory.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete [v tématu Návod: Zobrazení popisů rychlých informací](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

 Třídy jazykových služeb rozhraní MPF (Managed Package Framework) poskytují plnou podporu pro zobrazení tipu nástroje Rychlé informace technologie IntelliSense. Jediné, co musíte udělat, je zadat text, který má být zobrazen a povolit funkci rychlých informací.

 Text, který má být zobrazen, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> je získán voláním analyzátoru <xref:Microsoft.VisualStudio.Package.ParseReason>metody s hodnotou důvodu analýzy . Tento důvod informuje analyzátor, aby získal informace o typu (nebo co je vhodné zobrazit v tipu nástroje <xref:Microsoft.VisualStudio.Package.ParseRequest> Rychlé informace) pro identifikátor v umístění určeném v objektu. Objekt <xref:Microsoft.VisualStudio.Package.ParseRequest> je co bylo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> předáno metodě.

 Analyzátor musí analyzovat vše až do pozice <xref:Microsoft.VisualStudio.Package.ParseRequest> v objektu, aby bylo možné určit typy všech identifikátorů. Potom analyzátor musí získat identifikátor v umístění požadavku analýzy. Nakonec analyzátor musí předat data tip nástroje přidružené k <xref:Microsoft.VisualStudio.Package.AuthoringScope> tomuto identifikátoru objektu <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> tak, aby objekt může vrátit text z metody.

## <a name="enabling-the-quick-info-feature"></a>Povolení funkce Rychlých informací
 Chcete-li povolit funkci Rychlé `CodeSense` informace, musíte nastavit a `QuickInfo` pojmenované parametry rozhraní <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Tyto atributy <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> nastavit <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> vlastnosti a.

## <a name="implementing-the-quick-info-feature"></a>Implementace funkce rychlých informací
 Třída <xref:Microsoft.VisualStudio.Package.ViewFilter> zpracovává operaci Rychlých informací technologie IntelliSense. Když <xref:Microsoft.VisualStudio.Package.ViewFilter> třída obdrží <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkaz, třída volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu s důvodem analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> a umístění stříšky v době, kdy byl <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkaz odeslán. Analyzátor <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody pak musí analyzovat zdroj až do daného umístění a potom analyzovat identifikátor v daném umístění, aby bylo možné určit, co se má zobrazit v tipu nástroje Rychlé informace.

 Většina analyzátorů provést počáteční analýzu celého zdrojového souboru a uložit výsledky ve stromu analýzy. Kompletní analýza se provádí, <xref:Microsoft.VisualStudio.Package.ParseReason> když <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> je předán a metoda. Jiné druhy analýzy pak můžete použít strom analýzy k získání požadovaných informací.

 Například hodnota důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> můžete najít identifikátor ve zdrojovém umístění a vyhledat ve stromu analýzy získat informace o typu. Tento typ informace je <xref:Microsoft.VisualStudio.Package.AuthoringScope> pak předán do třídy a je vrácena <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodou.
