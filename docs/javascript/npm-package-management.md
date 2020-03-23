---
title: Správa balíčků npm
description: Visual Studio vám pomůže spravovat balíčky pomocí Správce balíčků Node.js (npm)
ms.custom: seodec18
ms.date: 03/12/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dba657d30eedef26337c708e7ede6c5ab85ed4cc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549963"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Správa balíčků npm v sadě Visual Studio

npm umožňuje instalovat a spravovat balíčky pro použití v aplikacích Node.js. Visual Studio usnadňuje interakci s npm a vydávat příkazy npm prostřednictvím ui nebo přímo. Pokud nejste obeznámeni s npm a chcete se dozvědět více, přejděte na [npm dokumentaci](https://docs.npmjs.com/).

Integrace visual studio s npm se liší v závislosti na typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otevřít složku (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm očekává *node_modules* složku a *package.json* v kořenovém adresáři projektu. Pokud se struktura složek aplikace liší, měli byste upravit strukturu složek, pokud chcete spravovat balíčky npm pomocí sady Visual Studio.

> [!NOTE]
> Pro existující projekty Node.js použijte šablonu **řešení řešení Z existujícího node.js** k povolení npm v projektu.

## <a name="nodejs-projects"></a>Projekty Node.js

Pro projekty Node.js použijte jednu z následujících metod:
* [Instalace balíčků z Průzkumníka řešení](#npmInstallWindow)
* [Správa nainstalovaných balíčků z Průzkumníka řešení](#solutionExplorer)
* [Použití `.npm` příkazu v interaktivním okně Node.js](#interactive)

Tyto funkce spolupracují a synchronizují se systémem projektu a souborem *package.json* v projektu.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Instalace balíčků z Průzkumníka řešení (Node.js)

U projektů Node.js je nejjednodušší způsob, jak nainstalovat balíčky npm, přes instalační okno balíčku npm. Chcete-li získat přístup k tomuto oknu, klepněte pravým tlačítkem myši na uzel **npm** v projektu a vyberte možnost **Instalovat nové balíčky npm**.

![Instalace nového balíčku npm z průzkumníka řešení](../javascript/media/solution-explorer-install-package.png)

V tomto okně můžete vyhledat balíček, určit možnosti a nainstalovat.

![Hledat balíček npm](../javascript/media/search-package.png)

* **Typ závislosti** – zvolen mezi **standardními**, **vývojovými**a **volitelnými** balíčky. Standard určuje, že balíček je závislost za běhu, vzhledem k tomu, že vývoj určuje, že balíček je vyžadován pouze během vývoje.
* **Přidat do souboru package.json** – tato možnost je zastaralá.
* **Vybraná verze** - Vyberte verzi balíčku, který chcete nainstalovat.
* **Jiné argumenty npm** - Zadejte jiné standardní argumenty npm. Můžete například zadat hodnotu verze, například `@~0.8` nainstalovat určitou verzi, která není k dispozici v seznamu verzí.

Průběh instalace můžete vidět ve výstupu **npm** v okně **Výstup.** To může nějakou dobu trvat.

![výstup npm](../javascript/media/npm-output.png)

> [!TIP]
> Balíčky s vymezeným oborem můžete vyhledat tak, že vyhledávací dotaz přejdete `@types/mocha` s oborem, který vás zajímá, například zadejte, abyste hledali definiční soubory typescriptu pro moka. Při instalaci definic typů pro TypeScript můžete také určit verzi jazyka TypeScript, na kterou cílíte, přidáním `@ts2.6` do pole argumentů npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Správa nainstalovaných balíčků v Průzkumníku řešení (Node.js)

balíčky npm jsou zobrazeny v Průzkumníku řešení. Položky pod uzlou **npm** napodobují závislosti v souboru *package.json.*

![Hledat balíček npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stav balíčku

* ![Nainstalovaný balíček](../javascript/media/installed-npm.png) - Instalovány a uvedeny v package.json
* ![Cizí balíček](../javascript/media/extraneous-npm.png) - Nainstalováno, ale není výslovně uvedeno v package.json
* ![Chybějící balíček](../javascript/media/missing-npm.png) - Není nainstalován, ale jsou uvedeny v package.json

Klepněte pravým tlačítkem myši na uzel balíčku nebo uzel **npm** a prováďte jednu z následujících akcí:
* **Instalace chybějících balíčků** uvedených v *souboru package.json*
* **Aktualizace balíčků** na nejnovější verzi
* **Odinstalace balíčku** a odebrání z *souboru package.json*

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Použití příkazu .npm v interaktivním okně Node.js (Node.js)

Příkaz v interaktivním `.npm` okně Node.js můžete také použít ke spuštění příkazů npm. Chcete-li okno otevřít, klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a zvolte **interaktivní okno Otevřít soubor Node.js**.

V okně můžete k instalaci balíčku použít následující příkazy:

`.npm install azure@4.2.3`

 > [!Tip]
 > Ve výchozím nastavení se npm spustí v domovském adresáři projektu. Pokud máte více projektů v řešení zadejte název nebo cestu projektu v závorkách.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Pokud váš projekt neobsahuje soubor package.json, použijte `.npm init -y` k vytvoření nového souboru package.json s výchozími položkami.

 ## <a name="aspnet-core-projects"></a>ASP.NET Hlavní projekty

U projektů, jako jsou projekty ASP.NET Core, můžete integrovat podporu npm do projektu a použít npm k instalaci balíčků.
* [Přidání podpory npm do projektu](#npmAdd)
* [Instalace balíčků pomocí souboru package.json](#npmInstallPackage)

>[!NOTE]
> Pro ASP.NET core projekty můžete také použít [Správce knihovny](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) nebo přízi namísto npm k instalaci souborů JavaScript a CSS na straně klienta.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Přidání podpory npm do projektu (ASP.NET Core)

Pokud váš projekt ještě neobsahuje soubor *package.json,* můžete přidat jednu podporu npm přidáním souboru package.json do projektu.

1. Chcete-li soubor přidat, klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a zvolte **Přidat** > **novou položku**. Zvolte **konfigurační soubor npm**, použijte výchozí název a klepněte na **tlačítko Přidat**.

   ![Přidání souboru package.json do projektu](../javascript/media/npm-add-package-json.png)

1. Zahrnout jeden nebo více balíčků `dependencies` `devDependencies` npm do nebo části *package.json*. Do souboru můžete například přidat následující:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Při uložení souboru Visual Studio přidá balíček pod **závislostí / npm** uzlu v Průzkumníku řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem myši na **soubor package.json** a zvolte **Obnovit balíčky**.

>[!NOTE]
> V některých případech může Průzkumník řešení znamenat, že balíček npm není synchronizován s *souborem package.json* z důvodu známého problému [popsaného zde](https://github.com/aspnet/Tooling/issues/479). Balíček se může například při instalaci zobrazit jako nenainstalovaný. Ve většině případů můžete aktualizovat Průzkumníka řešení odstraněním *package.json*, restartováním sady Visual Studio a opětovným přidáním souboru *package.json,* jak je popsáno výše v tomto článku.

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalace balíčků pomocí package.json (ASP.NET Core)

U projektů s npm v ceně můžete `package.json`konfigurovat balíčky npm pomocí . Klepněte pravým tlačítkem myši na uzel npm v Průzkumníku řešení a zvolte **Otevřít soubor package.json**.

![Hledat balíček npm](../javascript/media/npm-add-package.png)

Technologie IntelliSense v *souboru package.json* vám pomůže vybrat konkrétní verzi balíčku npm.

![Hledat balíček npm](../javascript/media/npm-add-package-intellisense.png)

Při uložení souboru Visual Studio přidá balíček pod **závislostí / npm** uzlu v Průzkumníku řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem myši na **soubor package.json** a zvolte **Obnovit balíčky**.

Instalace balíčku může trvat několik minut. Zkontrolujte průběh instalace balíčku přepnutím na výstup **npm** v okně **Výstup.**

![výstup npm](../javascript/media/npm-output.png)

