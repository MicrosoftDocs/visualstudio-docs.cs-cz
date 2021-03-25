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
ms.openlocfilehash: 1e3ef6dbfc58c67ce8e4dd7ff26634e4dbce2218
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089339"
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

     Tím se vytvoří zdroje s názvem kategorie Moje kategorie, objekt "Moje nastavení" a kategorie popis "OptionInteger a OptionFloat".

    > [!NOTE]
    > Z těchto tří typů se v průvodci **importem a exportem nastavení** nezobrazí pouze název kategorie.

3. V *MyToolsOptionsPackage. cs* přidejte `float` vlastnost s názvem `OptionFloat` do `OptionPageGrid` třídy, jak je znázorněno v následujícím příkladu.

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
    > `OptionPageGrid`Kategorie s názvem moje kategorie se teď skládá ze dvou vlastností `OptionInteger` a `OptionFloat` .

4. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> do `MyToolsOptionsPackage` třídy třídu, přiřaďte jí hodnotu NázevKategorie "Moje kategorie", dejte jí název ObjectName "Moje nastavení" a nastavte isToolsOptionPage na hodnotu true. Nastavte categoryResourceID, objectNameResourceID a DescriptionResourceID na odpovídající ID prostředků řetězců, které jste vytvořili dříve.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Sestavte projekt a spusťte ladění. V experimentální instanci byste měli vidět, že **Stránka Moje mřížka** teď má hodnoty Integer i float.

## <a name="examine-the-settings-file"></a>Projděte si soubor nastavení.
 V této části exportujete hodnoty kategorií vlastností do souboru nastavení. Prověřte soubor a pak hodnoty naimportujte zpátky do kategorie vlastností.

1. Spusťte projekt v režimu ladění stisknutím klávesy **F5**. Tím se spustí experimentální instance.

2. Otevřete   >  dialogové okno **Možnosti** nástrojů.

3. Ve stromovém zobrazení v levém podokně rozbalte **Moje kategorie** a potom klikněte na **stránku mřížka**.

4. Změňte hodnotu **OptionFloat** na 3,1416 a **OptionInteger** na 12. Klikněte na **OK**.

5. V nabídce **nástroje** klikněte na položku **Nastavení importu a exportu**.

     Zobrazí se průvodce **importem a exportem nastavení** .

6. Ujistěte se, že je zaškrtnuté **políčko Exportovat vybrané nastavení prostředí** , a pak klikněte na **Další**.

     Zobrazí se stránka **zvolit nastavení pro export** .

7. Klikněte na **Moje nastavení**.

     **Popis** se změní na **OptionInteger a OptionFloat**.

8. Ujistěte se, že je vybraná jediná kategorie **Nastavení** , a pak klikněte na **Další**.

     Zobrazí se stránka **název souboru s nastavením** .

9. Pojmenujte nový soubor nastavení *MySettings. vssettings* a uložte ho do příslušného adresáře. Klikněte na **Finish** (Dokončit).

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

12. V nabídce **nástroje** klikněte na **Možnosti**, rozbalte **Moje kategorie**, klikněte na **Stránka mřížka** a pak změňte hodnotu **OptionFloat** na 1,0 a **OptionInteger** na 1. Klikněte na **OK**.

13. V nabídce **nástroje** klikněte na položku **Nastavení importu a exportu**, vyberte možnost **Importovat vybrané nastavení prostředí** a pak klikněte na tlačítko **Další**.

     Zobrazí se stránka **Uložit aktuální nastavení** .

14. Vyberte **Ne, jenom importovat nové nastavení** a pak klikněte na **Další**.

     Zobrazí se stránka **zvolit kolekci nastavení k importu** .

15. V uzlu **Moje nastavení** stromového zobrazení vyberte soubor *MySettings. vssettings* . Pokud se soubor ve stromovém zobrazení nezobrazí, klikněte na tlačítko **Procházet** a vyhledejte ho. Klikněte na **Next** (Další).

     Zobrazí se dialogové okno **zvolit nastavení pro import** .

16. Ujistěte se, že je vybráno **Nastavení moje nastavení** , a pak klikněte na **Dokončit**. Po zobrazení stránky **Import dokončena** klikněte na tlačítko **Zavřít**.

17. V nabídce **nástroje** klikněte na **Možnosti**, rozbalte **Moje kategorie**, klikněte na **Stránka mřížka** a ověřte, zda byly obnoveny hodnoty kategorií vlastností.
