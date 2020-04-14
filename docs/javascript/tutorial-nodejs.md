---
title: Vytvoření aplikace Node.js a Express
description: V tomto kurzu vytvoříte aplikaci pomocí nástrojů Node.js Tools for Visual Studio.
ms.date: 09/24/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 260bc6ff6eb2d0bfbf0b9abd19062892c358728a
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224521"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Kurz: Vytvoření aplikace Node.js a Express v sadě Visual Studio

V tomto kurzu pro vývoj sady Visual Studio pomocí Node.js a Express vytvoříte jednoduchou webovou aplikaci Node.js, přidáte nějaký kód, prozkoumáte některé funkce ide a spustíte aplikaci. 

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu Node.js
> * Přidání nějakého kódu
> * Úpravy kódu pomocí technologie IntelliSense
> * Spuštění aplikace
> * Zásah do zarážky v ladicím programu

## <a name="before-you-begin"></a>Než začnete

Zde je rychlý FAQ představit vám některé klíčové pojmy.

### <a name="what-is-nodejs"></a>Co je Node.js?

Node.js je prostředí javascriptového runtime na straně serveru, které spouští serverjavascriptový server.

### <a name="what-is-npm"></a>Co je npm?

npm je výchozí správce balíčků pro soubor Node.js. Správce balíčků usnadňuje programátorům publikovat a sdílet zdrojový kód knihoven Node.js a je navržen tak, aby zjednodušil instalaci, aktualizaci a odinstalaci knihoven.

### <a name="what-is-express"></a>Co je expresní?

Express je rozhraní webové aplikace, které se používá jako serverová architektura pro soubor Node.js k vytváření webových aplikací. Express umožňuje zvolit různé front-endové architektury pro vytvoření ui, jako je Pug (dříve nazývaný Jade). Pug se používá v tomto kurzu.

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

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro nejlepší kompatibilitu s externími architekturami a knihovnami. Soubor Node.js je vytvořen pro 32bitové a 64bitové architektury. Nástroje Node.js v sadě Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Je vyžadován pouze jeden a instalační program Node.js podporuje pouze jednu, která je nainstalována současně.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nerozpozná nainstalovaný za běhu, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný běh na stránce vlastností (po vytvoření projektu klepněte pravým tlačítkem myši na uzel projektu, zvolte **Vlastnosti**a nastavte **cestu Node.exe**). Můžete použít globální instalaci souboru Node.js nebo můžete určit cestu k místnímu interpretu v každém z projektů Node.js. 

    Tento kurz byl testován pomocí souboru Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Vytvoření nového projektu Node.js

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

V tomto kurzu začnete s jednoduchým projektem obsahujícím kód pro aplikaci Node.js a express.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** otevřete vyhledávací pole, zadejte **Node.js**a pak zvolte **Vytvořit novou základní aplikaci Azure Node.js Express 4** (JavaScript). V zobrazeném dialogovém okně zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **JavaScript**a pak zvolte **Node.js**. V prostředním podokně zvolte **Základní aplikace Azure Node.js Express 4**a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte šablonu **projektu aplikace Basic Node.js Express 4,** musíte přidat vývojové **úlohy Node.js.** Podrobné pokyny naleznete v tématu [Požadavky](#prerequisites).

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně. Soubor projektu *app.js* se otevře v editoru (v levém podokně).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) Zvýrazněný **tučným písmem** je váš projekt s použitím názvu, který jste zadali v dialogovém okně **Nový projekt.** V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **Vlastnosti**. Můžete provést round-tripping s jinými vývojovými nástroji, protože soubor projektu neprovádí vlastní změny zdroje projektu Node.js.

    (2) Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako váš projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) Uzel npm zobrazuje všechny nainstalované balíčky npm. Můžete klepnout pravým tlačítkem myši na uzel npm a vyhledat a nainstalovat balíčky npm pomocí dialogového okna nebo nainstalovat a aktualizovat balíčky pomocí nastavení v *souboru package.json* a pravým tlačítkem myši v uzlu npm.

    (4) *package.json* je soubor používaný npm ke správě závislostí balíčků a verzí balíčků pro místně nainstalované balíčky. Další informace o tomto souboru naleznete v [tématu package.json configuration](../javascript/configure-packages-with-package-json.md)

    (5) Soubory projektu, jako je *například app.js,* se zobrazí pod uzlou aplikací projektu. *app.js* je spouštěcí soubor projektu, a proto se zobrazuje **tučně**. Spouštěcí soubor můžete nastavit tak, že klepnete pravým tlačítkem myši na soubor v projektu a vyberete **možnost Nastavit jako spouštěcí soubor Node.js**.

1. Otevřete uzel **npm** a ujistěte se, že jsou k dispozici všechny požadované balíčky npm.

    Pokud nějaké balíčky chybí (ikona vykřičníku), můžete klepnout pravým tlačítkem myši na uzel **npm** a zvolit **možnost Instalovat chybějící balíčky npm**.

## <a name="add-some-code"></a>Přidání nějakého kódu

Aplikace používá Pug pro front-end JavaScript framework. Pug používá jednoduchý kód značek, který se zkompiluje do HTML. (Pug je nastaven jako modul zobrazení v *app.js*. Kód, který nastaví modul zobrazení v `app.set('view engine', 'pug');` *app.js* je .)

1. V Průzkumníku řešení (v pravém podokně) otevřete složku zobrazení a otevřete *soubor index.pug*.

1. Nahraďte obsah následujícími značkami.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    Předchozí kód se používá k dynamickému generování stránky HTML s názvem a uvítací zprávou. Stránka také obsahuje kód pro zobrazení obrázku, který se změní při každém stisknutí tlačítka.

1. Ve složce Trasy otevřete *soubor index.js*.

1. Před volání `router.get`mj.

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Tento kód vytvoří datový objekt, který předáte dynamicky generované stránce HTML.

1. Nahraďte volání `router.get` funkce následujícím kódem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Předchozí kód nastaví aktuální stránku pomocí objektu express routeru a vykreslí stránku a předává stránku název a datový objekt. Soubor *index.pug* je zde zadán jako stránka, která se má načíst při spuštění *souboru index.js.* *index.js* je nakonfigurován jako výchozí trasa v kódu *app.js* (není zobrazen).

    Chcete-li demonstrovat několik funkcí sady Visual Studio, je záměrné chyby v řádku kódu obsahující `res.render`. Musíte opravit chybu před spuštěním aplikace, což uděláte v další části.

## <a name="use-intellisense"></a>Používání technologie IntelliSense

IntelliSense je nástroj sady Visual Studio, který vám pomůže při psaní kódu.

1. V *souboru index.js*přejděte na `res.render`řádek kódu obsahující .

1. Dejte kurzor `data` za řetězec, zadejte `: get` a IntelliSense vám ukáže funkci definovanou `getData` dříve v kódu. Vyberte `getData`.

    ![Používání technologie IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Přidejte závorky, aby bylo `getData()`volání funkce .

1. Odeberte čárku`,`( `"data"` ) dříve a ve výrazu se zobrazí zelené zvýraznění syntaxe. Najeďte na zvýraznění syntaxe.

    ![Chyba syntaxe zobrazení](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Poslední řádek této zprávy informuje, že interpret jazyka JavaScript`,`očekával čárku ( ).

1. V dolním podokně klikněte na kartu **Seznam chyb.**

    Zobrazí se upozornění a popis spolu s názvem souboru a číslem řádku.

    ![Zobrazit seznam chyb](../javascript/media/tutorial-nodejs-error-list.png)

1. Opravte kód přidáním čárky`,`( `"data"`) před .

    Po opravě by měl řádek kódu vypadat takto:`res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Nastavení zarážky

Dále spustíte aplikaci s připojeným ladicím programem Visual Studia. Než to uděláte, musíte nastavit zarážku.

1. V *souboru index index.js*klepněte v levém kanálu před následujícím řádkem kódu a nastavte zarážku:

    `res.render('index', { title: 'Express', "data": getData() });`

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Vyberte cíl ladění na panelu nástrojů Ladění, například Microsoft Edge nebo Chrome.

    ::: moniker range=">=vs-2019"
    ![Vyberte cíl ladění](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Vyberte cíl ladění](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Pokud je Chrome ve vašem počítači k dispozici, ale nezobrazuje se jako možnost, zvolte **Procházet pomocí** z rozevíracího seznamu ladění cíle a vyberte Chrome jako výchozí cíl prohlížeče (zvolte **Nastavit jako výchozí**).

1. Stisknutím **klávesy F5** (**Ladění** > **počátečního ladění**) spusťte aplikaci.

    Ladicí program se pozastaví na nastavené zarážky. Teď můžete zkontrolovat stav aplikace.

1. Najeďte `getData` přes a zoněkolikáte jeho vlastnosti v tipu DataTip

    ![Kontrola proměnných](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Pokračujte stisknutím **klávesy F5** (**Ladění** > **pokračovat).**

    Aplikace se otevře v prohlížeči.

    V okně prohlížeče uvidíte "Express" jako název a "Vítejte na Express" v prvním odstavci.

1. Kliknutím na tlačítka zobrazíte různé obrázky.

    ![Aplikace spuštěná v prohlížeči](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Zavřete webový prohlížeč.

## <a name="optional-publish-to-azure-app-service"></a>(Nepovinné) Publikování do služby Azure App Service

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat**.

   ![Publikování do Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Zvolte **Microsoft Azure App Service**.

    V dialogovém okně **Služba aplikace** se můžete přihlásit ke svému účtu Azure a připojit se k existujícím předplatným Azure.

1. Podle zbývajících kroků vyberte předplatné, zvolte nebo vytvořte skupinu prostředků, zvolte nebo vytvořte rovinu služby aplikace a po zobrazení výzvy k publikování do Azure postupujte podle pokynů. Podrobnější pokyny najdete v [tématu Publikování na webu Azure pomocí nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. Okno **Výstup** zobrazuje průběh nasazování do Azure.

    Při úspěšném nasazení se vaše aplikace otevře v prohlížeči spuštěném ve službě Azure App Service. Kliknutím na tlačítko zobrazíte obrázek.

   ![Aplikace spuštěná ve službě Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Gratulujeme k dokončení tohoto výukového programu!

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do linuxové služby App Service](../javascript/publish-nodejs-app-azure.md)
