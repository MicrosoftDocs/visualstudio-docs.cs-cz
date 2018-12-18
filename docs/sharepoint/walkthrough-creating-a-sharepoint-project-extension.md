---
title: 'Návod: Vytváření rozšíření projektu služby SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d68347f2b6b9f538555e05c91b15dcb045b46d6
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295979"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Návod: Vytváření rozšíření projektu SharePoint
  Tento návod ukazuje, jak vytvořit rozšíření pro projekty služby SharePoint. Rozšíření projektu můžete použít pro reakci na události na úrovni projektu, například pokud je projekt přidat, odstranit nebo přejmenovat. Můžete také přidat vlastní vlastnosti nebo odpovědět při změně hodnoty vlastnosti. Na rozdíl od rozšíření položky projektu projektu rozšíření nemůže být spojeny s konkrétní typ projektu služby SharePoint. Při vytváření rozšíření projektu rozšíření načte při otevření jakékoliv projektu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 V tomto návodu vytvoříte vlastní logickou vlastnost, která se přidá do jakéhokoli projektu SharePoint vytvoří v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pokud je nastavena na **True**, novou vlastnost přidá nebo mapuje složku Obrázky prostředků do vašeho projektu. Pokud je nastavena na **False**, složce bitové kopie je odebrána, pokud existuje. Další informace najdete v tématu [postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Tento návod demonstruje následující úkoly:  
  
-   Vytváření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření pro projekty služby SharePoint, který provede následující akce:  
  
    -   Přidá vlastní vlastnost projektu v okně Vlastnosti. Vlastnost se vztahuje do jakéhokoli projektu SharePoint.  
  
    -   Přidat mapovanou složku do projektu používá model objektu projektu služby SharePoint.  
  
    -   Používá [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modelu automatizačních objektů (DTE) pro mapovanou složku odstranit z projektu.  
  
-   Vytváření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension (VSIX) balíčku pro nasazení sestavení rozšíření vlastnost projektu.  
  
-   Ladění a testování vlastnosti projektu.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Tento návod používá **projekt VSIX** šablony [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] k vytvoření balíčku VSIX k nasazení rozšíření vlastnosti projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, je nutné vytvořit dva projekty:  
  
- Projekt VSIX k vytvoření balíčku VSIX k nasazení projektu rozšíření.  
  
- Projekt knihovny tříd, který implementuje rozšíření projektu.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
    > [!NOTE]  
    >  Tento uzel je dostupná jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
4.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework a klikněte na tlačítko **projekt VSIX** šablony.  
  
5.  V **název** zadejte **ProjectExtensionPackage**a klikněte na tlačítko **OK** tlačítko.  
  
     **ProjectExtensionPackage** projekt se objeví v **Průzkumníka řešení**.  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **Windows**.  
  
3.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework a klikněte na tlačítko **knihovny tříd** šablony projektu.  
  
4.  V **název** zadejte **ProjectExtension**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **ProjectExtension** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-project"></a>Konfigurace projektu
 Před napsáním kódu pro vytváření rozšíření projektu přidejte soubory kódu a odkazy na sestavení do projektu rozšíření.  
  
#### <a name="to-configure-the-project"></a>Konfigurace projektu  
  
1.  Přidat soubor kódu, který je pojmenován **CustomProperty** ProjectExtension projektu.  
  
2.  Otevřete místní nabídku **ProjectExtension** projektu a klikněte na tlačítko **přidat odkaz**.  
  
3.  V **správce odkazů - CustomProperty** dialogového okna zvolte **Framework** uzel a potom zaškrtněte políčko vedle System.ComponentModel.Composition a System.Windows.Forms sestavení.  
  
4.  Zvolte **rozšíření** uzlu, zaškrtněte políčko vedle Microsoft.VisualStudio.SharePoint a EnvDTE sestavení a klikněte na tlačítko **OK** tlačítko.  
  
5.  V **Průzkumníka řešení**v části **odkazy** složku **ProjectExtension** projektu, zvolte **EnvDTE**.  
  
6.  V **vlastnosti** okno Změnit **Embed Interop Types** vlastnost **False**.  
  
## <a name="define-the-new-sharepoint-project-property"></a>Definovat nové vlastnosti projektu služby SharePoint
 Vytvořte třídu, která definuje rozšíření projektu a chování nové vlastnosti projektu. Chcete-li definovat nový projekt rozšíření, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít definovat rozšíření projektu služby SharePoint. Přidejte také <xref:System.ComponentModel.Composition.ExportAttribute> do třídy. Tento atribut umožňuje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zjišťovat a načíst vaše <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementace. Předat <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> typ konstruktoru atributu.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Chcete-li definovat nové vlastnosti projektu služby SharePoint  
  
1.  Vložte následující kód do souboru CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>Sestavte řešení
 V dalším kroku sestavte řešení, abyste měli jistotu, že se zkompiluje bez chyb.  
  
#### <a name="to-build-the-solution"></a>Abyste mohli sestavit řešení  
  
1.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Vytvoření balíčku VSIX k nasazení rozšíření vlastností projektu
 Pokud chcete nasadit rozšíření projektu, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest, který je součástí projektu VSIX. Potom vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro soubor source.extension.vsixmanifest a klikněte na tlačítko **otevřete** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře soubor v Návrháři manifestu. Informace, které se zobrazí v **metadat** kartě se zobrazí také v **rozšíření a aktualizace**. Všechny balíčky VSIX vyžadují soubor extension.vsixmanifest. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **vlastní vlastnost projektu**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **vlastní vlastnost projektu služby SharePoint, která přepíná mapování složky prostředku bitové kopie do projektu**.  
  
5.  Zvolte **prostředky** kartu a klikněte na tlačítko **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
6.  V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MEFComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení** přepínač.  
  
8.  V **projektu** klikněte na položku **ProjectExtension**.  
  
     Tato hodnota určuje název sestavení, které vytváříte v projektu.  
  
9. Zvolte **OK** zavřete **přidat nové aktivum** dialogové okno.  
  
10. V panelu nabídky zvolte **souboru** > **Uložit vše** při dokončení a pak zavřete návrháře manifestu.  
  
11. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že se projekt zkompiluje bez chyb.  
  
12. V **Průzkumníka řešení**, otevřete místní nabídku **ProjectExtensionPackage** projekt a zvolte **otevřít složku v Průzkumníku souborů** tlačítko.  
  
13. V **Průzkumníka souborů**, otevřete výstupní složka sestavení pro projekt ProjectExtensionPackage a potom ověřte, zda složka obsahuje soubor s názvem ProjectExtensionPackage.vsix.  
  
     Výchozí je výstupní složka sestavení... složky \Bin\Debug ve složce, která obsahuje váš soubor projektu.  
  
## <a name="test-the-project-property"></a>Testování vlastností projektu
 Nyní jste připraveni otestovat vlastní vlastnosti projektu. Je nejjednodušší ladění a testování nového projektu vlastnost rozšíření v experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Tato instance [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] je vytvořen při spuštění rozšíření VSIX nebo jiný projekt rozšíření. Po ladění projektu, můžete nainstalovat rozšíření ve vašem systému a potom pokračovat v ladění a testování v normální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Ladění a testování rozšíření v experimentální instanci sady Visual Studio  
  
1.  Restartujte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s přihlašovacími údaji správce a pak otevřete ProjectExtensionPackage řešení.  
  
2.  Spustit sestavení pro ladění projektu buď pomocí tlačítka **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **spustit ladění**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1 projektu. 0 a spustí experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  V experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvoření projektu služby SharePoint pro řešení farmy a použijte výchozí hodnoty pro ostatní hodnoty v průvodci.  
  
    1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
    2.  V horní části **nový projekt** dialogového okna zvolte **rozhraní .NET Framework 3.5** v seznam verzí rozhraní .NET Framework.  
  
         Rozšíření nástrojů SharePoint vyžaduje funkce v této verzi [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  V části **šablony** uzlu, rozbalte **Visual C#** nebo **jazyka Visual Basic** uzlu, vyberte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
    4.  Zvolte **projektu služby SharePoint 2010** šablony a pak zadejte **ModuleTest** jako název projektu.  
  
4.  V **Průzkumníka řešení**, zvolte **ModuleTest** uzel projektu.  
  
     Nové vlastní vlastnost **složka obrázky mapy** se zobrazí v **vlastnosti** okno s výchozí hodnotou **False**.  
  
5.  Změňte hodnotu této vlastnosti na **True**.  
  
     Složka prostředků obrázků se přidá do projektu služby SharePoint.  
  
6.  Hodnota dané vlastnosti se vraťte do **False**.  
  
     Pokud se rozhodnete **Ano** tlačítko **odstranit složku Obrázky?** dialogové okno, bitové kopie z projektu služby SharePoint se odstraní složka prostředků.  
  
7.  Ukončete experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření projektů SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Ukládání dat do rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Přidružení vlastních dat k rozšíření nástrojů SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
