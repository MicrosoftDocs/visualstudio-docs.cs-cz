---
title: Příkazy navigace v kódu
description: Seznamte se s různými možnostmi, kterými se můžete pohybovat v kódu v editoru.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 77b0f8782f9ffaf37701f13b30be6e068ce05f8d
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871519"
---
# <a name="navigate-code"></a>Navigace v kódu

Visual Studio poskytuje mnoho způsobů navigace v editoru kódu. Toto téma shrnuje různé způsoby navigace v kódu a poskytuje odkazy na témata, která odkazují na další podrobnosti.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Navigace zpět a procházení příkazů vpřed

Pomocí tlačítek **Navigovat zpět** (**CTRL** + **-** ) a **Procházet vpřed** (**CTRL** + **+ +** + **-** ) na panelu nástrojů můžete přesunout kurzor na předchozí místa nebo se vrátit do novějšího umístění z předchozího umístění. Tato tlačítka si zachovávají posledních 20 umístění místa vložení. Tyto příkazy jsou k dispozici také v nabídce **Zobrazit** v části **Navigovat zpět** a **Přejít vpřed**.

![Navigační tlačítka pro navigaci a zpět](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Navigační panel

K přechodu na kód v základu kódu můžete použít **navigační panel** (rozevírací seznamy v horní části okna Code). Můžete zvolit typ nebo člena, který chcete přejít přímo na něj. Navigační panel se zobrazí při úpravách kódu v Visual Basic, C# nebo základu kódu jazyka C++. V částečné třídě mohou být členy, kteří jsou definováni mimo aktuální soubor kódu, zakázány (zobrazují se šedě).

![Navigační panel kódu](../ide/media/vside_navigation_bar.png)

Můžete se pohybovat v rozevíracích seznamech následujícím způsobem:

- Chcete-li přejít na jiný projekt, do kterého aktuální soubor patří, vyberte ho v rozevíracím seznamu vlevo.

- Chcete-li přejít na třídu nebo typ, vyberte ji v rozevíracím seznamu uprostřed.

- Chcete-li přejít přímo k proceduře nebo jinému členu třídy, vyberte ji v rozevíracím seznamu vpravo.

- Chcete-li posunout fokus z okna Code na navigační panel, stiskněte kombinaci kláves **CTRL** + **F2**.

- Chcete-li přesunout fokus z pole do pole na navigačním panelu, stiskněte klávesu **TAB** .

- Pokud chcete vybrat položku navigačního panelu, která má fokus, a vrátit se do okna Code (kód), stiskněte klávesu **ENTER** .

- Chcete-li vrátit fokus z navigačního panelu na kód bez výběru všeho, stiskněte klávesu **ESC** .

Chcete-li skrýt navigační panel, změňte možnost **navigační panel** v nastavení **textový editor všechny jazyky** (možnosti **nástrojů**  >  **Options**  >  **textový editor**  >  **všechny jazyky**), nebo můžete změnit nastavení pro jednotlivé jazyky.

## <a name="find-all-references"></a>Najít všechny odkazy

Vyhledá všechny odkazy na vybraný prvek v řešení. Tuto možnost můžete použít ke kontrole možných vedlejších účinků velkého refaktoringu nebo k ověření "mrtvého" kódu. Pro přechod mezi výsledky stiskněte klávesu **F8** . Další informace najdete v tématu [Hledání odkazů v kódu](finding-references.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte **SHIFT** + **F12** .
**Myš** | Vyberte **Najít všechny odkazy** z nabídky kliknutím pravým tlačítkem myši.

## <a name="reference-highlighting"></a>Zvýrazňování odkazů

Po kliknutí na symbol ve zdrojovém kódu se v dokumentu zvýrazní všechny výskyty tohoto symbolu. Zvýrazněné symboly mohou obsahovat deklarace a odkazy a mnoho dalších symbolů, které **naleznou všechny odkazy** , vrátí. Mezi ně patří názvy tříd, objektů, proměnných, metod a vlastností. V kódu Visual Basic jsou také zvýrazněna klíčová slova pro mnoho řídicích struktur. Chcete-li přejít na další nebo předchozí zvýrazněný symbol, stiskněte klávesovou **zkratku** + **SHIFT +** + **šipka dolů** nebo **CTRL** + **+** + **šipka nahoru**. Můžete změnit barvu zvýraznění v **nabídce nástroje**  >  **Možnosti**  >  **prostředí**  >  **písma a barvy**  >  **zvýrazněné odkazy**.

## <a name="go-to-commands"></a>Přejít na příkazy

Přejděte na následující příkazy, které jsou k dispozici v nabídce **Upravit** v části **Přejít na**:

- **Přejít na řádek** (**CTRL** + **G**): přesunout na zadané číslo řádku v aktivním dokumentu.

- **Přejít na vše** (**CTRL** + **T** nebo **CTRL** + **,**): přesunout na zadaný řádek, typ, soubor, člen nebo symbol.

- **Přejít k souboru** (**CTRL** + **1**, **CTRL** + **F**): přesunout do zadaného souboru v řešení.

- **Přejít na poslední soubor** (**CTRL** + **1**, **CTRL** + **R**): přesunout do zadaného souboru nedávno navštíveného v řešení.

- **Přejít na typ** (**CTRL** + **1**, **CTRL** + **T**): přesunout do zadaného typu v řešení.

- **Přejít na člena** (**CTRL** + **1**, **CTRL** + **M**): přesunout na zadaného člena v řešení.

- **Přejít na symbol** (**CTRL** + **1**, **CTRL** + **S**): přesune se k zadanému symbolu v řešení.

V aplikaci Visual Studio 2017 verze 15,8 a novější jsou k dispozici také následující příkazy **Přejít k** navigačním příkazům:

- **Přejít na další problém v souboru** (**ALT** + **Page Down**) a **Přejít na předchozí problém v souboru** (**ALT** + **Page Up**)

- **Přejít na poslední umístění pro úpravy** (**CTRL** + **+ SHIFT** + **BACKSPACE**)

Přečtěte si další informace o těchto příkazech v tématu [Hledání kódu pomocí příkazu Přejít na příkazy](../ide/go-to.md) .

## <a name="go-to-definition"></a>Přejít k definici

Přejít k definici přejde do definice vybraného elementu. Další informace najdete v tématu [Přejít k definici a náhled definice](../ide/go-to-and-peek-definition.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte klávesu **F12** .
**Myš** | Klikněte pravým tlačítkem myši na název typu a vyberte **Přejít k definici**  nebo stiskněte klávesu **CTRL** a klikněte na název typu.

## <a name="peek-definition"></a>Náhled definice

Náhled definice zobrazí definici vybraného prvku v okně bez přechodu z aktuálního umístění v editoru kódu. Další informace najdete v tématu [Postup: zobrazení a úpravy kódu pomocí náhledu definice](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) a [Přechod na definici a náhled definice](../ide/go-to-and-peek-definition.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte **ALT** + **F12** .
**Myš** | Klikněte pravým tlačítkem myši na název typu a vyberte možnost **Náhled definice** nebo stiskněte klávesu **CTRL** a klikněte na název typu (Pokud máte zaškrtnuté políčko **Otevřít definici v náhledu).**

## <a name="go-to-implementation"></a>Přejít k implementaci

Pomocí možnosti přejít k implementaci můžete přejít ze základní třídy nebo typu na jeho implementace. Pokud je k dispozici více implementací, zobrazí se v okně **výsledky hledání symbolu** v seznamu:

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte **kombinaci kláves CTRL +** + **F12** .
**Myš** | Klikněte pravým tlačítkem na název typu a vyberte **Přejít k implementaci** .

## <a name="go-to-base"></a>Přejít na základní typ

Pomocí možnosti přejít na základ můžete přejít k řetězci dědičnosti vybraného prvku. Pokud je k dispozici více výsledků, zobrazí se v okně **Přejít na základní** :

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte klávesu **ALT** + **Home**
**Myš** | Klikněte pravým tlačítkem na název typu a vyberte **Přejít na základní** .

## <a name="call-hierarchy"></a>Hierarchie volání

Můžete zobrazit volání a z metody v [okně hierarchie volání](../ide/reference/call-hierarchy.md):

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístěte textový kurzor někam do názvu typu a stiskněte klávesy **CTRL** + **K**, **CTRL** + **T**
**Myš** | Klikněte pravým tlačítkem myši na název členu a vyberte **Zobrazit hierarchii volání.**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Next – metoda a příkazy předchozí metody (Visual Basic)

V Visual Basic soubory kódu, použijte tyto příkazy pro přesun kurzoru do různých metod. Vyberte **Upravit**  >  **Další metodu** nebo **Upravit**  >  **předchozí metodu**.

## <a name="structure-visualizer"></a>Vizualizér struktury

Funkce Vizualizér struktury v editoru kódu zobrazuje *čáry vodítka struktury* – svislé přerušované čáry, které označují odpovídající složené závorky ve vašem základu kódu. To usnadňuje zjištění, kde začínají a končí logické bloky.

![Vizualizér struktury](../ide/media/vside_structure_visualizer.png)

Chcete-li zakázat čáry vodítka struktury **Tools**, otevřete  >  okno **Možnosti** nástroje  >  **textový editor**  >  **Obecné** a zrušte zaškrtnutí políčka **Zobrazit čáry Průvodce strukturou** .

## <a name="enhanced-scroll-bar"></a>Vylepšený posuvník

Můžete použít rozšířený posuvník v okně kódu a získat tak pohled na svůj kód v pohledech na oči. V režimu mapy můžete zobrazit náhledy kódu při přesunutí kurzoru nahoru a dolů posuvníku. Další informace najdete v tématu [Postupy: sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informace o CodeLens

Můžete najít informace o konkrétním kódu, například změny a o tom, kdo provedl tyto změny, odkazy, chyby, pracovní položky, revize kódu a stav testu jednotek při použití CodeLens v editoru kódu. CodeLens funguje jako při použití Visual Studio Enterprise s Team Foundation Server, jako je například zobrazení hlav. Viz téma [Vyhledání změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Zobrazit hierarchii volání](../ide/reference/call-hierarchy.md)
