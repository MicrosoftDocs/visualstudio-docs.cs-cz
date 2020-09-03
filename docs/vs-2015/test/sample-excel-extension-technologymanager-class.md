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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672155"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Ukázka rozšíření aplikace Excel: třída TechnologyManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato třída rozšiřuje <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> třídu a zodpovídá za poskytování základních služeb pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] rozšíření. I když základní třída obsahuje mnoho metod, v této ukázce je použita pouze její podmnožina.

 Některé metody pouze vracejí hodnotu vlastnosti. Mnohé z těchto metod jsou určeny k tomu, aby vývojář mohl přepsat výchozí algoritmy sestavení do strojového testu uživatelského rozhraní. Tyto metody vyvolávají <xref:System.NotSupportedException> nebo vrátí hodnotu `null` , která instruuje rozhraní, aby používalo výchozí algoritmus.

 V závislosti na složitosti základní technologie může vývoj kódu technického manažera trvat několik týdnů až pár měsíců. Excel nabízí možnost vytvořit potenciálně velmi rozsáhlý manažer technologie. Tento příklad je záměrně omezený na listy aplikace Excel a buňky a používá omezené formátování.

 Pokud je to možné, kód manažera technologie používá kanál vzdálené komunikace .NET, který je otevřen `Communicator` třídou pro extrakci informací z doplňku spuštěného v aplikaci Excel.

## <a name="com-visibility"></a>Viditelnost modelu COM
 Všimněte si, že tato třída a každá třída elementů, které rozšiřuje <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> třídu, mají <xref:System.Runtime.InteropServices.ComVisibleAttribute> hodnotu s hodnotou, `true` aby bylo zajištěno, že třídy jsou viditelné pro model COM.

## <a name="technologyname-property"></a>Vlastnost Technology
 Toto přepsání <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> vlastnosti musí poskytovat jedinečný a smysluplný název, který identifikuje základní technologii pro všechny ostatní komponenty rozšíření. Pro toto rozšíření je hodnota "Excel".

## <a name="getcontrolsupportlevel-method"></a>Metoda GetControlSupportLevel
 Toto přepsání <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> metody vrátí číslo, které označuje úroveň podpory, kterou může správce technologie nabídnout pro ovládací prvek reprezentovaný poskytovaným popisovačem. Čím vyšší je vrácená hodnota, tím víc může správce technologie podporovat ovládací prvek. V tomto případě metoda zkontroluje okno, které obsahuje ovládací prvek, a pokud se jedná o excelový list, metoda vrátí nejvyšší hodnotu. v opačném případě vrátí hodnotu nula, což znamená, že žádná podpora není k dispozici.

## <a name="methods-to-get-an-element"></a>Metody pro získání elementu
 Existuje několik důležitých metod, které jsou používány rozhraním programového testování uživatelského rozhraní k získání prvku specifického pro technologii tím, že poskytují popisovač, bod na obrazovce nebo prvek z jiné technologie. Kód pro tyto metody je samozřejmý. Základní metody jsou následující:

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>

## <a name="parsequeryid-method"></a>Metoda ParseQueryId
 Když je vytvořen programový test uživatelského rozhraní, může uživatel zadat hodnoty vlastností pro některé nebo všechny ovládací prvky v testu. Tyto hodnoty vlastností používá testovací rozhraní k vytvoření dvojic název-hodnota označované jako vlastnosti hledání, které se používají k vyhledání specifických ovládacích prvků uživatelského rozhraní během testu. Všechny vlastnosti hledání společně reprezentují hodnotu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> vlastnosti každého prvku v technologii, která zahrnuje každý ovládací prvek. Vzhledem k tomu, že v průběhu testu může být nějaký ovládací prvek několikrát nalezen, poskytuje tato metoda správci technologický způsob, jak optimalizovat analýzu vlastností hledání daného ovládacího prvku. Tato metoda také vrátí soubor cookie, který může rozhraní použít pro následné hledání daného ovládacího prvku. Tato implementace metody používá <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metodu k analýze vlastností hledání.

## <a name="matchelement-method"></a>Metoda MatchElement
 Chcete-li provést vyhledávání ovládacího prvku nástrojem Technology Manager, můžete implementovat <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> metodu pro návrat pole možných shod, nebo vyvolat <xref:System.NotSupportedException> příkaz, který instruuje rozhraní pro použití vlastního vyhledávacího algoritmu. V obou případech je nutné implementovat <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> metodu, kde tato implementace znovu používá <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metodu.

## <a name="navigation-methods"></a>Navigační metody
 Tyto metody získají nadřazené, podřízené položky nebo na stejné úrovni poskytnutého elementu z hierarchie uživatelského rozhraní. Kód je jednoduchý a zjevně komentovaný.

## <a name="getexcelelement-internal-method"></a>Interní metoda GetExcelElement
 Tato interní metoda přebírá popisovač okna a informace o excelovém prvku a vrací požadovaný prvek aplikace Excel.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> <xref:System.NotSupportedException>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
