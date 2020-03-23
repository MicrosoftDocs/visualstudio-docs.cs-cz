---
title: Řešení problémů a známé problémy (Nástroje VS pro jednotu)
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d6856ff73f9aab2325a31e164e7983a919097d46
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "66261119"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Řešení potíží a známé problémy (Visual Studio Tools for Unity)

V této části najdete řešení běžných problémů s Visual Studio Tools for Unity, popisy známých problémů a zjistěte, jak můžete pomoci vylepšit visual studio nástroje pro jednotu hlášením chyb.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Poradce při potížích s připojením mezi Unity a Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Potvrdit připojení editoru je povoleno.

V nabídce Unity vyberte **Upravit předvolby >** a pak **Editor Attaching** vyberte kartu **Externí nástroje.** Další informace naleznete v [dokumentaci unity předvolby](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nelze připojit

- Pokuste se dočasně zakázat antivirový program nebo vytvořit pravidla vyloučení pro VS a Unity.
- Pokuste se dočasně zakázat bránu firewall nebo vytvořte pravidla pro povolení sítí TCP/UDP mezi VS a Unity.
- Některé programy, například Team Viewer, mohou narušit detekci procesů. Můžete se pokusit dočasně zastavit jakýkoli další software, abyste zjistili, zda něco změní.
- Nepřejmenovávejte hlavní spustitelný soubor Unity, protože VSTU pouze monitoruje procesy "Unity.exe".

## <a name="visual-studio-crashes"></a>Selhání sady Visual Studio

Tento problém může být z důvodu poškození mezipaměti Visual Studio MEF.

Zkuste odebrat následující složku a obnovit mezipaměť MEF (před tím zavřete Visual Studio):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

To by mělo vyřešit váš problém. V případě, že potíže stále přetrvávají, spusťte příkazový řádek pro vývojáře pro Visual Studio jako správce a použijte následující příkaz:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio zablokuje

Několik Unity pluginy jako Parse, FMOD, UMP (Universal Media Player), ZFBrowser, nebo Embedded Browser používají nativní vlákna. Je to problém, když plugin skončí připojení nativní vlákno na modul runtime, který pak dělá blokování volání operačního operačního es. To znamená, že Unity nelze přerušit toto vlákno pro ladicí program (nebo domény znovu načíst) a zablokuje.

Pro FMOD existuje řešení, můžete předat `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` [příznak](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) inicializace zakázat asynchronní zpracování a provést veškeré zpracování v hlavním vlákně.

## <a name="incompatible-project-in-visual-studio"></a>Nekompatibilní projekt v sadě Visual Studio

Nejprve zkontrolujte, zda je Visual Studio nastaveno jako externí editor skriptů v unity (Upravit/Předvolby/Externí nástroje). Potom zkontrolujte, zda je modul plug-in sady Visual Studio nainstalován v unity (Nápověda/O musí zobrazit zprávu, jako je Microsoft Visual Studio Tools for Unity je povolena v dolní části). Potom zkontrolujte, zda je rozšíření správně nainstalováno v sadě Visual Studio (Nápověda/Popis).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Extra znovu načtení nebo Visual Studio ztrácí všechna otevřená okna

Nezapomeňte se nikdy nedotýkat souborů projektu přímo z procesoru datových zdrojů nebo jiného nástroje. Pokud opravdu potřebujete manipulovat se souborem projektu, zpřístupníme pro to rozhraní API. Zkontrolujte [část Problémy s odkazy](#assembly-reference-issues)na sestavení .

Pokud dochází k další opětovné načtení nebo pokud Visual Studio ztrácí všechny otevřené Windows při opětovném načtení, ujistěte se, že máte nainstalované správné balíčky cílení .NET. Další informace naleznete v následující části o rozhraních.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Ladicí program není porušit na výjimky

Při použití starší unity runtime (.NET 3.5 ekvivalent), ladicí program bude vždy přerušit, když výjimka je neošetřené (= mimo try/catch bloku). Pokud je výjimka zpracována, ladicí program použije okno Nastavení výjimky k určení, zda je požadováno přerušení.

S novým runtime (.NET 4.6 ekvivalent), Unity představil nový způsob správy výjimek uživatele a jako výsledek všechny výjimky jsou považovány za "user-handled" i v případě, že jsou mimo try/catch bloku. To je důvod, proč je nyní nutné explicitně zkontrolovat v okně Nastavení výjimky, pokud chcete, aby ladicí program došlo k přerušení.

V okně Nastavení výjimky (Ladění > Nastavení > výjimek) rozbalte uzel pro kategorii výjimek (například výjimky prostředí Common Language Runtime, což znamená výjimky .NET) a zaškrtněte políčko pro konkrétní výjimku, kterou chcete zachytit v rámci této kategorie (například System.NullReferenceException). Můžete také vybrat celou kategorii výjimek.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>V systému Windows visual studio požádá o stažení rozhraní Unity target framework

Visual Studio Tools for Unity vyžaduje rozhraní .NET framework 3.5, který není nainstalován ve výchozím nastavení na Windows 8 nebo 10. Chcete-li tento problém vyřešit, postupujte podle pokynů ke stažení a instalaci rozhraní .NET Framework 3.5.

Při použití nového runtime Unity jsou také vyžadovány balíčky cílení .NET verze 4.6 a 4.7.1. K jejich rychlé instalaci je možné použít instalační program VS2017 (upravte instalaci VS2017, jednotlivé součásti, kategorii .NET, vyberte všechny balíčky cílení 4.x).

## <a name="assembly-reference-issues"></a>Referenční problémy sestavení

Pokud je váš projekt komplexní odkaz nebo pokud chcete lépe řídit tento krok generování, můžete použít naše [rozhraní API](../cross-platform/customize-project-files-created-by-vstu.md) pro manipulaci s obsahem generovaného projektu nebo řešení. Soubory [odpovědí](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) můžete také použít v projektu Unity a my je zpracujeme.

## <a name="breakpoints-with-a-warning"></a>Zarážky s upozorněním

Pokud Visual Studio nemůže najít zdrojové umístění pro konkrétní zarážku, zobrazí se upozornění kolem zarážky. Zkontrolujte, zda je skript, který používáte, správně načten nebo použit v aktuální scéně Unity.

## <a name="breakpoints-not-hit"></a>Zarážky, které nebyly přístupů

Zkontrolujte, zda je skript, který používáte, správně načten nebo použit v aktuální scéně Unity. Ukončete aplikaci Visual Studio i\*Unity a \*odstraňte všechny generované soubory ( .csproj, .sln) a celou složku Knihovny.

## <a name="unable-to-debug-android-players"></a>Nelze ladit přehrávače Android

Pro detekci přehrávače používáme vícesměrové vysílání (což je výchozí mechanismus používaný Unity), ale poté k připojení ladicího programu použijeme běžné připojení TCP. Fáze detekce je hlavním problémem pro zařízení Android.

Wifi je univerzální, ale super pomalý ve srovnání s USB kvůli latenci. Viděli jsme nedostatek řádné podpory vícesměrového vysílání pro některé směrovače nebo zařízení (řada Nexus je tím dobře známá).

USB je super rychlý pro ladění a Visual Studio Tools for Unity je nyní schopen detekovat zařízení USB a mluvit na server adb správně předávat porty pro ladění.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problémy s Visual Studio 2015 a IntelliSense nebo zbarvení kódu

Zkuste upgradovat Visual Studio 2015 na aktualizaci 3.

## <a name="known-issues"></a>Známé problémy

 Existují známé problémy v Visual Studio Tools for Unity, které vyplývají z toho, jak ladicí program spolupracuje se starší verzí kompilátoru Jazyka C# Unity. Pracujeme na řešení těchto problémů, ale mezitím se mohou vyskytnou následující problémy:

- Při ladění Unity někdy dojde k chybě.

- Při ladění Unity někdy zamrzne.

- Krokování a z metod se někdy chová nesprávně, zejména v iterátorech nebo v příkazech switch.

## <a name="report-errors"></a>Hlášení chyb

 Pomozte nám zlepšit kvalitu nástrojů sady Visual Studio pro jednotu odesláním zpráv o chybách, když dojde k selhání, zamrznutí nebo jiným chybám. To nám pomáhá prozkoumat a opravit problémy v nástrojích Visual Studio pro jednotu. Děkujeme!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak nahlásit chybu při zamrznutí sady Visual Studio

 Existují zprávy, že Visual Studio někdy zamrzne při ladění s Visual Studio Tools for Unity, ale potřebujeme více dat k pochopení tohoto problému. Můžete nám pomoci prozkoumat pomocí následujících kroků.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Chcete-li ohlásit, že Visual Studio zamrzne při ladění pomocí nástrojů Sady Visual Studio pro jednotu

*Ve Windows:*

1. Otevřete novou instanci sady Visual Studio.

1. Otevřete dialogové okno Připojit k procesu. V nové instanci sady Visual Studio v hlavní nabídce zvolte **Ladění**, **Připojit k procesu**.

1. Připojte ladicí program k zmrazené instanci sady Visual Studio. V dialogovém okně **Připojit k procesu** vyberte zmrazenou instanci sady Visual Studio z tabulky **Dostupné procesy** a pak zvolte tlačítko **Připojit.**

1. Pozastavte ladicí program. V nové instanci sady Visual Studio v hlavní nabídce zvolte **Ladění**, **Break All**nebo stiskněte **kombinaci kláves Ctrl+Alt+Break**.

1. Vytvořte výpis vlákna. V okně Příkaz zadejte následující příkaz a stiskněte **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Možná budete muset nejprve zviditelnit okno **Příkaz.** V sadě Visual Studio v hlavní nabídce zvolte **Zobrazit**, **Jiné Windows**, **Příkazové okno**.

*Na počítači Mac:*

1. Otevřete terminál a získejte PID visual studia pro Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Spusťte ladicí program lldb:

    ```shell
    lldb
    ```

1. Připojte se k instanci Visual Studio pro Mac pomocí PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Načíst stacktrace pro všechny podprocesy:

    ```shell
    bt all
    ```

Nakonec odešlete výpis [vstusp@microsoft.com](mailto:vstusp@microsoft.com)vlákna do aplikace spolu s popisem toho, co jste dělali, když visual studio zamrzlo.
