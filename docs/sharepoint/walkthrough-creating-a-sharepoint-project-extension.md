---
title: 'Návod: Vytvoření rozšíření projektu služby SharePoint | Microsoft Docs'
description: Vytvořte rozšíření projektu služby SharePoint, které lze použít k reakci na události na úrovni projektu, například při přidání, odstranění nebo přejmenování projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 378e839ea5f4223873fbbeec8d7b401ae0b16fc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918765"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Návod: Vytvoření rozšíření projektu služby SharePoint
  Tento návod ukazuje, jak vytvořit rozšíření pro projekty služby SharePoint. Můžete použít rozšíření projektu pro reakci na události na úrovni projektu, jako je například přidání, odstranění nebo přejmenování projektu. Můžete také přidat vlastní vlastnosti nebo reagovat při změně hodnoty vlastnosti. Na rozdíl od rozšíření položek projektu nelze rozšíření projektu přidružit ke konkrétnímu typu projektu služby SharePoint. Při vytváření rozšíření projektu rozšíření načte, když je otevřen libovolný druh projektu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 V tomto návodu vytvoříte vlastní logickou vlastnost, která je přidána do jakéhokoli projektu služby SharePoint vytvořeného v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Když je nastavená **hodnota true**, nová vlastnost přidá nebo mapuje složku prostředků imagí do projektu. Pokud je nastavena **hodnota false**, složka images se odebere, pokud existuje. Další informace najdete v tématu [Postup: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření pro projekty služby SharePoint, které provádí následující akce:

  - Přidá do okno Vlastnosti vlastní vlastnost projektu. Vlastnost se vztahuje na všechny projekty služby SharePoint.

  - K přidání mapované složky do projektu používá objektový model projektu služby SharePoint.

  - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]K odstranění mapované složky z projektu používá automatizační objektový model (DTE).

- Sestavení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíčku rozšíření (VSIX) pro nasazení sestavení rozšíření vlastnosti projektu.

- Ladění a testování vlastnosti projektu.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Hodnota [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] Tento návod používá šablonu **projektu VSIX** v části [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] k vytvoření balíčku VSIX k nasazení rozšíření vlastností projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit dva projekty:

- Projekt VSIX k vytvoření balíčku VSIX pro nasazení rozšíření projektu.

- Projekt knihovny tříd, který implementuje rozšíření projektu.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

    > [!NOTE]
    > Tento uzel je k dispozici pouze v případě, že nainstalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

4. V horní části dialogového okna zvolte v seznamu verzí .NET Framework **.NET Framework 4,5** a potom zvolte šablonu **projektu VSIX** .

5. Do pole **název** zadejte **ProjectExtensionPackage** a pak klikněte na tlačítko **OK** .

     Projekt **ProjectExtensionPackage** se zobrazí v **Průzkumník řešení**.

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a pak zvolte možnost **Windows**.

3. V horní části dialogového okna zvolte v seznamu verzí .NET Framework **.NET Framework 4,5** a pak zvolte šablonu projektu **Knihovna tříd** .

4. Do pole **název** zadejte **ProjectExtension** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **ProjectExtension** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-project"></a>Konfigurace projektu
 Předtím, než napíšete kód pro vytvoření rozšíření projektu, přidejte soubory kódu a odkazy na sestavení do projektu rozšíření.

#### <a name="to-configure-the-project"></a>Konfigurace projektu

1. Přidejte do projektu ProjectExtension soubor kódu s názvem **vlastnosti CustomProperty** .

2. Otevřete místní nabídku projektu **ProjectExtension** a poté zvolte možnost **Přidat odkaz**.

3. V dialogovém okně **Správce odkazů – vlastnosti CustomProperty** zvolte uzel **rozhraní** a potom zaškrtněte políčko vedle sestavení System. ComponentModel. složení a System. Windows. Forms.

4. Zvolte uzel **rozšíření** , zaškrtněte políčko vedle sestavení Microsoft. VisualStudio. SharePoint a EnvDTE a pak klikněte na tlačítko **OK** .

5. V **Průzkumník řešení** ve složce **odkazy** pro projekt **ProjectExtension** vyberte možnost **EnvDTE**.

6. V okně **vlastnosti** změňte vlastnost **Vložit typy spolupráce** na **hodnotu false**.

## <a name="define-the-new-sharepoint-project-property"></a>Definujte novou vlastnost projektu služby SharePoint.
 Vytvořte třídu, která definuje rozšíření projektu a chování vlastnosti New Project. Chcete-li definovat nové rozšíření projektu, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní. Implementujte toto rozhraní vždy, když chcete definovat rozšíření pro projekt služby SharePoint. Přidejte také <xref:System.ComponentModel.Composition.ExportAttribute> do třídy. Tento atribut umožňuje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zjistit a načíst vaši <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementaci. Předejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> typ konstruktoru atributu.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Definování nové vlastnosti projektu služby SharePoint

1. Vložte následující kód do souboru kódu vlastnosti CustomProperty.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Sestavení řešení
 V dalším kroku Sestavte řešení, abyste se ujistili, že se zkompiluje bez chyb.

#### <a name="to-build-the-solution"></a>Sestavení řešení

1. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Vytvoření balíčku VSIX pro nasazení rozšíření vlastností projektu
 Chcete-li nasadit rozšíření projektu, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejdřív nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest, který je zahrnutý v projektu VSIX. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX

1. V **Průzkumník řešení** otevřete místní nabídku pro soubor source. extension. vsixmanifest a pak klikněte na tlačítko **otevřít** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře soubor v Návrháři manifestu. Informace, které se zobrazí na kartě **metadata** , se zobrazí také v části **rozšíření a aktualizace**. Všechny balíčky VSIX vyžadují soubor Extension. vsixmanifest. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Do pole **název produktu** zadejte **vlastní vlastnost projektu**.

3. Do pole **Autor** zadejte **Contoso**.

4. Do pole **Popis** zadejte **vlastní vlastnost projektu služby SharePoint, která přepíná mapování složky prostředků imagí na projekt**.

5. Zvolte kartu **aktiva** a pak klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

6. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MEFComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. V seznamu **zdroj** klikněte na tlačítko možnost **projekt v aktuálním řešení** .

8. V seznamu **projekt** vyberte možnost **ProjectExtension**.

     Tato hodnota určuje název sestavení, které vytváříte v projektu.

9. Kliknutím na **tlačítko OK** zavřete dialogové okno **Přidat nový prostředek** .

10. Na panelu nabídek zvolte možnost **soubor**  >  **Uložit vše** po dokončení a poté ukončete návrháře manifestu.

11. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení** a pak se ujistěte, že se projekt zkompiluje bez chyb.

12. V **Průzkumník řešení** otevřete místní nabídku pro projekt **ProjectExtensionPackage** a klikněte na tlačítko **Otevřít složku v Průzkumníkovi souborů** .

13. V **Průzkumníku souborů** otevřete výstupní složku sestavení pro projekt ProjectExtensionPackage a pak ověřte, že složka obsahuje soubor s názvem ProjectExtensionPackage. VSIX.

     Ve výchozím nastavení je výstupní složka sestavení.. Složka \bin\Debug ve složce, která obsahuje soubor projektu.

## <a name="test-the-project-property"></a>Otestování vlastnosti projektu
 Nyní jste připraveni otestovat vlastnost vlastního projektu. Je nejjednodušší ladit a testovat nové rozšíření vlastností projektu v experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Tato instance [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] je vytvořena, když spustíte VSIX nebo jiný projekt rozšiřitelnosti. Po ladění projektu můžete rozšíření nainstalovat do systému a poté pokračovat v ladění a otestovat ho v normální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Ladění a testování rozšíření v experimentální instanci aplikace Visual Studio

1. Restartujte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s přihlašovacími údaji správce a pak otevřete řešení ProjectExtensionPackage.

2. Spusťte ladicí sestavení projektu, a to tak, že vyberete klávesu **F5** nebo v řádku nabídek zvolíte **ladění**  >  **Spustit ladění**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nainstaluje rozšíření do%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom projektu Property\1.0 a spustí experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. V experimentální instanci nástroje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvořte projekt služby SharePoint pro řešení farmy a použijte výchozí hodnoty pro ostatní hodnoty v průvodci.

    1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

    2. V horní části dialogového okna **Nový projekt** vyberte v seznamu verzí .NET Framework položku **.NET Framework 3,5** .

         Rozšíření nástrojů služby SharePoint vyžadují funkce v této verzi [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. V uzlu **šablony** rozbalte uzel **Visual C#** nebo **Visual Basic** , zvolte uzel **služby SharePoint** a pak zvolte uzel **2010** .

    4. Zvolte šablonu **projektu SharePoint 2010** a pak jako název projektu zadejte **ModuleTest** .

4. V **Průzkumník řešení** vyberte uzel projektu **ModuleTest** .

     V okně **vlastnosti** se zobrazí nová **Složka obrázky mapy** vlastních vlastností s výchozí hodnotou **false (NEPRAVDA**).

5. Změňte hodnotu vlastnosti na **true**.

     Složka prostředků imagí je přidána do projektu služby SharePoint.

6. Změňte hodnotu vlastnosti zpět na **false**.

     Pokud kliknete na tlačítko **Ano** v dialogovém okně **Odstranit složku s obrázky?** , Složka prostředků imagí je odstraněna z projektu služby SharePoint.

7. Zavřete experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

## <a name="see-also"></a>Viz také
- [Rozšiřování projektů SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Uložení dat v rozšířeních systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Přidružit vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)