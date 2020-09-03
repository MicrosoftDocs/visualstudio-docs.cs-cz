---
title: Rozšíření editoru a jazykových služeb | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711717"
---
# <a name="extend-the-editor-and-language-services"></a>Rozšiřování editoru a jazykových služeb
Můžete přidat funkce jazykové služby (například IntelliSense) do vlastního editoru a zvětšit většinu funkcí editoru kódu sady Visual Studio.  Úplný seznam toho, co můžete rozšířit, najdete v tématu [jazykové služby a rozšiřovací body editoru](../extensibility/language-service-and-editor-extension-points.md).

 Většinu funkcí editoru rozšíříte pomocí Managed Extensibility Framework (MEF). Například pokud je funkce editoru, kterou chcete rozšiřuje, vybarvení syntaxe, můžete napsat *část komponenty* MEF definující klasifikace, pro které chcete vycházet z různých vybarvení a jak mají být zpracovány. Editor také podporuje více rozšíření stejné funkce.

 Prezentační vrstva editoru je založena na rozhraní WPF (Windows Presentation Framework). WPF poskytuje knihovnu grafiky pro flexibilní formátování textu a také poskytuje vizualizace, jako jsou grafiky a animace.

 Sada Visual Studio SDK poskytuje adaptéry označované jako *překrytí* , aby podporovaly sady VSPackage napsané pro starší verze. Nicméně pokud máte existující VSPackage, doporučujeme, abyste ho aktualizovali na novou technologii, abyste získali lepší výkon a spolehlivost.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Začínáme s rozšířeními služby jazyka a editoru](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Vysvětluje, jak vytvořit rozšíření pro Editor.|
|[Uvnitř editoru](../extensibility/inside-the-editor.md)|Popisuje obecnou strukturu editoru a uvádí některé z jeho funkcí.|
|[Managed Extensibility Framework v editoru](../extensibility/managed-extensibility-framework-in-the-editor.md)|Vysvětluje, jak použít Managed Extensibility Framework (MEF) s editorem.|
|[Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)|Zobrazí seznam rozšiřovacích bodů editoru. Body rozšíření reprezentují funkce editoru, které je možné rozšířit.|
|[Návod: vytvoření vylepšení zobrazení, příkazů a nastavení (vodítka sloupců)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Provede vás a vysvětluje sestavování příznaku zobrazení, které kreslí čáry vodítek sloupců, které vám pomůžou udržet kód na určitou šířku zobrazení.  Také ukazuje čtení a zápis nastavení a také deklarování a implementaci příkazů, které lze vyvolat z příkazového okna.|
|[Importy editoru](../extensibility/editor-imports.md)|Uvádí služby, které může rozšíření importovat.|
|[Přizpůsobení starší verze kódu editoru](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Popisuje různé způsoby, jak přizpůsobit starší kód (pre-Visual Studio 2010) pro rozšiřování editoru.|
|[Migrace služby starší verze jazyka](../extensibility/internals/migrating-a-legacy-language-service.md)|Vysvětluje, jak migrovat službu jazyka založenou na VSPackage.|
|[Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Ukazuje, jak propojit typ obsahu s příponou názvu souboru.|
|[Návod: vytvoření glyfu marže](../extensibility/walkthrough-creating-a-margin-glyph.md)|Ukazuje, jak přidat ikonu k okraji.|
|[Návod: zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)|Ukazuje, jak používat *značky* k zvýraznění textu.|
|[Návod: Přidání sbalení](../extensibility/walkthrough-outlining.md)|Ukazuje, jak přidat sbalení pro konkrétní druhy složených závorek.|
|[Návod: zobrazení vyhovujících složených závorek](../extensibility/walkthrough-displaying-matching-braces.md)|Ukazuje, jak zvýraznit párové závorky.|
|[Návod: zobrazení QuickInfoch popisků](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Ukazuje, jak zobrazit automaticky otevíraná okna QuickInfo, která popisují prvky kódu, jako jsou vlastnosti, metody a události.|
|[Návod: zobrazení podpisu – Help](../extensibility/walkthrough-displaying-signature-help.md)|Ukazuje, jak zobrazit automaticky otevíraná okna, která poskytují informace o počtu a typech parametrů v signatuře.|
|[Návod: dokončování příkazů zobrazení](../extensibility/walkthrough-displaying-statement-completion.md)|Ukazuje, jak implementovat dokončování příkazů.|
|[Návod: implementace fragmentů kódu](../extensibility/walkthrough-implementing-code-snippets.md)|Ukazuje, jak implementovat rozšíření fragment kódu.|
|[Návod: zobrazení návrhů žárovky](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Ukazuje, jak zobrazit žárovky pro návrhy kódu.|
|[Návod: použití příkazu shell s rozšířením editoru](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Ukazuje, jak přidružit příkaz nabídky ve VSPackage pomocí komponenty MEF.|
|[Návod: použití klávesových zkratek s rozšířením editoru](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Ukazuje, jak přidružit zástupce nabídky ve VSPackage s komponentou MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Poskytuje informace o Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Poskytuje informace o Windows Presentation Foundation (WPF).|

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
