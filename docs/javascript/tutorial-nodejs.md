---
title: Vytvoření aplikace Node. js a Express
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
ms.openlocfilehash: ecc14e4dc98caa17ac3849e9231ab17491f2acc8
ms.sourcegitcommit: 2f64b3b231900018fceafb72b5a1c65140213a18
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73428782"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Kurz: Vytvoření aplikace v Node. js a Express v aplikaci Visual Studio

V tomto kurzu pro vývoj sady Visual Studio pomocí Node. js a Express vytvoříte jednoduchou webovou aplikaci Node. js, přidáte nějaký kód, prozkoumáte některé funkce rozhraní IDE a spustíte aplikaci. 

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvořit projekt Node.js
> * Přidat kód
> * Použití IntelliSense k úpravám kódu
> * Spuštění aplikace
> * Volání zarážky v ladicím programu

## <a name="before-you-begin"></a>Před zahájením

Tady je stručné Nejčastější dotazy, které vám povedou k předvedeným klíčovým konceptům.

### <a name="what-is-nodejs"></a>Co je Node. js?

Node. js je běhové prostředí JavaScriptu na straně serveru, které spouští JavaScript na straně serveru.

### <a name="what-is-npm"></a>Co je npm?

NPM je výchozí správce balíčků pro Node. js. Správce balíčků usnadňuje programátorům publikování a sdílení zdrojového kódu knihoven Node. js a je navržen pro zjednodušení instalace, aktualizace a odinstalace knihoven.

### <a name="what-is-express"></a>Co je Express?

Express je rozhraní webové aplikace, které se používá jako serverová architektura pro Node. js k vytváření webových aplikací. Express umožňuje použít pro vytvoření uživatelského rozhraní, jako je například Pug (dříve označované jako Jade), možnost zvolit různé prostředí front-endu. V tomto kurzu se používá Pug.

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

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

    Tento kurz byl testován pomocí 8.10.0 Node. js.

## <a name="create-a-new-nodejs-project"></a>Vytvoří nový projekt Node. js.

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

V tomto kurzu začnete s jednoduchým projektem obsahujícím kód pro Node. js a aplikaci Express.

1. Otevřít Visual Studio.

1. Vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **Node. js**a pak zvolte **vytvořit novou základní aplikaci Azure Node. js Express 4** (JavaScript). V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **JavaScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **základní aplikace Node. js Express 4**a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte základní šablonu projektu **aplikace Node. js Express 4 v Azure** , musíte přidat úlohu **vývoje Node. js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně. Otevře se soubor projektu *App. js* v editoru (levé podokno).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) zvýrazněná **tučně** je váš projekt pomocí názvu, který jste zadali v dialogovém okně **Nový projekt** . V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **Vlastnosti**. Můžete provést operaci round-trip s jinými nástroji pro vývoj, protože soubor projektu neprovádí vlastní změny ve zdroji projektu Node. js.

    (2) na nejvyšší úrovni je řešení, které ve výchozím nastavení má stejný název jako projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) uzel npm zobrazuje všechny nainstalované balíčky npm. Kliknutím pravým tlačítkem myši na uzel npm můžete vyhledat a nainstalovat balíčky npm pomocí dialogového okna nebo nainstalovat a aktualizovat balíčky pomocí nastavení v balíčku npm. *JSON* a kliknutím pravým tlačítkem myši na možnosti v uzlu.

    (4) *Package. JSON* je soubor, který npm používá ke správě závislostí balíčků a verzí balíčků pro místně instalované balíčky. Další informace o tomto souboru najdete v tématu [Konfigurace Package. JSON.](../javascript/configure-packages-with-package-json.md)

    (5) soubory projektu, jako je *App. js* , se zobrazí pod uzlem projektu. *App. js* je spouštěcí soubor projektu a je to proto, proč se zobrazuje **tučně**. Spouštěcí soubor můžete nastavit tak, že kliknete pravým tlačítkem na soubor v projektu a vyberete **nastavit jako spouštěcí soubor Node. js**.

1. Otevřete uzel **npm** a ujistěte se, že jsou k dispozici všechny požadované balíčky npm.

    Pokud všechny balíčky, které chybí (ikona vykřičník), kliknete pravým tlačítkem **npm** uzlu a zvolte **instalovat chybějící balíčky npm**.

## <a name="add-some-code"></a>Přidat kód

Aplikace používá Pug pro front-end JavaScript Framework. Pug používá jednoduchý kód, který se zkompiluje do kódu HTML. (Pug je nastavená jako modul zobrazení v *App. js*. Kód, který nastaví modul zobrazení v *App. js* , je `app.set('view engine', 'pug');`.)

1. V Průzkumník řešení (pravé podokno) otevřete složku zobrazení a pak otevřete *index. pug*.

1. Nahraďte obsah následujícím kódem.

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

    Předchozí kód slouží k dynamickému vygenerování stránky HTML s nadpisem a uvítací zprávou. Stránka také obsahuje kód pro zobrazení obrázku, který se změní pokaždé, když stisknete tlačítko.

1. Ve složce Routes otevřete *index. js*.

1. Před voláním `router.get`přidejte následující kód:

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

    Tento kód vytvoří datový objekt, který předáte do dynamicky generované stránky HTML.

1. Nahraďte `router.get` volání funkce následujícím kódem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Předchozí kód nastaví aktuální stránku pomocí objektu Express router a vykreslí stránku, předáním názvu a datového objektu na stránku. Soubor *index. pug* je zde určen jako stránka, která se má načíst při spuštění souboru *index. js* . *index. js* je nakonfigurovaný jako výchozí trasa v kódu *App. js* (není zobrazený).

    Chcete-li předvést několik funkcí sady Visual Studio, existuje záměrné chyba v řádku kódu, který obsahuje `res.render`. Před spuštěním aplikace je potřeba chybu opravit, a to v další části.

## <a name="use-intellisense"></a>Používání technologie IntelliSense

IntelliSense je nástroj sady Visual Studio, který vám pomáhá při psaní kódu.

1. V *indexu. js*přejít na řádek kódu, který obsahuje `res.render`.

1. Umístěte kurzor za `data` řetězec, zadejte `: get` a IntelliSense zobrazí `getData` funkci definovanou dříve v kódu. Vyberte `getData`.

    ![Používání technologie IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Přidejte závorky pro volání funkce, `getData()`.

1. Odeberte čárku (`,`) před `"data"` a uvidíte zeleně zvýrazněnou syntaxi výrazu. Najeďte myší na zvýrazňování syntaxe.

    ![Zobrazit syntaktickou chybu](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Poslední řádek této zprávy oznamuje, že překladač JavaScriptu očekával čárku (`,`).

1. V dolním podokně klikněte na kartu **Seznam chyb** .

    Zobrazí se upozornění a popis spolu s názvem souboru a číslem řádku.

    ![Zobrazit seznam chyb](../javascript/media/tutorial-nodejs-error-list.png)

1. Opravte kód přidáním čárky (`,`) před `"data"`.

    Po opravě by měl řádek kódu vypadat takto: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Nastavení zarážky

Dál budete pokračovat ve spuštění aplikace s připojeným ladicím programem sady Visual Studio. Než to uděláte, musíte nastavit zarážku.

1. V souboru *index. js*klikněte na levé hřbety před následujícím řádkem kódu, abyste nastavili zarážku:

    `res.render('index', { title: 'Express', "data": getData() });`

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Vyberte cíl ladění na panelu nástrojů ladění, jako je například Microsoft Edge nebo Chrome.

    ::: moniker range=">=vs-2019"
    ![Vybrat cíl ladění](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Vybrat cíl ladění](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Pokud je v počítači k dispozici Chrome, ale nezobrazuje se jako možnost, zvolte **Procházet pomocí** v rozevíracím seznamu cíl ladění a jako výchozí cíl prohlížeče vyberte Chrome (zvolte **nastavit jako výchozí**).

1. Stisknutím klávesy **F5** (**ladění** > **Spustit ladění**) spusťte aplikaci.

    Ladicí program se zastaví na zarážce, kterou jste nastavili. Nyní můžete zkontrolovat stav aplikace.

1. Najeďte myší na `getData`, abyste viděli jeho vlastnosti v DataTip

    ![Kontrola proměnných](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Pokračujte stisknutím klávesy **F5** (**ladění** > **pokračovat**).

    Aplikace se otevře v prohlížeči.

    V okně prohlížeče se v prvním odstavci zobrazí text "Express" jako nadpis a "Vítejte v expresním".

1. Kliknutím na tlačítka zobrazíte různé obrázky.

    ![Aplikace spuštěná v prohlížeči](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Zavřete webový prohlížeč.

## <a name="optional-publish-to-azure-app-service"></a>Volitelné Publikovat do Azure App Service

1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **publikovat**.

   ![Publikování do Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Vyberte **Microsoft Azure App Service**.

    V dialogovém okně **App Service** se můžete přihlásit k účtu Azure a připojit se k existujícím předplatným Azure.

1. Podle zbývajících kroků vyberte předplatné, vyberte nebo vytvořte skupinu prostředků, zvolte nebo vytvořte plochu služby App Service a pak postupujte podle pokynů k publikování do Azure. Podrobnější pokyny najdete v tématu [publikování na webu Azure pomocí nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. V okně **výstup** se zobrazí průběh nasazování do Azure.

    Po úspěšném nasazení se vaše aplikace otevře v prohlížeči spuštěném v Azure App Service. Kliknutím na tlačítko zobrazíte obrázek.

   ![Aplikace spuštěná v Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do služby App Service pro Linux](../javascript/publish-nodejs-app-azure.md)
