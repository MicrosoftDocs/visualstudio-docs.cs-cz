---
title: Nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio | Microsoft Docs
description: Nasaďte rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio. Použijte projekty rozšíření sady Visual Studio (VSIX) k vytvoření balíčků VSIX.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c8b05b5cb74a28157436f95f01992515c716e6a
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672675"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio

Chcete-li nasadit rozšíření nástrojů služby SharePoint, vytvořte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX), který obsahuje sestavení rozšíření a všechny další soubory, které chcete distribuovat s příponou. VSIX balíček je komprimovaný soubor, který následuje Standard OPC (Open balení Conventions). Balíčky VSIX mají příponu *. vsix* .

Po vytvoření balíčku VSIX mohou jiní uživatelé spustit soubor. VSIX pro instalaci rozšíření. Když uživatel nainstaluje vaše rozšíření, všechny soubory se nainstalují do složky%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Chcete-li nasadit rozšíření, můžete nahrát balíček VSIX na web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , nebo můžete balíček distribuovat zákazníkům jinými způsoby, jako je například hostování balíčku ve sdílené síťové složce nebo na jiném webu.

Další informace o vytváření balíčků VSIX a jejich nasazení do [Visual Studio Marketplace](https://marketplace.visualstudio.com/)najdete v tématu dodávání [rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 VSIX balíček můžete vytvořit pomocí šablony **projektu VSIX** v aplikaci Visual Studio, nebo můžete vytvořit balíček VSIX ručně.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Použití projektů VSIX k vytváření balíčků VSIX

Můžete použít šablonu **projektu VSIX** poskytnutou sadou Visual Studio SDK k vytvoření balíčků VSIX pro rozšíření nástrojů služby SharePoint. Použití projektu VSIX přináší několik výhod ručního vytvoření balíčku VSIX:

- Sada Visual Studio automaticky generuje VSIX balíček při sestavování projektu. Úkoly, jako je přidání souborů nasazení do balíčku a vytvoření souboru. XML [Content_Types]. XML pro balíček, jsou pro vás hotové.

- Projekt VSIX můžete nakonfigurovat tak, aby zahrnoval výstup sestavení projektu rozšíření a další soubory, jako jsou šablony projektů a šablony položek, v balíčku VSIX.

Další informace o použití projektu VSIX naleznete v tématu [Šablona projektu VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Uspořádání projektů

Ve výchozím nastavení projekty VSIX generují pouze balíčky VSIX, nikoli sestavení. Proto obvykle neimplementujete rozšíření nástrojů služby SharePoint v projektu VSIX. Obecně pracujete s alespoň dvěma projekty:

- Projekt VSIX.

- Projekt knihovny tříd, který implementuje vaše rozšíření.

Také můžete pracovat s dalšími projekty pro určité typy rozšíření:

- Projekt knihovny tříd, který implementuje všechny příkazy služby SharePoint, které jsou používány vaším rozšířením. Návod, který ukazuje tento scénář, naleznete v tématu [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Šablona položky nebo projekt šablony projektu, které vytvoří šablonu položky nebo šablony projektu, pokud vaše rozšíření definuje nový typ položky projektu služby SharePoint. Návod, který ukazuje tento scénář, naleznete v tématu [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Projekt knihovny tříd, který implementuje vlastního průvodce pro šablonu položky nebo šablonu projektu, pokud vaše rozšíření obsahuje šablonu. Návod, který ukazuje tento scénář, naleznete v tématu [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Pokud zahrnete všechny projekty do stejného řešení sady Visual Studio, můžete upravit soubor source. extension. vsixmanifest v projektu VSIX tak, aby zahrnoval výstup sestavení projektů knihovny tříd.

### <a name="edit-the-vsix-manifest"></a>Upravit manifest VSIX

Je nutné upravit soubor source. extension. vsixmanifest v projektu VSIX, aby zahrnoval položky pro všechny položky, které chcete zahrnout do rozšíření. Když otevřete soubor source. extension. vsixmanifest z místní nabídky, soubor se zobrazí v návrháři, který poskytuje uživatelské rozhraní pro úpravy XML v souboru. Další informace naleznete v tématu [Návrhář manifestu VSIX](../extensibility/vsix-manifest-designer.md).

Do souboru source. extension. vsixmanifest je nutné přidat položky pro následující položky:

- Sestavení rozšíření.

- Sestavení, které implementuje všechny příkazy služby SharePoint, které jsou používány vaším rozšířením.

- Všechny šablony projektů nebo šablony položek, které jsou přidruženy k vašemu rozšíření.

- Vlastní průvodce pro šablonu, která je přidružená k vašemu rozšíření.

Následující postupy popisují, jak přidat položky do souboru. vsixmanifest pro každou z těchto položek.

#### <a name="to-include-the-extension-assembly"></a>Zahrnutí sestavení rozšíření

1. V projektu VSIX otevřete místní nabídku pro soubor source. extension. vsixmanifest a pak zvolte možnost **otevřít**.

     Soubor se otevře v návrháři.

2. Na kartě **assets (prostředky** ) Editoru klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

3. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

4. V seznamu **zdroj** proveďte jeden z následujících kroků:

    - Pokud je sestavení rozšíření sestaveno z projektu, který je ve stejném řešení jako projekt VSIX, vyberte **projekt v aktuálním řešení**. V seznamu **projekt** vyberte název projektu.

    - Pokud je sestavení rozšíření zahrnuto jako soubor v projektu, vyberte **soubor v systému souborů**. V seznamu **cesta** zadejte úplnou cestu k souboru sestavení rozšíření nebo použijte tlačítko **Procházet** a vyhledejte a vyberte soubor sestavení.

5. Klikněte na tlačítko **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Zahrnutí sestavení příkazu SharePoint

1. V projektu VSIX otevřete místní nabídku pro soubor source. extension. vsixmanifest a pak klikněte na tlačítko **otevřít** .

     Soubor se otevře v návrháři.

2. V části **assets** v Editoru klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

3. Do pole **typ** zadejte **SharePoint. Commands. v4**.

4. V seznamu **zdroj** proveďte jeden z následujících kroků:

    - Pokud je sestavení příkazu sestaveno z projektu, který je ve stejném řešení jako projekt VSIX, vyberte **projekt v aktuálním řešení**. V seznamu **projekt** vyberte název projektu.

    - Pokud je sestavení příkazu zahrnuto jako soubor v projektu, vyberte **soubor v systému souborů**. V seznamu **cesta** zadejte úplnou cestu k souboru sestavení rozšíření nebo použijte tlačítko **Procházet** a vyhledejte a vyberte soubor sestavení.

5. Klikněte na tlačítko **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Zahrnutí šablony, kterou vytvoříte

1. V projektu VSIX otevřete místní nabídku pro soubor source. extension. vsixmanifest a pak klikněte na tlačítko **otevřít** .

     Soubor se otevře v návrháři.

2. V části **assets** v Editoru klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

3. V seznamu **typ** vyberte **Microsoft. VisualStudio. ProjectTemplate** nebo **Microsoft. VisualStudio. ItemTemplate**.

4. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

5. V seznamu **projekt** zvolte název projektu a pak klikněte na tlačítko **OK** .

6. V **Průzkumník řešení** otevřete místní nabídku pro projekt šablony projektu nebo šablony položky a pak zvolte **Uvolnit projekt**.

7. Znovu otevřete místní nabídku uzlu projektu a pak zvolte **Upravit**_YourTemplateProjectName_**. csproj** nebo **Upravit**_YourTemplateProjectName_**. vbproj**.

8. `VSTemplate`V souboru projektu vyhledejte následující element.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Nahraďte tento prvek následujícím kódem XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Prvek určuje další složky v cestě, kde je vytvořena šablona projektu při sestavení projektu. Složky, které jsou zde uvedeny, zajistí, že šablona položky bude k dispozici pouze v případě, že zákazníci otevřou dialogové okno **Přidat nový projekt** , rozbalí uzel **služby SharePoint** a pak zvolí uzel **2010** .

10. Uložte soubor a zavřete ho.

11. V **Průzkumník řešení** otevřete místní nabídku pro projekt šablony projektu nebo šablony položky a pak zvolte možnost **znovu načíst projekt**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Chcete-li zahrnout šablonu, kterou vytvoříte ručně

1. V projektu VSIX přidejte do projektu novou složku, která bude obsahovat šablonu.

2. V této nové složce vytvořte následující podsložky a pak přidejte soubor šablony (. zip) do složky *ID národního prostředí* .

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID národního prostředí*

     *YourTemplateName*. zip

     Například pokud máte šablonu položky s názvem ContosoCustomAction.zip, která podporuje národní prostředí English (USA), může být celá cesta *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. V **Průzkumník řešení** vyberte soubor šablony (*YourTemplateName*. zip).

4. V okně **vlastnosti** nastavte vlastnost **Akce sestavení** na **obsah**.

5. Otevřete místní nabídku pro soubor source. extension. vsixmanifest a pak zvolte **otevřít**.

     Soubor se otevře v návrháři.

6. V části **assets** v Editoru klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

7. V seznamu **typ** vyberte **Microsoft. VisualStudio. ItemTemplate** nebo **Microsoft. VisualStudio. ProjectTemplate**.

8. V seznamu **zdroj** vyberte možnost **soubor v systému souborů**.

9. V poli **cesta** zadejte úplnou cestu k sestavení (například *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, nebo použijte tlačítko **Procházet** pro vyhledání a výběr sestavení a pak klikněte na tlačítko **OK** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Zahrnutí průvodce pro šablonu projektu nebo šablonu položky

1. V projektu VSIX otevřete místní nabídku pro soubor source. extension. vsixmanifest a pak zvolte možnost **otevřít**.

     Soubor se otevře v návrháři.

2. V části **assets** v Editoru klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

3. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. Assembly**.

4. V seznamu **zdroj** proveďte jeden z následujících kroků:

    - Pokud je sestavení průvodce sestaveno z projektu, který je ve stejném řešení jako projekt VSIX, vyberte **projekt v aktuálním řešení**. V seznamu **projekt** vyberte název projektu.

    - Pokud je sestavení průvodce zahrnuto jako soubor v projektu, vyberte **soubor v systému souborů**. Do pole **cesta** zadejte úplnou cestu k souboru sestavení nebo použijte tlačítko **Procházet** a vyhledejte a vyberte sestavení.

5. Klikněte na tlačítko **OK** .

### <a name="related-walkthroughs"></a>Související návody

V následující tabulce jsou uvedeny návody, které ukazují, jak použít projekt VSIX k nasazení různých typů rozšíření nástrojů služby SharePoint.

|Typ rozšíření|Související návody|
|--------------------|--------------------------|
|Rozšíření, které obsahuje pouze sestavení rozšíření|[Návod: rozšiřování typu položky projektu služby SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Návod: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Návod: volání do objektového modelu klienta služby SharePoint v rozšíření Průzkumník serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Rozšíření, které zahrnuje příkazy služby SharePoint|[Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Rozšíření, které obsahuje šablonu sady Visual Studio|[Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Rozšíření, které obsahuje Průvodce šablonou|[Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Vytvořit balíčky VSIX ručně

Chcete-li ručně vytvořit balíček VSIX pro rozšíření nástrojů služby SharePoint, proveďte následující kroky:

1. Vytvořte soubor Extension. vsixmanifest a soubor [Content_Types]. XML v nové složce. Další informace naleznete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. V Průzkumníku Windows klikněte pravým tlačítkem na složku, která obsahuje dva soubory XML, klikněte na Odeslat do a pak klikněte na Komprimovaná složka (ZIP). Přejmenujte výsledný soubor. zip na filename. vsix, kde filename je název redistribuovatelného souboru, který nainstaluje balíček.

3. Přidejte sestavení rozšíření do balíčku VSIX. Pokud vaše rozšíření obsahuje příkaz SharePoint, přidejte také sestavení, které implementuje příkaz služby SharePoint, do balíčku VSIX.

4. Upravte soubor Extension. vsixmanifest:

    - Do `Microsoft.VisualStudio.MefComponent` prvku přidejte element `Assets` a pak nastavte hodnotu nového prvku na relativní cestu sestavení, které implementuje vaše rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Pokud vaše rozšíření obsahuje příkaz SharePointu, který volá do objektového modelu serveru pro službu SharePoint, přidejte `Microsoft.VisualStudio.Assembly` element pod `Assets` element. Nastavte hodnotu nového prvku na relativní cestu sestavení, které implementuje příkaz služby SharePoint v balíčku VSIX. Další informace naleznete v tématu [Asset – element (schéma VSX)](/previous-versions/dd393737(v=vs.110)).

    - Pokud vaše rozšíření obsahuje šablonu projektu nebo šablonu položky, přidejte `ProjectTemplate` prvek nebo do `ItemTemplate` `Assets` prvku. Nastavte hodnotu nového prvku na relativní cestu ke složce, která obsahuje šablonu v balíčku VSIX. Další informace naleznete v tématu [ProjectTemplate Element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) a [ItemTemplate Element (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Pokud vaše rozšíření obsahuje vlastního průvodce pro šablonu projektu nebo šablonu položky, přidejte `Assembly` prvek pod `Assets` element. Nastavte hodnotu nového prvku na relativní cestu sestavení v balíčku VSIX a pak nastavte `AssemblyName` atribut na úplný název sestavení (včetně verze, jazykové verze a tokenu veřejného klíče). Další informace naleznete v tématu [dependency element (VSX Schema)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Příklad

Následující příklad ukazuje obsah souboru extension. vsixmanifest pro rozšíření nástrojů služby SharePoint. Rozšíření je implementováno v sestavení s názvem Contoso.ProjectExtension.dll. Rozšíření obsahuje sestavení příkazu SharePoint s názvem Contoso.ExtensionCommands.dll a šablonu položky ve složce s názvem **ItemTemplates** v balíčku VSIX. V tomto příkladu se předpokládá, že obě sestavení jsou ve stejné složce jako soubor Extension. vsixmanifest v balíčku VSIX.

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

## <a name="see-also"></a>Viz také

- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Rozšíření ladění pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)