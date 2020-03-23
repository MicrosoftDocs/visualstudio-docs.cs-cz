---
title: Vytvoření aplikace Node.js a React
description: V tomto kurzu vytvoříte aplikaci pomocí nástrojů Node.js Tools for Visual Studio.
ms.custom: mvc
ms.date: 11/01/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 55086c473929158f50f05db790cf5842f1b696db
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550031"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Kurz: Vytvoření aplikace Node.js a React v sadě Visual Studio

Visual Studio umožňuje snadno vytvořit projekt Node.js a zažít intelliSense a další integrované funkce, které podporují Node.js. V tomto kurzu pro Visual Studio vytvoříte projekt webové aplikace Node.js ze šablony sady Visual Studio. Pak vytvoříte jednoduchou aplikaci pomocí Reactu.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu Node.js
> * Přidat balíčky npm
> * Přidat do aplikace kód React
> * Transpilovat JSX
> * Připojit ladicí program

## <a name="before-you-begin"></a>Než začnete

Zde je rychlý FAQ představit vám některé klíčové pojmy.

### <a name="what-is-nodejs"></a>Co je Node.js?

Node.js je prostředí javascriptového runtime na straně serveru, které spouští serverjavascriptový server.

### <a name="what-is-npm"></a>Co je npm?

npm je výchozí správce balíčků pro soubor Node.js. Správce balíčků usnadňuje programátorům publikovat a sdílet zdrojový kód knihoven Node.js a je navržen tak, aby zjednodušil instalaci, aktualizaci a odinstalaci knihoven.

### <a name="what-is-react"></a>Co je React?

React je front-endový rámec pro vytvoření ui.

### <a name="what-is-jsx"></a>Co je JSX?

JSX je rozšíření syntaxe JavaScriptu, které se obvykle používá s React k popisu prvků uživatelského rozhraní. JSX kód musí být transponovány do prostého JavaScriptu, než to může běžet v prohlížeči.

### <a name="what-is-webpack"></a>Co je webpack?

webpack svazky JavaScript soubory, takže mohou běžet v prohlížeči. Může také transformovat nebo zabalit jiné prostředky a prostředky. Často se používá k určení kompilátoru, například Babel nebo TypeScript, pro transpile JSX nebo TypeScript kódu do prostého JavaScriptu.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou visual studio a úlohu vývoje Node.js.

    ::: moniker range=">=vs-2019"
    Pokud jste visual studio 2019 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste visual studio 2017 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha node.js v Instalačníslužbě VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Tento kurz byl testován s verzí 10.16.0.

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro nejlepší kompatibilitu s externími architekturami a knihovnami. Soubor Node.js je vytvořen pro 32bitové a 64bitové architektury. Nástroje Node.js v sadě Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Je vyžadován pouze jeden a instalační program Node.js podporuje pouze jednu, která je nainstalována současně.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nerozpozná nainstalovaný za běhu, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný běh na stránce vlastností (po vytvoření projektu klepněte pravým tlačítkem myši na uzel projektu, zvolte **Vlastnosti**a nastavte **cestu Node.exe**). Můžete použít globální instalaci souboru Node.js nebo můžete určit cestu k místnímu interpretu v každém z projektů Node.js. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Node.js.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** chcete-li otevřít vyhledávací pole, zadejte **Node.js**, pak zvolte **Blank Node.js Web Application - JavaScript**. (I když tento kurz používá kompilátor jazyka TypeScript, kroky vyžadují, abyste začali se šablonou **JavaScriptu.)**
    
    V zobrazeném dialogovém okně zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **JavaScript**a pak zvolte **Node.js**. V prostředním podokně zvolte **Blank Node.js Web Application**, zadejte název **NodejsWebAppBlank**a pak zvolte **OK**.
    ::: moniker-end
    Pokud šablonu projektu **webové aplikace Blank Node.js** nevidíte, je nutné přidat vývojové zatížení **souboru Node.js.** Podrobné pokyny naleznete v tématu [Požadavky](#prerequisites).

    Visual Studio vytvoří nové řešení a otevře příslušný projekt.

    ![Projekt Node.js v Průzkumníku řešení](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Zvýrazněný **tučným písmem** je váš projekt s použitím názvu, který jste zadali v dialogovém okně **Nový projekt.** V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **Vlastnosti**. Můžete provést round-tripping s jinými vývojovými nástroji, protože soubor projektu neprovádí vlastní změny zdroje projektu Node.js.

    (2) Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako váš projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) Uzel npm zobrazuje všechny nainstalované balíčky npm. Můžete klepnout pravým tlačítkem myši na uzel npm a vyhledat a nainstalovat balíčky npm pomocí dialogového okna nebo nainstalovat a aktualizovat balíčky pomocí nastavení v *souboru package.json* a pravým tlačítkem myši v uzlu npm.

    (4) *package.json* je soubor používaný npm ke správě závislostí balíčků a verzí balíčků pro místně nainstalované balíčky. Další informace o tomto souboru naleznete v [tématu package.json configuration](../javascript/configure-packages-with-package-json.md)

    (5) Soubory projektu, jako je *například server.js,* se zobrazí pod uzlou položkou projektu. *server.js* je spouštěcí soubor projektu, a proto se zobrazuje **tučně**. Spouštěcí soubor můžete nastavit tak, že klepnete pravým tlačítkem myši na soubor v projektu a vyberete **možnost Nastavit jako spouštěcí soubor Node.js**.

## <a name="add-npm-packages"></a>Přidat balíčky npm

Tato aplikace vyžaduje ke správnému fungování řadu modulů npm.

* react
* react-dom
* express
* cesta
* ts-loader
* typescript
* webpack
* webpack-cli

1. V Průzkumníku řešení (pravé podokno) klikněte pravým tlačítkem na uzel **npm** v projektu a zvolte **Nainstalovat nové balíčky npm**.

    V dialogovém okně **Nainstalovat nové balíčky npm** můžete zvolit instalaci nejnovější verze balíčků nebo určit konkrétní verzi. Pokud zvolíte instalaci nejnovější verze těchto balíčků, ale při dalším postupu dojde k neočekávaným chybám, bude asi potřeba nainstalovat přesně ty verze balíčků, které jsou uvedené dále v tomto postupu.

1. V dialogovém okně **Instalovat nové balíčky npm** vyhledejte balíček react a vyberte **instalovat balíček** a nainstalujte jej.

    ![Instalace balíčků npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Vyberte okno **Výstup,** chcete-li zobrazit průběh instalace balíčku (v poli **Zobrazit výstup z** vyberte možnost **Npm).** Po dokončení instalace se tento balíček zobrazí pod uzlem **npm**.

    Soubor *package.json* tohoto projektu se aktualizuje informacemi o novém balíčku, včetně verze tohoto balíčku.

1. Místo použití ui hledat a přidávat zbývající balíčky jeden po druhém, vložte následující kód do *package.json*. Chcete-li to `dependencies` provést, přidejte oddíl s tímto kódem:

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    Pokud již existuje `dependencies` oddíl ve vaší verzi prázdné šablony, stačí jej nahradit předchozím kódem JSON. Další informace o použití tohoto souboru naleznete v [tématu package.json configuration](../javascript/configure-packages-with-package-json.md).

1. Uložte změny.

1. Klepněte pravým tlačítkem myši na uzel **npm** v projektu a zvolte **Aktualizovat balíčky npm**.

    V dolním podokně vyberte okno **Výstup,** chcete-li zobrazit průběh instalace balíčků. Instalace může trvat několik minut a nemusí se zobrazit výsledky okamžitě. Chcete-li zobrazit výstup, ujistěte se, že vyberete **Npm** v poli **Zobrazit výstup z** v okně **Výstup.**

    Tady jsou moduly npm, které se po instalaci zobrazí v Průzkumníku řešení.

    ![Balíčky npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Pokud chcete balíčky npm nainstalovat raději pomocí příkazového řádku, klikněte pravým tlačítkem na uzel projektu a zvolte **Otevřít tady příkazový řádek**. K instalaci balíčků použijte standardní příkazy Node.js.

## <a name="add-project-files"></a>Přidání souborů projektu

V tomto postupu do projektu přidáte čtyři nové soubory.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Nové soubory projektu pro tuto jednoduchou aplikaci přidáte do kořenu projektu. (U většiny aplikací se soubory obvykle přidávají do podsložek a odkazy s relativní cestou se podle toho upraví.)

1. V Průzkumníku řešení klikněte pravým tlačítkem na projekt **NodejsWebAppBlank** a zvolte **Přidat** > **Nová položka**.

1. V dialogovém okně **Přidat novou položku** zvolte **TypeScript JSX soubor**, zadejte název *app.tsx*a vyberte **Přidat** nebo **OK**.

1. Opakováním tohoto postupu přidejte *webpack config.js*. Místo souboru Jazyka XSX jazyka TypeScript zvolte **soubor JavaScript**.

1. Opakováním stejného postupu do projektu přidejte *index.html*. Místo souboru JavaScript zvolte **Soubor HTML**.

1. Opakováním stejného postupu do projektu přidejte *tsconfig.json*. Místo souboru JavaScript zvolte **Konfigurační soubor JSON pro TypeScript**.

## <a name="add-app-code"></a>Přidání kódu aplikace

1. Otevřete *soubor server.js* a nahraďte existující kód následujícím kódem:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Uvedený kód spouští Node.js jako server vaší webové aplikace přes Express. Tento kód nastaví port na číslo, které je nakonfigurované ve vlastnostech projektu (ve výchozím nastavení je ve vlastnostech nakonfigurovaný port 1337). Vlastnosti projektu otevřete tak, že v Průzkumníku řešení kliknete pravým tlačítkem na příslušný projekt a zvolíte **Vlastnosti**.

1. Otevřete *app.tsx* a přidejte následující kód:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Uvedený kód používá k zobrazení jednoduché zprávy syntaxi JSX a React.

1. Otevřete *index.html* a nahraďte oddíl **body** následujícím kódem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Tato stránka HTML načte *app-bundle.js* s kódem JSX a React, který bude transpilovaný na prostý JavaScript. Momentálně je soubor *app-bundle.js* prázdný. V další části nakonfigurujete možnosti pro transpilaci tohoto kódu.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Konfigurace webpacku a možností kompilátoru TypeScriptu

V předchozím postupu jste do projektu přidali *webpack-config.js*. Dále přidáte kód pro konfiguraci webpacku. Přidáte jednoduchou konfiguraci webpacku, která určuje vstupní soubor (*app.tsx*) a výstupní soubor (*app-bundle.js*) pro sbalení a transpilaci JSX na prostý JavaScript. Pro transpilaci můžete nakonfigurovat také některé možnosti kompilátoru TypeScriptu. Tento kód představuje základní konfiguraci, která slouží k seznámení s webpackem a kompilátorem TypeScriptu.

1. V Průzkumníku řešení otevřete *webpack-config.js* a přidejte následující kód.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Konfigurační kód webpacku dává webpacku pokyn, aby pomocí zavaděče TypeScript překládky překládky JSX.

1. Otevřete *soubor tsconfig.json* a nahraďte výchozí kód následujícím kódem, který určuje volby kompilátoru jazyka TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    Jako zdrojový soubor je určený *app.tsx*.

## <a name="transpile-the-jsx"></a>Transpilace JSX

1. V Průzkumníku řešení klikněte pravým tlačítkem na uzel projektu a zvolte **Otevřít tady příkazový řádek**.

1. V příkazovém řádku zadejte následující příkaz:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    V okně příkazového řádku se zobrazí výsledek.

    ![Spuštění webpacku](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Pokud se místo uvedeného výstupu zobrazují nějaké chyby, je potřeba je před použitím aplikace odstranit. Příčinou těchto chyb může být skutečnost, že se vaše verze balíčků npm liší od verzí používaných v tomto kurzu. Jednou možností, jak chyby odstranit, je použití přesně těch verzí, které jsou uvedené v dřívějším postupu. Pokud jsou některé z těchto verzí balíčků zastaralé a způsobují chyby, může být k odstranění chyb potřeba nainstalovat novější verze. Informace o použití *souboru package.json* k řízení verzí balíčků npm naleznete v [tématu package.json configuration](../javascript/configure-packages-with-package-json.md).

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **existující složku**, pak zvolte složku *dist* a zvolte **Vybrat složku**.

    Visual Studio přidá do projektu složku *dist*, která obsahuje *app-bundle.js* a *app-bundle.js.map*.

1. Otevřete *app-bundle.js* a zobrazte transpilovaný kód jazyka JavaScript.

1. Pokud se zobrazí výzva k opětovnému načtení externě změněných souborů, vyberte **možnost Ano všem**.

    ![Načtení změněných souborů](../javascript/media/tutorial-nodejs-react-reload-files.png)

Vždycky, když provedete změny v *app.tsx*, je nutné znovu spustit příkaz webpack. Chcete-li tento krok automatizovat, přidejte skript sestavení pro transpile JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Přidání skriptu sestavení pro transpile JSX

Počínaje Visual Studio 2019 je vyžadován skript sestavení. Namísto transpilace JSX na příkazovém řádku (jak je znázorněno v předchozí části), můžete transpile JSX při vytváření z Visual Studio.

* Otevřete *package.json* a za `dependencies` oddíl přidejte následující oddíl:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Spuštění aplikace

1. Jako aktuální cíl ladění vyberte Microsoft Edge nebo Chrome.

    ::: moniker range=">=vs-2019"
    ![Výběr Chromu jako cíle ladění](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Výběr Chromu jako cíle ladění](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Pokud je Chrome ve vašem počítači k dispozici, ale nezobrazuje se jako možnost, zvolte **webový prohlížeč (název prohlížeče)** > **Vyberte webový prohlížeč** z rozevíracího seznamu ladění cíle a vyberte **Chrome** jako výchozí cíl prohlížeče.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud je Chrome ve vašem počítači k dispozici, ale nezobrazuje se jako možnost, zvolte z rozevíracího seznamu ladění cílovou adresu **Prohlížeče (název prohlížeče)** > **Google Chrome** a jako výchozí cíl prohlížeče vyberte Prohlížeč **Chrome.**
    ::: moniker-end

1. Ke spuštění aplikace stiskněte **F5** (**Ladit** > **Spustit ladění**) nebo tlačítko se zelenou šipkou.

    Otevře se okno konzoly Node.js, které zobrazuje port, na kterém ladicí program naslouchá.

    Visual Studio spustí danou aplikaci spuštěním spouštěcího souboru *server.js*.

    ![Spuštění Reactu v prohlížeči](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zavřete okno prohlížeče.

1. Zavřete okno konzoly.

## <a name="set-a-breakpoint-and-run-the-app"></a>Nastavení zarážky a spuštění aplikace

1. V souboru *server.js* kliknutím do mezery vedle okraje nalevo od deklarace `staticPath` nastavte zarážku:

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

1. Ke spuštění aplikace stiskněte **F5** (**Ladit** > **Spustit ladění**).

    Ladicí program se pozastaví na zarážce, kterou jste nastavili (aktuální příkaz je označený žlutě). Teď můžete stav aplikace zkontrolovat tak, že přesunete ukazatel myši nad proměnné v aktuálním rozsahu a použijete okna ladicího programu, například okna **Místní hodnoty** a **Kukátko**.

1. Pokud chcete pokračovat v aplikaci, stiskněte **F5**.

1. Pokud chcete používat nástroje pro vývojáře Chrome nebo nástroje F12 pro microsoft edge, stiskněte **klávesu F12**. Pomocí těchto nástrojů můžete prozkoumat model DOM a provádět interakce s aplikací pomocí konzoly jazyka JavaScript.

1. Zavřete webový prohlížeč a konzolu.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Nastavení a použití zarážky v kódu React na straně klienta

V předchozí části jste připojili ladicí program ke kódu Node.js na straně serveru. K připojení ladicího programu ze sady Visual Studio a používání zarážek v kódu React na straně klienta se v ladicím programu vyžaduje pomoc s identifikací správného procesu. Tady je jedna možnost, jak to udělat.

### <a name="prepare-the-browser-for-debugging"></a>Příprava prohlížeče na ladění

::: moniker range=">=vs-2019"
V tomto scénáři použijte buď Microsoft Edge (Chromium), aktuálně pojmenovaný **Microsoft Edge Beta** v IDE nebo Chrome.
::: moniker-end
::: moniker range="vs-2017"
V tomto scénáři použijte Chrome.
::: moniker-end

1. Zavřete všechna okna pro cílový prohlížeč.

   Jiné instance prohlížeče mohou zabránit otevření prohlížeče s povoleným laděním. (Rozšíření prohlížeče mohou být spuštěna a brání úplnému režimu ladění, takže možná budete muset otevřít Správce úloh, abyste našli neočekávané instance Chromu.)

   ::: moniker range=">=vs-2019"
   Pro Microsoft Edge (Chromium) také vypněte všechny instance Chromu. Vzhledem k tomu, že oba prohlížeče sdílejí základ kódu chromu, poskytuje to nejlepší výsledky.
   ::: moniker-end

2. Spusťte prohlížeč s povoleným laděním.

    ::: moniker range=">=vs-2019"
    Počínaje Visual Studio 2019, můžete `--remote-debugging-port=9222` nastavit příznak na spuštění prohlížeče výběrem **Procházet s ...** > z panelu nástrojů **ladění,** pak zvolte **Přidat**a pak nastavení příznaku v poli **Argumenty.** Pro prohlížeč použijte jiný popisný název, například **Edge with Debugging** nebo **Chrome with Debugging**. Podrobnosti naleznete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes-v16.2).

    ![Nastavení otevření prohlížeče s povoleným laděním](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Případně otevřete příkaz **Spustit** z tlačítka **Start** systému Windows (klepněte pravým tlačítkem myši a zvolte **Spustit)** a zadejte následující příkaz:

    `msedge --remote-debugging-port=9222`

    Nebo

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Otevřete příkaz **Spustit** z tlačítka Windows **Start** (klikněte na něj pravým tlačítkem a zvolte **Spustit**) a zadejte následující příkaz:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Tím se spustí prohlížeč s povolenou ladění.

    Aplikace ještě není spuštěná, takže dostanete prázdnou stránku prohlížeče.

### <a name="attach-the-debugger-to-client-side-script"></a>Připojení ladicího programu ke skriptu na straně klienta

1. Přepněte do sady Visual Studio a nastavte zarážku ve zdrojovém kódu, a to buď *ve zdrojovém kódu,* a to buď ve zdrojovém kódu, nebo *app.tsx*.

    Pro *soubor app-bundle.js*nastavte zarážku ve `render()` funkci, jak je znázorněno na následujícím obrázku:

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Chcete-li `render()` najít funkci v souboru transpilované *aplikace bundle.js,* použijte **kombinaci kláves Ctrl**+**F** (**Upravit** > **hledání a nahrazení** > **rychlého hledání**).

    Pro *app.tsx*nastavte zarážku uvnitř `render()` `return` funkce, na příkaz.

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Pokud nastavujete zarážku v souboru *.tsx* (spíše než *app-bundle.js*), je třeba aktualizovat *webpack-config.js*. Nahraďte následující kód:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    s tímto kódem:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Toto je nastavení pouze pro vývoj povolit ladění v sadě Visual Studio. Toto nastavení umožňuje přepsat generované odkazy ve zdrojovém mapovém *souboru, app-bundle.js.map*, při vytváření aplikace. Ve výchozím nastavení obsahují odkazy na webové balíčky ve zdrojovém mapovém souboru *webpack:///* předponu, která brání aplikaci Visual Studio v hledání zdrojového souboru *app.tsx*. Konkrétně při této změně se odkaz na zdrojový soubor *app.tsx*změní z *webpack:///./app.tsx* na *./app.tsx*, který umožňuje ladění.

3. Vyberte cílový prohlížeč jako ladicí cíl v sadě Visual Studio a stisknutím **kláves Ctrl**+**F5** **(Ladění** > **startu bez ladění)** aplikaci spusťte v prohlížeči.

    ::: moniker range=">=vs-2019"
    Pokud jste vytvořili konfiguraci prohlížeče s popisným názvem, zvolte ji jako cíl ladění.
    ::: moniker-end

    Aplikace se otevře na nové kartě prohlížeče.

4. Zvolte **Připojit ladění** > **ke zpracovat**.

    > [!TIP]
    > Počínaje Visual Studio 2017, po prvním připojení k procesu pomocí následujících kroků, můžete rychle znovu připojit ke stejnému procesu výběrem **ladění** > **znovu připojit k procesu**.

5. V dialogovém okně **Připojit k procesu** získáte filtrovaný seznam instancí prohlížeče, ke kterým se můžete připojit.

    ::: moniker range=">=vs-2019"
    V Sadě Visual Studio 2019 zvolte správný ladicí program pro cílový prohlížeč, **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge - Chromium)** v **poli Připojit k,** zadejte **chrom** nebo **okraj** do pole filtru pro filtrování výsledků hledání.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V Sadě Visual Studio 2017 zvolte v poli **Připojit k** **kód Webkitu** a do pole filtru zadejte **chrom,** abyste filtrovat výsledky hledání.
    ::: moniker-end

6. Vyberte proces prohlížeče se správným hostitelským portem (localhost v tomto příkladu) a vyberte **Připojit**.

    Port (1337) se může také zobrazit v poli **Název,** který vám pomůže vybrat správnou instanci prohlížeče.

    ::: moniker range=">=vs-2019"
    Následující příklad ukazuje, jak to vypadá pro prohlížeč Microsoft Edge (Chromium).

    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Pokud se v sadě Visual Studio otevřely Průzkumník modelu DOM a konzola jazyka JavaScript, je ladicí program správně připojený. Tyto ladicí nástroje jsou podobné nástrojům pro vývojáře Chrome a nástrojům F12 pro Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Pokud se ladicí program nepřipojí a zobrazí se zpráva „Nelze připojit k procesu. Operace není v aktuálním stavu legální.", pomocí Správce úloh zavřete všechny instance cílového prohlížeče před spuštěním prohlížeče v režimu ladění. Rozšíření prohlížeče může být spuštěna a brání režimu úplnéladění.

7. Kód se zarážkou se už spustil, a proto aktualizujte stránku prohlížeče, aby narazil na zarážku.

    Při pozastavení můžete v ladicím programu zkontrolovat stav aplikace tak, že přesunete ukazatel myši nad proměnné a použijete okna ladicího programu. Můžete v ladicím programu procházet kód pomocí krokování (**F5**, **F10** a **F11**). Další informace o základních funkcích ladění naleznete [v tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md).

    Zarážku můžete narazit na soubor *app-bundle.js* nebo v jejím mapovaném umístění v *souboru app.tsx*podle kroků, které jste postupovali dříve, spolu s prostředím a stavem prohlížeče. V obou případech můžete procházet kód pomocí krokování a zkoumat proměnné.

   * Pokud potřebujete proniknout do kódu v *app.tsx* a nedaří se vám to, připojte ladicí program pomocí dialogového okna **Připojit k procesu**, jak bylo popsáno v předchozím postupu. Ujistěte se, že je vaše prostředí správně nastaveno:

      * Zavřeli jste všechny instance prohlížeče, včetně rozšíření Chrome (pomocí Správce úloh), abyste mohli prohlížeč spustit v režimu ladění. Ujistěte se, že jste spustili prohlížeč v režimu ladění.

      * Ujistěte se, že zdrojový mapový soubor obsahuje odkaz na *soubor ./app.tsx* a nikoli *webpack:///./app.tsx*, který brání ladicímu programu sady Visual Studio v hledání *souboru app.tsx*.
       Případně, pokud potřebujete proniknout do kódu v *app.tsx* a nemůžete to `debugger;` udělat, zkuste použít příkaz v *app.tsx*nebo nastavte zarážky v Nástrojích pro vývojáře Chrome (nebo F12 Tools for Microsoft Edge).

   * Pokud potřebujete proniknout do kódu v *app-bundle.js* a nemůžete to udělat, odeberte zdrojový mapový soubor, *app-bundle.js.map*.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do linuxové služby App Service](../javascript/publish-nodejs-app-azure.md)
