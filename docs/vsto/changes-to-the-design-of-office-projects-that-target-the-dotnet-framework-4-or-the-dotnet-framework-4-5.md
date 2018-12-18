---
title: Změny v návrhu projektů Office cílených rozhraní .NET Framework
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b200c5b0df5f150e0d34b351a3e36a8a986f3ed6
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248241"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Změny v návrhu projektů Office cílených na rozhraní .NET Framework 4 nebo .NET Framework 4.5
  Počínaje [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio zavádí několik změn v návrhu projektů Office, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Pokud jste se seznámili s projekty sady Office v předchozích verzích sady Visual Studio, je třeba tyto změny předtím, než vývoj projektů Office cílených těchto verzí rozhraní .NET Framework 4.0 nebo novější. Ve výchozím nastavení cílit na všechny projekty, které vytvoříte pomocí sady Visual Studio 2013 nebo novější rozhraní .NET Framework 4.0 nebo novější.  
  
 Následující části popisují tyto změn v návrhu projektů Office.  
  
## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Pochopení návrhu na základě rozhraní sady Visual Studio 2010 Tools for Office runtime  
 Při vývoji projektu pro Office, který se zaměřuje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, většinu typů, které používáte ve Visual Studio 2010 Tools pro systém Office runtime jsou rozhraní. Toto je zásadní změny z předchozí verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], kde jsou tyto typy tříd. Například, pokud cílíte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, <xref:Microsoft.Office.Tools.Excel.Worksheet> a <xref:Microsoft.Office.Tools.Word.Document> typy budou rozhraním namísto třídy. Další informace najdete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Pro všechny typy, které může vytvořit instanci přímo v předchozích verzích [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], nyní použití metod pro posunutí `Globals.Factory` můžete získat instance těchto typů. Například, chcete-li získat objekt, který implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> rozhraní, použijte `Globals.Factory.CreateSmartTag` metody. Další informace naleznete v následujících tématech:  
  
-   [Aktualizace projektů Excel a Word, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizace vlastních nastavení pásu karet v projektech Office při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizace oblastí formulářů v projektech Outlook při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Nové základních tříd v projektech pro systém Office  
 Nový návrh na základě rozhraní sady Visual Studio 2010 Tools for Office runtime ovlivňuje vygenerovaných tříd v projektech Office, jako například `ThisDocument`, `ThisWorkbook`, a `ThisAddIn`. V projektech Office cílených rozhraní .NET Framework 3.5 a předchozími verzemi rozhraní framework, tyto vygenerované třídy jsou odvozeny z třídy v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] například `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet`, a `Microsoft.Office.Tools.AddIn`. V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, tyto [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] třídy jsou teď rozhraní. Proto vygenerovaných tříd v projektech pro systém Office již odvodit jejich provádění z nich. Místo toho generované třídy odvozovat nové základní třídy, jako <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>, a <xref:Microsoft.Office.Tools.AddInBase>. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md) a [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  
  
 Základní třídy, které nejsou součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistributable. Místo toho jsou definovány v sestaveních nástroje, které jsou součástí sady Visual Studio. Tato sestavení se zkopírují do výstupní složky při vytváření projektů pro systém Office a musí být nasazen v rámci řešení. Další informace o nástroje pro sestavení, naleznete v tématu [sestavení ve Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Rozbíjející změny v projektech Office, které se změnilo na rozhraní .NET Framework 4  
 Následující tabulka uvádí hlavní nejnovějších změn v projektech pro systém Office, které jsou změněn na cíl se můžete setkat [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Další podrobnosti najdete v tématu [řešení pro systém Office migrovat na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Zásadní změna|Důsledkem|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> Se už používá nebo podporované v projektech pro systém Office.|Tento atribut je nutné odebrat ze souboru AssemblyInfo kód v projektech pro systém Office, které upgradujete z aplikace Visual Studio 2008. Další informace najdete v tématu [požadované změny pro spouštění projektů Office migrovaných na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|**ExcelLocale1033Attribute** se už používá nebo podporované v projektech aplikace Excel.|Je třeba odebrat z tohoto atributu *AssemblyInfo* soubor kódu v projektech aplikace Excel. Další informace najdete v tématu [aktualizace Excelu a Wordu projekty, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Programovací model **pás karet (vizuální návrhář)** došlo ke změně položky projektu.|Je třeba upravit soubor kódu na pozadí pro všechny položky pásu karet v projektu. Také je třeba upravit jakýkoli kód, který vytvoří instanci ovládacích prvků pásu karet za běhu, zpracovává události pásu karet nebo nastaví pozici součásti pásu karet prostřednictvím kódu programu. Další informace najdete v tématu [přizpůsobení aktualizace pásu karet v projektech Office při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Programovací model oblastí formulářů aplikace Outlook byl změněn.|Je třeba upravit soubor kódu na pozadí pro všechny oblasti formuláře v projektu a veškerý kód, který vytvoří instanci určité třídy oblasti formuláře za běhu. Další informace najdete v tématu [aktualizace oblastí formulářů v projektech Outlook při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Programovací model pro inteligentní značky v projektech aplikace Excel a Word byl změněn. Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Pokud vaše řešení používá inteligentní značky, dojde k chybám při sestavení projektu. Protože inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], než budete moct testování a ladění řešení v je nutné odebrat značky [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] nebo novější.|  
|Syntaxe `GetVstoObject` a `HasVstoObject` došlo ke změně metody|Je nutné předat `Globals.Factory` těchto metod přístup na nativních objektů z primárních sestavení vzájemné spolupráce (PIA), nebo můžete přístup ke tyto metody pro objekt, který je vrácený objekt `Globals.Factory` vlastnosti ve vašem projektu. Další informace najdete v tématu [aktualizace Excelu a Wordu projekty, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Události ovládacích prvků obsahu aplikace Word jsou přidruženy k nové delegáty.|Je třeba upravit jakýkoli kód, který zpracovává události ovládacích prvků obsahu aplikace Word zadat nové delegáty. Další informace najdete v tématu [aktualizace Excelu a Wordu projekty, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|`OLEObject` a `OLEControl` přejmenovaná třídy.|Je třeba upravit jakýkoli kód, který používá instance těchto tříd pro použití <xref:Microsoft.Office.Tools.Excel.ControlSite> nebo <xref:Microsoft.Office.Tools.Word.ControlSite> objekty místo. Další informace najdete v tématu [aktualizace Excelu a Wordu projekty, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Hostování tříd položek, jako například `ThisWorkbook`, `Sheet` *n*, `ThisDocument`, a `ThisAddIn`, nadále poskytovat žádné `Dispose` metody, které můžete přepsat.|Jakýkoli kód, je nutné přesunout `Dispose` metody přepsání nastavení za účelem `Shutdown` obslužné rutiny události v hostiteli třída položky, například `ThisAddIn_Shutdown`a odeberte `Dispose` přepsat metodu z vaší třídy položku hostitele.|  
  
## <a name="see-also"></a>Viz také:  
 [Migrace řešení Office na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Co je nového ve vývoji Office](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  