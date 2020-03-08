---
title: Správa balíčků npm
description: Visual Studio vám pomůže při správě balíčků s využitím Node.js package Manageru (npm)
ms.custom: seodec18
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: de92c3f1f0d0e29d1ba2dfaf5d536a42e636be2c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409454"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Správa balíčků npm v sadě Visual Studio

npm umožňuje instalovat a spravovat balíčky pro použití v aplikacích Node.js. Pokud neznáte npm a chcete získat další informace, podívejte se do [dokumentace npm](https://docs.npmjs.com/).

Visual Studio umožňuje snadno pracovat s npm a vydávání příkazů npm přes uživatelské rozhraní nebo přímo. Můžete použít následující metody:
* [Instalovat balíčky z Průzkumník řešení](#npmInstallWindow)
* [Spravovat nainstalované balíčky z Průzkumník řešení](#solutionExplorer)
* [Použití příkazu `.npm` v interaktivním okně Node. js](#interactive)

Tyto funkce společně spolupracují a synchronizují se systémem projektu a souborem *Package. JSON* v projektu.

> [!Important]
> NPM očekává, že se složka *node_modules* a *Package. JSON* v kořenu projektu. Pokud je struktura složky vaší aplikace odlišná, měli byste aktualizovat strukturu složek, pokud chcete spravovat balíčky npm pomocí sady Visual Studio.

> [!NOTE]
> Pro existující projekty NPM použijte šablonu řešení **Code ze stávající Node. js** .

## <a name="npmInstallWindow"></a>Instalovat balíčky z Průzkumník řešení

Nejjednodušší způsob, jak nainstalovat balíčky npm se prostřednictvím okno instalace balíčku npm. Chcete-li získat přístup k tomuto oknu, klikněte pravým tlačítkem myši na uzel **npm** v projektu a vyberte možnost **instalovat nové balíčky npm**.

![Nainstalujte nový balíček npm z Průzkumníka řešení](../javascript/media/solution-explorer-install-package.png)

V tomto okně můžete vyhledat balíček, zadejte možnosti a nainstalovat.

![Hledání balíčku npm](../javascript/media/search-package.png)

* **Typ závislosti** – volba mezi **standardním**, **vývojem**a **volitelnými** balíčky. Standardní Určuje, že balíček je závislosti modulu runtime, že vývoj Určuje, že balíček je jenom nutné během vývoje.
* **Přidat do Package. JSON** – Tato možnost je zastaralá.
* **Vybraná verze** – vyberte verzi balíčku, který chcete nainstalovat.
* **Jiné argumenty npm** – zadejte jiné standardní argumenty npm. Například můžete zadat hodnotu verze, například `@~0.8` pro instalaci konkrétní verze, která není v seznamu verzí k dispozici.

Zobrazí se průběh instalace na kartě npm v okně výstup. To může nějakou dobu trvat.

> [!TIP]
> Můžete vyhledat balíčky s vymezeným oborem, které předčekají na vyhledávací dotaz s rozsahem, který vás zajímá, například zadejte `@types/mocha` pro hledání souborů definice TypeScript pro Mocha. Při instalaci definic typů pro TypeScript můžete také určit verzi TypeScriptu, kterou jste určený, přidáním `@ts2.6` do pole argument npm.

## <a name="solutionExplorer"></a>Spravovat nainstalované balíčky v Průzkumník řešení

balíčky npm se zobrazí v Průzkumníku řešení. Položky v uzlu **npm** napodobují závislosti v souboru *Package. JSON* .

![Hledání balíčku npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stav balíčku
* ![Nainstalovaný balíček](../javascript/media/installed-npm.png) -Nainstalované a jsou uvedeny v souboru package.json
* ![nadbytečného balíčku](../javascript/media/extraneous-npm.png) nainstalován, ale není výslovně uveden v balíčku Package. JSON
* ![Chybí balíček](../javascript/media/missing-npm.png) – Není nainstalována, ale uvedené v souboru package.json

Klikněte pravým tlačítkem myši na uzel balíčku nebo na uzel **npm** a proveďte jednu z následujících akcí:
* **Instalace chybějících balíčků** , které jsou uvedené v *balíčku Package. JSON*
* **Aktualizovat balíčky** na nejnovější verzi
* **Odinstalujte balíček** a odeberte ho z *Package. JSON.*

## <a name="interactive"></a>Použití příkazu. npm v interaktivním okně Node. js

K provádění příkazů npm můžete použít také příkaz `.npm` v interaktivním okně Node. js. Chcete-li otevřít okno, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a vyberte možnost **otevřít interaktivní okno Node. js**.

V okně slouží k instalaci balíčku příkazech, jako je následující:

`.npm install azure@4.2.3`

 > [!Tip]
 > Ve výchozím nastavení spustí npm v domovském adresáři vašeho projektu. Pokud máte více projektů v řešení zadejte název nebo cestu k projektu v závorkách.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Pokud projekt neobsahuje soubor Package. JSON, pomocí `.npm init -y` vytvořte nový soubor Package. JSON s výchozími položkami.
