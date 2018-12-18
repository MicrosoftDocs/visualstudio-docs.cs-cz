---
title: Vytvoření kategorie nastavení | Dokumentace Microsoftu
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
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30d7b4c95a02d841723a4ddf1dcf51dd0ef011b4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730364"
---
# <a name="creating-a-settings-category"></a>Vytvoření kategorie nastavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto názorném postupu vytvoření kategorie nastavení sady Visual Studio a použít ho k uložení hodnot a obnovení hodnoty ze souboru nastavení. Nastavení kategorie je skupina souvisejících vlastností, které se zobrazují jako "bod vlastní nastavení"; To znamená, že jako zaškrtávací políčko v **Import a export nastavení** průvodce. (Najdete ho na **nástroje** nabídky.) Nastavení se uloží nebo obnovili kategorii a individuální nastavení nejsou zobrazeny v průvodci. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Vytvoření kategorie nastavení odvozením z <xref:Microsoft.VisualStudio.Shell.DialogPage> třídy.  
  
 Chcete-li spustit Tento názorný postup, musíte nejdřív dokončit první část [vytvoření stránky možnosti](../extensibility/creating-an-options-page.md). Výsledný mřížky vlastností možnosti umožňuje zkontrolovat a změnit vlastnosti v kategorii. Po uložení vlastnosti kategorie v souboru nastavení zkontrolujte v souboru chcete zobrazit, jak jsou uložené hodnoty vlastností.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Vytvoření kategorie nastavení  
 V této části použijete k uložení a obnovení hodnoty kategorie nastavení bodu vlastní nastavení.  
  
#### <a name="to-create-a-settings-category"></a>Vytvoření kategorie nastavení  
  
1.  Dokončení [vytvoření stránky možnosti](../extensibility/creating-an-options-page.md).  
  
2.  Otevřete soubor VSPackage.resx a přidejte tyto tři řetězcové prostředky:  
  
    |Název|Hodnota|  
    |----------|-----------|  
    |106|Moje kategorie|  
    |107|Moje nastavení|  
    |108|OptionInteger a OptionFloat|  
  
     Tím se vytvoří prostředky tento název kategorie "My kategorie", objektu "nastavení" a "A OptionInteger OptionFloat" Popis kategorie.  
  
    > [!NOTE]
    >  Z těchto tří pouze na název kategorie nezobrazí v průvodci Import a Export nastavení.  
  
3.  V MyToolsOptionsPackage.cs, přidejte `float` vlastnost s názvem `OptionFloat` k `OptionPageGrid` třídy, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="examining-the-settings-file"></a>V souboru nastavení  
 V této části exportovat do souboru nastavení hodnot vlastností kategorie. Zkontrolujte v souboru a poté importovat hodnoty zpět do kategorie vlastnosti.  
  
1.  Stisknutím klávesy F5 spusťte projekt v režimu ladění. Otevře se experimentální instance.  
  
2.  Otevřít **Nástroje / možnosti** dialogového okna.  
  
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
  
9. Pojmenujte nový soubor nastavení `MySettings.vssettings` a uložte ho do příslušného adresáře. Klikněte na tlačítko **Dokončit**.  
  
     **Exportovat kompletní** stránku sestavy, nastavení bylo úspěšně exportováno.  
  
10. Na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **souboru**. Vyhledejte `MySettings.vssettings` a otevřete ho.  
  
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
  
15. Vyberte `MySettings.vssettings` soubor **má nastavení** uzlu ve stromovém zobrazení. Pokud soubor není uvedené ve stromovém zobrazení, klikněte na tlačítko **Procházet** a vyhledejte ho. Klikněte na tlačítko **Další**.  
  
     **Zvolte nastavení pro Import** zobrazí se dialogové okno.  
  
16. Ujistěte se, že **má nastavení** je vybrána a potom klikněte na tlačítko **Dokončit**. Když **úplný Import** stránky se zobrazí, klikněte na tlačítko **Zavřít**.  
  
17. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**, rozbalte **kategorie Mé**, klikněte na tlačítko **stránku mřížky** a ověřte, zda hodnoty vlastností kategorie bylo obnoveno.

