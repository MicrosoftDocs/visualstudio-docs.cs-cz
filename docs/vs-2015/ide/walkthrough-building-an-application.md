---
title: 'Návod: Sestavení aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6c45a552e66c2d256c191f6bd8296f5b2ca2c61
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220199"
---
# <a name="walkthrough-building-an-application"></a>Postupy: Sestavení aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu se seznámíte se podrobněji seznamujete s několik možností, které můžete konfigurovat při sestavování aplikací pomocí sady Visual Studio. Budete vytvářet vlastní proces sestavení, skryjete některé varovné zprávy a zvýšíte výstupní informace sestavení, stejně jako další úkoly pro ukázkovou aplikaci.  
  
 Toto téma obsahuje následující oddíly:  
  
 [Nainstalovat ukázkovou aplikaci](../ide/walkthrough-building-an-application.md#BKMK_installapp)  
  
 [Vytvořit vlastní proces sestavení](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)  
  
 [Sestavení aplikace](../ide/walkthrough-building-an-application.md#BKMK_building)  
  
 [Skrýt upozornění kompilátoru](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)  
  
 [Zobrazení dalších podrobností o sestavení v okně Výstup](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)  
  
 [Vytváření sestavení pro vydání](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)  
  
##  <a name="BKMK_installapp"></a> Nainstalovat ukázkovou aplikaci  
 Budete používat **rozšíření a aktualizace** dialogové okno Najít a nainstalovat [Úvod do vytváření aplikací WPF](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) ukázky z Galerie vzorových příkladů na webu společnosti Microsoft. Galerie vzorových příkladů obsahuje různé vzorové projekty a kód, který můžete si stáhnout a prohlédnout při plánování a vývoji vašich aplikací.  
  
#### <a name="to-install-the-sample-application"></a>Chcete-li nainstalovat ukázkovou aplikaci  
  
1. V panelu nabídky zvolte **nástroje**, **rozšíření a aktualizace**.  
  
2. Zvolte **Online** kategorie a klikněte na tlačítko **Galerie vzorových příkladů** kategorie.  
  
3. Zadejte `Introduction` do pole Hledat vyhledejte ukázku.  
  
    ![Dialogové okno rozšíření a aktualizace](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")  
  
4. V seznamu výsledků zvolte buď **Úvod do vytváření aplikací WPF (Visual C#)** nebo **Úvod do vytváření aplikací WPF (Visual Basic)**.  
  
5. Zvolte **Stáhnout** tlačítko a klikněte na tlačítko **Zavřít** tlačítko.  
  
   Úvod do vytváření aplikací WPF se zobrazí v **nový projekt** dialogové okno.  
  
#### <a name="to-create-a-solution-for-the-sample-application"></a>K vytvoření řešení pro ukázkovou aplikaci  
  
1.  Otevřít **nový projekt** dialogové okno.  
  
     ![Na panelu nabídek zvolte soubor, nový, projekt](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
2.  V **nainstalováno** kategorie, zvolte **ukázky** kategorií můžete zobrazit příklad Úvod do vytváření aplikací WPF.  
  
3.  Pojmenujte řešení `IntroWPFcsharp` pro jazyk Visual C#.  
  
     ![Dialogové okno Nový projekt, nainstalované ukázky](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")  
  
     NEBO  
  
     Pojmenujte řešení `IntroWPFvb` v jazyce Visual Basic.  
  
     ![Dialogové okno Nový projekt, Visual Basic ukázka](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")  
  
4.  Zvolte **OK** tlačítko.  
  
##  <a name="BKMK_CreateBuildConfig"></a> Vytvořit vlastní proces sestavení  
 Když vytvoříte řešení, konfigurace sestavení pro ladění a vydání a jejich výchozí cíle platformy jsou definovány pro řešení automaticky. Můžete poté přizpůsobit tyto konfigurace nebo vytvořit vlastní. Konfigurace sestavení určují typ sestavení. Platformy sestavení určují operační systém, který aplikace cílí pro danou konfiguraci. Další informace najdete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md), [Principy platforem sestavení](../ide/understanding-build-platforms.md), a [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Můžete změnit nebo vytvořit konfigurace a nastavení platformy pomocí **nástroje Configuration Manager** dialogové okno. V tomto postupu vytvoříte konfiguraci sestavení pro testování.  
  
#### <a name="to-create-a-build-configuration"></a>Chcete-li vytvořit vlastní proces sestavení  
  
1. Otevřít **nástroje Configuration Manager** dialogové okno.  
  
    ![Vytvoření nabídky, příkaz nástroje Configuration Manager](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2. V **konfigurace aktivního řešení** klikněte na položku **nový**.  
  
3. V **nová konfigurace řešení** dialogové okno, pojmenujte novou konfiguraci `Test`, zkopírujte nastavení z existující konfigurace ladění a klikněte na tlačítko **OK** tlačítko.  
  
    ![Nové řešení dialogové okno Konfigurace](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4. V **platformou aktivního řešení** klikněte na položku **nový**.  
  
5. V **nová platforma řešení** dialogového okna zvolte **x64**a nekopírujte nastavení z x86 platformy.  
  
    ![Nové řešení platformy dialogové okno](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6. Zvolte **OK** tlačítko.  
  
   Konfigurace aktivního řešení se změnil na Test s platformou aktivního řešení nastavenou na x64.  
  
   ![Configuration Manager s konfigurací testu](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
   Můžete rychle ověřit nebo změnit konfiguraci aktivního řešení pomocí **konfigurace řešení** seznamu **standardní** nástrojů.  
  
   ![Možnost konfigurace řešení standardním panelu nástrojů](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
##  <a name="BKMK_building"></a> Sestavení aplikace  
 V dalším kroku vytvoříte řešení s vlastní konfigurací sestavení.  
  
#### <a name="to-build-the-solution"></a>Abyste mohli sestavit řešení  
  
- V panelu nabídky zvolte **sestavení**, **sestavit řešení**.  
  
  **Výstup** okně se zobrazí výsledky sestavení. Sestavení bylo úspěšné, ale byly vygenerovány několik upozornění.  
  
  Obrázek 1: upozornění aplikace Visual Basic  
  
  ![Výstupní okno Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
  Obrázek 2: Visual C# upozornění  
  
  ![Výstupní okno aplikace Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
##  <a name="BKMK_hidewarning"></a> Skrýt upozornění kompilátoru  
 Je můžete dočasně skrýt některé varovné zprávy během sestavení a nenechat je zbytečně zatěžovat výstup sestavení.  
  
#### <a name="to-hide-a-specific-visual-c-warning"></a>Skrytí konkrétního upozornění Visual C#  
  
1.  V **Průzkumníka řešení**, zvolte uzel projektu nejvyšší úrovně.  
  
2.  V panelu nabídky zvolte **zobrazení**, **stránky vlastností**.  
  
     **Návrháře projektu** otevře.  
  
3.  Zvolte **sestavení** stránky a pak na **potlačit upozornění** zadejte číslo upozornění `1762`.  
  
     ![Vytvořit stránku, Návrhář projektu](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")  
  
     Další informace najdete v tématu [stránku sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
4.  Sestavte řešení.  
  
     **Výstup** okně zobrazí pouze souhrnné informace o sestavení.  
  
     ![Okno výstup, Visual C&#35; upozornění sestavení](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Pro potlačení všech chyb sestavení Visual Basic  
  
1. V **Průzkumníka řešení**, zvolte uzel projektu nejvyšší úrovně.  
  
2. V panelu nabídky zvolte **zobrazení**, **stránky vlastností**.  
  
    **Návrháře projektu** otevře.  
  
3. Na **kompilaci** stránky, vyberte **zakázat všechna upozornění** zaškrtávací políčko.  
  
    ![Stránka kompilovat, Návrhář projektu](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")  
  
    Další informace najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
4. Sestavte řešení.  
  
   **Výstup** okně zobrazí pouze souhrnné informace o sestavení.  
  
   ![Okno výstup, Visual Basic vytvářet upozornění](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
   Další informace najdete v tématu [postupy: potlačení upozornění kompilátoru](../ide/how-to-suppress-compiler-warnings.md).  
  
##  <a name="BKMK_outputdetails"></a> Zobrazení dalších podrobností o sestavení v okně Výstup  
 Můžete změnit, se zobrazí v tom, kolik informací o procesu sestavení **výstup** okna. Podrobnost sestavení je obvykle nastavena na minimální, což znamená, že **výstup** okně zobrazí pouze souhrnné informace o procesu sestavení spolu se všechna upozornění s vysokou prioritou a chyby. Můžete zobrazit další informace o sestavení pomocí [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).  
  
> [!IMPORTANT]
>  Pokud zobrazíte další informace, bude trvat déle k dokončení sestavení.  
  
#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Chcete-li změnit množství informací v okně Výstup  
  
1. Otevřít **možnosti** dialogové okno.  
  
    ![Možnosti příkazu v nabídce Nástroje](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2. Zvolte **projekty a řešení** kategorie a klikněte na tlačítko **sestavíte a spustíte** stránky.  
  
3. V **podrobnosti výstupu sestavení projektu nástroje MSBuild** klikněte na položku **normální**a klikněte na tlačítko **OK** tlačítko.  
  
4. V panelu nabídky zvolte **sestavení**, **Vyčistit řešení**.  
  
5. Sestavte řešení a pak si projděte informace v **výstup** okna.  
  
    Informace o sestavení obsahují čas spuštění sestavení (umístěný na začátku), pořadí, ve které soubory byly zpracovány a množství času, které potřeba k dokončení procesu (umístěné na konci). Tyto informace zahrnují také syntaxi skutečného kompilátoru, která sadě Visual Studio spustí během sestavování.  
  
    Například v sestavení Visual C# [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) možnost uvádí kód upozornění 1762, který jste zadali dříve v tomto tématu, a tři další varování.  
  
    V sestavení Visual Basic [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) neobsahuje konkrétní upozornění k vyloučení, takže se nezobrazují žádné upozornění.  
  
   > [!TIP]
   >  Můžete prohledávat obsah **výstup** okna, je-li je zobrazit **najít** dialogové okno výběrem klávesy Ctrl + F.  
  
   Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
##  <a name="BKMK_releasebuild"></a> Vytváření sestavení pro vydání  
 Můžete vytvořit verzi ukázkovou aplikaci, která je optimalizována pro jeho dodání. Pro sestavení vydání zadáte, že spustitelný soubor je zkopírován do sdílené síťové složky, předtím, než se sestavování.  
  
 Další informace najdete v tématu [postupy: Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md) a [sestavování a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).  
  
#### <a name="to-specify-a-release-build-for-visual-basic"></a>K určení verze sestavení v jazyce Visual Basic  
  
1.  Otevřít **Návrhář projektu**.  
  
     ![Zobrazení nabídky, stránky vlastností příkaz](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.  Zvolte **kompilaci** stránky.  
  
3.  V **konfigurace** klikněte na položku **vydání**.  
  
4.  V **platformy** klikněte na položku **x86**.  
  
5.  V **výstupní cesta sestavení** zadejte síťovou cestu.  
  
     Například můžete zadat \\\myserver\builds.  
  
    > [!IMPORTANT]
    >  Okno se zprávou se může zobrazit upozornění, že sdílené síťové složky, které jste zadali nemusí být důvěryhodným umístěním. Pokud důvěřujete umístění, které jste zadali, zvolte **OK** tlačítka v okně se zprávou.  
  
6.  Sestavení aplikace.  
  
     ![Sestavit řešení – příkaz v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
#### <a name="to-specify-a-release-build-for-visual-c"></a>K určení verze sestavení v jazyce Visual C#  
  
1. Otevřít **Návrhář projektu**.  
  
    ![Zobrazení nabídky, stránky vlastností příkaz](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Zvolte **sestavení** stránky.  
  
3. V **konfigurace** klikněte na položku **vydání**.  
  
4. V **platformy** klikněte na položku **x86**.  
  
5. V **výstupní cesta** zadejte síťovou cestu.  
  
    Například můžete zadat \\\myserver\builds.  
  
   > [!IMPORTANT]
   >  Okno se zprávou se může zobrazit upozornění, že sdílené síťové složky, které jste zadali nemusí být důvěryhodným umístěním. Pokud důvěřujete umístění, které jste zadali, zvolte **OK** tlačítka v okně se zprávou.  
  
6. Sestavení aplikace.  
  
    ![Sestavit řešení – příkaz v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
   Spustitelný soubor je zkopírován do síťové cesty, který jste zadali. Jeho cesta bude \\\myserver\builds\\*FileName*.exe.  
  
   Blahopřejeme: Úspěšně jste dokončili tento návod.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Sestavení projektu (C++)](http://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)   
 [Předkompilace přehled rozhraní ASP.NET Web Application Project](http://msdn.microsoft.com/en-us/b940abbd-178d-4570-b441-52914fa7b887)   
 [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md)



