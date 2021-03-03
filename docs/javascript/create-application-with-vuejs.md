---
title: Vytvoření aplikace Vue.js pomocí Node.js
description: V aplikaci Visual Studio můžete vytvářet Node.js aplikace pomocí rozhraní Vue.js Framework
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 338e53d576e9f4d73b32c3f432223480d9e708c3
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683932"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Vytvoření aplikace Vue.js pomocí nástrojů Node.js pro Visual Studio

Visual Studio podporuje vývoj aplikací pomocí [Vue.jsho ](https://vuejs.org/) rozhraní v JavaScriptu nebo TypeScript.

Následující nové funkce podporují Vue.js vývoj aplikací v aplikaci Visual Studio:

* Podpora pro bloky Script, Style a Template v souborech *. Vue*
* Rozpoznávání `lang` atributů u souborů *. Vue*
* Vue.js šablon projektů a souborů

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou verzi sady Visual Studio 2017 verze 15,8 nebo novější a **Node.js vývojové** úlohy.

    > [!IMPORTANT]
    > Tento článek vyžaduje funkce, které jsou k dispozici pouze počínaje verzí Visual Studio 2017 verze 15,8.

    ::: moniker range=">=vs-2019"
    Pokud požadovaná verze ještě není nainstalovaná, nainstalujte [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

* Pokud chcete vytvořit ASP.NET Core projekt, musíte mít nainstalované úlohy vývoje pro vývoj pro ASP.NET a web a .NET Core pro více platforem.

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nezjistí nainstalovaný modul runtime, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný modul runtime na stránce Vlastnosti. (Po vytvoření projektu klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**).

## <a name="create-a-vuejs-project-using-nodejs"></a>Vytvoření projektu Vue.js pomocí Node.js

Nové šablony Vue.js můžete použít k vytvoření nového projektu. Použití šablony představuje nejjednodušší způsob, jak začít. Podrobný postup najdete v tématu [použití sady Visual Studio k vytvoření první aplikace Vue.js](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Vytvoření projektu Vue.js pomocí ASP.NET Core a Vue CLI

Vue.js poskytuje oficiální rozhraní příkazového řádku pro rychlé generování uživatelského rozhraní pro projekty. Pokud chcete použít rozhraní příkazového řádku k vytvoření aplikace, postupujte podle kroků v tomto článku a nastavte své vývojové prostředí.

> [!IMPORTANT]
> Tyto kroky předpokládají, že již máte zkušenosti s Vue.js Framework. Pokud ne, přečtěte si prosím [Vue.js](https://vuejs.org/) , kde najdete další informace o rozhraní.

### <a name="create-a-new-aspnet-core-project"></a>Vytvoření nového projektu ASP.NET Core

V tomto příkladu použijete prázdnou ASP.NET Core aplikaci (C#). Můžete si však vybrat z nejrůznějších projektů a programovacích jazyků.

#### <a name="create-an-empty-project"></a>Vytvořit prázdný projekt

* Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 v okně Start vyberte možnost **vytvořit nový projekt** . Pokud okno Start není otevřeno, klikněte **na tlačítko**  >  **Start okna**. Zadejte **Web App**, jako jazyk vyberte **C#** , zvolte **ASP.NET Core prázdné** a pak zvolte **Další**. Na další obrazovce pojmenujte projekt **klient-aplikace** a klikněte na tlačítko **Další**.

    Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **Visual C#** a pak zvolte možnost **Web**. V prostředním podokně vyberte **ASP.NET Core webová aplikace**, zadejte název **klient-aplikace** a klikněte na **tlačítko OK**.

    Vyberte **prázdné** a pak klikněte na **OK**.

    Visual Studio vytvoří projekt, který se otevře v Průzkumník řešení (pravé podokno).
    ::: moniker-end

    Pokud nevidíte šablonu projektu **ASP.NET Core webové aplikace** , musíte nainstalovat úlohu **vývoje ASP.NET a webu** a. Nejprve úlohu vývoje **.NET Core** . Chcete-li nainstalovat úlohy, klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** (vyberte **soubor**  >  **Nový**  >  **projekt**). Spustí se instalační program pro Visual Studio. Vyberte požadované úlohy.

#### <a name="configure-the-project-startup-file"></a>Konfigurace spouštěcího souboru projektu

* Otevřete soubor *./Startup.cs* a do metody Configure přidejte následující řádky:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Instalace rozhraní příkazového řádku Vue

Pokud chcete nainstalovat modul Vue-CLI NPM, otevřete příkazový řádek a zadejte `npm install --g vue-cli` nebo `npm install -g @vue/cli` pro verzi 3,0 (aktuálně ve verzi beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Vytvoření nové klientské aplikace pomocí rozhraní příkazového řádku (Vue)

1. Přejděte na příkazový řádek a změňte aktuální adresář na kořenovou složku projektu.

1. `vue init webpack client-app`Po zobrazení výzvy k zodpovězení dalších otázek zadejte a postupujte podle těchto kroků.

    > [!NOTE]
    > Pro soubory *. Vue* je nutné použít k převodu rozhraní Webpack nebo podobnou architekturu pro zavaděč. TypeScript a Visual Studio neznají, jak zkompilovat soubory *. Vue* . Totéž platí pro sdružování; TypeScript neobsahuje informace o tom, jak převést ES2015 moduly (to znamená `import` a `export` příkazy) do jediného finálního souboru *. js* , který se načte v prohlížeči. V tuto akci je teď nejlepší volbou možnost Webpack. Chcete-li tento proces řídit v rámci sady Visual Studio pomocí nástroje MSBuild, je nutné začít od šablony sady Visual Studio. V současné době není k dispozici žádná šablona ASP.NET pro vývoj Vue.js v rámci.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Úprava konfigurace sady Webpack pro výstup sestavených souborů na wwwroot

* Otevřete soubor *./client-app/config/index.js* a změňte `build.index` `build.assetsRoot` cestu a na Wwwroot.

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Označení projektu pro sestavení klientské aplikace pokaždé, když se spustí sestavení

1. V aplikaci Visual Studio, přejít na  >  **vlastnosti** projektu  >  **události sestavení**.

1. Do **příkazového řádku události před sestavením** zadejte `npm --prefix ./client-app run build` .

#### <a name="configure-webpacks-output-module-names"></a>Nakonfigurovat názvy výstupních modulů pro Webpack

* Otevřete soubor *./client-app/build/webpack.base.conf.js* a do vlastnosti Output přidejte následující vlastnosti:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Přidání podpory TypeScript pomocí rozhraní příkazového řádku Vue

Tyto kroky vyžadují Vue-CLI 3,0, který je aktuálně ve verzi beta.

1. Přejděte na příkazový řádek a změňte aktuální adresář na kořenovou složku projektu.

1. Zadejte `vue create client-app` a zvolte možnost **ručně vybrat funkce**.

1. Zvolte **TypeScript** a pak vyberte další požadované možnosti.

1. Postupujte podle zbývajících kroků a odpovězte na otázky.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurace projektu Vue.js pro TypeScript

1. Otevřete soubor *./client-app/tsconfig.js* a přidejte `noEmit:true` do možností kompilátoru.

    Nastavením této možnosti předejdete zbytečnému zaplnění projektu při každém sestavení v aplikaci Visual Studio.

1. Dále vytvořte soubor *vue.config.js* v souboru *./Client-App/* a přidejte následující kód.

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

    Předchozí kód nakonfiguruje Webpack a nastaví složku Wwwroot.

#### <a name="build-with-vue-cli-30"></a>Sestavení pomocí Vue-CLI 3,0

Neznámý problém s Vue-CLI 3,0 může zabránit automatizaci procesu sestavení. Pokaždé, když se pokusíte aktualizovat složku Wwwroot, musíte spustit příkaz `npm run build` ve složce klient-aplikace.

Alternativně můžete vytvořit projekt Vue-CLI 3,0 jako událost před sestavením pomocí vlastností projektu ASP.NET. Klikněte pravým tlačítkem myši na projekt, vyberte možnost **vlastnosti** a na kartě **sestavení** přidejte následující příkazy do textového pole **příkazový řádek události před sestavením** .

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Omezení

* `lang` atribut podporuje pouze jazyky JavaScript a TypeScript. Přípustné hodnoty jsou: js, JSX, TS a TSX.
* `lang` atribut nepracuje se značkami šablony nebo stylu.
* Ladění bloků skriptu v souborech *. Vue* není podporováno z důvodu jeho předzpracovaného charakteru.
* TypeScript nerozpozná soubory *. Vue* jako moduly. Potřebujete soubor, který obsahuje kód, například následující informace o tom, jak soubory TypeScript *. Vue* vypadají jako (šablona Vue-CLI 3,0 již tento soubor obsahuje).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Spuštění příkazu `npm run build` jako události před sestavením ve vlastnostech projektu nefunguje při použití Vue-cli 3,0.

## <a name="see-also"></a>Viz také

- [Příručka Začínáme s Vue](https://vuejs.org/v2/guide).
- [Projekt CLI Vue](https://github.com/vuejs/vue-cli)
- [Dokumentace ke konfiguraci sady Webpack](https://webpack.js.org/configuration/).
