---
title: Řešení potíží s balení a nasazení SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba6f0a1aff0c263534c17256b7f5cf49ff9c9533
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898054"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Řešení potíží s balení a nasazení SharePoint
  Toto téma popisuje různé problémy, které se mohou vyskytnout po zabalení a nasazení řešení služby SharePoint.

## <a name="enable-enhanced-debugging"></a>Povolení rozšířeného ladění
 K diagnostice mezi Visual Studio, SharePoint a jinými vrstvami, můžete klíč registru EnableDiagnostics pro zobrazení trasování zásobníku. Další informace najdete v tématu [řešení ladění služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Přidat výstup projektu do balíčku řešení
 Můžete přidat výstup projektu do balíčku prostřednictvím návrháře balíčku. Ale při přidání výstupu projektu, ujistěte se, zda odpovídá platforma projektu platformě řešení služby SharePoint. Doporučujeme použít **jakýkoli procesor** cílovou platformu pro sestavení, které chcete nasadit na SharePoint server. Další informace najdete v tématu [stránka kompilovat, Návrhář projektu &#40;jazyka Visual Basic&#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) a [Advanced kompilátoru dialogové okno nastavení &#40;jazyka Visual Basic&#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).

## <a name="validation-warnings-and-errors"></a>Ověření upozornění a chyby
 Nástroje pro vývoj služby SharePoint v sadě Visual Studio provedou kroky ověření, že je správně vytvořen balíček řešení. Můžete také vytvořit vlastní ověřovací postup pro součásti a balíčky. Další informace najdete v tématu [postupy: vytvoření vlastní funkce a balíku ověřovacích pravidel pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Řešení konfliktů při nasazení
 Když nasadíte řešení služby SharePoint, můžete najít kolize, když položka na serveru má stejný název, URL nebo ID jako položka v balíčku řešení. Můžete změnit **řešení konfliktů při nasazení** vlastnosti řešení, sestavu nebo ignorování kolizí pro moduly, webové části, seznam instancí a typy obsahu.

 Následující tabulka ukazuje nastavení **řešení konfliktů při nasazení** vlastnost.

|Hodnota|Popis|
|-----------|-----------------|
|Automatické|Detekuje kolize a řeší konflikty automaticky.|
|řádek|Detekuje kolize a ohlásí je vývojáři před řešením konfliktů.|
|Žádné|Nemůže zjistit kolize.|

## <a name="differences-between-f5-deployment"></a>Rozdíly mezi nasazením pomocí klávesy F5
 Při použití [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] k nasazení projektu služby SharePoint na místní server SharePoint pro testování a ladění, existují některé další kroky, které provádí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1. Resetujte Internetové informační služby (IIS) při kroku nasazení.

2. Automaticky přidruží pracovní postupy.

3. Nastavte pořadí aktivace funkce podle hierarchie v Návrháři balíčku.

   Můžete přidat vlastní kroky nasazení pro další změny **F5** chování. Další informace najdete v tématu [návod: vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Prodleva zobrazení stránky služby SharePoint při nasazení vizuální webové části
 Stránku služby SharePoint trvá zobrazení velmi při nasazení vizuální webové části do složky Bin na [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], nebo [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Pokud změníte některé soubory v nejvyšší úrovni [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] znovu zkompiluje adresář, jako je například adresář Bin, celá webová aplikace. To může způsobit zpoždění až 25 sekund pro stránku služby SharePoint k vykreslení.

### <a name="error-message"></a>Chybová zpráva
 Žádné

### <a name="resolution"></a>Rozlišení
 Chcete-li tento problém vyřešit, proveďte následující kroky:

1.  Nainstalujte aktualizaci KB967535, jak je uvedeno v článek Microsoft Support [oprava: oprava hotfix je k dispozici pro opravu dvou problémů v technologii ASP.NET ve službě IIS 7.0 pro Windows Vista a Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Přidejte následující řádek do souboru Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Nasazení projektu služby SharePoint se nezdaří s chybou "Nepodařilo se extrahovat soubor cab v rámci řešení"
 Pokud název žádné položky projektu služby SharePoint obsahuje závorky, jeho řešení se nezdaří v nasazení s chybou.

### <a name="error-message"></a>Chybová zpráva
 V kroku nasazení "Přidání řešení" došlo k chybě: nepovedlo se extrahovat soubor cab v řešení.

### <a name="resolution"></a>Rozlišení
 Chcete-li tento problém vyřešit, odeberte všechny závorky v názvech položek projektu služby SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Při nasazení vizuální webové části na web jiné webové aplikace se zobrazí chyba
 Při prvním nasazení vizuální webové části na web na webové aplikace jiné než té, na které je právě nasazena (změnou vlastnosti SiteUrl vizuální webové části), dojde k chybě.

### <a name="error-message"></a>Chybová zpráva
 V kroku nasazení "Přidání řešení" došlo k chybě: funkci s ID [#] již byla v této farmě nainstalována. Znovu explicitně nainstalujte funkci pomocí atributu force.

### <a name="resolution"></a>Rozlišení
 K této chybě dochází kvůli způsobu, jakým jsou odvolány vizuální funkce webových částí služby SharePoint. K úspěšnému zavedení vizuální webové části, nasaďte řešení znovu kliknutím **F5** klíč.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Při nasazení vnořených uživatelských ovládacích prvků se zobrazí upozornění
 K tomuto upozornění dochází, když nasadíte řešení služby SharePoint, která obsahuje vnořené uživatelské ovládací prvky, jako je například vizuální webovou část, obsahující uživatelský ovládací prvek nebo uživatelský ovládací prvek, který obsahuje vizuální webovou část nebo jiný uživatelský ovládací prvek. Toto upozornění se zobrazí, zda je ovládací prvek přidat do návrháře přetažením z panelu nástrojů nebo pomocí @Register direktiv v zobrazení zdroje.

### <a name="error-message"></a>Chybová zpráva
 Upozornění 1 prvek "[*název ovládacího prvku*]" není známý prvek. Tato situace může nastat, pokud dochází k chybě kompilace na webovém serveru nebo v souboru web.config chybí.

### <a name="resolution"></a>Rozlišení
 Pokud [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektový systém nebude vědět o vnořeném uživatelském ovládacím prvku, nemůže poskytnout technologii IntelliSense a vydá varování. Projektový systém nebude vědět o vnořeném uživatelském ovládacím prvku. Pokud projekt není sestaven a Návrhář není uzavřen a znovu otevřen nebo pokud automatické odvolání možnost povolená, což způsobí, že uživatelský ovládací prvek na být stažen z podregistru služby SharePoint po ladění.

 Pokud chcete toto upozornění odebrat, sestavte projekt a pak zavřete a znovu otevřete návrháře nebo zakázat pro projekt možnost automatického odvolání. Chcete-li to provést, zrušte **automatické odvolání po ladění** zaškrtávací políčko na **SharePoint** kartu dialogové okno Vlastnosti projektu.

## <a name="see-also"></a>Viz také:
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

