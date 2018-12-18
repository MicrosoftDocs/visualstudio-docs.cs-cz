---
title: 'Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c74feaed6c108f9dcfb5f2b374a72c34526134b0
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296148"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint
  Při nasazení projektu služby SharePoint, aplikace Visual Studio provede série kroků nasazení v určitém pořadí. Visual Studio obsahuje mnoho vestavěné kroky nasazení, ale můžete také vytvořit svoje vlastní.  
  
 V tomto návodu vytvoříte vlastního kroku nasazení pro upgrade řešení na serveru, na kterém běží SharePoint. Visual Studio obsahuje vestavěné kroky nasazení pro celou řadu úloh, tyto odvolává nebo přidání řešení, ale nezahrnuje krok nasazení upgradu řešení. Ve výchozím nastavení, když nasadíte řešení služby SharePoint, Visual Studio nejprve odvolá řešení (pokud už je nasazený) a pak znovu nasadí celé řešení. Další informace o postupu integrované nasazení najdete v tématu [nasazení, publikování a upgradování balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Tento návod demonstruje následující úkoly:  
  
-   Vytváření rozšíření pro Visual Studio, který provádí dvě hlavní úlohy:  
  
    -   Definuje rozšíření vlastního kroku nasazení pro upgrade řešení služby SharePoint.  
  
    -   Toto rozšíření vytvoří rozšíření projektu, který definuje novou konfiguraci nasazení, což je sada kroky nasazení, které jsou spouštěny pro daný projekt. Novou konfiguraci nasazení zahrnuje krok vlastního nasazení a několik vestavěné kroky nasazení.  
  
-   Vytvoření dvou vlastních příkazů služby SharePoint, která volá sestavení rozšíření. SharePoint – příkazy jsou metody, které je možné vyvolat v sestavení rozšíření, které chcete používat rozhraní API v objektovém modelu serveru SharePoint. Další informace najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Vytváření balíčku rozšíření Visual Studio (VSIX) nasadit obě sestavení.  
  
-   Testování nového kroku nasazení.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované edice systému Windows, SharePoint a Visual Studio.
  
- Visual Studio SDK. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení rozšíření. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Použití objektového modelu serveru pro službu SharePoint. Další informace najdete v tématu [pomocí objektového modelu SharePoint Foundation na straně serveru](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- Řešení služby SharePoint. Další informace najdete v tématu [přehled řešení](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
- Upgrade řešení služby SharePoint. Další informace najdete v tématu [upgradování řešení](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, je nutné vytvořit tři projekty:  
  
- Projekt VSIX k vytvoření balíčku VSIX k nasazení rozšíření.  
  
- Projekt knihovny tříd, který implementuje rozšíření. Tento projekt musí cílit na rozhraní .NET Framework 4.5.  
  
- Projekt knihovny tříd, který definuje vlastní příkazy služby SharePoint. Tento projekt musí cílit na rozhraní .NET Framework 3.5.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
    > [!NOTE]  
    >  **Rozšiřitelnost** uzel je dostupný jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
4.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework.  
  
5.  Zvolte **projekt VSIX** šablony, pojmenujte projekt **UpgradeDeploymentStep**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **UpgradeDeploymentStep** projektu **Průzkumníka řešení**.  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel UpgradeDeploymentStep řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **Windows** uzlu.  
  
3.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework.  
  
4.  Zvolte **knihovny tříd** šablony projektu, pojmenujte projekt **DeploymentStepExtension**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **DeploymentStepExtension** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Chcete-li vytvořit příkaz projektu služby SharePoint  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel UpgradeDeploymentStep řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **Windows** uzlu.  
  
3.  V horní části dialogového okna zvolte **rozhraní .NET Framework 3.5** v seznam verzí rozhraní .NET Framework.  
  
4.  Zvolte **knihovny tříd** šablony projektu, pojmenujte projekt **SharePointCommands**a klikněte na tlačítko **OK** tlačítko.  
  
     Visual Studio přidá **SharePointCommands** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-projects"></a>Konfigurace projektů
 Než napíšete kód k vytvoření vlastního nasazení kroku, je nutné přidat soubory kódu a odkazy na sestavení a je nutné nakonfigurovat projekty.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Ke konfiguraci projektu DeploymentStepExtension
  
1.  V **DeploymentStepExtension** projektu, přidejte dva soubory kódu, které mají následující názvy:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Otevřete místní nabídku pro projekt DeploymentStepExtension a klikněte na tlačítko **přidat odkaz**.  
  
3.  Na **Framework** kartu, zaškrtněte políčko pro sestavení System.ComponentModel.Composition.  
  
4.  Na **rozšíření** kartu, zaškrtněte políčko pro sestavení Microsoft.VisualStudio.SharePoint a klikněte na tlačítko **OK** tlačítko.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Ke konfiguraci projektu SharePointCommands
  
1.  V **SharePointCommands** projektu, přidejte soubor kódu, který je pojmenován příkazy.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku na **SharePointCommands** uzel projektu a klikněte na tlačítko **přidat odkaz**.  
  
3.  Na **rozšíření** kartu, zaškrtněte políčka pro následující sestavení a pak klikněte na tlačítko **OK** tlačítko  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Definice kroku vlastní nasazení
 Vytvořte třídu, která definuje krok upgradu nasazení. Chcete-li definovat krok nasazení, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít definovat vlastní krok nasazení.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Chcete-li definovat kroku vlastní nasazení  
  
1.  V **DeploymentStepExtension** projektu, otevřete soubor kódu UpgradeStep a vložte následující kód do něj.  
  
    > [!NOTE]  
    >  Po přidání tohoto kódu, bude mít projekt několik chyb kompilace, ale zmizí při vložení kódu v dalších krocích.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Vytvořte konfiguraci nasazení, která zahrnuje krok vlastní nasazení
 Vytváření rozšíření projektu pro novou konfiguraci nasazení, která zahrnuje několik vestavěné kroky nasazení a nový krok upgradu nasazení. Vytvořením tohoto rozšíření pomoci vývojářům Sharepointu pomocí kroku nasazení upgradu v projektech SharePoint.  
  
 Pro vytvoření konfigurace nasazení, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít vytváření rozšíření projektu služby SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Pro vytvoření konfigurace nasazení  
  
1.  V **DeploymentStepExtension** projektu, otevřete soubor kódu DeploymentConfigurationExtension a vložte následující kód do něj.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Vytvoření vlastních příkazů služby SharePoint
 Vytvořte dvě vlastní příkazy, které volají do objektového modelu serveru pro službu SharePoint. Jeden příkaz určuje, jestli už je nasazená řešení; Další příkaz provede upgrade řešení.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Chcete-li definovat příkazů služby SharePoint  
  
1.  V **SharePointCommands** projektu, otevřete soubor kódu příkazy a vložte následující kód do něj.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu, je celý kód pro vlastní nasazení krok a příkazů služby SharePoint v projektech. Sestavení je, abyste měli jistotu, že proveďte kompilaci bez chyby.  
  
#### <a name="to-build-the-projects"></a>K sestavení projektů  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **DeploymentStepExtension** projektu a klikněte na tlačítko **sestavení**.  
  
2.  Otevřete místní nabídku **SharePointCommands** projektu a klikněte na tlačítko **sestavení**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Vytvoření balíčku VSIX k nasazení rozšíření
 Pokud chcete nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest v projektu VSIX. Pak vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX  
  
1.  V **Průzkumníka řešení**v části **UpgradeDeploymentStep** projektu, otevřete místní nabídku **source.extension.vsixmanifest** souboru a klikněte na tlačítko  **Otevřít**.  
  
     Visual Studio otevře soubor v editoru manifestu. Soubor source.extension.vsixmanifest je základem pro soubor extension.vsixmanifest, které vyžadují všechny balíčky VSIX. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **upgradovat kroku nasazení pro projekty SharePoint**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **poskytuje vlastní nasazení upgradu krok, který lze použít v projektech SharePoint**.  
  
5.  V **prostředky** kartu Editor, zvolte **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
6.  V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MefComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
8.  V **projektu** klikněte na položku **DeploymentStepExtension**a klikněte na tlačítko **OK** tlačítko.  
  
9. V editoru manifestu vyberte **nový** tlačítko znovu.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
10. V **typ** seznamu, zadejte **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Tento prvek určuje vlastní rozšíření, které chcete zahrnout do rozšíření aplikace Visual Studio. Další informace najdete v tématu [Asset – Element (VSX schéma)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
12. V **projektu** klikněte na položku **SharePointCommands**a klikněte na tlačítko **OK** tlačítko.  
  
13. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že řešení zkompiluje bez chyb.  
  
14. Ujistěte se, že výstupní složka sestavení pro projekt UpgradeDeploymentStep nyní obsahuje soubor UpgradeDeploymentStep.vsix.  
  
     Výchozí je výstupní složka sestavení... složky \Bin\Debug ve složce, která obsahuje váš soubor projektu.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Příprava na testovací krok nasazení upgradu
 Otestovat krok nasazení upgradu, musíte nejprve nasadit ukázkové řešení na Sharepointovém webu. Začněte tím, že ladění rozšíření v experimentální instanci sady Visual Studio. Vytvořte definici seznamu a instancí seznamu k otestování nasazení krok a pak je nasadit na web služby SharePoint. V dalším kroku změnit definici seznamu a seznam instancí a znovu nasadit k předvedení jak přepíše výchozí proces nasazení řešení na webu služby SharePoint.  
  
 Dále v tomto názorném postupu upravíte definici seznamu a instancí seznamu a pak je budete upgradovat na webu služby SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Chcete-li začít ladit rozšíření  
  
1.  Restartujte sadu Visual Studio s přihlašovacími údaji správce a pak otevřete UpgradeDeploymentStep řešení.  
  
2.  V projektu DeploymentStepExtension, otevřete soubor kódu UpgradeStep a na první řádek kódu přidejte zarážku `CanExecute` a `Execute` metody.  
  
3.  Spuštění ladění zvolením **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **spustit ladění**.  
  
4.  Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade kroku nasazení pro SharePoint Projects\1.0 a spustí experimentální instanci sady Visual Studio. Krok nasazení upgradu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Vytvoření projektu služby SharePoint s definicí seznamu a instance seznamu  
  
1. V experimentální instanci sady Visual Studio na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2. V **nový projekt** dialogového okna rozbalte **Visual C#** uzlu nebo **jazyka Visual Basic** uzlu, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
3. V horní části dialogového okna, ujistěte se, že **rozhraní .NET Framework 3.5** se zobrazí v seznamu verzí rozhraní .NET Framework.  
  
    Projekty pro [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] vyžadují tuto verzí rozhraní .NET Framework.  
  
4. V seznamu šablon projektu vyberte **projektu služby SharePoint 2010**, pojmenujte projekt **EmployeesListDefinition**a klikněte na tlačítko **OK** tlačítko.  
  
5. V **Průvodce přizpůsobením SharePoint**, zadejte adresu URL webu, který chcete použít pro ladění.  
  
6. V části **co je úroveň důvěryhodnosti pro toto řešení SharePoint**, zvolte **nasadit jako řešení farmy** přepínač.  
  
   > [!NOTE]  
   >  Krok nasazení upgradu nepodporuje řešení v izolovaném prostoru.  
  
7. Zvolte **Dokončit** tlačítko.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt EmployeesListDefinition.  
  
8. Otevřete místní nabídku pro projekt EmployeesListDefinition, zvolte **přidat**a klikněte na tlačítko **nová položka**.  
  
9. V **přidat novou položku - EmployeesListDefinition** dialogového okna rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
10. Zvolte **seznamu** šablony položky, název položky **zaměstnanci seznamu**a klikněte na tlačítko **přidat** tlačítko.  
  
     Zobrazí se Průvodce přizpůsobením Sharepointu  
  
11. Na **zvolit nastavení seznamu** stránce, ověřte následující nastavení a klikněte na tlačítko **Dokončit** tlačítka:  
  
    1. **Zaměstnanci seznamu** se zobrazí v **zadejte název chcete pro seznam zobrazit?** pole.  
  
    2. **Vytvořit seznam přizpůsobitelné podle:** je přepínač vybrán.  
  
    3. **Výchozí (prázdné)** je vybrán v **vytvořit seznam přizpůsobitelné podle:** seznamu.  
  
       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří položku seznamu zaměstnanci se sloupec názvu a jedné prázdnou instanci a otevře se Návrhář seznamu.  
  
12. V Návrháři List na **sloupce** , vyberte **zadejte název nového nebo existujícího sloupce** řádku a potom přidejte následující sloupce v **zobrazovaný název sloupce** seznamu:  
  
    1.  Křestní jméno  
  
    2.  Společnosti  
  
    3.  Telefon do zaměstnání  
  
    4.  E-mailu  
  
13. Uložte všechny soubory a pak zavřete návrháře seznamu.  
  
14. V **Průzkumníka řešení**, rozbalte **zaměstnanci seznamu** uzel a potom rozbalte **instanci seznamu zaměstnanci** podřízený uzel.  
  
15. V *Elements.xml* souboru, nahraďte výchozí XML v tomto souboru následující kód XML. Tato konfigurace XML se změní název seznamu **zaměstnanci** a přidá informace o zaměstnanec, který má s názvem Jim Hance.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Uložte a zavřete *Elements.xml* souboru.  
  
17. Otevřete místní nabídku pro projekt EmployeesListDefinition a klikněte na tlačítko **otevřít** nebo **vlastnosti**.  
  
     Otevře se Návrhář vlastnosti.  
  
18. Na **SharePoint** kartu, zrušte **automatické odvolání po ladění** zaškrtněte políčko a potom uložte vlastnosti.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>K nasazení definice seznamu a instance seznamu  
  
1.  V **Průzkumníka řešení**, zvolte **EmployeesListDefinition** uzel projektu.  
  
2.  V **vlastnosti** okno, ujistěte se, že **aktivní konfiguraci nasazení** je nastavena na **výchozí**.  
  
3.  Zvolte **F5** klíče, nebo na panelu nabídek zvolte **ladění** > **spustit ladění**.  
  
4.  Ověřte, že projekt vytvoří úspěšně, že webový prohlížeč otevře web služby SharePoint, který **uvádí** obsahuje novou položku v panelu Snadné spuštění **zaměstnanci** seznamu a které  **Zaměstnanci** seznam obsahuje položku pro Jim Hance.  
  
5.  Zavřete webový prohlížeč.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Znovu nasadit a upravit definici seznamu a instance seznamu  
  
1.  V projektu EmployeesListDefinition otevřete *Elements.xml* soubor, který je podřízeným prvkem **instanci seznamu zaměstnance** položky projektu.  
  
2.  Odeberte `Data` elementu a odeberte položku pro Jim Hance ze seznamu své podřízené objekty.  
  
     Po dokončení soubor musí obsahovat následující kód XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Uložte a zavřete *Elements.xml* souboru.  
  
4.  Otevřete místní nabídku **zaměstnanci seznamu** položky projektu a klikněte na tlačítko **otevřít** nebo **vlastnosti**.  
  
5.  V Návrháři seznamu zvolte **zobrazení** kartu.  
  
6.  V **vybrané sloupce** klikněte na položku **přílohy**a klikněte na tlačítko < klíč pro tento sloupec můžete přesunout **dostupných sloupců** seznamu.  
  
7.  Opakujte předchozí krok pro přesunutí **Telefon do zaměstnání** sloupec **vybrané sloupce** do seznamu **dostupných sloupců** seznamu.  
  
     Tato akce odebere z výchozího zobrazení těchto polí **zaměstnanci** seznam na Sharepointovém webu.  
  
8.  Spuštění ladění zvolením **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **spustit ladění**.  
  
9. Ověřte, že **konflikty při nasazení** zobrazí se dialogové okno.  
  
     Toto dialogové okno se zobrazí, když Visual Studio se pokusí o nasazení řešení (instance seznamu) na Sharepointový web, ke kterému již byla nasazena toto řešení. Toto dialogové okno nezobrazí při spuštění kroku nasazení upgradu později v tomto názorném postupu.  
  
10. V **konflikty při nasazení** dialogového okna zvolte **vyřešit automaticky** přepínač.  
  
     Visual Studio odstraní instanci seznamu na webu služby SharePoint, nasadí položky seznamu v projektu a potom se otevře web služby SharePoint.  
  
11. V **uvádí** části panelu Snadné spuštění zvolte **zaměstnanci** seznamu a potom ověřte následující podrobnosti:  
  
    -   **Přílohy** a **Telefon domů** sloupce nejsou zobrazeny v tomto zobrazení seznamu.  
  
    -   Seznam je prázdný. Při použití **výchozí** konfigurace nasazení k opětovnému nasazení řešení, **zaměstnanci** seznam byl nahrazen nový prázdný seznam ve vašem projektu.  
  
## <a name="test-the-deployment-step"></a>Testovací krok nasazení
 Nyní jste připraveni k testování krok upgradu nasazení. Nejprve přidejte položku do instance seznamu v Sharepointu. Změňte definici seznamu a seznam instancí, upgraduje je na webu služby SharePoint a potvrďte, že v kroku nasazení upgradu nepřepíše nová položka.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Chcete-li ručně přidat položku do seznamu  
  
1.  Na pásu karet na webu služby SharePoint v části **nástroje seznamu** , vyberte **položky** kartu.  
  
2.  V **nový** skupině, zvolte **nová položka**.  
  
     Jako alternativu můžete použít **přidat novou položku** odkaz v seznamu položek, samotného.  
  
3.  V **zaměstnanci – nová položka** okno v **Title** zadejte **Správce zařízení**.  
  
4.  V **křestní jméno** zadejte **Andy**.  
  
5.  V **společnosti** zadejte **Contoso**.  
  
6.  Zvolte **Uložit** tlačítko, ověřte, že se v seznamu objeví nová položka a pak zavřete webový prohlížeč.  
  
     Dále v tomto názorném postupu použijete tato položka k ověření, že v kroku nasazení upgradu nepřepíše obsah tohoto seznamu.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>K otestování krok nasazení upgradu  
  
1. V experimentální instanci sady Visual Studio v **Průzkumníka řešení**, otevřete místní nabídku **EmployeesListDefinition** uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
    Otevře se Návrhář/Editor vlastnosti.  
  
2. Na **SharePoint** kartu, nastavte **aktivní konfiguraci nasazení** vlastnost **upgradovat**.  
  
    Konfigurace vlastního nasazení obsahuje nový krok upgradu nasazení.  
  
3. Otevřete místní nabídku **zaměstnanci seznamu** položky projektu a klikněte na tlačítko **vlastnosti** nebo **otevřít**.  
  
    Otevře se Návrhář/Editor vlastnosti.  
  
4. Na **zobrazení** , vyberte **e-mailu** sloupce a klikněte na tlačítko **<** klíč přesune tento sloupec z **vybrané sloupce**do seznamu **dostupných sloupců** seznamu.  
  
    Tato akce odebere z výchozího zobrazení těchto polí **zaměstnanci** seznam na Sharepointovém webu.  
  
5. Spuštění ladění zvolením **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **spustit ladění**.  
  
6. Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `CanExecute` metody.  
  
7. Zvolte **F5** klíč znovu, nebo na panelu nabídek zvolte **ladění** > **pokračovat**.  
  
8. Ověřte, že kód zastaví na zarážce, kterou jste nastavili dříve v `Execute` metody.  
  
9. Zvolte **F5** klíče, nebo na panelu nabídek zvolte **ladění** > **pokračovat** koncového času.  
  
     Webový prohlížeč otevře web služby SharePoint.  
  
10. V **uvádí** části oblasti Snadné spuštění zvolte **zaměstnanci** seznamu a potom ověřte následující podrobnosti:  
  
    - Položka, kterou jste ručně přidali dříve (k Andy, Správce zařízení) je stále v seznamu.  
  
    - **Telefon do zaměstnání** a **e-mailovou adresu** sloupce nejsou zobrazeny v tomto zobrazení seznamu.  
  
      **Upgradovat** konfigurace nasazení upraví stávající **zaměstnanci** instance seznamu na webu služby SharePoint. Pokud jste použili **výchozí** konfigurace nasazení místo **upgradovat** konfiguraci by dojít ke konfliktu nasazení. Visual Studio by konflikt vyřešit tak, že nahradíte **zaměstnanci** seznamu a položkou Andy, Správce zařízení se odstraní.  
  
## <a name="clean-up-the-development-computer"></a>Vyčištění vývojovém počítači
 Po dokončení testování nasazení upgradu krok odebrat instanci seznamu a seznam definice z webu služby SharePoint a odeberte rozšíření krok nasazení z Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Chcete-li odebrat instanci seznamu z webu služby SharePoint  
  
1.  Otevřete **zaměstnanci** seznam na Sharepointovém webu, pokud ještě není otevřeno v seznamu.  
  
2.  Na pásu karet na webu služby SharePoint, zvolte **nástroje seznamu** kartu a klikněte na tlačítko **seznamu** kartu.  
  
3.  V **nastavení** skupině, zvolte **nastavení seznamu** položky.  
  
4.  V části **oprávnění a správa**, zvolte **odstranit tento seznam** příkazu, zvolte **OK** potvrďte, že chcete odeslat seznam do odpadkového koše a pak zavřete webu prohlížeč.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Chcete-li odebrat definici seznamu z webu služby SharePoint  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **sestavení** > **odvolat**.  
  
     Visual Studio odvolá definici seznamu z webu služby SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Chcete-li odinstalovat rozšíření  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **upgradovat kroku nasazení pro projekty SharePoint**a klikněte na tlačítko **odinstalovat** příkazu.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření a klikněte na tlačítko **restartovat nyní** dokončete odinstalaci.  
  
4.  Zavřete obě instance programu Visual Studio (experimentální instanci a instanci sady Visual Studio, ve kterém je otevřen UpgradeDeploymentStep řešení).  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření balení a nasazení SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
