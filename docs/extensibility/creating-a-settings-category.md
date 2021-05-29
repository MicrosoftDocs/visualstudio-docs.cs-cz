---
title: Vytváření kategorie nastavení | Microsoft Docs
description: Naučte se, jak vytvořit kategorii nastavení sady Visual Studio a použít ji k ukládání a obnovování hodnot ze souboru nastavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe46ea835a119978fd3decd26949db3d59944e5e
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687609"
---
# <a name="create-a-settings-category"></a>Vytvoření kategorie nastavení

V tomto návodu vytvoříte kategorii nastavení sady Visual Studio a použijete ji k ukládání hodnot do a obnovení hodnot ze souboru nastavení. Kategorie nastavení je skupina souvisejících vlastností, které se zobrazují jako "vlastní bod nastavení"; To je jako zaškrtávací políčko v průvodci **importem a exportem nastavení** . (Můžete ji najít v nabídce **nástroje** .) Nastavení jsou uložena nebo obnovena jako kategorie a jednotlivá nastavení nejsou v průvodci zobrazena. Další informace najdete v tématu [nastavení prostředí](../ide/environment-settings.md).

Kategorii nastavení můžete vytvořit odvozením z <xref:Microsoft.VisualStudio.Shell.DialogPage> třídy.

Chcete-li spustit tento návod, je nutné nejprve dokončit první část [stránky vytvořit možnosti](../extensibility/creating-an-options-page.md). Výsledná Mřížka vlastností možností umožňuje prozkoumávat a měnit vlastnosti v kategorii. Po uložení kategorie vlastností do souboru nastavení prověřte soubor, abyste viděli, jak jsou hodnoty vlastností uložené.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Vytvoření kategorie nastavení
 V této části použijete vlastní bod nastavení k uložení a obnovení hodnot kategorie nastavení.

### <a name="to-create-a-settings-category"></a>Postup vytvoření kategorie nastavení

1. Dokončete [stránku vytvořit možnosti](../extensibility/creating-an-options-page.md).

2. Otevřete soubor *VSPackage. resx* a přidejte tyto tři řetězcové prostředky:

    |Name|Hodnota|
    |----------|-----------|
    |106|Moje kategorie|
    |107|Moje nastavení|
    |108|OptionInteger a OptionFloat|

     Tím se vytvoří prostředky s názvem kategorie "Moje kategorie", objekt "Moje nastavení" a popis kategorie "OptionInteger a OptionFloat".

    > [!NOTE]
    > Z těchto tří se v průvodci importem a exportem nastavení nezobrazí pouze název **kategorie.**

3. V *souboru MyToolsOptionsPackage.cs* přidejte do třídy vlastnost `float` s názvem , jak je `OptionFloat` `OptionPageGrid` znázorněno v následujícím příkladu.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > Kategorie `OptionPageGrid` s názvem "Moje kategorie" se teď skládá ze dvou vlastností, `OptionInteger` a `OptionFloat` .

4. Přidejte do třídy a přidejte jí CategoryName "Moje kategorie", dejte jí <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` ObjectName "Moje nastavení" a nastavte isToolsOptionPage na true. Nastavte categoryResourceID, objectNameResourceID a DescriptionResourceID na odpovídající ID prostředků řetězců vytvořených dříve.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Sestavte projekt a spusťte ladění. V experimentální instanci byste měli vidět, že **stránka Moje mřížka** teď má celočíselné i plovoucí hodnoty.

## <a name="examine-the-settings-file"></a>Prozkoumání souboru nastavení
 V této části exportujete hodnoty kategorií vlastností do souboru nastavení. Prozkoumáte soubor a pak hodnoty naimportujete zpět do kategorie vlastností.

1. Stisknutím klávesy F5 spusťte projekt v režimu **ladění.** Tím se spustí experimentální instance.

2. Otevřete dialogové **okno**  >  **Možnosti** nástrojů.

3. Ve stromovém zobrazení v levém podokně rozbalte **Moje** kategorie a pak klikněte na **My Grid Page (Moje stránka mřížky).**

4. Změňte hodnotu **OptionFloat** na 3.1416 a **OptionInteger** na 12. Klikněte na **OK**.

5. V nabídce **Nástroje** klikněte na **Importovat a exportovat nastavení**.

     Zobrazí se průvodce **importem a exportem nastavení** .

6. Ujistěte se, že je zaškrtnuté **políčko Exportovat vybrané nastavení prostředí** , a pak klikněte na **Další**.

     Zobrazí se stránka **zvolit nastavení pro export** .

7. Klikněte na **Moje nastavení**.

     **Popis** se změní na **OptionInteger a OptionFloat**.

8. Ujistěte se, že je vybraná jediná kategorie **Nastavení** , a pak klikněte na **Další**.

     Zobrazí se stránka **název souboru s nastavením** .

9. Pojmenujte nový soubor nastavení *MySettings. vssettings* a uložte ho do příslušného adresáře. Klikněte na **Finish** (Dokončit).

   `.vssettings`Soubor je soubor nastavení aplikace Visual Studio. Schéma souboru je otevřené. Nejčastěji se schéma řídí strukturou XML, kde každá kategorie je značka, která může obsahovat Tagy podkategorie. Tyto značky podkategorie můžou obsahovat značky hodnot vlastností. I když většina balíčků používá společnou strukturu, jakýkoli balíček v aplikaci Visual Studio může přispívat libovolný soubor XML do souboru se schématem, které zvolí.

   Stránka **exportovat kompletní** hlásí, že vaše nastavení bylo úspěšně exportováno.

10. V nabídce **soubor** přejděte na příkaz **otevřít** a poté klikněte na možnost **soubor**. Vyhledejte *MySettings. vssettings* a otevřete ho.

     Kategorii vlastností, kterou jste exportovali, můžete najít v následující části souboru (vaše identifikátory GUID se budou lišit).

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

     Všimněte si, že název celé kategorie je tvořen přidáním podtržítka k názvu kategorie následovaný názvem objektu. OptionFloat a OptionInteger se zobrazí v kategorii společně s jejich exportovanými hodnotami.

11. Zavřete soubor nastavení beze změny.

12. V nabídce **Nástroje** klikněte na **Možnosti,** rozbalte **Moje** kategorie, klikněte na **Moje** stránka mřížky a pak změňte hodnotu **OptionFloat** na 1.0 a **OptionInteger na** 1. Klikněte na **OK**.

13. V nabídce **Nástroje** klikněte na **Importovat a exportovat nastavení,** vyberte Importovat vybrané nastavení **prostředí** a potom klikněte na **Další.**

     Zobrazí **se stránka Uložit aktuální** nastavení.

14. Vyberte **Ne, stačí naimportovat nová nastavení** a pak **kliknout na Další.**

     Zobrazí **se stránka Choose a Collection of Settings to Import (Zvolte kolekci** nastavení, která se má importovat).

15. V uzlu Moje nastavení ve  stromovém zobrazení vyberte soubor *MySettings.vssettings.* Pokud se soubor ve stromovém zobrazení nezobrazí, klikněte na **Procházet a** vyhledejte ho. Klikněte na **Next** (Další).

     Zobrazí **se dialogové okno Zvolit nastavení** k importu.

16. Ujistěte se, **že je vybraná** možnost Moje nastavení, a pak klikněte na **Dokončit.** Po zobrazení **stránky Import complete (Import dokončeno)** klikněte na Close **(Zavřít).**

17. V nabídce **Nástroje** **klikněte na** Možnosti, rozbalte **Moje** kategorie, klikněte na Moje stránka **mřížky** a ověřte, že byly obnoveny hodnoty kategorií vlastností.
