---
title: Ladění kódu v Pythonu
description: Visual Studio poskytují bohatá podpora ladění pro kód Python, včetně nastavení zarážek, krokování, kontrolu hodnoty, prohlížení výjimek a ladění v interaktivním okně.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4678e3508c16b38fec2a10cdeb79bc499eaf15fd
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409947"
---
# <a name="debug-your-python-code"></a>Ladění kódu Pythonu

Sada Visual Studio poskytuje komplexní ladicí prostředí pro Python, včetně připojení ke spuštěným procesům, vyhodnocování výrazů v okně **kukátko** a **bezprostředních** oknech, kontrolu místních proměnných, zarážek, krokování/převzetí/převzetí příkazů, **nastavení dalšího příkazu**a další.

Také naleznete v následujících článcích ladění specifické pro scénář:

- [Vzdálené ladění pro Linux](debugging-python-code-on-remote-linux-machines.md)
- [Python/C++ ladění ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symboly pro ladění ve smíšeném režimu](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python v sadě Visual Studio podporuje ladění bez projektu. Po otevření samostatného souboru Pythonu klikněte v editoru pravým tlačítkem myši, vyberte **Spustit s laděním**a Visual Studio spustí skript s globálním výchozím prostředím (viz [prostředí Python](managing-python-environments-in-visual-studio.md)) a žádné argumenty. Ale od té chvíle má úplnou podporu ladění.
>
> Chcete-li řídit prostředí a argumenty, vytvořte projekt pro kód, který lze snadno provést pomocí existující šablony projektu [kódu Pythonu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) .

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Základní ladění

Základní ladicí pracovní postup zahrnuje nastavení zarážek, krokování kódem, kontrolu hodnoty a zpracování výjimek, jak je popsáno v následujících částech.

Relace ladění začíná příkazem **ladění** > **Spustit ladění** , tlačítkem **Start** na panelu nástrojů nebo klávesou **F5** . Tyto akce spustí spouštěcí soubor projektu (zobrazený tučně v **Průzkumník řešení**) s aktivním prostředím projektu a libovolnými argumenty příkazového řádku nebo vyhledávacími cestami, které byly zadány ve **vlastnostech projektu** (viz [možnosti ladění projektu](#project-debugging-options)). Sada Visual Studio 2017 verze 15,6 a novější vás upozorní, pokud nemáte nastaven spouštěcí soubor. starší verze můžou otevřít okno výstup se spuštěným překladačem Pythonu, jinak se okno výstup krátce zobrazí a zmizí. V každém případě klikněte pravým tlačítkem na příslušný soubor a vyberte **nastavit jako spouštěcí soubor**.

> [!Note]
> Ladicí program vždy začíná na aktivní prostředí projektu Pythonu. Chcete-li změnit prostředí, vytvořte jinou aktivní, jak je popsáno v tématu [Výběr prostředí Python pro projekt](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Zarážky

Zarážky zastaví provádění kódu označenou okamžiku tak můžete kontrolovat stav programu. Nastavte zarážky kliknutím na levý okraj editoru kódu nebo kliknutím pravým tlačítkem myši na řádek kódu a výběrem **zarážky** > **Vložit zarážku**. Na každém řádku s zarážky, zobrazí se červená tečka.

![Zarážky v sadě Visual Studio](media/debugging-breakpoints.png)

Kliknutím na červenou tečku nebo kliknutím pravým tlačítkem myši na řádek kódu a výběrem **zarážky** > **Odstranit** zarážku odeberete zarážku. Můžete ji také zakázat, aniž byste ji odebrali pomocí příkazu **zarážky** > **Zakázat zarážku** .

> [!Note]
> Některé zarážky v jazyce Python se dá překvapivé pro vývojáře, kteří pracovali s jinými programovací jazyky. V jazyce Python je celý soubor spustitelného kódu, takže Python spustí soubor je načtena na zpracování jakékoli třídy nejvyšší úrovně nebo definice funkcí. Pokud byla nastavena na zarážku, můžete zjistit ladicí program zásadní součástí – způsob, jak prostřednictvím deklarace třídy. Toto chování je správná, i když je někdy překvapivé.

Můžete přizpůsobit podmínky, za kterých se aktivuje zarážky, jako je zastavení jenom v případě, že proměnná je nastavena na hodnotu nebo rozsah hodnot. Pokud chcete nastavit podmínky, klikněte pravým tlačítkem myši na červenou tečku zarážky, vyberte **Podmínka**a pak vytvořte výrazy pomocí kódu Pythonu. Úplné podrobnosti o této funkci v aplikaci Visual Studio naleznete v tématu [podmínky zarážky](../debugger/using-breakpoints.md#breakpoint-conditions).

Při nastavování podmínek můžete také nastavit **akci** a vytvořit zprávu pro protokolování do okna výstup, volitelně pokračovat v provádění automaticky. Protokolování zprávy vytvoří, co se říká *zarážka s trasováním* bez přidání kódu protokolování do aplikace přímo:

![Vytváření zarážku s trasováním s zarážku](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Krokovat kód

Po zastavení na zarážce, budete mít různé způsoby, jak procházet kód nebo spuštění bloků kódu před dopadem na dřívější kód znovu. Tyto příkazy jsou k dispozici na mnoha místech, včetně panelu nástrojů pro ladění, nabídky **ladění** , v kontextové nabídce pravého tlačítka myši v editoru kódu a prostřednictvím klávesových zkratek (i když nejsou všechny příkazy umístěny na všech místech):

| Funkce | Stisknutí kláves | Popis |
| --- | --- | --- |
| **Continue** | **Stisknutím** | Spouští kód, dokud nebude dosaženo k další zarážce. |
| **Krokovat s vnořením** | **Kláves** | Následující příkaz spustí a zastaví. Pokud je volání funkce další příkaz, ladicí program se zastaví na prvním řádku volané funkce. |
| **Krokovat** | **F10** | Spustí další příkaz, včetně volání na funkci (s jeho kód) a použití jakékoli návratovou hodnotu. Krokování přes umožňuje snadno přeskočit funkce, které není potřeba ladění. |
| **Krok ven** | **Shift**+**F11** | Spustí kód do konce aktuální funkci a pak kroky volání příkazu.  Tento příkaz je užitečné, když není nutné ladit zbytek aktuální funkce. |
| **Spustit ke kurzoru** | **Ctrl**+**F10** | Spustí kód do umístění blikající kurzor v editoru. Tento příkaz umožňuje snadno přeskočit část kódu, který není nutné k ladění. |
| **Nastavení dalšího příkazu** | **Ctrl**+**SHIFT**+**F10** | Změny aktuálního spuštění bodu do umístění blikajícího kurzoru v kódu. Tento příkaz umožňuje vynechat segment kódu na všech spuštění, jako když víte, kód je chybný nebo je výsledný nežádoucí vedlejší efekt. |
| **Zobrazit další příkaz** | **Alt**+**číslo** **&#42;**| Vrátíte se do dalšího příkazu ke spuštění. Tento příkaz je užitečné, pokud jste hledání ve vašem kódu a nepamatujete, kde je zastavený ladicím programu. |

### <a name="inspect-and-modify-values"></a>Kontrola a změny hodnot

Při zastavení v ladicím programu, můžete zkontrolovat a změnit hodnoty proměnných. Okno **kukátka** můžete také použít k monitorování jednotlivých proměnných i vlastních výrazů. (Další informace najdete v tématu [Kontrola proměnných](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) .)

Chcete-li zobrazit hodnotu pomocí datových **tipů**, Stačí umístit ukazatel myši na libovolnou proměnnou v editoru. Můžete kliknout na hodnotu a změňte ji:

![DataTips zobrazující v ladicím programu sady Visual Studio](media/debugging-quick-tips.png)

Okno **Automatické** hodnoty (**ladění** > **Automatické**sady **Windows** > ) obsahuje proměnné a výrazy, které se blíží aktuálnímu příkazu. Můžete dvakrát kliknout ve sloupci hodnota nebo vybrat a stisknout **F2** pro úpravu hodnoty:

![Okno Automatické hodnoty v ladicím programu sady Visual Studio](media/debugging-autos-window.png)

Okno **místní** hodnoty (**ladění** > **lokálních**hodnot **Windows** > ) zobrazí všechny proměnné, které jsou v aktuálním oboru, které se dají znovu upravit:

![Okno místních hodnot v ladicím programu sady Visual Studio](media/debugging-locals-window.png)

Další informace o používání **automatických** funkcí a **místních**hodnot najdete v tématu [Kontrola proměnných v oknech automatické hodnoty a místní](../debugger/autos-and-locals-windows.md)hodnoty.

Okna **kukátka** (**ladění** > **Windows** > **kukátko** > **sledování 1-4**) umožňují zadat libovolné výrazy Pythonu a zobrazit výsledky. Výrazy jsou již znovu pro každý krok:

![Podívejte se na okno v ladicím programu sady Visual Studio](media/debugging-watch-window.png)

Další informace o používání **sledování**najdete v tématu [Nastavení sledování proměnných pomocí oken kukátka a QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Když kontrolujete řetězcovou hodnotu (`str`, `unicode`, `bytes`a `bytearray` jsou pro tento účel považovány za řetězce), zobrazí se na pravé straně hodnoty ikona lupy. Kliknutím na ikonu se zobrazí hodnota řetězec bez uvozovek v dialogovém okně automaticky otevírané okno s zabalení a posouvání, což je užitečné pro dlouhé řetězce. Kromě toho na tlačítko se šipkou rozevíracího seznamu na ikonu vám umožní vybrat prostý text, HTML, XML a JSON vizualizace:

![Řetězec vizualizéry v ladicím programu sady Visual Studio](media/debugging-string-visualizers.png)

HTML, XML a JSON vizualizace zobrazí ve windows samostatné automaticky otevírané okno se zobrazeními zvýrazňování a stromu syntaxe.

### <a name="exceptions"></a>Výjimky

Pokud dojde k chybě ve svém programu během ladění, ale pro něj nemáte obslužnou rutinu výjimky, ladicí program přeruší místě výjimku:

![Automaticky otevírané okno výjimky v ladicím programu sady Visual Studio](media/debugging-exception-popup.png)

V tomto okamžiku můžete kontrolovat stav programu, včetně zásobníku volání. Ale pokud se pokusíte krokovat kód, výjimka dál vyvolávána, dokud se buď zpracovává nebo ukončení programu.

Příkaz nabídky **Nastavení výjimek** >  > **Windows** pro **ladění** zobrazí okno, ve kterém můžete rozbalit **výjimky Pythonu**:

![Okno výjimky v ladicím programu sady Visual Studio](media/debugging-exception-settings.png)

Zaškrtávací políčko pro každou výjimku určuje, zda ladicí program *vždy* při vyvolání dojde k přerušení. Toto políčko zaškrtněte, pokud chcete přerušit častěji pro určité výjimky.

Ve výchozím nastavení většina výjimek přerušit, pokud obslužná rutina výjimky nebyl nalezen ve zdrojovém kódu. Chcete-li toto chování změnit, klikněte pravým tlačítkem myši na libovolnou výjimku a změňte možnost **pokračovat, pokud není zpracována v uživatelském kódu** . Zaškrtnutí tohoto políčka zrušte, pokud chcete přerušit méně často pro výjimku.

Chcete-li konfigurovat výjimku, která se v tomto seznamu nezobrazí, klikněte na tlačítko **Přidat** a přidejte ji. Název musí odpovídat názvu výjimky.

## <a name="project-debugging-options"></a>Možnosti ladění projektu

Ve výchozím nastavení spustí ladicí program programu pomocí standardní Spouštěč Pythonu, bez argumentů příkazového řádku a žádné jiné speciální cesty nebo podmínky. Možnosti spuštění jsou změněny prostřednictvím vlastností ladění projektu, které jsou k dispozici, kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení**, výběrem **vlastností**a výběrem karty **ladění** .

![Vlastnosti ladění projektu v ladicím programu sady Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Možnosti režimu spuštění

| Možnost | Popis |
| --- | --- |
| **Standardní spouštěč Pythonu** | Použití ladění kódu napsaného v přenosných Pythonu, který je kompatibilní s CPython, IronPython a variant, jako jsou Stackless Python. Poskytuje nejlepší prostředí pro ladění čistého kódu v Pythonu. Když se připojíte k běžícímu procesu *Python. exe* , použije se tato spouštěcí služba. Tato spouštěč taky poskytuje [ladění ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) pro CPython, což vám umožní plynule krokovat mezi kódem CC++ /kódem a kódem Pythonu. |
| **Webový spouštěč** | Spustí výchozí prohlížeč při spuštění a povolí ladění šablon. Další informace najdete v části [ladění webové šablony](python-web-application-project-templates.md#debugging) . |
| **Webový spouštěč Django** | Stejné jako webový Spouštěč a zobrazuje pouze pro zpětnou kompatibilitu. |
| **Spouštěč Ironpythonu (.NET)** | Používá ladicí program .NET, která funguje jenom v Ironpythonu, ale umožňuje krokování mezi jakéhokoli projektu .NET jazyka, včetně C# a VB. Tento program se používá, pokud je připojit ke spuštěnému procesu .NET, který je hostitelem Ironpythonu. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Možností spuštění (cesty pro hledání, argumenty pro spuštění a proměnných prostředí)

| Možnost | Popis |
| --- | --- |
| **Cesty pro hledání** | Tyto hodnoty se shodují s tím, co se zobrazuje v uzlu **cesty hledání** projektu v **Průzkumník řešení**. Tuto hodnotu můžete upravit zde, ale je snazší použít **Průzkumník řešení** , která umožňuje procházet složky a automaticky převádět cesty k relativnímu formuláři. |
| **Argumenty skriptu** | Tyto argumenty jsou přidány do příkaz použitý ke spuštění skriptu, vyskytující se po název souboru vašeho skriptu. První položka je k dispozici pro váš skript jako `sys.argv[1]`, druhý jako `sys.argv[2]`atd. |
| **Argumenty interpretu** | Tyto argumenty jsou přidány do příkazového řádku Spouštěč před název vašeho skriptu. Sem patří běžné argumenty, které se `-W ...` k řízení upozornění, `-O` pro mírné optimalizaci programu a `-u` používání neuložených vstupně-výstupních operací. Ironpythonu uživatelé mohou použít toto pole k předání `-X` možností, jako je například `-X:Frames` nebo `-X:MTA`. |
| **Cesta k interpretu** | Přepíše cestu spojené s aktuálním prostředí. Hodnota může být užitečné při spouštění skriptu nestandardní překladač. |
| **Proměnné prostředí** | Do tohoto víceřádkového textového pole přidejte položky \<název > =\<VALUE >. Vzhledem k tomu, že toto nastavení bylo použito jako poslední, nad všemi existujícími globálními proměnnými prostředí a po `PYTHONPATH` nastaveno podle nastavení **cest hledání** , lze použít k ručnímu přepsání kterékoli z těchto ostatních proměnných. |

## <a name="immediate-and-interactive-windows"></a>Okamžité a interaktivní okna

Existují dva interaktivní systémy Windows, které můžete použít během relace ladění: **standardní okno aplikace Visual Studio a** **interaktivní okno ladění Pythonu** .

**Příkazové** **okno ( > ** ** > ** **okamžité**) se používá pro rychlé vyhodnocení výrazů Pythonu a kontrolu nebo přiřazení proměnných v rámci běžícího programu. Podrobnosti najdete v článku o [okamžitém okně](../ide/reference/immediate-window.md) .

**Interaktivní okno ladění Pythonu** (**ladění** > **Windows** > **Python Interactive**) je bohatší, protože zpřístupňuje plné [interaktivní REPL](python-interactive-repl-in-visual-studio.md) prostředí při ladění, včetně psaní a spouštění kódu. Automaticky se připojí k jakémukoli procesu spuštěnému v ladicím programu pomocí standardní spouštěče Pythonu (včetně procesů připojených prostřednictvím **ladění** > **připojit k procesu**). Není, ale k dispozici při ladění ve smíšeném režimu C/C++.

![Ladění interaktivní okno Pythonu](media/debugging-interactive.png)

**Interaktivní okno ladění** podporuje kromě [standardních příkazů REPL](python-interactive-repl-in-visual-studio.md#meta-commands)speciální meta příkazy:

| Příkaz | Argumenty | Popis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Spustí se program od aktuálního příkazu. |
| `$down`, `$d` | Posune aktuální rámec o jednu úroveň dolů v trasování zásobníku. |
| `$frame` | | Zobrazí aktuální ID rámce.
| `$frame` | ID rámce | Přepne aktuální rámec na zadané ID rámce.
| `$load` | Načte příkazy ze souboru a spustí, až do dokončení |
| `$proc` |  | Zobrazí aktuální ID procesu. |
| `$proc` | ID procesu | Přepne aktuální proces na zadané ID procesu. |
| `$procs` | | Vypíše procesy, které jsou právě laděny. |
| `$stepin`, `$step`, `$s` | Kroky v dalším volání funkce, pokud je to možné. |
| `$stepout`, `$return`, `$r` | Vystoupí z aktuální funkce. |
| `$stepover`, `$until`, `$unt` | Překročí volání další funkce. |
| `$thread` | | Zobrazí aktuální ID vlákna. |
| `$thread` | ID vlákna | Přepne aktuální vlákno na zadané ID vlákna. |
| `$threads` | | Vypíše vlákna, která se právě ladí. |
| `$up`, `$u` | | Posune aktuální rámec o jednu úroveň v trasování zásobníku. |
| `$where`, `$w`, `$bt` | Vypíše rámce aktuálního vlákna. |

Všimněte si, že standardní okna ladicího programu, například **procesy**, **vlákna**a **zásobník volání** , nejsou synchronizována s **interaktivním oknem ladění** . Změna aktivního procesu, vlákna nebo snímku v **interaktivním okně ladění** nemá vliv na ostatní okna ladicího programu. Podobně Změna aktivního procesu, vlákna nebo snímku v ostatních oknech ladicího programu nemá vliv na **interaktivní okno ladění** .

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Používání starší verze ladicího programu

Visual Studio 2017 verze 15,8 a novější použijte ladicí program založené na verzi ptvsd verze 4.1 a vyšší. Tuto verzi ptvsd je kompatibilní s Python 2.7 nebo Python 3.5 +. Pokud používáte Python 2,6, 3,1 až 3,4 nebo Ironpythonu, Visual Studio zobrazí chybu, **ladicí program nepodporuje toto prostředí Pythonu**:

![Ladicí program nepodporuje tuto chybu prostředí Pythonu při použití ladicího programu](media/debugging-experimental-incompatible-error.png)

V těchto případech je nutné použít starší ladicí program (což je výchozí hodnotou v sadě Visual Studio 2017 verze 15.7 a starší). Vyberte příkaz nabídky **nástroje** > **Možnosti** , přejděte na **Python** > **ladění**a vyberte možnost **použít starší verzi ladicího programu** .

Pokud si nainstalujete starší verzi ptvsd v aktuálním prostředí (například ze starší verze 4.0.x nebo 3.x verze požadovaná pro vzdálené ladění), Visual Studio může zobrazit chybu nebo upozornění.

Chyba, **balíček ladicího programu se nepovedlo načíst**, po instalaci ptvsd 3. x se zobrazí:

![Ladicí program balíček nelze načíst chyby při používání ladicího programu](media/debugging-experimental-version-error.png)

V takovém případě vyberte **použít starší verzi ladicího programu** k nastavení možnosti **použít starší verzi ladicího** programu a znovu spusťte ladicí program.

Upozornění, **balíček ladicího programu je zastaralá**, zobrazí se, když jste nainstalovali starší verzi 4. x ptvsd:

![Ladicí program balíček je zastaralý, upozornění, když pomocí ladicího programu](media/debugging-experimental-version-warning.png)

> [!Important]
> I když se můžete rozhodnout ignorovat upozornění pro některé verzi ptvsd, Visual Studio nemusí fungovat správně.

Ke správě vaší instalace ptvsd:

1. Přejděte na kartu **balíčky** v okně **prostředí Pythonu** .

1. Do vyhledávacího pole zadejte "ptvsd" a zkontrolujte nainstalovanou verzi ptvsd:

    ![Kontrola verzi ptvsd v okně prostředí Pythonu](media/debugging-experimental-check-ptvsd.png)

1. Pokud je verze nižší než 4.1.1 (verze sady Visual Studio), vyberte **X** napravo od balíčku pro odinstalaci starší verze. Visual Studio použije jeho jako součást balíčku verze. (Můžete také z PowerShellu odinstalovat pomocí `pip uninstall ptvsd`.)

1. Alternativně můžete balíček ptvsd aktualizovat na jeho nejnovější verzi, a to podle pokynů uvedených v části [řešení potíží](#troubleshooting) .

## <a name="troubleshooting"></a>Řešení potíží

Pokud máte problémy s ladicím programem, nejprve následujícím způsobem upgradujte verzi ptvsd:

1. Přejděte na kartu **balíčky** v okně **prostředí Pythonu** .

1. Do vyhledávacího pole zadejte `ptvsd --upgrade` a pak vyberte **Spustit příkaz: PIP Install ptvsd--upgrade**. (Můžete také použít stejný příkaz z Powershellu.)

    ![Poskytuje příkaz pro upgrade ptvsd v okně prostředí Pythonu](media/debugging-experimental-upgrade-ptvsd.png)

Pokud potíže potrvají, uveďte problém v [úložišti GitHubu PTVS](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Povolit protokolování ladicího programu

Při zkoumání problému s ladicího programu, Microsoft vás může požádat o povolení a shromažďovat protokoly ladicího programu, které pomáhají s diagnostikou.

Následujícím postupem povolíte ladění v aktuální relaci aplikace Visual Studio:

1. Otevřete okno příkazového řádku v aplikaci Visual Studio pomocí příkazu **zobrazit** > jiné > **příkazového** řádku nabídky **Windows** .

1. Zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Spustit ladění a projít jakýchkoli kroků je potřebné k reprodukci problému. Během této doby se protokoly ladění zobrazí v okně **výstup** v části **protokol hostitele adaptéru ladění**. Pak můžete zkopírovat protokoly z tohoto okna a vložte do problém Githubu, e-mail atd.

    ![Ladicího programu uložit výstup protokolování v okně Výstup](media/debugger-logging-output.png)

1. Pokud Visual Studio přestane reagovat nebo jste jinak nedokázali získat přístup k oknu **výstup** , restartujte Visual Studio, otevřete příkazové okno a zadejte tento příkaz:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Spustit ladění a problém reprodukovat. znovu. Protokoly ladicího programu se pak dají najít v `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Viz také

Úplné podrobnosti o ladicím programu sady Visual Studio naleznete [v tématu ladění v aplikaci Visual Studio](../debugger/debugger-feature-tour.md).
