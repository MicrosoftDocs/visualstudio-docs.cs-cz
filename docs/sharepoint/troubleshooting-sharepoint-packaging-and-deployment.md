---
title: Řešení potíží s balíčkem a nasazením služby SharePoint | Microsoft Docs
ms.date: 02/22/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eafac8015b7a2c51279b7a2d664f0e094d2397b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981939"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Řešení potíží s balením a nasazením služby SharePoint
  Toto téma popisuje různé problémy, se kterými se můžete setkat při zabalení a nasazení řešení služby SharePoint.

## <a name="enable-enhanced-debugging"></a>Povolit rozšířené ladění
 Chcete-li diagnostikovat mezi Visual Studio, SharePointem a jinými vrstvami, můžete použít klíč registru EnableDiagnostics k zobrazení trasování zásobníku. Další informace najdete v tématu [ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Přidat výstup projektu do balíčku řešení
 Výstup projektu můžete přidat do balíčku prostřednictvím návrháře balíčků. Pokud však přidáte výstup projektu, ujistěte se, že platforma projektu odpovídá platformě řešení služby SharePoint. Doporučujeme, abyste pro sestavení, která chcete nasadit na server SharePoint, používali všechny cílové platformy pro **procesor** . Další informace najdete v tématu [kompilace stránky, Návrháře projektu &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) a [pokročilé nastavení kompilátoru &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Upozornění a chyby ověřování
 Vývojové nástroje služby SharePoint v aplikaci Visual Studio provádějí kroky ověření a ověřují, zda je balíček řešení správně vytvořen. Můžete také vytvořit vlastní kroky ověření pro vaše funkce a balíčky. Další informace najdete v tématu [Postupy: vytváření vlastních funkcí a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Řešení konfliktů nasazení
 Když nasadíte řešení služby SharePoint, můžete najít kolize, pokud má položka na serveru stejný název, adresu URL nebo ID jako položka v balíčku řešení. Vlastnost **řešení konfliktů nasazení** můžete změnit tak, aby vyřešila, vyhlásila nebo ignorovala kolize pro moduly, webové části, instance seznamů a typy obsahu.

 Následující tabulka ukazuje nastavení vlastnosti **řešení konfliktů při nasazení** .

|Hodnota|Popis|
|-----------|-----------------|
|Automaticky|Detekuje kolizí a automaticky vyřeší konflikty.|
|Výzva|Před řešením konfliktů detekuje kolize a oznamuje je vývojářům.|
|Žádné|Nedetekuje kolize.|

## <a name="differences-between-f5-deployment"></a>Rozdíly mezi nasazením F5
 Použijete [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -li k nasazení projektu služby SharePoint na místní server SharePoint pro účely testování a ladění, je nutné provést několik dalších kroků [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Obnovte Internetovou informační službu (IIS) během kroku nasazení.

2. Automaticky přidružit pracovní postupy.

3. Nastavte pořadí aktivace funkcí v závislosti na hierarchii v Návrháři balíčků.

   Můžete přidat vlastní kroky nasazení a dále změnit chování **F5** . Další informace najdete v tématu [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Zpoždění zobrazení stránky služby SharePoint při nasazení vizuální webové části
 Zobrazení stránky SharePoint trvá při nasazení vizuální webové části do složky bin na [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)] , [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] nebo [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] . Změníte-li všechny soubory v adresáři nejvyšší úrovně [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , například adresář Bin, bude celá webová aplikace znovu zkompilována. To může způsobit zpoždění až 25 sekund, než se stránka SharePointu vykreslí.

### <a name="error-message"></a>Chybová zpráva
 Žádné

### <a name="resolution"></a>Řešení
 Pokud chcete tento problém obejít, proveďte následující kroky:

1. Nainstalujte aktualizaci KB967535, jak je uvedeno v podpora Microsoftu článku [Oprava: oprava hotfix je k dispozici pro opravu dvou problémů v ASP.NET ve službě IIS 7,0 pro systémy Windows Vista a Windows Server 2008](https://support.microsoft.com/help/967535).

2. Do souboru Web.config přidejte následující řádek:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Nasazení projektu SharePoint se nepovede s chybou. nepovedlo se extrahovat soubor CAB v řešení.
 Pokud název jakékoli položky SharePointového projektu obsahuje závorky, jeho řešení se při nasazení nepovede s chybou.

### <a name="error-message"></a>Chybová zpráva
 V kroku nasazení došlo k chybě: Přidat řešení: Nepodařilo se extrahovat soubor CAB v řešení.

### <a name="resolution"></a>Řešení
 Chcete-li tento problém obejít, odeberte všechny závorky v názvech položek projektu služby SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Při nasazení vizuální webové části do webu v jiné webové aplikaci se zobrazí chyba
 Při prvním nasazení vizuální webové části na web na jiné webové aplikaci, než na které je právě nasazená (změnou vlastnosti SiteUrl vizuální webové části), se zobrazí chyba.

### <a name="error-message"></a>Chybová zpráva
 Došlo k chybě v kroku nasazení – přidat řešení: funkce s ID [#] už je v této farmě nainstalovaná. K explicitnímu opětovnému přeinstalaci funkce použijte atribut Force.

### <a name="resolution"></a>Řešení
 K této chybě dochází z důvodu odvolání funkcí vizuální webové části na SharePointu. Chcete-li úspěšně nasadit vizuální webovou část, znovu nasaďte řešení volbou klávesy **F5** .

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Při nasazení vnořených uživatelských ovládacích prvků se zobrazí upozornění.
 K tomuto upozornění dochází, když nasadíte řešení služby SharePoint, které obsahuje vnořené uživatelské ovládací prvky, jako je například vizuální webová část obsahující uživatelský ovládací prvek nebo uživatelský ovládací prvek, který obsahuje vizuální webovou část nebo jiný uživatelský ovládací prvek. K tomuto upozornění dochází, je-li ovládací prvek přidán do návrháře přetažením z panelu nástrojů nebo pomocí @Register direktivy v zobrazení zdroje.

### <a name="error-message"></a>Chybová zpráva
 Upozornění 1 prvek ' [*název ovládacího prvku*] ' není známý prvek. Tato situace může nastat, pokud dojde k chybě kompilace na webu nebo chybí soubor web.config.

### <a name="resolution"></a>Řešení
 Pokud [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] systém projektu nemá informace o vnořeném uživatelském ovládacím prvku, nemůže poskytnout IntelliSense a vygeneruje upozornění. Systém projektu nezohledňuje vnořený uživatelský ovládací prvek, pokud projekt není sestaven a Návrhář není uzavřen a znovu otevřen, nebo pokud je povolena možnost automatického odvolání, což způsobí, že uživatelský ovládací prvek bude po ladění odvolán z podregistru služby SharePoint.

 Chcete-li toto upozornění odebrat, buď Sestavte projekt, a pak zavřete a znovu otevřete návrháře, nebo zakažte možnost automatického odvolání projektu. Chcete-li to provést, zrušte zaškrtnutí políčka **automaticky odvolat po ladění** na kartě **SharePoint** v dialogovém okně Vlastnosti projektu.

## <a name="see-also"></a>Viz také

- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)