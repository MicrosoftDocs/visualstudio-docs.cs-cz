---
title: Přejít na soubor, přejít na symbol, přejít na řádek
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3a810e96b410c0f1f6f5d6ffdaa07b1e007abd6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654644"
---
# <a name="find-code-using-go-to-commands"></a>Vyhledání kódu pomocí příkazu Přejít

Příkaz **Přejít na** příkazy sady Visual Studio provede cílené hledání kódu, které vám pomůže rychle najít zadané položky. Můžete přejít na konkrétní řádek, typ, symbol, soubor a člen z jednoduchého a sjednoceného rozhraní.

## <a name="how-to-use-it"></a>Jak ji použít

Vstup | Funkce
------------ | ---
**Kombinace** | Stiskněte **ctrl** +**t** nebo **CTRL** + **,**
**Stisknut** | Vyberte **upravit**  > **Přejít na**  > **Přejít na vše** .

V pravém horním rohu editoru kódu se zobrazí malé okno.

![Přejít do celého okna](media/go-to-all.png)

Při psaní do textového pole se výsledky zobrazí v rozevíracím seznamu pod textovým polem. Chcete-li přejít na prvek, vyberte ho v seznamu.

![Přejít na okno](../ide/media/vside_navigatetowindow.png)

Můžete také zadat otazník ( **?** ) a získat tak další nápovědu.

![Přejít na všechny informace](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrovaná hledání

Ve výchozím nastavení je zadaná položka prohledána ve všech položkách řešení. Hledání kódu však můžete omezit na konkrétní typy prvků, protože hledané výrazy mají určité znaky. Vyhledávací filtr můžete také rychle změnit výběrem tlačítek na panelu nástrojů **Přejít na** dialogové okno. Tlačítka, která mění filtry typů, jsou na levé straně a tlačítka, která mění rozsah hledání, jsou na pravé straně.

![Přejít na členy](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrovat na konkrétní typ elementu kódu

Chcete-li zúžit hledání na konkrétní typ prvku kódu, můžete buď zadat předponu do vyhledávacího pole, nebo vybrat jednu z pěti ikon filtru:

směr | Ikona | Zástupce | Popis
:-: | - | - | -
:| ![Ikona čáry](media/gotoall-line-icon.png) | **Ctrl**+**G** | Přejít na zadané číslo řádku
FJ| ![Ikona souborů](media/gotoall-files-icon.png) | **Ctrl** +**1**, **CTRL** +**F** | Přejít na zadaný soubor
Í| ![Ikona posledních souborů](media/gotoall-recent-files-icon.png) | **Ctrl** +**1**, **CTRL** +**R** | Přejít na zadaný, nedávno navštívený soubor
t| ![Ikona typů](media/gotoall-types-icon.png) | **Ctrl** +**1**, **CTRL** +**t** | Přejít na zadaný typ
m| ![Ikona členů](media/gotoall-members-icon.png) | **Ctrl** +**1**, **CTRL** +**M** | Přejít na zadaného člena
\#| ![Ikona symbolů](media/gotoall-symbols-icon.png) | **Ctrl** +**1**, **CTRL** +**S** | Přejít na zadaný symbol

### <a name="filter-to-a-specific-location"></a>Filtrovat do konkrétního umístění

Chcete-li zúžit hledání na konkrétní umístění, vyberte jednu ze dvou ikon dokumentu:

Ikona | Popis
---- | ---
![Aktuální dokument](media/gotoall_currentdocument.png) | Hledat pouze aktuální dokument
![Externí dokumenty](media/gotoall_external.png) | Hledání externích dokumentů kromě těch, které se nacházejí v projektu nebo řešení

## <a name="camel-casing"></a>Ve stylu CamelCase velká a malá písmena

Pokud používáte [ve stylu CamelCase velká a malá](https://en.wikipedia.org/wiki/Camel_case) písmena v kódu, můžete najít prvky kódu rychleji zadáním pouze velkých písmen názvu elementu kódu. Například pokud má váš kód typ s názvem `CredentialViewModel`, můžete zúžit hledání tak, že vyberete filtr **typu** (**t**) a pak v dialogovém okně Přejít na zadáte jenom velká písmena názvu (`CVM`). Tato funkce může být užitečná v případě, že váš kód má dlouhé názvy.

![Přejít na okno – vyhledávání pomocí velkých písmen](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Nastavení

Výběr ikony ozubeného kolečka ![Ikona ozubeného kolečka](media/gotoall_gear.png) umožňuje změnit, jak tato funkce funguje:

Nastavením | Popis
------- | ---
Použít kartu náhledu | Zobrazit vybranou položku hned na kartě náhled v integrovaném vývojovém prostředí
Zobrazit podrobnosti | Zobrazení projektu, souboru, řádku a souhrnu informací z dokumentačních komentářů v okně
Okno na střed | Přesune toto okno do horního středu editoru kódu místo pravého horního rohu.

## <a name="see-also"></a>Viz také:

- [Navigace v kódu](../ide/navigating-code.md)
- [Přejít na řádek – dialogové okno](../ide/reference/go-to-line.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)