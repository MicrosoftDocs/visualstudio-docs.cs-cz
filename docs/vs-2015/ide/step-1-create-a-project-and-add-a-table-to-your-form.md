---
title: 'Krok 1: Vytvořte projekt a přidejte tabulku do formuláře | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a7f9930dc1619d6f35a6024bd0f754f7caeeb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643507"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1: Vytvořte projekt a přidejte do svého formuláře tabulku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prvním krokem při vytváření porovnávací hry je vytvořit projekt a přidat tabulku do formuláře. Tabulka pomáhá zarovnat ikony do mřížky 4x4. Nastavením několika vlastností můžete také vylepšit vzhled hrací plochy.

### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Vytvoření projektu a přidání tabulky do formuláře

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

2. Pokud nepoužíváte Visual Studio Express, musíte nejprve vybrat programovací jazyk. V seznamu **Nainstalované šablony** vyberte možnost **vizuál C#**  nebo **Visual Basic**.

3. V seznamu šablon projektu zvolte možnost **model Windows Forms aplikace**, pojmenujte projekt **MatchingGame**a pak klikněte na tlačítko **OK** .

4. V okně **vlastnosti** nastavte následující vlastnosti formuláře.

   1. Změňte vlastnost **text** formuláře z **Form1** na **porovnávací hru**. Tento text se zobrazí v horní části herního okna.

   2. Nastavte velikost formuláře na šířku 550 pixelů a výšku 550 pixelů. To můžete provést buď nastavením vlastnosti **Size** na **550, 550**nebo přetažením rohu formuláře, dokud neuvidíte správnou velikost v pravém dolním rohu integrovaného vývojového prostředí (IDE).

5. Zobrazení panelu nástrojů výběrem karty **panelu nástrojů** na levé straně rozhraní IDE.

6. Přetáhněte ovládací prvek `TableLayoutPanel` z kategorie **kontejnery** v sadě nástrojů a nastavte pro něj následující vlastnosti.

   1. Nastavte vlastnost **BackColor** na **hodnotu CornflowerBlue**. Chcete-li to provést, otevřete dialogové okno **BackColor** výběrem šipky rozevíracího seznamu vedle vlastnosti **BackColor** v okně **vlastnosti** .  Pak zvolte kartu **Web** v dialogovém okně **BackColor** , abyste zobrazili seznam dostupných názvů barev.

      > [!NOTE]
      > Barvy nejsou zobrazeny v abecedním pořadí a položka CornflowerBlue je v dolní části seznamu.

   2. Nastavte vlastnost **Dock** na **Fill** tak, že vyberete tlačítko rozevíracího seznamu vedle vlastnosti a zvolíte velké prostřední tlačítko. Rozšíříte tak tabulku, aby zahrnovala celý formulář.

   3. Nastavte vlastnost **CellBorderStyle** na hodnotu **inkrýt**. Nastavíte tak vizuální hranice mezi každou buňkou na ploše.

   4. Kliknutím na tlačítko trojúhelníku v pravém horním rohu kontejneru TableLayoutPanel zobrazíte nabídku úloh.

   5. V nabídce Úloha klikněte dvakrát na možnost **Přidat řádek** a přidejte tak další dva řádky. potom kliknutím na **Přidat sloupec** dvakrát přidejte další dva sloupce.

   6. V nabídce úloha vyberte možnost **Upravit řádky a sloupce** a otevřete tak okno **styly sloupců a řádků** . Zvolte všechny sloupce, zvolte tlačítko **procento** a pak nastavte šířku každého sloupce na 25 procent celkové šířky. Pak z rozevíracího seznamu v horní části okna vyberte **řádky** a nastavte výšku každého řádku na 25 procent. Až skončíte, klikněte na tlačítko **OK** .

      Váš kontejner TableLayoutPanel by nyní měl být mřížka 4x4, se 16 stejně velkými čtvercovými buňkami. Na místě těchto řádků a sloupců se později zobrazí obrázky ikon.

7. Kontejner TableLayoutPanel musí být vybrán v editoru formuláře. Pokud to chcete ověřit, měli byste vidět **tableLayoutPanel1** v horní části okna **vlastnosti** . Pokud není vybrána, vyberte kontejner TableLayoutPanel ve formuláři nebo ho vyberte v ovládacím prvku rozevírací seznam v horní části okna **vlastnosti** .

    Když je kontejner TableLayoutPanel vybrán, otevřete sadu nástrojů a přidejte ovládací prvek **popisek** (umístěný v kategorii **běžné ovládací prvky** ) do levé horní buňky kontejneru TableLayoutPanel. V integrovaném vývojovém prostředí by teď měl být vybraný ovládací prvek `Label`. Nastavte pro něj následující vlastnosti.

   1. Ujistěte se, že vlastnost **BackColor** popisku je nastavená na **hodnotu CornflowerBlue**.

   2. Nastavte vlastnost **AutoSize** na **hodnotu false**.

   3. Nastavte vlastnost **Dock** na **Fill**.

   4. Nastavte vlastnost **TextAlign** na **hodnotu MiddleCenter** výběrem rozevíracího tlačítka vedle vlastnosti a následným kliknutím na prostřední tlačítko. Ikona se tak zobrazí uprostřed buňky.

   5. Vyberte vlastnost **Font** . Mělo by se zobrazit tlačítko tří teček (...).

   6. Klikněte na tlačítko se třemi tečkami a nastavte hodnotu **písma** na **Webdings**, **styl písma** na **tučné**a **Velikost** na **72**.

   7. Nastavte vlastnost **text** popisku na písmeno **c**.

        Levá horní buňka v kontejneru TableLayoutPanel by měla nyní obsahovat černé pole zarovnané na střed na modrém pozadí.

       > [!NOTE]
       > Písmo Webdings je písmo ikon dodávané s operačním systémem Windows. Ve vaší porovnávací hře musí hráči hledat dvojice ikon, takže toto písmo použijete k zobrazení ikon, které mají být spárovány. Místo vložení **c** do vlastnosti **text** zkuste zadat různá písmena, abyste viděli, jaké ikony se zobrazí. Vykřičník je pavouk, velké písmeno N je oko a čárka je čili paprička.

8. Zvolte svůj ovládací prvek popisku a zkopírujte jej na další buňku v kontejneru TableLayoutPanel. (Vyberte klávesy CTRL + C nebo na panelu nabídek vyberte možnost **Upravit**, **Kopírovat**.) Pak jej vložte. (Stiskněte klávesy CTRL + V nebo na panelu nabídek vyberte možnost **Upravit**, **Vložit**.) Kopie prvního popisku se zobrazí v druhé buňce kontejneru TableLayoutPanel. Vložit jej znovu a ve třetí buňce se zobrazí další popisek. Pokračujte v vkládání `Label` ovládacích prvků, dokud nebudou všechny buňky vyplněny.

   > [!NOTE]
   > Pokud popisek vložíte příliš často, rozhraní IDE přidá do kontejneru TableLayoutPanel nový řádek tak, aby bylo místo pro přidání nového ovládacího prvku popisku. Akci můžete vrátit zpět. Chcete-li odebrat novou buňku, stiskněte klávesy CTRL + Z nebo na panelu nabídek vyberte možnost **Upravit**, **zpět**.

    Teď je váš formulář rozložený. Měl by vypadat jako na následujícím obrázku.

    ![Formulář počáteční vyhovující hry](../ide/media/express-tut4step1.png "Express_Tut4Step1") Formulář počáteční vyhovující hry

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Pokud se chcete vrátit k tématu Přehled, přečtěte si [kurz 3: vytvoření vyhovující hry](../ide/tutorial-3-create-a-matching-game.md).
