---
title: Lokalizační příkazy nabídky | Dokumenty společnosti Microsoft
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702950"
---
# <a name="localize-menu-commands"></a>Lokalizovat příkazy nabídky

Lokalizovaný text pro příkazy nabídek a panelu nástrojů můžete zadat vytvořením lokalizovaných souborů *.vsct* a lokalizovaných souborů *Resx* pro váš balíček VSPackage a následným aktualizací souborů projektu tak, aby zahrnovaly změny.

Informace o lokalizaci instalace naleznete v [tématu Localize VSIX packages](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalizovat názvy příkazů

V položkách VSPackages jsou příkazy nabídek a tlačítka panelu nástrojů definovány v souboru *.vsct.*

1. V **Průzkumníku řešení**změňte název souboru *.vsct* ze *souboru filename.vsct* na *filename.en-US.vsct*.

2. Vytvořte kopii *souboru filename.en-US.vsct* pro každý lokalizovaný jazyk.

    Pojmenujte každý *název souboru kopie.{ Národní prostředí}.vsct*, kde *{Locale}* je konkrétní název jazykové verze. Seznam hodnot názvů jazykové verze naleznete v tématu [ID národního prostředí přiřazená společností Microsoft](/windows/uwp/publish/supported-languages).

    Tento *název souboru. Soubory locale.vsct* budou obsahovat lokalizovaný text nabídky pro váš balíček.

3. Otevřete každý *název souboru. Soubor Locale.vsct* pro lokalizaci textu.

   1. Upravte hodnoty elementu [ButtonText](../extensibility/buttontext-element.md) podle potřeby pro daný jazyk.

   2. Pokud zadáte lokalizované ikony, upravte hodnoty [Bitmap](../extensibility/bitmap-element.md) tak, aby ukazovaly na cílové soubory.

      Následující příklad ukazuje text tlačítka angličtina a španělština pro příkaz otevřít okno nástroje Průzkumník a family tree.

      [*FamilyTree.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Lokalizovat další textové prostředky

Textové prostředky jiné než názvy příkazů jsou definovány v souborech prostředků (*Resx*).

1. Přejmenujte *soubor VSPackage.resx* na *Soubor VSPackage.en-US.resx*.

2. Vytvořte kopii souboru *VSPackage.en-US.resx* pro každý lokalizovaný jazyk.

     Pojmenujte každou kopii *VSPackage.{ Národní prostředí}.resx*, kde *{Locale}* je konkrétní název jazykové verze.

3. Přejmenujte *soubor Resources.resx* na *Resources.en-US.resx*.

4. Vytvořte kopii souboru *Resources.en-US.resx* pro každý lokalizovaný jazyk.

     Pojmenujte každou kopii *Zdroje.{ Národní prostředí}.resx*, kde *{Locale}* je konkrétní název jazykové verze.

5. Otevřete každý soubor *.resx* a upravte hodnoty řetězce podle potřeby pro konkrétní jazyk a jazykovou verzi. Následující příklad ukazuje lokalizovanou definici prostředků pro záhlaví okna nástroje.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Začlenění lokalizovaných zdrojů do projektu

Je nutné upravit *soubor assemblyinfo.cs* a soubor projektu začlenit lokalizované prostředky.

1. V uzlu **Vlastnosti** v **Průzkumníku řešení**otevřete *assemblyinfo.cs* nebo *assemblyinfo.vb* v editoru.

2. Přidejte následující položku.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Tím nastavíte americkou angličtinu jako výchozí jazyk.

3. Uvolnit projekt.

4. Otevřete soubor projektu v editoru.

5. V kořenovém `Project` `PropertyGroup` prvku přidejte `UICulture` prvek s prvkem, který odpovídá výchozímu jazyku.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Tím nastavíte americkou angličtinu jako výchozí jazykovou verzi rozhraní pro ovládací prvky WPF (Windows Presentation Foundation).

6. Vyhledejte `ItemGroup` prvek, `EmbeddedResource` který obsahuje prvky.

7. V `EmbeddedResource` elementu, který volá *VSPackage.en-US.resx* `LogicalName` , nahraďte `VSPackage.en-US.Resources` `ManifestResourceName` prvek elementem, který je nastaven na , takto:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Pro každý lokalizovaný `EmbeddedResource` jazyk `VsPackage.en-US`zkopírujte prvek pro aplikaci a nastavte element **Include** atribut a **LogicalName** kopie do cílového národního prostředí.

9. Ke každému `VSCTCompile` lokalizovanému `ResourceName` prvku přidejte prvek, který odkazuje na `Menus.ctmenu`, jak je znázorněno v následujícím příkladu:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Uložte soubor projektu a znovu načtěte projekt.

11. Sestavte projekt.

     Tím se vytvoří hlavní sestavení a sestavení prostředků pro každý jazyk. Informace o lokalizaci procesu nasazení naleznete v [tématu Localize VSIX packages](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Viz také

- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Globalizace a lokalizovat aplikace](../ide/globalizing-and-localizing-applications.md)
