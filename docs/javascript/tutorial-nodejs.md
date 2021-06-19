---
title: Vytvoření aplikace Node.js a Express
description: V tomto kurzu se dozvíte, jak vytvořit jednoduchou Node.js aplikace pomocí architektury webových aplikací Express v Visual Studio.
ms.date: 03/25/2021
ms.custom: vs-acquisition
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d4ea086d20f5a1000067343ac7571a9a8f8309db
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386810"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Kurz: Vytvoření aplikace Node.js a Express v Visual Studio

V tomto kurzu pro Visual Studio pomocí Node.js a Expressu vytvoříte jednoduchou webovou aplikaci Node.js, přidáte kód, prozkoumáte některé funkce integrovaného vývojového prostředí (IDE) a spustíte aplikaci. 

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio 2022 Preview, přejděte na stránku [stahování Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) a nainstalujte si ji zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvořit projekt Node.js
> * Přidání kódu
> * Použití IntelliSense k úpravě kódu
> * Spuštění aplikace
> * Přístup k zarážce v ladicím programu

## <a name="before-you-begin"></a>Než začnete

Tady je stručný přehled nejčastějších dotazů, které vás seznámí s některými klíčovými koncepty.

### <a name="what-is-nodejs"></a>Co je Node.js?

Node.js je prostředí javascriptového modulu runtime na straně serveru, které spouští JavaScript na straně serveru.

### <a name="what-is-npm"></a>Co je npm?

npm je výchozí správce balíčků pro Node.js. Správce balíčků usnadňuje programátorům publikování a sdílení zdrojového kódu knihoven Node.js a je navržený tak, aby zjednodušil instalaci, aktualizaci a odinstalaci knihoven.

### <a name="what-is-express"></a>Co je express?

Express je rozhraní webových aplikací, které se používá jako serverová Node.js k vytváření webových aplikací. Express umožňuje zvolit různé front-endové architektury pro vytvoření uživatelského rozhraní, jako je Pug (dříve Jade). V tomto kurzu se používá Pug.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou Visual Studio a Node.js vývojové úlohy.

    ::: moniker range=">=vs-2019"
    Pokud jste si ještě nenainstalujete Visual Studio 2019, přejděte na stránku [Visual Studio ke](https://visualstudio.microsoft.com/downloads/) stažení a nainstalujte si ji zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste si ještě nenainstalujete Visual Studio 2017, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.
    ::: moniker-end

    Pokud potřebujete tuto úlohu nainstalovat, ale Visual Studio, přejděte na **Nástroje** Získat nástroje a funkce. Otevře se  >  Instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Node.js úlohy v instalačním programu sady Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro zajištění nejlepší kompatibility s externími rozhraními a knihovnami. Node.js je sestavená pro 32bitovou a 64bitovou architekturu. Nástroje Node.js v Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Vyžaduje se jenom jeden z nich a Node.js podporuje jenom jednu instalaci najednou.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nainstalovaný modul runtime nezjistí, můžete projekt nakonfigurovat tak, aby odkazovat na nainstalovaný modul runtime na stránce vlastností (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu, zvolte Vlastnosti a nastavte **cestuNode.exe ).** Můžete použít globální instalaci Node.js nebo můžete zadat cestu k místnímu interpretu v každém z vašich Node.js projektů. 

    Tento kurz byl testován s Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Vytvoření nového Node.js projektu

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

V tomto kurzu začnete jednoduchým projektem obsahujícím kód pro aplikaci Node.js a express.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete úvodní okno. Zadejte **Ctrl + Q,** otevřete vyhledávací pole, zadejte **Node.js** a pak zvolte Vytvořit novou aplikaci Azure Basic Node.js **Express 4** (JavaScript). V dialogovém okně, které se zobrazí, zvolte **Vytvořit.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **File** New Project  >  **(Soubor nového**  >  **projektu).** V levém podokně dialogového okna **Nový** projekt rozbalte **JavaScript** a pak **zvolteNode.js**. V prostředním podokně zvolte **Základní Azure Node.js Express 4** a pak zvolte **OK.**
    ::: moniker-end
    Pokud nevidíte šablonu projektu základní aplikace **Azure Node.js Express 4,** musíte přidat úlohu **Node.js vývoj.** Podrobné pokyny najdete v tématu [Požadavky.](#prerequisites)

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně. Soubor *app.js* projektu se otevře v editoru (levé podokno).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) Projekt  je zvýrazněný tučně a používá název, který jste dali v **dialogovém okně Nový** projekt. V systému souborů je tento projekt reprezentovaný souborem *.njsproj* ve složce projektu. Vlastnosti a proměnné prostředí přidružené k projektu můžete nastavit tak, že kliknete pravým tlačítkem na projekt a zvolíte **Vlastnosti**. U jiných vývojových nástrojů můžete provádět přecházování zpět, protože soubor projektu neproovádá vlastní změny ve zdroji Node.js projektu.

    (2) Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako váš projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

    (3) Uzel npm zobrazuje všechny nainstalované balíčky npm. Kliknutím pravým tlačítkem na uzel npm můžete vyhledat a nainstalovat balíčky npm pomocí dialogového okna nebo nainstalovat a aktualizovat balíčky pomocí nastavení v souboru *package.json* a kliknout pravým tlačítkem na uzlu npm.

    (4) *package.json* je soubor, který npm používá ke správě závislostí balíčků a verzí balíčků pro místně nainstalované balíčky. Další informace najdete v tématu [Správa balíčků npm](../javascript/npm-package-management.md).

    (5) Soubory projektu, *jakoapp.js* se zobrazí pod uzlem projektu. *app.js* je spouštěcí soubor projektu, a proto se zobrazuje **tučně.** Spouštěcí soubor můžete nastavit tak, že kliknete pravým tlačítkem na soubor v projektu a vyberete Nastavit **jako Node.js spouštěcí soubor**.

1. Otevřete uzel **npm** a ujistěte se, že jsou k dispozici všechny požadované balíčky npm.

    Pokud některé balíčky chybí (ikona vykřičník), můžete kliknout pravým tlačítkem na **uzel npm** a zvolit **Nainstalovat balíčky npm**.

## <a name="add-some-code"></a>Přidání kódu

Aplikace používá Pug pro front-endovou javascriptovou rozhraní. Pug používá jednoduchý kód značek, který se kompiluje do HTML. (Pug je nastavený jako modul zobrazení v *app.js*. Kód, který nastaví modul zobrazení v *app.js* je `app.set('view engine', 'pug');` .)

1. V Průzkumník řešení (pravé podokno) otevřete složku views a pak *otevřete soubor index.pug.*

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

    Předchozí kód slouží k dynamickému vygenerování stránky HTML s nadpisem a uvítací zprávou. Stránka obsahuje také kód pro zobrazení obrázku, který se změní pokaždé, když stisknete tlačítko.

1. Ve složce routes otevřete *index.js*.

1. Před volání přidejte následující `router.get` kód:

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

1. Volání `router.get` funkce nahraďte následujícím kódem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Předchozí kód nastaví aktuální stránku pomocí objektu směrovače Express a vykreslí stránku a předá na stránku název a datový objekt. Soubor *index.pug* je tady zadaný jako stránka, která se má při spuštění *index.js* načtení. *index.js* je nakonfigurovaná jako výchozí trasa v *app.js* kódu (není zobrazená).

    K předvedení několika Visual Studio je na řádku kódu, který obsahuje , úmyslná `res.render` chyba. Než bude možné aplikaci spustit, musíte tuto chybu opravit, což můžete udělat v další části.

## <a name="use-intellisense"></a>Používání technologie IntelliSense

IntelliSense je Visual Studio nástroj, který vám při psaní kódu pomůže.

1. V *index.js* přejděte na řádek kódu, který obsahuje `res.render` .

1. Umístěte kurzor za řetězec, zadejte a IntelliSense zobrazí funkci definovanou `data` `: get` dříve v `getData` kódu. Vyberte `getData`.

    ![Používání technologie IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Přidejte závorky, aby byla voláním funkce `getData()` .

1. Odeberte čárku ( ) před a u výrazu uvidíte zelené zvýraznění `,` `"data"` syntaxe. Najeďte myší na zvýraznění syntaxe.

    ![Zobrazení chyby syntaxe](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Poslední řádek této zprávy oznamuje, že překladač JavaScriptu očekával čárku ( `,` ).

1. V dolním podokně klikněte na kartu **Seznam chyb** a vyberte **sestavení + IntelliSense** pro typ hlášených problémů.

    Zobrazí se upozornění a popis spolu s názvem souboru a číslem řádku.

    ![Zobrazit seznam chyb](../javascript/media/tutorial-nodejs-error-list.png)

1. Opravte kód přidáním čárky ( `,` ) před `"data"` .

    Po opravě by měl řádek kódu vypadat takto: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Nastavení zarážky

Dál budete pokračovat ve spuštění aplikace s připojeným ladicím programem sady Visual Studio. Než to uděláte, musíte nastavit zarážku.

1. V *index.js* klikněte na levé hřbety před následujícím řádkem kódu, abyste nastavili zarážku:

    `res.render('index', { title: 'Express', "data": getData() });`

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Vyberte cíl ladění na panelu nástrojů ladění, jako je například **webový server (Google Chrome)** nebo **webový server (Microsoft Edge)**.

    ::: moniker range=">=vs-2019"
    ![Vybrat cíl ladění](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Vybrat cíl ladění](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Pokud je v počítači k dispozici Chrome, ale nezobrazuje se jako možnost, zvolte **Procházet pomocí** v rozevíracím seznamu cíl ladění a jako výchozí cíl prohlížeče vyberte Chrome (zvolte **nastavit jako výchozí**).

1. Stisknutím klávesy **F5** (**ladění**  >  **Spusťte ladění**) spusťte aplikaci.

    Ladicí program se zastaví na zarážce, kterou jste nastavili. Nyní můžete zkontrolovat stav aplikace.

1. Najeďte myší `getData` na zobrazení vlastností DataTip

    ![Kontrola proměnných](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Pokračujte stisknutím klávesy **F5** (**ladění**  >  **pokračuje**).

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
> [Nasazení aplikace na Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Rozšíření služby pro jazyk AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
