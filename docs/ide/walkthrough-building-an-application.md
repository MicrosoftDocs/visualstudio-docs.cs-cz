---
title: 'Návod: Sestavení aplikace'
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f94cc62cdadb2df3806f5b188278f49e4041235
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647176"
---
# <a name="walkthrough-build-an-application"></a>Návod: Sestavení aplikace

Po dokončení tohoto návodu se seznámíte s několika možnostmi, které můžete konfigurovat při sestavování aplikací pomocí sady Visual Studio. Vytvoříte vlastní konfiguraci sestavení, skryjete určité zprávy upozornění a zvýšíte informace o výstupu sestavení pro ukázkovou aplikaci.

## <a name="install-the-sample-application"></a>Instalace ukázkové aplikace

Stáhněte si ukázku [Úvod k vytváření aplikací WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) . Vyberte buď C# nebo Visual Basic. Po stažení souboru *zip* ho rozbalte a otevřete soubor *ExpenseItIntro. sln* pomocí sady Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Vytvoření vlastní konfigurace sestavení

Když vytvoříte řešení, konfigurace sestavení ladění a vydání a jejich výchozí cíle platformy jsou definovány pro řešení automaticky. Tyto konfigurace pak můžete přizpůsobit nebo vytvořit vlastní. Konfigurace sestavení určují typ sestavení. Platformy buildu určují operační systém, pro který aplikace cílí na tuto konfiguraci. Další informace naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md), [pochopení platforem sestavení](../ide/understanding-build-platforms.md)a [Postupy: nastavení konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md).

Konfigurace a nastavení platformy můžete změnit nebo vytvořit pomocí dialogového okna **Configuration Manager** . V tomto postupu vytvoříte konfiguraci sestavení pro testování.

### <a name="create-a-build-configuration"></a>Vytvoření konfigurace sestavení

1. Otevřete dialogové okno **Configuration Manager** .

   ![Nabídka sestavení, Configuration Manager příkaz](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. V seznamu **aktivní konfigurace řešení** vyberte možnost **\<New... \>** .

1. V dialogovém okně **Nová konfigurace řešení** zadejte název nové konfigurace `Test`, zkopírujte nastavení z existující konfigurace **ladění** a pak klikněte na tlačítko **OK** .

   ![Dialogové okno Nová konfigurace řešení](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. V seznamu **Aktivní platforma řešení** vyberte **\<New... \>** .

1. V dialogovém okně **Nová platforma řešení** vyberte **x64**a nekopírujte nastavení z platformy x86.

   ![Dialogové okno Nová platforma řešení](../ide/media/buildwalk_newsolutionplatform.png)

1. Klikněte na tlačítko **OK** .

   Konfigurace aktivního řešení se změnila na **test** s aktivní platformou řešení nastavenou na x64.

   ![Configuration Manager s konfigurací testu](../ide/media/buildwalk_configmanagertestconfig.png)

1. Klikněte na tlačítko **Zavřít**.

Můžete rychle ověřit nebo změnit konfiguraci aktivního řešení pomocí seznamu **Konfigurace řešení** na **standardním** panelu nástrojů.

![Možnost konfigurace řešení standardní panel nástrojů](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Sestavení aplikace

V dalším kroku sestavíte řešení s vlastní konfigurací sestavení.

### <a name="build-the-solution"></a>Sestavení řešení

- Na panelu nabídek zvolte **sestavení**  > **Sestavit řešení**nebo stiskněte **klávesovou zkratku CTRL** +**SHIFT** +**B**.

    V okně **výstup** se zobrazí výsledky sestavení. Sestavení bylo úspěšné.

## <a name="hide-compiler-warnings"></a>Skrýt upozornění kompilátoru

Dále zavádíme nějaký kód, který způsobí, že kompilátor generuje upozornění.

1. V C# projektu otevřete soubor *ExpenseReportPage.XAML.cs* . Do metody **ExpenseReportPage** přidejte následující kód: `int i;`.

    NEBO

    V projektu Visual Basic otevřete soubor *ExpenseReportPage. XAML. vb* . V konstruktoru **Public Sub New vlastního konstruktoru...** přidejte následující kód: `Dim i`.

1. Sestavte řešení.

V okně **výstup** se zobrazí výsledky sestavení. Sestavení bylo úspěšné, ale vygenerovala se upozornění:

![okno Výstup Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![okno Výstup Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Můžete dočasně skrýt určité varovné zprávy během sestavování, ale nemusíte mít k dispozici výstup sestavení.

### <a name="hide-a-specific-c-warning"></a>Skrýt konkrétní C# upozornění

1. V **Průzkumník řešení**vyberte uzel projektu nejvyšší úrovně.

1. Na panelu nabídek vyberte možnost **zobrazit**  > **stránky vlastností**.

     Otevře se **Návrhář projektu** .

1. Zvolte stránku **sestavení** a potom v poli **potlačit upozornění** zadejte číslo upozornění **0168**.

     ![Stránka sestavení, Návrhář projektu](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Sestavte řešení.

     V okně **výstup** se zobrazí pouze souhrnné informace o sestavení.

     ![Okno Výstup, upozornění sestavení&#35; v jazyce Visual c++](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Potlačit všechna upozornění sestavení Visual Basic

1. V **Průzkumník řešení**vyberte uzel projektu nejvyšší úrovně.

2. Na panelu nabídek vyberte možnost **zobrazit**  > **stránky vlastností**.

     Otevře se **Návrhář projektu** .

3. Na stránce **kompilace** zaškrtněte políčko **Zakázat všechna upozornění** .

     ![Stránka Kompilovat, Návrhář projektu](../ide/media/buildwalk_vbsuppresswarnings.png)

     Další informace najdete v tématu [Konfigurace upozornění v Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Sestavte řešení.

   V okně **výstup** se zobrazí pouze souhrnné informace o sestavení.

   ![Okno Výstup, upozornění sestavení Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Další informace naleznete v tématu [How to: potlačit upozornění kompilátoru](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Zobrazit další podrobnosti o sestavení v okně výstup

Můžete změnit, kolik informací o procesu sestavení se zobrazí v okně **výstup** . Úroveň podrobností sestavení je obvykle nastavena na hodnotu **minimální**, což znamená, že okno **výstup** zobrazuje pouze souhrn procesu sestavení spolu s upozorněními s vysokou prioritou nebo chybami. Můžete zobrazit další informace o sestavení pomocí [dialogového okna Možnosti, projekty a řešení, sestavit a spustit](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Pokud zobrazíte více informací, dokončení sestavení bude trvat déle.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Změna množství informací v okně výstup

1. Otevřete dialogové okno **Možnosti** .

     ![Příkaz Možnosti v nabídce nástroje](../ide/media/exploreide-toolsoptionsmenu.png)

1. Zvolte kategorii **projekty a řešení** a potom zvolte stránku **sestavení a spuštění** .

1. V seznamu **podrobností výstupu sestavení projektu nástroje MSBuild** zvolte možnost **normální**a pak klikněte na tlačítko **OK** .

1. Na panelu nabídek vyberte možnost **sestavit**  > **Vyčistit řešení**.

1. Sestavte řešení a pak zkontrolujte informace v okně **výstup** .

     Informace o sestavení zahrnují čas spuštění sestavení (umístěný na začátku) a pořadí, ve kterém byly soubory zpracovány. Tyto informace obsahují také skutečnou syntaxi kompilátoru, kterou Visual Studio spouští během sestavení.

     Například v C# sestavách možnost [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) vypíše kód upozornění, **1762**, který jste zadali dříve v tomto tématu, spolu se třemi dalšími upozorněními.

     V sestavách Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) neobsahuje specifická upozornění, která se mají vyloučit, takže se nezobrazí žádná upozornění.

    > [!TIP]
    > Pokud zobrazíte dialogové okno **Najít** kliknutím na klávesovou zkratku **CTRL** +**F** , můžete vyhledat obsah okna **výstup** .

Další informace najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Vytvoření sestavení pro vydání

Můžete vytvořit verzi ukázkové aplikace optimalizované pro odeslání IT. Pro Build vydaných verzí určíte, že se spustitelný soubor zkopíruje do sdílené síťové složky před tím, než se sestaví.

Další informace naleznete v tématu [Postupy: Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md) a [sestavování a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Zadejte sestavení pro vydání pro Visual Basic

1. Otevřete **Návrhář projektu**.

     ![Nabídka zobrazení, příkaz stránky vlastností](../ide/media/buildwalk_viewpropertypages.png)

1. Vyberte stránku **kompilovat** .

1. V seznamu **Konfigurace** vyberte možnost **verze**.

1. V seznamu **platforma** vyberte možnost **x86**.

1. V poli **výstupní cesta sestavení** zadejte síťovou cestu.

     Můžete například zadat `\\myserver\builds`.

    > [!IMPORTANT]
    > Může se zobrazit okno se zprávou s upozorněním, že sdílená síťová složka, kterou jste zadali, nemusí být důvěryhodné umístění. Pokud důvěřujete umístění, které jste zadali, klikněte na tlačítko **OK** v okně se zprávou.

1. Sestavte aplikaci.

     ![Příkaz Sestavit řešení v nabídce sestavení](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Zadejte sestavení pro vydání pro C \#

1. Otevřete **Návrhář projektu**.

     ![Nabídka zobrazení, příkaz stránky vlastností](../ide/media/buildwalk_viewpropertypages.png)

1. Vyberte stránku **sestavení** .

1. V seznamu **Konfigurace** vyberte možnost **verze**.

1. V seznamu **platforma** vyberte možnost **x86**.

1. V poli **výstupní cesta** zadejte síťovou cestu.

     Můžete například zadat `\\myserver\builds`.

    > [!IMPORTANT]
    > Může se zobrazit okno se zprávou s upozorněním, že sdílená síťová složka, kterou jste zadali, nemusí být důvěryhodné umístění. Pokud důvěřujete umístění, které jste zadali, klikněte na tlačítko **OK** v okně se zprávou.

1. Na **standardním panelu nástrojů**nastavte Konfigurace řešení na **release** a platformy řešení na **x86**.

1. Sestavte aplikaci.

     ![Příkaz Sestavit řešení v nabídce sestavení](../ide/media/exploreide-buildsolution.png)

   Spustitelný soubor je zkopírován do síťové cesty, kterou jste zadali. Cesta by byla `\\myserver\builds\\FileName.exe`.

Blahopřejeme! Úspěšně jste dokončili tento návod.

## <a name="see-also"></a>Viz také:

- [Návod: sestavení projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Přehled Předkompilace projektu webové aplikace v ASP.NET](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md)
