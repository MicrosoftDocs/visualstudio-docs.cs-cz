---
title: Rychlé informace ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc8bfff0903d2ed1554cfd8b3d5b1dcf5cf0fa8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64781986"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Rychlé informace ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rychlé informace technologie IntelliSense zobrazuje informace o identifikátoru ve zdroji, když uživatel umístí blikající kurzor do identifikátoru a vybere možnost **rychlé informace** z nabídky **technologie IntelliSense** nebo drží ukazatel myši nad identifikátorem. To způsobí zobrazení popisu tlačítka s informacemi o identifikátoru. Tyto informace se obvykle skládají z typu identifikátoru. Když je ladicí modul aktivní, můžou tyto informace obsahovat aktuální hodnotu. Modul ladění dodává hodnoty výrazu, zatímco služba jazyka zpracovává pouze identifikátory.  
  
 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [Návod: zobrazení popisů QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.  
  
 Třídy služby jazyka Managed Package Framework (MPF) poskytují plnou podporu pro zobrazení tipu rychlých informací o nástroji IntelliSense. Stačí, když zadáte text, který se má zobrazit, a povolíte funkci rychlá informace.  
  
 Text, který se má zobrazit, se získá voláním <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analyzátoru metody s hodnotou důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> . Tento důvod oznamuje analyzátoru, aby získal informace o typu (nebo cokoli, co je vhodné zobrazit v popisu nástroje rychlých informací) pro identifikátor v umístění zadaném v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu. <xref:Microsoft.VisualStudio.Package.ParseRequest>Objekt je co byl předán <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodě.  
  
 Analyzátor musí analyzovat vše až do pozice v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu, aby bylo možné určit typy všech identifikátorů. Analyzátor pak musí získat identifikátor v umístění žádosti o analýzu. Nakonec analyzátor musí předat data popisu nástroje přidruženého k tomuto identifikátoru <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu, aby objekt mohl vracet text z <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.  
  
## <a name="enabling-the-quick-info-feature"></a>Povolení funkce rychlé informace  
 Chcete-li povolit funkci rychlá informace, je nutné nastavit `CodeSense` a `QuickInfo` pojmenované parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Tyto atributy nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnosti a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> .  
  
## <a name="implementing-the-quick-info-feature"></a>Implementace funkce rychlé informace  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>Třída zpracovává rychlou informační operaci technologie IntelliSense. Když <xref:Microsoft.VisualStudio.Package.ViewFilter> třída obdrží <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkaz, třída volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu s důvodem analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> a umístěním blikajícího kurzoru v době <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> odeslání příkazu. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Analyzátor metody pak musí analyzovat zdroj až do daného umístění a potom analyzovat identifikátor v daném umístění, aby určil, co se má zobrazit v popisu nástroje rychlé informace.  
  
 Většina analyzátorů provede počáteční analýzu celého zdrojového souboru a výsledky uloží do stromu analýzy. Při předání do metody se provede kompletní analýza <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Jiné druhy analýz pak mohou pomocí stromu analýzy získat požadované informace.  
  
 Například hodnota důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> může najít identifikátor ve zdrojovém umístění a vyhledat jej ve stromové struktuře analýzy a získat informace o typu. Tyto informace o typu jsou poté předány <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídě a jsou vráceny <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodou.
