---
title: 'Postupy: vytvoření. Soubor vsct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158353"
---
# <a name="how-to-create-a-vsct-file"></a>Postupy: Vytvoření souboru .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Existuje několik způsobů, jak vytvořit soubor konfigurace příkazového řádku sady Visual Studio založený na jazyce XML (. vsct).  
  
- V šabloně balíčku můžete vytvořit nový VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- K vygenerování souboru z existujícího souboru. ctc lze použít kompilátor konfigurace příkazového řádku založený na jazyce XML, Vsct.exe.  
  
- Pomocí Vsct.exe můžete vygenerovat soubor. vsct z existujícího souboru. technický ředitel.  
  
- Můžete ručně vytvořit nový soubor. vsct.  
  
  Toto téma vysvětluje, jak ručně vytvořit nový soubor. vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Ruční vytvoření nového souboru. vsct  
  
1. Spustit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
2. V nabídce **soubor** přejděte na příkaz **Nový**a poté klikněte na možnost **soubor**.  
  
3. V podokně **šablony** klikněte na **soubor XML** a potom klikněte na **otevřít**.  
  
4. V nabídce **zobrazení** klikněte na **okno Vlastnosti** . zobrazí se vlastnosti souboru XML.  
  
5. V okně **vlastnosti** klikněte na tlačítko Procházet (...) na vlastnosti schemas.  
  
6. V seznamu schémat XSD vyberte schéma vsct. xsd. Pokud není v seznamu, klikněte na tlačítko **Přidat** a vyhledejte soubor na místním disku. Až skončíte, klikněte na **OK** .  
  
7. V souboru XML zadejte `<CommandTable` a stiskněte klávesu TAB. Uzavřete značku zadáním `>` .  
  
     Tím se vytvoří základní soubor. vsct.  
  
8. Vyplňte prvky souboru XML, který chcete přidat, podle [schématu vsct](../../extensibility/vsct-xml-schema-reference.md). Další informace najdete v tématu [vytváření obsahu. Soubory vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pouhým přidáním souboru. vsct do projektu nezpůsobí jeho zkompilování. Je nutné jej začlenit do procesu sestavení.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Přidání souboru. vsct do kompilace projektu  
  
1. Otevřete soubor projektu v editoru. Pokud je projekt načten, je nutné jej nejprve uvolnit.  
  
2. Přidejte [element Item](../../msbuild/itemgroup-element-msbuild.md) , který obsahuje element VSCTCompile, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Element resourceName by měl být vždy nastaven na hodnotu `Menus.ctmenu` .  
  
3. Pokud projekt obsahuje soubor. resx, přidejte element EmbeddedResource, který obsahuje element MergeWithCTO, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Tento kód by měl jít uvnitř elementu Item, který obsahuje vložené prostředky.  
  
4. Otevřete soubor balíčku, obvykle nazvaný *projectname*Package.cs nebo *ProjectName*Package. vb, v editoru.  
  
5. Přidejte atribut ProvideMenuResource do třídy Package, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     První hodnota parametru se musí shodovat s hodnotou atributu resourceName, který jste definovali v souboru projektu.  
  
## <a name="see-also"></a>Viz také  
 [Zdroj. Soubory vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Příkazová tabulka sady Visual Studio (. Soubory vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Postupy: vytvoření. Soubor vsct ze stávajícího souboru. Soubor CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Postupy: vytvoření. Soubor vsct ze stávajícího souboru. Soubor technický ředitel](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [XML schéma VSCT – referenční informace](../../extensibility/vsct-xml-schema-reference.md)
