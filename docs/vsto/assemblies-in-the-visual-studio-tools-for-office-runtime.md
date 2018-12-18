---
title: Sestavení v nástrojích Visual Studio Tools pro systém Office runtime
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66ee95d4f102ac4206a9ed55a1fc97fc251c4f9c
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248108"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Sestavení v nástrojích Visual Studio Tools pro systém Office runtime
  Když vytvoříte projekt sady Office, Visual Studio automaticky přidá odkazy na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sestavení, které se používají pro zvolený typ projektu a cílové rozhraní .NET Framework projektu. Existují různých sestaveních v rozšířeních Office pro rozhraní .NET Framework 3.5 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Další informace o rozšířeních sady Office naleznete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Sestavení v rozšířeních Office pro rozhraní .NET Framework 4 a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Následující tabulka uvádí, které jsou zahrnuty v rozšířeních Office pro sestavení [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dokumentaci ke službě obory názvů a typy v sestavení, naleznete v tématu [spravované referenční materiály služby &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Název sestavení|Popis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Poskytuje následující typy:<br /><br /> -Typy pro vytváření vlastních nastavení pásu karet a inteligentní značky. **Poznámka:**      Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Typy pro Tvorba podoken akcí v přizpůsobeních na úrovni dokumentu a vlastních podoken úloh v doplňků VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Poskytuje rozhraní, které představují hostitelských položek a hostitelských ovládacích prvků pro projekty aplikace Excel a podpůrné typy. Další informace najdete v tématu [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Poskytuje typy, které můžete použít k vytvoření vlastního formuláře oblastí v doplňcích VSTO pro Outlook.|  
|Microsoft.Office.Tools.Word.dll|Poskytuje rozhraní, které představují hostitelských položek a hostitelských ovládacích prvků pro projekty aplikace Word a podpůrné typy. Další informace najdete v tématu [automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Poskytuje následující typy:<br /><br /> – Výjimky, které mohou být vyvolány Visual Studio Tools for Office runtime.<br />– Oblastem formuláře atributy, které můžete použít při vytváření aplikace Outlook.|  
|Microsoft.Office.Tools.dll|Poskytuje typy, které jsou součástí sady Visual Studio Tools for Office runtime infrastrukturu a není určena pro použití přímo v kódu.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atribut a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> rozhraní, které vám umožní mezipaměti datové objekty v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [ukládat data do mezipaměti](../vsto/caching-data.md).<br />– <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Rozhraní, které můžete implementovat, abyste spusťte další instalační kroky jako poslední krok instalační program ClickOnce pro řešení Office. Další informace najdete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />– Výjimky, které mohou být vyvolány Visual Studio Tools for Office runtime.<br />-Další typy, které jsou součástí sady Visual Studio Tools for Office runtime infrastrukturu a není určena pro použití přímo v kódu.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Třídy, který můžete použít k připojení vlastního nastavení sestavení k dokumentům a pro přístup k data uložená v mezipaměti v dokumentech. Další informace najdete v tématu [spravovat dokumenty na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Několik tříd, které představují hierarchii uložené v mezipaměti dat v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Projekty, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] také odkazovat na následující sestavení. Tato sestavení nejsou součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistributable. Místo toho jsou závislá sestavení, které musí být nasazen v rámci řešení. Ve výchozím nastavení, budou zkopírovány do výstupní složka sestavení pro projekt ( **Kopírovat místně** vlastnost pro tato sestavení jsou nastavena na **True**). Pokud nasadíte projekt s použitím technologie ClickOnce, jsou tato sestavení součástí vygenerovaný balíček.  
  
|Název sestavení|Popis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Poskytuje základní třídy pro vygenerovaný `ThisAddIn` třídou v generované třídě pásu karet ve všech projektech a jeho projekty doplňku VSTO.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Poskytuje následující typy:<br /><br /> -Základní třídy pro vygenerovaný `ThisWorkbook` a `Sheet` třídy v úrovni dokumentu projekty aplikace Excel.<br />– Windows Forms ovládací prvky, které můžete použít na listy v projektech aplikace Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Poskytuje základní třídy pro vygenerovaný `ThisAddIn` tvořících oblasti tříd v projektech Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Poskytuje následující typy:<br /><br /> -Základní třídy pro vygenerovaný `ThisDocument` tříd v projektech na úrovni dokumentu pro aplikaci Word.<br />– Windows Forms ovládací prvky, které můžete použít v dokumentech v projektech aplikace Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Sestavení v rozšířeních Office pro rozhraní .NET Framework 3.5  
 V následující tabulce jsou uvedeny sestavení, které jsou obsaženy v rozšířeních Office pro rozhraní .NET Framework 3.5. Dokumentaci k obory názvů a třídy v těchto sestaveních, najdete v následující informační části dokumentace k Visual Studiu 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Název sestavení|Popis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Poskytuje následující typy:<br /><br /> -Microsoft.Office.Tools.AddIn základní třídu pro doplňky VSTO.<br />– Třídy pro vytváření vlastních nastavení pásu karet a inteligentní značky. **Poznámka:**      Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />– Třídy pro tvorbu podokna akcí v přizpůsobeních na úrovni dokumentu a vlastních podoken úloh v doplňcích VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Poskytuje hostitelských položek a hostitelských ovládacích prvků pro řešení pro aplikaci Excel. Další informace najdete v tématu [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Poskytuje třídy, které můžete použít k vytvoření vlastního formuláře oblastí v doplňcích VSTO pro Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Poskytuje hostitelských položek a hostitelských ovládacích prvků pro řešení aplikace Word. Další informace najdete v tématu [automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Poskytuje následující typy:<br /><br /> – [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) třídu, která poskytuje možnosti vázání dat pro hostitelské ovládací prvky v úrovni dokumentu přizpůsobení.<br />-Další typy, které jsou součástí sady Visual Studio Tools for Office runtime infrastrukturu a není určena pro použití přímo v kódu.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atribut a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> rozhraní, které vám umožní mezipaměti datové objekty v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [ukládat data do mezipaměti](../vsto/caching-data.md).<br />– Výjimky, které mohou být vyvolány Visual Studio Tools for Office runtime.<br />-Další typy, které jsou součástí sady Visual Studio Tools for Office runtime infrastrukturu a není určena pro použití přímo v kódu.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Poskytuje <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> rozhraní, které můžete implementovat, abyste spusťte další instalační kroky jako poslední krok instalační program ClickOnce pro řešení Office. Další informace najdete v tématu [nasazení řešení Advanced Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Poskytuje následující typy:<br /><br /> – <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Třídy, který můžete použít k připojování do dokumentů prostřednictvím kódu programu vlastního nastavení sestavení a pro přístup k data uložená v mezipaměti v dokumentech. Další informace najdete v tématu [spravovat dokumenty na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Několik tříd, které představují hierarchii uložené v mezipaměti dat v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Poskytuje následující typy:<br /><br /> -Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry a Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList třídy, které vám umožní vytvořit uživatele zařazení položky seznamu zajištění důvěryhodnosti pro Office řešení, které jsou cíleny rozhraní .NET Framework 3.5.<br />-Další typy, které jsou součástí sady Visual Studio Tools for Office runtime infrastrukturu a není určena pro použití přímo v kódu.|  
  
## <a name="see-also"></a>Viz také:  
 [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office runtime instalace scénáře](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  