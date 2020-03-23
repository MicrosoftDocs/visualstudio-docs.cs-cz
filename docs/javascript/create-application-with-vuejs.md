---
title: Vytvoření aplikace Vue.js pomocí souboru Node.js
description: Aplikace Node.js můžete vytvořit v sadě Visual Studio pomocí rozhraní Vue.js
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "70180264"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Vytvoření aplikace Vue.js pomocí nástrojů Node.js pro visual studio

Visual Studio podporuje vývoj aplikací s rámcem [Vue.js](https://vuejs.org/) v jazyce JavaScript nebo TypeScript.

Následující nové funkce podporují vývoj aplikací Vue.js v sadě Visual Studio:

* Podpora bloků Skript, Styl a Šablona v souborech *.vue*
* Rozpoznávání atributu na `lang` souborech *.vue*
* Šablony projektů a souborů Vue.js

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou visual studio 2017 verze 15.8 nebo novější verzi a vývojové úlohy **Node.js.**

    > [!IMPORTANT]
    > Tento článek vyžaduje funkce, které jsou k dispozici pouze od visual studia 2017 verze 15.8.

    ::: moniker range=">=vs-2019"
    Pokud požadovaná verze ještě není nainstalovaná, nainstalujte [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)a nainstalujte ji zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

* Chcete-li vytvořit ASP.NET základní projekt, musíte mít nainstalovanou ASP.NET a vývoj webových aplikací a .NET Core vývojové úlohy napříč platformami.

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nerozpozná nainstalovaný za běhu, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný běh na stránce vlastností. (Po vytvoření projektu klepněte pravým tlačítkem myši na uzel projektu a zvolte **vlastnosti).**

## <a name="create-a-vuejs-project-using-a-template"></a>Vytvoření projektu Vue.js pomocí šablony

Nové šablony Vue.js můžete použít k vytvoření nového projektu. Použití šablony je nejjednodušší způsob, jak začít. Podrobné kroky najdete [v tématu Vytvoření první aplikace Vue.js pomocí Sady Visual Studio](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Vytvoření projektu Vue.js s ASP.NET core a Vue CLI

Vue.js poskytuje oficiální CLI pro rychle lešení projektů. Pokud chcete použít vykreslování po ruce k vytvoření aplikace, postupujte podle kroků v tomto článku nastavit vývojové prostředí.

> [!IMPORTANT]
> Tyto kroky předpokládají, že již máte nějaké zkušenosti s rozhraním Vue.js. Pokud ne, navštivte [Vue.js](https://vuejs.org/) se dozvědět více o rámci.

### <a name="create-a-new-aspnet-core-project"></a>Vytvoření nového projektu ASP.NET Core

V tomto příkladu použijete prázdnou ASP.NET základní aplikace (C#). Můžete si však vybrat z různých projektů a programovacích jazyků.

#### <a name="create-an-empty-project"></a>Vytvoření prázdného projektu

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** chcete-li otevřít vyhledávací pole, zadejte **asp.net**a pak zvolte Vytvořit novou ASP.NET **základní webovou aplikaci**. V zobrazeném dialogovém okně zadejte název **klient-app**a pak zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **položku Visual C#** a pak zvolte **Web**. V prostředním podokně zvolte **ASP.NET Core Web Application**, zadejte název **klient-app**a pak zvolte **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **ASP.NET core webová aplikace,** je nutné nainstalovat **ASP.NET a zatížení vývoje webu** a . **NET Základní** vývojové zatížení jako první. Chcete-li nainstalovat úlohy, klepněte na odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt** (vyberte **Soubor** > **nový** > **projekt).** Spustí se instalační program pro Visual Studio. Vyberte požadované úlohy.

1. Vyberte **Prázdné**a klepněte na tlačítko **OK**.

    Visual Studio vytvoří projekt, který se otevře v Průzkumníku řešení (pravé podokno).

#### <a name="configure-the-project-startup-file"></a>Konfigurace spouštěcího souboru projektu

* Otevřete soubor *./Startup.cs*a do metody Configure přidejte následující řádky:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Instalace vue CLI

Chcete-li nainstalovat modul vue-cli npm, `npm install --g vue-cli` otevřete příkazový řádek a zadejte nebo `npm install -g @vue/cli` pro verzi 3.0 (aktuálně v beta verzi).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Lešení nové klientské aplikace pomocí vue CLI

1. Přejděte do příkazového řádku a změňte aktuální adresář do kořenové složky projektu.

1. Po `vue init webpack client-app` zobrazení výzvy k zodpovězení dalších otázek zadejte a postupujte podle pokynů.

    > [!NOTE]
    > Pro *soubory .vue* je třeba použít WebPack nebo podobný rámec s zavaděčem k převodu. Skripty TypeScript a sady Visual Studio neznají způsob kompilace souborů *VUE.* Totéž platí pro svazování; TypeScript neví, jak převést moduly ES2015 `import` (tj. a `export` příkazy) do jednoho konečného souboru *JS,* který se načte v prohlížeči. Opět platí, že WebPack je nejlepší volbou zde. Chcete-li řídit tento proces z v rámci sady Visual Studio pomocí MSBuild, je třeba spustit ze šablony sady Visual Studio. V současné době neexistuje žádná šablona ASP.NET pro vývoj vue.js in-the-box.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Úprava konfigurace webového balíčku pro výstup vytvořených souborů do wwwroot

* Otevřete soubor *./client-app/config/index.js*a `build.index` `build.assetsRoot` změňte cestu a wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Označte projekt pro sestavení klientské aplikace při každém spuštění sestavení

1. V sadě Visual Studio přejděte na**události sestavení sestavení vlastností****Properties** >  **projektu** > .

1. Na **příkazovém řádku události Před sestavením**zadejte `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurace názvů výstupních modulů webového balíčku

* Otevřete soubor *./client-app/build/webpack.base.conf.js*a přidejte do výstupní vlastnosti následující vlastnosti:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Přidání podpory jazyka TypeScript pomocí příkazového příkazu Vue

Tyto kroky vyžadují vue-cli 3.0, který je v současné době v beta verzi.

1. Přejděte do příkazového řádku a změňte aktuální adresář do kořenové složky projektu.

1. Zadejte `vue create client-app`a pak zvolte **Ručně vybrat funkce**.

1. Zvolte **Typescript**a pak vyberte další požadované volby.

1. Postupujte podle zbývajících kroků a odpovězte na otázky.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurace projektu Vue.js pro typescript

1. Otevřete soubor *./client-app/tsconfig.json* a přidejte `noEmit:true` do možností kompilátoru.

    Nastavením této možnosti se vyhnete zahlcení projektu při každém sestavení v sadě Visual Studio.

1. Dále vytvořte soubor *vue.config.js* v *./client-app/* a přidejte následující kód.

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

    Předchozí kód konfiguruje webpack a nastaví složku wwwroot.

#### <a name="build-with-vue-cli-30"></a>Sestavení s vue-cli 3.0

Neznámý problém s vue-cli 3.0 může zabránit automatizaci procesu sestavení. Pokaždé, když se pokusíte aktualizovat složku wwwroot, `npm run build` je třeba spustit příkaz ve složce klient-app.

Případně můžete vytvořit projekt vue-cli 3.0 jako událost předběžného sestavení pomocí vlastností ASP.NET projektu. Klepněte pravým tlačítkem myši na projekt, zvolte **Build** **Vlastnosti**a do textového pole **příkazového řádku události Před sestavením** zahrňte následující příkazy.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Omezení

* `lang`atribut podporuje pouze jazyky JavaScript a TypeScript. Přijaté hodnoty jsou: js, jsx, ts a tsx.
* `lang`atribut nefunguje se značkami šablony nebo stylu.
* Ladění bloků skriptů v souborech *.vue* není podporováno z důvodu jeho předzpracované povahy.
* Skript TypeScript nerozpozná soubory *.vue* jako moduly. Potřebujete soubor, který obsahuje například následující, abyste sdělili TypeScript, jak vypadají soubory *.vue* (šablona vue-cli 3.0 již tento soubor obsahuje).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Spuštění příkazu `npm run build` jako události předběžného sestavení ve vlastnostech projektu nefunguje při použití vue-cli 3.0.

## <a name="see-also"></a>Viz také

- [Vue začít průvodce](https://vuejs.org/v2/guide).
- [Projekt Vue CLI](https://github.com/vuejs/vue-cli).
- [Dokumentace ke konfiguraci webového balíčku](https://webpack.js.org/configuration/).
