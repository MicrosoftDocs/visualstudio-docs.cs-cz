---
title: Vytvoření aplikace Node.js a React
description: Naučte se, jak vytvořit projekt webové aplikace Node.js ze šablony sady Visual Studio.
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 80516adffcb058d6ce28751e7a9f30002ca3a640
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729296"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Kurz: Vytvoření aplikace Node.js a React v sadě Visual Studio

Visual Studio umožňuje snadno vytvořit Node.js projekt a vyzkoušet IntelliSense a další integrované funkce, které podporují Node.js. V tomto kurzu pro Visual Studio vytvoříte projekt webové aplikace Node.js ze šablony sady Visual Studio. Pak vytvoříte jednoduchou aplikaci pomocí Reactu.

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

Node.js je běhové prostředí JavaScriptu na straně serveru, které spouští JavaScript na straně serveru.

### <a name="what-is-npm"></a>Co je npm?

NPM je výchozí správce balíčků pro Node.js. Správce balíčků usnadňuje programátorům publikování a sdílení zdrojového kódu Node.js knihoven a je navržený tak, aby zjednodušil instalaci, aktualizaci a odinstalaci knihoven.

### <a name="what-is-react"></a>Co reaguje?

Reakce je front-endové rozhraní pro vytvoření uživatelského rozhraní.

### <a name="what-is-jsx"></a>Co je JSX?

JSX je rozšíření syntaxe JavaScriptu, které se obvykle používá s reakci na popis prvků uživatelského rozhraní. JSX kód musí být převeden na prostý JavaScript předtím, než může běžet v prohlížeči.

### <a name="what-is-webpack"></a>Co je to sada Webpack?

sada Webpack rozbalí soubory JavaScriptu tak, aby mohly běžet v prohlížeči. Může také transformovat nebo zabalit další prostředky a prostředky. Často se používá k určení kompilátoru, jako je Babel nebo TypeScript, k přeformátování JSX nebo kódu TypeScript na prostý JavaScript.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node.js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali Visual Studio 2019, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali Visual Studio 2017, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Node.js úlohy v instalačním programu sady Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Tento kurz byl testován s verzí 12.6.2.

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro zajištění nejlepší kompatibility s externími rozhraními a knihovnami. Node.js je sestavená pro 32bitovou a 64bitovou architekturu. Nástroje Node.js v Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Vyžaduje se jenom jeden z nich a Node.js podporuje jenom jednu instalaci najednou.

    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nainstalovaný modul runtime nezjistí, můžete projekt nakonfigurovat tak, aby odkazovat na nainstalovaný modul runtime na stránce vlastností (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu, zvolte Vlastnosti **(nebo** stiskněte **Klávesu Alt**  +  **Enter)** a **nastavte cestuNode.exe ).** Můžete použít globální instalaci Node.js nebo můžete zadat cestu k místnímu interpretu v každém z vašich Node.js projektů. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Node.js.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete úvodní okno. Zadejte **Ctrl + Q** a otevřete vyhledávací pole, zadejte **Node.js** a pak zvolte Blank (Prázdná) Node.js Web Application - JavaScript (Webová aplikace **– JavaScript).** (I když tento kurz používá kompilátor TypeScriptu, kroky vyžadují, aby se začalo s **šablonou JavaScriptu.)**
    
    V dialogovém okně, které se zobrazí, zvolte **Vytvořit.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **File** New Project  >  **(Soubor nového**  >  **projektu).** V levém podokně dialogového okna **Nový** projekt rozbalte **JavaScript** a pak **zvolteNode.js**. V prostředním podokně zvolte **Prázdná Node.js aplikace,** zadejte název **NodejsWebAppBlank** a pak zvolte **OK.**
    ::: moniker-end
    Pokud nevidíte šablonu projektu **Prázdná Node.js webové** aplikace, musíte přidat úlohu **Node.js vývoj.** Podrobné pokyny najdete v tématu [Požadavky.](#prerequisites)

    Visual Studio vytvoří nové řešení a otevře příslušný projekt.

    ![Projekt Node.js v Průzkumníku řešení](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Projekt  je zvýrazněný tučně s použitím názvu, který jste dali v **dialogovém okně Nový** projekt. V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **vlastnosti** (nebo stisknete klávesu **ALT**  +  **ENTER**). Můžete provést operaci round-trip s jinými nástroji pro vývoj, protože soubor projektu neprovádí vlastní změny ve zdroji projektu Node.js.

    (2) na nejvyšší úrovni je řešení, které ve výchozím nastavení má stejný název jako projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) uzel npm zobrazuje všechny nainstalované balíčky npm. Kliknutím pravým tlačítkem myši na uzel npm můžete vyhledat a nainstalovat balíčky npm pomocí dialogového okna nebo nainstalovat a aktualizovat balíčky pomocí nastavení v *package.jszapnuto* a kliknutím pravým tlačítkem myši na možnosti v uzlu npm.

    (4) *package.js* je soubor, který používá npm ke správě závislostí balíčků a verzí balíčků pro místně instalované balíčky. Další informace najdete v tématu [Správa balíčků npm](../javascript/npm-package-management.md).

    (5) soubory projektu, například *server.js* , se zobrazí pod uzlem projektu. *server.js* je spouštěcí soubor projektu a to je důvod, proč se zobrazuje **tučně**. Spouštěcí soubor můžete nastavit tak, že kliknete pravým tlačítkem na soubor v projektu a vyberete **nastavit jako Node.js spouštěcí soubor**.

## <a name="add-npm-packages"></a>Přidat balíčky npm

Tato aplikace vyžaduje ke správnému fungování řadu modulů npm.

* react
* react-dom
* express
* program
* ts-loader
* typescript
* webpack
* webpack-cli

1. V Průzkumníku řešení (pravé podokno) klikněte pravým tlačítkem na uzel **npm** v projektu a zvolte **Nainstalovat nové balíčky npm**.

    V dialogovém okně **Nainstalovat nové balíčky npm** můžete zvolit instalaci nejnovější verze balíčků nebo určit konkrétní verzi. Pokud se rozhodnete nainstalovat aktuální verzi těchto balíčků, ale později se můžete setkat s neočekávanými chybami, budete možná chtít nainstalovat přesné verze balíčku popsané dále v tomto postupu.

1. V dialogovém okně **instalovat nové balíčky npm** vyhledejte balíček s možností reakce a vyberte **nainstalovat balíček** a nainstalujte ho.

    ![Instalace balíčků npm](../javascript/media/tutorial-nodejs-react-install-package.png)

    Vyberte okno **výstup** , ve kterém se zobrazí průběh instalace balíčku (vyberte **npm** v poli **Zobrazit výstup z** ). Po dokončení instalace se tento balíček zobrazí pod uzlem **npm**.

    Soubor *package.json* tohoto projektu se aktualizuje informacemi o novém balíčku, včetně verze tohoto balíčku.

1. Místo použití uživatelského rozhraní k vyhledání a přidání zbývajících balíčků po jednom vložte následující kód do *package.js*. Uděláte to tak, že přidáte `dependencies` oddíl s tímto kódem:

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    Pokud již existuje `dependencies` část ve vaší verzi prázdné šablony, stačí ji nahradit předchozím kódem JSON. Další informace o používání tohoto souboru najdete v tématu [package.jsv konfiguraci](../javascript/configure-packages-with-package-json.md).

1. Uložte změny.

1. Klikněte pravým **tlačítkem na uzel npm** ve vašem projektu a zvolte **Nainstalovat balíčky npm**.

    Tento příkaz spustí příkaz npm install přímo.

    V dolním podokně vyberte okno **Výstup,** abyste viděli průběh instalace balíčků. Instalace může trvat několik minut a výsledky se nemusí zobrazit okamžitě. Pokud chcete zobrazit výstup, ujistěte se, že v okně Výstup v poli **Zobrazit výstup z** **vyberete** **Npm.** (Pokud chcete otevřít okno, zvolte **Zobrazit.**  >  **Výstup** nebo stiskněte **Ctrl**  +  **Alt**  +  **O**.)

    Tady jsou moduly npm, které se po instalaci zobrazí v Průzkumníku řešení.

    ![Balíčky npm](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Pokud chcete balíčky npm nainstalovat raději pomocí příkazového řádku, klikněte pravým tlačítkem na uzel projektu a zvolte **Otevřít tady příkazový řádek**. K instalaci balíčků použijte standardní příkazy Node.js.

## <a name="add-project-files"></a>Přidání souborů projektu

V tomto postupu do projektu přidáte čtyři nové soubory.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Nové soubory projektu pro tuto jednoduchou aplikaci přidáte do kořenu projektu. (U většiny aplikací se soubory obvykle přidávají do podsložek a odkazy s relativní cestou se podle toho upraví.)

1. V Průzkumník řešení klikněte pravým tlačítkem na projekt **NodejsWebAppBlank** a zvolte **Přidat**  >  **novou položku** (nebo stiskněte **Ctrl**  +  **SHIFT**  +  **A).**

1. V dialogovém **okně Přidat** novou položku zvolte Soubor **TypeScript JSX,** zadejte název *app.tsx* a vyberte **Přidat** nebo **OK**.

1. Opakováním tohoto postupu přidejte *webpack config.js*. Místo souboru JSX TypeScriptu zvolte **javascriptový soubor**.

1. Opakováním stejného postupu do projektu přidejte *index.html*. Místo souboru JavaScript zvolte **Soubor HTML**.

1. Opakováním stejného postupu do projektu přidejte *tsconfig.json*. Místo souboru JavaScript zvolte **Konfigurační soubor JSON pro TypeScript**.

## <a name="add-app-code"></a>Přidání kódu aplikace

1. Otevřete *server.js* a nahraďte existující kód následujícím kódem:

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

    Konfigurační kód webpacku instruuje webpack, aby k transpilaci JSX použít zavaděč TypeScriptu.

1. Otevřete *tsconfig.json a* nahraďte výchozí kód následujícím kódem, který určuje možnosti kompilátoru TypeScriptu:

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

    ![Spuštění webpacku](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Pokud se místo uvedeného výstupu zobrazují nějaké chyby, je potřeba je před použitím aplikace odstranit. Příčinou těchto chyb může být skutečnost, že se vaše verze balíčků npm liší od verzí používaných v tomto kurzu. Jednou možností, jak chyby odstranit, je použití přesně těch verzí, které jsou uvedené v dřívějším postupu. Pokud jsou některé z těchto verzí balíčků zastaralé a způsobují chyby, může být k odstranění chyb potřeba nainstalovat novější verze. Informace o použití nástroje *package.json* k řízení verzí balíčků npm najdete vpackage.js [ o konfiguraci](../javascript/configure-packages-with-package-json.md).

1. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu, zvolte Přidat existující složku, zvolte složku  >   *dist* a zvolte **Vybrat složku**.

    Visual Studio přidá do projektu složku *dist*, která obsahuje *app-bundle.js* a *app-bundle.js.map*.

1. Otevřete *app-bundle.js* a zobrazte transpilovaný kód jazyka JavaScript.

1. Pokud se zobrazí výzva k opětovnému načtení externě upravených souborů, **vyberte Ano všem**.

    ![Načtení změněných souborů](../javascript/media/tutorial-nodejs-react-reload-files.png)

Vždycky, když provedete změny v *app.tsx*, je nutné znovu spustit příkaz webpack. Pokud chcete tento krok automatizovat, přidejte skript sestavení pro transpilaci JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Přidání skriptu sestavení pro transpilaci JSX

Od Visual Studio 2019 se vyžaduje skript sestavení. Místo transpilace JSX na příkazovém řádku (jak je znázorněno v předchozí části) můžete při sestavování z příkazového řádku transpilovat JSX Visual Studio.

* Otevřete *package.json a* za část přidejte následující `dependencies` část:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Spuštění aplikace

1. Jako aktuální cíl ladění vyberte buď **webový server (Google Chrome)** , nebo **webový server (Microsoft Edge)** .

    ::: moniker range=">=vs-2019"
    ![Výběr Chromu jako cíle ladění](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Výběr Chromu jako cíle ladění](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Pokud je v počítači k dispozici Chrome, ale nezobrazuje se jako možnost, zvolte **Procházet pomocí** v rozevíracím seznamu cíl ladění a jako výchozí cíl prohlížeče vyberte Chrome (zvolte **nastavit jako výchozí**).

1. Ke spuštění aplikace stiskněte **F5** (**Ladit** > **Spustit ladění**) nebo tlačítko se zelenou šipkou.

    Otevře se okno konzoly Node.js, které zobrazuje port, na kterém ladicí program naslouchá.

    Visual Studio spustí danou aplikaci spuštěním spouštěcího souboru *server.js*.

    ![Spuštění Reactu v prohlížeči](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zavřete okno prohlížeče.

1. Zavřete okno konzoly.

## <a name="set-a-breakpoint-and-run-the-app"></a>Nastavení zarážky a spuštění aplikace

1. V souboru *server.js* kliknutím do mezery vedle okraje nalevo od deklarace `staticPath` nastavte zarážku:

    ![Snímek obrazovky okna Visual Studio Code pro server.js. Červená tečka na levém hřbetu indikuje, že je pro deklaraci staticPath nastavená zarážka.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

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

2. Spusťte prohlížeč s povoleným laděním.

    ::: moniker range=">=vs-2019"
    Počínaje verzí Visual Studio 2019 můžete nastavit `--remote-debugging-port=9222` příznak při spuštění prohlížeče tak, že na panelu nástrojů **ladění** kliknete na **Procházet s...** > a pak zvolíte **Přidat** a pak nastavíte příznak v poli **argumenty** . Použijte jiný popisný název prohlížeče, jako je například **Edge s laděním** nebo **Chrome s laděním**. Podrobnosti najdete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes-v16.2).

    ![Nastavte prohlížeč tak, aby se otevřel s povoleným laděním.](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternativně otevřete příkaz **Run** z tlačítka **Start** systému Windows (klikněte pravým tlačítkem myši a vyberte možnost **Spustit**) a zadejte následující příkaz:

    `msedge --remote-debugging-port=9222`

    ani

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Otevřete příkaz **Spustit** z tlačítka Windows **Start** (klikněte na něj pravým tlačítkem a zvolte **Spustit**) a zadejte následující příkaz:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Tím se spustí prohlížeč s povoleným laděním.

    Aplikace ještě není spuštěná, takže se zobrazí prázdná stránka prohlížeče.

### <a name="attach-the-debugger-to-client-side-script"></a>Připojení ladicího programu ke skriptu na straně klienta

1. Přepněte Visual Studio a nastavte zarážku ve zdrojovém kódu, a to buď *app-bundle.js,*  nebo *app.tsx*.

    Například *app-bundle.js* nastavte zarážku ve funkci , `render()` jak je znázorněno na následujícím obrázku:

    ![Snímek obrazovky s Visual Studio kódu pro app-bundle.js Červená tečka v levé okapové oblasti indikuje, že je ve funkci vykreslování nastavena zarážka.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Pokud chcete funkci `render()` najít v  transpilovanéapp-bundle.jssouboru, použijte **Ctrl** + **F** (**Rychlé** hledání a  >  **nahrazení** pro  >  úpravy).

    Pro *app.tsx* nastavte zarážku uvnitř `render()` funkce na příkaz `return` .

    ![Snímek obrazovky Visual Studio kódu pro app.tsx Červená tečka v levém okapu značí, že je u příkazu return funkce render nastavena zarážka.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Pokud nastavíte zarážku v *souboru .tsx* (app-bundle.js *),* musíte aktualizovat *webpack-config.js*. Nahraďte následující kód:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    tímto kódem:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Toto je nastavení pouze pro vývoj, které umožňuje ladění v Visual Studio. Toto nastavení umožňuje přepsat vygenerované odkazy ve zdrojovém souboru mapy *app-bundle.js.map* při sestavování aplikace. Ve výchozím nastavení obsahují odkazy webpacku ve zdrojovém souboru mapy předponu *webpack:///,* která brání Visual Studio zdrojovému souboru *app.tsx.* Konkrétně se při této změně změní odkaz na zdrojový soubor *app.tsx* *z webpack:///./app.tsx* *na ./app.tsx*, což umožňuje ladění.

3. Vyberte cílový prohlížeč jako cíl ladění v Visual Studio a potom stiskněte **Ctrl** + **F5** **(Spustit** ladění bez ladění) a spusťte aplikaci v  >  prohlížeči.

    ::: moniker range=">=vs-2019"
    Pokud jste vytvořili konfiguraci prohlížeče s popisný název, zvolte tuto možnost jako cíl ladění.
    ::: moniker-end

    Aplikace se otevře na nové kartě prohlížeče.

4. Zvolte **ladit**  >  **připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL**  +  **+**  +  **P**).

    > [!TIP]
    > Od sady Visual Studio 2017 se po prvním připojení k procesu pomocí následujícího postupu můžete rychle připojit ke stejnému procesu tak, že zvolíte možnost **ladění** znovu  >  **připojit k procesu** (nebo stiskněte klávesu **SHIFT**  +  **ALT**  +  **P**).

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

    Zarážku můžete narazit buď v *app-bundle.js* nebo v jeho mapovaném umístění v *App. TSX* v závislosti na tom, jaké kroky jste předtím použili, spolu s vaším prostředím a stavem prohlížeče. V obou případech můžete procházet kód pomocí krokování a zkoumat proměnné.

   * Pokud potřebujete proniknout do kódu v *app.tsx* a nedaří se vám to, připojte ladicí program pomocí dialogového okna **Připojit k procesu**, jak bylo popsáno v předchozím postupu. Ujistěte se, že je prostředí správně nastavené:

      * Zavřeli jste všechny instance prohlížeče, včetně rozšíření chromu (pomocí Správce úloh), abyste mohli prohlížeč spustit v režimu ladění. Ujistěte se, že prohlížeč spustíte v režimu ladění.

      * Ujistěte se, že zdrojový soubor mapy obsahuje odkaz na *./app.tsx* a ne *na webpack:///./app.tsx*, což ladicímu programu Visual Studio brání v vyhledání *souboru app.tsx.*
       Případně pokud potřebujete prolomit kód v *app.tsx* a nemůžete to udělat, zkuste místo toho použít příkaz v app.tsx nebo nastavit zarážky v Chrome `debugger;` Vývojářské nástroje (nebo F12 Tools for Microsoft Edge). 

   * Pokud potřebujete rozdělit kód  doapp-bundle.jsa nemůžete to udělat, odeberte zdrojový soubor mapy *app-bundle.js.map*.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do Linuxu App Service](../javascript/publish-nodejs-app-azure.md)
