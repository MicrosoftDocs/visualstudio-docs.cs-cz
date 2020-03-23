---
title: 'Krok 1: Vytvoření projektu a přidání tabulky do formuláře'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1134fb5bb02bd8c78f347ef582f12da35074c36
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579930"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1: Vytvoření projektu a přidání tabulky do formuláře

Prvním krokem při vytváření porovnávací hry je vytvořit projekt a přidat tabulku do formuláře. Tabulka pomáhá zarovnat ikony do mřížky 4x4. Nastavením několika vlastností můžete také vylepšit vzhled hrací plochy.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Vytvoření projektu a přidání tabulky do formuláře

::: moniker range="vs-2017"

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. Na levé straně dialogového okna **Nový projekt** zvolte **visual c#** nebo **visual basic** a pak zvolte **Plochu systému Windows**.

1. V seznamu šablon zvolte šablonu **aplikace Windows Forms App (.NET Framework),** pojmenujte ji *MatchingGame*a pak zvolte tlačítko **OK.**

    V závislosti na vybraném programovacím jazyce se zobrazí formulář s názvem *Form1.cs* nebo *Form1.vb.*

   > [!NOTE]
   > Pokud šablonu aplikace **Windows Forms App (.NET Framework)** nevidíte, nainstalujte pracovní vytížení **pro vývoj plochy .NET** pomocí Instalační služby visual studia.<br/><br/>![Úloha vývoje plochy rozhraní .NET v Instalační službě sady Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [Instalace sady Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte windows *forms* do vyhledávacího pole. Dále zvolte **Plocha** ze seznamu **typ projektu.**

   Po použití filtru **typu projektu** zvolte šablonu aplikace Windows Forms **App (.NET Framework)** pro c# nebo visual basic a pak zvolte **Další**.

   ![Zvolte šablonu jazyka C# nebo Visual Basic pro aplikaci Windows Forms App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud šablonu **Aplikace Windows Forms (.NET Framework)** nevidíte, můžete ji nainstalovat z okna Vytvořit nový **projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Dále v Instalační službě sady Visual Studio zvolte zvolte **úlohu vývoje plochy .NET.**
   >
   > ![Úloha jádra .NET v Instalační službě sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy.

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MatchingGame* do pole **Název projektu.** Potom zvolte **Vytvořit**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Nastavení vlastností formuláře

1. V okně **Vlastnosti** nastavte následující vlastnosti formuláře.

   1. Změňte vlastnost **Text** formuláře z **Formuláře1** na **Odpovídající hru**. Tento text se zobrazí v horní části herního okna.

   2. Nastavte velikost formuláře na šířku 550 pixelů a výšku 550 pixelů. Můžete to provést buď nastavením **Size** vlastnost **550, 550**nebo přetažením rohu formuláře, dokud se zobrazí správná velikost v pravém dolním rohu integrovanévývojové prostředí (IDE).

2. Zobrazte panel nástrojů výběrem karty **Panel nástrojů** na levé straně ide.

3. Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek z kategorie **Kontejnery** v panelu nástrojů a nastavte pro něj následující vlastnosti.

   1. Nastavte vlastnost **BackColor** na **CornflowerBlue**. Chcete-li to provést, otevřete dialogové okno **Zpětbarevná** výběrem šipky rozevíracího seznamu vedle vlastnosti **BackColor** v okně **Vlastnosti.**  Potom zvolte **webovou** kartu v dialogovém okně **Zpětbarevná,** abyste zobrazili seznam dostupných názvů barev.

      > [!NOTE]
      > Barvy nejsou v abecedním pořadí a **CornflowerBlue** je v dolní části seznamu.

   2. Nastavte vlastnost **Dock** na **Výplň** tak, že vyberete rozbalovací tlačítko vedle vlastnosti a zvolíte velké prostřední tlačítko. Rozšíříte tak tabulku, aby zahrnovala celý formulář.

   3. Nastavte vlastnost **CellBorderStyle** na **Vsazení**. Nastavíte tak vizuální hranice mezi každou buňkou na ploše.

   4. Kliknutím na tlačítko trojúhelníku v pravém horním rohu kontejneru TableLayoutPanel zobrazíte nabídku úloh.

   5. V nabídce úkolu zvolte **Přidat řádek** dvakrát, chcete-li přidat další dva řádky, a pak zvolte **Přidat sloupec** dvakrát, abyste přidali další dva sloupce.

   6. V nabídce úkolů zvolte **Upravit řádky a sloupce,** abyste otevřeli okno **Styly sloupců a řádků.** Zvolte každý ze sloupců, zvolte možnost **Procento** a nastavte šířku každého sloupce na 25 procent celkové šířky. Pak vyberte **řádky** z rozevíracího pole v horní části okna a nastavte výšku každého řádku na 25 procent. Až budete hotovi, zvolte tlačítko **OK.**

      Váš kontejner TableLayoutPanel by nyní měl být mřížka 4x4, se 16 stejně velkými čtvercovými buňkami. Na místě těchto řádků a sloupců se později zobrazí obrázky ikon.

4. Kontejner TableLayoutPanel musí být vybrán v editoru formuláře. Chcete-li to ověřit, měli byste vidět **tableLayoutPanel1** v horní části okna **Vlastnosti.** Pokud není vybrána, zvolte TableLayoutPanel ve formuláři nebo ji zvolte v ovládacím prvku rozevírací v horní části okna **Vlastnosti.**

    Když je vybrána tabulka LayoutPanel, otevřete <xref:System.Windows.Forms.Label> panel nástrojů a přidejte ovládací prvek (umístěný v kategorii **Společné ovládací prvky)** do levé horní buňky TableLayoutPanel. Ovládací prvek popisek by nyní měla být vybrána v ide. Nastavte pro něj následující vlastnosti.

   1. Ujistěte se, že vlastnost **BackColor** štítku je nastavena na **CornflowerBlue**.

   2. Nastavte vlastnost **AutoSize** na **hodnotu False**.

   3. Nastavte vlastnost **Dock** na **Fill**.

   4. Nastavte vlastnost **TextAlign** na **MiddleCenter** tak, že zvolíte rozevírací tlačítko vedle vlastnosti a pak zvolíte prostřední tlačítko. Ikona se tak zobrazí uprostřed buňky.

   5. Zvolte **Vlastnost Písmo.** Mělo by se zobrazit tlačítko se třemi tečkami (**...**).

   6. Zvolte tlačítko se třemi tečkami a nastavte hodnotu **Písmo** na **Webdings**, **Styl písma** na **tučné**a **Velikost** na **48**.

   7. Nastavte **vlastnost Text** popisku na písmeno **c**.

        Levá horní buňka v kontejneru TableLayoutPanel by měla nyní obsahovat černé pole zarovnané na střed na modrém pozadí.

       > [!NOTE]
       > Písmo Webdings je písmo ikon dodávané s operačním systémem Windows. Ve vaší porovnávací hře musí hráči hledat dvojice ikon, takže toto písmo použijete k zobrazení ikon, které mají být spárovány. Místo vložení **c** do vlastnosti **Text** zkuste zadat různá písmena, abyste zjistili, jaké ikony se zobrazují. Vykřičník je pavouk, velké písmeno N je oko a čárka je čili paprička.

5. Zvolte ovládací prvek Label a zkopírujte ho do další buňky panelu TableLayout. (Zvolte klávesy **Ctrl**+**C** nebo na řádku nabídek zvolte **Upravit** > **kopii**.) Pak jej vložte. (Zvolte klávesy **Ctrl**+**V** nebo na řádku nabídek zvolte **Upravit** > **vložit**.) Kopie prvního labelu se zobrazí v druhé buňce panelu TableLayoutPanel. Vložte jej znovu a ve třetí buňce se zobrazí jiný popisek. Ponechte ovládací prvky Popisek v nos, dokud nebudou vyplněny všechny buňky.

   > [!NOTE]
   > Pokud vložíte příliš mnohokrát, ide přidá nový řádek TableLayoutPanel tak, aby má místo pro přidání nového label ovládacího prvku. Akci můžete vrátit zpět. Chcete-li odebrat novou buňku, zvolte klávesy **Ctrl**+**Z** nebo na řádku nabídek zvolte **Upravit** > **zpět**.

    Nyní je váš formulář rozložen. Mělo by vypadat podobně jako na následujícím obrázku.

    ![Počáteční formulář porovnávací hry](../ide/media/express_tut4step1.png)<br/>*Počáteční formulář porovnávací hry*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít k dalšímu kroku kurzu, [přečtěte si krok 2: Přidání náhodného objektu a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Chcete-li se vrátit k tématu [přehledu, přečtěte si téma 3: Vytvoření odpovídající hry](../ide/tutorial-3-create-a-matching-game.md).
