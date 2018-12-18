---
title: 'Ukázka rozšíření Excel: Třída TechnologyManager | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: b23c3e735aba74d86b31afb4b83862d83bcd2bdb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190577"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Ukázka rozšíření aplikace Excel: třída TechnologyManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato třída rozšiřuje <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> třídy a je odpovědný za poskytnutí základních služeb pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] rozšíření. Přestože základní třídy obsahuje mnoho metod, pouze jen některé z nich se používá v této ukázce.  
  
 Některé metody pouze vrátí hodnotu vlastnosti. Mnoho metod jsou určeny k umožňuje vývojářům přepsat výchozí hodnotu, kterou algoritmy do modulu programového testu uživatelského rozhraní. Tyto metody vyvolání <xref:System.NotSupportedException> nebo vrátit `null`, který říká rozhraní framework používat výchozí algoritmus.  
  
 V závislosti na složitosti základní technologie vývoj kódu Správce technologie může celý proces trvat pár týdnů pár měsíců. Excel nabízí příležitost k vytvoření potenciálně velmi rozsáhlé technologie správce. Tento příklad je záměrně omezená na listech aplikace Excel a buňky a používá omezené formátování.  
  
 Pokud je to možné, kód Správce technologie používá vzdálené komunikace .NET kanál otevírány `Communicator` třídy extrahovat informace z doplňku spuštění v procesu Excelu.  
  
## <a name="com-visibility"></a>Viditelnost modelu COM.  
 Všimněte si, že tato třída a každý element třídy, které rozšiřují <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> třídy mají <xref:System.Runtime.InteropServices.ComVisibleAttribute> s hodnotou `true` k Ujistěte se, že třídy jsou viditelné v modelu COM.  
  
## <a name="technologyname-property"></a>Vlastnost TechnologyName  
 Toto přepsání <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> vlastnost musíte zadat jedinečný a smysluplný název, který identifikuje základní technologie pro všechny ostatní komponenty rozšíření. Pro toto rozšíření je hodnota "Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel – metoda  
 Toto přepsání <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> metoda vrátí číslo určující úroveň podpory, které může správce technologie nabízejí pro ovládací prvek reprezentovaný Zadaný popisovač. Další Správce technologie je vrácená hodnota vyšší, může podporovat ovládacího prvku. V tomto případě metoda zkontroluje okna obsahující ovládací prvek, a pokud je listu aplikace Excel, metoda vrátí nejvyšší hodnotu; v opačném případě vrátí nulové hodnoty, který označuje, že nenabízí žádnou podporu.  
  
## <a name="methods-to-get-an-element"></a>Metody k získání elementu  
 Existuje několik důležitých metod, které se používají rozhraní programového testování uživatelského rozhraní pro získání elementu specifické pro technologie tím, že poskytuje popisovač bodu na obrazovce nebo element z různých technologií. Kód pro tyto metody není potřeba vysvětlovat. Základní metody jsou následující:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId – metoda  
 Při vytvoření programového testu uživatelského rozhraní, může uživatel zadat hodnoty vlastností pro některé nebo všechny ovládací prvky v testu. Hodnoty těchto vlastností jsou testovací rozhraní používá k vytvoření dvojice název hodnota s názvem vlastnosti hledání, které se používají k vyhledání konkrétní ovládacích prvků uživatelského rozhraní během testu. Všechny vlastnosti hledání dohromady představují hodnoty <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> vlastnost člena každý prvek v technologii, která obsahuje každý ovládací prvek. Protože ovládací prvek může být nutné najít několikrát během testu, tato metoda poskytuje způsob, jak optimalizovat parsování vlastnosti hledání pro zadaný ovládací prvek Správce technologie. Tato metoda také vrátí hodnotu souboru cookie, který můžete použít rozhraní pro následné hledání pro ovládací prvek. Tato implementace metody používá <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metoda analyzovat vlastnosti hledání.  
  
## <a name="matchelement-method"></a>MatchElement – metoda  
 Můžete vyhledávat ovládací prvek správcem technologie, můžete implementovat <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> metoda vrátit pole z možných shod, nebo vyvolat <xref:System.NotSupportedException>, který říká rozhraní framework použití vlastního vyhledávacího algoritmu. V obou případech je nutné implementovat <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> metody, kde se používá tato implementace znovu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metoda.  
  
## <a name="navigation-methods"></a>Navigační metody  
 Tyto metody získat nadřazeného, podřízené položky nebo na stejné úrovni Zadaný prvek z hierarchie uživatelského rozhraní. Kód je jednoduchý a jasně komentářem.  
  
## <a name="getexcelelement-internal-method"></a>Interní metoda GetExcelElement  
 Tato interní metoda přebírá popisovač okna a informace o elementu s aplikace Excel a vrací požadovaný element aplikace Excel.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



