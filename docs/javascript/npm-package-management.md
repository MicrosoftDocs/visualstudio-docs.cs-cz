---
title: Správa balíčků npm
description: Visual Studio vám pomůže při správě balíčků s využitím Node.js package Manageru (npm)
ms.custom: seodec18
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 297bad186c7f3412e56a5a59f65b82ab9cd35a03
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049649"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Správa balíčků npm v sadě Visual Studio

npm umožňuje instalovat a spravovat balíčky pro použití v aplikacích Node.js. Pokud nejste obeznámeni s npm a chcete dozvědět více, pokračujte [npm dokumentaci](https://docs.npmjs.com/).

Visual Studio umožňuje snadno pracovat s npm a vydávání příkazů npm přes uživatelské rozhraní nebo přímo. Můžete použít následující metody:
* [Instalace balíčků z Průzkumníka řešení](#npmInstallWindow)
* [Spravovat nainstalované balíčky z Průzkumníka řešení](#solutionExplorer)
* [Použití `.npm` v interaktivním okně Node.js](#interactive)

Tyto funkce fungují společně a synchronizovat systém projektu a *package.json* soubor v projektu.

## <a name="npmInstallWindow"></a> Instalace balíčků z Průzkumníka řešení

Nejjednodušší způsob, jak nainstalovat balíčky npm se prostřednictvím okno instalace balíčku npm. Pro přístup k toto okno, klikněte pravým tlačítkem myši **npm** uzel projektu a vyberte **nainstalovat nové balíčky npm**.

![Nainstalujte nový balíček npm z Průzkumníka řešení](../javascript/media/solution-explorer-install-package.png)

V tomto okně můžete vyhledat balíček, zadejte možnosti a nainstalovat. 

![Hledání balíčku npm](../javascript/media/search-package.png)

* **Typ závislosti** -zvolili mezi **standardní**, **vývoj**, a **volitelné** balíčky. Standardní Určuje, že balíček je závislosti modulu runtime, že vývoj Určuje, že balíček je jenom nutné během vývoje.
* **Přidat do package.json** – tato možnost je zastaralý.
* **Vybraná verze** – vyberte verzi balíčku, kterou chcete nainstalovat.
* **Jiné argumenty npm** -zadat další argumenty pro standard npm. Například můžete zadat hodnotu verze, jako `@~0.8` instalace konkrétní verze, která není k dispozici v seznamu verzí.

Zobrazí se průběh instalace na kartě npm v okně výstup. To může chvíli trvat.

> [!TIP]
> Můžete hledat balíčků vymezených předponou v podobě vyhledávací dotaz s oborem vás zajímá, zadejte například `@types/mocha` hledat soubory definice TypeScript mocha. Při instalaci definice typů TypeScript, můžete také zadat TypeScript verze se budou zaměřovat přidáním `@ts2.6` v poli argumentů npm.

## <a name="solutionExplorer"></a>Spravovat nainstalované balíčky v Průzkumníku řešení

balíčky npm se zobrazí v Průzkumníku řešení. Položky v části **npm** napodobují závislosti v uzlu *package.json* souboru.

![Hledání balíčku npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stav balíčku
* ![Nainstalovaný balíček](../javascript/media/installed-npm.png) -Nainstalované a jsou uvedeny v souboru package.json
* ![Nadbytečné balíčku](../javascript/media/extraneous-npm.png) – nainstalované, ale nejsou výslovně uvedené v souboru package.json
* ![Chybí balíček](../javascript/media/missing-npm.png) – Není nainstalována, ale uvedené v souboru package.json

Klikněte pravým tlačítkem na uzel balíčku nebo **npm** uzlu proveďte jednu z následujících akcí:
* **Nainstalovat chybějící balíčky** , které jsou uvedeny v *package.json*
* **Aktualizace balíčků** na nejnovější verzi
* **Odinstalovat balíček** a odebrání *package.json*

## <a name="interactive"></a>Použijte příkaz .npm v interaktivním okně Node.js

Můžete také použít `.npm` v interaktivním okně Node.js příkazy npm. Pokud chcete otevřít okno, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a zvolte **otevřete interaktivní okno Node.js**.

V okně slouží k instalaci balíčku příkazech, jako je následující:

`.npm install azure@4.2.3`
 
 > [!Tip]
 > Ve výchozím nastavení spustí npm v domovském adresáři vašeho projektu. Pokud máte více projektů v řešení zadejte název nebo cestu k projektu v závorkách. 
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Pokud projekt neobsahuje soubor package.json, použijte `.npm init -y` vytvořte nový soubor package.json pomocí výchozí položky. 