---
title: Sestavení v modulu runtime Visual Studio Tools for Office
description: Přečtěte si, že Visual Studio automaticky přidá odkazy na sestavení modulu runtime Visual Studio Tools for Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86c3c2b77b6bbea1e609bbea092b44bd1dee1dd4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848295"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Sestavení v modulu runtime Visual Studio Tools for Office
  Při vytváření projektu sady Office sada Visual Studio automaticky přidá odkazy na [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] sestavení, která jsou použita pro typ projektu a cílovou .NET Framework projektu. Existují různá sestavení v rozšířeních sady Office pro .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a [!INCLUDE[net_v45](includes/net-v45-md.md)] . Další informace o rozšířeních Office najdete v tématu [Visual Studio Tools for Office runtime – přehled](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Sestavení v rozšířeních sady Office pro .NET Framework 4 a [!INCLUDE[net_v45](includes/net-v45-md.md)]
 Následující tabulka uvádí sestavení, která jsou obsažena v rozšířeních sady Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a [!INCLUDE[net_v45](includes/net-v45-md.md)] . Dokumentaci k oborům názvů a typům v těchto sestaveních naleznete v tématu [Managed reference &#40;vývoj pro Office v sadě Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Název sestavení|Popis|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Poskytuje následující typy:<br /><br /> -Typy pro vytváření přizpůsobení pásu karet a inteligentních značek. **Poznámka:**      Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Typy pro vytváření podoken akcí v přizpůsobení na úrovni dokumentu a vlastních podoknech úloh v Doplňkech VSTO.|
|Microsoft.Office.Tools.Excel.dll|Poskytuje rozhraní, která představují hostitelské položky a hostitelské ovládací prvky pro excelové projekty a podpůrné typy. Další informace najdete v tématu [Automatizace Excelu pomocí rozšířených objektů](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Poskytuje typy, které můžete použít k vytvoření vlastních oblastí formulářů v doplňkových doplňcích pro Outlook VSTO.|
|Microsoft.Office.Tools.Word.dll|Poskytuje rozhraní, která představují hostitelské položky a hostitelské ovládací prvky pro projekty aplikace Word a podpůrné typy. Další informace najdete v tématu [Automatizace Wordu pomocí rozšířených objektů](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Poskytuje následující typy:<br /><br /> -Výjimky, které mohou být vyvolány modulem runtime Visual Studio Tools for Office.<br />– Atributy, které lze použít při vytváření oblastí formulářů aplikace Outlook.|
|Microsoft.Office.Tools.dll|Poskytuje typy, které jsou součástí běhové infrastruktury Visual Studio Tools for Office a nejsou určeny pro použití přímo v kódu.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atribut a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> rozhraní, které lze použít pro ukládání datových objektů do mezipaměti v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [cache data](caching-data.md).<br />– <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Rozhraní, které lze implementovat pro spuštění dalších kroků instalace, jako poslední krok instalačního programu ClickOnce pro řešení Office. Další informace najdete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />-Výjimky, které mohou být vyvolány modulem runtime Visual Studio Tools for Office.<br />– Jiné typy, které jsou součástí infrastruktury Visual Studio Tools for Office runtime a nejsou určeny pro použití přímo v kódu.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Třída, kterou můžete použít pro připojení sestavení přizpůsobení k dokumentům a pro přístup k datům uloženým v mezipaměti v dokumentech. Další informace najdete v tématu [Správa dokumentů na serveru pomocí třídy ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />– Několik tříd, které reprezentují hierarchii dat uložených v mezipaměti v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](accessing-data-in-documents-on-the-server.md).|

 Projekty, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](includes/net-v45-md.md)] také odkazují na následující sestavení. Tato sestavení nejsou součástí [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] redistribuovatelného rozhraní. Místo toho jsou závislá sestavení, která musí být nasazena s vaším řešením. Ve výchozím nastavení jsou zkopírovány do výstupní složky sestavení pro váš projekt ( **kopie lokální** vlastnosti pro tato sestavení je nastavena na **hodnotu true**). Pokud nasadíte projekt pomocí technologie ClickOnce, jsou tato sestavení součástí vygenerovaného balíčku.

|Název sestavení|Popis|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Poskytuje základní třídy pro generovanou `ThisAddIn` třídu v projektech VSTO Add-In a vygenerovanou třídu pásu karet ve všech projektech.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Poskytuje následující typy:<br /><br /> – Základní třídy pro vygenerované `ThisWorkbook` `Sheet` třídy a v projektech na úrovni dokumentu pro Excel.<br />-Model Windows Forms ovládací prvky, které lze použít na listech v projektech aplikace Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Poskytuje základní třídy pro třídy vygenerované `ThisAddIn` a formové oblasti v projektech aplikace Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Poskytuje následující typy:<br /><br /> – Základní třídy pro generovanou `ThisDocument` třídu v projektech na úrovni dokumentu pro Word<br />-Model Windows Forms ovládací prvky, které lze použít na dokumentech v projektech aplikace Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Sestavení v rozšířeních sady Office pro .NET Framework 3,5
 V následující tabulce jsou uvedena sestavení, která jsou součástí rozšíření Office pro .NET Framework 3,5. Dokumentaci o oborech názvů a třídách v těchto sestaveních naleznete v následující referenční části v dokumentaci k sadě Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Název sestavení|Popis|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Poskytuje následující typy:<br /><br /> – Základní třída Microsoft. Office. Tools. AddIn pro doplňky VSTO.<br />-Třídy pro vytváření přizpůsobení a inteligentních značek pásu karet. **Poznámka:**      Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Třídy pro vytváření podoken akcí v přizpůsobení na úrovni dokumentu a vlastních podoknech úloh v Doplňkech VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Poskytuje hostitelské položky a hostitelské ovládací prvky pro řešení aplikace Excel. Další informace najdete v tématu [Automatizace Excelu pomocí rozšířených objektů](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Poskytuje třídy, které lze použít k vytvoření vlastních oblastí formulářů v doplňkových doplňcích aplikace Outlook VSTO.|
|Microsoft.Office.Tools.Word.v9.0.dll|Poskytuje hostitelské položky a hostitelské ovládací prvky pro řešení pro Word. Další informace najdete v tématu [Automatizace Wordu pomocí rozšířených objektů](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Poskytuje následující typy:<br /><br /> – Třída [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) , která poskytuje možnosti datové vazby pro ovládací prvky hostitele v přizpůsobení na úrovni dokumentu.<br />– Jiné typy, které jsou součástí infrastruktury Visual Studio Tools for Office runtime a nejsou určeny pro použití přímo v kódu.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atribut a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> rozhraní, které lze použít pro ukládání datových objektů do mezipaměti v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [cache data](caching-data.md).<br />-Výjimky, které mohou být vyvolány modulem runtime Visual Studio Tools for Office.<br />– Jiné typy, které jsou součástí infrastruktury Visual Studio Tools for Office runtime a nejsou určeny pro použití přímo v kódu.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Poskytuje <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> rozhraní, které lze implementovat pro spuštění dalších kroků instalace jako poslední krok instalačního programu ClickOnce pro řešení Office. Další informace najdete v tématu [Pokročilé nasazení řešení Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Třída, kterou můžete použít k programovému připojení sestavení přizpůsobení k dokumentům a k přístupu k datům uloženým v mezipaměti v dokumentech. Další informace najdete v tématu [Správa dokumentů na serveru pomocí třídy ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />– Několik tříd, které reprezentují hierarchii dat uložených v mezipaměti v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Poskytuje následující typy:<br /><br /> – Třídy Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry a Microsoft. VisualStudio. Tools. Office. Runtime. Security. UserInclusionList, které můžete použít k vytvoření záznamů seznamu zahrnutí uživatelů pro udělení důvěryhodnosti na řešení pro systém Office, která cílí na .NET Framework 3,5.<br />– Jiné typy, které jsou součástí infrastruktury Visual Studio Tools for Office runtime a nejsou určeny pro použití přímo v kódu.|

## <a name="see-also"></a>Viz také
- [Přehled prostředí Visual Studio Tools for Office runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Scénáře instalace Visual Studio Tools for Office runtime](visual-studio-tools-for-office-runtime-installation-scenarios.md)
