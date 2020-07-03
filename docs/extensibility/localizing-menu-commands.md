---
title: Lokalizace příkazů nabídky | Microsoft Docs
ms.date: 10/08/2019
ms.topic: how-to
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
ms.openlocfilehash: 1c1c158fd689cbcae18fec5d3306e6d6fadb169f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904557"
---
# <a name="localize-menu-commands"></a>Příkazy nabídky lokalizace

Lokalizovaný text pro příkazy nabídky a panelu nástrojů můžete poskytnout vytvořením lokalizovaných souborů *. vsct* a lokalizovaných souborů *. resx* pro svůj VSPackage a následnou aktualizací souborů projektu pro zahrnutí změn.

Informace o lokalizaci instalačního prostředí naleznete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalizovat názvy příkazů

V rozhraních VSPackage jsou příkazy nabídky a tlačítka panelu nástrojů definovány v souboru *. vsct* .

1. V **Průzkumník řešení**změňte název souboru *. vsct* z *filename. vsct* na *filename. en-US. vsct*.

2. Vytvořte kopii *filename. en-US. vsct* pro každý lokalizovaný jazyk.

    Název každého *souboru kopie. { Locale}. vsct*, kde *{locale}* je konkrétní název jazykové verze. Seznam hodnot názvů jazykových verzí najdete v tématu [ID národního prostředí přiřazené společností Microsoft](/windows/uwp/publish/supported-languages).

    Tyto *názvy souborů. Soubory locale. vsct* budou obsahovat lokalizovaný text nabídky pro váš balíček.

3. Otevřete každý *název souboru. Locale. vsct* soubor pro lokalizaci textu.

   1. Upravte hodnoty prvku [ButtonText](../extensibility/buttontext-element.md) podle potřeby pro konkrétní jazyk.

   2. Pokud budete poskytovat lokalizované ikony, upravte hodnoty [rastrového obrázku](../extensibility/bitmap-element.md) tak, aby odkazovaly na cílové soubory.

      Následující příklad ukazuje text tlačítka v angličtině a španělštině pro příkaz k otevření okna nástroje Průzkumník stromu rodiny.

      [*FamilyTree. en-US. vsct*]

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

    [*FamilyTree.ES-ES. vsct*]

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

## <a name="localize-other-text-resources"></a>Lokalizace jiných textových prostředků

Textové prostředky jiné než názvy příkazů jsou definovány v souborech prostředků (*. resx*).

1. Přejmenujte *VSPackage. resx* na *VSPackage. en-US. resx*.

2. Vytvořte kopii souboru *VSPackage. en-US. resx* pro každý lokalizovaný jazyk.

     Pojmenujte každou kopii *VSPackage. { Locale}. resx*, kde *{locale}* je konkrétní název jazykové verze.

3. Přejmenujte *Resources. resx* na *Resources. en-US. resx*.

4. Vytvořte kopii souboru *Resources. en-US. resx* pro každý lokalizovaný jazyk.

     Pojmenujte jednotlivé *prostředky kopírování. { Locale}. resx*, kde *{locale}* je konkrétní název jazykové verze.

5. Otevřete jednotlivé soubory *. resx* pro úpravu hodnot řetězce podle potřeby pro konkrétní jazyk a jazykovou verzi. Následující příklad ukazuje lokalizovanou definici prostředků v záhlaví okna nástroje.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.ES-ES. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Zahrnutí lokalizovaných prostředků do projektu

Je nutné upravit soubor *AssemblyInfo.cs* a soubor projektu pro zahrnutí lokalizovaných prostředků.

1. V uzlu **vlastnosti** v **Průzkumník řešení**otevřete v editoru *AssemblyInfo.cs* nebo *AssemblyInfo. vb* .

2. Přidejte následující položku.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     V češtině se nastaví jako výchozí jazyk.

3. Uvolněte projekt.

4. Otevřete soubor projektu v editoru.

5. V kořenovém `Project` elementu přidejte `PropertyGroup` element s `UICulture` elementem, který odpovídá vašemu výchozímu jazyku.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Toto nastaví angličtinu jako výchozí jazykovou verzi uživatelského rozhraní pro ovládací prvky WPF (Windows Presentation Foundation).

6. Vyhledejte `ItemGroup` prvek, který obsahuje `EmbeddedResource` prvky.

7. V `EmbeddedResource` elementu, který volá *VSPackage. en-US. resx*, nahraďte `ManifestResourceName` element `LogicalName` prvkem, který je nastaven na `VSPackage.en-US.Resources` , následovně:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Pro každý lokalizovaný jazyk zkopírujte `EmbeddedResource` element pro `VsPackage.en-US` a nastavte atribut **include** a element **logického** atributu pro kopírování do cílového národního prostředí.

9. Do každého lokalizovaného `VSCTCompile` prvku přidejte `ResourceName` element, který odkazuje na `Menus.ctmenu` , jak je znázorněno v následujícím příkladu:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Uložte soubor projektu a znovu načtěte projekt.

11. Sestavte projekt.

     Tím se vytvoří hlavní sestavení a sestavení prostředků pro jednotlivé jazyky. Informace o lokalizaci procesu nasazení najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md) .

## <a name="see-also"></a>Viz také

- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)
