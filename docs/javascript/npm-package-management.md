---
title: Správa balíčků npm
description: Sada Visual Studio vám pomůže se správou balíčků pomocí Správce balíčků Node.js (npm).
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d2c7ec425767e432105bfcec493599197e2fd5ec
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815682"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Správa balíčků npm v aplikaci Visual Studio

NPM umožňuje instalovat a spravovat balíčky pro použití v aplikacích Node.js. Visual Studio usnadňuje interakci s npm a vydávání npmch příkazů prostřednictvím uživatelského rozhraní nebo přímo. Pokud neznáte npm a chcete získat další informace, podívejte se do [dokumentace npm](https://docs.npmjs.com/).

Integrace se sadou Visual Studio s npm se liší v závislosti na typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otevřít složku (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> NPM očekává, že se složka *node_modules* a *package.js* v kořenu projektu. Pokud je struktura složky vaší aplikace odlišná, měli byste změnit strukturu složky, pokud chcete spravovat balíčky npm pomocí sady Visual Studio.

## <a name="nodejs-projects"></a>Node.js projekty

U Node.js projektů můžete provádět následující úlohy:
* [Instalovat balíčky z Průzkumník řešení](#npmInstallWindow)
* [Spravovat nainstalované balíčky z Průzkumník řešení](#solutionExplorer)
* [Použití `.npm` příkazu v interaktivním okně Node.js](#interactive)

Tyto funkce společně spolupracují a synchronizují se systémem projektu a *package.js* v souboru v projektu.

### <a name="prerequisites"></a>Předpoklady

Pro přidání podpory npm do projektu potřebujete nainstalovanou úlohu **vývojeNode.js** a modul runtime Node.js. Podrobný postup najdete v tématu [Vytvoření projektu Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> Pro existující projekty Node.js použijte šablonu řešení **z existující Node.js kódu** nebo [otevřené složky (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) , abyste povolili npm v projektu.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Instalovat balíčky z Průzkumník řešení (Node.js)

V případě Node.js projektů je nejjednodušší způsob, jak nainstalovat balíčky NPM, projít oknem instalace balíčku npm. Chcete-li získat přístup k tomuto oknu, klikněte pravým tlačítkem myši na uzel **npm** v projektu a vyberte možnost **instalovat nové balíčky npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Nainstalovat nový balíček npm z Průzkumníka řešení" border="true":::

V tomto okně můžete vyhledat balíček, zadat možnosti a nainstalovat.

![Snímek obrazovky dialogového okna nainstalovat nové balíčky npm Je vybraný balíček Azure 2.2.1-Preview a zobrazí se podrobnosti a možnosti tohoto balíčku.](../javascript/media/search-package.png)

* **Typ závislosti** – volba mezi **standardním**, **vývojem** a **volitelnými** balíčky. Standard určuje, že balíček je běhová závislost, zatímco při vývoji se určuje, že balíček je vyžadován pouze během vývoje.
* **Přidat k package.js** Doporučené. Tato konfigurovatelná možnost je zastaralá.
* **Vybraná verze** – vyberte verzi balíčku, který chcete nainstalovat.
* **Jiné argumenty npm** – zadejte jiné standardní argumenty npm. Můžete například zadat hodnotu verze `@~0.8` , například pro instalaci konkrétní verze, která není v seznamu verzí k dispozici.

Průběh instalace můžete zobrazit ve výstupu **npm** v okně **výstup** . To může nějakou dobu trvat.

![výstup npm](../javascript/media/npm-output.png)

> [!TIP]
> Můžete vyhledat balíčky s vymezeným oborem, které předčekají na vyhledávací dotaz s rozsahem, který vás zajímá, například `@types/mocha` můžete zadat, aby se soubory definic TypeScript pro Mocha vyhledaly. Při instalaci definic typů pro TypeScript můžete také zadat cílovou verzi TypeScriptu přidáním `@ts2.6` do pole argument npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Spravovat nainstalované balíčky v Průzkumník řešení (Node.js)

balíčky npm se zobrazují v Průzkumník řešení. Položky v uzlu **npm** napodobují závislosti v *package.jsv* souboru.

![Snímek obrazovky uzlu npm v Průzkumník řešení znázorňující stav instalace balíčků npm.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stav balíčku

* ![Nainstalovaný balíček](../javascript/media/installed-npm.png) – Nainstalováno a uvedeno v package.jszapnuto
* ![Nadbytečné balíčky ](../javascript/media/extraneous-npm.png) – nainstalováno, ale není výslovně uvedeno v package.jszapnuto
* ![Chybějící balíček](../javascript/media/missing-npm.png) – Není nainstalované, ale je uvedené v package.jsdne.

::: moniker range=">=vs-2019"
Klikněte pravým tlačítkem na uzel **npm** a proveďte jednu z následujících akcí:

* **Nainstalovat nové balíčky npm** Otevře uživatelské rozhraní pro instalaci nových balíčků.
* **Nainstalovat balíčky npm** Spustí příkaz Install NPM, který nainstaluje všechny balíčky uvedené v *package.js*. (Spouští `npm install` .)
* **Aktualizovat balíčky npm** Aktualizuje balíčky na nejnovější verze podle rozsahu SemVer (sémantické verze), který je zadaný v *package.js*. (Spouští se `npm update --save` .). SemVer rozsahy se obvykle zadává pomocí "~" nebo "^". Další informace najdete [ vpackage.jsv konfiguraci](../javascript/configure-packages-with-package-json.md).

Kliknutím pravým tlačítkem myši na uzel balíčku proveďte jednu z následujících akcí:

* **Nainstalovat balíčky npm** Spustí příkaz Install NPM, který nainstaluje verzi balíčku uvedenou v *package.js*. (Spouští `npm install` .)
* **Aktualizovat balíčky npm** Aktualizuje balíček na nejnovější verzi podle rozsahu SemVer zadaného v *package.js*. (Spustit `npm update --save` .) SemVer rozsahy se obvykle zadává pomocí "~" nebo "^".
* **Odinstalace balíčků npm** Odinstaluje balíček a odebere ho z *package.js* (spustí `npm uninstall --save` ).
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

`.npm`K provádění příkazů npm můžete použít také příkaz v interaktivním okně Node.js. Chcete-li otevřít okno, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a vyberte možnost **otevřít Node.js interaktivní okno**.

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

   NPM vyžaduje Node.js.

1. Chcete-li přidat *package.js* do souboru, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a vyberte možnost **Přidat**  >  **novou položku**. Vyberte **konfigurační soubor npm**, použijte výchozí název a klikněte na **Přidat**.

   ![Přidat package.jsdo projektu](../javascript/media/npm-add-package-json.png)

   Pokud se v seznamu nenachází konfigurační soubor NPM, Node.js vývojové nástroje nejsou nainstalované. K přidání úlohy **vývojeNode.js** můžete použít instalační program pro Visual Studio. Pak opakujte předchozí krok.

1. Zahrňte jeden nebo více balíčků npm do `dependencies` `devDependencies` části nebo v *package.jsna*. Do souboru můžete například přidat následující:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Když soubor uložíte, Visual Studio přidá balíček pod uzel **závislosti/npm** v Průzkumník řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem na **package.jsna** a vyberte **obnovit balíčky**.

>[!NOTE]
> V některých scénářích Průzkumník řešení nemusí zobrazovat správný stav nainstalovaných balíčků npm. Další informace naleznete v tématu [Poradce při potížích](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalovat balíčky pomocí package.js(ASP.NET Core)

Pro projekty, které obsahují NPM, můžete nakonfigurovat balíčky npm pomocí `package.json` . V Průzkumník řešení klikněte pravým tlačítkem myši na uzel npm a vyberte možnost **otevřít package.jsna**.

![Snímek obrazovky Průzkumník řešení s vybraným uzlem npm Místní nabídka kliknutí pravým tlačítkem je otevřená a je vybrána možnost otevřít package.js.](../javascript/media/npm-add-package.png)

IntelliSense v *package.js* vám pomůže vybrat konkrétní verzi balíčku npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Vybrat verzi balíčku npm" border="true":::

Když soubor uložíte, Visual Studio přidá balíček pod uzel **závislosti/npm** v Průzkumník řešení. Pokud uzel nevidíte, klikněte pravým tlačítkem na **package.jsna** a vyberte **obnovit balíčky**.

Instalace balíčku může trvat několik minut. V okně **výstupu** přepněte do výstupu **npm** a podívejte se na průběh instalace balíčku.

![výstup npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Řešení potíží s balíčky npm

* NPM vyžaduje Node.js, pokud nemáte Node.js nainstalované, doporučujeme, abyste si nainstalovali verzi LTS z webu [Node.js](https://nodejs.org/en/download/) , abyste dosáhli nejlepší kompatibility s externími architekturami a knihovnami.

* U Node.js projektů musíte mít nainstalovanou úlohu **vývojNode.js** pro podporu npm.

* V některých scénářích Průzkumník řešení nemusí zobrazit správný stav nainstalovaných balíčků npm z důvodu známého problému, který je [zde](https://github.com/aspnet/Tooling/issues/479)popsán. Balíček se například může zobrazit jako nenainstalovaný při instalaci. Ve většině případů můžete aktualizovat Průzkumník řešení odstraněním *package.jsna*, restartováním sady Visual Studio a opětovným přidáním *package.jsdo* souboru, jak je popsáno výše v tomto článku. Nebo při instalaci balíčků můžete použít okno výstup npm k ověření stavu instalace.

* Pokud se při sestavování aplikace nebo transpiling kódu TypeScript zobrazí nějaké chyby, zkontrolujte, že se nekompatibilita balíčku npm v podobě potenciálního zdroje chyb. Pokud chcete identifikovat chyby, podívejte se do okna výstup npm při instalaci balíčků, jak je popsáno výše v tomto článku. Například pokud jedna nebo více npmch verzí balíčku je zastaralých a výsledkem je chyba, možná budete muset nainstalovat novější verzi, abyste opravili chyby. Informace o použití *package.js* k řízení verzí balíčku npm naleznete v části [package.jsv konfiguraci](../javascript/configure-packages-with-package-json.md).
