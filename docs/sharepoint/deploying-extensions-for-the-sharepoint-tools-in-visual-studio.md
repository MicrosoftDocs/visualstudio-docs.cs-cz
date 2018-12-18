---
title: Nasazování rozšíření pro nástroje služby SharePoint v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3bf20f945c40dd963820b1bf3f4032a2dd517ca
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295966"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Nasazení rozšíření pro nástroje služby SharePoint v sadě Visual Studio

Pokud chcete nasadit rozšíření nástrojů služby SharePoint, vytvořit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček extension (VSIX), který obsahuje sestavení rozšíření a další soubory, které chcete distribuovat s příponou. Balíček VSIX je komprimovaný soubor, který dodržuje standardní konvence Open Packaging (OPC). Balíčků VSIX *VSIX* rozšíření.

Po vytvoření balíčku VSIX ostatní uživatelé mohou spouštět souboru .vsix, chcete-li nainstalovat rozšíření. Když uživatel nainstaluje rozšíření, nainstaluje se všechny soubory ke složce %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. K nasazení rozšíření, můžete nahrát balíčku VSIX k [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webové stránky, nebo můžete distribuovat balíček vašim zákazníkům jiným způsobem, jako je například hostování balíčku ve sdílené síťové složce nebo jiný webový server.

Další informace o vytváření balíčků VSIX a jejich nasazení [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), naleznete v tématu [přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Můžete vytvořit pomocí balíčku VSIX **projekt VSIX** balíčku VSIX šablony v sadě Visual Studio, nebo můžete vytvořit ručně.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Použít projektů VSIX k vytváření balíčků VSIX

Můžete použít **projekt VSIX** šablony, které poskytuje Visual Studio SDK k vytváření balíčků VSIX pro rozšíření nástrojů SharePoint. Použití projektu VSIX nabízí několik výhod v porovnání s ruční vytvoření balíčku VSIX:

-   Visual Studio automaticky vygeneruje VSIX balíček při vytváření projektu. Úlohy, jako je přidání soubory nasazení balíčku a vytvoření souboru [Content_Types] .xml pro balíček jsou provede za vás.

-   Můžete nakonfigurovat projekt VSIX pro zahrnutí výstupu sestavení projektu rozšíření a další soubory, jako jsou šablony projektů a šablon položek v balíčku souboru VSIX.

Další informace o použití projektu VSIX, naleznete v tématu [šablonou projektu VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Uspořádání projektů

Ve výchozím nastavení generovat jenom projekty VSIX balíčků VSIX, není sestavení. Proto je obvykle neimplementují rozšíření nástrojů SharePoint v projektu VSIX. Obecně pracovat s alespoň dva projekty:

-   Projekt VSIX.

-   Projekt knihovny tříd, který implementuje rozšíření.

Můžete také pracovat i s další projekty pro některé typy rozšíření:

-   Projekt knihovny tříd, který implementuje všechny příkazy služby SharePoint, které jsou používány rozšíření. Postup, který ukazuje tento scénář, najdete v části [návod: rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

-   Šabloně položky nebo šablony projektu projekt, který vytvoří šablonu položky nebo šablony projektu, pokud vaše rozšíření definuje nový typ položky projektu služby SharePoint. Postup, který ukazuje tento scénář, najdete v části [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

-   Projekt knihovny tříd, který implementuje vlastního průvodce šablony položky nebo šablony projektu, pokud vaše rozšíření obsahuje šablony. Postup, který ukazuje tento scénář, najdete v části [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Pokud zahrnete všechny projekty ve stejném řešení sady Visual Studio, můžete upravit soubor source.extension.vsixmanifest v projektu VSIX pro zahrnutí výstupu sestavení projekty knihovny tříd.

### <a name="edit-the-vsix-manifest"></a>Upravit VSIX manifest

Je nutné upravit soubor source.extension.vsixmanifest v projektu VSIX a zahrnují položky pro všechny položky, které chcete zahrnout do rozšíření. Při otevření souboru source.extension.vsixmanifest z jeho místní nabídku souboru se zobrazí v návrháři, který poskytuje uživatelské rozhraní pro úpravy XML v souboru. Další informace najdete v tématu [Návrhář manifestu VSIX](../extensibility/vsix-manifest-designer.md).

Je nutné přidat položky do souboru source.extension.vsixmanifest pro následující položky:

-   Rozšíření sestavení.

-   Sestavení, který implementuje všechny příkazy služby SharePoint, které jsou používány rozšíření.

-   Šablony projektů nebo šablony položek, které jsou spojeny s rozšíření.

-   Vlastní Průvodce pro šablony, který je přidružený k rozšíření.

Následující postupy popisují, jak přidat položky do souboru .vsixmanifest pro každou z těchto položek.

#### <a name="to-include-the-extension-assembly"></a>Zahrnout sestavení rozšíření

1.  V projektu VSIX, otevřete místní nabídku pro soubor source.extension.vsixmanifest a klikněte na tlačítko **otevřete**.

     Soubor se otevře v Návrháři

2.  Na **prostředky** kartu Editor, zvolte **nový** tlačítko.

     **Přidat nové aktivum** zobrazí se dialogové okno.

3.  V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.

4.  V **zdroj** seznamu, proveďte jednu z následujících kroků:

    -   Pokud se sestavení rozšíření je sestaven z projektu, který je ve stejném řešení jako projekt VSIX, zvolte **projekt v aktuálním řešení**. V **projektu** seznamu, vyberte název projektu.

    -   Pokud je sestavení rozšíření zahrnut jako soubor ve vašem projektu, zvolte **soubor v systému souborů**. V **cesta** seznamu, zadejte úplnou cestu k souboru sestavení rozšíření nebo použít **Procházet** tlačítko a vyhledejte a vyberte soubor sestavení.

5.  Zvolte **OK** tlačítko.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Zahrnout sestavení příkazu SharePoint

1.  V projektu VSIX, otevřete místní nabídku pro soubor source.extension.vsixmanifest a klikněte na tlačítko **otevřete** tlačítko.

     Soubor se otevře v návrháři.

2.  V **prostředky** části editoru, zvolte **nový** tlačítko.

     **Přidat nové aktivum** zobrazí se dialogové okno.

3.  V **typ** zadejte **SharePoint.Commands.v4**.

4.  V **zdroj** seznamu, proveďte jednu z následujících kroků:

    -   Pokud příkaz sestavení je sestaven z projektu, který je ve stejném řešení jako projekt VSIX, zvolte **projekt v aktuálním řešení**. V **projektu** seznamu, vyberte název projektu.

    -   Pokud příkaz sestavení je zahrnut jako soubor ve vašem projektu, zvolte **soubor v systému souborů**. V **cesta** seznamu, zadejte úplnou cestu k souboru sestavení rozšíření nebo použít **Procházet** tlačítko a vyhledejte a vyberte soubor sestavení.

5.  Zvolte **OK** tlačítko.

#### <a name="to-include-a-template-that-you-create"></a>Zahrnout šablonu, kterou vytvoříte

1.  V projektu VSIX, otevřete místní nabídku pro soubor source.extension.vsixmanifest a klikněte na tlačítko **otevřete** tlačítko.

     Soubor se otevře v návrháři.

2.  V **prostředky** části editoru, zvolte **nový** tlačítko.

     **Přidat nové aktivum** zobrazí se dialogové okno.

3.  V **typ** klikněte na položku **Microsoft.VisualStudio.ProjectTemplate** nebo **Microsoft.VisualStudio.ItemTemplate**.

4.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.

5.  V **projektu** seznamu, vyberte název projektu a klikněte na tlačítko **OK** tlačítko.

6.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt šablony nebo šablony položek projektu a klikněte na tlačítko **uvolnit projekt**.

7.  Znovu otevřete místní nabídku pro uzel projektu a klikněte na tlačítko **upravit**_YourTemplateProjectName_**.csproj** nebo **upravit**  _YourTemplateProjectName_**.vbproj**.

8.  Vyhledejte následující `VSTemplate` element v souboru projektu.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Tento prvek nahraďte následující kód XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Prvek určuje další složky v cestě, pod kterým šabloně projektu je vytvořen při sestavení projektu. Složky tady zadané, ujistěte se, že šablonu položky bude k dispozici pouze v případě, že zákazníci otevřít **přidat nový projekt** dialogového okna rozbalte **SharePoint** uzel a klikněte na tlačítko **2010**  uzlu.

10. Soubor uložte a zavřete.

11. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt šablony nebo šablony položek projektu a klikněte na tlačítko **znovu načíst projekt**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Zahrnout šablony, které ručně vytvoříte

1.  V projektu VSIX přidejte do projektu tak, aby šablona obsahovala novou složku.

2.  V této nové složky, vytvořte následující podsložky a pak přidejte soubor šablony (.zip), který má *ID národního prostředí* složky.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID národního prostředí*

     *YourTemplateName*ZIP

     Například pokud máte šablony položky s názvem ContosoCustomAction.zip, který podporuje národní prostředí Angličtina (Spojené státy), úplná cesta může být *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3.  V **Průzkumníka řešení**, zvolte soubor šablony (*YourTemplateName*.zip).

4.  V **vlastnosti** okno, nastaveno **akce sestavení** vlastnost **obsahu**.

5.  Otevřete místní nabídku pro soubor source.extension.vsixmanifest a klikněte na tlačítko **otevřít**.

     Soubor se otevře v návrháři.

6.  V **prostředky** části editoru, zvolte **nový** tlačítko.

     **Přidat nové aktivum** zobrazí se dialogové okno.

7.  V **typ** klikněte na položku **Microsoft.VisualStudio.ItemTemplate** nebo **Microsoft.VisualStudio.ProjectTemplate**.

8.  V **zdroj** klikněte na položku **soubor v systému souborů**.

9. V **cesta** zadejte úplnou cestu k sestavení (například *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, nebo použijte **Procházet**tlačítko vyhledejte a vyberte sestavení a klikněte na tlačítko **OK** tlačítko.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Zahrnout Průvodce pro šablony projektu nebo šablony položek

1.  V projektu VSIX, otevřete místní nabídku pro soubor source.extension.vsixmanifest a klikněte na tlačítko **otevřete**.

     Soubor se otevře v návrháři.

2.  V **prostředky** části editoru, zvolte **nový** tlačítko.

     **Přidat nové aktivum** zobrazí se dialogové okno.

3.  V **typ** klikněte na položku **Microsoft.VisualStudio.Assembly**.

4.  V **zdroj** seznamu, proveďte jednu z následujících kroků:

    -   Pokud Průvodce sestavení je sestaven z projektu, který je ve stejném řešení jako projekt VSIX, zvolte **projekt v aktuálním řešení**. V **projektu** seznamu, vyberte název projektu.

    -   Pokud Průvodce sestavení je zahrnut jako soubor ve vašem projektu, zvolte **soubor v systému souborů**. V **cesta** pole, zadejte úplnou cestu k souboru sestavení nebo použít **Procházet** tlačítko a vyhledejte a vyberte sestavení.

5.  Zvolte **OK** tlačítko.

### <a name="related-walkthroughs"></a>Související návody

Následující tabulka uvádí postupy, které popisují způsob použití projektu VSIX nasadit různé typy rozšíření nástrojů služby SharePoint.

|Typ rozšíření|Související návody|
|--------------------|--------------------------|
|Rozšíření, která zahrnuje pouze sestavení rozšíření|[Návod: Rozšíření typu položky projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Návod: Vytváření rozšíření projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Návod: Volání do objektového modelu klienta SharePoint v rozšíření Průzkumníka serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Rozšíření, které obsahuje příkazy pro SharePoint|[Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Návod: Rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Rozšíření, které obsahuje šablony sady Visual Studio|[Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Rozšíření, které obsahuje Průvodce šablony|[Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Ruční vytvoření balíčků VSIX

Pokud chcete ručně vytvořit balíčku VSIX pro rozšíření nástrojů služby SharePoint, proveďte následující kroky:

1.  V nové složce vytvořte soubor extension.vsixmanifest a souboru [Content_Types] .xml. Další informace najdete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2.  V Průzkumníku Windows klikněte pravým tlačítkem na složku, která obsahuje příslušné dva soubory XML, klikněte na tlačítko Odeslat a pak klikněte na složku komprimované. Přejmenujte výsledný soubor ZIP na Filename.vsix, kde název_souboru je název redistribuovatelného souboru, který nainstaluje balíček.

3.  Rozšíření sestavení přidáte do balíčku VSIX. Pokud vaše rozšíření obsahuje příkaz SharePoint, přidejte také sestavení, který implementuje příkaz SharePoint balíčku VSIX.

4.  Upravte soubor extension.vsixmanifest:

    -   Přidat `Microsoft.VisualStudio.MefComponent` element v rámci `Assets` element a pak nastavte hodnotu nový prvek do relativní cestu sestavení, který implementuje rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    -   Pokud vaše rozšíření obsahuje příkaz SharePoint, která volá do objektového modelu serveru pro službu SharePoint, přidejte `Microsoft.VisualStudio.Assembly` element v rámci `Assets` elementu. Nastavte hodnotu nového elementu na relativní cestu sestavení, který implementuje příkaz serveru SharePoint v balíčku souboru VSIX. Další informace najdete v tématu [Asset – Element (VSX schéma)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    -   Pokud vaše rozšíření obsahuje šablonu projektu nebo šablony položky, přidejte `ProjectTemplate` nebo `ItemTemplate` element v rámci `Assets` elementu. Nastavte hodnotu nový prvek do relativní cesty ke složce, která obsahuje šablonu v balíčku souboru VSIX. Další informace najdete v tématu [ProjectTemplate – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) a [ItemTemplate – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    -   Pokud vaše rozšíření obsahuje vlastního průvodce šablony projektu nebo šablony položky, přidejte `Assembly` element v rámci `Assets` elementu. Nastavte hodnotu nového elementu na relativní cesta k sestavení v balíčku souboru VSIX a potom nastavte `AssemblyName` atribut sestavení úplný název (včetně verze, jazykovou verzi a token veřejného klíče). Další informace najdete v tématu [Element Dependency (schéma VSX)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Příklad

Následující příklad ukazuje obsah souboru extension.vsixmanifest pro rozšíření nástrojů služby SharePoint. Rozšíření je implementované v sestavení, který je pojmenován Contoso.ProjectExtension.dll. Toto rozšíření obsahuje příkaz sestavení SharePoint s názvem Contoso.ExtensionCommands.dll a šablonu položky v rámci složky s názvem **šablon položek** v balíčku souboru VSIX. Tento příklad předpokládá, že jsou obě sestavení ve stejné složce jako soubor extension.vsixmanifest v balíčku souboru VSIX.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Viz také:

- [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Ladění rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
