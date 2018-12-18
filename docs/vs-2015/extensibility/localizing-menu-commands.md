---
title: Lokalizace příkazů nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b16771e4d47416f09774ce2f4765de9d6023e94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753898"
---
# <a name="localizing-menu-commands"></a>Lokalizace příkazů nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zadat lokalizovaný text nabídky a panelu nástrojů příkazy ve vytváření souborů .vsct lokalizované a lokalizované soubory .resx pro váš balíček VSPackage správy kódu a následně aktualizovat soubory projektu změny.  
  
 Informace o tom, jak lokalizovat prostředí instalace najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Lokalizace názvů příkazů  
 V balíčcích VSPackage příkazy nabídky a tlačítka panelu nástrojů jsou definovány v souboru .vsct.  
  
1. V **Průzkumníka řešení**, změňte název souboru .vsct z *filename*.vsct k *filename*.en-US.vsct.  
  
2. Vytvořte kopii *filename*.en-US.vsct pro každý lokalizovaný jazyk.  
  
    Název každé kopie *filename*. *Národní prostředí*.vsct, kde *národní prostředí* je název konkrétní jazykové verze. Seznam hodnot název jazykové verze, najdete v části [ID národního prostředí přiřazené společností Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Tyto *filename*. *Národní prostředí*soubory .vsct bude obsahovat text lokalizované nabídky pro svůj balíček.  
  
3. Otevřete každý *filename*. *Národní prostředí*souboru .vsct lokalizovat text.  
  
   1. Upravit [ButtonText](../extensibility/buttontext-element.md) elementu hodnoty podle potřeby pro konkrétní jazyk.  
  
   2. Pokud zadáte lokalizované ikony, upravte [rastrový obrázek](../extensibility/bitmap-element.md) hodnoty tak, aby odkazoval na cílové soubory.  
  
      Následující příklad ukazuje angličtinu a slovenštinu text tlačítka pro příkaz pro otevření panelu nástrojů Průzkumník řady stromu.  
  
      [FamilyTree.en US.vsct]  
  
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
  
    [FamilyTree.es ES.vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Lokalizace prostředků jiných Text  
 Text prostředků než názvy příkazů jsou definovány v souborech prostředky (RESX).  
  
1.  Přejmenujte VSPackage.resx VSPackage.en US.resx.  
  
2.  Vytvořte kopii souboru VSPackage.en US.resx pro každý lokalizovaný jazyk.  
  
     Název každé kopie balíčku VSPackage. *Národní prostředí*.resx, kde *národní prostředí* je název konkrétní jazykové verze.  
  
3.  Přejmenujte na názvy Resources.en US.resx Resources.resx.  
  
4.  Vytvořte kopii souboru názvy Resources.en US.resx pro každý lokalizovaný jazyk.  
  
     Název každé kopie prostředků. *Národní prostředí*.resx, kde *národní prostředí* je název konkrétní jazykové verze.  
  
5.  Otevřete oba soubory .resx a upravit hodnoty řetězce podle potřeby pro konkrétní jazyk a jazykovou verzi. Následující příklad ukazuje definici lokalizovaný prostředek pro záhlaví panelu nástrojů.  
  
     [Názvy Resources.en US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Začlenění lokalizované prostředky do projektu  
 Je třeba upravit soubor assemblyinfo.cs a soubor projektu a začlenit lokalizované prostředky.  
  
1.  Z **vlastnosti** uzel v **Průzkumníka řešení**, otevřete soubor assemblyinfo.cs nebo assemblyinfo.vb v editoru.  
  
2.  Přidejte následující položku.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Tím se nastaví Angličtina (USA) jako výchozí jazyk.  
  
3.  Uvolněte projekt.  
  
4.  Otevřete soubor projektu v editoru.  
  
5.  Vyhledejte `ItemGroup` element, který obsahuje `EmbeddedResource` elementy.  
  
6.  V `EmbeddedResource` nahraďte element, který volá VSPackage.en-US.resx `ManifestResourceName` element s `LogicalName` elementu, nastavte na `VSPackage.en-US.Resources`, následujícím způsobem.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Pro každý lokalizovaný jazyk, zkopírujte `EmbeddedResource` – element pro VsPackage.en-US a nastavte **zahrnout** atribut a **LogicalName** element kopírovat do cílového národního prostředí, jak je znázorněno v následujícím Příklad.  
  
8.  Pro každý lokalizovaný `VSCTCompile` elementu, přidejte `ResourceName` element, který odkazuje na `Menus.ctmenu`, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Uložte soubor projektu a znovu načíst projekt.  
  
10. Sestavte projekt.  
  
     Tím se vytvoří do hlavního sestavení a sestavení prostředků pro jednotlivé jazyky. Informace o lokalizaci procesu nasazení najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalizace a lokalizace](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)

