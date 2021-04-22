---
title: Řešení potíží a známé problémy (nástroje VS Tools for Unity)
description: Přečtěte si informace o řešení potíží v Visual Studio Tools for Unity. Podívejte se na popisy známých problémů a seznamte se s řešeními těchto problémů.
ms.custom: ''
ms.date: 04/15/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 37ee35fa66d37f9b85af01f5012e8ede76e877de
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879366"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Řešení potíží a známé problémy (Visual Studio Tools for Unity)

V této části najdete řešení běžných potíží s Visual Studio Tools for Unity, popisy známých problémů a Naučte se, jak můžete Visual Studio Tools for Unity vylepšit pomocí hlášení chyb.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Řešení potíží s připojením mezi Unity a Visual Studio

### <a name="confirm-editor-attaching-is-enabled-or-code-optimization-on-startup-is-set-to-debug"></a>Potvrzení `Editor Attaching` je povolené nebo `Code Optimization On Startup` je nastavené na. `Debug`

V nabídce Unity vyberte `Edit / Preferences` .

V závislosti na použité verzi Unity:
- Potvrďte, že `Code Optimization On Startup` je nastavená na `Debug` .
- Nebo vyberte `External Tools` kartu. Potvrďte, že `Editor Attaching` je zaškrtávací políčko povoleno. 

Další informace najdete v dokumentaci k [preferenceem Unity](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nelze se připojit

- Pokuste se dočasně zakázat antivirový program nebo vytvořit pravidla vyloučení pro VS i Unity.
- Zkuste dočasně zakázat bránu firewall nebo vytvořit pravidla pro povolení sítě TCP/UDP mezi VS a Unity.
- Některé programy, jako je například prohlížeč týmu, mohou kolidovat s detekcí procesů. Můžete se pokusit dočasně zastavit veškerý další software, abyste viděli, jestli se něco změní.
- Neměňte název hlavního spustitelného souboru Unity, protože VSTU sleduje pouze procesy "Unity.exe".

## <a name="visual-studio-crashes"></a>Chyby sady Visual Studio

K tomuto problému může dojít kvůli poškození mezipaměti rozhraní MEF sady Visual Studio.

Zkuste odebrat následující složku, aby se obnovila mezipaměť MEF (před provedením této akce zavřete Visual Studio):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Tato chyba by měla vyřešit váš problém. V případě, že stále dochází k potížím, spusťte Developer Command Prompt pro Visual Studio jako správce a použijte následující příkaz:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Visual Studio přestane reagovat

Několik modulů plug-in Unity jako analyze, FMOD –, UMP (Universal Media Player), ZFBrowser nebo Embedded Browser používá nativní vlákna. Jedná se o problém, když modul plug-in ukončí připojení nativního vlákna k modulu runtime, který pak zablokuje volání do operačního systému. To znamená, že Unity nemůže přerušit toto vlákno pro ladicí program (nebo znovu načíst doménu) a přestat reagovat.

Pro FMOD – existuje alternativní řešení, pomocí kterého můžete předat `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` [příznak](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) inicializace, který zakáže asynchronní zpracování a provede veškeré zpracování v hlavním vlákně.

## <a name="incompatible-project-in-visual-studio"></a>Nekompatibilní projekt v aplikaci Visual Studio

Velmi důležitou věcí je, že Visual Studio ukládá "nekompatibilní" stav v nastavení projektu a nepokusí se znovu načíst projekt, dokud jej nepoužijete explicitně `Reload Project` . Takže po každém kroku řešení potíží se ujistěte, že se pokusíte znovu otevřít řešení a zkusit kliknout pravým tlačítkem na všechny nekompatibilní projekty a vybrat `Reload Project` .

1. Ověřte, že sada Visual Studio je nastavená jako váš externí editor skriptů v Unity pomocí `Edit / Preferences / External Tools` .
2. V závislosti na vaší verzi Unity:
   - Ověřte, že je v Unity nainstalovaný modul plug-in Visual Studio. `Help / About` měla by se zobrazit zpráva, například Microsoft Visual Studio nástroje pro Unity, je v dolní části povolená.
   - Unity 2020. x +: Ověřte, že používáte nejnovější balíček editoru sady Visual Studio v `Window / Package Manager` .
3. Zkuste odstranit všechny projekty nebo soubory řešení a `.vs` složku v projektu.
4. Zkuste znovu vytvořit projekty nebo řešení pomocí `Open C# Project` nebo `Edit / Preferences / External tools / Regenerate Project files` .
5. Ujistěte se, že jste nainstalovali úlohu hry/Unity v nástroji Visual Studio.
6. Zkuste vyčistit mezipaměť MEF, jak je popsáno [zde](#visual-studio-crashes).
7. Zkuste znovu nainstalovat Visual Studio (jenom pomocí úlohy hry/Unity).
8. Zkuste zakázat rozšíření jiných výrobců v případě, že by mohlo narušit rozšíření Unity v nástroji `Tools / Extensions` .

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Další opětovné načtení nebo aplikace Visual Studio ztratí všechna otevřená okna

Ujistěte se, že soubory projektu nemusíte upravovat přímo z procesoru assetů nebo jiného nástroje. Pokud skutečně potřebujete manipulovat se souborem projektu, zveřejňujeme pro něj rozhraní API. Podívejte se prosím do [oddílu problémy s odkazy na sestavení](#assembly-reference-or-project-property-issues).

Pokud se objeví další opakované načítání nebo pokud Visual Studio ztratí při opětovném spuštění všechny otevřené systémy Windows, ujistěte se, že máte nainstalované správné sady .NET targeting pack. Další informace najdete v následující části o rozhraních.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Ladicí program neprovádí přerušení při výjimkách

Při použití starší verze prostředí Unity runtime (.NET 3,5 ekvivalentní) se ladicí program vždy přeruší, pokud je výjimka Neošetřená (= mimo blok try/catch). Pokud je výjimka zpracována, ladicí program použije okno Nastavení výjimek k určení, zda je přerušení požadováno nebo ne.

V rámci nového modulu runtime (.NET 4,6 Equivalent) představila Unity nový způsob, jak spravovat výjimky uživatelů, a v důsledku toho se všechny výjimky zobrazují jako "zpracování uživatelem", a to i v případě, že jsou mimo blok try/catch. To je důvod, proč je nyní nutné explicitně zkontrolovat v okně Nastavení výjimek, pokud chcete, aby byl ladicí program přerušen.

V okně nastavení výjimky (ladění > > nastavení výjimek) rozbalte uzel pro kategorii výjimek (například výjimky modulu CLR (Common Language Runtime), tzn. výjimky rozhraní .NET) a zaškrtněte políčko pro konkrétní výjimku, kterou chcete zachytit v rámci této kategorie (například System. NullReferenceException). Můžete také vybrat celou kategorii výjimek.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Ve Windows se Visual Studio zeptá na stažení cílové architektury Unity.

Pokud používáte starší verzi prostředí Unity runtime (.NET 3,5 ekvivalentní), Visual Studio Tools for Unity vyžaduje rozhraní .NET Framework 3,5, které není ve výchozím nastavení nainstalované ve Windows 8 nebo 10. Chcete-li tento problém vyřešit, postupujte podle pokynů ke stažení a instalaci rozhraní .NET Framework 3,5.

Při použití nového modulu runtime Unity se v závislosti na verzi Unity taky vyžadují sady .NET Targeting Packs verze 4,6 nebo 4.7.1. Je možné pomocí instalačního programu sady Visual Studio rychle nainstalovat (upravit instalaci, jednotlivé komponenty, kategorii .NET, vybrat všechny 4. x cílené sady).

## <a name="assembly-reference-or-project-property-issues"></a>Problémy s odkazem na sestavení nebo vlastností projektu

Pokud je projekt složitým odkazem nebo pokud chcete lepší kontrolu nad tímto krokem generace, můžete použít naše [rozhraní API](../extensibility/customize-project-files-created-by-vstu.md) pro manipulaci s generovaným obsahem projektu nebo řešení. V projektu Unity můžete také použít [soubory odpovědí](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) a my je zpracujeme.

S nejnovější verzí sady Visual Studio a Unity je nejlepší přístup k použití vlastního `Directory.Build.props` souboru spolu s generovanými projekty. Pak budete moci přispívat do struktury projektu bez narušování procesu generování. Další informace najdete [tady](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build#directorybuildprops-and-directorybuildtargets).

## <a name="breakpoints-with-a-warning"></a>Zarážky s upozorněním

Pokud Visual Studio nemůže najít zdrojové umístění pro konkrétní zarážku, zobrazí se upozornění kolem zarážky. Ověřte, že skript, který používáte, je správně načtený nebo použitý v aktuální scéně.

## <a name="breakpoints-not-hit"></a>Zarážky nejsou k dispozice

Ověřte, že skript, který používáte, je správně načtený nebo použitý v aktuální scéně. Ukončete aplikaci Visual Studio a Unity a pak odstraňte všechny generované soubory ( \* . csproj, \* . sln), `.vs` složku a celou složku knihovny. Další informace o ladění v C# najdete na [webu](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html)Unity.

## <a name="unable-to-debug-android-players"></a>Nepovedlo se ladit přehrávače pro Android.

Pro detekci přehrávačů používáme vícesměrové vysílání (což je výchozí mechanismus používaný v Unity), ale po použití běžného připojení TCP pro připojení ladicího programu. Fáze zjišťování je hlavním problémem pro zařízení s Androidem.

Wi-Fi je univerzální, ale ve srovnání s USB je v důsledku latence velmi pomalé. Zjistili jsme, že pro některé směrovače nebo zařízení chybí vhodná podpora vícesměrového vysílání (pro toto je dobře známá řada Nexus).

USB je velmi rychlé pro ladění a Visual Studio Tools for Unity teď dokáže detekovat zařízení USB a komunikovat se serverem ADB a správně převinout porty pro ladění.

## <a name="issues-with-intellisense-or-code-coloration"></a>Problémy s technologií IntelliSense nebo zbarvení kódu

Zkuste upgradovat Visual Studio na nejnovější verzi. Zkuste stejné kroky pro řešení potíží, jako u [nekompatibilních projektů](#incompatible-project-in-visual-studio).

## <a name="known-issues"></a>Známé problémy

V Visual Studio Tools for Unity jsou známé problémy, které vedou k tomu, jak ladicí program komunikuje se starší verzí kompilátoru jazyka C#. Pracujeme na tom, abychom vám pomohli tyto problémy vyřešit, ale mezitím se můžete setkat s následujícími problémy:

- V případě ladění aplikace Unity někdy dochází k chybě.

- V případě ladění se aplikace Unity někdy zablokuje.

- Rozkrokování a vyzkoušení metod se někdy chová nesprávně, zejména v iterátorech nebo v rámci příkazů Switch.

## <a name="report-errors"></a>Oznamovat chyby

Pomůžeme nám vylepšit kvalitu Visual Studio Tools for Unity odesláním zpráv o chybách, když dojde k chybě, zablokování nebo dalším chybám. To nám pomůže prozkoumat a opravit problémy v Visual Studio Tools for Unity. Děkujeme!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak ohlásit chybu při zablokování sady Visual Studio

K dispozici jsou sestavy, které Visual Studio někdy zablokuje při ladění pomocí Visual Studio Tools for Unity, ale potřebujeme více dat pro pochopení tohoto problému. Můžete nám pomohou prozkoumat podle následujících kroků.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Chcete-li ohlásit, že aplikace Visual Studio zablokuje při ladění pomocí Visual Studio Tools for Unity

*Ve Windows:*

1. Otevřete novou instanci sady Visual Studio.

1. Otevřete dialog připojit k procesu. V hlavní nabídce v nové instanci aplikace Visual Studio vyberte možnost **ladit**, **připojit k procesu**.

1. Připojte ladicí program k zmrazené instanci aplikace Visual Studio. V dialogovém okně **připojit k procesu** vyberte zmrazenou instanci sady Visual Studio z tabulky **Dostupné procesy** a pak klikněte na tlačítko **připojit** .

1. Pozastavit ladicí program. V nové instanci aplikace Visual Studio v hlavní nabídce zvolte možnost **ladit**, **přerušit vše** nebo stačí stisknout **kombinaci kláves CTRL + ALT + BREAK**.

1. Vytvořte výpis vlákna. V okno Příkaz zadejte následující příkaz a stiskněte klávesu **ENTER**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Může být nutné okno **příkazového** řádku zviditelnit jako první. V aplikaci Visual Studio v hlavní nabídce vyberte možnost **zobrazení**, **ostatní** okna, **příkazové okno**.

*Na počítači Mac:*

1. Otevřete terminál a získejte PID Visual Studio pro Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Spusťte ladicí program lldb:

    ```shell
    lldb
    ```

1. Připojte se k instanci Visual Studio pro Mac pomocí identifikátoru PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Načíst trasování zásobníku pro všechna vlákna:

    ```shell
    bt all
    ```

Nakonec pošlete výpis vlákna do [vstusp@microsoft.com](mailto:vstusp@microsoft.com) , spolu s popisem toho, co jste prováděli při zmrazení sady Visual Studio.

## <a name="see-also"></a>Viz také

- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
