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
ms.openlocfilehash: d94a525f9938b6845584b6d5872bd486e947025d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115407"
---
# <a name="walkthrough-build-an-application"></a>Návod: Sestavení aplikace

Dokončením tohoto návodu se lépe seznámíte s několika možnostmi, které můžete nakonfigurovat při vytváření aplikací pomocí sady Visual Studio. Vytvoříte vlastní konfiguraci sestavení, skryjete určité varovné zprávy a zvýšíte výstupní informace sestavení pro ukázkovou aplikaci.

## <a name="install-the-sample-application"></a>Instalace ukázkové aplikace

Stáhněte si [ukázku úvodu do vytváření aplikací WPF.](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) Zvolte c# nebo visual basic. Po stažení souboru *ZIP* jej extrahujte a otevřete soubor *ExpenseItIntro.sln* pomocí sady Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Vytvoření vlastní konfigurace sestavení

Při vytváření řešení, ladění a uvolnění konfigurace sestavení a jejich výchozí cíle platformy jsou definovány pro řešení automaticky. Potom můžete přizpůsobit tyto konfigurace nebo vytvořit vlastní. Konfigurace sestavení určují typ sestavení. Platformy sestavení určují operační systém, na který se aplikace zaměřuje pro danou konfiguraci. Další informace naleznete [v tématech Principy konfigurací sestavení](../ide/understanding-build-configurations.md), [Principy platforem sestavení](../ide/understanding-build-platforms.md)a [Postup: Nastavení konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md).

Konfigurace a nastavení platformy můžete změnit nebo vytvořit pomocí dialogového okna **Správce konfigurace.** V tomto postupu vytvoříte konfiguraci sestavení pro testování.

### <a name="create-a-build-configuration"></a>Vytvoření konfigurace sestavení

1. Otevřete dialogové okno **Správce konfigurace.**

   ![Nabídka Sestavení, příkaz Správce konfigurace](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. V seznamu **Konfigurace aktivního řešení** zvolte ** \<Nový... \>**.

1. V dialogovém okně **Nová konfigurace** řešení `Test`pojmenujte novou konfiguraci , zkopírujte nastavení z existující konfigurace **ladění** a pak zvolte tlačítko **OK.**

   ![Dialogové okno Nová konfigurace řešení](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. V seznamu **Aktivní platforma řešení** zvolte ** \<Nový... \>**.

1. V dialogovém okně **Nová platforma řešení** zvolte **x64**a nekopírujte nastavení z platformy x86.

   ![Dialogové okno Nová platforma řešení](../ide/media/buildwalk_newsolutionplatform.png)

1. Zvolte tlačítko **OK.**

   Konfigurace aktivního řešení byla změněna na **Test** s aktivní platformou řešení nastavenou na x64.

   ![Správce konfigurace s konfigurací testu](../ide/media/buildwalk_configmanagertestconfig.png)

1. Zvolte **Zavřít**.

Konfiguraci aktivního řešení můžete rychle ověřit nebo změnit pomocí seznamu **Konfigurace řešení** na panelu nástrojů **Standardní.**

![Standardní panel nástrojů Možnost Konfigurace řešení](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Sestavení aplikace

Dále vytvoříte řešení s vlastní konfigurací sestavení.

### <a name="build-the-solution"></a>Sestavení řešení

- Na řádku nabídek zvolte **Build** > **Build Build Solution**nebo stiskněte **Ctrl**+**Shift**+**B**.

    Okno **Výstup** zobrazuje výsledky sestavení. Sestavení bylo úspěšné.

## <a name="hide-compiler-warnings"></a>Skrýt upozornění kompilátoru

Dále budeme zavádět nějaký kód, který způsobí, že upozornění, které mají být generovány kompilátorem.

1. V projektu C# otevřete *soubor ExpenseReportPage.xaml.cs.* V metodě **ExpenseReportPage** přidejte `int i;`následující kód: .

    NEBO

    V projektu jazyka Visual Basic otevřete soubor *ExpenseReportPage.xaml.vb.* Do vlastního konstruktoru **Public Sub New...** `Dim i`přidejte následující kód: .

1. Sestavte řešení.

Okno **Výstup** zobrazuje výsledky sestavení. Sestavení proběhlo úspěšně, ale byla vygenerována upozornění:

![Výstupní okno Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Vizuální&#35; okna výstupu](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Můžete dočasně skrýt některé varovné zprávy během sestavení, spíše než je zaneřádit výstup sestavení.

### <a name="hide-a-specific-c-warning"></a>Skrytí upozornění konkrétního jazyka C#

1. V **Průzkumníku řešení**zvolte uzel projektu nejvyšší úrovně.

1. Na řádku nabídek zvolte **Zobrazit** > **stránky vlastností**.

     Otevře se **Návrhář projektu.**

1. Zvolte stránku **Sestavení** a pak v poli **Potlačit upozornění** zadejte číslo upozornění **0168**.

     ![Stránka sestavení, Návrhář projektu](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Další informace naleznete v [tématu Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Sestavte řešení.

     Okno **Výstup** zobrazuje pouze souhrnné informace pro sestavení.

     ![Výstupní okno, vizuální c&#35; upozornění sestavení](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Potlačit všechna upozornění na sestavení jazyka Visual Basic

1. V **Průzkumníku řešení**zvolte uzel projektu nejvyšší úrovně.

2. Na řádku nabídek zvolte **Zobrazit** > **stránky vlastností**.

     Otevře se **Návrhář projektu.**

3. Na stránce **Kompilace** zaškrtněte políčko **Zakázat všechna upozornění.**

     ![Stránka kompilace, Návrhář projektu](../ide/media/buildwalk_vbsuppresswarnings.png)

     Další informace naleznete [v tématu Konfigurace upozornění v jazyce Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Sestavte řešení.

   Okno **Výstup** zobrazuje pouze souhrnné informace pro sestavení.

   ![Okno výstupu, upozornění sestavení jazyka Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Další informace naleznete v [tématu How to: Suppress compiler warnings](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Zobrazení dalších podrobností sestavení v okně Výstup

Můžete změnit, kolik informací o procesu sestavení se zobrazí v okně **Výstup.** Podrobnost sestavení je obvykle nastavena na **minimální**, což znamená, že okno **Výstup** zobrazuje pouze souhrn procesu sestavení spolu s upozorněními nebo chybami s vysokou prioritou. Další informace o sestavení můžete zobrazit pomocí [dialogového okna Možnosti, Projekty a řešení, Sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Pokud zobrazíte další informace, dokončení sestavení bude trvat déle.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Změna množství informací v okně Výstup

1. Otevřete dialogové okno **Možnosti.**

     ![Příkaz Volby v nabídce Nástroje](../ide/media/exploreide-toolsoptionsmenu.png)

1. Zvolte kategorii **Projekty a řešení** a pak zvolte stránku **Sestavení a spuštění.**

1. V seznamu **podrobností o vytváření sestavení projektu MSBuild** zvolte **Normální**a pak zvolte tlačítko **OK.**

1. Na řádku nabídek zvolte **Sestavit** > **čisté řešení**.

1. Vytvořte řešení a zkontrolujte informace v okně **Výstup.**

     Informace o sestavení zahrnuje čas spuštění sestavení (umístěné na začátku) a pořadí, ve kterém byly zpracovány soubory. Tyto informace také zahrnují skutečnou syntaxi kompilátoru, kterou visual studio spouští během sestavení.

     Například v sestavení C# [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) uvádí kód upozornění, **0168**, který jste zadali dříve v tomto tématu, spolu s dalšími třemi upozorněními.

     V sestavení jazyka [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) neobsahuje konkrétní upozornění vyloučit, takže se zobrazí žádná upozornění.

    > [!TIP]
    > Obsah okna **Výstup** můžete prohledat, pokud zobrazíte dialogové okno **Najít,** a to výběrem kláves **Ctrl**+**F.**

Další informace naleznete v [tématu Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Vytváření sestavení pro vydání

Můžete vytvořit verzi ukázkové aplikace, která je optimalizovaná pro její odesílání. Pro sestavení verze určíte, že spustitelný soubor je zkopírován do sdílené síťové složky před spuštěním sestavení.

Další informace naleznete v [tématu Postup: Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md) a [sestavení a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Určení sestavení verze pro jazyk Visual Basic

1. Otevřete **Návrháře projektů**.

     ![Nabídka Zobrazení, příkaz Stránky vlastností](../ide/media/buildwalk_viewpropertypages.png)

1. Zvolte stránku **Kompilace.**

1. V seznamu **Konfigurace** zvolte **Uvolnit**.

1. V seznamu **Platforma** zvolte **x86**.

1. V poli **Sestavit výstupní cestu** zadejte síťovou cestu.

     Můžete například zadat `\\myserver\builds`.

    > [!IMPORTANT]
    > Může se zobrazit okno se zprávou s upozorněním, že zadaná síťová sdílená síť ová síťová sdílená síť ová, že se nemusí na popřípadě ustavit jako důvěryhodné umístění. Pokud zadanému umístění důvěřujete, zvolte v poli se zprávou tlačítko **OK.**

1. Sestavte aplikaci.

     ![Příkaz Sestavit řešení v nabídce Sestavení](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Určení sestavení verze pro C\#

1. Otevřete **Návrháře projektů**.

     ![Nabídka Zobrazení, příkaz Stránky vlastností](../ide/media/buildwalk_viewpropertypages.png)

1. Zvolte stránku **Sestavení.**

1. V seznamu **Konfigurace** zvolte **Uvolnit**.

1. V seznamu **Platforma** zvolte **x86**.

1. V poli **Výstupní cesta** zadejte síťovou cestu.

     Můžete například zadat `\\myserver\builds`.

    > [!IMPORTANT]
    > Může se zobrazit okno se zprávou s upozorněním, že zadaná síťová sdílená síť ová síťová sdílená síť ová, že se nemusí na popřípadě ustavit jako důvěryhodné umístění. Pokud zadanému umístění důvěřujete, zvolte v poli se zprávou tlačítko **OK.**

1. Na **panelu nástrojů Standard**nastavte konfigurace řešení na **verzi** a platformy řešení na **x86**.

1. Sestavte aplikaci.

     ![Příkaz Sestavit řešení v nabídce Sestavení](../ide/media/exploreide-buildsolution.png)

   Spustitelný soubor se zkopíruje do zadané síťové cesty. Jeho cesta `\\myserver\builds\\FileName.exe`by byla .

Blahopřejeme! Tento návod jste úspěšně dokončili.

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET přehled předkompilace projektu webové aplikace](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Návod: Použití MSBuild](../msbuild/walkthrough-using-msbuild.md)
