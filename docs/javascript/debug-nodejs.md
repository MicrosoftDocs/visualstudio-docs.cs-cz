---
title: Ladění JavaScriptu nebo aplikace TypeScriptu
description: Visual Studio poskytuje podporu pro ladění aplikací JavaScript a TypeScript v aplikaci Visual Studio.
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 47f709ae086a32c0680fca060744898251a76afd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589137"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Ladění JavaScriptu nebo aplikace TypeScriptu v aplikaci Visual Studio

Pomocí sady Visual Studio můžete ladit kód JavaScript a TypeScript. Můžete nastavit a spustit zarážky, připojit ladicí program, kontrolovat proměnné, zobrazit zásobník volání a používat další funkce ladění.

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma. V závislosti na typu vývoje aplikací budete možná muset nainstalovat **vývojovou úlohu Node. js** pomocí sady Visual Studio.

## <a name="debug-server-side-script"></a>Ladění skriptu na straně serveru

1. Otevřete projekt v sadě Visual Studio tak, že otevřete soubor JavaScriptu na straně serveru (například *Server. js*), kliknete na hřbet na levé straně a nanastavíte zarážku:

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

1. Pokud chcete aplikaci spustit, stiskněte klávesu **F5** **(ladění**  > **Spustit ladění**).

    Ladicí program se pozastaví na zarážce, kterou jste nastavili (aktuální příkaz je označený žlutě). Teď můžete stav aplikace zkontrolovat tak, že přesunete ukazatel myši nad proměnné v aktuálním rozsahu a použijete okna ladicího programu, například okna **Místní hodnoty** a **Kukátko**.

1. Pokud chcete pokračovat v aplikaci, stiskněte **F5**.

1. Pokud chcete použít Vývojářské nástroje nebo nástroje F12, stiskněte klávesu **F12**. Pomocí těchto nástrojů můžete prozkoumat model DOM a provádět interakce s aplikací pomocí konzoly jazyka JavaScript.

## <a name="debug-client-side-script"></a>Ladění skriptu na straně klienta

Visual Studio poskytuje podporu ladění pro Chrome a Internet Explorer. V některých scénářích ladicí program automaticky narazí na zarážky v kódu JavaScript a TypeScript a v vložených skriptech v souborech HTML.

Pokud je váš zdroj minifikovaného nebo vytvořen pomocí nástroje pro vyvýšení, jako je TypeScript nebo Babel, je pro nejlepší ladění nutné použít [zdrojové mapy](#generate_sourcemaps) . Bez map zdrojového kódu můžete ladicí program připojit ke spuštěnému skriptu na straně klienta. Je však možné pouze nastavit a spustit zarážky v souboru minifikovaného nebo provedený soubor, nikoli v původním zdrojovém souboru. Například v aplikaci Vue. js se skript minifikovaného předává jako řetězec do příkazu `eval` a neexistuje žádný způsob, jak tento kód efektivně Krokovat pomocí ladicího programu sady Visual Studio, pokud nepoužíváte zdrojové mapy. V některých složitých scénářích ladění můžete také použít nástroje Chrome Vývojářské nástroje nebo F12 pro Microsoft Edge.

Chcete-li připojit ladicí program ze sady Visual Studio a zarážky volání v kódu na straně klienta, ladicí program obvykle potřebuje k identifikaci správného procesu. Tady je jeden ze způsobů, jak to povolit pomocí Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Připojení ladicího programu ke skriptu na straně klienta pomocí Chrome

1. Zavřete všechna okna Chromu.

    Tuto akci je nutné provést, aby bylo možné spustit Chrome v režimu ladění.

2. Otevřete příkaz **Spustit** z tlačítka Windows **Start** (klikněte na něj pravým tlačítkem a zvolte **Spustit**) a zadejte následující příkaz:

    `chrome.exe --remote-debugging-port=9222`

    Tento příkaz spustí Chrome s povoleným laděním.

    ::: moniker range=">=vs-2019"

    > [!NOTE]
    > Příznak `--remote-debugging-port` můžete nastavit také při spuštění prohlížeče, a to tak, že na panelu nástrojů **ladění** vyberete **Procházet pomocí...** > a pak zvolíte **Přidat**a pak nastavíte příznak v poli **argumenty** . Použijte jiný popisný název prohlížeče, jako je například **Chrome s laděním**. Podrobnosti najdete v [poznámkách k verzi](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-preview).

    ::: moniker-end

3. Přepněte do sady Visual Studio a nastavte zarážku ve zdrojovém kódu. (Nastavte zarážku na řádek kódu, který umožňuje zarážky, jako je například příkaz `return` nebo deklarace `var`).

    ![Nastavení zarážky](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Pokud potřebujete najít konkrétní kód ve velkém, vygenerovaném souboru, použijte **Ctrl** +**F** (**upravit**  > **Najít a nahradit**  > **Rychlé hledání**).

4. Jako cíl ladění je v sadě Visual Studio vybraný Chrome. Stisknutím **Ctrl**+**F5** (**Ladit** > **Spustit bez ladění**) spusťte aplikaci v prohlížeči.

    Aplikace se otevře na nové kartě prohlížeče.

    Pokud je v počítači k dispozici Chrome, ale nezobrazuje se jako možnost, zvolte **Procházet pomocí** v rozevíracím seznamu cíl ladění a jako výchozí cíl prohlížeče vyberte Chrome (zvolte **nastavit jako výchozí**).

5. Zvolte **Ladit** > **Připojit k procesu**.

6. V dialogovém okně **připojit k procesu** vyberte v poli **připojit k** možnost **WebKit Code** (připojit k), do pole Filtr zadejte **Chrome** a vyfiltrujte výsledky hledání.

    **WebKit kód** je požadovaná hodnota pro Chrome, což je prohlížeč založený na WebKit.

7. Vyberte proces Chrome se správným portem hostitele (1337 na tomto obrázku) a vyberte **připojit**.

    ![Připojení k procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    ::: moniker range="vs-2017"
    Pokud se v sadě Visual Studio otevřely Průzkumník modelu DOM a konzola jazyka JavaScript, je ladicí program správně připojený. Tyto ladicí nástroje jsou podobné nástrojům Chrome Vývojářské nástroje a F12 pro Microsoft Edge.
    ::: moniker-end

    > [!NOTE]
    > Pokud se ladicí program nepřipojí a zobrazí se zpráva „Nelze připojit k procesu. Operace není v aktuálním stavu platná, pomocí Správce úloh zavřete všechny instance Chromu před spuštěním stylu okolí v režimu ladění. Můžou být spuštěná rozšíření Chromu, která brání plnému režimu ladění.

8. Pokud kód se zarážkou už provedený, aktualizujte stránku prohlížeče, aby se dosáhlo zarážky.

    Při pozastavení můžete v ladicím programu zkontrolovat stav aplikace tak, že přesunete ukazatel myši nad proměnné a použijete okna ladicího programu. Můžete v ladicím programu procházet kód pomocí krokování (**F5**, **F10** a **F11**).

    Pro minifikovaného nebo převedený jazyk JavaScript můžete v souboru TypeScript (pomocí map zdroje) použít zarážku buď na rozdrobnějším JavaScriptu, nebo na jeho mapované umístění (pomocí mapování zdrojového kódu), a to v závislosti na vašem prostředí a stavu prohlížeče. V obou případech můžete procházet kód pomocí krokování a zkoumat proměnné.

    * Pokud potřebujete přerušit kód v souboru TypeScript a nemůžete ho provést, použijte příkaz **připojit k procesu** , jak je popsáno v předchozích krocích pro připojení ladicího programu. Pak otevřete dynamicky vygenerovaný soubor TypeScript z Průzkumník řešení otevřením **dokumentů skriptu**  > **filename. TSX**, nastavte zarážku a aktualizujte stránku v prohlížeči (nastavte zarážku na řádek kódu, který umožňuje zarážky, Například příkaz `return` nebo deklarace `var`).

        Případně, pokud potřebujete přerušit kód v souboru TypeScript a nemůžete to provést, zkuste použít příkaz `debugger;` v souboru TypeScript nebo nastavte zarážky v Vývojářské nástroje Chrome.

    * Pokud potřebujete přerušit kód v souboru JavaScriptu (například *App-Bundle. js*) a nemůžete ho provést, odeberte zdrojový soubor mapování souboru *filename. js. map*.

     > [!TIP]
     > Po prvním připojení k procesu pomocí následujícího postupu se můžete rychle znovu připojit ke stejnému procesu výběrem možnosti **ladění**  >  znovu**připojit k procesu**.

## <a name="generate_sourcemaps"></a>Generovat zdrojové mapování pro ladění

Visual Studio má možnost používat a generovat zdrojové mapy ve zdrojových souborech JavaScriptu. To se často vyžaduje v případě, že je váš zdroj minifikovaného nebo vytvořen pomocí proBabelho, jako je TypeScript nebo. Dostupné možnosti závisí na typu projektu.

* Projekt TypeScript v aplikaci Visual Studio vygeneruje ve výchozím nastavení zdroje mapování.

* V projektu JavaScriptu potřebujete generovat zdrojová mapování pomocí sady prostředků, jako je například Webpack, a kompilátoru, jako je například kompilátor TypeScript (nebo Babel), které můžete přidat do projektu. Pro kompilátor TypeScript musíte také přidat soubor *tsconfig. JSON* . Příklad, který ukazuje, jak to provést pomocí základní konfigurace sady Webpack, najdete v tématu [Vytvoření aplikace v Node. js s odpověďmi](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Pokud začínáte se zdrojovými mapami, přečtěte si [Úvod do zdrojového mapování JavaScriptu](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) , než budete pokračovat.

Pro konfiguraci rozšířených nastavení pro zdrojové mapy použijte buď *tsconfig. JSON* , nebo nastavení projektu v projektu TypeScript, ale ne obojí.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Konfigurace zdrojových mapování pomocí souboru tsconfig. JSON

Pokud do projektu přidáte soubor *tsconfig. JSON* , Visual Studio považuje kořen adresáře za projekt TypeScript. Chcete-li přidat soubor, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a pak zvolte **přidat > nová položka > skripty webu > > konfigurační soubor TYPESCRIPT JSON**. Do vašeho projektu se přidá soubor *tsconfig. JSON* podobný následujícímu.

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

#### <a name="compiler-options-for-tsconfigjson"></a>Možnosti kompilátoru pro tsconfig. JSON

* **inlineSourceMap**: vygenerujte jeden soubor se zdrojovými mapami místo vytvoření samostatného zdrojového mapování pro každý zdrojový soubor.
* **inlineSources**: emituje zdroj společně se zdrojovými mapami v rámci jednoho souboru; vyžaduje, aby byl nastaven *inlineSourceMap* nebo *sourceMap* .
* **mapRoot**: Určuje umístění, kde má ladicí program najít soubory zdrojového mapování ( *. map*) místo výchozího umístění. Tento příznak použijte v případě, že soubory run-time *. map* musí být v jiném umístění než soubory *. js* . Zadané umístění je vložené ve zdrojovém mapování pro přesměrování ladicího programu do umístění souborů *. map* .
* **sourceMap**: vygeneruje odpovídající soubor *. map* .
* **sourceRoot**: Určuje umístění, kde by měl ladicí program najít soubory TypeScript místo zdrojových umístění. Tento příznak použijte v případě, že se zdroje za běhu musí nacházet v jiném umístění, než je umístění v době návrhu. Zadané umístění je vložené ve zdrojovém mapování pro přesměrování ladicího programu na místo, kde jsou umístěny zdrojové soubory.

Další podrobnosti o možnostech kompilátoru najdete v [možnostech kompilátoru](https://www.typescriptlang.org/docs/handbook/compiler-options.html) na stránce v příručce TypeScript.

### <a name="configure-source-maps-using-project-settings"></a>Konfigurace zdrojových mapování pomocí nastavení projektu

Můžete také nakonfigurovat nastavení mapování zdrojového kódu pomocí vlastností projektu kliknutím pravým tlačítkem myši na projekt a následným výběrem **Vlastnosti projektu > >m ladění TypeScript Build >** .

Tato nastavení projektu jsou k dispozici.

* **Generovat zdrojové mapy** (ekvivalentem **sourceMap** v souboru *tsconfig. JSON*): vygeneruje odpovídající soubor *. map* .
* **Zadat kořenový adresář zdrojových mapování** (ekvivalentem **mapRoot** v souboru *tsconfig. JSON*): Určuje umístění, kde by měl ladicí program najít soubory map místo vygenerovaných umístění. Tento příznak použijte v případě, že soubory run-time *. map* musí být umístěny v jiném umístění než soubory. js. Zadané umístění je vložené ve zdrojovém mapování pro přesměrování ladicího programu na místo, kde jsou umístěny soubory map.
* **Zadejte kořenový adresář souborů TypeScriptu** (ekvivalentní **sourceRoot** ve *tsconfig. JSON*): Určuje umístění, kde by měl ladicí program najít soubory TypeScript místo zdrojových umístění. Tento příznak použijte v případě, že zdrojové soubory za běhu musí být v jiném umístění než v době návrhu. Zadané umístění je vložené ve zdrojovém mapování pro přesměrování ladicího programu na místo, kde jsou umístěny zdrojové soubory.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Ladění JavaScriptu v dynamických souborech pomocí Razor (ASP.NET)

Visual Studio poskytuje podporu ladění pro Chrome a Internet Explorer. Automaticky připojí zarážky do JavaScriptu/TypeScript a vložené skripty v souborech HTML.

Ladění dynamicky generovaných souborů není automatické. V souborech vygenerovaných pomocí syntaxe Razor (cshtml, VBHTML) nemůžete automaticky narazit zarážky. Existují dva přístupy, které můžete použít k ladění tohoto typu souboru:

* **Umístěte příkaz `debugger;`, kde chcete přerušit**: způsobí to, že dynamický skript zastaví provádění a spustí ladění ihned během vytváření.
* **Načíst stránku a otevřít dynamický dokument v sadě Visual Studio**: budete muset otevřít dynamický soubor během ladění, nastavit zarážku a aktualizovat stránku, aby fungovala Tato metoda. V závislosti na tom, jestli používáte Chrome nebo Internet Explorer, najdete soubor pomocí jedné z následujících strategií:

   Pro Chrome použijte **Průzkumník řešení > dokumentů skriptů > YourPageName**.

    > [!NOTE]
    > Pokud používáte Chrome, může se zobrazit zpráva **žádný zdroj není k dispozici mezi \<script > značek**. To je v pořádku, stačí pokračovat v ladění.

   Pro Internet Explorer použijte **Průzkumník řešení > dokumentů skriptu > Windows Internet Explorer > YourPageName**.

Další informace najdete v tématu [ladění projektů ASP.NET na straně klienta v Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).