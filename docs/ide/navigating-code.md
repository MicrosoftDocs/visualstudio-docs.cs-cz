---
title: Navigační příkazy kódu
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: tglee
ms.workload:
- multiple
ms.openlocfilehash: 0216a71b675473d54aec9738ea7bdc85b7643841
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585818"
---
# <a name="navigate-code"></a>Navigace v kódu

Visual Studio poskytuje mnoho způsobů, jak procházet kód v editoru. Toto téma shrnuje různé způsoby navigace v kódu a obsahuje odkazy na témata, která jsou podrobnější.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Příkazy Navigace vzad a Vpřed

Pomocí tlačítek **Přejít dozadu** **(Ctrl**+**-**) a **Shift kláves** **(Ctrl**+**Shift)**+**-** na panelu nástrojů můžete přesunout textový kurzor do předchozích umístění nebo se vrátit z předchozího umístění na novější místo. Tato tlačítka zachová posledních 20 umístění kurzoru. Tyto příkazy jsou také k dispozici v nabídce **Zobrazení** v části **Navigace vzad** a **Navigace vpřed**.

![Navigační tlačítka vpřed a vzad](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Navigační panel

**Navigační panel** (rozevírací seznamy v horní části okna kódu) můžete použít k přechodu na kód v základu kódu. Můžete zvolit typ nebo člen, který chcete přejít přímo na něj. Navigační panel se zobrazí při úpravě kódu v jazyce Visual Basic, C# nebo C++. V částečné třídě mohou být členy definované mimo aktuální soubor kódu zakázány (zobrazují se šedě).

![Navigační panel kódu](../ide/media/vside_navigation_bar.png)

V rozevíracích polích můžete procházet následujícím způsobem:

- Chcete-li přejít na jiný projekt, do kterého aktuální soubor patří, zvolte jej v levém rozevíracím souboru.

- Chcete-li přejít na třídu nebo typ, zvolte ji v rozbalovací maješce prostřední.

- Chcete-li přejít přímo na proceduru nebo jiného člena třídy, zvolte ji v pravém rozevíracím souboru.

- Chcete-li přesunout fokus z okna kódu na navigační panel, stiskněte kombinaci **klávesových zkratek Ctrl**+**F2**.

- Chcete-li na navigačním panelu přesunout fokus z pole na pole, stiskněte klávesu **Tab.**

- Chcete-li vybrat položku navigačního panelu, která má fokus, a vrátit se do okna kódu, stiskněte klávesu **Enter.**

- Chcete-li vrátit fokus z navigačního panelu na kód, aniž byste cokoli vybrali, stiskněte klávesu **Esc.**

Chcete-li navigační panel skrýt, změňte možnost Navigační **panel** v nastavení Textový editor **Všechny jazyky** **Options** > **(Textový editor** > **možností** > všechny**jazyky)** nebo můžete změnit nastavení pro jednotlivé jazyky.

## <a name="find-all-references"></a>Najít všechny reference

Vyhledá všechny odkazy na vybraný prvek v řešení. Můžete použít ke kontrole možných vedlejších účinků velké refaktoringu nebo k ověření "mrtvý" kód. Stisknutím **klávesy F8** přejdete mezi výsledky. Další informace naleznete [v tématu Hledání odkazů v kódu](finding-references.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístění textového kurzoru někde uvnitř názvu typu a stisknutí **klávesy Shift**+**F12**
**Myš** | V nabídce po kliknutí pravým tlačítkem myši vyberte **Najít všechny reference.**

## <a name="reference-highlighting"></a>Zvýraznění odkazů

Když klepnete na symbol ve zdrojovém kódu, všechny výskyty tohoto symbolu se v dokumentu zvýrazní. Zvýrazněné symboly mohou obsahovat deklarace a odkazy a mnoho dalších symbolů, které **by se vrátily najít všechny odkazy.** Patří mezi ně názvy tříd, objektů, proměnných, metod a vlastností. V kódu jazyka Visual Basic jsou zvýrazněna také klíčová slova pro mnoho řídicích struktur. Chcete-li přejít na další nebo předchozí zvýrazněný symbol, stiskněte **kombinaci kláves**+**Ctrl Shift**+**Arrow** nebo **Ctrl**+**Shift**+Shift**Arrow**. Barvu zvýraznění můžete změnit v části**Volby** >  **nástrojů** > **Písma** > **a zvýrazněné barvy** > **.**

## <a name="go-to-commands"></a>Příkazy Přejít na

Přejít na má následující příkazy, které jsou k dispozici v nabídce **Úpravy** v části **Přejít na**:

- **Přejít na čáru** **(Ctrl**+**G):** Přechod na zadané číslo řádku v aktivním dokumentu.

- **Přejít na vše** **(Ctrl**+**T** nebo **Ctrl**+**,**): Přechod na zadaný řádek, typ, soubor, člen nebo symbol.

- **Přejít na soubor** **(Ctrl**+**1**, **Ctrl**+**F):** Přechod na zadaný soubor v řešení.

- **Přejít na poslední soubor** (**Ctrl**+**1**, **Ctrl**+**R**): Přechod na zadaný nedávno navštívený soubor v řešení.

- **Přejít na text** **(Ctrl**+**1**, **Ctrl**+**T):** Přechod na zadaný typ v řešení.

- **Přejít na člen** (**Ctrl**+**1**, **Ctrl**+**M**): Přechod na zadaný člen v řešení.

- **Přejít na symbol** **(Ctrl**+**1**, **Ctrl**+**S):** Přechod na zadaný symbol v řešení.

Ve Visual Studiu 2017 verze 15.8 a novější jsou k dispozici také následující příkazy **přejít na** navigaci:

- **Přejít na další problém v souboru** **(Alt**+**PgDn)** a **Přejít na předchozí vydání v souboru** (**Alt**+**PgUp**)

- **Přejít na poslední umístění pro úpravy** **(Ctrl**+**Shift**+**Backspace)**

Další informace o těchto příkazech najdete v tématu Najít kód pomocí příkazů [Přejít](../ide/go-to.md) na.

## <a name="go-to-definition"></a>Přejít na definici

Přejít na definici přejdete k definici vybraného prvku. Další informace naleznete v [tématu Go To Definition and Peek Definition](../ide/go-to-and-peek-definition.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte **klávesu F12**
**Myš** | Klikněte pravým tlačítkem myši na název typu a vyberte **Přejít na definici** nebo stiskněte **klávesu Ctrl** a klikněte na název typu

## <a name="peek-definition"></a>Náhled definice

Definice náhledu zobrazuje definici vybraného prvku v okně, aniž by se v editoru kódu vyhýbala aktuálnímu umístění. Další informace naleznete v [tématu How to: Zobrazení a úpravy kódu pomocí definice náhledu](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) a [Přejít na definici a definici náhledu](../ide/go-to-and-peek-definition.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte **Alt**+**F12**
**Myš** | Klikněte pravým tlačítkem myši na název typu a vyberte **Peek Definition** OR stiskněte **ctrl** a klikněte na název typu (pokud máte zaškrtnutou možnost **Otevřít definici v náhledu)**

## <a name="go-to-implementation"></a>Přejít na implementaci

Pomocí přejít na implementaci, můžete přejít ze základní třídy nebo typu na jeho implementace. Pokud existuje více implementací, uvidíte je uvedené v okně **Najít výsledky symbolu:**

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístění textového kurzoru na místo pod název textu a stisknutí **klávesy Ctrl**+**F12**
**Myš** | Klikněte pravým tlačítkem myši na název typu a vyberte **Přejít na implementaci.**

## <a name="go-to-base"></a>Přejít na základní typ

Pomocí přejít na základnu můžete procházet řetězec dědičnosti vybraného prvku. Pokud existuje více výsledků, zobrazí se v okně **Přejít na základnu:**

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu textu a stiskněte **Alt**+**Home**
**Myš** | Klikněte pravým tlačítkem myši na název typu a vyberte **Přejít na základnu.**

## <a name="call-hierarchy"></a>Hierarchie volání

Volání a z metody můžete zobrazit v [okně Hierarchie volání](../ide/reference/call-hierarchy.md):

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu textu a stiskněte **Ctrl**+**K**, **Ctrl**+**T**
**Myš** | Klikněte pravým tlačítkem myši na jméno člena a vyberte **Zobrazit hierarchii volání.**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Příkazy Další metoda a Předchozí metoda (Visual Basic)

V souborech kódu jazyka Visual Basic použijte tyto příkazy k přesunutí kurzoru na různé metody. Zvolte **Upravit** > **další metodu** nebo **Upravit** > **předchozí metodu**.

## <a name="structure-visualizer"></a>Vizualizér struktury

Funkce Struktura vizualizér v editoru kódu zobrazuje *vodicí čáry struktury* - svislé přerušované čáry, které označují odpovídající složené závorky v základu kódu. Díky tomu je snazší zjistit, kde logické bloky začínají a končí.

![Vizualizér struktury](../ide/media/vside_structure_visualizer.png)

Chcete-li zakázat vodicí čáry struktury, přejděte na**obecné** **editor textových editorů** > **možností** >  **nástrojů** > a zrušte zaškrtnutí políčka **Zobrazit vodítko struktury.**

## <a name="enhanced-scroll-bar"></a>Vylepšený posuvník

Pomocí rozšířeného posuvníku v okně kódu můžete získat pohled z ptačí perspektivy na váš kód. V režimu mapy můžete vidět náhledy kódu, když přesunete kurzor nahoru a dolů posuvníkem. Další informace najdete v [tématu Postup: Sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informace codelens

Můžete najít informace o konkrétní kód, jako jsou změny a kdo tyto změny, odkazy, chyby, pracovní položky, revize kódu a stav testování částí při použití CodeLens v editoru kódu. CodeLens funguje jako heads-up displej při použití Visual Studio Enterprise s Team Foundation Server. Viz [Hledání změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Zobrazit hierarchii volání](../ide/reference/call-hierarchy.md)
