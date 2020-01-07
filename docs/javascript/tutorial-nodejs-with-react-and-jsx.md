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
ms.openlocfilehash: faf418155708ebc577efea57ed3352953a8d577d
ms.sourcegitcommit: 5920a8b0c68350f11eabc1652a19b04d0196881a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75622572"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Kurz: Vytvoření aplikace Node.js a React v sadě Visual Studio

Visual Studio umožňuje snadno vytvořit projekt Node. js a zkušenosti s IntelliSense a dalšími integrovanými funkcemi, které podporují Node. js. V tomto kurzu pro Visual Studio vytvoříte projekt webové aplikace Node.js ze šablony sady Visual Studio. Pak vytvoříte jednoduchou aplikaci pomocí Reactu.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvořit projekt Node.js
> * Přidat balíčky npm
> * Přidat do aplikace kód React
> * Transpilovat JSX
> * Připojit ladicí program

## <a name="before-you-begin"></a>Než začnete

Tady je stručné Nejčastější dotazy, které vám povedou k předvedeným klíčovým konceptům.

### <a name="what-is-nodejs"></a>Co je Node.js?

Node. js je běhové prostředí JavaScriptu na straně serveru, které spouští JavaScript na straně serveru.

### <a name="what-is-npm"></a>Co je npm?

NPM je výchozí správce balíčků pro Node. js. Správce balíčků usnadňuje programátorům publikování a sdílení zdrojového kódu knihoven Node. js a je navržen pro zjednodušení instalace, aktualizace a odinstalace knihoven.

### <a name="what-is-react"></a>Co reaguje?

Reakce je front-endové rozhraní pro vytvoření uživatelského rozhraní.

### <a name="what-is-jsx"></a>Co je JSX?

JSX je rozšíření syntaxe JavaScriptu, které se obvykle používá s reakci na popis prvků uživatelského rozhraní. JSX kód musí být převeden na prostý JavaScript předtím, než může běžet v prohlížeči.

### <a name="what-is-webpack"></a>Co je to sada Webpack?

sada Webpack rozbalí soubory JavaScriptu tak, aby mohly běžet v prohlížeči. Může také transformovat nebo zabalit další prostředky a prostředky. Často se používá k určení kompilátoru, jako je Babel nebo TypeScript, k přeformátování JSX nebo kódu TypeScript na prostý JavaScript.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node. js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2019, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2017, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha Node.js v instalačním programu VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Tento kurz byl testován pomocí 10.16.0 verze.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Node.js.

1. Otevřít Visual Studio.

1. Vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **Node. js**a pak zvolte **prázdná webová aplikace Node. js – JavaScript**. (I když tento kurz používá kompilátor TypeScript, postup vyžaduje, abyste začali s šablonou **JavaScriptu** .)
    
    V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **JavaScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **prázdná webová aplikace Node. js**, zadejte název **NodejsWebAppBlank**a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte prázdnou šablonu projektu **webové aplikace Node. js** , je nutné přidat úlohu **vývoje Node. js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří nové řešení a otevře příslušný projekt.

    ![Projekt Node.js v Průzkumníku řešení](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) zvýrazněná **tučně** je váš projekt pomocí názvu, který jste zadali v dialogovém okně **Nový projekt** . V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **Vlastnosti**. Můžete provést operaci round-trip s jinými nástroji pro vývoj, protože soubor projektu neprovádí vlastní změny ve zdroji projektu Node. js.

    (2) na nejvyšší úrovni je řešení, které ve výchozím nastavení má stejný název jako projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) uzel npm zobrazuje všechny nainstalované balíčky npm. Kliknutím pravým tlačítkem myši na uzel npm můžete vyhledat a nainstalovat balíčky npm pomocí dialogového okna nebo nainstalovat a aktualizovat balíčky pomocí nastavení v balíčku npm. *JSON* a kliknutím pravým tlačítkem myši na možnosti v uzlu.

    (4) *Package. JSON* je soubor, který npm používá ke správě závislostí balíčků a verzí balíčků pro místně instalované balíčky. Další informace o tomto souboru najdete v tématu [Konfigurace Package. JSON.](../javascript/configure-packages-with-package-json.md)

    (5) soubory projektu, například *Server. js* , se zobrazí pod uzlem projektu. *Server. js* je spouštěcí soubor projektu a je, proč se zobrazuje **tučně**. Spouštěcí soubor můžete nastavit tak, že kliknete pravým tlačítkem na soubor v projektu a vyberete **nastavit jako spouštěcí soubor Node. js**.

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

1. V dialogovém okně **instalovat nové balíčky npm** vyhledejte balíček s možností reakce a vyberte **nainstalovat balíček** a nainstalujte ho.

    ![Instalace balíčků npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Vyberte okno **výstup** , ve kterém se zobrazí průběh instalace balíčku (vyberte **npm** v poli **Zobrazit výstup z** ). Po dokončení instalace se tento balíček zobrazí pod uzlem **npm**.

    Soubor *package.json* tohoto projektu se aktualizuje informacemi o novém balíčku, včetně verze tohoto balíčku.

1. Místo použití uživatelského rozhraní k vyhledání a přidání zbývajících částí balíčků vložte do soubor *Package. JSON*následující kód. Chcete-li to provést, přidejte část `dependencies` s tímto kódem:

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

    Pokud je ve vaší verzi prázdné šablony již `dependencies` oddíl, stačí ho nahradit předchozím kódem JSON. Další informace o používání tohoto souboru najdete v tématu [Konfigurace Package. JSON](../javascript/configure-packages-with-package-json.md).

1. Uložte změny.

1. V projektu klikněte pravým tlačítkem na uzel **npm** a vyberte **Aktualizovat balíčky npm**.

    V dolním podokně vyberte okno **výstup** , abyste viděli pokrok při instalaci balíčků. Instalace může trvat několik minut a okamžitě se výsledky neprojeví. Chcete-li zobrazit výstup, ujistěte se, že jste vybrali možnost **npm** v poli **Zobrazit výstup z** v okně **výstup** .

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

1. V dialogovém okně **Přidat novou položku** zvolte **soubor TypeScript JSX**, zadejte název *App. TSX*a vyberte **Přidat** nebo **OK**.

1. Opakováním tohoto postupu přidejte *webpack config.js*. Místo souboru TypeScript JSX vyberte **soubor JavaScriptu**.

1. Opakováním stejného postupu do projektu přidejte *index.html*. Místo souboru JavaScript zvolte **Soubor HTML**.

1. Opakováním stejného postupu do projektu přidejte *tsconfig.json*. Místo souboru JavaScript zvolte **Konfigurační soubor JSON pro TypeScript**.

## <a name="add-app-code"></a>Přidání kódu aplikace

1. Otevřete *Server. js* a nahraďte existující kód následujícím kódem:

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

    Konfigurační kód pro sadu Webpack instruuje sadu Webpack, aby používala zavaděč TypeScript k JSXí.

1. Otevřete *tsconfig. JSON* a nahraďte výchozí kód následujícím kódem, který určuje možnosti kompilátoru TypeScript:

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

    Pokud se místo uvedeného výstupu zobrazují nějaké chyby, je potřeba je před použitím aplikace odstranit. Příčinou těchto chyb může být skutečnost, že se vaše verze balíčků npm liší od verzí používaných v tomto kurzu. Jednou možností, jak chyby odstranit, je použití přesně těch verzí, které jsou uvedené v dřívějším postupu. Pokud jsou některé z těchto verzí balíčků zastaralé a způsobují chyby, může být k odstranění chyb potřeba nainstalovat novější verze. Informace o použití *balíčku Package. JSON* k řízení verzí balíčku npm najdete v tématu [Konfigurace Package. JSON](../javascript/configure-packages-with-package-json.md).

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **existující složku**, zvolte složku *DIST* a zvolte **možnost vybrat složku**.

    Visual Studio přidá do projektu složku *dist*, která obsahuje *app-bundle.js* a *app-bundle.js.map*.

1. Otevřete *app-bundle.js* a zobrazte transpilovaný kód jazyka JavaScript.

1. Pokud se zobrazí výzva k opětovnému načtení externě upravených souborů, vyberte **Ano pro všechny**.

    ![Načtení změněných souborů](../javascript/media/tutorial-nodejs-react-reload-files.png)

Vždycky, když provedete změny v *app.tsx*, je nutné znovu spustit příkaz webpack. Chcete-li tento krok automatizovat, přidejte skript sestavení pro JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Přidání skriptu sestavení pro přebudování JSX

Počínaje verzí Visual Studio 2019 je vyžadován skript sestavení. Namísto transpiling JSX na příkazovém řádku (jak je znázorněno v předchozí části), můžete přepracovat JSX při sestavování ze sady Visual Studio.

* Otevřete soubor *Package. JSON* a přidejte následující část za `dependencies` oddíl:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Spuštění aplikace

1. Jako aktuální cíl ladění vyberte buď Microsoft Edge, nebo Chrome.

    ::: moniker range=">=vs-2019"
    ![Výběr Chromu jako cíle ladění](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Výběr Chromu jako cíle ladění](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Pokud je v počítači k dispozici Chrome, ale nezobrazuje se jako možnost, zvolte **webový prohlížeč (browser)** > v rozevíracím seznamu cíl ladění vyberte **webový prohlížeč** a jako výchozí cíl prohlížeče vyberte **Chrome** .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud je v počítači k dispozici Chrome, ale nezobrazuje se jako možnost, zvolte **webový prohlížeč (browser)** > **Google Chrome** z rozevíracího seznamu cíl ladění a jako výchozí cíl prohlížeče vyberte **Chrome** .
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

1. Pokud chcete použít Vývojářské nástroje nebo nástroje pro Chrome pro Microsoft Edge, stiskněte klávesu **F12**. Pomocí těchto nástrojů můžete prozkoumat model DOM a provádět interakce s aplikací pomocí konzoly jazyka JavaScript.

1. Zavřete webový prohlížeč a konzolu.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Nastavení a použití zarážky v kódu React na straně klienta

V předchozí části jste připojili ladicí program ke kódu Node.js na straně serveru. K připojení ladicího programu ze sady Visual Studio a používání zarážek v kódu React na straně klienta se v ladicím programu vyžaduje pomoc s identifikací správného procesu. Tady je jedna možnost, jak to udělat.

### <a name="prepare-the-browser-for-debugging"></a>Příprava prohlížeče pro ladění

::: moniker range=">=vs-2019"
V tomto scénáři použijte Microsoft Edge (chrom), aktuálně pojmenovaný **Microsoft Edge beta** , v integrovaném vývojovém prostředí (IDE) nebo Chrome.
::: moniker-end
::: moniker range="vs-2017"
V tomto scénáři použijte Chrome.
::: moniker-end

1. Zavřete všechna okna pro cílový prohlížeč.

   Jiné instance prohlížeče můžou zabránit otevírání prohlížeče s povoleným laděním. (Rozšíření prohlížeče můžou běžet a bránit úplnému režimu ladění, takže možná budete muset otevřít Správce úloh a najít neočekávané instance Chromu.)

   ::: moniker range=">=vs-2019"
   V případě Microsoft Edge (chrom) vypněte také všechny instance aplikace Chrome. Vzhledem k tomu, že oba prohlížeče sdílí základní kód Chromu, dává to nejlepší výsledky.
   ::: moniker-end

   ::: moniker range=">=vs-2019"
   V případě Microsoft Edge (chrom) vypněte také všechny instance aplikace Chrome. Vzhledem k tomu, že oba prohlížeče používají základ kódu Chromu, dává to nejlepší výsledky.
   ::: moniker-end

2. Spusťte prohlížeč s povoleným laděním.

    ::: moniker range=">=vs-2019"
    Od sady Visual Studio 2019 můžete nastavit příznak `--remote-debugging-port=9222` při spuštění prohlížeče tak, že vyberete **Procházet s...** > z panelu nástrojů **ladění** a pak vyberete **Přidat**a pak nastavíte příznak v poli **argumenty** . Použijte jiný popisný název prohlížeče, jako je například **Edge s laděním** nebo **Chrome s laděním**. Podrobnosti najdete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes-v16.2).

    ![Nastavte prohlížeč tak, aby se otevřel s povoleným laděním.](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternativně otevřete příkaz **Run** z tlačítka **Start** systému Windows (klikněte pravým tlačítkem myši a vyberte možnost **Spustit**) a zadejte následující příkaz:

    `msedge --remote-debugging-port=9222`

    nebo,

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Otevřete příkaz **Spustit** z tlačítka Windows **Start** (klikněte na něj pravým tlačítkem a zvolte **Spustit**) a zadejte následující příkaz:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Spustí se prohlížeč s povoleným laděním.

    Aplikace ještě není spuštěná, takže získáte prázdnou stránku prohlížeče.

### <a name="attach-the-debugger-to-client-side-script"></a>Připojení ladicího programu ke skriptu na straně klienta

1. Přepněte do sady Visual Studio a pak nastavte zarážku ve zdrojovém kódu, buď *App-Bundle. js* , nebo *App. TSX*.

    Pro *App-Bundle. js*nastavte zarážku ve funkci `render()`, jak je znázorněno na následujícím obrázku:

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Chcete-li najít funkci `render()` v souboru *App-Bundle. js* , použijte **kombinaci kláves CTRL**+**F** (**Upravit** > **Najít a nahradit** > **Rychlé hledání**).

    Pro *App. TSX*nastavte zarážku uvnitř funkce `render()` v příkazu `return`.

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Pokud nastavujete zarážku v souboru *. TSX* (spíše než *App-Bundle. js*), musíte aktualizovat *Webpack-config. js*. Nahraďte následující kód:

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

    Toto je nastavení jenom pro vývoj, které umožňuje ladění v aplikaci Visual Studio. Toto nastavení umožňuje při sestavování aplikace přepsat vygenerované odkazy v souboru zdrojového mapování *App-Bundle. js. map*. Ve výchozím nastavení odkazy na sadu Webpack v souboru zdrojového mapování zahrnují předponu *Webpack:///* , která brání sadě Visual Studio najít zdrojový soubor *App. TSX*. Konkrétně při provedení této změny se odkaz na zdrojový soubor *App. TSX*změní z *Webpack:///./app.TSX* na *./app.TSX*, který umožňuje ladění.

3. Vyberte cílový prohlížeč jako cíl ladění v aplikaci Visual Studio a potom stiskněte **klávesu Ctrl**+**F5** (**ladění** > **Spustit bez ladění**) pro spuštění aplikace v prohlížeči.

    ::: moniker range=">=vs-2019"
    Pokud jste vytvořili konfiguraci prohlížeče s popisným názvem, vyberte jako cíl ladění.
    ::: moniker-end

    Aplikace se otevře na nové kartě prohlížeče.

4. Zvolte **Ladit** > **Připojit k procesu**.

    > [!TIP]
    > Od aplikace Visual Studio 2017 se po prvním připojení k procesu pomocí následujícího postupu můžete rychle znovu připojit ke stejnému procesu výběrem možnosti **ladit** > znovu **připojit k procesu**.

5. V dialogovém okně **připojit k procesu** Získejte filtrovaný seznam instancí prohlížeče, ke kterým se můžete připojit.

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 vyberte správný ladicí program pro cílový prohlížeč, **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge-chrom)** v poli **připojit k** , pokud chcete filtrovat výsledky hledání, zadejte v poli Filtr text **Chrome** nebo **Edge** .
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 v poli **připojit k** vyberte **WebKit kód** , do pole Filtr zadejte **Chrome** a vyfiltrujte výsledky hledání.
    ::: moniker-end

6. V tomto příkladu vyberte proces prohlížeče se správným hostitelským portem (localhost) a vyberte **připojit**.

    Port (1337) se může také zobrazit v poli **název** , abyste si mohli vybrat správnou instanci prohlížeče.

    ::: moniker range=">=vs-2019"
    Následující příklad ukazuje, jak to vypadá v prohlížeči Microsoft Edge (chrom).

    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Pokud se v sadě Visual Studio otevřely Průzkumník modelu DOM a konzola jazyka JavaScript, je ladicí program správně připojený. Tyto ladicí nástroje jsou podobné nástrojům Chrome Vývojářské nástroje a F12 pro Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Pokud se ladicí program nepřipojí a zobrazí se zpráva „Nelze připojit k procesu. Operace není v aktuálním stavu platná. pomocí Správce úloh zavřete všechny instance cílového prohlížeče před spuštěním prohlížeče v režimu ladění. Rozšíření prohlížeče můžou být spuštěná a zabraňují úplnému režimu ladění.

7. Kód se zarážkou se už spustil, a proto aktualizujte stránku prohlížeče, aby narazil na zarážku.

    Při pozastavení můžete v ladicím programu zkontrolovat stav aplikace tak, že přesunete ukazatel myši nad proměnné a použijete okna ladicího programu. Můžete v ladicím programu procházet kód pomocí krokování (**F5**, **F10** a **F11**). Další informace o funkcích základního ladění naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

    Zarážku můžete narazit buď na *App-Bundle. js* , nebo na jeho mapované umístění v *App. TSX*v závislosti na tom, jaké kroky jste předtím použili, spolu s vaším prostředím a stavem prohlížeče. V obou případech můžete procházet kód pomocí krokování a zkoumat proměnné.

   * Pokud potřebujete proniknout do kódu v *app.tsx* a nedaří se vám to, připojte ladicí program pomocí dialogového okna **Připojit k procesu**, jak bylo popsáno v předchozím postupu. Ujistěte se, že je prostředí správně nastavené:

      * Zavřeli jste všechny instance prohlížeče, včetně rozšíření Chrome (pomocí Správce úloh), abyste mohli spustit prohlížeč v režimu ladění. Ujistěte se, že jste spustili prohlížeč v režimu ladění.

      * Ujistěte se, že váš zdrojový soubor mapování obsahuje odkaz na *./app.TSX* a ne *Webpack:///./app.TSX*, což brání ladicímu programu sady Visual Studio v umístění *App. TSX*.
       Případně, pokud potřebujete přerušit kód v souboru *App. TSX* a nemůžete to provést, zkuste použít příkaz `debugger;` v *App. TSX*nebo nastavit zarážky v sadě Chrome vývojářské nástroje (nebo v nástrojích F12 pro Microsoft Edge) místo toho.

   * Pokud potřebujete přerušit kód v souboru *App-Bundle. js* a nemůžete ho provést, odeberte zdrojový soubor mapování *App-Bundle. js. map*.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do služby App Service pro Linux](../javascript/publish-nodejs-app-azure.md)
