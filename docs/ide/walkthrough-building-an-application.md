---
title: 'Návod: Sestavení aplikace'
ms.date: 09/25/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2987df6c8ed8a26c2cf95020e26f67c36721d676
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672779"
---
# <a name="walkthrough-build-an-application"></a>Návod: Sestavení aplikace

V tomto návodu se seznámíte se podrobněji seznamujete s několik možností, které můžete konfigurovat při sestavování aplikací pomocí sady Visual Studio. Budete vytvářet vlastní proces sestavení, skryjete některé varovné zprávy a zvýšíte výstupní informace sestavení pro ukázkovou aplikaci.

## <a name="install-the-sample-application"></a>Nainstalovat ukázkovou aplikaci

Stáhněte si [Úvod do vytváření aplikací WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) vzorku. Zvolte buď C# nebo Visual Basic. Po *ZIP* soubor byl stažen, rozbalte ho a otevřete *ExpenseItIntro.sln* souborů pomocí sady Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Vytvořit vlastní proces sestavení

Když vytvoříte řešení, konfigurace sestavení pro ladění a vydání a jejich výchozí cíle platformy jsou definovány pro řešení automaticky. Můžete poté přizpůsobit tyto konfigurace nebo vytvořit vlastní. Konfigurace sestavení určují typ sestavení. Platformy sestavení určují operační systém, který aplikace cílí pro danou konfiguraci. Další informace najdete v tématu [pochopení konfigurace sestavení](../ide/understanding-build-configurations.md), [platformy sestavení porozumění](../ide/understanding-build-platforms.md), a [postupy: nastavení ladění a vydání konfigurace](../debugger/how-to-set-debug-and-release-configurations.md).

Můžete změnit nebo vytvořit konfigurace a nastavení platformy pomocí **nástroje Configuration Manager** dialogové okno. V tomto postupu vytvoříte konfiguraci sestavení pro testování.

### <a name="create-a-build-configuration"></a>Vytvořit vlastní proces sestavení

1. Otevřít **nástroje Configuration Manager** dialogové okno.

   ![Vytvoření nabídky, příkaz nástroje Configuration Manager](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. V **konfigurace aktivního řešení** klikněte na položku  **\<nový... \>**.

1. V **nová konfigurace řešení** dialogové okno, pojmenujte novou konfiguraci `Test`, zkopírujte nastavení z existující **ladění** konfigurace a klikněte na tlačítko **OK**tlačítko.

   ![Nové řešení dialogové okno Konfigurace](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. V **platformou aktivního řešení** klikněte na položku  **\<nový... \>**.

1. V **nová platforma řešení** dialogového okna zvolte **x64**a nekopírujte nastavení z x86 platformy.

   ![Nové řešení platformy dialogové okno](../ide/media/buildwalk_newsolutionplatform.png)

1. Zvolte **OK** tlačítko.

   Byla změněna konfigurace aktivního řešení na **Test** s platformou aktivního řešení nastavenou na x64.

   ![Configuration Manager s konfigurací testu](../ide/media/buildwalk_configmanagertestconfig.png)

1. Zvolte **Zavřít**.

Můžete rychle ověřit nebo změnit konfiguraci aktivního řešení pomocí **konfigurace řešení** seznamu **standardní** nástrojů.

![Možnost konfigurace řešení standardním panelu nástrojů](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Sestavení aplikace

V dalším kroku vytvoříte řešení s vlastní konfigurací sestavení.

### <a name="build-the-solution"></a>Sestavte řešení

-   V panelu nabídky zvolte **sestavení** > **sestavit řešení**.

    **Výstup** okně se zobrazí výsledky sestavení. Sestavení bylo úspěšné.

## <a name="hide-compiler-warnings"></a>Skrýt upozornění kompilátoru

Potom ukážeme některé kód, který způsobí upozornění na generovaný kompilátorem.

1. V C# projekt, otevřete *ExpenseReportPage.xaml.cs* souboru. V **ExpenseReportPage** metodu, přidejte následující kód: `int i;`.

    NEBO

    V projektu jazyka Visual Basic otevřete *ExpenseReportPage.xaml.vb* souboru. V konstruktoru vlastní **Public Sub New...** , přidejte následující kód: `Dim i`.

1. Sestavte řešení.

**Výstup** okně se zobrazí výsledky sestavení. Sestavení bylo úspěšné, ale byly vygenerovány upozornění:

![Výstupní okno Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Visual C okno výstup&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Je můžete dočasně skrýt některé varovné zprávy během sestavení a nenechat je zbytečně zatěžovat výstup sestavení.

### <a name="hide-a-specific-c-warning"></a>Skrýt konkrétní C# upozornění

1. V **Průzkumníka řešení**, zvolte uzel projektu nejvyšší úrovně.

1. V panelu nabídky zvolte **zobrazení** > **stránky vlastností**.

     **Návrháře projektu** otevře.

1. Zvolte **sestavení** stránky a pak na **potlačit upozornění** zadejte číslo upozornění **0168**.

     ![Vytvořit stránku, Návrhář projektu](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Další informace najdete v tématu [stránku sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Sestavte řešení.

     **Výstup** okně zobrazí pouze souhrnné informace o sestavení.

     ![Okno výstup, Visual C&#35; upozornění sestavení](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Potlačení všech chyb sestavení Visual Basic

1. V **Průzkumníka řešení**, zvolte uzel projektu nejvyšší úrovně.

2. V panelu nabídky zvolte **zobrazení** > **stránky vlastností**.

     **Návrháře projektu** otevře.

3. Na **kompilaci** stránky, vyberte **zakázat všechna upozornění** zaškrtávací políčko.

     ![Stránka kompilovat, Návrhář projektu](../ide/media/buildwalk_vbsuppresswarnings.png)

     Další informace najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Sestavte řešení.

   **Výstup** okně zobrazí pouze souhrnné informace o sestavení.

   ![Upozornění sestavení okno výstup, Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Další informace najdete v tématu [postupy: potlačení upozornění kompilátoru](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Zobrazit další podrobnosti v okně výstupu sestavení

Můžete změnit, se zobrazí v tom, kolik informací o procesu sestavení **výstup** okna. Podrobnost sestavení je obvykle nastavená **minimální**, což znamená, že **výstup** okně zobrazí pouze souhrnné informace o procesu sestavení spolu se všechna upozornění s vysokou prioritou a chyby. Můžete zobrazit další informace o sestavení pomocí [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Pokud zobrazíte další informace, bude trvat déle k dokončení sestavení.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Změnit množství informací v okně Výstup

1. Otevřít **možnosti** dialogové okno.

     ![Příkaz Možnosti v nabídce Nástroje](../ide/media/exploreide-toolsoptionsmenu.png)

1. Zvolte **projekty a řešení** kategorie a klikněte na tlačítko **sestavíte a spustíte** stránky.

1. V **podrobnosti výstupu sestavení projektu nástroje MSBuild** klikněte na položku **normální**a klikněte na tlačítko **OK** tlačítko.

1. V panelu nabídky zvolte **sestavení** > **Vyčistit řešení**.

1. Sestavte řešení a pak si projděte informace v **výstup** okna.

     Informace o sestavení obsahují čas spuštění sestavení (umístěný na začátku) a pořadí, ve kterém jsou zpracovány soubory. Tyto informace zahrnují také syntaxi skutečného kompilátoru, která sadě Visual Studio spustí během sestavování.

     Například v C# sestavení, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) možnost uvádí kód upozornění **1762**, který jste zadali dříve v tomto tématu, a tři další varování.

     V sestavení Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) neobsahuje konkrétní upozornění k vyloučení, takže se nezobrazují žádné upozornění.

    > [!TIP]
    > Můžete vyhledávat obsah **výstup** okna, je-li je zobrazit **najít** dialogové okno kliknutím **Ctrl**+**F** klíče.

Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Vytváření sestavení pro vydání

Můžete vytvořit verzi ukázkovou aplikaci, která je optimalizována pro jeho dodání. Pro sestavení vydání zadáte, že spustitelný soubor je zkopírován do sdílené síťové složky, předtím, než se sestavování.

Další informace najdete v tématu [postupy: Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md) a [sestavení a vyčištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Určení verze sestavení v jazyce Visual Basic

1. Otevřít **Návrhář projektu**.

     ![Nabídka Zobrazit, příkaz stránky vlastností](../ide/media/buildwalk_viewpropertypages.png)

1. Zvolte **kompilaci** stránky.

1. V **konfigurace** klikněte na položku **vydání**.

1. V **platformy** klikněte na položku **x86**.

1. V **výstupní cesta sestavení** zadejte síťovou cestu.

     Například můžete zadat `\\myserver\builds`.

    > [!IMPORTANT]
    > Okno se zprávou se může zobrazit upozornění, že sdílené síťové složky, které jste zadali nemusí být důvěryhodným umístěním. Pokud důvěřujete umístění, které jste zadali, zvolte **OK** tlačítka v okně se zprávou.

1. Sestavení aplikace.

     ![V nabídce sestavení sestavit řešení – příkaz](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Určení verze sestavení proC# #

1. Otevřít **Návrhář projektu**.

     ![Nabídka Zobrazit, příkaz stránky vlastností](../ide/media/buildwalk_viewpropertypages.png)

1. Zvolte **sestavení** stránky.

1. V **konfigurace** klikněte na položku **vydání**.

1. V **platformy** klikněte na položku **x86**.

1. V **výstupní cesta** zadejte síťovou cestu.

     Například můžete zadat `\\myserver\builds`.

    > [!IMPORTANT]
    > Okno se zprávou se může zobrazit upozornění, že sdílené síťové složky, které jste zadali nemusí být důvěryhodným umístěním. Pokud důvěřujete umístění, které jste zadali, zvolte **OK** tlačítka v okně se zprávou.

1. Na **standardním panelu nástrojů**, nastavena konfigurace řešení na **vydání** a platformy řešení na **x86**.

1. Sestavení aplikace.

     ![V nabídce sestavení sestavit řešení – příkaz](../ide/media/exploreide-buildsolution.png)

   Spustitelný soubor je zkopírován do síťové cesty, který jste zadali. Jeho cesta bude `\\myserver\builds\\FileName.exe`.

Blahopřejeme! Úspěšně jste dokončili tento návod.

## <a name="see-also"></a>Viz také:

- [Návod: Sestavení projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Přehled technologie ASP.NET do webové aplikace projektu předkompilace](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md)