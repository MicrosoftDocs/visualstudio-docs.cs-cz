---
title: Vytvoření aplikace Node.js a React
description: V tomto kurzu vytvoříte aplikaci pomocí nástrojů Node.js Tools for Visual Studio.
ms.custom: mvc
ms.date: 11/01/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9203b07767d38443dbad8cc619a40971ca09f2c6
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750783"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Kurz: Vytvoření aplikace Node.js a React v sadě Visual Studio

Visual Studio umožňuje snadno vytvořit projekt Node.js a technologie IntelliSense a dalších integrované funkce, které podporují Node.js. V tomto kurzu pro Visual Studio vytvoříte projekt webové aplikace Node.js ze šablony sady Visual Studio. Pak vytvoříte jednoduchou aplikaci pomocí Reactu.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvořit projekt Node.js
> * Přidat balíčky npm
> * Přidat do aplikace kód React
> * Transpilovat JSX
> * Připojit ladicí program

## <a name="before-you-begin"></a>Než začnete

Tady je rychlý – nejčastější dotazy vám představí některé klíčové koncepty.

### <a name="what-is-nodejs"></a>Co je Node.js?

Node.js je prostředí runtime jazyka JavaScript na straně serveru, který se spustí JavaScript na straně serveru.

### <a name="what-is-npm"></a>Co je npm?

npm je výchozí Správce balíčků pro na Node.js. Správce balíčků usnadňuje práci programátorům k publikování a sdílet zdrojový kód z knihoven Node.js a je navržené pro zjednodušení instalace, aktualizace nebo odinstalace knihoven.

### <a name="what-is-react"></a>Co je React?

React je front-endové rozhraní pro vytvoření uživatelského rozhraní.

### <a name="what-is-jsx"></a>Co je JSX?

JSX je rozšíření syntaxe jazyka JavaScript, obvykle používají k popisu prvky uživatelského rozhraní pomocí React. Kódu JSX musí být transpiled do prostého jazyka Javasript, než můžete spustit v prohlížeči.

### <a name="what-is-webpack"></a>Co je webpacku?

webpacku sady Javascriptové soubory, můžete spustit v prohlížeči. Můžete také transformovat nebo jiné prostředky a prostředky. Se často používá k určení kompilátor, jako je například Babel nebo TypeScript, transpiluje kódu JSX nebo TypeScript pro prostý jazyk JavaScript.

## <a name="prerequisites"></a>Požadavky

* Je nutné mít nainstalovanou sadu Visual Studio 2017 a úlohu Vývoj aplikací Node.js.

    Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

    Pokud je potřeba, nainstalujte úlohu, ale už máte sadu Visual Studio, vyberte **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

* Je nutné mít nainstalovaný modul runtime Node.js.

    V tomto kurzu byl testován s verzí 8.11.2.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Node.js.

1. Otevřete Visual Studio 2017.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **JavaScript** a zvolte **Node.js**. V prostředním podokně zvolte **Prázdná webová aplikace Node.js**, zadejte název **NodejsWebAppBlank** a zvolte **OK**.

     Pokud se šablona projektu **Prázdná webová aplikace Node.js** nezobrazuje, je nutné nejprve nainstalovat úlohu Vývoj aplikací Node.js.

    Visual Studio vytvoří nové řešení a otevře příslušný projekt.

    ![Projekt Node.js v Průzkumníku řešení](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) zvýrazněno **tučné** je váš projekt, pomocí názvu, který jste zadali v **nový projekt** dialogové okno. V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **Vlastnosti**. Verzemi s jinými nástroji pro vývoj, můžete provést, protože soubor projektu není provádět vlastní změny zdroje projektu Node.js.

    (2) na nejvyšší úrovni je řešení, která ve výchozím nastavení má stejný název jako projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) npm uzlu se zobrazuje všechny balíčky npm nainstalované. Kliknete pravým tlačítkem na uzel npm, který se má vyhledat a nainstalovat balíčky npm pomocí dialogové okno nebo instalace a aktualizace balíčků pomocí nastavení v *package.json* a klikněte pravým tlačítkem na možnosti v uzlu npm.

    (4) *package.json* je soubor používaný npm Spravovat závislosti balíčků a verze balíčku pro místně nainstalované balíčky. Další informace v tomto souboru najdete v tématu [konfigurační soubor package.json](../javascript/configure-packages-with-package-json.md)

    (5) soubory projektu, jako *server.js* zobrazí pod uzlem projektu. *Server.js* je spouštěcí soubor projektu a, který je proč zobrazí v **tučné**. Můžete nastavit spouštěcí soubor tak, že kliknete pravým tlačítkem soubor v projektu a vyberete **nastavit jako spouštěcí soubor Node.js**.

## <a name="add-npm-packages"></a>Přidání balíčků npm

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

1. V **nainstalovat nové balíčky npm** dialogové okno, vyhledejte balíček react a vyberte **instalovat balíček** k její instalaci.

    ![Instalace balíčků npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Vyberte **výstup** okna pro instalaci balíčku naleznete v průběhu (vyberte **Npm** v **zobrazit výstup z:** pole). Po dokončení instalace se tento balíček zobrazí pod uzlem **npm**.

    Soubor *package.json* tohoto projektu se aktualizuje informacemi o novém balíčku, včetně verze tohoto balíčku.

1. Namísto použití uživatelského rozhraní k vyhledat a přidat zbývající balíčky jeden po druhém, vložte následující kód do *package.json*. Chcete-li to provést, přidejte `dependencies` oddílu s tímto kódem:

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

    Pokud už existuje `dependencies` oddílu ve vaší verzi i prázdnou šablonu, stačí ji nahradit předchozí kód JSON. Další informace o použití tohoto souboru najdete v tématu [konfigurační soubor package.json](../javascript/configure-packages-with-package-json.md)

1. Klikněte pravým tlačítkem na **npm** uzlu ve vašem projektu a zvolte **aktualizovat balíčky npm**.

    V dolním podokně, vyberte **výstup** okna pro instalaci balíčků naleznete v průběhu. Instalace může trvat několik minut a nemusí ihned sledujte výsledky. Pokud chcete zobrazit výstup, ujistěte se, že vyberete **Npm** v **zobrazit výstup z:** pole v **výstup** okno.

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

1. V **přidat novou položku** dialogového okna zvolte **soubor TypeScript JSX**, zadejte název *app.tsx*a vyberte **OK**.

1. Opakováním tohoto postupu přidejte *webpack config.js*. Místo soubor TypeScript JSX, zvolte **soubor JavaScript**.

1. Opakováním stejného postupu do projektu přidejte *index.html*. Místo souboru JavaScript zvolte **Soubor HTML**.

1. Opakováním stejného postupu do projektu přidejte *tsconfig.json*. Místo souboru JavaScript zvolte **Konfigurační soubor JSON pro TypeScript**.

## <a name="add-app-code"></a>Přidání kódu aplikace

1. Otevřít *server.js* a nahraďte existující kód následujícím kódem:

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

    Kód pro konfiguraci webpacku určuje, že k transpilaci JSX se má použít zavaděč TypeScriptu.

1. Otevřít *tsconfig.json* a nahraďte kód následujícím kódem, který určuje možnosti kompilátoru TypeScript:

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

    Pokud se místo uvedeného výstupu zobrazují nějaké chyby, je potřeba je před použitím aplikace odstranit. Příčinou těchto chyb může být skutečnost, že se vaše verze balíčků npm liší od verzí používaných v tomto kurzu. Jednou možností, jak chyby odstranit, je použití přesně těch verzí, které jsou uvedené v dřívějším postupu. Pokud jsou některé z těchto verzí balíčků zastaralé a způsobují chyby, může být k odstranění chyb potřeba nainstalovat novější verze. Informace o používání *package.json* řízení verze balíčku npm, naleznete v tématu [konfigurační soubor package.json](../javascript/configure-packages-with-package-json.md).

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel projektu a zvolte **přidat** > **existující složku**, klikněte na tlačítko *dist* složky a vyberte  **Vyberte složku**.

    Visual Studio přidá do projektu složku *dist*, která obsahuje *app-bundle.js* a *app-bundle.js.map*.

1. Otevřete *app-bundle.js* a zobrazte transpilovaný kód jazyka JavaScript.

1. Pokud se zobrazí výzva k opětovnému načtení externě změněné soubory, vyberte **Ano všem**.

    ![Načtení změněných souborů](../javascript/media/tutorial-nodejs-react-reload-files.png)

Vždycky, když provedete změny v *app.tsx*, je nutné znovu spustit příkaz webpack.

## <a name="run-the-app"></a>Spuštění aplikace

1. Jako aktuální cíl ladění vyberte Chrome.

    ![Výběr Chromu jako cíle ladění](../javascript/media/tutorial-nodejs-react-debug-target.png)

    Pokud je k dispozici na svém počítači Chrome, ale nezobrazí jako možnost, zvolte **procházet s** z rozevíracího seznamu cíl ladění a jako cíl výchozí prohlížeč vybrat Chrome (zvolte **nastavit jako výchozí**).

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

1. Pokud chcete použít nástroje Chrome Developer Tools, stiskněte **F12**. Pomocí těchto nástrojů můžete prozkoumat model DOM a provádět interakce s aplikací pomocí konzoly jazyka JavaScript.

1. Zavřete webový prohlížeč a konzolu.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Nastavení a použití zarážky v kódu React na straně klienta

V předchozí části jste připojili ladicí program ke kódu Node.js na straně serveru. K připojení ladicího programu ze sady Visual Studio a používání zarážek v kódu React na straně klienta se v ladicím programu vyžaduje pomoc s identifikací správného procesu. Tady je jedna možnost, jak to udělat.

1. Zavřete všechna okna Chromu.

2. Otevřete příkaz **Spustit** z tlačítka Windows **Start** (klikněte na něj pravým tlačítkem a zvolte **Spustit**) a zadejte následující příkaz:

    `chrome.exe --remote-debugging-port=9222`

    Spustí se Chrome s povoleným laděním.

3. Přepněte do sady Visual Studio a nastavte zarážku v kódu *app-bundle.js* na funkci `render()`, jak je znázorněno na následujícím obrázku:

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Najít `render()` fungovat v *aplikace bundle.js*, použijte **Ctrl**+**F** (**upravit**  >   **Najít a nahradit** > **rychle najít**).

4. Jako cíl ladění je v sadě Visual Studio vybraný Chrome. Stisknutím **Ctrl**+**F5** (**Ladit** > **Spustit bez ladění**) spusťte aplikaci v prohlížeči.

    Aplikace se otevře na nové kartě prohlížeče.

5. Zvolte **Ladit** > **Připojit k procesu**.

6. V dialogovém okně **Připojit k procesu** v poli **Připojit k** zvolte **Webkit kód** a zadáním slova **chrome** do pole pro filtr vyfiltrujte výsledky hledání.

7. Vyberte zpracování Chrome pomocí správného hostitele, portu (1337 v tomto příkladu) a vyberte **připojit**.

    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Pokud se v sadě Visual Studio otevřely Průzkumník modelu DOM a konzola jazyka JavaScript, je ladicí program správně připojený. Tyto ladicí nástroje se podobají nástrojům Chrome Developer Tools a nástrojům F12 pro Edge.

    > [!NOTE]
    > Pokud se ladicí program nepřipojí a zobrazí se zpráva „Nelze připojit k procesu. Operace není v aktuálním stavu platná“, zavřete před spuštěním Chromu v režimu ladění všechny instance Chromu pomocí Správce úloh. Můžou být spuštěná rozšíření Chromu, která brání plnému režimu ladění.

8. Kód se zarážkou se už spustil, a proto aktualizujte stránku prohlížeče, aby narazil na zarážku.

    Při pozastavení můžete v ladicím programu zkontrolovat stav aplikace tak, že přesunete ukazatel myši nad proměnné a použijete okna ladicího programu. Můžete v ladicím programu procházet kód pomocí krokování (**F5**, **F10** a **F11**).

    V závislosti na vašem prostředí a stavu prohlížeče můžete narazit na zarážku v souboru *app-bundle.js* nebo v jeho namapovaném umístění v souboru *app.tsx*. V obou případech můžete procházet kód pomocí krokování a zkoumat proměnné.

   * Pokud potřebujete proniknout do kódu v *app.tsx* a nedaří se vám to, připojte ladicí program pomocí dialogového okna **Připojit k procesu**, jak bylo popsáno v předchozím postupu. Pak otevřete dynamicky generované *app.tsx* souboru z Průzkumníku řešení otevřete **dokumenty skriptu** > **app.tsx**, nastavte zarážku a aktualizovat na stránce v prohlížeči (nastavit zarážku do řádku kódu, který umožňuje zarážky, jako například `return` příkazu nebo `var` prohlášení).

       Když potřebujete proniknout do kódu v *app.tsx* a nedaří se vám to, můžete také zkusit použít příkaz `debugger;` v *app.tsx* nebo nastavit zarážky v nástrojích Chrome Developer Tools.

   * Pokud potřebujete proniknout do kódu v *app-bundle.js* a nedaří se vám to, odeberte soubor zdrojového mapování *app-bundle.js.map*.

     > [!TIP]
     > Po prvním připojení k procesu podle tohoto postupu se v sadě Visual Studio 2017 můžete rychle znovu připojit ke stejnému procesu tak, že zvolíte **Ladit** > **Znovu připojit k procesu**.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do služby App Service pro Linux](../javascript/publish-nodejs-app-azure.md)