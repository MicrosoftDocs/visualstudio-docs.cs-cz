---
title: 'Krok 1: Vytvořte projekt a přidejte do svého formuláře tabulku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c49a3e9ac7c4a37c1c030d631667d90b274143cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934688"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1: Vytvořte projekt a přidejte do svého formuláře tabulku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prvním krokem při vytváření porovnávací hry je vytvořit projekt a přidat tabulku do formuláře. Tabulka pomáhá zarovnat ikony do mřížky 4x4. Nastavením několika vlastností můžete také vylepšit vzhled hrací plochy.  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Vytvoření projektu a přidání tabulky do formuláře  
  
1. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. Pokud nepoužíváte Visual Studio Express, musíte nejprve vybrat programovací jazyk. Z **nainstalované šablony** , zvolte buď **Visual C#** nebo **jazyka Visual Basic**.  
  
3. V seznamu šablon projektu vyberte **formulářová aplikace Windows**, pojmenujte projekt **Porovnávací hra**a klikněte na tlačítko **OK** tlačítko.  
  
4. V **vlastnosti** okno, nastavte následující vlastnosti formuláře.  
  
   1.  Změna formuláře **Text** vlastnost z **Form1** k **Porovnávací hra**. Tento text se zobrazí v horní části herního okna.  
  
   2.  Nastavte velikost formuláře na šířku 550 pixelů a výšku 550 pixelů. Uděláte to buď tak, že nastavíte **velikost** vlastnost **550, 550**, nebo tažením rohu formuláře, dokud se nezobrazí správná velikost v pravém horním rohu na integrované vývojové prostředí ( INTEGROVANÉ VÝVOJOVÉ PROSTŘEDÍ).  
  
5. Zobrazit panel nástrojů výběrem **nástrojů** karty na levé straně rozhraní IDE.  
  
6. Přetáhněte `TableLayoutPanel` ovládacího prvku **kontejnery** kategorie na panelu nástrojů a pak nastavte pro něj následující vlastnosti.  
  
   1. Nastavte **BackColor** vlastnost **CornflowerBlue**. Chcete-li to provést, otevřete **BackColor** dialogové okno kliknutím na šipku rozevíracího seznamu vedle položky **BackColor** vlastnost **vlastnosti** okna.  Poté vyberte položku **webové** kartu **BackColor** dialogové okno k zobrazení seznamu názvů dostupných barev.  
  
      > [!NOTE]
      >  Barvy nejsou zobrazeny v abecedním pořadí a položka CornflowerBlue je v dolní části seznamu.  
  
   2. Nastavte **Dock** vlastnost **vyplnit** výběrem rozevírací tlačítko vedle vlastnosti a kliknutím na velké prostřední tlačítko. Rozšíříte tak tabulku, aby zahrnovala celý formulář.  
  
   3. Nastavte **CellBorderStyle** vlastnost **Inset**. Nastavíte tak vizuální hranice mezi každou buňkou na ploše.  
  
   4. Kliknutím na tlačítko trojúhelníku v pravém horním rohu kontejneru TableLayoutPanel zobrazíte nabídku úloh.  
  
   5. V nabídce úloh, zvolte **přidat řádek** dvakrát a přidejte další dva řádky, klikněte na tlačítko **přidat sloupec** dvakrát přidáte další dva sloupce.  
  
   6. V nabídce úloh, zvolte **upravit řádky a sloupce** otevřít **styly sloupců a řádků** okna. Vyberte jednotlivé sloupce, vyberte **procent** přepínač a pak nastavte šířku každého sloupce na 25 procent celkové šířky. Potom vyberte **řádky** z rozevíracího seznamu pole v horní části okna a nastavte výšku každého řádku na 25 procent. Jakmile budete hotovi, zvolte **OK** tlačítko.  
  
      Váš kontejner TableLayoutPanel by nyní měl být mřížka 4x4, se 16 stejně velkými čtvercovými buňkami. Na místě těchto řádků a sloupců se později zobrazí obrázky ikon.  
  
7. Kontejner TableLayoutPanel musí být vybrán v editoru formuláře. Chcete-li to ověřit, měli byste vidět **tableLayoutPanel1** v horní části **vlastnosti** okna. Pokud není vybraná, vyberte TableLayoutPanel ve formuláři nebo jej zvolte v ovládacím prvku rozevíracího seznamu v horní části **vlastnosti** okna.  
  
    Zatímco kontejner TableLayoutPanel vybrán, otevřete sadu nástrojů a přidejte **popisek** ovládacího prvku (umístěný ve **běžné ovládací prvky** kategorie) na levou horní buňky kontejneru TableLayoutPanel. `Label` By měl nyní být vybrán ovládací prvek v integrovaném vývojovém prostředí. Nastavte pro něj následující vlastnosti.  
  
   1.  Ujistěte se, že popisku **BackColor** je nastavena na **CornflowerBlue**.  
  
   2.  Nastavte **AutoSize** vlastnost **False**.  
  
   3.  Nastavte **Dock** vlastnost **vyplnit**.  
  
   4.  Nastavte **TextAlign** vlastnost **MiddleCenter** výběrem rozevírací tlačítko vedle vlastnosti a pak kliknutím na prostřední tlačítko. Ikona se tak zobrazí uprostřed buňky.  
  
   5.  Zvolte **písmo** vlastnost. Mělo by se zobrazit tlačítko tří teček (...).  
  
   6.  Vyberte tlačítko se třemi tečkami a nastavte hodnotu **písmo** hodnota, která se **Webdings**, **styl písma** k **tučné**a **velikost** k **72**.  
  
   7.  Nastavte **Text** vlastnosti tohoto popisku na písmeno **c**.  
  
        Levá horní buňka v kontejneru TableLayoutPanel by měla nyní obsahovat černé pole zarovnané na střed na modrém pozadí.  
  
       > [!NOTE]
       >  Písmo Webdings je písmo ikon dodávané s operačním systémem Windows. Ve vaší porovnávací hře musí hráči hledat dvojice ikon, takže toto písmo použijete k zobrazení ikon, které mají být spárovány. Namísto vložení hodnoty **c** v **Text** vlastnost, zkuste zadat různá písmena a zjistit, jaké ikony se zobrazí. Vykřičník je pavouk, velké písmeno N je oko a čárka je čili paprička.  
  
8. Zvolte svůj ovládací prvek popisku a zkopírujte jej na další buňku v kontejneru TableLayoutPanel. (Stiskněte klávesy Ctrl + C nebo na panelu nabídek zvolte **upravit**, **kopírování**.) Potom jej vložte. (Stiskněte klávesy Ctrl + V nebo v řádku nabídek zvolte **upravit**, **vložit**.) Kopie prvního popisku se zobrazí v druhé buňce kontejneru TableLayoutPanel. Vložit jej znovu a ve třetí buňce se zobrazí další popisek. Pokračujte ve vkládání `Label` ovládací prvky, dokud nejsou vyplněny všechny buňky.  
  
   > [!NOTE]
   >  Pokud popisek vložíte příliš často, rozhraní IDE přidá do kontejneru TableLayoutPanel nový řádek tak, aby bylo místo pro přidání nového ovládacího prvku popisku. Akci můžete vrátit zpět. Chcete-li novou buňku odstranit, stiskněte klávesy Ctrl + Z nebo na panelu nabídek zvolte **upravit**, **zpět**.  
  
    Rozvržení vašeho formuláře je nyní hotovo. Mělo by vypadat jako na následujícím obrázku.  
  
    ![Počáteční odpovídající formulář](../ide/media/express-tut4step1.png "Express_Tut4Step1")  
   Počáteční formulář porovnávací hry  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 2: Add Random Object and List of Icons](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   K návratu na téma přehledu přejděte [Tutorial 3: Create a Matching Game](../ide/tutorial-3-create-a-matching-game.md).



