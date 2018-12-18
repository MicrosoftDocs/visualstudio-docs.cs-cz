---
title: Příkazy pro navigaci kódu
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ac6fb3ae1f8c4e7fb48c9cd9a0d2b77cb875094
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894466"
---
# <a name="navigate-code"></a>Vyhledání kódu

Visual Studio poskytuje mnoho způsobů, jak procházet kód v editoru. Toto téma shrnuje různé způsoby, jak se můžete dostat kódu a poskytuje odkazy na témata, které patří do více podrobností.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Přejděte zpět a přejít vpřed příkazy

Můžete použít **přejít zpět** (**Ctrl**+**-**) a **přejít vpřed** ( **CTRL**+**Shift**+**-**) tlačítka na panelu nástrojů, přesuňte kurzor na předchozí umístění, nebo se vraťte do více Poslední umístění z předchozího umístění. Tato tlačítka si ponechávají posledních 20 umístění kurzoru. Tyto příkazy jsou také k dispozici na **zobrazení** nabídky v části **přejít zpět** a **přejít vpřed**.

![Navigační tlačítka vpřed a zpět](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Navigační panel

Můžete použít **navigační panel** (polí rozevíracího seznamu v horní části okna kódu) pro přechod do kódu v základu kódu. Můžete na něj přímo přejít na typ nebo člena. Na navigačním panelu se zobrazí, když upravujete kód v jazyce Visual Basic, C# nebo základ kódu C++. V dílčí třídě mohou být členy definovány mimo aktuální soubor kódu zakázána (zobrazí se šedě).

 ![Kód navigační panel](../ide/media/vside_navigation_bar.png)

Můžete navigaci v rozevíracích seznamech následujícím způsobem:

- Pokud chcete přejít na jiný projekt, který patří aktuálního souboru, vyberte v rozevíracím seznamu vlevo.

- Přejděte do třídy nebo typu, vyberte je uprostřed rozevíracího seznamu.

- Pokud chcete přejít přímo na procedury nebo jiný člen třídy, vyberte jej v pravém rozevíracího seznamu.

- Chcete-li přesunout fokus z okna kódu na navigační panel, stiskněte kombinaci kláves **Ctrl**+**F2**.

- Chcete-li přesunout fokus z pole na pole na navigačním panelu, stiskněte **kartu** klíč.

- Chcete-li vybrat položku navigačního panelu, který má fokus a vraťte se do okna kódu, stiskněte **Enter** klíč.

- Chcete-li vrátit fokus z navigačního panelu kódu bez provedení výběru, stiskněte **Esc** klíč.

Chcete-li skrýt navigační panel, změňte **navigační panel** možnost **všechny jazyky textového editoru** nastavení (**nástroje** > **možnosti**  >  **Textový Editor** > **všechny jazyky**), nebo můžete změnit nastavení pro jednotlivé jazyky.

## <a name="find-all-references"></a>Najít všechny odkazy

Vyhledá všechny odkazy na vybraný prvek v řešení. Můžete to zkontrolovat možné vedlejší účinky z velkých refaktoring, nebo k ověření kódu "neaktivní". Stisknutím klávesy **F8** pro přechod mezi výsledky. Další informace najdete v tématu [najít odkazy ve vašem kódu](finding-references.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístit textový kurzor někam název typu a stiskněte klávesu **Shift**+**F12**
**Myši** | Vyberte **najít všechny odkazy** v místní nabídce

## <a name="reference-highlighting"></a>Zvýraznění odkazů

Po kliknutí na symbol ve zdrojovém kódu se zvýrazní všechny výskyty symbolu v dokumentu. Zvýrazněné symboly mohou obsahovat prohlášení a odkazy a mnoho dalších symbolů, které **najít všechny odkazy** vrátí. Patří sem názvy tříd, objektů, proměnných, metod a vlastností. V kódu jazyka Visual Basic jsou také zvýrazněna klíčová slova pro mnoho řídících struktur. Chcete-li přesunout na další nebo předchozí zvýrazněný symbol, stiskněte **Ctrl**+**Shift**+**šipka dolů** nebo **Ctrl** + **Shift**+**šipka nahoru**. Můžete změnit barvu zvýraznění v **nástroje** > **možnosti** > **prostředí** > **písma a Barvy** > **zvýrazněný odkaz**.

## <a name="go-to-commands"></a>Přejít na příkazy

Přejít na má následující příkazy, které jsou k dispozici v **upravit** nabídky v části **přejít na**:

- **Přejít na řádek** (**Ctrl**+**G**): přesunout na zadaný počet řádků v aktivním dokumentu.

- **Přejít na vše** (**Ctrl**+**T** nebo **Ctrl**+**,**): Přesune zadaný řádek, typ, soubor, člen nebo symbol.

- **Přejděte do souboru** (**Ctrl**+**1**, **Ctrl**+**F**): přesunout do zadaného souboru řešení.

- **Přejít na poslední soubor** (**Ctrl**+**1**, **Ctrl**+**R**): přesunout na zadaný, naposledy navštívené soubor řešení (nové v sadě Visual Studio 2017 verze 15.8).

- **Přejít na typ** (**Ctrl**+**1**, **Ctrl**+**T**): přesunout do zadaného typu řešení.

- **Přejít na člen** (**Ctrl**+**1**, **Ctrl**+**M**): přesunout do zadaného člena v řešení.

- **Přejít na Symbol** (**Ctrl**+**1**, **Ctrl**+**S**): přesunout na zadaný symbol v řešení.

V sadě Visual Studio 2017 verze 15,8 a novější, následující **přejít na** navigačními příkazy jsou také k dispozici:

- **Přejděte na další problém v souboru** (**Alt**+**Page Down**) a **přejít na předchozí problém v souboru** (**Alt** + **PgUp**)

- **Přejít na poslední úpravy umístění** (**Ctrl**+**Shift**+**Backspace**)

Další informace o těchto příkazech v [vyhledávání kódu pomocí příkazu Přejít](../ide/go-to.md) tématu.

## <a name="go-to-definition"></a>Přejít k definici

Přejít k definici přejdete na definici vybraného prvku. Další informace najdete v tématu [přejít k definici a náhled definice](../ide/go-to-and-peek-definition.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístit textový kurzor někam název typu a stiskněte klávesu **F12**
**Myši** | Klikněte pravým tlačítkem na název typu a vyberte **přejít k definici** nebo stiskněte klávesu **Ctrl** a klikněte na název typu (nové sady Visual Studio 2017 verze 15.4)

## <a name="peek-definition"></a>Náhled definice

Náhled definice zobrazí definici vybraného prvku v okně bez navigaci pryč z aktuální umístění v editoru kódu. Další informace najdete v tématu [postupy: zobrazení a úpravy kódu s použitím definice operace Peek](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) a [přejít k definici a náhled definice](../ide/go-to-and-peek-definition.md).

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístit textový kurzor někam název typu a stiskněte klávesu **Alt**+**F12**
**Myši** | Klikněte pravým tlačítkem na název typu a vyberte **funkce Náhled definice** nebo stiskněte klávesu **Ctrl** a klikněte na název typu (Pokud máte **Otevřít definici v zobrazení náhledu** zaškrtnutým políčkem)

## <a name="go-to-implementation"></a>Přejít k implementaci

Přejít k implementaci můžete přejít ze základní třídy nebo typ, který jeho implementace. Pokud existuje víc implementací, uvidíte je uvedené v **výsledky hledáni symbolu** okno:

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístit textový kurzor někam název typu a stiskněte klávesu **Ctrl**+**F12**
**Myši** | Klikněte pravým tlačítkem na název typu a vyberte **přejít k implementaci**

## <a name="call-hierarchy"></a>Hierarchie volání

Můžete zobrazit volání do a z metody v [hierarchie volání okno](../ide/reference/call-hierarchy.md):

Vstup | Funkce
------------ | ---
**Klávesnice** | Umístit textový kurzor někam název typu a stiskněte klávesu **Ctrl**+**K**, **Ctrl**+**T**
**Myši** | Klikněte pravým tlačítkem na název člena a vyberte **zobrazit hierarchii volání**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Další metodou a metodou předchozí příkazy (Visual Basic)

V souborech kódu jazyka Visual Basic pomocí následujících příkazů můžete přesunout kurzor do různých metod. Zvolte **upravit** > **další metoda** nebo **upravit** > **předchozí metoda**.

## <a name="structure-visualizer"></a>Vizualizér struktur

Vizualizér struktur funkce v editoru ukazuje kód *vodicí čáry struktury* -Čárkovaná svislá řádky, které označují odpovídající složené závorky ve vašem základu kódu. Díky tomu je snazší zjistit, kde logické bloky begin a end.

![Vizualizér struktur](../ide/media/vside_structure_visualizer.png)

Chcete-li vypnout vodicí čáry struktury, přejděte na **nástroje** > **možnosti** > **textový Editor** > **Obecné** a zrušte **Zobrazit vodicí čáry struktury** pole.

## <a name="enhanced-scroll-bar"></a>Rozšířený posuvník

Rozšířený posuvník v okně kódu můžete získat reálné zobrazení kódu. V režimu mapu uvidíte náhledy kódu při přesunutí kurzoru nahoru a dolů posuvníku. Další informace najdete v tématu [postupy: sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informace funkce CodeLens

Můžete najít informace o konkrétním kódu, jako jsou změny a kdo provedl tyto změny, odkazy, chyby, pracovní položky, revize kódu a stav jednotky testování, při použití CodeLens v editoru kódu. CodeLens funguje jako pohotové zobrazení při použití sady Visual Studio Enterprise s Team Foundation Server. Zobrazit [nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Zobrazit hierarchii volání](../ide/reference/call-hierarchy.md)
