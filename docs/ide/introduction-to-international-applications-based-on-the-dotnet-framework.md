---
title: Představení mezinárodních aplikací založených na prostředí .NET Framework
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cd2a749bc96271e4ed16872f1d5c4a485c55900e
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863948"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Představení mezinárodních aplikací založených na prostředí .NET Framework

V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], existují dvě části vytváření globalizované aplikace: globalizace, proces návrhu aplikací, které se přizpůsobí různé jazykové verze a lokalizace, proces převodu prostředky pro konkrétní jazykovou verzi. Obecné informace o navrhování aplikací pro mezinárodní cílové skupiny, najdete v části [osvědčené postupy pro vývoj globalizovaných aplikací](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps).

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] – Model lokalizace se skládá z hlavní sestavení, která obsahuje kód aplikace a materiály záložního – řetězců, obrázků a dalších objektů pro jazyk, ve kterém je aplikace byl původně vyvinutý. Satelitní sestavení nebo sestavení, které obsahují lokalizované prostředky, bude mít každý lokalizované aplikace. Protože vždy hlavní sestavení obsahuje náhradní zdrojů, pokud se prostředek nenajde v lokalizovaná satelitní sestavení, <xref:System.Resources.ResourceManager> se pokusí načíst hierarchické způsobem, nakonec návrat k prostředku v hlavním sestavení. Záložní systém prostředků je vysvětleno podrobněji v [hierarchická organizace zdrojů pro lokalizaci](../ide/hierarchical-organization-of-resources-for-localization.md).

 Jeden prostředek lokalizace, měli byste zvážit použití je Glosář pro všechny Microsoft lokalizované produktů. Tento soubor CSV obsahuje více než 12 000 anglické podmínky a překlady podmínkami až 59 různých jazycích. Glosáře je k dispozici ke stažení [překlady terminologie Microsoftu](http://go.microsoft.com/fwlink/?LinkId=128146) webové stránky.

 Systém projektu pro aplikace Windows Forms může generovat soubory prostředků nouzové situaci a každý požadovaného další jazykové verze uživatelského rozhraní. Soubor prostředků pro použití náhradní lokality je integrovaná do hlavního sestavení a soubory prostředků specifické pro jazykovou verzi jsou pak integrované do satelitních sestavení, jeden pro jednotlivé jazykové verze uživatelského rozhraní. Při sestavování projektu se soubory prostředků jsou kompilovány z formátu XML pro Visual Studio (RESX) do zprostředkující binární formát (.resources), které jsou pak vložený do satelitních sestavení.

 Systém projektu pro Windows Forms a webové formuláře můžete pomocí šablony sestavení soubor prostředků soubory prostředků, přístup k prostředkům, ale taky popustit svůj projekt sestavit. Vytvoří se satelitní sestavení spolu s hlavním sestavením.

 Jakmile lokalizované aplikace spustí, její vzhled určené dvě hodnoty jazykovou verzi. (A *jazykovou verzi* je sada informací o uživatelských předvolbách týkající se jazyka uživatele, prostředí a kulturní konvence.) Nastavení jazykové verze uživatelského rozhraní určuje, které prostředky se načtou. Jazyková verze uživatelského rozhraní je nastaven jako `UICulture` v souborech Web.config a direktivy stránky, a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> v kódu jazyka Visual Basic nebo C#. Nastavení jazykové verze Určuje formátování hodnot například kalendářní data, čísla, měny a tak dále. Jazyková verze nastavena jako `Culture` v souborech Web.config a direktivy stránky <xref:System.Globalization.CultureInfo.CurrentCulture%2A> v kódu jazyka Visual Basic nebo C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Globalization>
- <xref:System.Resources>
- [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)
- [Zabezpečení a lokalizovaná satelitní sestavení](../ide/security-and-localized-satellite-assemblies.md)