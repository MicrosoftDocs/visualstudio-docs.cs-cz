---
title: Rozšíření pro Editor a jazykových služeb | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91eab151680d936c350c8c5745aec6c9fe86e47c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723067"
---
# <a name="extending-the-editor-and-language-services"></a>Rozšíření pro editor a služby jazyka
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete přidat funkce služby jazyka (například technologie IntelliSense) na vlastní editor a rozšíření většinu funkcí editoru kódu sady Visual Studio.  Úplný seznam co můžete rozšířit, naleznete v tématu [služba jazyka a editoru Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md).  
  
 Většina funkcí editoru rozšířit pomocí Managed Extensibility Framework (MEF). Například pokud chcete rozšířit funkce editoru je barevné zvýrazňování syntaxe, můžete napsat MEF *součást* , který definuje klasifikace, pro které chcete různé barvy a způsob jejich zpracování. Editor podporuje také několik rozšíření stejné funkce.  
  
 Prezentační vrstva editoru je založená Windows Presentation Framework (WPF). WPF obsahuje grafickou knihovnu pro flexibilní formátování textu a také poskytuje vizualizace, jako je například grafika a animace.  
  
 Visual Studio SDK poskytuje adaptérů, označované jako *překrytí* pro podporu rozšíření VSPackages napsaných pro starší verze. Nicméně pokud máte existující VSPackage, doporučujeme aktualizovat na novou technologii získat lepší výkon a spolehlivost.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Začínáme s rozšířeními pro služby jazyka a editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Vysvětluje, jak vytvořit rozšíření pro editor.|  
|[Práce v editoru](../extensibility/inside-the-editor.md)|Popisuje obecnou strukturu editoru a uvádí některé z jejích funkcí.|  
|[Managed Extensibility Framework v editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Vysvětluje, jak pomocí editoru služby Managed Extensibility Framework (MEF).|  
|[Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)|Zobrazí seznam Rozšiřovací body editoru. Body rozšíření představují funkce editoru, které je možné rozšířit.|  
|[Návod: Vytvoření grafického doplňku zobrazení, příkazů a nastavení (vodítka sloupců)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Provede a vysvětluje vytvoření grafického doplňku zobrazení, který vykreslí sloupec gudie řádky vám pomůže ochránit kód na určité šířky zobrazení.  Také ukazuje, čtení a zápis nastavení stejně jako deklarace a provádění příkazů, které můžete vyvolat z příkazového okna.|  
|[Importy do editoru](../extensibility/editor-imports.md)|Seznam služeb, které můžete importovat rozšíření.|  
|[Přizpůsobení zastaralého kódu editoru](../extensibility/adapting-legacy-code-to-the-editor.md)|Popisuje různé způsoby, jak přizpůsobit staršího kódu (předem Visual Studio 2010), rozšíření editoru.|  
|[Migrace služby starší verze jazyka](../extensibility/internals/migrating-a-legacy-language-service.md)|Vysvětluje, jak migrovat službu jazyka na základě balíčku VSPackage.|  
|[Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Ukazuje, jak propojit příponu názvu souboru typu obsahu.|  
|[Návod: Vytvoření okrajového piktogramu](../extensibility/walkthrough-creating-a-margin-glyph.md)|Ukazuje, jak přidat ikonu na okraj.|  
|[Návod: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)|Ukazuje, jak používat *značky* zvýraznění textu.|  
|[Návod: Sbalení](../extensibility/walkthrough-outlining.md)|Ukazuje, jak přidat sbalení pro konkrétní druhy složené závorky.|  
|[Návod: Zobrazení párových složených závorek](../extensibility/walkthrough-displaying-matching-braces.md)|Ukazuje, jak zvýraznění odpovídající složené závorky.|  
|[Návod: Zobrazení popisů tlačítek s rychlými informacemi](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Ukazuje, jak zobrazit rychlé informace překryvných ovládacích prvků, které popisují prvky kódu, jako jsou vlastnosti, metody a události.|  
|[Návod: Zobrazení vyhrazené nápovědy](../extensibility/walkthrough-displaying-signature-help.md)|Ukazuje, jak zobrazit překryvných ovládacích prvků, které poskytují informace o počtu a typů parametrů v signatuře.|  
|[Návod: Zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)|Ukazuje, jak implementovat dokončování příkazů.|  
|[Návod: Implementace fragmentů kódu](../extensibility/walkthrough-implementing-code-snippets.md)|Ukazuje, jak implementovat fragment kódu rozšíření.|  
|[Návod: Zobrazení návrhů v podobě žárovky](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Ukazuje, jak zobrazit návrhy pro návrhy kódu.|  
|[Návod: Použití příkazů prostředí s rozšířením editoru](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Ukazuje, jak přidružit příkazu nabídky v sadě VSPackage komponentu MEF.|  
|[Návod: Použití klávesové zkratky s rozšířením editoru](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Ukazuje, jak přidružit místní nabídky v sadě VSPackage komponentu MEF.|  
|[MEF (Managed Extensibility Framework)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Poskytuje informace o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Poskytuje informace o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Odkaz  
 Editor sady Visual Studio obsahuje následující obory názvů.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>

