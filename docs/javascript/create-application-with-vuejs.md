---
title: Vytvoření aplikace Vue.js pomocí Node.js
description: Můžete vytvářet aplikace Node.js v sadě Visual Studio pomocí rozhraní Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: af781f5735a3539d8b0e2d098bb9252bc60193fc
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180264"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Vytvoření aplikace Vue.js pomocí Node.js Tools for Visual Studio

Visual Studio podporuje vývoj aplikací s architekturou [Vue. js](https://vuejs.org/) buď v JavaScriptu, nebo v TypeScript.

Následující nové funkce podporují Vue.js vývoj aplikací v sadě Visual Studio:

* Podpora pro bloky skriptu, stylu a šablon v *.vue* soubory
* Rozpoznávání `lang` atribut na *.vue* soubory
* Šablony projektů a souborů VUE.js

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou verzi sady Visual Studio 2017 verze 15,8 nebo novější a úlohu **vývoje Node. js** .

    > [!IMPORTANT]
    > Tento článek vyžaduje funkce, které jsou k dispozici pouze počínaje verzí Visual Studio 2017 verze 15,8.

    ::: moniker range=">=vs-2019"
    Pokud požadovaná verze ještě není nainstalovaná, nainstalujte [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

* Chcete-li vytvořit projekt ASP.NET Core, musí mít technologie ASP.NET a web development a instalaci úlohy vývoj pro různé platformy .NET Core.

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nainstalovaný modul runtime nemůže zjistit, můžete nakonfigurovat tak, aby odkazovaly nainstalovaný modul runtime na stránce vlastností projektu. (Po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **vlastnosti**).

## <a name="create-a-vuejs-project-using-a-template"></a>Vytvoření projektu Vue.js pomocí šablony

Nové šablony Vue.js slouží k vytvoření nového projektu. Použití šablony je nejjednodušší způsob, jak začít pracovat. Podrobné pokyny najdete v článku [použijte sadu Visual Studio k vytvoření první aplikace pro Vue.js](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Vytvoření projektu Vue.js s ASP.NET Core a rozhraní příkazového řádku Vue

VUE.js poskytuje oficiální příkazového řádku pro rychle projekty generování uživatelského rozhraní. Pokud chcete používat rozhraní příkazového řádku k vytvoření aplikace, postupujte podle kroků v tomto článku nastavte vývojové prostředí.

> [!IMPORTANT]
> Tento postup předpokládá, že už máte nějaké zkušenosti s Vue.js framework. Pokud ne, navštivte prosím [Vue.js](https://vuejs.org/) získat další informace o rozhraní.

### <a name="create-a-new-aspnet-core-project"></a>Vytvořte nový projekt ASP.NET Core

V tomto příkladu použijete prázdnou aplikaci ASP.NET Core (jazyk C#). Ale můžete zvolit z různých projektů a programovacích jazyků.

#### <a name="create-an-empty-project"></a>Vytvořit prázdný projekt

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **ASP.NET**a pak zvolte **vytvořit novou ASP.NET Core webovou aplikaci**. V dialogovém okně, které se zobrazí, zadejte název **klient-aplikace**a pak zvolte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **Visual C#** a pak zvolte možnost **Web**. V prostředním podokně vyberte **ASP.NET Core webová aplikace**, zadejte název **klient-aplikace**a klikněte na **tlačítko OK**.
    ::: moniker-end

    Pokud se nezobrazí **webové aplikace ASP.NET Core** šablony projektu, je nutné nainstalovat **vývoj pro ASP.NET a web** pracovního vytížení a. **.NET Core** úlohy pro vývoj první. K instalaci workload(s), klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno (vyberte **souboru**  >  **Nové** > **projektu**). Spustí se instalační program pro Visual Studio. Vyberte požadované úlohy.

1. Vyberte **prázdný**a potom klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt, který se otevře v okně Průzkumník řešení (pravé podokno).

#### <a name="configure-the-project-startup-file"></a>Konfigurace spouštěcího souboru projektu

* Otevřete soubor *./Startup.cs*a přidejte následující řádky do metody konfigurace:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Nainstalujte vue rozhraní příkazového řádku

Chcete-li nainstalovat modul npm vue rozhraní příkazového řádku, otevřete příkazový řádek a zadejte `npm install --g vue-cli` nebo `npm install -g @vue/cli` pro verzi 3.0 (aktuálně ve verzi beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Vygenerované uživatelské rozhraní pomocí rozhraní příkazového řádku vue novou klientskou aplikaci

1. Přejděte na příkazovém řádku a přejděte do kořenové složky projektu.

1. Typ `vue init webpack client-app` a postupujte podle kroků po zobrazení výzvy na další otázky.

    > [!NOTE]
    > Pro soubory *. Vue* je nutné použít k převodu rozhraní Webpack nebo podobnou architekturu pro zavaděč. TypeScript a Visual Studio neznají, jak zkompilovat soubory *. Vue* . Totéž platí pro sdružování; TypeScript neobsahuje informace o tom, jak převést ES2015 moduly (tj. příkazy `import` a `export`) do jediného finálního souboru *. js* , který se načte v prohlížeči. V tuto akci je teď nejlepší volbou možnost Webpack. Chcete-li tento proces řídit v rámci sady Visual Studio pomocí nástroje MSBuild, je nutné začít od šablony sady Visual Studio. V současné době není k dispozici žádná šablona ASP.NET pro vývoj v Vue. js.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Upravit konfiguraci webpacku pro výstupní soubory sestavení do wwwroot

* Otevřete soubor *./Client-App/config/index.js*a změňte `build.index` a `build.assetsRoot` na cestu wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Označení projektu pro sestavení klientské aplikace pokaždé, když se spustí sestavení

1. V sadě Visual Studio, přejděte na **projektu** > **vlastnosti** > **události sestavení**.

1. Na **příkazový řádek události před sestavením**, typ `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurovat webpacku na výstup modulu názvy

* Otevřete soubor *./Client-App/Build/Webpack.Base.conf.js*a do vlastnosti Output přidejte následující vlastnosti:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Přidání podpory TypeScript pomocí rozhraní příkazového řádku Vue

Tyto kroky vyžadují vue – rozhraní příkazového řádku 3.0, která je aktuálně ve verzi beta.

1. Přejděte na příkazovém řádku a změňte aktuální adresář ke kořenové složce projektu.

1. Typ `vue create client-app`a klikněte na tlačítko **ručně vybrat funkce**.

1. Zvolte **Typescript**a pak vyberte další požadované možnosti.

1. Postupujte podle pokynů a odpovědět na otázky.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurace projektu Vue.js pro TypeScript

1. Otevřete soubor *./Client-App/tsconfig.JSON* a přidejte `noEmit:true` k možnostem kompilátoru.

    Nastavením této možnosti byste se vyhnout, nebudou zbytečně zabírat váš projekt pokaždé, když sestavení v sadě Visual Studio.

1. Dále vytvořte soubor *Vue. config. js* v souboru *./Client-App/* a přidejte následující kód.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Předchozí kód konfiguruje webpacku a nastaví složku wwwroot.

#### <a name="build-with-vue-cli-30"></a>Sestavení s vue – rozhraní příkazového řádku 3.0

Neznámý problém s Vue-CLI 3,0 může zabránit automatizaci procesu sestavení. Pokaždé, když se pokusíte aktualizovat složku Wwwroot, musíte spustit příkaz `npm run build` ve složce klient-aplikace.

Alternativně můžete vytvořit projekt Vue-CLI 3,0 jako událost před sestavením pomocí vlastností projektu ASP.NET. Klikněte pravým tlačítkem myši na projekt, vyberte možnost **vlastnosti**a na kartě **sestavení** přidejte následující příkazy do textového pole **příkazový řádek události před sestavením** .

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Omezení

* `lang` Atribut se podporuje jenom jazyky JavaScript a TypeScript. Přípustné hodnoty jsou: js, jsx, ts a tsx.
* `lang` atribut nefunguje s šablonu nebo styl značky.
* Ladění skriptů blokuje *.vue* soubory nejsou podporovány díky jejich povaze předzpracovaná.
* Nerozpozná TypeScript *.vue* soubory jako moduly. Budete potřebovat soubor, který obsahuje například následující TypeScript říct, co kód *.vue* soubory vypadat (vue – rozhraní příkazového řádku 3.0 šablona již obsahuje tento soubor).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Spuštění příkazu `npm run build` jako událost před sestavením ve vlastnostech projektu nefunguje při použití vue – rozhraní příkazového řádku 3.0.

## <a name="see-also"></a>Viz také:

- [Příručka Začínáme s Vue](https://vuejs.org/v2/guide).
- [Projekt CLI Vue](https://github.com/vuejs/vue-cli)
- [Dokumentace ke konfiguraci sady Webpack](https://webpack.js.org/configuration/).
