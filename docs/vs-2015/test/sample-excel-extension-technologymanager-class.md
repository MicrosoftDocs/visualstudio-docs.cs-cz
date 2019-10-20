---
title: 'Ukázka rozšíření aplikace Excel: třída TechnologyManager | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac9a4517fcf13dbb0e1d7a6f994092168723e660
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672155"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Ukázka rozšíření aplikace Excel: třída TechnologyManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato třída rozšiřuje třídu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> a zodpovídá za poskytování základních služeb pro rozšíření [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. I když základní třída obsahuje mnoho metod, v této ukázce je použita pouze její podmnožina.

 Některé metody pouze vracejí hodnotu vlastnosti. Mnohé z těchto metod jsou určeny k tomu, aby vývojář mohl přepsat výchozí algoritmy sestavení do strojového testu uživatelského rozhraní. Tyto metody vyvolávají <xref:System.NotSupportedException> nebo vrátí `null`, který instruuje rozhraní, aby používalo výchozí algoritmus.

 V závislosti na složitosti základní technologie může vývoj kódu technického manažera trvat několik týdnů až pár měsíců. Excel nabízí možnost vytvořit potenciálně velmi rozsáhlý manažer technologie. Tento příklad je záměrně omezený na listy aplikace Excel a buňky a používá omezené formátování.

 Pokud je to možné, kód manažera technologie používá kanál vzdálené komunikace .NET, který je otevřen třídou `Communicator` k extrakci informací z doplňku spuštěného v aplikaci Excel.

## <a name="com-visibility"></a>Viditelnost modelu COM
 Všimněte si, že tato třída a každá třída elementů, které rozšiřuje <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> třídy, mají <xref:System.Runtime.InteropServices.ComVisibleAttribute> s hodnotou `true`, aby bylo zajištěno, že třídy jsou viditelné v modelu COM.

## <a name="technologyname-property"></a>Vlastnost Technology
 Toto přepsání vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> musí poskytovat jedinečný a smysluplný název, který identifikuje základní technologii pro všechny ostatní komponenty rozšíření. Pro toto rozšíření je hodnota "Excel".

## <a name="getcontrolsupportlevel-method"></a>Metoda GetControlSupportLevel
 Toto přepsání metody <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> vrátí číslo, které označuje úroveň podpory, kterou může správce technologie nabídnout pro ovládací prvek reprezentovaný poskytovaným popisovačem. Čím vyšší je vrácená hodnota, tím víc může správce technologie podporovat ovládací prvek. V tomto případě metoda zkontroluje okno, které obsahuje ovládací prvek, a pokud se jedná o excelový list, metoda vrátí nejvyšší hodnotu. v opačném případě vrátí hodnotu nula, což znamená, že žádná podpora není k dispozici.

## <a name="methods-to-get-an-element"></a>Metody pro získání elementu
 Existuje několik důležitých metod, které jsou používány rozhraním programového testování uživatelského rozhraní k získání prvku specifického pro technologii tím, že poskytují popisovač, bod na obrazovce nebo prvek z jiné technologie. Kód pro tyto metody je samozřejmý. Základní metody jsou následující:

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>

## <a name="parsequeryid-method"></a>Metoda ParseQueryId
 Když je vytvořen programový test uživatelského rozhraní, může uživatel zadat hodnoty vlastností pro některé nebo všechny ovládací prvky v testu. Tyto hodnoty vlastností používá testovací rozhraní k vytvoření dvojic název-hodnota označované jako vlastnosti hledání, které se používají k vyhledání specifických ovládacích prvků uživatelského rozhraní během testu. Všechny vlastnosti hledání společně reprezentují hodnotu vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> každého prvku v technologii, která zahrnuje všechny ovládací prvky. Vzhledem k tomu, že v průběhu testu může být nějaký ovládací prvek několikrát nalezen, poskytuje tato metoda správci technologický způsob, jak optimalizovat analýzu vlastností hledání daného ovládacího prvku. Tato metoda také vrátí soubor cookie, který může rozhraní použít pro následné hledání daného ovládacího prvku. Tato implementace metody používá metodu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> k analýze vlastností vyhledávání.

## <a name="matchelement-method"></a>Metoda MatchElement
 Chcete-li provést vyhledávání ovládacího prvku nástrojem Technology Manager, můžete implementovat metodu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> pro návrat pole možných shod nebo vyvolat <xref:System.NotSupportedException>, která instruuje rozhraní, aby používalo vlastní vyhledávací algoritmus. V obou případech je nutné implementovat metodu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>, kde tato implementace znovu používá metodu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.

## <a name="navigation-methods"></a>Navigační metody
 Tyto metody získají nadřazené, podřízené položky nebo na stejné úrovni poskytnutého elementu z hierarchie uživatelského rozhraní. Kód je jednoduchý a zjevně komentovaný.

## <a name="getexcelelement-internal-method"></a>Interní metoda GetExcelElement
 Tato interní metoda přebírá popisovač okna a informace o excelovém prvku a vrací požadovaný prvek aplikace Excel.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager><xref:System.NotSupportedException>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
