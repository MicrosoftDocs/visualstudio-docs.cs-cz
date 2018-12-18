---
title: Přejděte na soubor, přejděte na symbol, přejít na řádek
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d9ceeb7c4d24871bc0f2ddfc743c2c65e087205
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907050"
---
# <a name="find-code-using-go-to-commands"></a>Vyhledání kódu pomocí příkazu Přejít

Visual Studio **přejít na** příkazy provádějí cílené hledání kódu vám pomůžou rychle najít zadané položky. Můžete přejít na konkrétní řádek, typ, symbolů, souboru a člen od jednoduché jednotné rozhraní. Tato funkce je v sadě Visual Studio 2017 nebo novější.

## <a name="how-to-use-it"></a>Jak jej používat

Vstup | Funkce
------------ | ---
**Klávesnice** | Stisknutím klávesy **Ctrl**+**T** nebo **Ctrl**+**,**
**Myši** | Vyberte **upravit** > **přejít na** > **ejít na vše**

Malé okno se zobrazí v horní části přímo z editoru kódu.

![Okno Přejít na vše](media/go-to-all.png)

Při psaní do textového pole, výsledky se zobrazí v rozevíracím seznamu pod textovým polem. Přejít na element, vyberte v seznamu.

![Navigovat na okno](../ide/media/vside_navigatetowindow.png)

Můžete také zadat otazník (**?**) Chcete-li získat další pomoc.

![Přejít na všechny nápovědy](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrované hledání

Ve výchozím nastavení se zadanou položku hledá ve všech položkách řešení. Hledání kódu na konkrétní elementu typů lze však omezit zahájením literálu hledané výrazy pomocí určitých znaků. Vyhledávací filtr můžete také rychle změnit výběrem tlačítka na **přejít na** panel nástrojů dialogu pole. Tlačítka, které se mění filtrů typu jsou na levé straně a tlačítka, které se mění obor hledání na pravé straně.

![Přejít na členy](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrovat na konkrétní typ prvku kódu

Chcete-li zúžit hledání tak, aby konkrétní typ prvku kódu, můžete do vyhledávacího pole zadejte předponu nebo vyberte jeden z pěti ikony filtru:

Předpona | Ikona | Zástupce | Popis
:-: | - | - | -
:| ![Ikona řádku](media/gotoall-line-icon.png) | **CTRL**+**G** | Přejít na zadaný počet řádků
f| ![Soubory ikony](media/gotoall-files-icon.png) | **CTRL**+**1**, **Ctrl**+**F** | Přejděte do zadaného souboru
r| ![Ikona poslední soubory](media/gotoall-recent-files-icon.png) | **CTRL**+**1**, **Ctrl**+**R** | Přejděte k souboru zadané, naposledy navštívené
t| ![Ikona typy](media/gotoall-types-icon.png) | **CTRL**+**1**, **Ctrl**+**T** | Přejděte na zadaný typ.
m| ![Ikona členy](media/gotoall-members-icon.png) | **CTRL**+**1**, **Ctrl**+**M** | Přejděte k zadanému členu
\#| ![Ikony symbolů](media/gotoall-symbols-icon.png) | **CTRL**+**1**, **Ctrl**+**S** | Přejít na zadaný symbol

### <a name="filter-to-a-specific-location"></a>Filtrovat na konkrétní umístění

Chcete-li zúžit hledání tak, aby konkrétní umístění, vyberte jednu z ikon dvou dokumentu:

Ikona | Popis
---- | ---
![Aktuální dokument](media/gotoall_currentdocument.png) | Prohledat pouze aktuální dokument
![Externí dokumenty](media/gotoall_external.png) | Hledat externí dokumenty kromě ti se sídlem na projekt nebo řešení

## <a name="camel-casing"></a>CamelCase

Pokud používáte [camelCase](https://en.wikipedia.org/wiki/Camel_case) ve vašem kódu, můžete najít rychlejší prvky kódu tak, že zadáte pouze písmeny název prvku kódu. Například, pokud váš kód obsahuje typ s názvem `CredentialViewModel`, můžete zúžit hledání výběrem **typ** filtru (**t**) a následně zadají stejně velká písmena názvu (`CVM`) v Přejděte do dialogových oken. Tato funkce může být užitečné, pokud váš kód obsahuje dlouhé názvy.

![Navigovat na okno - hledání s písmeny](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Nastavení

Vyberte ikonu ozubeného kolečka ![Ikona ozubeného kolečka](media/gotoall_gear.png) Umožňuje změnit, jak tato funkce funguje:

Nastavení | Popis
------- | ---
Použít kartu náhledu | Okamžitě zobrazit na vybranou položku na kartě preview rozhraní IDE
Zobrazit podrobnosti | V okně zobrazovat project, soubor, řádek a souhrnné informace z komentářů k dokumentaci
Zarovnat okno na střed | Přesuňte toto okno do středu horní části editoru kódu místo pravé horní části

## <a name="see-also"></a>Viz také:

- [Vyhledání kódu](../ide/navigating-code.md)
- [Dialogové okno Přejít na řádek](../ide/reference/go-to-line.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)