---
title: Ladění kódu v Pythonu
description: Visual Studio poskytují bohatá podpora ladění pro kód Python, včetně nastavení zarážek, krokování, kontrolu hodnoty, prohlížení výjimek a ladění v interaktivním okně.
ms.date: 10/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0e4cc2ff43b59fff0aac70d9cc13a0a00662e209
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068432"
---
# <a name="debug-your-python-code"></a>Ladění kódu Pythonu

Visual Studio nabízí komplexní možnosti ladění pro Python, včetně připojení ke spuštěným procesům, vyhodnocování výrazů v **Watch** a **okamžité** windows, kontrola místní proměnné, zarážky, krok v/out nebo přes příkazy **nastavit další příkaz**a provádění dalších akcí.

Také naleznete v následujících článcích ladění specifické pro scénář:

- [Vzdálené ladění pro Linux](debugging-python-code-on-remote-linux-machines.md)
- [Ladění ve smíšeném režimu Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symboly pro ladění ve smíšeném režimu](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) ukázku pythonu ladění (3 m 32s).|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python v sadě Visual Studio podporuje ladění bez projektu. Samostatný Python soubor otevřít, klikněte pravým tlačítkem v editoru vyberte **začínat ladění**, a sady Visual Studio spustí skript s prostředím globální výchozí nastavení (naleznete v tématu [prostředí Pythonu](managing-python-environments-in-visual-studio.md)) a bez argumentů. Ale od té chvíle má úplnou podporu ladění.
>
> K řízení prostředí a argumenty, vytvořte projekt pro kód, který se snadno provádí pomocí [z existující Pythonu kódu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) šablony projektu.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Základní ladění

Základní ladicí pracovní postup zahrnuje nastavení zarážek, krokování kódem, kontrolu hodnoty a zpracování výjimek, jak je popsáno v následujících částech.

Ladicí relace začíná **ladění** > **spustit ladění** příkazu **Start** tlačítko na panelu nástrojů nebo **F5**klíč. Tyto akce spuštění po spuštění souboru projektu (ukazuje tučně v **Průzkumníku řešení**) s aktivní prostředí projektu a jakékoli argumenty příkazového řádku nebo vyhledávací cesty zadané v **projektu Vlastnosti** (viz [možnosti ladění projektu](#project-debugging-options)). **Visual Studio 2017 verze 15.6** a upozorní vás později, pokud není nutné nastavit spouštěcí soubor; starší verze může otevřít okno výstupu překladač Pythonu s nebo krátce se zobrazí v okně Výstup a zmizí. V každém případě klikněte pravým tlačítkem na příslušný soubor a vyberte **nastavit jako spouštěcí soubor**.

> [!Note]
> Ladicí program vždy začíná na aktivní prostředí projektu Pythonu. Chcete-li změnit prostředí, ujistěte se, jiné jednu aktivní jak je popsáno na [vyberte prostředí Pythonu pro projekt](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Zarážky

Zarážky zastaví provádění kódu označenou okamžiku tak můžete kontrolovat stav programu. Nastavení zarážek kliknutím do levého okraje editoru kódu nebo tak, že kliknete pravým tlačítkem na řádek kódu a vyberete **zarážku** > **vložit zarážku**. Na každém řádku s zarážky, zobrazí se červená tečka.

![Zarážky v sadě Visual Studio](media/debugging-breakpoints.png)

Kliknutím na červenou tečku nebo kliknete pravým tlačítkem na řádek kódu a výběrem **zarážku** > **odstranění zarážky** tím tuto zarážku odstraníte. Můžete ho také zakázat bez nutnosti odebírání pomocí **zarážku** > **zakázat zarážku** příkazu.

> [!Note]
> Některé zarážky v jazyce Python se dá překvapivé pro vývojáře, kteří pracovali s jinými programovací jazyky. V jazyce Python je celý soubor spustitelného kódu, takže Python spustí soubor je načtena na zpracování jakékoli třídy nejvyšší úrovně nebo definice funkcí. Pokud byla nastavena na zarážku, můžete zjistit ladicí program zásadní součástí – způsob, jak prostřednictvím deklarace třídy. Toto chování je správná, i když je někdy překvapivé.

Můžete přizpůsobit podmínky, za kterých se aktivuje zarážky, jako je zastavení jenom v případě, že proměnná je nastavena na hodnotu nebo rozsah hodnot. Chcete-li nastavit podmínky, klikněte pravým tlačítkem na červenou tečku k zarážce, vyberte **podmínku**, vytvořte výrazů pomocí kódu v Pythonu. Úplné podrobnosti o této funkci v sadě Visual Studio najdete v tématu [podmínky zarážky](../debugger/using-breakpoints.md#breakpoint-conditions).

Při nastavování podmínky, můžete také nastavit **akce** a vytvořit zprávu do protokolu v okně výstupu, Volitelně můžete pokračovat v provádění automaticky. Protokolování zprávy vytvoří, co se volá *zarážka s trasováním* bez přidání protokolování kódu přímo do vaší aplikace:

![Vytváření zarážku s trasováním s zarážku](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Krokovat kód

Po zastavení na zarážce, budete mít různé způsoby, jak procházet kód nebo spuštění bloků kódu před dopadem na dřívější kód znovu. Tyto příkazy jsou dostupné v řadě míst, včetně nástrojů nejvyšší ladění **ladění** nabídky, v místní nabídce klikněte pravým tlačítkem v editoru kódu a pomocí klávesové zkratky (ale ne všechny příkazy jsou na všech místech):

| Funkce | Stisknutí kláves | Popis |
| --- | --- | --- |
| **Continue** | **F5** | Spouští kód, dokud nebude dosaženo k další zarážce. |
| **Krokovat s vnořením** | **F11** | Následující příkaz spustí a zastaví. Pokud je volání funkce další příkaz, ladicí program se zastaví na prvním řádku volané funkce. |
| **Krok přes** | **F10** | Spustí další příkaz, včetně volání na funkci (s jeho kód) a použití jakékoli návratovou hodnotu. Krokování přes umožňuje snadno přeskočit funkce, které není potřeba ladění. |
| **Krokovat s Vystoupením** | **SHIFT**+**F11** | Spustí kód do konce aktuální funkci a pak kroky volání příkazu.  Tento příkaz je užitečné, když není nutné ladit zbytek aktuální funkce. |
| **Spustit ke kurzoru** | **CTRL**+**F10** | Spustí kód do umístění blikající kurzor v editoru. Tento příkaz umožňuje snadno přeskočit část kódu, který není nutné k ladění. |
| **Nastavení dalšího příkazu** | **CTRL**+**Shift**+**F10** | Změny aktuálního spuštění bodu do umístění blikajícího kurzoru v kódu. Tento příkaz umožňuje vynechat segment kódu na všech spuštění, jako když víte, kód je chybný nebo je výsledný nežádoucí vedlejší efekt. |
| **Zobrazit další příkaz** | **ALT**+**Num****&#42;**| Vrátíte se do dalšího příkazu ke spuštění. Tento příkaz je užitečné, pokud jste hledání ve vašem kódu a nepamatujete, kde je zastavený ladicím programu. |

### <a name="inspect-and-modify-values"></a>Kontrola a změny hodnot

Při zastavení v ladicím programu, můžete zkontrolovat a změnit hodnoty proměnných. Můžete také použít **Watch** okno monitorovat jednotlivé proměnné, stejně jako vlastní výrazy. (Viz [kontrolovat proměnné](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows) obecné podrobnosti.)

Chcete-li zobrazit hodnotu pomocí **DataTips**, stačí najet myší přes všechny proměnné v editoru. Můžete kliknout na hodnotu a změňte ji:

![DataTips zobrazující v ladicím programu sady Visual Studio](media/debugging-quick-tips.png)

**Automatické hodnoty** okno (**ladění** > **Windows** > **automatické hodnoty**) obsahuje proměnné a výrazy, které blíží aktuální příkaz. Dvojitým kliknutím na sloupec hodnoty nebo vyberte a stiskněte **F2** upravte hodnotu:

![Okno Automatické hodnoty v ladicím programu sady Visual Studio](media/debugging-autos-window.png)

**Lokální** okno (**ladění** > **Windows** > **lokální**) zobrazí všechny proměnné, které jsou v aktuální obor, který lze upravovat znovu:

![Okno místních hodnot v ladicím programu sady Visual Studio](media/debugging-locals-window.png)

Pro další použití v **automatické hodnoty** a **lokální**, naleznete v tématu [kontrolovat proměnné v okně Automatické hodnoty a místní hodnoty](../debugger/autos-and-locals-windows.md).

**Watch** systému windows (**ladění** > **Windows** > **Watch**  >   **Podívejte se na 1 až 4**) vám umožní zadat libovolné výrazy Pythonu a zobrazit výsledky. Výrazy jsou již znovu pro každý krok:

![Podívejte se na okno v ladicím programu sady Visual Studio](media/debugging-watch-window.png)

Pro další použití v **Watch**, naleznete v tématu [nastavení sledování u proměnných v oknech kukátka a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md).

Při kontrole řetězcovou hodnotu (`str`, `unicode`, `bytes`, a `bytearray` jsou všechny považovány za řetězce k tomuto účelu), s ikonou lupy se zobrazí na pravé straně hodnoty. Kliknutím na ikonu se zobrazí hodnota řetězec bez uvozovek v dialogovém okně automaticky otevírané okno s zabalení a posouvání, což je užitečné pro dlouhé řetězce. Kromě toho na tlačítko se šipkou rozevíracího seznamu na ikonu vám umožní vybrat prostý text, HTML, XML a JSON vizualizace:

![Řetězec vizualizéry v ladicím programu sady Visual Studio](media/debugging-string-visualizers.png)

HTML, XML a JSON vizualizace zobrazí ve windows samostatné automaticky otevírané okno se zobrazeními zvýrazňování a stromu syntaxe.

### <a name="exceptions"></a>Výjimky

Pokud dojde k chybě ve svém programu během ladění, ale pro něj nemáte obslužnou rutinu výjimky, ladicí program přeruší místě výjimku:

![Automaticky otevírané okno výjimky v ladicím programu sady Visual Studio](media/debugging-exception-popup.png)

V tomto okamžiku můžete kontrolovat stav programu, včetně zásobníku volání. Ale pokud se pokusíte krokovat kód, výjimka dál vyvolávána, dokud se buď zpracovává nebo ukončení programu.

**Ladění** > **Windows** > **nastavení výjimek** příkaz nabídky zobrazí okno, ve kterém můžete rozbalit **Pythonu Výjimky**:

![Okno výjimky v ladicím programu sady Visual Studio](media/debugging-exception-settings.png)

Zaškrtávací políčko u každé výjimce ovládací prvky, zda ladicí program *vždy* přestane fungovat, když je vyvolána. Toto políčko zaškrtněte, pokud chcete přerušit častěji pro určité výjimky.

Ve výchozím nastavení většina výjimek přerušit, pokud obslužná rutina výjimky nebyl nalezen ve zdrojovém kódu. Chcete-li toto chování změnit, klikněte pravým tlačítkem na jakékoli výjimce a upravit **pokračovat po neošetřené v uživatelském kódu** možnost. Zaškrtnutí tohoto políčka zrušte, pokud chcete přerušit méně často pro výjimku.

Ke konfiguraci výjimky, které nejsou uvedené v tomto seznamu, klikněte na tlačítko **přidat** tlačítko Přidat. Název musí odpovídat názvu výjimky.

## <a name="project-debugging-options"></a>Možnosti ladění projektu

Ve výchozím nastavení spustí ladicí program programu pomocí standardní Spouštěč Pythonu, bez argumentů příkazového řádku a žádné jiné speciální cesty nebo podmínky. Možnosti spuštění jsou změnit prostřednictvím vlastnosti ladění projektu přistupovat kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení**, kde vyberou **vlastnosti**a výběr **ladění**  kartu.

![Vlastnosti ladění projektu v ladicím programu sady Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Možnosti režimu spuštění

| Možnost | Popis |
| --- | --- |
| **Standardní Spouštěč Pythonu** | Použití ladění kódu napsaného v přenosných Pythonu, který je kompatibilní s CPython, IronPython a variant, jako jsou Stackless Python. Poskytuje nejlepší prostředí pro ladění čistého kódu v Pythonu. Jestliže se pokusíte připojit ke spuštěnému *python.exe* procesu, se používá tento program. Tento program také poskytuje [ladění ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) pro CPython, díky tomu Krokovat bez problémů mezi kódu C/C++ a kódu v Pythonu. |
| **Webový Spouštěč** | Spustí výchozí prohlížeč při spuštění a povolí ladění šablon. Najdete v článku [ladění šablon webové](python-web-application-project-templates.md#debugging) části Další informace. |
| **Django webový Spouštěč** | Stejné jako webový Spouštěč a zobrazuje pouze pro zpětnou kompatibilitu. |
| **Spouštěč pro IronPython (.NET)** | Používá ladicí program .NET, která funguje jenom v Ironpythonu, ale umožňuje krokování mezi jakéhokoli projektu .NET jazyka, včetně C# a VB. Tento program se používá, pokud je připojit ke spuštěnému procesu .NET, který je hostitelem Ironpythonu. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Možností spuštění (cesty pro hledání, argumenty pro spuštění a proměnných prostředí)

| Možnost | Popis |
| --- | --- |
| **Cesty pro hledání** | Tyto hodnoty odpovídat, jak je zobrazeno v projektu **cesty pro hledání** uzel v **Průzkumníka řešení**. Tuto hodnotu Tady můžete upravit, ale je snáze se použít **Průzkumníka řešení** , který vám umožňuje procházet složky a automaticky převede do formuláře relativní cesty. |
| **Argumenty skriptu** | Tyto argumenty jsou přidány do příkaz použitý ke spuštění skriptu, vyskytující se po název souboru vašeho skriptu. První položka zde je k dispozici pro váš skript jako `sys.argv[1]`, druhý jako `sys.argv[2]`, a tak dále. |
| **Argumenty pro interpret** | Tyto argumenty jsou přidány do příkazového řádku Spouštěč před název vašeho skriptu. Běžné argumenty tady `-W ...` řízení upozornění `-O` mírně optimalizovat váš program a `-u` používat vstupně-výstupní operace bez vyrovnávací paměti. IronPython uživatelé můžou toto pole použít k předání `-X` možnosti, jako například `-X:Frames` nebo `-X:MTA`. |
| **Cesta k interpretu** | Přepíše cestu spojené s aktuálním prostředí. Hodnota může být užitečné při spouštění skriptu nestandardní překladač. |
| **Proměnné prostředí** | V tomto poli víceřádkový text, přidat položky ve formuláři \<NAME > =\<hodnota >. Protože toto nastavení je použito jako poslední, v horní části všechny existující globálních proměnných prostředí a po `PYTHONPATH` byla nastavena podle **cesty pro hledání** nastavení, to umožňuje ručně přepsat něco z toho jiné proměnné. |

## <a name="immediate-and-interactive-windows"></a>Okamžité a interaktivní okna

Existují dva interaktivních oken, můžete použít během relace ladění: standardní sady Visual Studio **okamžité** okně a **interaktivní ladění Pythonu** okna.

**Okamžité** okno (**ladění** > **Windows** > **okamžité**) se používá pro rychlé vyhodnocení Výrazy Pythonu a kontroly nebo přiřazení proměnných v běžící aplikaci. Zobrazit obecné [podokna](../ide/reference/immediate-window.md) , kde najdete podrobnosti.

**Interaktivní ladění Pythonu** okno (**ladění** > **Windows** > **interaktivní ladění Pythonu**) je bohatší tak kompletní [interaktivní okno REPL](python-interactive-repl-in-visual-studio.md) dojde k dispozici při ladění, včetně psaní a spouštění kódu. Automaticky připojí k jakékoli proces spuštěný v ladicím programu pomocí Spouštěč standardní Pythonu (včetně procesů připojená prostřednictvím **ladění** > **připojit k procesu**). Není, ale k dispozici při ladění ve smíšeném režimu C/C++.

![Ladění interaktivní okno Pythonu](media/debugging-interactive.png)

**Interaktivní ladění** okna podporuje speciální meta příkazy kromě [standardní příkazy REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Příkaz | Arguments | Popis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Spustí se program od aktuálního příkazu. |
| `$down`, `$d` | Posune aktuální rámec o jednu úroveň dolů v trasování zásobníku. |
| `$frame` | | Zobrazí aktuální id rámce.
| `$frame` | id rámce | Přepne aktuální rámec na zadané id rámce.
| `$load` | Načte příkazy ze souboru a spustí, až do dokončení |
| `$proc` |  | Zobrazí aktuální id procesu. |
| `$proc` | id procesu | Přepne aktuální proces na id určeného procesu. |
| `$procs` | | Vypíše procesy, které jsou právě laděny. |
| `$stepin`, `$step`, `$s` | Kroky v dalším volání funkce, pokud je to možné. |
| `$stepout`, `$return`, `$r` | Vystoupí z aktuální funkce. |
| `$stepover`, `$until`, `$unt` | Překročí volání další funkce. |
| `$thread` | | Zobrazí aktuální id vlákna. |
| `$thread` | id vlákna | Přepne aktuální vlákno na id zadaného vlákna. |
| `$threads` | | Vypíše vlákna, která se právě ladí. |
| `$up`, `$u` | | Posune aktuální rámec o jednu úroveň v trasování zásobníku. |
| `$where`, `$w`, `$bt` | Vypíše rámce aktuálního vlákna. |

Všimněte si, že standardní okna ladicího programu, jako například **procesy**, **vlákna**, a **zásobník volání** nejsou synchronizované s **interaktivní ladění** okna. Změna aktivního procesu, vlákna nebo snímek **interaktivní ladění** okno nemá vliv na ostatní okna ladicího programu. Naopak Změna aktivního procesu, vlákna nebo v jiných oknech ladicího programu snímků nemá vliv **interaktivní ladění** okna.

**Interaktivní ladění** okno má vlastní sadu možností, které můžete přistupovat prostřednictvím **nástroje** > **možnosti**  >   **Nástroje Python Tools** > **interaktivní okno ladění**. Na rozdíl od standardní **interaktivní Python** okna, která má samostatné instance pro každé prostředí Pythonu, existuje pouze jeden **interaktivní ladění** okna a vždy používá překladač Pythonu pro proces je laděn. Zobrazit [možnosti – možnosti ladění](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Interaktivní okno Možnosti ladění](media/debugging-interactive-options.png)

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Používání starší verze ladicího programu

Visual Studio 2017 verze 15,8 a novější použijte ladicí program založené na verzi ptvsd verze 4.1 a vyšší. Tuto verzi ptvsd je kompatibilní s Python 2.7 nebo Python 3.5 +. Pokud používáte Python 2.6, 3.1 3.4 nebo Ironpythonu, Visual Studio zobrazí chybu, **ladicí program nepodporuje toto prostředí Python**:

![Ladicí program nepodporuje tuto chybu prostředí Pythonu při použití ladicího programu](media/debugging-experimental-incompatible-error.png)

V těchto případech je nutné použít starší ladicí program (což je výchozí hodnotou v sadě Visual Studio 2017 verze 15.7 a starší). Vyberte **nástroje** > **možnosti** nabídky příkazu, přejděte na **Python** > **ladění**a vyberte **pomocí starší verze ladicího programu** možnost.

Pokud si nainstalujete starší verzi ptvsd v aktuálním prostředí (například ze starší verze 4.0.x nebo 3.x verze požadovaná pro vzdálené ladění), Visual Studio může zobrazit chybu nebo upozornění.

Chyba, **balíčků ladicího programu se nepovedlo načíst**, se zobrazí, když si nainstalujete ptvsd 3.x:

![Ladicí program balíček nelze načíst chyby při používání ladicího programu](media/debugging-experimental-version-error.png)

V tomto případě vyberte **pomocí starší verze ladicího programu** nastavit **pomocí starší verze ladicího programu** možnost a restartování ladicího programu.

Toto upozornění **ladicí program balíček je zastaralý**, se zobrazí, když jste nainstalovali dřívější verzi ptvsd 4.x:

![Ladicí program balíček je zastaralý, upozornění, když pomocí ladicího programu](media/debugging-experimental-version-warning.png)

> [!Important]
> I když se můžete rozhodnout ignorovat upozornění pro některé verzi ptvsd, Visual Studio nemusí fungovat správně.

Ke správě vaší instalace ptvsd:

1. Přejděte **balíčky** kartu **prostředí Pythonu** okna.

1. Do vyhledávacího pole zadejte "ptvsd" a zkontrolujte nainstalovanou verzi ptvsd:

    ![Kontrola verzi ptvsd v okně prostředí Pythonu](media/debugging-experimental-check-ptvsd.png)

1. Pokud je verze nižší než 4.1.1a9 (verze součástí sady Visual Studio), vyberte **X** napravo od balíček odinstalovat starší verzi. Visual Studio použije jeho jako součást balíčku verze. (Můžete odinstalovat i z Powershellu pomocí `pip uninstall ptvsd`.)

1. Alternativně můžete aktualizovat balíček ptvsd jeho nejnovější verzi podle pokynů v [Poradce při potížích s](#troubleshooting) oddílu.

## <a name="troubleshooting"></a>Poradce při potížích

Pokud máte problémy s ladicím programem, nejprve následujícím způsobem upgradujte verzi ptvsd:

1. Přejděte **balíčky** kartu **prostředí Pythonu** okna.

1. Zadejte `ptvsd --upgrade` do vyhledávacího pole, vyberte **spusťte příkaz: pip nainstalujte ptvsd--upgrade**. (Můžete také použít stejný příkaz z Powershellu.)

    ![Poskytuje příkaz pro upgrade ptvsd v okně prostředí Pythonu](media/debugging-experimental-upgrade-ptvsd.png)

Pokud problémy přetrvávají, založte prosím problém na [úložiště PTVS GitHub](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Povolit protokolování ladicího programu

Při zkoumání problému s ladicího programu, Microsoft vás může požádat o povolení a shromažďovat protokoly ladicího programu, které pomáhají s diagnostikou.

Následujícím postupem povolíte ladění v aktuální relaci aplikace Visual Studio:

1. Otevřete okno příkazového řádku v sadě Visual Studio pomocí **zobrazení** > **ostatní Windows** > **příkazové okno** příkazu nabídky.

1. Zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Spustit ladění a projít jakýchkoli kroků je potřebné k reprodukci problému. Během této doby, protokoly ladění joinkind **výstup** okně v části **protokol hostitele adaptéru ladění**. Pak můžete zkopírovat protokoly z tohoto okna a vložte do problém Githubu, e-mail atd.

    ![Ladicího programu uložit výstup protokolování v okně Výstup](media/debugger-logging-output.png)

1. Pokud Visual Studio přestane reagovat nebo nejste jinak mít přístup **výstup** restartujte sadu Visual Studio, otevřete okno příkazového řádku a zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Spustit ladění a problém reprodukovat. znovu. Ladicí program protokoly pak najdete v `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Viz také:

Kompletní informace o ladicím programu sady Visual Studio, naleznete v tématu [ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md).
