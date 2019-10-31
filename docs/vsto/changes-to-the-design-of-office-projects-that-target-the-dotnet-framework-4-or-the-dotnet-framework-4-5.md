---
title: Změny v návrhu projektů Office cílících na .NET Framework
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
ms.openlocfilehash: c46b0e7ea6cad5cb96117dedaa28ba6c4505a90b
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189644"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Změny v návrhu projektů Office cílených na .NET Framework 4 nebo .NET Framework 4,5
  Počínaje [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]sada Visual Studio představila nějaké změny v návrhu projektů Office cílených na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Pokud jste obeznámeni s projekty Office v předchozích verzích sady Visual Studio, měli byste si být vědomi těchto změn před vývojem projektů Office, které cílí na tyto verze .NET Framework 4,0 nebo novější. Ve výchozím nastavení všechny projekty, které vytvoříte pomocí Visual Studio 2013 nebo novější, cílí na .NET Framework 4,0 nebo novější.

 Následující části popisují tyto změny návrhu projektu Office.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Pochopení návrhu založeného na rozhraní sady Visual Studio 2010 Tools for Office runtime
 Při vývoji projektu Office, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou většina typů, které používáte v sadě Visual Studio 2010 Tools for Office runtime, rozhraní. Jedná se o zásadní změnu z předchozích verzí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], kde jsou tyto typy třídy. Například když cílíte na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, typy <xref:Microsoft.Office.Tools.Excel.Worksheet> a <xref:Microsoft.Office.Tools.Word.Document> jsou rozhraním namísto tříd. Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Pro všechny typy, které lze vytvořit přímo v předchozích verzích [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], nyní používáte metody objektu `Globals.Factory` k získání instancí těchto typů. Například chcete-li získat objekt, který implementuje rozhraní <xref:Microsoft.Office.Tools.Excel.SmartTag>, použijte metodu `Globals.Factory.CreateSmartTag`. Další informace naleznete v následujících tématech:

- [Aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizace přizpůsobení pásu karet v projektech Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aktualizace oblastí formulářů v projektech aplikace Outlook, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Nové základní třídy v projektech pro systém Office
 Nový návrh založený na rozhraních sady Visual Studio 2010 Tools for Office runtime má vliv na generované třídy v projektech pro systém Office, například `ThisDocument`, `ThisWorkbook`a `ThisAddIn`. V projektech pro systém Office, které cílí na .NET Framework 3,5 a předchozí verze rozhraní, jsou tyto generované třídy odvozeny ze tříd v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], jako je například `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet`a `Microsoft.Office.Tools.AddIn`. V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou nyní tyto [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] třídy rozhraní. Proto vygenerované třídy v projektech pro systém Office již nemohou z nich odvodit jejich implementaci. Namísto toho generované třídy jsou odvozeny z nových základních tříd, například <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>a <xref:Microsoft.Office.Tools.AddInBase>. Další informace najdete v článku [doplňky VSTO](../vsto/programming-vsto-add-ins.md) a [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 Základní třídy nejsou součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] distribuovatelné. Místo toho jsou definovány v sestaveních nástrojů, která jsou součástí sady Visual Studio. Tato sestavení jsou zkopírována do výstupní složky při sestavování projektů Office a musí být nasazena s vaším řešením. Další informace o sestaveních nástrojů naleznete v tématu [sestavení v modulu runtime Visual Studio Tools for Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Zásadní změny v projektech Office, které jsou zaměřeny na .NET Framework 4
 V následující tabulce je uveden seznam hlavních podstatných změn, se kterými se můžete setkat v projektech Office, jejichž cílem je [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Další podrobnosti najdete v tématu [migrace řešení pro systém Office do .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Zásadní změna|Následky|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute> se už v projektech Office nepoužívá ani se nepodporuje.|Tento atribut je nutné odebrat ze souboru kódu AssemblyInfo v projektech pro systém Office, které upgradujete ze sady Visual Studio 2008. Další informace najdete v tématu [požadované změny pro spouštění projektů Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|**ExcelLocale1033Attribute** se už nepoužívá nebo není podporovaný v projektech Excelu.|Tento atribut je nutné odebrat ze souboru kódu *AssemblyInfo* v projektech aplikace Excel. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Programovací model položek projektu **pásu karet (vizuální Návrhář)** se změnil.|Je nutné upravit soubor kódu na pozadí pro všechny položky pásu karet v projektu. Musíte také upravit jakýkoli kód, který vytvoří instanci ovládacích prvků pásu karet za běhu, zpracovává události pásu karet nebo nastavuje pozici komponenty pásu karet programově. Další informace najdete v tématu [aktualizace přizpůsobení pásu karet v projektech Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|Programovací model oblastí formuláře aplikace Outlook se změnil.|Je nutné upravit soubor kódu na pozadí pro jakékoli oblasti formuláře v projektu a jakýkoliv kód, který vytváří instance určitých tříd oblastí formuláře za běhu. Další informace najdete v tématu [aktualizace oblastí formulářů v projektech Outlooku, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Programovací model pro inteligentní značky v projektech aplikace Excel a Word se změnil. Inteligentní značky jsou v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]zastaralé.|Pokud vaše řešení používá inteligentní značky, při sestavování projektu dojde k chybám. Vzhledem k tomu, že inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], je nutné značky odebrat předtím, než budete moci otestovat a ladit řešení v [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] nebo novějším.|
|Syntaxe metod `GetVstoObject` a `HasVstoObject` se změnila.|K těmto metodám musíte předat `Globals.Factory` objekt, když k nim přistupujete v nativních objektech z primární spolupráce sestavení (PIA), nebo můžete získat přístup k těmto metodám objektu, který je vrácen vlastností `Globals.Factory` ve vašem projektu. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Události ovládacích prvků obsahu aplikace Word jsou přidruženy k novým delegátům.|Je nutné upravit jakýkoli kód, který zpracovává události ovládacích prvků obsahu aplikace Word, a určit tak nové delegáty. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Třídy `OLEObject` a `OLEControl` byly přejmenovány.|Je třeba upravit jakýkoli kód, který používá instance těchto tříd pro místo toho použití <xref:Microsoft.Office.Tools.Excel.ControlSite> nebo <xref:Microsoft.Office.Tools.Word.ControlSite> objektů. Další informace najdete v tématu [aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Třídy hostitelských položek, například `ThisWorkbook`, `Sheet`*n*, `ThisDocument`a `ThisAddIn`, již neposkytují `Dispose` metodu, kterou lze přepsat.|Je nutné přesunout jakýkoliv kód v metodě `Dispose` přepsání do obslužné rutiny události `Shutdown` ve třídě položky hostitele, například `ThisAddIn_Shutdown`, a odebrat přepsání metody `Dispose` z vaší třídy položky hostitele.|

## <a name="see-also"></a>Viz také:
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Co je nového ve vývoji pro Office](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
