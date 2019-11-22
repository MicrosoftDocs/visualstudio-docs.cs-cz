---
title: 'Návod: sestavování aplikace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2d9b958dacfb35877abc9ad1e83a349e43a7af0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296856"
---
# <a name="walkthrough-building-an-application"></a>Postupy: Sestavení aplikace

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po dokončení tohoto návodu se seznámíte s několika možnostmi, které můžete konfigurovat při sestavování aplikací pomocí sady Visual Studio. Vytvoříte vlastní konfiguraci sestavení, skryjete určité varovné zprávy a zvýšíte informace o výstupu sestavení, a to mimo jiné úkoly pro ukázkovou aplikaci.

Toto téma obsahuje následující oddíly:

[Instalace ukázkové aplikace](../ide/walkthrough-building-an-application.md)

[Vytvoření vlastní konfigurace sestavení](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[Sestavení aplikace](../ide/walkthrough-building-an-application.md#BKMK_building)

[Skrýt upozornění kompilátoru](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[Zobrazit další podrobnosti o sestavení v okno Výstup](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[Vytvoření sestavení pro vydání](../ide/walkthrough-building-an-application.md)

#### <a name="to-install-the-sample-application"></a>Instalace ukázkové aplikace

1. Na řádku nabídek klikněte na **nástroje**, **rozšíření a aktualizace**.

2. Zvolte kategorii **online** a pak zvolte kategorii **Galerie ukázek** .

3. Zadáním `Introduction` do vyhledávacího pole vyhledejte ukázku.

    ![Dialogové okno rozšíření a aktualizace](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. V seznamu výsledků vyberte možnost **Úvod k sestavování aplikací WPF (Visual C#)** nebo **Úvod do vytváření aplikací WPF (Visual Basic)** .

5. Klikněte na tlačítko **Download (stáhnout** ) a pak klikněte na tlačítko **Zavřít** .

   Ukázka Úvod do vytváření aplikací WPF se zobrazí v dialogovém okně **Nový projekt** .

#### <a name="to-create-a-solution-for-the-sample-application"></a>Vytvoření řešení pro ukázkovou aplikaci

1. Otevřete dialogové okno **Nový projekt** .

     ![Na panelu nabídek vyberte možnosti soubor, nový, projekt.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. V kategorii **nainstalováno** vyberte kategorii **ukázky** , aby se zobrazil Úvod k ukázce vytváření aplikací WPF.

3. Pojmenujte `IntroWPFcsharp` řešení pro C#vizuál.

     ![Dialogové okno Nový projekt, nainstalované ukázky](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     NEBO

     Pojmenujte `IntroWPFvb` řešení Visual Basic.

     ![Dialogové okno Nový projekt, ukázka Visual Basic](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. Zvolte **OK** tlačítko.

## <a name="BKMK_CreateBuildConfig"></a>Vytvoření vlastní konfigurace sestavení

Když vytvoříte řešení, konfigurace sestavení ladění a vydání a jejich výchozí cíle platformy jsou definovány pro řešení automaticky. Tyto konfigurace pak můžete přizpůsobit nebo vytvořit vlastní. Konfigurace sestavení určují typ sestavení. Platformy buildu určují operační systém, pro který aplikace cílí na tuto konfiguraci. Další informace naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md), [Principy platforem sestavení](../ide/understanding-build-platforms.md)a [Konfigurace projektů ladění a vydání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

Konfigurace a nastavení platformy můžete změnit nebo vytvořit pomocí dialogového okna **Configuration Manager** . V tomto postupu vytvoříte konfiguraci sestavení pro testování.

#### <a name="to-create-a-build-configuration"></a>Vytvoření konfigurace sestavení

1. Otevřete dialogové okno **Configuration Manager** .

    ![Nabídka sestavení, Configuration Manager příkaz](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. V seznamu **aktivní konfigurace řešení** vyberte možnost **Nový**.

3. V dialogovém okně **Nová konfigurace řešení** zadejte název nové konfigurace `Test`, zkopírujte nastavení z existující konfigurace ladění a pak klikněte na tlačítko **OK** .

    ![Dialogové okno Nová konfigurace řešení](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. V seznamu **Aktivní platforma řešení** vyberte možnost **Nový**.

5. V dialogovém okně **Nová platforma řešení** vyberte **x64**a nekopírujte nastavení z platformy x86.

    ![Dialogové okno Nová platforma řešení](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. Zvolte **OK** tlačítko.

   Konfigurace aktivního řešení se změnila na test s aktivní platformou řešení nastavenou na x64.

   ![Configuration Manager s konfigurací testu](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   Můžete rychle ověřit nebo změnit konfiguraci aktivního řešení pomocí seznamu **Konfigurace řešení** na **standardním** panelu nástrojů.

   ![Možnost konfigurace řešení standardní panel nástrojů](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="BKMK_building"></a>Sestavení aplikace

V dalším kroku sestavíte řešení s vlastní konfigurací sestavení.

#### <a name="to-build-the-solution"></a>Abyste mohli sestavit řešení

- Na panelu nabídek vyberte **sestavení**, **řešení sestavení**.

  V okně **výstup** se zobrazí výsledky sestavení. Sestavení bylo úspěšné, ale vygenerovalo se několik varovných zpráv.

  Obrázek 1: upozornění Visual Basic

  ![okno Výstup Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  Obrázek 2: upozornění C# vizuálů

  ![okno Výstup Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="BKMK_hidewarning"></a>Skrýt upozornění kompilátoru

Můžete dočasně skrýt určité varovné zprávy během sestavování, ale nemusíte mít k dispozici výstup sestavení.

#### <a name="to-hide-a-specific-visual-c-warning"></a>Skrytí konkrétního vizuálního C# upozornění

1. V **Průzkumník řešení**vyberte uzel projektu nejvyšší úrovně.

2. Na panelu nabídek vyberte možnost **zobrazení**, **stránky vlastností**.

     Otevře se **Návrhář projektu** .

3. Zvolte stránku **sestavení** a potom v poli **potlačit upozornění** zadejte číslo upozornění `1762`.

     ![Stránka sestavení, Návrhář projektu](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

4. Sestavte řešení.

     V okně **výstup** se zobrazí pouze souhrnné informace o sestavení.

     ![Okno Výstup, upozornění sestavení&#35; v jazyce Visual c++](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Chcete-li potlačit všechna Visual Basic upozornění sestavení

1. V **Průzkumník řešení**vyberte uzel projektu nejvyšší úrovně.

2. Na panelu nabídek vyberte možnost **zobrazení**, **stránky vlastností**.

    Otevře se **Návrhář projektu** .

3. Na stránce **kompilace** zaškrtněte políčko **Zakázat všechna upozornění** .

    ![Stránka Kompilovat, Návrhář projektu](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    Další informace najdete v tématu [Konfigurace upozornění v Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Sestavte řešení.

   V okně **výstup** se zobrazí pouze souhrnné informace o sestavení.

   ![Okno Výstup, upozornění sestavení Visual Basic](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   Další informace naleznete v tématu [How to: potlačit upozornění kompilátoru](../ide/how-to-suppress-compiler-warnings.md).

## <a name="BKMK_outputdetails"></a>Zobrazit další podrobnosti o sestavení v okno Výstup

Můžete změnit, kolik informací o procesu sestavení se zobrazí v okně **výstup** . Úroveň podrobností sestavení je obvykle nastavena na hodnotu minimální, což znamená, že okno **výstup** zobrazuje pouze souhrn procesu sestavení spolu s upozorněními s vysokou prioritou nebo chybami. Můžete zobrazit další informace o sestavení pomocí [dialogového okna Možnosti, projekty a řešení, sestavit a spustit](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Pokud zobrazíte více informací, dokončení sestavení bude trvat déle.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Změna množství informací v okně výstup

1. Otevřete dialogové okno **Možnosti** .

    ![Příkaz Možnosti v nabídce nástroje](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Zvolte kategorii **projekty a řešení** a potom zvolte stránku **sestavení a spuštění** .

3. V seznamu **podrobností výstupu sestavení projektu nástroje MSBuild** zvolte možnost **normální**a pak klikněte na tlačítko **OK** .

4. Na řádku nabídek klikněte na položku **sestavit**, **Vyčistit řešení**.

5. Sestavte řešení a pak zkontrolujte informace v okně **výstup** .

    Informace o sestavení zahrnují čas spuštění sestavení (umístěný na začátku), pořadí, ve kterém byly soubory zpracovány, a množství času, po který byl proces dokončen (umístěný na konci). Tyto informace obsahují také skutečnou syntaxi kompilátoru, kterou Visual Studio spouští během sestavení.

    Například ve Visual C# buildu možnost [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) vypíše kód upozornění 1762, který jste zadali dříve v tomto tématu, spolu se třemi dalšími upozorněními.

    V sestavách Visual Basic [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) neobsahuje specifická upozornění, která se mají vyloučit, takže se nezobrazí žádná upozornění.

   > [!TIP]
   > Pokud zobrazíte dialogové okno **Najít** kliknutím na klávesovou zkratku CTRL + F, můžete vyhledat obsah okna **výstup** .

   Další informace najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Vytvoření sestavení pro vydání

Můžete vytvořit verzi ukázkové aplikace optimalizované pro odeslání IT. Pro Build vydaných verzí určíte, že se spustitelný soubor zkopíruje do sdílené síťové složky před tím, než se sestaví.

Další informace naleznete v tématu [Postupy: Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md) a [sestavování a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

#### <a name="to-specify-a-release-build-for-visual-basic"></a>Určení sestavení pro vydání pro Visual Basic

1. Otevřete **Návrhář projektu**.

     ![Nabídka zobrazení, příkaz stránky vlastností](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Vyberte stránku **kompilovat** .

3. V seznamu **Konfigurace** vyberte možnost **verze**.

4. V seznamu **platforma** vyberte možnost **x86**.

5. V poli **výstupní cesta sestavení** zadejte síťovou cestu.

     Můžete například zadat \\\myserver\builds.

    > [!IMPORTANT]
    > Může se zobrazit okno se zprávou s upozorněním, že sdílená síťová složka, kterou jste zadali, nemusí být důvěryhodné umístění. Pokud důvěřujete umístění, které jste zadali, klikněte na tlačítko **OK** v okně se zprávou.

6. Sestavte aplikaci.

     ![Příkaz Sestavit řešení v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>Chcete-li zadat sestavení pro vydání pro Visual C\#

1. Otevřete **Návrhář projektu**.

    ![Nabídka zobrazení, příkaz stránky vlastností](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Zvolte **sestavení** stránky.

3. V seznamu **Konfigurace** vyberte možnost **verze**.

4. V seznamu **platforma** vyberte možnost **x86**.

5. V poli **výstupní cesta** zadejte síťovou cestu.

    Můžete například zadat \\\myserver\builds.

   > [!IMPORTANT]
   > Může se zobrazit okno se zprávou s upozorněním, že sdílená síťová složka, kterou jste zadali, nemusí být důvěryhodné umístění. Pokud důvěřujete umístění, které jste zadali, klikněte na tlačítko **OK** v okně se zprávou.

6. Sestavte aplikaci.

    ![Příkaz Sestavit řešení v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Spustitelný soubor je zkopírován do síťové cesty, kterou jste zadali. Cesta by \\\myserver\builds\\*filename*. exe.

   Gratulujeme: úspěšně jste dokončili tento návod.

## <a name="see-also"></a>Viz také

- [Návod: Sestavení projektu (C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [Přehled Předkompilace projektu webové aplikace v ASP.NET](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md)
