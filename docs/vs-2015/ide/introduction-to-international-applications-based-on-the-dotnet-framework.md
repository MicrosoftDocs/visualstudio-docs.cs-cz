---
title: Seznámení s mezinárodními aplikacemi na základě .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8243b2f735fb15f5c4e2fe841721696b87590997
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670439"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Představení mezinárodních aplikací založených na prostředí .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou k dispozici dvě části pro vytvoření špičkové aplikace: globalizace, proces navrhování aplikací, které mohou být přizpůsobeny různým kulturám a lokalizaci, proces překladu prostředků pro konkrétní jazykovou verzi. Obecné informace o navrhování aplikací pro mezinárodní cílovou skupinu najdete v tématu [osvědčené postupy pro vývoj aplikací připravených](https://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c)pro použití ve světě.

 Model lokalizace [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sestává z hlavního sestavení, které obsahuje kód aplikace a záložní prostředky – řetězce, obrázky a další objekty pro jazyk, ve kterém se aplikace původně vyvinula. Každá lokalizovaná aplikace bude mít satelitní sestavení nebo sestavení, která obsahují pouze lokalizované prostředky. Vzhledem k tomu, že hlavní sestavení vždy obsahuje záložní prostředky, pokud prostředek nebyl nalezen v lokalizovaném satelitním sestavení, <xref:System.Resources.ResourceManager> se pokusí ho načíst hierarchicky způsobem, a nakonec vrátit se k prostředku v hlavním sestavení. Záložní systém prostředků je podrobněji vysvětlen v [hierarchické organizaci prostředků k lokalizaci](../ide/hierarchical-organization-of-resources-for-localization.md).

 Jedním z prostředků lokalizace, které byste měli zvážit, je Glosář všech lokalizovaných produktů společnosti Microsoft. Tento soubor CSV obsahuje více než 12 000 anglických podmínek a překlady podmínek až do 59 různých jazyků. Glosář je k dispozici ke stažení na webové stránce [překlady terminologie společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=128146) .

 Projektový systém pro model Windows Forms aplikace může generovat soubory prostředků pro záložní i každou požadovanou jazykovou verzi uživatelského rozhraní. Záložní soubor prostředků je integrován do hlavního sestavení a soubory prostředků specifické pro jazykovou verzi jsou pak integrovány do satelitních sestavení, jeden pro každou jazykovou verzi uživatelského rozhraní. Při sestavování projektu jsou soubory prostředků kompilovány z formátu XML sady Visual Studio (. resx) do mezilehlého binárního formátu (. Resources), které jsou poté vloženy do satelitních sestavení.

 Projektový systém pro model Windows Forms i webové formuláře umožňuje vytvářet soubory prostředků pomocí šablony souboru prostředků sestavení, přístupu k prostředkům a sestavení projektu. Satelitní sestavení budou vytvořena společně s hlavním sestavením.

 Když se spustí lokalizovaná aplikace, její vzhled je určen dvěma hodnotami kultury. ( *Jazyková verze* je sada informací o uživatelských preferencích souvisejících s jazykem, prostředím a kulturním konvencím uživatele.) Nastavení jazykové verze uživatelského rozhraní určuje, které prostředky budou načteny. Jazyková verze uživatelského rozhraní je nastavena jako `UICulture` v souborech Web. config a direktivách stránky a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> v kódu Visual Basic C# nebo vizuálu. Nastavení jazykové verze určuje formátování hodnot, jako jsou data, čísla, měna a tak dále. Jazyková verze je nastavena jako `Culture` v souborech Web. config a direktivách stránky <xref:System.Globalization.CultureInfo.CurrentCulture%2A> v kódu Visual Basic nebo C# vizuálu.

## <a name="see-also"></a>Viz také
 <xref:System.Globalization><xref:System.Resources>
 [Globalizace a lokalizace zabezpečení aplikací](../ide/globalizing-and-localizing-applications.md) [a lokalizovaných satelitních sestavení](../ide/security-and-localized-satellite-assemblies.md)
