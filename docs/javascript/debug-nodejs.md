---
title: Ladění javascriptové nebo textové aplikace
description: Visual Studio poskytuje podporu pro ladění aplikací JavaScript a TypeScript v sadě Visual Studio
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678971"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Ladění javascriptu nebo aplikace TypeScript ve Visual Studiu

Kód JavaScriptu a TypeScriptu můžete ladit pomocí sady Visual Studio. Můžete nastavit a zasáhnout zarážky, připojit ladicí program, zkontrolovat proměnné, zobrazit zásobník volání a použít další funkce ladění.

> [!TIP]
> Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte ji zdarma. V závislosti na typu vývoje aplikací, který provádíte, může být nutné nainstalovat **úlohu vývoje Node.js** pomocí sady Visual Studio.

## <a name="debug-server-side-script"></a>Ladění skriptu na straně serveru

1. Když je projekt otevřený v sadě Visual Studio, otevřete soubor JavaScript na straně serveru (například *server.js*), klikněte do kanálu na levé okapu a nastavte zarážku:

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

1. Chcete-li aplikaci spustit, stiskněte **klávesu F5** (**Ladění** > **ladění startování**).

    Ladicí program se pozastaví na zarážce, kterou jste nastavili (aktuální příkaz je označený žlutě). Teď můžete stav aplikace zkontrolovat tak, že přesunete ukazatel myši nad proměnné v aktuálním rozsahu a použijete okna ladicího programu, například okna **Místní hodnoty** a **Kukátko**.

1. Pokud chcete pokračovat v aplikaci, stiskněte **F5**.

1. Chcete-li použít nástroje pro vývojáře Chrome nebo nástroje F12, stiskněte **klávesu F12**. Pomocí těchto nástrojů můžete prozkoumat model DOM a provádět interakce s aplikací pomocí konzoly jazyka JavaScript.

## <a name="debug-client-side-script"></a>Ladění skriptu na straně klienta

::: moniker range=">=vs-2019"
Visual Studio poskytuje podporu ladění na straně klienta pouze pro Prohlížeče Chrome a Microsoft Edge (Chromium). V některých případech ladicí program automaticky zasáhne zarážky v kódu JavaScriptu a Typu Script u vložených skriptů v souborech HTML. Ladění skriptu na straně klienta v ASP.NET aplikací chod naleznete v příspěvku blogu [Ladění JavaScriptu v prohlížeči Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) a v tomto [příspěvku pro Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Ladění jazyka TypeScript v ASP.NET jádru najdete také v [tématu Vytvoření aplikace ASP.NET Jádro pomocí jazyka TypeScript](tutorial-aspnet-with-typescript.md).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio poskytuje podporu ladění na straně klienta pouze pro Prohlížeče Chrome a Internet Explorer. V některých případech ladicí program automaticky zasáhne zarážky v kódu JavaScriptu a Typu Script u vložených skriptů v souborech HTML. Ladění skriptu na straně klienta v ASP.NET aplikacích najdete v příspěvku blogu [Ladění ASP.NET projektů na straně klienta v prohlížeči Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Pro jiné aplikace než ASP.NET postupujte podle pokynů popsaných zde.

### <a name="prepare-your-app-for-debugging"></a>Příprava aplikace na ladění

Pokud je váš zdroj minififován nebo vytvořen transpilerem, jako je TypeScript nebo Babel, je pro nejlepší ladění vyžadováno použití [zdrojových map.](#generate_source_maps) Bez zdrojových map můžete stále připojit ladicí program ke spuštěnému skriptu na straně klienta. Však může být možné nastavit a zasáhnout zarážky v minified nebo transpilovaný soubor, nikoli v původním zdrojovém souboru. Například v aplikaci Vue.js minified skript získá předán `eval` jako řetězec do příkazu a neexistuje žádný způsob, jak krokovat tento kód efektivně pomocí ladicího programu Visual Studio, pokud používáte zdrojové mapy. Ve složitých scénářích ladění můžete místo toho použít nástroje pro vývojáře Chrome nebo nástroje F12 pro Microsoft Edge.

Nápovědu ke generování zdrojových map naleznete v [tématu Generování zdrojových map pro ladění](#generate_source_maps).

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>Příprava prohlížeče na ladění

::: moniker range=">=vs-2019"
V tomto scénáři použijte buď Microsoft Edge (Chromium), aktuálně pojmenovaný **Microsoft Edge Beta** v IDE nebo Chrome.
::: moniker-end
::: moniker range="vs-2017"
V tomto scénáři použijte Chrome.
::: moniker-end

1. Zavřete všechna okna pro cílový prohlížeč.

   Jiné instance prohlížeče mohou zabránit otevření prohlížeče s povoleným laděním. (Rozšíření prohlížeče mohou být spuštěna a brání úplnému režimu ladění, takže možná budete muset otevřít Správce úloh, abyste našli neočekávané instance Chromu.)

   ::: moniker range=">=vs-2019"
   Pro Microsoft Edge (Chromium) také vypněte všechny instance Chromu. Vzhledem k tomu, že oba prohlížeče používají základ kódu chromu, poskytuje to nejlepší výsledky.
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

Chcete-li připojit ladicí program z visual studia a přístupových zarážek v kódu na straně klienta, ladicí program potřebuje pomoc k identifikaci správného procesu. Tady je jedna možnost, jak to udělat.

1. Přepněte do sady Visual Studio a nastavte zarážku ve zdrojovém kódu, což může být soubor JavaScript, soubor TypeScript nebo soubor JSX. (Nastavte zarážku v řádku kódu, který umožňuje zarážky, jako je například příkaz return nebo deklarace var.)

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Chcete-li najít konkrétní kód v transpovaném souboru, použijte **kombinaci kláves Ctrl**+**F** (**Upravit** > rychlé**hledání**a**nahradit** > ).

    Pro kód na straně klienta, chcete-li zasáhnout zarážku v souboru TypeScript, *.vue*nebo JSX soubor obvykle vyžaduje použití [zdrojových map](#generate_source_maps). Zdrojová mapa musí být správně nakonfigurována tak, aby podporovala ladění v sadě Visual Studio.

2. Vyberte cílový prohlížeč jako ladicí cíl v sadě Visual Studio a stisknutím **kláves Ctrl**+**F5** **(Ladění** > **startu bez ladění)** aplikaci spusťte v prohlížeči.

    ::: moniker range=">=vs-2019"
    Pokud jste vytvořili konfiguraci prohlížeče s popisným názvem, zvolte ji jako cíl ladění.
    ::: moniker-end

    Aplikace se otevře na nové kartě prohlížeče.

3. Zvolte **Připojit ladění** > **ke zpracovat**.

    > [!TIP]
    > Počínaje Visual Studio 2017, po prvním připojení k procesu pomocí následujících kroků, můžete rychle znovu připojit ke stejnému procesu výběrem **ladění** > **znovu připojit k procesu**.

4. V dialogovém okně **Připojit k procesu** získáte filtrovaný seznam instancí prohlížeče, ke kterým se můžete připojit.
    ::: moniker range=">=vs-2019"
    V Sadě Visual Studio 2019 zvolte správný ladicí program pro cílový prohlížeč, **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge - Chromium)** v **poli Připojit k,** zadejte **chrom** nebo **okraj** do pole filtru pro filtrování výsledků hledání.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V Sadě Visual Studio 2017 zvolte v poli **Připojit k** **kód Webkitu** a do pole filtru zadejte **chrom,** abyste filtrovat výsledky hledání.
    ::: moniker-end

5. Vyberte proces prohlížeče se správným hostitelským portem (localhost v tomto příkladu) a vyberte **Připojit**.

    Port (například 1337) se může také zobrazit v poli **Název,** který vám pomůže vybrat správnou instanci prohlížeče.

    ::: moniker range=">=vs-2019"
    Následující příklad ukazuje, jak to vypadá pro prohlížeč Microsoft Edge (Chromium).

    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Pokud se v sadě Visual Studio otevřely Průzkumník modelu DOM a konzola jazyka JavaScript, je ladicí program správně připojený. Tyto ladicí nástroje jsou podobné nástrojům pro vývojáře Chrome a nástrojům F12 pro Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Pokud ladicí program nepřipojí a zobrazí se zpráva "Nepodařilo se spustit ladicí adaptér" nebo "Nelze připojit k procesu. Operace není v aktuálním stavu legální.", Pomocí Správce úloh systému Windows zavřete všechny instance cílového prohlížeče před spuštěním prohlížeče v režimu ladění. Rozšíření prohlížeče může být spuštěna a brání režimu úplnéladění.

6. Vzhledem k tomu, že kód s zarážkou již byl proveden, aktualizujte stránku prohlížeče. V případě potřeby proveďte akci a způsobte spuštění kódu s zarážkou.

    Při pozastavení můžete v ladicím programu zkontrolovat stav aplikace tak, že přesunete ukazatel myši nad proměnné a použijete okna ladicího programu. Můžete v ladicím programu procházet kód pomocí krokování (**F5**, **F10** a **F11**). Další informace o základních funkcích ladění naleznete [v tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md).

    V závislosti na typu aplikace, předchozích krocích a dalších faktorech, jako je stav prohlížeče, můžete narazit na zarážku v transpovaném souboru *JS* nebo ve zdrojovém souboru. V obou případech můžete procházet kód pomocí krokování a zkoumat proměnné.

   * Pokud potřebujete rozdělit do kódu ve zdrojovém souboru TypeScript, JSX nebo *.vue* a nemůžete to udělat, ujistěte se, že vaše prostředí je správně nastaveno, jak je popsáno v části [Poradce při potížích.](#troubleshooting_source_maps)

   * Pokud potřebujete proniknout do kódu v transpovaném souboru JavaScriptu (například *app-bundle.js)* a nemůžete to udělat, odeberte zdrojový mapový soubor file, *filename.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>Poradce při potížích s zarážkymi a zdrojovými mapami

Pokud potřebujete rozdělit do kódu ve zdrojovém souboru TypeScript nebo JSX a nemůžete to udělat, použijte **připojit k procesu,** jak je popsáno v předchozích krocích připojit ladicí program. Ujistěte se, že je vaše prostředí správně nastaveno:

* Zavřeli jste všechny instance prohlížeče, včetně rozšíření Chrome (pomocí Správce úloh), abyste mohli prohlížeč spustit v režimu ladění.
      
* Ujistěte se, že [jste spustili prohlížeč v režimu ladění](#prepare_the_browser_for_debugging).

* Ujistěte se, že zdrojový mapový soubor obsahuje správnou relativní cestu ke zdrojovému souboru a že neobsahuje nepodporované prefixy, jako je *webpack:///*, což brání ladicímu programu sady Visual Studio v hledání zdrojového souboru. Například odkaz, jako *je webpack:///.app.tsx* může být opravenna *./app.tsx*. Můžete to provést ručně ve zdrojovém mapovém souboru (což je užitečné pro testování) nebo prostřednictvím vlastní konfigurace sestavení. Další informace naleznete v [tématu Generovat zdrojové mapy pro ladění](#generate_source_maps).

Případně, pokud potřebujete proniknout do kódu ve zdrojovém souboru (například *app.tsx)* a `debugger;` nemůžete to udělat, zkuste použít příkaz ve zdrojovém souboru nebo místo toho nastavte zarážky v Nástrojích pro vývojáře Chrome (nebo F12 Tools for Microsoft Edge).

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a>Generovat zdrojové mapy pro ladění

Visual Studio má schopnost používat a generovat zdrojové mapy na zdrojových souborech JavaScript. To je často vyžadováno, pokud je váš zdroj minifován nebo vytvořen transpilerem, jako je TypeScript nebo Babel. Dostupné možnosti závisí na typu projektu.

* Projekt TypeScript v sadě Visual Studio ve výchozím nastavení generuje zdrojové mapy. Další informace naleznete v [tématu Konfigurace zdrojových map pomocí souboru tsconfig.json](#configure_source_maps).

* V projektu JavaScript, můžete generovat zdrojové mapy pomocí bundler jako webpack a kompilátor jako kompilátor TypeScript (nebo Babel), které můžete přidat do svého projektu. Pro kompilátor TypeScript musíte také přidat soubor *tsconfig.json* a nastavit možnost kompilátoru. `sourceMap` Příklad, který ukazuje, jak to provést pomocí základní konfigurace webového balíčku, najdete v [tématu Vytvoření aplikace Node.js s React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Pokud se zdrojovými mapami tečujete, přečtěte si před pokračováním [úvod do javascriptových zdrojových map.](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) 

Chcete-li nakonfigurovat upřesňující nastavení pro zdrojové mapy, použijte *tsconfig.json* nebo nastavení projektu v projektu typu TypeScript, ale ne obojí.

Chcete-li povolit ladění pomocí sady Visual Studio, musíte se ujistit, že odkazy na zdrojový soubor v generované zdrojové mapě jsou správné (to může vyžadovat testování). Pokud například používáte webpack, odkazy ve zdrojovém mapovém souboru obsahují *předponu webpack:///,* která brání aplikaci Visual Studio v hledání zdrojového souboru Typu Script nebo JSX. Konkrétně při této opravy pro účely ladění, odkaz na zdrojový soubor (například *app.tsx*), musí být změněn z něco jako *webpack:///./app.tsx* na něco jako *./app.tsx*, který umožňuje ladění (cesta je relativní k zdrojového souboru). Následující příklad ukazuje, jak můžete nakonfigurovat zdrojové mapy ve webovém balíčku, což je jeden z nejběžnějších balíčků, aby fungovaly s Visual Studio.

(Pouze webpack) Pokud nastavujete zarážku v typescriptu souboru JSX (spíše než transpilovaný soubor JavaScript), musíte aktualizovat konfiguraci webového balíčku. Například v *souboru webpack-config.js*může být nutné nahradit následující kód:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

s tímto kódem:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Toto je nastavení pouze pro vývoj, které umožňuje ladění kódu na straně klienta v sadě Visual Studio.

Pro složité scénáře nástroje prohlížeče **(F12**) někdy fungují nejlépe pro ladění, protože nevyžadují změny vlastních předpon.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>Konfigurace zdrojových map pomocí souboru tsconfig.json

Pokud do projektu přidáte soubor *tsconfig.json,* visual studio považuje kořen adresáře adresáře za projekt typu TypeScript. Chcete-li soubor přidat, klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a pak zvolte **Přidat > novou položku > konfiguračním souboru Jazyka TypeScript**. Do projektu se přidá soubor *tsconfig.json,* jako je následující.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Možnosti kompilátoru pro soubor tsconfig.json

* **inlineSourceMap**: Vyzařujte jeden soubor se zdrojovými mapami namísto vytvoření samostatné zdrojové mapy pro každý zdrojový soubor.
* **inlineSources**: Vyzařovat zdroj vedle zdrojové mapy v rámci jednoho souboru; vyžaduje *nastavení inlineSourceMap* nebo *sourceMap.*
* **mapRoot**: Určuje umístění, kde by měl ladicí program najít zdrojové mapy (*.map)* soubory namísto výchozího umístění. Tento příznak použijte, pokud soubory *mapy* za běhu musí být v jiném umístění než soubory *JS.* Zadané umístění je vloženo do zdrojové mapy a ladicí program směřuje do umístění souborů *MAPY.*
* **sourceMap**: Generuje odpovídající soubor *.map.*
* **sourceRoot**: Určuje umístění, kde by měl ladicí program najít soubory TypeScript namísto zdrojových umístění. Tento příznak použijte, pokud zdroje za běhu musí být v jiném umístění než umístění v době návrhu. Zadané umístění je vloženo do zdrojové mapy a ladicí program nasměruje na místo, kde jsou umístěny zdrojové soubory.

Další podrobnosti o možnostech kompilátoru najdete na stránce [Možnosti kompilátoru](https://www.typescriptlang.org/docs/handbook/compiler-options.html) v příručce TypeScript Handbook.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Konfigurace zdrojových map pomocí nastavení projektu (typescriptový projekt)

Nastavení zdrojového mapování můžete také nakonfigurovat pomocí vlastností projektu tak, že klepnete pravým tlačítkem myši na projekt a pak zvolíte **Vlastnosti aplikace Project > >** ladění sestavení > .

Tato nastavení projektu jsou k dispozici.

* **Generovat zdrojové mapy** (ekvivalentní **sourceMap** v *tsconfig.json*): Generuje odpovídající soubor *.map.*
* **Zadejte kořenový adresář zdrojových map** (ekvivalentní **mapRoot** v *tsconfig.json*): Určuje umístění, kde by měl ladicí program najít mapové soubory namísto generovaných umístění. Tento příznak použijte, pokud soubory *mapy* za běhu musí být umístěny v jiném umístění než soubory JS. Zadané umístění je vloženo do zdrojové mapy a ladicí program nasměruje na místo, kde jsou umístěny mapové soubory.
* **Zadejte kořenový adresář souborů TypeScript** (ekvivalentní **sourceRoot** v *tsconfig.json*): Určuje umístění, kde by měl ladicí program najít soubory TypeScript místo zdrojových umístění. Tento příznak použijte, pokud zdrojové soubory za běhu musí být v jiném umístění než umístění v době návrhu. Zadané umístění je vloženo do zdrojové mapy a ladicí program nasměruje na místo, kde jsou umístěny zdrojové soubory.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Ladění JavaScriptu v dynamických souborech pomocí Razor (ASP.NET)

::: moniker range=">=vs-2019"
Od visual studia 2019 poskytuje Visual Studio podporu ladění pouze pro Chrome a Microsoft Edge (Chromium).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio poskytuje podporu ladění pouze pro Prohlížeče Chrome a Internet Explorer.
::: moniker-end

Nelze však automaticky zasáhnout zarážky u souborů generovaných syntaxí Razor (cshtml, vbhtml). Existují dva přístupy, které můžete použít k ladění tohoto druhu souboru:

* **Umístěte `debugger;` příkaz na místo, kde chcete přerušit**: To způsobí, že dynamický skript zastavit provádění a spustit ladění okamžitě, zatímco je vytvářen.
* **Načtěte stránku a otevřete dynamický dokument v sadě Visual Studio**: Při ladění budete muset otevřít dynamický soubor, nastavit zarážku a aktualizovat stránku, aby tato metoda fungovala. V závislosti na tom, zda používáte Chrome nebo Internet Explorer, najdete soubor pomocí jedné z následujících strategií:

   V případě Chromu přejděte do **Průzkumníka řešení > dokumenty skriptů > název stránky**.

    > [!NOTE]
    > Při používání Chromu se může stát, že **mezi \<značkami skriptů>** není k dispozici žádný zdroj . To je v pořádku, jen pokračovat v ladění.

   ::: moniker range=">=vs-2019"
   Pro Microsoft Edge (Chromium) použijte stejný postup jako Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   V aplikaci Internet Explorer přejděte do **aplikace Solution Explorer > Script Documents > windows internet explorer > YourPageName**.
   ::: moniker-end

Další informace naleznete [v tématu Ladění ASP.NET projektů na straně klienta v prohlížeči Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
