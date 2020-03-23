---
title: Ladění kódu Pythonu
description: Visual Studio poskytují bohaté ladění kódu Pythonu, včetně nastavení zarážek, krokování, kontrola hodnot, při pohledu na výjimky a ladění v interaktivním okně.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302887"
---
# <a name="debug-your-python-code"></a>Ladění kódu Pythonu

Visual Studio poskytuje komplexní ladění prostředí pro Python, včetně připojení k běžící procesy, vyhodnocení výrazy v **watch** a **okamžité** okna, kontrola místníproměnné, zarážky, krok dovnitř/ven/přes příkazy, **Set Next Statement**a další.

Viz také následující články ladění specifické pro scénář:

- [Vzdálené ladění Linuxu](debugging-python-code-on-remote-linux-machines.md)
- [Ladění pythonu/C++ ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symboly pro ladění ve smíšeném režimu](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python v sadě Visual Studio podporuje ladění bez projektu. Při otevřeném samostatném souboru Pythonu klikněte pravým tlačítkem myši do editoru, vyberte **Začít s laděním**a Visual Studio spustí skript s globálním výchozím prostředím (viz [prostředí Pythonu)](managing-python-environments-in-visual-studio.md)a bez argumentů. Ale od té doby máte plnou podporu ladění.
>
> Chcete-li řídit prostředí a argumenty, vytvořte projekt pro kód, který lze snadno provést pomocí šablony projektu [existujícího kódu Pythonu.](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files)

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Základní ladění

Základní pracovní postup ladění zahrnuje zarážky nastavení, krokování kódu, kontrolu hodnot a zpracování výjimek, jak je popsáno v následujících částech.

Relace ladění začíná příkazem **Ladění** > **spouštět ladění,** tlačítkem **Start** na panelu nástrojů nebo klávesou **F5.** Tyto akce spustí spouštěcí soubor projektu (zobrazený tučně v **Průzkumníku řešení**) s aktivním prostředím projektu a všemi argumenty příkazového řádku nebo cestami hledání, které byly zadány v **části Vlastnosti projektu** (viz [Možnosti ladění projektu](#project-debugging-options)). Visual Studio 2017 verze 15.6 a novější vás upozorní, pokud nemáte nastavený spouštěcí soubor; starší verze mohou otevřít výstupní okno se spuštěným překladačem Pythonu nebo se krátce zobrazí a zmizí výstupní okno. V každém případě klepněte pravým tlačítkem myši na příslušný soubor a vyberte **příkaz Nastavit jako spouštěcí soubor**.

> [!Note]
> Ladicí program vždy začíná aktivním prostředím Pythonu pro projekt. Chcete-li změnit prostředí, vytvořte jiný aktivní, jak je popsáno v [aplikaci Select a Python environment for a project](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Zarážky

Zarážky zastavit provádění kódu v označeném bodě, takže můžete zkontrolovat stav programu. Nastavte zarážky klepnutím na levý okraj editoru kódu nebo kliknutím pravým tlačítkem myši na řádek kódu a výběrem **zarážky** > **vložení zarážky zarážky**. Na každém řádku s zarážkou se zobrazí červená tečka.

![Zarážky, které se zobrazují v sadě Visual Studio](media/debugging-breakpoints.png)

Kliknutím na červenou tečku nebo kliknutím pravým tlačítkem myši na řádek kódu a výběrem **příkazu** > **Odstranit zarážku** se zarážka odebere. Můžete jej také zakázat bez jeho odebrání pomocí příkazu > **Zakácení zakázat zarážku.** **Breakpoint**

> [!Note]
> Některé zarážky v Pythonu mohou být překvapivé pro vývojáře, kteří pracovali s jinými programovacími jazyky. V Pythonu je celý soubor spustitelný kód, takže Python spustí soubor, když se načte, aby zpracoval všechny definice třídy nebo funkce nejvyšší úrovně. Pokud byla nastavena zarážka, můžete najít ladicí program rozdělení části prostřednictvím deklarace třídy. Toto chování je správné, i když je to někdy překvapující.

Můžete přizpůsobit podmínky, za kterých je aktivována zarážka, jako je například rozdělení pouze v případě, že proměnná je nastavena na určitou hodnotu nebo rozsah hodnot. Chcete-li nastavit podmínky, klepněte pravým tlačítkem myši na červenou tečku zarážky, vyberte **možnost Podmínka**a vytvořte výrazy pomocí kódu Pythonu. Úplné podrobnosti o této funkci v sadě Visual Studio naleznete v tématu [Podmínky zarážky](../debugger/using-breakpoints.md#breakpoint-conditions).

Při nastavování podmínek můžete také nastavit **akci** a vytvořit zprávu pro přihlášení do výstupního okna, volitelně automaticky pokračovat v provádění. Protokolování zprávy vytvoří to, co se nazývá *trasovací bod* bez přidání kódu protokolování do aplikace přímo:

![Vytvoření trasovacího bodu s zarážkou](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Krokovat kódem

Po zastavení na zarážky, máte různé způsoby, jak krokovat kód nebo spustit bloky kódu před přerušením znovu. Tyto příkazy jsou k dispozici na mnoha místech, včetně horního panelu nástrojů ladění, nabídky **Ladění,** v kontextové nabídce pravým tlačítkem myši v editoru kódu a pomocí klávesových zkratek (i když ne všechny příkazy jsou na všech místech):

| Funkce | Stisknutí klávesy | Popis |
| --- | --- | --- |
| **Pokračovat** | **F5** | Spustí kód, dokud není dosaženo další zarážky. |
| **Krok do** | **F11** | Spustí další příkaz a zastaví. Pokud další příkaz je volání funkce, ladicí program se zastaví na prvním řádku funkce, která je volána. |
| **Krok přes** | **F10** | Spustí další příkaz, včetně volání funkce (spuštění všech jeho kódu) a použití libovolné vrácené hodnoty. Krokování umožňuje snadno přeskočit funkce, které není nutné ladit. |
| **Krok ven** | **Posun**+**F11** | Spustí kód až do konce aktuální funkce a potom provede kroky k příkazu pro volání.  Tento příkaz je užitečný, pokud nepotřebujete ladit zbytek aktuální funkce. |
| **Spustit na kurzor** | **Ctrl**+**F10** | Spustí kód až do umístění stříšky v editoru. Tento příkaz umožňuje snadno přeskočit segment kódu, který není nutné ladit. |
| **Nastavit další příkaz** | **Ctrl**+**Shift**+**F10** | Změní aktuální bod spuštění v kódu na umístění stříšky. Tento příkaz umožňuje vynechat segment kódu ze spuštění vůbec, například když víte, že kód je vadný nebo vytváří nežádoucí vedlejší účinek. |
| **Zobrazit další příkaz** | **&#42;alternativního**+**pole** **&#42;**| Vrátí vás na další příkaz ke spuštění. Tento příkaz je užitečný, pokud jste se v kódu rozhlíželi a nepamatujete si, kde je ladicí program zastaven. |

### <a name="inspect-and-modify-values"></a>Kontrola a úprava hodnot

Po zastavení v ladicím programu můžete zkontrolovat a upravit hodnoty proměnných. Okno **Kukátko** můžete také použít ke sledování jednotlivých proměnných i vlastních výrazů. (Obecné podrobnosti naleznete v části [Kontrola proměnných.)](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows)

Chcete-li zobrazit hodnotu pomocí **datatips**, jednoduše najeďte myší na libovolnou proměnnou v editoru. Můžete kliknout na hodnotu změnit:

![Tipy pro data zobrazené v ladicím programu Sady Visual Studio](media/debugging-quick-tips.png)

Okno **Autos** (**Debug** > **Windows** > **Autos**) obsahuje proměnné a výrazy, které se blíží aktuálnímu příkazu. Můžete poklepat ve sloupci hodnoty nebo vybrat a stisknutím **klávesy F2** upravit hodnotu:

![Okno Autos v ladicím programu sady Visual Studio](media/debugging-autos-window.png)

V okně **Locals** **(Debug** > **Windows** > **Locals)** se zobrazí všechny proměnné, které jsou v aktuálním oboru a které lze znovu upravit:

![Místní okno v ladicím programu Visual Studio](media/debugging-locals-window.png)

Další informace o používání **autos** a **locals**najdete [v tématu Kontrola proměnných v oknech Autos a Locals](../debugger/autos-and-locals-windows.md).

**Okna Hodinek** **(Ladění** > **windows** > **watch** > **watch 1-4)** umožňují zadat libovolné výrazy Pythonu a zobrazit výsledky. Výrazy jsou přehodnoceny pro každý krok:

![Okno sledování v ladicím programu sady Visual Studio](media/debugging-watch-window.png)

Další informace o používání **hodinek**najdete [v tématu Nastavení hodinek na proměnných pomocí oken Watch a QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Při kontrole hodnoty`str`řetězce( `unicode` `bytes`, `bytearray` , , a jsou všechny považovány za řetězce pro tento účel), lupa ikona se zobrazí na pravé straně hodnoty. Kliknutím na ikonu se zobrazí nekotovaná hodnota řetězce v vyskakovacím dialogovém okně s obtékáním a posouváním, což je užitečné pro dlouhé řetězce. Kromě toho výběrem šipky rozevíracího seznamu na ikoně můžete vybrat vizualizace ve formátu prostého textu, HTML, XML a JSON:

![Vizualizéry řetězců v ladicím programu Visual Studio](media/debugging-string-visualizers.png)

Vizualizace HTML, XML a JSON se zobrazují v samostatných vyskakovacích oknech se zvýrazněním syntaxe a zobrazeními stromu.

### <a name="exceptions"></a>Výjimky

Pokud dojde k chybě v programu během ladění, ale nemáte obslužnou rutinu výjimky pro něj, ladicí program přestávky v bodě výjimky:

![Místní okno s výjimkou v ladicím programu sady Visual Studio](media/debugging-exception-popup.png)

V tomto okamžiku můžete zkontrolovat stav programu, včetně zásobníku volání. Pokud se však pokusíte krokovat kód, výjimka bude nadále vyvolána, dokud nebude zpracována nebo dokud program neukončí.

Příkaz Příkaz **Nastavení** > **výjimek** **ladění systému Windows** > vyvolá okno, ve kterém můžete rozbalit **výjimky pythonu**:

![Okno Výjimky v ladicím programu sady Visual Studio](media/debugging-exception-settings.png)

Zaškrtávací políčko pro každou výjimku určuje, zda ladicí program *vždy* přeruší, když je aktivována. Toto políčko zaškrtněte, pokud chcete přerušit častěji pro určitou výjimku.

Ve výchozím nastavení většina výjimek přeruší, když nelze nalézt obslužnou rutinu výjimky ve zdrojovém kódu. Chcete-li toto chování změnit, klepněte pravým tlačítkem myši na libovolnou výjimku a upravte možnost **Pokračovat při neošetřeném v uživatelském kódu.** Toto políčko zrušte, pokud chcete pro výjimku přerušit méně často.

Chcete-li nakonfigurovat výjimku, která se v tomto seznamu nezobrazuje, přidejte ji klepnutím na tlačítko **Přidat.** Název se musí shodovat s úplným názvem výjimky.

## <a name="project-debugging-options"></a>Možnosti ladění projektu

Ve výchozím nastavení ladicí program spustí program se standardním spouštěč Pythonu, žádné argumenty příkazového řádku a žádné jiné speciální cesty nebo podmínky. Možnosti spuštění se mění pomocí vlastností ladění projektu, ke kterým přistupujete klepnutím pravým tlačítkem myši na projekt v **Průzkumníku řešení**, výběrem **možnosti vlastností**a výběrem karty **Ladění.**

![Vlastnosti ladění projektu v ladicím programu sady Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Možnosti režimu spuštění

| Možnost | Popis |
| --- | --- |
| **Standardní spouštěč Pythonu** | Používá ladicí kód napsaný v přenosném Pythonu, který je kompatibilní s CPython, IronPython a variantami, jako je Stackless Python. Poskytuje nejlepší prostředí pro ladění čistého kódu Pythonu. Při připojení k běžícímu procesu *python.exe* se používá tento spouštěč. Tento spouštěč také poskytuje [ladění v kombinovaném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) pro CPython, což umožňuje bezproblémově krokovat mezi kódem C/C++ a kódem Pythonu. |
| **Spouštěč webových stránek** | Spustí výchozí prohlížeč při spuštění a povolí ladění šablon. Další informace naleznete v části [Ladění webové šablony.](python-web-application-project-templates.md#debugging) |
| **Spouštěč webu Django** | Shodné s webovým spouštěčem a zobrazeno pouze pro zpětnou kompatibilitu. |
| **Spouštěč IronPython (.NET)** | Používá ladicí program .NET, který funguje pouze s IronPython, ale umožňuje krokování mezi libovolným jazykovým projektem .NET, včetně C# a VB. Tento spouštěč se používá, pokud se připojíte ke spuštěnému procesu rozhraní .NET, který je hostitelem IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Možnosti spuštění (vyhledávací cesty, argumenty při spuštění a proměnné prostředí)

| Možnost | Popis |
| --- | --- |
| **Hledat cesty** | Tyto hodnoty odpovídají tomu, co je zobrazeno v uzlu **Cesty hledání** projektu v **Průzkumníku řešení**. Zde můžete tuto hodnotu upravit, ale je jednodušší použít **Průzkumníka řešení,** který umožňuje procházet složky a automaticky převádí cesty do relativního tvaru. |
| **Argumenty skriptu** | Tyto argumenty jsou přidány do příkazu použitého ke spuštění skriptu, který se zobrazí za názvem souboru skriptu. První položka je zde k `sys.argv[1]`dispozici skript `sys.argv[2]`jako , druhý jako , a tak dále. |
| **Argumenty tlumočníka** | Tyto argumenty jsou přidány do příkazového řádku spouštěče před názvem skriptu. Běžné argumenty `-W ...` zde jsou `-O` řízení upozornění, mírně optimalizovat `-u` program a používat nebufferované VI. Uživatelé IronPython udávají toto `-X` pole pravděpodobně `-X:Frames` `-X:MTA`k předání možností, například nebo . |
| **Cesta interpreta** | Přepíše cestu přidruženou k aktuálnímu prostředí. Hodnota může být užitečná pro spuštění skriptu s nestandardním interpretem. |
| **Proměnné prostředí** | Do tohoto víceřádkového textového pole \<přidejte\<položky formuláře NÁZEV>= HODNOTA>. Vzhledem k tomu, že toto nastavení je použito `PYTHONPATH` jako poslední, nad všechny existující proměnné globálního prostředí a po nastavení podle nastavení **Cesty hledání,** lze jej použít k ručnímu přepsání některé z těchto dalších proměnných. |

## <a name="immediate-and-interactive-windows"></a>Okamžitá a interaktivní okna

Existují dvě interaktivní okna, která můžete použít během relace ladění: standardní okno Visual Studio **Immediate** a interaktivní okno **ladění pythonu.**

Okno **Immediate** **(Debug** > **Windows** > **Immediate)** se používá pro rychlé vyhodnocení výrazů Pythonu a kontrolu nebo přiřazení proměnných v rámci spuštěného programu. Podrobnosti naleznete v obecném článku [okamžitého okna.](../ide/reference/immediate-window.md)

Interaktivní okno **ladění pythonu** **(Ladění** > **Windows** > **Python Debug Interactive**) je bohatší, protože zpřístupňuje úplné interaktivní prostředí [REPL](python-interactive-repl-in-visual-studio.md) při ladění, včetně psaní a spuštění kódu. Automaticky se připojí k libovolnému procesu spuštěného v ladicím programu pomocí standardního spouštěče Pythonu (včetně procesů připojených prostřednictvím **debug** > **upočit procesu).** Není však k dispozici při použití ladění c/c++ ve smíšeném režimu.

![Interaktivní okno ladění pythonu](media/debugging-interactive.png)

Okno **Interaktivní ladění** podporuje kromě [standardních příkazů REPL](python-interactive-repl-in-visual-studio.md#meta-commands)speciální metapříkazy :

| Příkaz | Argumenty | Popis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Spustí spuštění programu z aktuálního příkazu. |
| `$down`, `$d` | Přesunutí aktuálního snímku o jednu úroveň dolů v trasování zásobníku. |
| `$frame` | | Zobrazí ID aktuálního snímku.
| `$frame` | ID rámce | Přepne aktuální snímek na zadané ID snímku.
| `$load` | Načte příkazy ze souboru a provede až do dokončení |
| `$proc` |  | Zobrazí ID aktuálního procesu. |
| `$proc` | ID procesu | Přepne aktuální proces na zadané ID procesu. |
| `$procs` | | Zobrazí seznam procesů, které jsou aktuálně laděny. |
| `$stepin`, `$step`, `$s` | Kroky do dalšího volání funkce, pokud je to možné. |
| `$stepout`, `$return`, `$r` | Kroky z aktuální funkce. |
| `$stepover`, `$until`, `$unt` | Kroky přes další volání funkce. |
| `$thread` | | Zobrazí Aktuální ID vlákna. |
| `$thread` | ID vlákna | Přepne aktuální vlákno na zadané ID vlákna. |
| `$threads` | | Zobrazí seznam vláken, která jsou aktuálně laděna. |
| `$up`, `$u` | | Přesunutí aktuálního snímku o jednu úroveň výš v trasování zásobníku |
| `$where`, `$w`, `$bt` | Zobrazí seznam rámců pro aktuální vlákno. |

Všimněte si, že standardní ladicí systém okna, jako jsou **procesy**, **vlákna**a **zásobník volání** nejsou synchronizovány s interaktivním oknem **ladění.** Změna aktivního procesu, vlákna nebo rámce v interaktivním **ladicím okně** nemá vliv na ostatní okna ladicího programu. Podobně změna aktivního procesu, vlákna nebo rámce v jiných oknech ladicího programu nemá vliv na interaktivní okno **ladění.**

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Použití staršího ladicího programu

Visual Studio 2017 verze 15.8 a novější použít ladicí program na základě ptvsd verze 4.1+. Tato verze ptvsd je kompatibilní s Python 2.7 a Python 3.5+. Pokud používáte Python 2.6, 3.1 až 3.4 nebo IronPython, Visual Studio zobrazí chybu, **Debugger nepodporuje toto prostředí Pythonu**:

![Ladicí program nepodporuje tuto chybu prostředí Pythonu při použití ladicího programu](media/debugging-experimental-incompatible-error.png)

V těchto případech je nutné použít starší ladicí program (což je výchozí verze sady Visual Studio 2017 verze 15.7 a starší). Vyberte příkaz nabídky**Možnosti** **nástrojů,** > přejděte na**Ladění** **Pythonu** > a vyberte možnost **Použít starší ladicí program.**

Pokud jste nainstalovali starší verzi ptvsd v aktuálním prostředí (například starší verze 4.0.x nebo verze 3.x požadovaná pro vzdálené ladění), visual studio může zobrazit chybu nebo upozornění.

Chyba, **balíček debuggeru nelze načíst**, se zobrazí po instalaci ptvsd 3.x:

![Balíček ladicího programu nelze načíst chybu při použití ladicího programu](media/debugging-experimental-version-error.png)

V takovém případě vyberte **Použít starší ladicí program** k nastavení **možnosti Použít starší ladicí program** a restartujte ladicí program.

Upozornění, **Debugger balíček je zastaralý**, se zobrazí, když jste nainstalovali starší verzi 4.x ptvsd:

![Balíček ladicího programu je zastaralé upozornění při použití ladicího programu](media/debugging-experimental-version-warning.png)

> [!Important]
> I když můžete ignorovat upozornění pro některé verze ptvsd, Visual Studio nemusí fungovat správně.

Správa instalace ptvsd:

1. Přejděte na kartu **Balíčky** v okně **Prostředí Pythonu.**

1. Do vyhledávacího pole zadejte "ptvsd" a zkontrolujte nainstalovanou verzi ptvsd:

    ![Kontrola verze ptvsd v okně Prostředí Pythonu](media/debugging-experimental-check-ptvsd.png)

1. Pokud je verze nižší než 4.1.1a9 (verze dodávaná s Visual Studio), vyberte **X** vpravo od balíčku odinstalovat starší verzi. Visual Studio pak používá jeho přibalenou verzi. (Můžete také odinstalovat z `pip uninstall ptvsd`prostředí PowerShell pomocí .)

1. Alternativně můžete aktualizovat balíček ptvsd na jeho nejnovější verzi podle pokynů v části [Poradce při potížích.](#troubleshooting)

## <a name="troubleshooting"></a>Řešení potíží

Pokud máte problémy s ladicím programem, nejprve upgradujte verzi ptvsd takto:

1. Přejděte na kartu **Balíčky** v okně **Prostředí Pythonu.**

1. Zadejte `ptvsd --upgrade` do vyhledávacího pole a pak vyberte **Spustit příkaz: pip install ptvsd --upgrade**. (Můžete také použít stejný příkaz z prostředí PowerShell.)

    ![Udělení příkazu pro upgrade ptvsd v okně Prostředí Pythonu](media/debugging-experimental-upgrade-ptvsd.png)

Pokud problémy přetrvávají, nahlaste problém v [úložišti PTVS GitHub](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Povolení protokolování ladicího programu

V průběhu vyšetřování problému ladicího programu vás společnost Microsoft může požádat o povolení a shromažďování protokolů ladicího programu, které pomáhají při diagnostice.

Následující kroky umožňují ladění v aktuální relaci sady Visual Studio:

1. Otevřete příkazové okno v sadě Visual Studio pomocí příkazu **Zobrazit** > jiné**příkazové okno systému** **Windows.** > 

1. Zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Začněte ladit a projděte si všechny kroky, které jsou nezbytné k reprodukci problému. Během této doby se protokoly ladění zobrazí ve **výstupním** okně v části **Protokol hostitele ladicího adaptéru**. Potom můžete zkopírovat protokoly z tohoto okna a vložit do problému GitHub, e-mailu atd.

    ![Výstup protokolování ladicího programu v okně Výstup](media/debugger-logging-output.png)

1. Pokud visual studio přestane reagovat nebo jinak nemáte přístup k oknu **Výstup,** restartujte visual studio, otevřete příkazové okno a zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Začněte ladit a znovu reprodukovat problém. Protokoly ladicího programu se `%temp%\DebugAdapterHostLog.txt`pak nacházejí v .

## <a name="see-also"></a>Viz také

Úplné podrobnosti o ladicím programu sady Visual Studio naleznete v tématu [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md).
