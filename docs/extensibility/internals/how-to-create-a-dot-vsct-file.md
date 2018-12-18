---
title: 'Postupy: vytvoření. Vsct soubor | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612ad5668ebb1033ef07dcad1fc07030d78e1643
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921207"
---
# <a name="how-to-create-a-vsct-file"></a>Postupy: vytvoření souboru .vsct  
  
Existuje několik způsobů, jak vytvořit konfiguraci sady Visual Studio založený na formátu XML příkaz tabulky (*.vsct*) soubor.  
  
- Můžete vytvořit nový balíček VSPackage správy kódu v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] balíčku šablony.  
  
- Můžete použít kompilátor konfigurace tabulky založený na formátu XML příkaz *Vsct.exe*můžete generovat soubor z existující *.ctc* souboru.  
  
- Můžete použít *Vsct.exe* ke generování *.vsct* souboru z existující *.cto* souboru.  
  
- Můžete ručně vytvořit nový *.vsct* souboru.  
  
  Tento článek vysvětluje, jak ručně vytvořit nový *.vsct* souboru.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Ruční vytvoření nového souboru .vsct  
  
1. Spustit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **souboru**.  
  
3. V **šablony** podokně klikněte na tlačítko **soubor XML** a potom klikněte na tlačítko **otevřít**.  
  
4. Na **zobrazení** nabídky, klikněte na tlačítko **vlastnosti** k zobrazení vlastností souboru XML.  
  
5. V **vlastnosti** okna, klikněte na tlačítko **Procházet** tlačítko **schémata** vlastnost.  
  
6. V seznamu schémata XSD, vyberte *vsct.xsd* schématu. Pokud to není v seznamu, klikněte na tlačítko **přidat** a pak vyhledejte soubor na místním disku. Klikněte na tlačítko **OK** až budete hotoví.  
  
7. V souboru XML, zadejte *< commandtable –* a potom stiskněte klávesu **kartu**. Zavřete značku zadáním *>*.  
  
    Tato akce vytvoří základní *.vsct* souboru.  
  
8. Vyplňte elementy souboru XML, který chcete přidat, podle [– referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md). Další informace najdete v tématu [vytváření souborů .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Postupy: vytvoření .vsct souboru z existujícího souboru .ctc  
  
Můžete vytvořit základě XML *.vsct* soubor z existující tabulky příkazů *.ctc* zdrojový soubor. Díky tomu mohou využít výhod nového založený na formátu XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formátu kompilátoru příkaz tabulky (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Vytvoření souboru .vsct ze souboru .ctc  
  
1. Získejte kopii souboru jazyka Perl.  
  
2. Získejte kopii souboru skriptu jazyka Perl *ConvertCTCToVSCT.pl*, který je obvykle umístěn ve  *\<Visual Studio SDK instalační_cesta > \VisualStudioIntegration\Tools\bin* složky.  
  
3. Získejte kopii souboru *.ctc* zdrojového souboru, který má být převeden.  
  
4. Soubory umístíte do stejného adresáře.  
  
5. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] okna příkazového řádku, přejděte do adresáře.  
  
6. Typ  
  
   ```  
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
   ```  
  
    kde *PkgCmd.ctc* je název *.ctc* souboru a *PkgCmd.vsct* je název *.vsct* soubor, který chcete vytvořit.  
  
    Tato akce vytvoří novou *.vsct* souboru zdroje tabulky příkazů XML. Soubor můžete zkompilovat pomocí *Vsct.exe*, kompilátor VSCT, jako jste vytvářeli jakýkoli jiný *.vsct* souboru.  
  
   > [!NOTE]
   >  Můžete zlepšit čitelnost *.vsct* souboru přeformátování komentáře XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Postupy: vytvoření souboru .vsct z existujícího souboru .cto  
  
Můžete vytvořit základě XML *.vsct* soubor z existujícího binárního souboru *.cto* souboru. To umožňuje využít výhod nového příkazu formát tabulky kompilátoru. I když tento proces funguje *.cto* soubor byl zkompilován z *.ctc* souboru. Při úpravě a kompilaci *.vsct* souboru do jiného souboru .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Vytvoření souboru .vsct ze souboru .cto  
  
1.  Získání kopií *.cto* Souborová služba a její odpovídající *.ctsym* souboru.  
  
2.  Soubory umístit do stejného adresáře jako *vsct.exe* kompilátoru.  
  
3.  Na příkazovém řádku aplikace Visual Studio, přejděte do adresáře, který obsahuje *.cto* a *.ctsym* soubory.  
  
4.  Typ  

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     kde \<ctofilename\> je název *.cto* souboru \<vsctfilename\> je název *.vsct* soubor vytvořit a \<symfilename\> je název *.ctsym* souboru.  
  
     Tento proces vytvoří nový *.vsct* souboru kompilátoru tabulky příkazů XML. Při úpravě a kompilaci souboru s *vsct.exe*, kompilátor vsct, jako jste vytvářeli jakýkoli jiný *.vsct* souboru.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Pouhým přidáním *.vsct* soubor do projektu nezpůsobí ho ke kompilaci. Musí obsahovat ho v procesu sestavení.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Přidat do projektu kompilace souboru .vsct  
  
1.  Otevřete soubor projektu v editoru. Pokud projekt načíst, musí se nejdřív uvolnit.  
  
2.  Přidat [itemgroup – element](../../msbuild/itemgroup-element-msbuild.md) , která obsahuje `VSCTCompile` elementu, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     `ResourceName` Element by měl být vždy nastaven na `Menus.ctmenu`.  
  
3.  Pokud váš projekt obsahuje *RESX* přidejte `EmbeddedResource` element, který obsahuje `MergeWithCTO` elementu, jak je znázorněno v následujícím příkladu:  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Tento kód by měl přejít uvnitř `ItemGroup` element, který obsahuje vložené prostředky.  
  
4.  Otevřete soubor balíčku, obvykle s názvem  *\<ProjectName\>Package.cs* nebo  *\<ProjectName\>Package.vb*, v editoru.  
  
5.  Přidat `ProvideMenuResource` atribut třídě balíčku, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     První hodnota parametru musí odpovídat hodnotě `ResourceName` atributu definovanému v souboru projektu.  
  
## <a name="see-also"></a>Viz také:  
 [Vytváření souborů .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Soubory tabulky (.vsct) příkaz pro Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)