---
title: Rychlé informace ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132146"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Rychlé informace ve službě jazyk starší verze
Rychlé informace technologie IntelliSense zobrazí informace o identifikátor ve zdroji, když uživatel umístí znak v identifikátoru a vybere **rychlé informace** z **IntelliSense** nabídky nebo obsahuje myši kurzor přes identifikátor. To způsobí, že aby se s informacemi o identifikátor tip nástroj. Tyto informace se obvykle skládá z typu identifier. Pokud modul ladění je aktivní, mohou obsahovat tyto informace aktuální hodnotu. Modul ladění poskytuje hodnot výrazu, zatímco služba jazyka zpracovává jenom identifikátory.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace naleznete v tématu [návod: zobrazení popisů tlačítek QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
 Spravované balíček framework (MPF) jazyk služby třídy poskytují plnou podporu pro zobrazení rychlé informace technologie IntelliSense popis tlačítka. Všechny, které musíte udělat je, zadejte text, který se má zobrazit a povolit funkci Rychlé informace.  
  
 Text, který se zobrazí se získá voláním <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda analyzátor s hodnotou Důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason>. Z tohoto důvodu informuje analyzátor k získání informací o typu (nebo jakékoli je vhodné, který se má zobrazit v popisu tlačítka rychlé informace) pro identifikátor v umístění zadaném v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu. <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt je, co byl předán <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda.  
  
 Analyzátor musí analyzovat všechno až pozice v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu, aby bylo možné zjistit typy všechny identifikátory. Analyzátor, musíte získat identifikátor v žádosti o umístění analýzy. Nakonec analyzátor musí projít nástroj tip data související s Tento identifikátor <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu, tento objekt můžete vrátit text z <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metoda.  
  
## <a name="enabling-the-quick-info-feature"></a>Povolení funkce Rychlé informace  
 Chcete-li povolit funkci Rychlé informace, musíte nastavit `CodeSense` a `QuickInfo` pojmenované parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Nastavte tyto atributy <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> vlastnosti.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementace funkce Rychlé informace  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Třída zpracovává operaci rychlé informace technologie IntelliSense. Při <xref:Microsoft.VisualStudio.Package.ViewFilter> obdrží – třída <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkaz, třída volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda pomocí důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> a umístění služby pomocí kurzoru v době <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> byl odeslán příkaz. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda analyzátor musí pak analyzovat zdroji až do daného umístění a pak analyzovat identifikátor v daném umístění k určení toho, které chcete zobrazit v popisu tlačítka rychlé informace.  
  
 Většina analyzátory nezadávejte počáteční analýzy celý zdrojový soubor a uložit výsledek jako strom analýzy. Dokončení analýzy se provede při <xref:Microsoft.VisualStudio.Package.ParseReason> předaný <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda. Jiné druhy analýzy pak můžete použít strom analýzy získat požadované informace.  
  
 Například analýzy důvod hodnotu <xref:Microsoft.VisualStudio.Package.ParseReason> můžete najít identifikátor v umístění zdroje a vyhledat ve stromu analýzy k získání informací o typu. Tento typ informací jsou předána do <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy a vrátí <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metoda.