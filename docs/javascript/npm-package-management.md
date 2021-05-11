---
title: Správa balíčků npm
description: Visual Studio vám pomůže spravovat balíčky pomocí správce balíčků Node.js (npm).
ms.custom: seodec18
ms.date: 02/23/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2fcf1bd9e9ef5c3ff0663cf12684e6e638d1e5e4
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729283"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Správa balíčků npm v Visual Studio

Npm umožňuje instalovat a spravovat balíčky pro použití ve vašich Node.js aplikacích. Visual Studio umožňuje snadnou interakci s npm a vydávání příkazů npm prostřednictvím uživatelského rozhraní nebo přímo. Pokud npm ještě nevíte a chcete se dozvědět víc, přejděte k dokumentaci [k npm.](https://docs.npmjs.com/)

Visual Studio integrace s npm se liší v závislosti na typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otevřít složku (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm očekává složku *node_modules* a *package.jsv* kořenovém adresáři projektu je on. Pokud se struktura složek vaší aplikace liší, měli byste upravit strukturu složek, pokud chcete spravovat balíčky npm pomocí Visual Studio.

## <a name="nodejs-projects"></a>Node.js projekty

U Node.js projektů můžete provádět následující úlohy:
* [Instalace balíčků z Průzkumník řešení](#npmInstallWindow)
* [Správa nainstalovaných balíčků z Průzkumník řešení](#solutionExplorer)
* [V `.npm` interaktivním okně Node.js příkaz](#interactive)

Tyto funkce spolupracují a synchronizují se se systémem projektu a *package.jsna* souboru v projektu.

### <a name="prerequisites"></a>Požadavky

K přidání **podpory npmNode.js** projektu potřebujete nainstalovanou úlohu vývoje Node.js a modul runtime modulu runtime. Podrobný postup najdete v [tématu Vytvoření Node.js projektu.](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json)

> [!NOTE]
> U existujících Node.js projektů použijte šablonu řešení Z existujícího **Node.js** kódu nebo typ projektu Otevřít složku [(Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) a povolte npm ve vašem projektu.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Instalace balíčků z Průzkumník řešení (Node.js)

U Node.js projektů je nejjednodušší způsob, jak nainstalovat balíčky npm, prostřednictvím okna instalace balíčku npm. Chcete-li získat přístup k tomuto oknu, klikněte pravým tlačítkem myši na uzel **npm** v projektu a vyberte možnost **instalovat nové balíčky npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Nainstalovat nový balíček npm z Průzkumníka řešení" border="true":::

V tomto okně můžete vyhledat balíček, zadat možnosti a nainstalovat.

![Snímek obrazovky dialogového okna nainstalovat nové balíčky npm Je vybraný balíček Azure 2.2.1-Preview a zobrazí se podrobnosti a možnosti tohoto balíčku.](../javascript/media/search-package.png)

* **Typ závislosti** – volba mezi **standardním**, **vývojem** a **volitelnými** balíčky. Standard určuje, že balíček je běhová závislost, zatímco při vývoji se určuje, že balíček je vyžadován pouze během vývoje.
* **Přidat k package.js** Doporučené. Tato konfigurovatelná možnost je zastaralá.
* **Vybraná verze** – vyberte verzi balíčku, který chcete nainstalovat.
* **Jiné argumenty npm** – zadejte jiné standardní argumenty npm. Můžete například zadat hodnotu verze `@~0.8` , například pro instalaci konkrétní verze, která není v seznamu verzí k dispozici.

Průběh instalace můžete zobrazit ve výstupu **npm** v okně **výstup** (Chcete-li otevřít okno, zvolte možnost **Zobrazit**  >  **výstup** nebo stiskněte klávesu **CTRL**  +  **ALT**  +  **O**). To může nějakou dobu trvat.

![výstup npm](../javascript/media/npm-output.png)

> [!TIP]
> Můžete vyhledat balíčky s vymezeným oborem, které předčekají na vyhledávací dotaz s rozsahem, který vás zajímá, například `@types/mocha` můžete zadat, aby se soubory definic TypeScript pro Mocha vyhledaly. Při instalaci definic typů pro TypeScript můžete také zadat cílovou verzi TypeScriptu přidáním `@ts2.6` do pole argument npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Spravovat nainstalované balíčky v Průzkumník řešení (Node.js)

balíčky npm se zobrazují v Průzkumník řešení. Položky v uzlu **npm** napodobují závislosti v *package.jsv* souboru.

![Snímek obrazovky uzlu npm v Průzkumník řešení znázorňující stav instalace balíčků npm.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stav balíčku

* ![Nainstalovaný balíček](../javascript/media/installed-npm.png) – Nainstalováno a uvedené v package.jsna
* ![Vnější balíček – ](../javascript/media/extraneous-npm.png) nainstalovaný, ale není explicitně uvedený v package.json
* ![Chybějící balíček](../javascript/media/missing-npm.png) – Nenainstalované, ale uvedené v package.json

::: moniker range=">=vs-2019"
Klikněte pravým tlačítkem na **uzel npm** a udělejte jednu z následujících akcí:

* **Instalace nových balíčků npm** Otevře uživatelské rozhraní pro instalaci nových balíčků.
* **Instalace balíčků npm** Spustí příkaz npm install, který nainstaluje všechny balíčky uvedené v *package.jsna .* (Spustí `npm install` .)
* **Aktualizace balíčků npm** Aktualizuje balíčky na nejnovější verze podle rozsahu sémantické verze (SemVer) zadaného *package.jsna .* (Spustí `npm update --save` .). Rozsahy SemVer jsou obvykle určeny pomocí "~" nebo "^". Další informace najdete v [package.jso konfiguraci](../javascript/configure-packages-with-package-json.md).

Klikněte pravým tlačítkem na uzel balíčku a udělejte jednu z následujících akcí:

* **Instalace balíčků npm** Spustí příkaz npm install, který nainstaluje verzi balíčku uvedenou v *package.jsna .* (Spustí `npm install` .)
* **Aktualizace balíčků npm** Aktualizuje balíček na nejnovější verzi podle rozsahu SemVer určeného v *package.jsna .* (Spusťte `npm update --save` .) Rozsahy SemVer jsou obvykle určeny pomocí "~" nebo "^".
* **Odinstalace balíčků npm** Odinstaluje balíček a odebere ho *zpackage.jsna* (spustí `npm uninstall --save` .)
::: moniker-end
::: moniker range="vs-2017"
Klikněte pravým tlačítkem myši na uzel balíčku nebo na uzel **npm** a proveďte jednu z následujících akcí:
* **Instalace chybějících balíčků** , které jsou uvedené v *package.jsna*
* **Aktualizovat balíčky npm** na nejnovější verzi
* **Odinstalace balíčku** a odebrání z *package.js*
::: moniker-end

>[!NOTE]
> Pomoc s řešením problémů s balíčky npm najdete v tématu [řešení potíží](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Použití příkazu. npm v interaktivním okně Node.js (Node.js)

`.npm`K provádění příkazů npm můžete použít také příkaz v interaktivním okně Node.js. Chcete-li otevřít okno, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a zvolte možnost **otevřít Node.js interaktivní okno** (nebo stiskněte klávesu **CTRL**  +  **K**, **N**).

V okně můžete k instalaci balíčku použít následující příkazy:

`.npm install azure@4.2.3`

 > [!Tip]
 > Ve výchozím nastavení se npm spustí v domovském adresáři vašeho projektu. Pokud máte ve svém řešení více projektů, zadejte název nebo cestu k projektu v závorkách.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Pokud projekt neobsahuje package.jspro soubor, použijte `.npm init -y` k vytvoření nového package.jssouboru s výchozími položkami.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core projekty

U projektů, jako jsou ASP.NET Core projekty, můžete integrovat podporu npm do projektu a použít npm k instalaci balíčků.
* [Přidání podpory npm do projektu](#npmAdd)
* [Instalovat balíčky pomocí package.js](#npmInstallPackage)

>[!NOTE]
> Pro ASP.NET Core projekty můžete použít také [Správce knihovny](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) nebo přízi namísto npm k instalaci souborů JavaScript a CSS na straně klienta.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> Přidat do projektu podporu NPM (ASP.NET Core)

Pokud projekt ještě nezahrnuje *package.jsdo* souboru, můžete ho přidat, aby se povolila podpora npm přidáním *package.js* do souboru do projektu.

1. Pokud nemáte nainstalované Node.js, doporučujeme, abyste si nainstalovali verzi LTS z webu [Node.js](https://nodejs.org/en/download/) , abyste dosáhli nejlepší kompatibility s externími architekturami a knihovnami.

   Npm vyžaduje Node.js.

1. Pokud chcete přidat *souborpackage.js,* klikněte pravým tlačítkem na projekt v souboru Průzkumník řešení zvolte **Přidat** novou položku  >   (nebo stiskněte **Ctrl**  +  **SHIFT**  +  **A).** Zvolte konfigurační **soubor npm,** použijte výchozí název a klikněte na **Přidat.**

   ![Přidání package.jsdo projektu](../javascript/media/npm-add-package-json.png)

   Pokud se konfigurační soubor npm v seznamu nenainstaluje, Node.js nejsou nainstalované vývojové nástroje. K přidání úlohy Instalační program pro Visual Studio dat můžete **použítNode.js prostředí.** Pak opakujte předchozí krok.

1. V části nebo souboru souboru zahrťte `dependencies` jeden nebo více balíčků `devDependencies` *npmpackage.jsna .* Do souboru můžete například přidat následující:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Když soubor uložíte, Visual Studio balíček do **uzlu Závislosti / npm** v Průzkumník řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem napackage.js **a** zvolte **Obnovit balíčky**.

>[!NOTE]
> V některých scénářích Průzkumník řešení pro nainstalované balíčky npm nemusí zobrazit správný stav. Další informace naleznete v tématu [Poradce při potížích](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalace balíčků pomocí package.json (ASP.NET Core)

Pro projekty s zahrnutou npm můžete nakonfigurovat balíčky npm pomocí `package.json` . Klikněte pravým tlačítkem na uzel npm v Průzkumník řešení a zvolte **Otevřít package.jsna .**

![Snímek obrazovky Průzkumník řešení s vybraným uzlem npm Otevře se místní nabídka po kliknutí pravým tlačítkem a package.jsje vybraná možnost Otevřít a zaškrtnuté.](../javascript/media/npm-add-package.png)

IntelliSense *vpackage.json* vám pomůže vybrat konkrétní verzi balíčku npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Výběr verze balíčku npm" border="true":::

Když soubor uložíte, Visual Studio balíček do **uzlu Závislosti / npm** v Průzkumník řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem na **package.jsna** a vyberte **obnovit balíčky**.

Instalace balíčku může trvat několik minut. V okně **výstupu** přepněte do výstupu **npm** a podívejte se na průběh instalace balíčku.

![výstup npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Řešení potíží s balíčky npm

* NPM vyžaduje Node.js, pokud nemáte Node.js nainstalované, doporučujeme, abyste si nainstalovali verzi LTS z webu [Node.js](https://nodejs.org/en/download/) , abyste dosáhli nejlepší kompatibility s externími architekturami a knihovnami.

* U Node.js projektů musíte mít nainstalovanou úlohu **vývojNode.js** pro podporu npm.

* V některých scénářích Průzkumník řešení nemusí zobrazit správný stav nainstalovaných balíčků npm z důvodu známého problému, který je [zde](https://github.com/aspnet/Tooling/issues/479)popsán. Balíček se například může zobrazit jako nenainstalovaný při instalaci. Ve většině případů můžete aktualizovat Průzkumník řešení odstraněním *package.jsna*, restartováním sady Visual Studio a opětovným přidáním *package.jsdo* souboru, jak je popsáno výše v tomto článku. Nebo při instalaci balíčků můžete použít okno výstup npm k ověření stavu instalace.

* V některých scénářích ASP.NET Core nemusí být uzel npm v Průzkumník řešení po sestavení projektu viditelný. Chcete-li znovu zobrazit uzel, klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Uvolnit projekt.** Poté klikněte pravým tlačítkem myši na uzel projektu a zvolte možnost **znovu načíst projekt**.

* Pokud se při sestavování aplikace nebo transpiling kódu TypeScript zobrazí nějaké chyby, zkontrolujte, že se nekompatibilita balíčku npm v podobě potenciálního zdroje chyb. Pokud chcete identifikovat chyby, podívejte se do okna výstup npm při instalaci balíčků, jak je popsáno výše v tomto článku. Například pokud jedna nebo více npmch verzí balíčku je zastaralých a výsledkem je chyba, možná budete muset nainstalovat novější verzi, abyste opravili chyby. Informace o použití *package.js* k řízení verzí balíčku npm naleznete v části [package.jsv konfiguraci](../javascript/configure-packages-with-package-json.md).
