---
title: Vytvoření kategorie nastavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739604"
---
# <a name="create-a-settings-category"></a>Vytvoření kategorie nastavení

V tomto návodu vytvoříte kategorii nastavení sady Visual Studio a použijete ji k ukládání hodnot a obnovení hodnot ze souboru nastavení. Kategorie nastavení je skupina souvisejících vlastností, které se zobrazují jako "vlastní bod nastavení"; to znamená, že jako zaškrtávací políčko v průvodci **Nastavení importu a exportu.** (Najdete ji v nabídce **Nástroje.)** Nastavení jsou uložena nebo obnovena jako kategorie a jednotlivá nastavení se v průvodci nezobrazí. Další informace naleznete v [tématu Nastavení prostředí](../ide/environment-settings.md).

Kategorie nastavení vytvoříte odvozením z <xref:Microsoft.VisualStudio.Shell.DialogPage> třídy.

Chcete-li tento návod spustit, musíte nejprve dokončit první oddíl [stránky Vytvořit možnosti](../extensibility/creating-an-options-page.md). Výsledná mřížka vlastností Options umožňuje prozkoumat a změnit vlastnosti v kategorii. Po uložení kategorie vlastností do souboru nastavení zkontrolujte soubor, abyste zjistili, jak jsou uloženy hodnoty vlastností.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Vytvoření kategorie nastavení
 V této části použijete vlastní bod nastavení k uložení a obnovení hodnot kategorie nastavení.

### <a name="to-create-a-settings-category"></a>Vytvoření kategorie nastavení

1. Vyplňte [stránku Vytvořit možnosti](../extensibility/creating-an-options-page.md).

2. Otevřete soubor *VSPackage.resx* a přidejte tyto tři řetězcové prostředky:

    |Name (Název)|Hodnota|
    |----------|-----------|
    |106|Moje kategorie|
    |107|Moje nastavení|
    |108|OptionInteger a OptionFloat|

     Tím se vytvoří prostředky, které pojmenují kategorii "Moje kategorie", objekt "Moje nastavení" a popis kategorie "OptionInteger a OptionFloat".

    > [!NOTE]
    > Z těchto tří se v Průvodci **importem a exportem nastavení** nezobrazí pouze název kategorie.

3. V *MyToolsOptionsPackage.cs*přidejte `float` `OptionFloat` vlastnost `OptionPageGrid` s názvem do třídy, jak je znázorněno v následujícím příkladu.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > Kategorie `OptionPageGrid` s názvem "Moje kategorie" se nyní skládá `OptionInteger` `OptionFloat`ze dvou vlastností a .

4. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a `MyToolsOptionsPackage` do třídy a dát mu CategoryName "Moje kategorie", dát mu ObjectName "Moje nastavení", a nastavte isToolsOptionPage na true. Nastavte kategorii ResourceID, objectNameResourceID a DescriptionResourceID na odpovídající dříve vytvořená ID prostředků řetězce.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Sestavení projektu a začít ladění. V experimentální instanci byste měli vidět, že **moje stránka mřížky** má nyní celé číslo a float hodnoty.

## <a name="examine-the-settings-file"></a>Zkontrolujte soubor nastavení
 V této části exportujete hodnoty kategorií vlastností do souboru nastavení. Zkontrolujte soubor a potom importujte hodnoty zpět do kategorie vlastností.

1. Spusťte projekt v režimu ladění stisknutím **klávesy F5**. Tím se spustí experimentální instance.

2. Otevřete dialogové okno**Možnosti** **nástrojů.** > 

3. Ve stromovém zobrazení v levém podokně **rozbalte položku Moje kategorie** a potom klepněte na **položku Moje stránka mřížky**.

4. Změňte hodnotu **OptionFloat** na 3.1416 a **OptionInteger** na 12. Klikněte na tlačítko **OK**.

5. V nabídce **Nástroje** klepněte na **položku Importovat a exportovat nastavení**.

     Zobrazí se Průvodce **nastavením importu a exportu.**

6. Zkontrolujte, zda je vybraná volba **Exportovat vybraná nastavení prostředí,** a klepněte na tlačítko **Další**.

     Zobrazí se stránka **Zvolit nastavení exportu.**

7. Klepněte na **položku Moje nastavení**.

     **Popis** se změní na **OptionInteger a OptionFloat**.

8. Zkontrolujte, zda je **moje nastavení** jedinou vybranou kategorií, a klepněte na tlačítko **Další**.

     Zobrazí se stránka **Název souboru nastavení.**

9. Pojmenujte nový soubor nastavení *MySettings.vssettings* a uložte jej do příslušného adresáře. Klikněte na **Finish** (Dokončit).

     Stránka **Exportovat dokončena** hlásí, že nastavení bylo úspěšně exportováno.

10. V nabídce **Soubor** přejděte na **Otevřít**a potom klepněte na **příkaz Soubor**. Vyhledejte *soubor MySettings.vssettings* a otevřete jej.

     Kategorii vlastností, kterou jste exportovali, najdete v následující části souboru (identifikátory GUID se budou lišit).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Všimněte si, že úplný název kategorie je tvořen přidáním podtržítka do názvu kategorie následované názvem objektu. OptionFloat a OptionInteger se zobrazí v kategorii spolu s jejich exportovanými hodnotami.

11. Zavřete soubor nastavení bez změny.

12. V nabídce **Nástroje** klikněte na **Možnosti**, rozbalte **položku Moje kategorie**, klikněte na Stránka **mřížky** a změňte hodnotu **OptionFloat** na 1,0 a **OptionInteger** na 1. Klikněte na tlačítko **OK**.

13. V nabídce **Nástroje** klepněte na **položku Importovat a exportovat nastavení**, vyberte **Importovat vybraná nastavení prostředí**a potom klepněte na tlačítko **Další**.

     Zobrazí se stránka **Uložit aktuální nastavení.**

14. Vyberte **Ne, stačí importovat nová nastavení** a potom klepnout na tlačítko **Další**.

     Zobrazí se stránka **Vybrat kolekci nastavení k importu.**

15. Vyberte soubor *MySettings.vssettings* v uzlu **Moje nastavení** stromového zobrazení. Pokud se soubor ve stromovém zobrazení nezobrazí, klikněte na **Procházet** a najděte ho. Klikněte na **Další**.

     Zobrazí se dialogové okno **Zvolit nastavení k importu.**

16. Zkontrolujte, zda je vybraná možnost **Moje nastavení,** a klepněte na tlačítko **Dokončit**. Po zobrazení stránky **Importovat dokončeno** klepněte na **tlačítko Zavřít**.

17. V nabídce **Nástroje** klikněte na **Možnosti**, rozbalte **položku Moje kategorie**, klikněte na Stránka **mřížky** a ověřte, zda byly obnoveny hodnoty kategorie vlastností.
