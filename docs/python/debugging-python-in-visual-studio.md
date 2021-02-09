---
title: Ladění kódu Pythonu
description: Visual Studio poskytuje bohatou ladění kódu Pythonu, včetně nastavení zarážek, krokování, kontrolování hodnot, hledání výjimek a ladění v interaktivním okně.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b5a86f600f9145742f6447af54fccb10dbc302a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931770"
---
# <a name="debug-your-python-code"></a>Ladění kódu Pythonu

Sada Visual Studio poskytuje komplexní ladicí prostředí pro Python, včetně připojení ke spuštěným procesům, vyhodnocování výrazů v okně **kukátko** a **bezprostředních** oknech, kontrolu místních proměnných, zarážek, krokování/převzetí/převzetí příkazů, **nastavení dalšího příkazu** a další.

Viz také následující články o ladění pro konkrétní scénář:

- [Vzdálené ladění pro Linux](debugging-python-code-on-remote-linux-machines.md)
- [Ladění ve smíšeném režimu Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symboly pro ladění ve smíšeném režimu](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python v aplikaci Visual Studio podporuje ladění bez projektu. Po otevření samostatného souboru Pythonu klikněte v editoru pravým tlačítkem myši, vyberte **Spustit s laděním** a Visual Studio spustí skript s globálním výchozím prostředím (viz [prostředí Python](managing-python-environments-in-visual-studio.md)) a žádné argumenty. Od potom pak máte úplnou podporu ladění.
>
> Chcete-li řídit prostředí a argumenty, vytvořte projekt pro kód, který lze snadno provést pomocí existující šablony projektu [kódu Pythonu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) .

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Základní ladění

Základní pracovní postup ladění zahrnuje nastavení zarážek, krokování kódu, kontrolu hodnot a zpracování výjimek, jak je popsáno v následujících částech.

Relace ladění začíná příkazem **ladění**  >  **Spustit ladění** , tlačítkem **Start** na panelu nástrojů nebo klávesou **F5** . Tyto akce spustí spouštěcí soubor projektu (zobrazený tučně v **Průzkumník řešení**) s aktivním prostředím projektu a libovolnými argumenty příkazového řádku nebo vyhledávacími cestami, které byly zadány ve **vlastnostech projektu** (viz [možnosti ladění projektu](#project-debugging-options)). Sada Visual Studio 2017 verze 15,6 a novější vás upozorní, pokud nemáte nastaven spouštěcí soubor. starší verze můžou otevřít okno výstup se spuštěným překladačem Pythonu, jinak se okno výstup krátce zobrazí a zmizí. V každém případě klikněte pravým tlačítkem na příslušný soubor a vyberte **nastavit jako spouštěcí soubor**.

> [!Note]
> Ladicí program vždy začíná aktivním prostředím Python pro projekt. Chcete-li změnit prostředí, vytvořte jinou aktivní, jak je popsáno v tématu [Výběr prostředí Python pro projekt](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Zarážky

Zarážky zastaví provádění kódu v označeném bodě, takže můžete zkontrolovat stav programu. Nastavte zarážky kliknutím na levý okraj editoru kódu nebo kliknutím pravým tlačítkem myši na řádek kódu a výběrem **zarážky**  >  **Vložit** zarážku. Na každém řádku se zarážkou se zobrazí červená tečka.

![Zarážky se zobrazují v aplikaci Visual Studio.](media/debugging-breakpoints.png)

Kliknutím na červenou tečku nebo kliknutím pravým tlačítkem myši na řádek kódu a výběrem **zarážky**  >  **Odstranit** zarážku odeberete zarážku. Můžete ji také zakázat bez odebrání pomocí příkazu **zarážka**  >  **Disable** zarážky.

> [!Note]
> Některé zarážky v Pythonu můžou být překvapivé pro vývojáře, kteří pracovali s jinými programovacími jazyky. V Pythonu je celý soubor spustitelný kód, takže Python spustí soubor, když je načten pro zpracování jakékoli definice třídy nebo funkce nejvyšší úrovně. Pokud byla zarážka nastavena, může být ladicí program s částečnou částí převedený prostřednictvím deklarace třídy. Toto chování je správné, i když se někdy překvapivé.

Můžete přizpůsobit podmínky, za kterých je aktivována zarážka, jako je například rozdělení pouze v případě, že je proměnná nastavena na určitou hodnotu nebo rozsah hodnot. Pokud chcete nastavit podmínky, klikněte pravým tlačítkem myši na červenou tečku zarážky, vyberte **Podmínka** a pak vytvořte výrazy pomocí kódu Pythonu. Úplné podrobnosti o této funkci v aplikaci Visual Studio naleznete v tématu [podmínky zarážky](../debugger/using-breakpoints.md#breakpoint-conditions).

Při nastavování podmínek můžete také nastavit **akci** a vytvořit zprávu pro protokolování do okna výstup, volitelně pokračovat v provádění automaticky. Protokolování zprávy vytvoří, co se říká *zarážka s trasováním* bez přidání kódu protokolování do aplikace přímo:

![Vytvoření zarážka s trasováním se zarážkou](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Krokovat kód

Po zastavení na zarážce máte různé způsoby, jak krokovat kód nebo spustit bloky kódu před opětovným přerozdělením. Tyto příkazy jsou k dispozici na mnoha místech, včetně panelu nástrojů pro ladění, nabídky **ladění** , v kontextové nabídce pravého tlačítka myši v editoru kódu a prostřednictvím klávesových zkratek (i když nejsou všechny příkazy umístěny na všech místech):

| Funkce | Klávesnice | Description |
| --- | --- | --- |
| **Pokračovat** | **F5** | Spustí kód, dokud není dosaženo další zarážce. |
| **Krokovat s vnořením** | **Kláves** | Spustí další příkaz a zastaví se. Pokud je dalším příkazem volání funkce, ladicí program se zastaví na prvním řádku volané funkce. |
| **Krokovat** | **F10** | Spustí další příkaz, včetně volání funkce (spuštění veškerého kódu) a použití libovolné návratové hodnoty. Krokování přes umožňuje snadno přeskočit funkce, které nemusíte ladit. |
| **Krok ven** | **Posun** + Klávesa **F11** | Spustí kód do konce aktuální funkce a pak kroky volání příkazu.  Tento příkaz je užitečný, pokud nepotřebujete ladit zbytek aktuální funkce. |
| **Spustit ke kurzoru** | **CTRL** + **F10** | Spustí kód v umístění blikajícího kurzoru v editoru. Tento příkaz umožňuje snadno přeskočit segment kódu, který není nutné ladit. |
| **Nastavení dalšího příkazu** | **CTRL** + **Posun** + **F10** | Změní aktuální bod spuštění v kódu na umístění blikajícího kurzoru. Tento příkaz umožňuje vynechat segment kódu, který se spouští vůbec, například když víte, že kód je chybný nebo vytváří nežádoucí vedlejší účinky. |
| **Zobrazit další příkaz** | **ALT** + **Počet** **&#42;**| Vrátí se k dalšímu příkazu, který se má spustit. Tento příkaz je užitečný, pokud jste se seznámili v kódu a nepamatujete si, kde je ladicí program zastavený. |

### <a name="inspect-and-modify-values"></a>Kontrola a úprava hodnot

Při zastavení v ladicím programu můžete zkontrolovat a upravit hodnoty proměnných. Okno **kukátka** můžete také použít k monitorování jednotlivých proměnných i vlastních výrazů. (Další informace najdete v tématu [Kontrola proměnných](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) .)

Chcete-li zobrazit hodnotu pomocí datových **tipů**, Stačí umístit ukazatel myši na libovolnou proměnnou v editoru. Můžete ji změnit kliknutím na tuto hodnotu:

![Zobrazení datových tipů v ladicím programu sady Visual Studio](media/debugging-quick-tips.png)

Okno **Automatické** hodnoty (**ladění**  >  **systému Windows**  >  **auto**) obsahuje proměnné a výrazy, které se blíží aktuálnímu příkazu. Můžete dvakrát kliknout ve sloupci hodnota nebo vybrat a stisknout **F2** pro úpravu hodnoty:

![Okno Automatické hodnoty v ladicím programu sady Visual Studio](media/debugging-autos-window.png)

Okno **místní** hodnoty (**ladění**  >  místních hodnot **systému Windows**  >  ) zobrazí všechny proměnné, které jsou v aktuálním oboru, které lze znovu upravit:

![Okno místní hodnoty v ladicím programu sady Visual Studio](media/debugging-locals-window.png)

Další informace o používání **automatických** funkcí a **místních** hodnot najdete v tématu [Kontrola proměnných v oknech automatické hodnoty a místní](../debugger/autos-and-locals-windows.md)hodnoty.

Okna **kukátka** (**ladění**  >    >  **kukátka Windows Watch**  >  **1-4**) umožňují zadat libovolné výrazy Pythonu a zobrazit výsledky. Výrazy jsou znovu vyhodnoceny pro každý krok:

![okno Kukátko v ladicím programu sady Visual Studio](media/debugging-watch-window.png)

Další informace o používání **sledování** najdete v tématu [Nastavení sledování proměnných pomocí oken kukátka a QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Když kontrolujete řetězcovou hodnotu ( `str` , `unicode` , `bytes` a `bytearray` jsou pro tento účel považovány za řetězce), zobrazí se na pravé straně hodnoty ikona lupy. Kliknutím na ikonu se zobrazí hodnota řetězce bez uvozovek v automaticky otevíraném dialogovém okně s balením a posouváním, což je užitečné pro dlouhé řetězce. Kromě toho, když vyberete šipku rozevíracího seznamu na ikoně, můžete vybrat vizualizace prostého textu, HTML, XML a JSON:

![Řetězcové vizualizace v ladicím programu sady Visual Studio](media/debugging-string-visualizers.png)

Vizualizace HTML, XML a JSON se zobrazí v samostatných překryvných oknech se zvýrazňováním syntaxe a zobrazeními stromové struktury.

### <a name="exceptions"></a>Výjimky

Pokud během ladění dojde k chybě v programu, ale nemáte pro ni obslužnou rutinu výjimky, ladicí program se ukončí v bodě výjimky:

![Místní nabídka výjimky v ladicím programu sady Visual Studio](media/debugging-exception-popup.png)

V tomto okamžiku můžete zkontrolovat stav programu, včetně zásobníku volání. Nicméně pokud se pokusíte krokovat kód, výjimka pokračuje vyvoláním, dokud není buď zpracována, nebo ukončení programu.

Příkaz nabídky **ladit**  >    >  **Nastavení výjimek** v systému Windows přinese okno, ve kterém můžete rozbalit **výjimky Pythonu**:

![Okno výjimky v ladicím programu sady Visual Studio](media/debugging-exception-settings.png)

Zaškrtávací políčko pro každou výjimku určuje, zda ladicí program *vždy* při vyvolání dojde k přerušení. Toto políčko zaškrtněte, pokud chcete pro určitou výjimku rozdělit častěji.

Ve výchozím nastavení je většina výjimek přerušena v případě, že se ve zdrojovém kódu nenajde obslužná rutina výjimky. Chcete-li toto chování změnit, klikněte pravým tlačítkem myši na libovolnou výjimku a změňte možnost **pokračovat, pokud není zpracována v uživatelském kódu** . Toto políčko zrušte, pokud chcete pro výjimku přerušit méně často.

Chcete-li konfigurovat výjimku, která se v tomto seznamu nezobrazí, klikněte na tlačítko **Přidat** a přidejte ji. Název musí odpovídat celému názvu výjimky.

## <a name="project-debugging-options"></a>Možnosti ladění projektu

Ve výchozím nastavení ladicí program spustí program se standardním spouštěčem Pythonu, bez argumentů příkazového řádku a žádné další speciální cesty ani podmínky. Možnosti spuštění jsou změněny prostřednictvím vlastností ladění projektu, které jsou k dispozici, kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení**, výběrem **vlastností** a výběrem karty **ladění** .

![Vlastnosti ladění projektu v ladicím programu sady Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Možnosti režimu spuštění

| Možnost | Popis |
| --- | --- |
| **Standardní spouštěč Pythonu** | Používá ladění kódu napsaného v přenositelném Pythonu, které je kompatibilní s CPython, Ironpythonu a variantami, jako je Python bez zásobníku. Poskytuje nejlepší prostředí pro ladění čistě kódu Pythonu. Když se připojíte k procesu běžícího *python.exe* , použije se tento spouštěč. Tento spouštěč taky poskytuje [ladění ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) pro CPython, což vám umožní plynule krokovat kód C/C++ a kód Pythonu. |
| **Webový spouštěč** | Spustí výchozí prohlížeč při spuštění a povolí ladění šablon. Další informace najdete v části [ladění webové šablony](python-web-application-project-templates.md#debugging) . |
| **Webový spouštěč Django** | Stejné jako webový spouštěč a zobrazená jenom z důvodu zpětné kompatibility. |
| **Spouštěč Ironpythonu (.NET)** | Používá ladicí program .NET, který funguje pouze s Ironpythonu, ale umožňuje krokování mezi jakýmkoli projektem jazyka .NET, včetně C# a VB. Tato spouštěcí služba se používá, pokud se připojíte ke spuštěnému procesu .NET, který je hostitelem Ironpythonu. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Možnosti spuštění (cesty hledání, spouštěcí argumenty a proměnné prostředí)

| Možnost | Popis |
| --- | --- |
| **Cesty pro hledání** | Tyto hodnoty se shodují s tím, co se zobrazuje v uzlu **cesty hledání** projektu v **Průzkumník řešení**. Tuto hodnotu můžete upravit zde, ale je snazší použít **Průzkumník řešení** , která umožňuje procházet složky a automaticky převádět cesty k relativnímu formuláři. |
| **Argumenty skriptu** | Tyto argumenty se přidají do příkazu, který se používá ke spuštění skriptu, který se zobrazí za názvem souboru vašeho skriptu. První položka je k dispozici pro váš skript jako `sys.argv[1]` , druhý jako `sys.argv[2]` a tak dále. |
| **Argumenty interpretu** | Tyto argumenty jsou přidány do příkazového řádku spouštěče před názvem vašeho skriptu. Zde jsou společné argumenty pro `-W ...` řízení upozornění, `-O` pro mírně optimalizaci programu a `-u` používání neuložených vstupně-výstupních operací. Ironpythonu uživatelé mohou použít toto pole k předání `-X` možností, například `-X:Frames` nebo `-X:MTA` . |
| **Cesta k interpretu** | Přepíše cestu přidruženou k aktuálnímu prostředí. Hodnota může být užitečná pro spuštění skriptu pomocí nestandardního překladače. |
| **Proměnné prostředí** | Do tohoto víceřádkového textového pole přidejte položky formuláře \<NAME> = \<VALUE> . Vzhledem k tomu, že toto nastavení bylo použito jako poslední, nad všemi existujícími globálními proměnnými prostředí a poté `PYTHONPATH` , co je nastaveno podle nastavení **cest hledání** , lze použít k ručnímu přepsání kterékoli z těchto ostatních proměnných. |

## <a name="immediate-and-interactive-windows"></a>Okamžitá a interaktivní okna

Existují dva interaktivní systémy Windows, které můžete použít během relace ladění: **standardní okno aplikace Visual Studio a** **interaktivní okno ladění Pythonu** .

**Okamžité** okno (**ladění**  >  **systému Windows**  >  je **okamžité**) se používá pro rychlé vyhodnocení výrazů Pythonu a kontrolu nebo přiřazení proměnných v rámci běžícího programu. Podrobnosti najdete v článku o [okamžitém okně](../ide/reference/immediate-window.md) .

**Interaktivní okno ladění Pythonu** (**ladění**  >  **Windows**  >  **Pythonu** pro ladění interaktivní) je bohatší, protože zpřístupňuje kompletní [interaktivní REPL](python-interactive-repl-in-visual-studio.md) při ladění, včetně psaní a spouštění kódu. Automaticky se připojí k jakémukoli procesu spuštěnému v ladicím programu pomocí standardní spouštěče Pythonu (včetně procesů připojených prostřednictvím příkazu **ladit**  >  **připojení k procesu**). Není však k dispozici při použití ladění ve smíšeném režimu C/C++.

![Interaktivní okno ladění Pythonu](media/debugging-interactive.png)

**Interaktivní okno ladění** podporuje kromě [standardních příkazů REPL](python-interactive-repl-in-visual-studio.md#meta-commands)speciální meta příkazy:

| Příkaz | Argumenty | Description |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Spustí program spuštěný z aktuálního příkazu. |
| `$down`, `$d` | Posune aktuální rámec v trasování zásobníku o jednu úroveň níž. |
| `$frame` | | Zobrazí aktuální ID rámce.
| `$frame` | ID rámce | Přepne aktuální rámec na zadané ID rámce.
| `$load` | Načte příkazy ze souboru a provede až do dokončení. |
| `$proc` |  | Zobrazí aktuální ID procesu. |
| `$proc` | ID procesu | Přepne aktuální proces na zadané ID procesu. |
| `$procs` | | Vypíše procesy, které jsou právě laděny. |
| `$stepin`, `$step`, `$s` | Pokud je to možné, proveďte kroky do dalšího volání funkce. |
| `$stepout`, `$return`, `$r` | Vykrocích z aktuální funkce. |
| `$stepover`, `$until`, `$unt` | Kroky nad voláním funkce Next. |
| `$thread` | | Zobrazí aktuální ID vlákna. |
| `$thread` | ID vlákna | Přepne aktuální vlákno na zadané ID vlákna. |
| `$threads` | | Vypíše vlákna, která se právě ladí. |
| `$up`, `$u` | | Posune aktuální rámec v trasování zásobníku o jednu úroveň výš. |
| `$where`, `$w`, `$bt` | Vypíše rámce aktuálního vlákna. |

Všimněte si, že standardní okna ladicího programu, například **procesy**, **vlákna** a **zásobník volání** , nejsou synchronizována s **interaktivním oknem ladění** . Změna aktivního procesu, vlákna nebo snímku v **interaktivním okně ladění** nemá vliv na ostatní okna ladicího programu. Podobně Změna aktivního procesu, vlákna nebo snímku v ostatních oknech ladicího programu nemá vliv na **interaktivní okno ladění** .

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Použití starší verze ladicího programu

Visual Studio 2017 verze 15,8 a novější používají ladicí program založený na ptvsd verze 4.1 +. Visual Studio 2019 verze 16,5 a novější používají ladicí program založený na debugpy. Tyto verze ladicího programu jsou kompatibilní s Pythonem 2,7 a Python 3.5 +. Pokud používáte Python 2,6, 3,1 až 3,4 nebo Ironpythonu, Visual Studio zobrazí chybu, **ladicí program nepodporuje toto prostředí Pythonu**:

![Ladicí program nepodporuje tuto chybu prostředí Python při použití ladicího programu.](media/debugging-experimental-incompatible-error.png)

V těchto případech je nutné použít starší ladicí program (což je výchozí nastavení v aplikaci Visual Studio 2017 verze 15,7 a starší). Vyberte   >  příkaz nabídky **Možnosti** nástrojů, přejděte na ladění **Pythonu**  >  a vyberte možnost **použít starší verzi ladicího programu** .

Pokud jste nainstalovali starší verzi ptvsd do aktuálního prostředí (například starší verze 4.0. x nebo verzi 3. x, která je vyžadována pro vzdálené ladění), Visual Studio může zobrazit chybu nebo upozornění.

Chyba, **balíček ladicího programu se nepovedlo načíst**, po instalaci ptvsd 3. x se zobrazí:

![Při použití ladicího programu se nepovedlo načíst balíček ladicího programu.](media/debugging-experimental-version-error.png)

V takovém případě vyberte **použít starší verzi ladicího programu** k nastavení možnosti **použít starší verzi ladicího** programu a znovu spusťte ladicí program.

Upozornění, **balíček ladicího programu je zastaralá**, zobrazí se, když jste nainstalovali starší verzi 4. x ptvsd:

![Při použití ladicího programu je zastaralá výstraha balíčku ladicího programu](media/debugging-experimental-version-warning.png)

> [!Important]
> I když se můžete rozhodnout ignorovat varování pro některé verze ptvsd, Visual Studio nemusí správně fungovat.

Správa instalace ptvsd:

1. Přejděte na kartu **balíčky** v okně **prostředí Pythonu** .

1. Do vyhledávacího pole zadejte "ptvsd" a Projděte si nainstalovanou verzi ptvsd:

    ![Kontrola verze ptvsd v okně prostředí Pythonu](media/debugging-experimental-check-ptvsd.png)

1. Pokud je verze nižší než 4.1.1 (verze sady Visual Studio), vyberte **X** napravo od balíčku pro odinstalaci starší verze. Sada Visual Studio pak použije svou sadu oddaných verzí. (Můžete také z PowerShellu odinstalovat pomocí `pip uninstall ptvsd` .)

1. Alternativně můžete balíček ptvsd aktualizovat na jeho nejnovější verzi, a to podle pokynů uvedených v části [řešení potíží](#troubleshooting) .

## <a name="troubleshooting"></a>Řešení potíží

### <a name="for-visual-studio-2019-version-164-and-earlier-upgrade-ptvsd"></a>Pro Visual Studio 2019 (verze 16,4 a starší) upgrade ptvsd
Pokud máte s ladicím programem problémy, nejprve upgradujte verzi ladicího programu následujícím způsobem:

1. Přejděte na kartu **balíčky** v okně **prostředí Pythonu** .

1. `ptvsd --upgrade`Do vyhledávacího pole zadejte a pak vyberte **Spustit příkaz: PIP Install ptvsd--upgrade**. (Můžete také použít stejný příkaz z PowerShellu.)

    ![Poskytnutí příkazu pro upgrade ptvsd v okně prostředí Pythonu](media/debugging-experimental-upgrade-ptvsd.png)

   Pokud potíže potrvají, uveďte problém v [úložišti GitHubu PTVS](https://github.com/Microsoft/ptvs/issues).

   > [!NOTE]
   > Pro Visual Studio 2019 verze 16,5 a novější je debugpy součástí úlohy Python sady Visual Studio a je aktualizovaný společně se sadou Visual Studio.

### <a name="enable-debugger-logging"></a>Povolit protokolování ladicího programu

V průběhu vyšetřování problému s ladicím programem vás může společnost Microsoft požádat o povolení a shromažďování protokolů ladicího programu, které vám pomohou diagnostikovat.

Následující kroky umožňují ladění v aktuální relaci sady Visual Studio:

1. Otevřete okno příkazového řádku v aplikaci Visual Studio pomocí příkazu **Zobrazit**  >  **jiný**  >  **příkaz** v nabídce okna.

1. Zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Spusťte ladění a Projděte si jakékoli kroky potřebné k reprodukování problému. Během této doby se protokoly ladění zobrazí v okně **výstup** v části **protokol hostitele adaptéru ladění**. Pak můžete zkopírovat protokoly z tohoto okna a vložit je do problému, e-mailu, atd.

    ![Výstup protokolování ladicího programu v okně výstup](media/debugger-logging-output.png)

1. Pokud Visual Studio přestane reagovat nebo jste jinak nedokázali získat přístup k oknu **výstup** , restartujte Visual Studio, otevřete příkazové okno a zadejte následující příkaz:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Spusťte ladění a znovu vytvořte problém. Protokoly ladicího programu se pak dají najít v `%temp%\DebugAdapterHostLog.txt` .

## <a name="see-also"></a>Viz také

Úplné podrobnosti o ladicím programu sady Visual Studio naleznete [v tématu ladění v aplikaci Visual Studio](../debugger/debugger-feature-tour.md).
