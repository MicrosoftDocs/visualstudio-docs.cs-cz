---
title: Vytvoření kategorie nastavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66667b97ef10d6b07bef3e8c1c3b19842a07482e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388660"
---
# <a name="create-a-settings-category"></a>Vytvoření kategorie nastavení

V tomto názorném postupu vytvoření kategorie nastavení sady Visual Studio a použít ho k uložení hodnot a obnovení hodnoty ze souboru nastavení. Nastavení kategorie je skupina souvisejících vlastností, které se zobrazují jako "bod vlastní nastavení"; To znamená, že jako zaškrtávací políčko v **Import a export nastavení** průvodce. (Najdete ho na **nástroje** nabídky.) Nastavení se uloží nebo obnovili kategorii a individuální nastavení nejsou zobrazeny v průvodci. Další informace najdete v tématu [nastavení prostředí](../ide/environment-settings.md).

Vytvoření kategorie nastavení odvozením z <xref:Microsoft.VisualStudio.Shell.DialogPage> třídy.

Chcete-li spustit Tento názorný postup, musíte nejdřív dokončit první část [vytvoření stránky možnosti](../extensibility/creating-an-options-page.md). Výsledný mřížky vlastností možnosti umožňuje zkontrolovat a změnit vlastnosti v kategorii. Po uložení vlastnosti kategorie v souboru nastavení zkontrolujte v souboru chcete zobrazit, jak jsou uložené hodnoty vlastností.

## <a name="prerequisites"></a>Požadavky
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Vytvoření kategorie nastavení
 V této části použijete k uložení a obnovení hodnoty kategorie nastavení bodu vlastní nastavení.

### <a name="to-create-a-settings-category"></a>Vytvoření kategorie nastavení

1.  Dokončení [vytvoření stránky možnosti](../extensibility/creating-an-options-page.md).

2.  Otevřít *VSPackage.resx* a přidejte tyto tři řetězcové prostředky:

    |Název|Hodnota|
    |----------|-----------|
    |106|Moje kategorie|
    |107|Moje nastavení|
    |108|OptionInteger a OptionFloat|

     Tím se vytvoří prostředky tento název kategorie "My kategorie", objektu "nastavení" a "A OptionInteger OptionFloat" Popis kategorie.

    > [!NOTE]
    >  Z těchto tří pouze na název kategorie se nezobrazují v **nastavení importu a exportu** průvodce.

3.  V *MyToolsOptionsPackage.cs*, přidejte `float` vlastnost s názvem `OptionFloat` k `OptionPageGrid` třídy, jak je znázorněno v následujícím příkladu.

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
    >  `OptionPageGrid` Kategorii s názvem "My kategorie" nyní se skládá ze dvou vlastností `OptionInteger` a `OptionFloat`.

4.  Přidat <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> k `MyToolsOptionsPackage` třídy a poskytněte CategoryName "My kategorie", jí ObjectName "Nastavení" a isToolsOptionPage nastavena na hodnotu true. Nastavení categoryResourceID, objectNameResourceID a DescriptionResourceID na odpovídající prostředek řetězce, který ID vytvořili dříve.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5.  Sestavte projekt a spusťte ladění. V experimentální instanci byste měli vidět, který **stránku mřížky** nyní obsahuje hodnoty celé číslo a plovoucí desetinnou čárkou.

## <a name="examine-the-settings-file"></a>Zkontrolujte soubor nastavení
 V této části exportovat do souboru nastavení hodnot vlastností kategorie. Zkontrolujte v souboru a poté importovat hodnoty zpět do kategorie vlastnosti.

1.  Spusťte projekt v režimu ladění stisknutím kombinace kláves **F5**. Otevře se experimentální instance.

2.  Otevřít **nástroje** > **možnosti** dialogového okna.

3.  V zobrazení stromu v levém podokně rozbalte **kategorie Mé** a potom klikněte na tlačítko **stránku mřížky**.

4.  Změňte hodnotu vlastnosti **OptionFloat** k 3.1416 a **OptionInteger** do 12. Klikněte na tlačítko **OK**.

5.  Na **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**.

     **Nastavení importu a exportu** průvodce se zobrazí.

6.  Ujistěte se, že **exportovat vybrané nastavení prostředí** je vybrána a potom klikněte na tlačítko **Další**.

     **Zvolte nastavení pro Export** se zobrazí stránka.

7.  Klikněte na tlačítko **nastavení**.

     **Popis** změny **OptionInteger a OptionFloat**.

8.  Ujistěte se, že **má nastavení** je jediná kategorie, která je vybrána a potom klikněte na tlačítko **Další**.

     **Názvu souboru nastavení** se zobrazí stránka.

9. Pojmenujte nový soubor nastavení *MySettings.vssettings* a uložte ho do příslušného adresáře. Klikněte na tlačítko **Dokončit**.

     **Exportovat kompletní** stránku sestavy, nastavení bylo úspěšně exportováno.

10. Na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **souboru**. Vyhledejte *MySettings.vssettings* a otevřete ho.

     Můžete najít vlastnost kategorii, kterou jste exportovali v následující části souboru (vaše GUID se bude lišit).

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

     Všimněte si, že název úplnou kategorii je tvořen přidáním podtržítka na název kategorie, za nímž následuje název objektu. OptionFloat a OptionInteger zobrazí v kategorii, spolu s jejich exportovaných hodnot.

11. Zavřete soubor nastavení bez provedení změn.

12. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**, rozbalte **kategorie Mé**, klikněte na tlačítko **stránku mřížky** a potom změňte hodnotu vlastnosti  **OptionFloat** 1.0 a **OptionInteger** na hodnotu 1. Klikněte na tlačítko **OK**.

13. Na **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**vyberte **importovat vybrané nastavení prostředí**a potom klikněte na tlačítko **Další**.

     **Uložit aktuální nastavení** se zobrazí stránka.

14. Vyberte **Ne, importovat nové nastavení** a potom klikněte na tlačítko **Další**.

     **Vybrat kolekce nastavení pro Import** se zobrazí stránka.

15. Vyberte *MySettings.vssettings* soubor **má nastavení** uzlu ve stromovém zobrazení. Pokud soubor není uvedené ve stromovém zobrazení, klikněte na tlačítko **Procházet** a vyhledejte ho. Klikněte na tlačítko **Další**.

     **Zvolte nastavení pro Import** zobrazí se dialogové okno.

16. Ujistěte se, že **má nastavení** je vybrána a potom klikněte na tlačítko **Dokončit**. Když **úplný Import** stránky se zobrazí, klikněte na tlačítko **Zavřít**.

17. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**, rozbalte **kategorie Mé**, klikněte na tlačítko **stránku mřížky** a ověřte, zda hodnoty vlastností kategorie bylo obnoveno.