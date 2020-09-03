---
title: Vytvoření vlastního kroku nasazení pro projekty SharePoint
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56fac2be1e73de5df9da8aa13e6631c4cc9d1022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015890"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint
  Když nasadíte projekt služby SharePoint, sada Visual Studio provede řadu kroků nasazení v určitém pořadí. Visual Studio obsahuje mnoho vestavěných kroků nasazení, ale můžete si také vytvořit vlastní.

 V tomto návodu vytvoříte vlastní krok nasazení, který bude upgradovat řešení na serveru, na kterém běží SharePoint. Visual Studio obsahuje integrované kroky nasazení pro mnoho úkolů, jako je odvolání nebo přidání řešení, ale nezahrnuje krok nasazení pro upgrade řešení. Ve výchozím nastavení, když nasazujete řešení služby SharePoint, Visual Studio nejprve odvolá řešení (Pokud již bylo nasazeno) a pak znovu nasadí celé řešení. Další informace o předdefinovaných krocích nasazení najdete v tématu [nasazení, publikování a Upgrade balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření rozšíření aplikace Visual Studio, které provádí dvě hlavní úlohy:

  - Rozšíření definuje vlastní krok nasazení pro upgrade řešení SharePoint.

  - Rozšíření vytvoří rozšíření projektu, které definuje novou konfiguraci nasazení, což je sada kroků nasazení, které jsou spouštěny pro daný projekt. Nová konfigurace nasazení zahrnuje krok vlastního nasazení a několik integrovaných kroků nasazení.

- Vytvořte dva vlastní příkazy SharePointu, které sestavení rozšíření volá. Příkazy služby SharePoint jsou metody, které mohou být volány sestaveními rozšíření pro použití rozhraní API v objektovém modelu serveru pro službu SharePoint. Další informace naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Sestavení balíčku rozšíření sady Visual Studio (VSIX) pro nasazení obou sestavení.

- Testování nového kroku nasazení.

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice Windows, SharePointu a sady Visual Studio.

- Sada Visual Studio SDK. Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení rozšíření. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Použití objektového modelu serveru pro službu SharePoint. Další informace naleznete v tématu [použití modelu objektu na straně serveru služby SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Řešení služby SharePoint. Další informace najdete v tématu [Přehled řešení](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- Upgradují se řešení SharePoint. Další informace najdete v tématu [Upgrade řešení](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit tři projekty:

- Projekt VSIX k vytvoření balíčku VSIX pro nasazení rozšíření.

- Projekt knihovny tříd, který implementuje rozšíření. Tento projekt musí být zaměřen na .NET Framework 4,5.

- Projekt knihovny tříd, který definuje vlastní příkazy služby SharePoint. Tento projekt musí být zaměřen na .NET Framework 3,5.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

    > [!NOTE]
    > Uzel **rozšiřitelnosti** je k dispozici pouze v případě, že instalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

4. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 4,5** .

5. Zvolte šablonu **projektu VSIX** , pojmenujte projekt **UpgradeDeploymentStep**a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **UpgradeDeploymentStep** do **Průzkumník řešení**.

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení UpgradeDeploymentStep, zvolte možnost **Přidat**a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak vyberte uzel **Windows** .

3. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 4,5** .

4. Zvolte šablonu projektu **Knihovna tříd** , pojmenujte projekt **DeploymentStepExtension**a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **DeploymentStepExtension** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

#### <a name="to-create-the-sharepoint-command-project"></a>Vytvoření projektu příkazu SharePoint

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení UpgradeDeploymentStep, zvolte možnost **Přidat**a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#** nebo **Visual Basic**a pak vyberte uzel **Windows** .

3. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 3,5** .

4. Zvolte šablonu projektu **Knihovna tříd** , pojmenujte projekt **SharePointCommands**a pak klikněte na tlačítko **OK** .

     Visual Studio přidá projekt **SharePointCommands** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurace projektů
 Předtím, než napíšete kód pro vytvoření vlastního kroku nasazení, je nutné přidat soubory kódu a odkazy na sestavení a je nutné nakonfigurovat projekty.

#### <a name="to-configure-the-deploymentstepextension-project"></a>Konfigurace projektu DeploymentStepExtension

1. V projektu **DeploymentStepExtension** přidejte dva soubory kódu, které mají následující názvy:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. Otevřete místní nabídku projektu DeploymentStepExtension a poté zvolte možnost **Přidat odkaz**.

3. Na kartě **rozhraní** zaškrtněte zaškrtávací políčko pro sestavení System. ComponentModel. složení.

4. Na kartě **rozšíření** zaškrtněte políčko pro sestavení Microsoft. VisualStudio. SharePoint a pak klikněte na tlačítko **OK** .

#### <a name="to-configure-the-sharepointcommands-project"></a>Konfigurace projektu SharePointCommands

1. V projektu **SharePointCommands** přidejte soubor kódu s názvem Commands.

2. V **Průzkumník řešení**otevřete místní nabídku uzlu projektu **SharePointCommands** a poté zvolte možnost **Přidat odkaz**.

3. Na kartě **rozšíření** zaškrtněte políčka u následujících sestavení a potom klikněte na tlačítko **OK** .

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

## <a name="define-the-custom-deployment-step"></a>Definování vlastního kroku nasazení
 Vytvořte třídu, která definuje krok upgradu nasazení. Pro definování kroku nasazení třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> rozhraní. Toto rozhraní implementujte vždy, když chcete definovat vlastní krok nasazení.

#### <a name="to-define-the-custom-deployment-step"></a>Definování vlastního kroku nasazení

1. V projektu **DeploymentStepExtension** otevřete soubor kódu UpgradeStep a vložte do něj následující kód.

    > [!NOTE]
    > Po přidání tohoto kódu dojde k chybě při kompilaci projektu, ale při přidávání kódu v pozdějších krocích zmizí.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Vytvoření konfigurace nasazení, která zahrnuje krok vlastního nasazení
 Vytvořte rozšíření projektu pro novou konfiguraci nasazení, které zahrnuje několik vestavěných kroků nasazení a nový krok nasazení upgradu. Vytvořením tohoto rozšíření pomůžete vývojářům služby SharePoint použít krok upgradu nasazení v projektech služby SharePoint.

 Chcete-li vytvořit konfiguraci nasazení, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní. Implementujte toto rozhraní vždy, když chcete vytvořit rozšíření projektu služby SharePoint.

#### <a name="to-create-the-deployment-configuration"></a>Vytvoření konfigurace nasazení

1. V projektu **DeploymentStepExtension** otevřete soubor kódu DeploymentConfigurationExtension a vložte do něj následující kód.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Vytvoření vlastních příkazů SharePointu
 Vytvořte dva vlastní příkazy, které volají do objektového modelu serveru pro službu SharePoint. Jeden příkaz určuje, zda je řešení již nasazeno; Druhý příkaz upgraduje řešení.

#### <a name="to-define-the-sharepoint-commands"></a>Definování příkazů služby SharePoint

1. V projektu **SharePointCommands** otevřete soubor kódu Commands a vložte do něj následující kód.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu se všechny kódy pro vlastní krok nasazení a příkazy služby SharePoint nyní nacházejí v projektech. Sestavujte je, abyste měli jistotu, že se zkompiluje bez chyb.

#### <a name="to-build-the-projects"></a>Sestavení projektů

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt **DeploymentStepExtension** a pak zvolte možnost **sestavit**.

2. Otevřete místní nabídku pro projekt **SharePointCommands** a pak zvolte možnost **sestavit**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Vytvoření balíčku VSIX pro nasazení rozšíření
 Chcete-li nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest v projektu VSIX. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX

1. V **Průzkumník řešení**v projektu **UpgradeDeploymentStep** otevřete místní nabídku pro soubor **source. extension. vsixmanifest** a pak zvolte **otevřít**.

     Visual Studio otevře soubor v editoru manifestu. Soubor source. extension. vsixmanifest je základem pro soubor Extension. vsixmanifest, který vyžaduje všechny balíčky VSIX. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Do pole **název produktu** zadejte **upgrade kroku nasazení pro projekty SharePoint**.

3. Do pole **Autor** zadejte **Contoso**.

4. Do pole **Popis** zadejte příkaz **poskytuje vlastní krok nasazení upgradu, který lze použít v projektech služby SharePoint**.

5. Na kartě **assets (prostředky** ) Editoru klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

6. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MefComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

8. V seznamu **projekt** zvolte možnost **DeploymentStepExtension**a pak klikněte na tlačítko **OK** .

9. V editoru manifestu znovu klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

10. V seznamu **typ** zadejte **SharePoint. Commands. v4**.

    > [!NOTE]
    > Tento prvek určuje vlastní rozšíření, které chcete zahrnout do rozšíření aplikace Visual Studio. Další informace naleznete v tématu [Asset – element (schéma VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

12. V seznamu **projekt** zvolte možnost **SharePointCommands**a pak klikněte na tlačítko **OK** .

13. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení**a pak se ujistěte, že se řešení zkompiluje bez chyb.

14. Ujistěte se, že výstupní složka sestavení pro projekt UpgradeDeploymentStep nyní obsahuje soubor UpgradeDeploymentStep. VSIX.

     Ve výchozím nastavení je výstupní složka sestavení.. Složka \bin\Debug ve složce, která obsahuje soubor projektu.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Příprava na test kroku nasazení upgradu
 Chcete-li otestovat krok nasazení upgradu, musíte nejprve nasadit ukázkové řešení na web služby SharePoint. Začněte laděním rozšíření v experimentální instanci sady Visual Studio. Pak vytvořte definici seznamu a instanci seznamu, které chcete použít k otestování kroku nasazení, a pak je nasaďte na web služby SharePoint. Dále upravte definici seznamu a instanci seznamu a znovu je nasaďte, abyste ukázali, jak výchozí proces nasazení Přepisuje řešení na webu služby SharePoint.

 Později v tomto návodu upravíte definici seznamu a instanci seznamu a potom je upgradujete na webu služby SharePoint.

#### <a name="to-start-debugging-the-extension"></a>Spuštění ladění rozšíření

1. Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení UpgradeDeploymentStep.

2. V projektu DeploymentStepExtension otevřete soubor kódu UpgradeStep a poté přidejte zarážku do prvního řádku kódu v `CanExecute` `Execute` metodách a.

3. Spusťte ladění tak, že vyberete klávesu **F5** nebo v řádku nabídek vyberete **ladění**  >  **Spustit ladění**.

4. Visual Studio nainstaluje rozšíření pro%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade nasazení služby SharePoint Projects\1.0 a spustí experimentální instanci sady Visual Studio. Otestujete krok nasazení upgradu v této instanci aplikace Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Vytvoření projektu služby SharePoint s definicí seznamu a instancí seznamu

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** uzel, rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

3. V horní části dialogového okna se ujistěte, že se v seznamu verzí .NET Framework zobrazí **.NET Framework 3,5** .

    Projekty pro [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] vyžadují tuto verzi .NET Framework.

4. V seznamu šablon projektu zvolte **projekt SharePoint 2010**, pojmenujte projekt **EmployeesListDefinition**a pak klikněte na tlačítko **OK** .

5. V **Průvodci vlastním nastavením služby SharePoint**zadejte adresu URL webu, který chcete použít pro ladění.

6. V části **co je úroveň vztahu důvěryhodnosti pro toto řešení služby SharePoint**vyberte tlačítko možnosti **nasadit jako řešení farmy** .

   > [!NOTE]
   > Krok nasazení upgradu nepodporuje řešení v izolovaném prostoru (sandbox).

7. Klikněte na tlačítko **Dokončit** .

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt EmployeesListDefinition.

8. Otevřete místní nabídku projektu EmployeesListDefinition, zvolte možnost **Přidat**a pak zvolte možnost **Nová položka**.

9. V dialogovém okně **Přidat novou položku – EmployeesListDefinition** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

10. Zvolte šablonu položky **seznam** , pojmenujte **seznam zaměstnanci**položky a pak klikněte na tlačítko **Přidat** .

     Zobrazí se Průvodce přizpůsobením SharePointu.

11. Na stránce **Vybrat nastavení seznamu** ověřte následující nastavení a pak klikněte na tlačítko **Dokončit** :

    1. **Seznam zaměstnanci** se zobrazí v poli **jaký název chcete zobrazit pro váš seznam?** .

    2. Je zvolen přepínač **vytvořit přizpůsobitelný seznam na základě:** .

    3. V seznamu **vytvořit přizpůsobitelný seznam na základě:** je zvolena možnost **výchozí (prázdná)** .

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří položku seznamu zaměstnanci se sloupcem název a jedinou prázdnou instancí a otevře se Návrhář seznamu.

12. V Návrháři seznamu na kartě **sloupce** vyberte řádek **Zadejte nový nebo existující název sloupce** a přidejte následující sloupce do seznamu **Zobrazovaný název sloupce** :

    1. Jméno

    2. Společnost

    3. Telefon do zaměstnání

    4. E-Mail

13. Uložte všechny soubory a pak zavřete návrháře seznamu.

14. V **Průzkumník řešení**rozbalte uzel **seznam zaměstnanci** a potom rozbalte uzel **seznam zaměstnanců instance** podřízeného uzlu.

15. V souboru *Elements.xml* nahraďte výchozí XML v tomto souboru následujícím kódem XML. Tento kód XML změní název seznamu na **Employees** a přidá informace pro zaměstnance s názvem jim Hance.

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

16. Uložte a zavřete soubor *Elements.xml* .

17. Otevřete místní nabídku pro projekt EmployeesListDefinition a pak zvolte možnost **otevřít** nebo **vlastnosti**.

     Otevře se Návrhář vlastností.

18. Na kartě **SharePoint** zrušte zaškrtnutí políčka **automaticky odvolat po ladění** a pak vlastnosti uložte.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Nasazení definice seznamu a instance seznamu

1. V **Průzkumník řešení**vyberte uzel projektu **EmployeesListDefinition** .

2. V okně **vlastnosti** zkontrolujte, zda je vlastnost **Konfigurace aktivního nasazení** nastavena na hodnotu **výchozí**.

3. Klikněte na klávesu **F5** nebo na panelu nabídek vyberte **ladění**  >  **Spustit ladění**.

4. Ověřte, že se projekt úspěšně sestavil, že se webový prohlížeč otevře na webu služby SharePoint, že položka **seznamy** na panelu snadného spuštění obsahuje seznam nový **zaměstnanci** a že seznam **zaměstnanci** obsahuje položku pro jim Hance.

5. Zavřete webový prohlížeč.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Úprava definice seznamu a instance seznamu a jejich opětovné nasazení

1. V projektu EmployeesListDefinition otevřete *Elements.xml* soubor, který je podřízenou položkou položky projektu **instance seznamu zaměstnanců** .

2. Odeberte `Data` prvek a jeho podřízené položky k odebrání položky jim Hance ze seznamu.

     Až skončíte, soubor by měl obsahovat následující kód XML.

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

3. Uložte a zavřete soubor *Elements.xml* .

4. Otevřete místní nabídku položky projektu **seznam zaměstnanců** a pak zvolte možnost **otevřít** nebo **vlastnosti**.

5. V Návrháři seznamu vyberte kartu **zobrazení** .

6. V seznamu **vybrané sloupce** zvolte možnost **přílohy**a potom vyberte klíč < pro přesunutí tohoto sloupce do seznamu **Dostupné sloupce** .

7. Opakujte předchozí krok pro přesun sloupce **obchodní telefon** ze seznamu **vybrané sloupce** do seznamu **Dostupné sloupce** .

     Tato akce odebere tato pole z výchozího zobrazení seznamu **zaměstnanci** na webu služby SharePoint.

8. Spusťte ladění tak, že vyberete klávesu **F5** nebo v řádku nabídek vyberete **ladění**  >  **Spustit ladění**.

9. Ověřte, že se zobrazí dialogové okno **konflikty nasazení** .

     Toto dialogové okno se zobrazí, když se aplikace Visual Studio pokusí nasadit řešení (instanci seznamu) na web služby SharePoint, na který bylo toto řešení již nasazeno. Toto dialogové okno se nezobrazí při spuštění kroku upgradu nasazení dále v tomto návodu.

10. V dialogovém okně **konflikty nasazení** klikněte na přepínač **vyřešit automaticky** .

     Visual Studio odstraní instanci seznamu na webu služby SharePoint, nasadí položku seznamu v projektu a pak otevře web služby SharePoint.

11. V části **seznamy** na panelu snadného spuštění zvolte seznam **zaměstnanci** a pak ověřte následující údaje:

    - V tomto zobrazení seznamu se nezobrazí sloupce **přílohy** a **Domů telefon** .

    - Seznam je prázdný. Pokud jste k opětovnému nasazení řešení použili konfiguraci **výchozího** nasazení, seznam **zaměstnanci** byl nahrazen novým prázdným seznamem v projektu.

## <a name="test-the-deployment-step"></a>Testování kroku nasazení
 Nyní jste připraveni otestovat krok nasazení upgradu. Nejdřív přidejte položku do instance seznamu na SharePointu. Pak změňte definici seznamu a instanci seznamu, upgradujte je na webu služby SharePoint a potvrďte, že krok nasazení upgradu nepřepisuje novou položku.

#### <a name="to-manually-add-an-item-to-the-list"></a>Ruční přidání položky do seznamu

1. Na pásu karet na webu služby SharePoint klikněte na kartě **Nástroje seznamu** na kartu **položky** .

2. V **nové** skupině vyberte možnost **Nová položka**.

     Alternativně můžete zvolit odkaz **Přidat novou položku** v samotném seznamu položek.

3. V okně **zaměstnanci – nová položka** v poli **název** zadejte **Správce zařízení**.

4. Do pole **jméno** zadejte **Andy**.

5. Do pole **Společnost** zadejte **Contoso**.

6. Klikněte na tlačítko **Uložit** , ověřte, zda se nová položka zobrazí v seznamu, a poté zavřete webový prohlížeč.

     Později v tomto návodu použijete tuto položku k ověření, že krok nasazení upgradu nepřepisuje obsah tohoto seznamu.

#### <a name="to-test-the-upgrade-deployment-step"></a>Testování kroku nasazení upgradu

1. V experimentální instanci aplikace Visual Studio v **Průzkumník řešení**otevřete místní nabídku uzlu projektu **EmployeesListDefinition** a poté zvolte možnost **vlastnosti**.

    Otevře se Editor vlastností nebo Návrhář.

2. Na kartě **SharePoint** nastavte vlastnost **Konfigurace aktivního nasazení** na **upgradovat**.

    Tato vlastní konfigurace nasazení zahrnuje nový krok nasazení upgradu.

3. Otevřete místní nabídku položky projektu **seznam zaměstnanců** a pak zvolte možnost **vlastnosti** nebo **otevřít**.

    Otevře se Editor vlastností nebo Návrhář.

4. Na kartě **zobrazení** vyberte sloupec **E-mail** a potom zvolte **<** klíč pro přesunutí tohoto sloupce ze seznamu **vybrané sloupce** do seznamu **Dostupné sloupce** .

    Tato akce odebere tato pole z výchozího zobrazení seznamu **zaměstnanci** na webu služby SharePoint.

5. Spusťte ladění tak, že vyberete klávesu **F5** nebo v řádku nabídek vyberete **ladění**  >  **Spustit ladění**.

6. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `CanExecute` metodě.

7. Znovu stiskněte klávesu **F5** nebo v řádku nabídek vyberte možnost **ladit**  >  **pokračovat**.

8. Ověřte, že se kód zastaví na zarážce, kterou jste nastavili dříve v `Execute` metodě.

9. Klikněte na klávesu **F5** nebo na panelu nabídek vyberte možnost **ladit**  >  **pokračovat** v konečném čase.

     Webový prohlížeč otevře web služby SharePoint.

10. V části **seznamy** v oblasti snadné spuštění zvolte seznam **zaměstnanci** a pak ověřte následující údaje:

    - Položka, kterou jste ručně přidali dříve (pro Andy, Správce zařízení), je stále v seznamu.

    - V tomto zobrazení seznamu se nezobrazí sloupce **obchodní telefon** a **e-mailová adresa** .

      Konfigurace nasazení **upgradu** upravuje existující instanci seznamu **zaměstnanci** na webu služby SharePoint. Pokud jste místo konfigurace **upgradu** použili **výchozí** konfiguraci nasazení, narazíte ke konfliktu nasazení. Visual Studio by vyřešilo konflikt nahrazením seznamu **zaměstnanci** a položky pro Andy, Správce zařízení, se odstraní.

## <a name="clean-up-the-development-computer"></a>Vyčištění vývojového počítače
 Po dokončení testování kroku nasazení upgradu odeberte instanci seznamu a definici seznamu z webu služby SharePoint a odeberte rozšíření kroku nasazení ze sady Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Odebrání instance seznamu z webu služby SharePoint

1. Otevřete seznam **zaměstnanci** na webu služby SharePoint, pokud seznam ještě není otevřený.

2. Na pásu karet na webu služby SharePoint zvolte kartu **Nástroje seznamu** a poté zvolte kartu **seznam** .

3. Ve skupině **Nastavení** vyberte položku **Nastavení seznamu** .

4. V části **oprávnění a Správa**zvolte příkaz **Odstranit tento seznam** , zvolte **OK** , abyste potvrdili, že chcete odeslat seznam do koše a pak zavřete webový prohlížeč.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Odebrání definice seznamu z webu služby SharePoint

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte možnost **sestavení**  >  **odvolání**.

     Visual Studio odvolá definici seznamu z webu služby SharePoint.

#### <a name="to-uninstall-the-extension"></a>Odinstalace rozšíření

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte **upgradovat krok nasazení pro projekty SharePoint**a pak zvolte příkaz **odinstalovat** .

3. V dialogovém okně, které se zobrazí, kliknutím na **Ano** potvrďte, že chcete rozšíření odinstalovat, a kliknutím na **restartovat nyní** dokončete odinstalaci.

4. Zavřete obě instance sady Visual Studio (experimentální instance a instance sady Visual Studio, ve které je otevřeno řešení UpgradeDeploymentStep).

## <a name="see-also"></a>Viz také
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
