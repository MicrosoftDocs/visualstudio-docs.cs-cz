---
title: Rozšíření editoru a jazykových služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711717"
---
# <a name="extend-the-editor-and-language-services"></a>Rozšíření editoru a jazykových služeb
Do vlastního editoru můžete přidat funkce jazykových služeb (například IntelliSense) a rozšířit většinu funkcí editoru kódu sady Visual Studio.  Úplný seznam toho, co můžete rozšířit, naleznete [v tématu Jazyková služba a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md).

 Většinu funkcí editoru rozšiřujete pomocí rozhraní MEF spravované hojné funkce (MEF). Pokud je například funkce editoru, kterou chcete rozšířit, zbarvení syntaxe, můžete napsat *součást mef,* která definuje klasifikace, pro které chcete různé zbarvení a jak je chcete zpracovat. Editor také podporuje více rozšíření stejné funkce.

 Prezentační vrstva editoru je založena na rozhraní WPF (Windows Presentation Framework). WPF poskytuje grafickou knihovnu pro flexibilní formátování textu a také vizualizace, jako je grafika a animace.

 Sada Visual Studio SDK poskytuje adaptéry známé jako *překrytí* pro podporu balíčků VSPackages, které byly napsány pro starší verze. Nicméně pokud máte existující VSPackage, doporučujeme aktualizovat na novou technologii získat lepší výkon a spolehlivost.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Začínáme s jazykovými službami a rozšířeními editoru](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Vysvětluje, jak vytvořit rozšíření editoru.|
|[Uvnitř editoru](../extensibility/inside-the-editor.md)|Popisuje obecnou strukturu editoru a uvádí některé jeho funkce.|
|[Rozhraní Spravované rozšiřitelnosti v editoru](../extensibility/managed-extensibility-framework-in-the-editor.md)|Vysvětluje, jak používat spravované rozhraní pro rozšiřitelnost (MEF) s editorem.|
|[Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)|Zobrazí seznam rozšiřujících bodů editoru. Rozšiřující body představují funkce editoru, které lze rozšířit.|
|[Návod: Vytvoření vylepšení zobrazení, příkazů a nastavení (vodítka sloupců)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Prochází a vysvětluje vytváření vylepšení zobrazení, které kreslí čáry vodicích sloupců, které vám pomohou zachovat kód na určitou šířku zobrazení.  Také zobrazuje nastavení čtení a zápisu, stejně jako deklarování a implementaci příkazů, které můžete vyvolat z příkazového okna.|
|[Editor importy](../extensibility/editor-imports.md)|Uvádí služby, které může rozšíření importovat.|
|[Přizpůsobení staršího kódu editoru](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Vysvětluje různé způsoby, jak přizpůsobit starší kód (pre-Visual Studio 2010) rozšířit editor.|
|[Migrace služby staršího jazyka](../extensibility/internals/migrating-a-legacy-language-service.md)|Vysvětluje, jak migrovat jazykovou službu založenou na jazyce VSPackage.|
|[Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Ukazuje, jak propojit typ obsahu s příponou názvu souboru.|
|[Návod: Vytvoření symbolu okraje](../extensibility/walkthrough-creating-a-margin-glyph.md)|Ukazuje, jak přidat ikonu k okraji.|
|[Návod: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)|Ukazuje, jak používat *tagy* ke zvýraznění textu.|
|[Návod: Přidání osnovy](../extensibility/walkthrough-outlining.md)|Ukazuje, jak přidat osnovu pro určité druhy závorek.|
|[Návod: Zobrazení odpovídajících závorek](../extensibility/walkthrough-displaying-matching-braces.md)|Ukazuje, jak zvýraznit odpovídající závorky.|
|[Návod: Zobrazení popisů rychlých informací](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Ukazuje, jak zobrazit vyskakovací okna QuickInfo, které popisují prvky kódu, jako jsou vlastnosti, metody a události.|
|[Návod: Zobrazit nápovědu k podpisu](../extensibility/walkthrough-displaying-signature-help.md)|Ukazuje, jak zobrazit vyskakovací okno, které poskytují informace o počtu a typech parametrů v podpisu.|
|[Návod: Zobrazení dokončení příkazu](../extensibility/walkthrough-displaying-statement-completion.md)|Ukazuje, jak implementovat dokončení příkazu.|
|[Návod: Implementace fragmentů kódu](../extensibility/walkthrough-implementing-code-snippets.md)|Ukazuje, jak implementovat rozšíření fragmentu kódu.|
|[Návod: Zobrazení návrhů žárovek](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Ukazuje, jak zobrazit žárovky pro návrhy kódu.|
|[Návod: Použití příkazu prostředí s rozšířením editoru](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Ukazuje, jak přidružit příkaz nabídky v balíčku VSPackage s komponentou MEF.|
|[Návod: Použití klávesové zkratky s rozšířením editoru](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Ukazuje, jak přidružit zástupce nabídky v balíčku VSPackage s komponentou MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Obsahuje informace o rozhraní MEF spravované rozšiřitelnosti .|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Obsahuje informace o windows presentation foundation (WPF).|

## <a name="reference"></a>Referenční informace
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
