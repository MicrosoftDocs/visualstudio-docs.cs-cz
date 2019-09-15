---
title: 'Krok 1: Vytvoření projektu a přidání tabulky do formuláře'
ms.date: 05/31/2019
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b57164938f8256743f314d1c302a24547f6074d
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987797"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1: Vytvoření projektu a přidání tabulky do formuláře

Prvním krokem při vytváření porovnávací hry je vytvořit projekt a přidat tabulku do formuláře. Tabulka pomáhá zarovnat ikony do mřížky 4x4. Nastavením několika vlastností můžete také vylepšit vzhled hrací plochy.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Vytvoření projektu a přidání tabulky do formuláře

::: moniker range="vs-2017"

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. Na levé straně dialogového okna **Nový projekt** vyberte buď **vizuál C#**  , nebo **Visual Basic** , a pak zvolte **Windows Desktop**.

1. V seznamu šablon vyberte šablonu **model Windows Forms App (.NET Framework)** , pojmenujte ji *MatchingGame*a pak klikněte na tlačítko **OK** .

    Zobrazí se formulář s názvem *Form1.cs* nebo *Form1. vb* v závislosti na zvoleném programovacím jazyce.

   > [!NOTE]
   > Pokud nevidíte šablonu **aplikace model Windows Forms App (.NET Framework)** , nainstalujte úlohu **vývoj desktopových aplikací .NET** pomocí instalační program pro Visual Studio.<br/><br/>![Úloha vývoj desktopových aplikací .NET v Instalační program pro Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [instalace sady Visual Studio](../install/install-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** zadejte nebo zadejte *model Windows Forms* do vyhledávacího pole.

1. Zvolte šablonu **aplikace model Windows Forms App (.NET Framework)** a klikněte na tlačítko **Další**.

   ![Vyberte šablonu Visual Basic pro aplikaci model Windows Forms (.NET Framework).](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **aplikace model Windows Forms App (.NET Framework)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V části Instalační program pro Visual Studio klikněte na možnost zvolit úlohu **vývoj desktopových aplikací .NET** .
   >
   > ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu.

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MatchingGame* do pole **název projektu** . Pak zvolte **vytvořit**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Nastavení vlastností pro formulář

1. V okně **vlastnosti** nastavte následující vlastnosti formuláře.

   1. Změňte vlastnost **text** formuláře z **Form1** na **porovnávací hru**. Tento text se zobrazí v horní části herního okna.

   2. Nastavte velikost formuláře na šířku 550 pixelů a výšku 550 pixelů. To můžete provést buď nastavením vlastnosti **Size** na **550, 550**nebo přetažením rohu formuláře, dokud neuvidíte správnou velikost v pravém dolním rohu integrovaného vývojového prostředí (IDE).

2. Zobrazení panelu nástrojů výběrem karty **panelu nástrojů** na levé straně rozhraní IDE.

3. Přetáhněte ovládací prvek z kategorie kontejnery v sadě nástrojů a nastavte pro něj následující vlastnosti. <xref:System.Windows.Forms.TableLayoutPanel>

   1. Nastavte vlastnost **BackColor** na **hodnotu CornflowerBlue**. Chcete-li to provést, otevřete dialogové okno **BackColor** výběrem šipky rozevíracího seznamu vedle vlastnosti **BackColor** v okně **vlastnosti** .  Pak zvolte kartu **Web** v dialogovém okně **BackColor** , abyste zobrazili seznam dostupných názvů barev.

      > [!NOTE]
      > Barvy nejsou v abecedním pořadí a **hodnotu CornflowerBlue** se blíží k dolnímu okraji seznamu.

   2. Nastavte vlastnost **Dock** na **Fill** tak, že vyberete tlačítko rozevíracího seznamu vedle vlastnosti a zvolíte velké prostřední tlačítko. Rozšíříte tak tabulku, aby zahrnovala celý formulář.

   3. Nastavte vlastnost **CellBorderStyle** na hodnotu **inkrýt**. Nastavíte tak vizuální hranice mezi každou buňkou na ploše.

   4. Kliknutím na tlačítko trojúhelníku v pravém horním rohu kontejneru TableLayoutPanel zobrazíte nabídku úloh.

   5. V nabídce Úloha klikněte dvakrát na možnost **Přidat řádek** a přidejte tak další dva řádky. potom kliknutím na **Přidat sloupec** dvakrát přidejte další dva sloupce.

   6. V nabídce úloha vyberte možnost **Upravit řádky a sloupce** a otevřete tak okno **styly sloupců a řádků** . Zvolte všechny sloupce, zvolte tlačítko **procento** a pak nastavte šířku každého sloupce na 25 procent celkové šířky. Pak z rozevíracího seznamu v horní části okna vyberte **řádky** a nastavte výšku každého řádku na 25 procent. Až skončíte, klikněte na tlačítko **OK** .

      Váš kontejner TableLayoutPanel by nyní měl být mřížka 4x4, se 16 stejně velkými čtvercovými buňkami. Na místě těchto řádků a sloupců se později zobrazí obrázky ikon.

4. Kontejner TableLayoutPanel musí být vybrán v editoru formuláře. Pokud to chcete ověřit, měli byste vidět **tableLayoutPanel1** v horní části okna **vlastnosti** . Pokud není vybrána, vyberte kontejner TableLayoutPanel ve formuláři nebo ho vyberte v ovládacím prvku rozevírací seznam v horní části okna **vlastnosti** .

    Když je kontejner TableLayoutPanel vybrán, otevřete sadu nástrojů a přidejte <xref:System.Windows.Forms.Label> ovládací prvek (umístěný v kategorii **běžné ovládací prvky** ) do levé horní buňky kontejneru TableLayoutPanel. Ovládací prvek popisek by teď měl být vybraný v integrovaném vývojovém prostředí. Nastavte pro něj následující vlastnosti.

   1. Ujistěte se, že vlastnost **BackColor** popisku je nastavená na **hodnotu CornflowerBlue**.

   2. Nastavte vlastnost **AutoSize** na **hodnotu false**.

   3. Nastavte vlastnost **Dock** na **Fill**.

   4. Nastavte vlastnost **TextAlign** na **hodnotu MiddleCenter** výběrem rozevíracího tlačítka vedle vlastnosti a následným kliknutím na prostřední tlačítko. Ikona se tak zobrazí uprostřed buňky.

   5. Vyberte vlastnost **Font** . Mělo by se zobrazit tlačítko se třemi tečkami ( **...** ).

   6. Klikněte na tlačítko se třemi tečkami a nastavte hodnotu **písma** na **Webdings**, **styl písma** na **tučné**a **Velikost** na **48**.

   7. Nastavte vlastnost **text** popisku na písmeno **c**.

        Levá horní buňka v kontejneru TableLayoutPanel by měla nyní obsahovat černé pole zarovnané na střed na modrém pozadí.

       > [!NOTE]
       > Písmo Webdings je písmo ikon dodávané s operačním systémem Windows. Ve vaší porovnávací hře musí hráči hledat dvojice ikon, takže toto písmo použijete k zobrazení ikon, které mají být spárovány. Místo vložení **c** do vlastnosti **text** zkuste zadat různá písmena, abyste viděli, jaké ikony se zobrazí. Vykřičník je pavouk, velké písmeno N je oko a čárka je čili paprička.

5. Vyberte ovládací prvek popisku a zkopírujte jej na další buňku v kontejneru TableLayoutPanel. (**Vyberte klávesy** **CTRL +** +nebo na panelu nabídek vyberte možnost **Upravit** > **kopii**.) Potom jej vložte. (Stiskněte klávesy **CTRL**+**v** nebo na panelu nabídek vyberte možnost **Upravit** > **vložení**.) Kopie prvního popisku se zobrazí v druhé buňce kontejneru TableLayoutPanel. Vložte ho znovu a pod třetí buňku se zobrazí další popisek. Nechejte vkládat ovládací prvky popisku, dokud nebudou všechny buňky vyplněny.

   > [!NOTE]
   > Pokud vložíte příliš mnoho časů, rozhraní IDE přidá nový řádek do kontejneru TableLayoutPanel, aby měl místo pro přidání nového ovládacího prvku popisek. Akci můžete vrátit zpět. Chcete-li novou buňku odebrat, **stiskněte klávesy CTRL**+**Z** nebo na panelu nabídek vyberte možnost **Upravit** > **zpět**.

    Rozvržení vašeho formuláře je nyní hotovo. Měl by vypadat podobně jako na následujícím obrázku.

    ![Formulář počáteční vyhovující hry](../ide/media/express_tut4step1.png)<br/>*Formulář počáteční vyhovující hry*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 2: Přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Pokud se chcete vrátit k tématu Přehled, [Přečtěte si kurz 3: Vytvořte porovnávací hru](../ide/tutorial-3-create-a-matching-game.md).
