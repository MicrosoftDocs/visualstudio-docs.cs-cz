---
title: Přejít na soubor, přejít na symbol, přejít na řádek
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb39f1d395e48351aeacb587556224b0f86aac3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593782"
---
# <a name="find-code-using-go-to-commands"></a>Vyhledání kódu pomocí příkazu Přejít

Příkazy **go** to aplikace Visual Studio provádějí cílené hledání kódu, které vám pomůže rychle najít zadané položky. Na určitý řádek, typ, symbol, soubor a člen můžete přejít z jednoduchého, jednotného rozhraní.

## <a name="how-to-use-it"></a>Jak ji použít

Vstup | Funkce
------------ | ---
**Klávesnice** | Stiskněte **kombinaci kláves Ctrl**+**T** nebo **Ctrl**+**,**
**Myš** | Vyberte **Možnost Upravit** > **přejít na** > **vše**

Malé okno se zobrazí v pravém horním rohu editoru kódu.

![Okno Přejít na vše](media/go-to-all.png)

Při psaní do textového pole se výsledky zobrazí v rozevíracím seznamu pod textovým polem. Chcete-li přejít na prvek, zvolte jej v seznamu.

![Přejít na okno](../ide/media/vside_navigatetowindow.png)

Můžete také zadat otazník (**?**) a získat další nápovědu.

![Přejít na nápovědu](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrovaná hledání

Ve výchozím nastavení je zadaná položka vyhledána ve všech položkách řešení. Hledání kódu však můžete omezit na určité typy prvků přednastavením hledaných výrazů určitými znaky. Filtr hledání můžete také rychle změnit výběrem tlačítek na panelu nástrojů dialogového okna **Přejít na.** Tlačítka, která mění typové filtry, jsou na levé straně a tlačítka, která mění rozsah hledání, jsou na pravé straně.

![Přejít na členy](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrování na určitý typ prvku kódu

Chcete-li hledání zúžit na určitý typ prvku kódu, můžete do vyhledávacího pole zadat předponu nebo vybrat jednu z pěti ikon filtru:

Předpona | Ikona | Zástupce | Popis
:-: | - | - | -
:| ![Ikona čáry](media/gotoall-line-icon.png) | **Ctrl**+**G** | Přejít na zadané číslo řádku
f| ![Ikona Soubory](media/gotoall-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**F** | Přejít na zadaný soubor
r| ![Ikona Posledních souborů](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**R** | Přejít na zadaný nedávno navštívený soubor
t| ![Ikona Typy](media/gotoall-types-icon.png) | **Ctrl**+**1**, **Ctrl**+**T** | Přejít na zadaný typ
m| ![Ikona Členové](media/gotoall-members-icon.png) | **Ctrl**+**1**, **Ctrl**+**M** | Přejít na zadaný člen
\#| ![Ikona symbolů](media/gotoall-symbols-icon.png) | **Ctrl**+**1**, **Ctrl**+**S** | Přejít na zadaný symbol

### <a name="filter-to-a-specific-location"></a>Filtrování do určitého umístění

Chcete-li hledání zúžit na určité místo, vyberte jednu ze dvou ikon dokumentu:

Ikona | Popis
---- | ---
![Aktuální dokument](media/gotoall_currentdocument.png) | Hledat pouze aktuální dokument
![Externí dokumenty](media/gotoall_external.png) | Vyhledávání externích dokumentů kromě dokumentů umístěných v projektu/řešení

## <a name="camel-casing"></a>Kryt velblouda

Pokud v kódu používáte [camel case,](https://en.wikipedia.org/wiki/Camel_case) můžete rychleji najít prvky kódu zadáním pouze velkých písmen názvu znakového prvku. Pokud má například váš kód `CredentialViewModel`typ s názvem , můžete hledání zúžit výběrem filtru **Typ** (**t**) a zadáním pouze velkých písmen názvu (`CVM`) do dialogového okna Přejít na. Tato funkce může být užitečná, pokud má váš kód dlouhé názvy.

![Přejít na okno - vyhledávání s velkými písmeny](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Nastavení

Výběr ikony ozubeného kola ![Ikona ozubeného kolečka](media/gotoall_gear.png) umožňuje změnit způsob fungování této funkce:

Nastavení | Popis
------- | ---
Použít kartu Náhled | Okamžité zobrazení vybrané položky na kartě náhledu ide
Zobrazit podrobnosti | Zobrazení informací o projektu, souboru, řádku a souhrnu z komentářů dokumentace v okně
Středové okno | Přesunutí tohoto okna do horního středu editoru kódu namísto vpravo nahoře

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)
- [Přejít na řádek – dialogové okno](../ide/reference/go-to-line.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)
