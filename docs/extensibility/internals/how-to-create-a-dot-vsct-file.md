---
title: 'Postup: Vytvoření souboru . Vsct Soubor | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708110"
---
# <a name="how-to-create-a-vsct-file"></a>Postup: Vytvoření souboru .vsct

Existuje několik způsobů, jak vytvořit soubor tabulky příkazů sady Visual Studio založené na jazyce XML (*.vsct).*

- Můžete vytvořit nový VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v šabloně balíčku.

- K vygenerování souboru z existujícího souboru *CTC* můžete použít k onikrek konfigurace tabulky příkazů xml *Vsct.exe.*

- *Vsct.exe* můžete použít ke generování souboru *.vsct* z existujícího souboru *CTO.*

- Můžete ručně vytvořit nový soubor *.vsct.*

  Tento článek vysvětluje, jak ručně vytvořit nový soubor *VSCT.*

### <a name="to-manually-create-a-new-vsct-file"></a>Ruční vytvoření nového souboru VSCT

1. Spustit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **příkaz Soubor**.

3. V podokně **Šablony** klikněte na **Soubor XML** a potom na **Otevřít**.

4. V nabídce **View** klepněte na **příkaz Vlastnosti** a zobrazte vlastnosti souboru XML.

5. V okně **Vlastnosti** klepněte na tlačítko **Procházet** ve vlastnosti **Schémata.**

6. V seznamu schémat XSD vyberte schéma *vsct.xsd.* Pokud není v seznamu, klepněte na tlačítko **Přidat** a vyhledejte soubor na místní jednotce. Po dokončení klepněte na **tlačítko OK.**

7. Do souboru XML zadejte *<CommandTable* a stiskněte **klávesu Tab**. Zavřete značku zadáním *>*.

    Tato akce vytvoří základní *soubor .vsct.*

8. Vyplňte prvky souboru XML, který chcete přidat, podle [odkazu na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md). Další informace naleznete v [tématu Author .vsct files](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Postup: Vytvoření souboru .vsct z existujícího souboru CTC

Soubor *VSCT* založený na jazyce XML můžete vytvořit z existujícího zdrojového souboru *CTC* tabulky příkazů. Tímto způsobem můžete využít nový formát kompilátoru založeného na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] XML (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Vytvoření souboru CtC .vsct ze souboru CTC

1. Získejte kopii jazyka Perl.

2. Získejte kopii skriptu Perl *ConvertCTCToVSCT.pl*, který se obvykle nachází v * \<instalační cestě sady Visual Studio SDK>\VisualStudioIntegration\Tools\bin.*

3. Získejte kopii zdrojového souboru *CTC,* který chcete převést.

4. Umístěte soubory do stejného adresáře.

5. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] okně příkazového řádku přejděte do adresáře.

6. Typ

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    kde *PkgCmd.ctc* je název souboru *CTC* a *PkgCmd.vsct* je název souboru *.vsct,* který chcete vytvořit.

    Tato akce vytvoří nový zdrojový soubor tabulky *příkazu XML .vsct.* Soubor můžete zkompilovat pomocí *vsct.exe*, kompilátoru VSCT, stejně jako jakýkoli jiný soubor *.vsct.*

   > [!NOTE]
   > Čitelnost souboru *.vsct* můžete zlepšit přeformátováním komentářů XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Postup: Vytvoření souboru .vsct z existujícího souboru CTO

Soubor *VSCT* založený na jazyce XML můžete vytvořit z existujícího binárního souboru *CTO.* To umožňuje využít nový formát kompilátoru tabulky příkazů. Tento proces funguje i v případě, že soubor *.cto* byl zkompilován ze souboru *CTC.* Soubor *.vsct* můžete upravit a zkompilovat do jiného souboru .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Vytvoření souboru .vsct ze souboru .cto

1. Získejte kopie souboru *CTTO* a jeho odpovídajícího souboru *CTSYM.*

2. Umístěte soubory do stejného adresáře jako kompilátor *vsct.exe.*

3. Na příkazovém řádku sady Visual Studio přejděte do adresáře, který obsahuje soubory *CtTO* a *CTSYM.*

4. Typ

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     kde \<\> ctofilename je název souboru *.cto,* \<vsctfilename\> je název souboru *.vsct,* který chcete vytvořit, a \<název symfilename\> je název souboru *CTSYM.*

     Tento proces vytvoří nový soubor kompilátoru příkazové tabulky XML *.vsct.* Soubor můžete upravovat a kompilovat pomocí *vsct.exe*, kompilátoru vsct, stejně jako jakýkoli jiný soubor *.vsct.*

## <a name="compile-the-code"></a>Kompilace kódu
 Jednoduše přidání souboru *.vsct* do projektu nezpůsobí jeho kompilaci. Je nutné začlenit do procesu sestavení.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Přidání souboru .vsct do kompilace projektu

1. Otevřete soubor projektu v editoru. Pokud je projekt načten, musíte jej nejprve uvolnit.

2. Přidejte [element ItemGroup,](../../msbuild/itemgroup-element-msbuild.md) který obsahuje `VSCTCompile` prvek, jak je znázorněno v následujícím příkladu.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Prvek `ResourceName` by měl být `Menus.ctmenu`vždy nastaven na .

3. Pokud váš projekt obsahuje soubor *Resx,* `EmbeddedResource` přidejte `MergeWithCTO` prvek, který obsahuje prvek, jak je znázorněno v následujícím příkladu:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Tato značka by měla `ItemGroup` přejít do prvku, který obsahuje vložené prostředky.

4. Otevřete soubor balíčku, obvykle s názvem * \<\>ProjectName Package.cs* nebo * \<ProjectName\>Package.vb*, v editoru.

5. Přidejte `ProvideMenuResource` atribut do třídy balíčku, jak je znázorněno v následujícím příkladu.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     První hodnota parametru se musí `ResourceName` shodovat s hodnotou atributu definovaného v souboru projektu.

## <a name="see-also"></a>Viz také
- [Soubory Autor .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Soubory příkazů sady Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odkaz na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
