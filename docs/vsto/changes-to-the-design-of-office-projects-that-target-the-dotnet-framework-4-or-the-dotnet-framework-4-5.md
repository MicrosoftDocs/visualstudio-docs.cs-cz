---
title: Změny v návrhu projektů Office cílících na .NET Framework
description: Přečtěte si o změnách zavedených v sadě Visual Studio na návrh projektů Office, které cílí na .NET Framework 4 nebo novější.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 05f3662f1bc6379fa3401e98473971bcefc36ddd
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847855"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Změny v návrhu projektů Office cílených na .NET Framework 4 nebo .NET Framework 4,5
  Počínaje [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] verzí sada Visual Studio zavádí některé změny v návrhu projektů Office, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Pokud jste obeznámeni s projekty Office v předchozích verzích sady Visual Studio, měli byste si být vědomi těchto změn před vývojem projektů Office, které cílí na tyto verze .NET Framework 4,0 nebo novější. Ve výchozím nastavení všechny projekty, které vytvoříte pomocí Visual Studio 2013 nebo novější, cílí na .NET Framework 4,0 nebo novější.

 Následující části popisují tyto změny návrhu projektu Office.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Pochopení návrhu založeného na rozhraní sady Visual Studio 2010 Tools for Office runtime
 Při vývoji projektu Office, který se zaměřuje na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou většina typů, které používáte v sadě Visual Studio 2010 Tools for Office runtime, rozhraní. Jedná se o zásadní změnu z předchozích verzí nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , kde jsou tyto typy třídy. Například když cílíte na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> typy a jsou rozhraním namísto tříd. Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Pro všechny typy, které mohou být vytvořeny přímo v předchozích verzích nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , nyní použijte metody `Globals.Factory` objektu pro získání instancí těchto typů. Například chcete-li získat objekt, který implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> rozhraní, použijte `Globals.Factory.CreateSmartTag` metodu. Další informace najdete v následujících tématech:

- [Aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizace přizpůsobení pásu karet v projektech Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aktualizace oblastí formulářů v projektech aplikace Outlook, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Nové základní třídy v projektech pro systém Office
 Nový návrh založený na rozhraních sady Visual Studio 2010 Tools for Office runtime má vliv na generované třídy v projektech pro systém Office, například `ThisDocument` , `ThisWorkbook` a `ThisAddIn` . V projektech pro systém Office, které cílí na .NET Framework 3,5 a předchozí verze rozhraní, tyto generované třídy jsou odvozeny ze tříd v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] `Microsoft.Office.Tools.Word.Document` , například, `Microsoft.Office.Tools.Excel.Worksheet` a `Microsoft.Office.Tools.AddIn` . V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jsou nyní tyto třídy rozhraní. Proto vygenerované třídy v projektech pro systém Office již nemohou z nich odvodit jejich implementaci. Namísto toho generované třídy jsou odvozeny z nových základních tříd, jako například <xref:Microsoft.Office.Tools.Word.DocumentBase> , <xref:Microsoft.Office.Tools.Excel.WorksheetBase> a <xref:Microsoft.Office.Tools.AddInBase> . Další informace najdete v článku [doplňky VSTO](../vsto/programming-vsto-add-ins.md) a [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 Základní třídy nejsou součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuovatelného rozhraní. Místo toho jsou definovány v sestaveních nástrojů, která jsou součástí sady Visual Studio. Tato sestavení jsou zkopírována do výstupní složky při sestavování projektů Office a musí být nasazena s vaším řešením. Další informace o sestaveních nástrojů naleznete v tématu [sestavení v modulu runtime Visual Studio Tools for Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Zásadní změny v projektech Office, které jsou zaměřeny na .NET Framework 4
 V následující tabulce je uveden seznam hlavních podstatných změn, se kterými se můžete setkat v projektech Office, které jsou zaměřeny na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Další podrobnosti najdete v tématu [migrace řešení pro systém Office do .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Zásadní změna|Následky|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute>V projektech pro systém Office již není používán ani podporován.|Tento atribut je nutné odebrat ze souboru kódu AssemblyInfo v projektech pro systém Office, které upgradujete ze sady Visual Studio 2008. Další informace najdete v tématu [požadované změny pro spouštění projektů Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|**ExcelLocale1033Attribute** se už nepoužívá nebo není podporovaný v projektech Excelu.|Tento atribut je nutné odebrat ze souboru kódu *AssemblyInfo* v projektech aplikace Excel. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Programovací model položek projektu **pásu karet (vizuální Návrhář)** se změnil.|Je nutné upravit soubor kódu na pozadí pro všechny položky pásu karet v projektu. Musíte také upravit jakýkoli kód, který vytvoří instanci ovládacích prvků pásu karet za běhu, zpracovává události pásu karet nebo nastavuje pozici komponenty pásu karet programově. Další informace najdete v tématu [aktualizace přizpůsobení pásu karet v projektech Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|Programovací model oblastí formuláře aplikace Outlook se změnil.|Je nutné upravit soubor kódu na pozadí pro jakékoli oblasti formuláře v projektu a jakýkoliv kód, který vytváří instance určitých tříd oblastí formuláře za běhu. Další informace najdete v tématu [aktualizace oblastí formulářů v projektech Outlooku, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Programovací model pro inteligentní značky v projektech aplikace Excel a Word se změnil. Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] .|Pokud vaše řešení používá inteligentní značky, při sestavování projektu dojde k chybám. Vzhledem k tomu, že inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] , je nutné značky odebrat předtím, než budete moci testovat a ladit řešení v [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] nebo novějším.|
|Syntaxe `GetVstoObject` `HasVstoObject` metod a se změnila.|K těmto metodám musíte předat `Globals.Factory` objekt, když k nim přistupujete v nativních objektech z primární spolupráce sestavení (PIA), nebo můžete získat přístup k těmto metodám objektu, který je vrácen `Globals.Factory` vlastností v projektu. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Události ovládacích prvků obsahu aplikace Word jsou přidruženy k novým delegátům.|Je nutné upravit jakýkoli kód, který zpracovává události ovládacích prvků obsahu aplikace Word, a určit tak nové delegáty. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|`OLEObject`Třídy a `OLEControl` byly přejmenovány.|Je třeba upravit jakýkoli kód, který používá instance těchto tříd pro <xref:Microsoft.Office.Tools.Excel.ControlSite> <xref:Microsoft.Office.Tools.Word.ControlSite> místo toho použití nebo objektů. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Třídy hostitelských položek, například `ThisWorkbook` , `Sheet` *n*, `ThisDocument` a `ThisAddIn` , již neposkytují `Dispose` metodu, kterou lze přepsat.|Do `Dispose` `Shutdown` obslužné rutiny události v třídě položky hostitele musíte přesunout jakýkoliv kód v přepsání metody, například `ThisAddIn_Shutdown` a odebrat `Dispose` metodu override z vaší třídy položky hostitele.|

## <a name="see-also"></a>Viz také
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Co je nového ve vývoji pro Office](/previous-versions/86bkz018(v=vs.110))
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)