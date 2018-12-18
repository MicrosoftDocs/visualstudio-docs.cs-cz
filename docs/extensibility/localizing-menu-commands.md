---
title: Lokalizace příkazů nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8eb9e566f4f5916961a95a1c61f8fdcbb689f1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876214"
---
# <a name="localize-menu-commands"></a>Lokalizace příkazů nabídky
Lokalizovaný text příkazů nabídky a panelu nástrojů můžete zadat tak, že vytvoříte lokalizované *.vsct* soubory a lokalizované *RESX* soubory vašeho balíčku VSPackage a pak aktualizuje soubory projektu začlenit změny.  
  
 Informace o tom, jak lokalizovat prostředí instalace najdete v tématu [balíčků VSIX lokalizovat](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localize-command-names"></a>Lokalizace názvů příkazů  
 V balíčcích VSPackage, příkazy nabídky a tlačítka panelu nástrojů jsou definovány v *.vsct* souboru.  
  
1. V **Průzkumníka řešení**, změňte název *.vsct* souboru z *filename.vsct* k *filename.en US.vsct*.  
  
2. Vytvořte kopii *filename.en US.vsct* pro každý lokalizovaný jazyk.  
  
    Název každé kopie *filename. { Národní prostředí} .vsct*, kde *{národní prostředí}* je název konkrétní jazykové verze. Seznam hodnot název jazykové verze, najdete v části [ID národních prostředí přiřazené společností Microsoft](/windows/uwp/publish/supported-languages).  
  
    Tyto *název souboru. Locale.vsct* soubory bude obsahovat text lokalizované nabídky pro svůj balíček.  
  
3. Otevřete každý *název souboru. Locale.vsct* soubor k lokalizaci text.  
  
   1. Upravit [ButtonText](../extensibility/buttontext-element.md) elementu hodnoty podle potřeby pro konkrétní jazyk.  
  
   2. Pokud zadáte lokalizované ikony, upravte [rastrový obrázek](../extensibility/bitmap-element.md) hodnoty tak, aby odkazoval na cílové soubory.  
  
      Následující příklad ukazuje angličtinu a slovenštinu text tlačítka pro příkaz pro otevření panelu nástrojů Průzkumník řady stromu.  
  
      [*FamilyTree.en US.vsct*]  
  
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
  
    [*FamilyTree.es ES.vsct*]  
  
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
  
## <a name="localize-other-text-resources"></a>Lokalizace další prostředky text  
 Text zdroje než názvy příkazů jsou definovány v prostředku (*RESX*) soubory.  
  
1.  Přejmenovat *VSPackage.resx* k *VSPackage.en US.resx*.  
  
2.  Vytvořte kopii *VSPackage.en US.resx* souboru pro každý lokalizovaný jazyk.  
  
     Název každé kopie *VSPackage. { Národní prostředí} RESX*, kde *{národní prostředí}* je název konkrétní jazykové verze.  
  
3.  Přejmenovat *Resources.resx* k *názvy Resources.en US.resx*.  
  
4.  Vytvořte kopii *názvy Resources.en US.resx* souboru pro každý lokalizovaný jazyk.  
  
     Název každé kopie *prostředky. { Národní prostředí} RESX*, kde *{národní prostředí}* je název konkrétní jazykové verze.  
  
5.  Otevřete každý *RESX* soubor upravit řetězec hodnoty podle potřeby pro konkrétní jazyk a jazykovou verzi. Následující příklad ukazuje definici lokalizovaný prostředek pro záhlaví panelu nástrojů.  
  
     [*Názvy Resources.en US.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [*Resources.es ES.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporate-localized-resources-into-the-project"></a>Lokalizované prostředky začlenit do projektu  
 Je třeba upravit *assemblyinfo.cs* soubor a soubor projektu začlenit lokalizované prostředky.  
  
1.  Z **vlastnosti** uzel v **Průzkumníka řešení**, otevřete *assemblyinfo.cs* nebo *assemblyinfo.vb* v editoru.  
  
2.  Přidejte následující položku.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Tím se nastaví Angličtina (USA) jako výchozí jazyk.  
  
3.  Uvolněte projekt.  
  
4.  Otevřete soubor projektu v editoru.  
  
5.  Vyhledejte `ItemGroup` element, který obsahuje `EmbeddedResource` elementy.  
  
6.  V `EmbeddedResource` element, který volá *VSPackage.en US.resx*, nahraďte `ManifestResourceName` element s `LogicalName` elementu, nastavte na `VSPackage.en-US.Resources`, následujícím způsobem.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Pro každý lokalizovaný jazyk, zkopírujte `EmbeddedResource` – element pro `VsPackage.en-US`a nastavte **zahrnout** atribut a **LogicalName** element kopírovat do cílového národního prostředí, jak je znázorněno v následujícím Příklad.  
  
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
  
     Tím se vytvoří do hlavního sestavení a sestavení prostředků pro jednotlivé jazyky. Informace o lokalizaci procesu nasazení najdete v tématu [balíčků VSIX lokalizace](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)