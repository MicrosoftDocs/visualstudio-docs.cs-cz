---
title: Správa balíčků npm
description: Visual Studio vám pomůže spravovat balíčky pomocí Správce balíčků Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 31eab6c10451bb6be9e53870bf2724c188d650f4
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649499"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Správa balíčků npm v sadě Visual Studio

npm umožňuje instalovat a spravovat balíčky pro použití v aplikacích Node.js. Visual Studio usnadňuje interakci s npm a vydávat příkazy npm prostřednictvím ui nebo přímo. Pokud nejste obeznámeni s npm a chcete se dozvědět více, přejděte na [npm dokumentaci](https://docs.npmjs.com/).

Integrace visual studio s npm se liší v závislosti na typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otevřít složku (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm očekává *node_modules* složku a *package.json* v kořenovém adresáři projektu. Pokud se struktura složek aplikace liší, měli byste upravit strukturu složek, pokud chcete spravovat balíčky npm pomocí sady Visual Studio.

## <a name="nodejs-projects"></a>Projekty Node.js

U projektů Node.js můžete provádět následující úkoly:
* [Instalace balíčků z Průzkumníka řešení](#npmInstallWindow)
* [Správa nainstalovaných balíčků z Průzkumníka řešení](#solutionExplorer)
* [Použití `.npm` příkazu v interaktivním okně Node.js](#interactive)

Tyto funkce spolupracují a synchronizují se systémem projektu a souborem *package.json* v projektu.

### <a name="prerequisites"></a>Požadavky

Chcete-li přidat podporu npm do projektu, potřebujete **zatížení vývoje Node.js** a nainstalovaný runtime Node.js. Podrobné kroky naleznete v [tématu Vytvoření projektu Node.js](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json).

> [!NOTE]
> Pro existující projekty Node.js použijte **šablonu řešení řešení Z existujícího node.js** nebo typ projektu [Otevřít složku (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) k povolení npm v projektu.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Instalace balíčků z Průzkumníka řešení (Node.js)

U projektů Node.js je nejjednodušší způsob, jak nainstalovat balíčky npm, přes instalační okno balíčku npm. Chcete-li získat přístup k tomuto oknu, klepněte pravým tlačítkem myši na uzel **npm** v projektu a vyberte možnost **Instalovat nové balíčky npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Instalace nového balíčku npm z průzkumníka řešení" border="true":::

V tomto okně můžete vyhledat balíček, určit možnosti a nainstalovat.

![Hledat balíček npm](../javascript/media/search-package.png)

* **Typ závislosti** – zvolen mezi **standardními**, **vývojovými**a **volitelnými** balíčky. Standard určuje, že balíček je závislost za běhu, vzhledem k tomu, že vývoj určuje, že balíček je vyžadován pouze během vývoje.
* **Přidat do package.json** - Doporučeno. Tato konfigurovatelná možnost je zastaralá.
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

::: moniker range=">=vs-2019"
Chcete-li provést jednu z následujících akcí, klepněte pravým tlačítkem myši na uzel **npm:**

* **Instalace nových balíčků NPM** Otevře ui pro instalaci nových balíčků.
* **Instalace balíčků NPM** Spustí příkaz instalace npm a nainstaluje všechny balíčky uvedené v *souboru package.json*. (Spustí `npm install`.)
* **Aktualizovat balíčky npm** Aktualizuje balíček na verzi zadanou v *souboru package.json*. (Spustí `npm update --save`.)

Klepněte pravým tlačítkem myši na uzel balíčku a prováďte jednu z následujících akcí:

* **Instalace balíčků npm** Spustí příkaz npm install a nainstaluje verzi balíčku uvedenou v *souboru package.json*. (Spustí `npm install`.)
* **Aktualizovat balíčky npm** Aktualizuje balíček na verzi zadanou v *souboru package.json*. (Spustit `npm update --save`.)
* **Odinstalovat npm balíčky** Odinstalujte balíček a odeberte jej `npm uninstall --save`z *souboru package.json* (Spustí .)
::: moniker-end
::: moniker range="vs-2017"
Klepněte pravým tlačítkem myši na uzel balíčku nebo uzel **npm** a prováďte jednu z následujících akcí:
* **Instalace chybějících balíčků** uvedených v *souboru package.json*
* **Aktualizace balíčků NPM** na nejnovější verzi
* **Odinstalace balíčku** a odebrání z *souboru package.json*
::: moniker-end

>[!NOTE]
> Nápovědu k řešení problémů s balíčky NPM naleznete v [tématu Poradce při potížích](#troubleshooting-npm-packages).

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

Pokud váš projekt ještě neobsahuje soubor *package.json,* můžete jej přidat a povolit podporu npm přidáním souboru *package.json* do projektu.

1. Pokud nemáte nainstalovaný soubor Node.js, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro nejlepší kompatibilitu s externími rozhraními a knihovnami.

   npm vyžaduje Node.js.

1. Chcete-li přidat soubor *package.json,* klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a zvolte **Přidat** > **novou položku**. Zvolte **konfigurační soubor npm**, použijte výchozí název a klepněte na **tlačítko Přidat**.

   ![Přidání souboru package.json do projektu](../javascript/media/npm-add-package-json.png)

   Pokud nevidíte npm konfigurační soubor uvedené, Node.js vývojové nástroje nejsou nainstalovány. Instalační službu sady Visual Studio můžete použít k přidání **vývojovéúlohy Node.js.** Poté opakujte předchozí krok.

1. Zahrnout jeden nebo více balíčků `dependencies` `devDependencies` npm do nebo části *package.json*. Do souboru můžete například přidat následující:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Při uložení souboru Visual Studio přidá balíček pod **závislostí / npm** uzlu v Průzkumníku řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem myši na **soubor package.json** a zvolte **Obnovit balíčky**.

>[!NOTE]
> V některých případech Průzkumník řešení nemusí zobrazit správný stav pro nainstalované balíčky npm. Další informace naleznete v tématu [Poradce při potížích](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalace balíčků pomocí package.json (ASP.NET Core)

U projektů s npm v ceně můžete `package.json`konfigurovat balíčky npm pomocí . Klepněte pravým tlačítkem myši na uzel npm v Průzkumníku řešení a zvolte **Otevřít soubor package.json**.

![Hledat balíček npm](../javascript/media/npm-add-package.png)

Technologie IntelliSense v *souboru package.json* vám pomůže vybrat konkrétní verzi balíčku npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Vybrat verzi balíčku npm" border="true":::

Při uložení souboru Visual Studio přidá balíček pod **závislostí / npm** uzlu v Průzkumníku řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem myši na **soubor package.json** a zvolte **Obnovit balíčky**.

Instalace balíčku může trvat několik minut. Zkontrolujte průběh instalace balíčku přepnutím na výstup **npm** v okně **Výstup.**

![výstup npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Poradce při potížích s balíčky npm

* npm vyžaduje Node.js Pokud nemáte nainstalovaný Soubor Node.js, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro nejlepší kompatibilitu s externími rozhraními a knihovnami.

* U projektů Node.js musíte mít nainstalovanou pracovní zátěž **vývoje Node.js** pro podporu npm.

* V některých případech průzkumník řešení nemusí zobrazit správný stav pro nainstalované balíčky npm z důvodu známého problému [popsaného zde](https://github.com/aspnet/Tooling/issues/479). Balíček se může například při instalaci zobrazit jako nenainstalovaný. Ve většině případů můžete aktualizovat Průzkumníka řešení odstraněním *package.json*, restartováním sady Visual Studio a opětovným přidáním souboru *package.json,* jak je popsáno výše v tomto článku. Nebo při instalaci balíčků můžete použít okno npm Output k ověření stavu instalace.

* Pokud se při vytváření aplikace nebo transkompilaci kódu TypeScriptu zobrazí nějaké chyby, zkontrolujte nekompatibility balíčku npm jako potenciální zdroj chyb. Chcete-li pomoci identifikovat chyby, zkontrolujte okno npm Výstup při instalaci balíčků, jak je popsáno výše v tomto článku. Například pokud jedna nebo více verzí balíčku npm byla zastaralá a má za následek chybu, bude pravděpodobně nutné nainstalovat novější verzi opravit chyby. Informace o použití *souboru package.json* k řízení verzí balíčků npm naleznete v [tématu package.json configuration](../javascript/configure-packages-with-package-json.md).

