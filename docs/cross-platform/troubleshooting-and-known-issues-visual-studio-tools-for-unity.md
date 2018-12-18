---
title: Řešení potíží a známé problémy (Visual Studio Tools for Unity) | Dokumentace Microsoftu
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
ms.openlocfilehash: 1c69c78e9a081680c6ee5279ddce1816bf500672
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027286"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Řešení potíží a známé problémy (Visual Studio Tools for Unity)

V této části vám najít řešení běžných potíží s nástroji Visual Studio Tools for Unity, popis známých problémů a zjistěte, jak můžete pomoci zvýšit zpráv o chybách Visual Studio Tools for Unity.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Řešení potíží s připojení mezi Unity a Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Potvrďte, že je povolená připojení editoru

V nabídce Unity vyberte **Upravit > Předvolby** a pak vyberte **externích nástrojů** kartu. Ujistěte se, že **Editor připojení** zaškrtávací políčko je povolená. Další informace najdete v tématu [dokumentace k Unity Předvolby](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nelze se připojit

- Zkuste dočasně zakázat antivirový nebo vytvoření pravidel vyloučení pro VS a Unity.
- Zkuste dočasně zakázat bránu firewall nebo vytvořit pravidla povolení protokolu TCP/UDP sítě mezi VS a Unity.
- Některé programy, jako je pomocí programu Team Viewer, může narušovat proces zjišťování. Zkuste dočasně pozastavit veškerý další software zobrazíte, pokud se něco změní.
- Nepřejmenovávejte hlavní spustitelný soubor Unity, protože VSTU pouze monitoruje procesy "Unity.exe".

## <a name="visual-studio-crashes"></a>Dojde k chybě sady Visual Studio

Tento problém může být způsobeno mezipaměť Visual Studio MEF je poškozený.

Odstraňte následující složku resetovat mezipaměť MEF (zavřete sadu Visual Studio před provedením této akce):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

To by měl váš problém vyřešit. V případě, že stále dochází k problému, spusťte příkazový řádek vývojáře pro sadu Visual Studio jako správce a použijte následující příkaz:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio přestane reagovat

Několik modulů plug-in Unity, jako jsou analýzy, FMOD, JÍMKU (univerzální přehrávač), ZFBrowser nebo vložený prohlížeče jsou pomocí nativních vláken. Protože představuje problém, když modul plug-in končí nativních vláken se připojuje k modulu runtime, který potom provede blokování volání do operačního systému. To znamená Unity nelze přerušit bylo vlákno pro ladicí program (nebo opětovné načtení domény) a přestane reagovat.

Fmod –, existuje alternativní řešení, můžete předat `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` inicializace [příznak](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) zakázat asynchronního zpracování a provádět veškeré zpracování na hlavním vlákně.

## <a name="incompatible-project-in-visual-studio"></a>Nekompatibilní projektu v sadě Visual Studio

Nejdřív zkontrolujte, že Visual Studio je nastavena jako externí skript editoru Unity (úpravy/předvolby/externí nástroje). Potom zkontrolujte, jestli je modul plug-in sady Visual Studio nainstalovaný v Unity (Nápověda/o musí zobrazit zpráva, jako je Microsoft Visual Studio Tools for Unity je povolená v dolní části). Zkontrolujte, že rozšíření je správně nainstalované v sadě Visual Studio (Nápověda/o).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Navíc opětovné načtení, nebo Visual Studio ztráty všechna otevřená okna.

Ujistěte se, že nikdy touch soubory projektu přímo z procesor asset nebo jakýkoli jiný nástroj. Pokud opravdu potřebujete k práci s souboru projektu, jsme k tomu vystavit rozhraní API. Zkontrolujte, zda [sestavení odkazuje na část problémy](#Assembly-reference-issues).

Pokud máte navíc opětovné načtení, nebo pokud ztráty sady Visual Studio znovu načíst všechny otevřené Windows na, ujistěte se, že máte správné balíčky .NET targeting Pack. Zkontrolujte následující část o rozhraní pro další informace.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Ladicí program není přerušit na výjimkách

Pokud používáte starší verzi modulu runtime Unity (ekvivalent .NET 3.5), ladicí program přeruší vždy po neošetřené výjimce (tzn. mimo blok try/catch). Pokud je výjimka ošetřena, ladicí program použije v okně Nastavení výjimky k určení, zda přerušení je povinný, nebo ne.

Pomocí nového modulu runtime (ekvivalent .NET 4.6) Unity zavedl nový způsob, jak spravovat uživatelské výjimky a v důsledku toho jsou všechny výjimky považovány za "uživatel zpracované" i v případě, že jsou mimo blok try/catch. To je důvod, proč je teď potřeba explicitně je kontrolovat v okně Nastavení výjimek, pokud chcete přerušení ladicího programu.

V okně Nastavení výjimek (ladění > Windows > Nastavení výjimek), rozbalte uzel pro kategorii výjimek (například běžné výjimky modulu CLR, což znamená výjimky .NET) a zaškrtněte políčko pro určité výjimky, které chcete zachytit v rámci dané kategorie (například System.NullReferenceException). Můžete také vybrat celou kategorii výjimek.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Na Windows Visual Studio výzvu ke stažení Cílová architektura Unity

Visual Studio Tools for Unity vyžaduje rozhraní .NET framework 3.5, který není nainstalovaný ve výchozím nastavení ve Windows 8 nebo 10. Chcete-li vyřešit tento problém, postupujte podle pokynů ke stažení a instalaci rozhraní .NET framework 3.5.

Pokud používáte nový modul runtime Unity, se rovněž vyžadují, targeting Pack verzi rozhraní .NET 4.6 a 4.7.1. Je možné použít instalační program VS2017 k rychlé instalaci (Upravit instalací VS2017, jednotlivé komponenty, .NET, vyberte kategorii všechny 4.x targeting Pack).

## <a name="assembly-reference-issues"></a>Problémy odkaz na sestavení

Pokud váš projekt je komplexní reference-wise nebo pokud chcete lepší kontrolu nad tento krok generování, můžete použít naši [API](../cross-platform/customize-project-files-created-by-vstu.md) pro manipulaci s vygenerovaný obsah projektu nebo řešení. Můžete také použít [soubory odpovědí](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) v Unite projektu a my vám jejich zpracování.

## <a name="breakpoints-with-a-warning"></a>Zarážky s upozorněním

Pokud není schopen vyhledat zdrojové umístění pro zarážku konkrétní sady Visual Studio se zobrazí upozornění kolem vaší zarážce. Zkontrolujte, že skript, který používáte správně načíst nebo použít aktuální scény Unity.

## <a name="breakpoints-not-hit"></a>Není zarážky

Zkontrolujte, že skript, který používáte správně načíst nebo použít aktuální scény Unity. Ukončení sady Visual Studio a Unity pak odstraňte všechny vygenerované soubory (\*.csproj, \*.sln) a na celou složku knihovny.

## <a name="unable-to-debug-android-players"></a>Nelze ladit aktérů Androidu

Můžeme použít vícesměrové vysílání pro přehrávač detekce (což je výchozí mechanismus používaný Unity), ale po, který používáme regulární připojení TCP připojení ladicího programu. Fázi zjišťování je hlavní problém pro zařízení s Androidem.

Wi-Fi je univerzální, ale velmi pomalý kvůli latenci v porovnání s USB. Jsme viděli nedostatek správné podpora vícesměrového vysílání pro některá zařízení (Nexus řady jsou dobře známé pro tento) nebo směrovače.

Je mimořádně rychlým pro ladění USB a Visual Studio Tools for Unity je teď možné zjišťovat jiná zařízení USB a Pobavte se se server adb správně přesměrování portů pro ladění.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problémy s Visual Studio 2015 a technologie IntelliSense nebo kód zabarvení

Zkuste ho upgradovat vaše Visual Studio 2015 update 3.

## <a name="known-issues"></a>Známé problémy

 Jsou známy problémy ve Visual Studio Tools for Unity, které jsou výsledkem způsobu interakce ladicí program Unity a starší verzi kompilátoru jazyka C#. Pracujeme na řešení těchto problémů, ale do té doby může dojít k následujícím problémům:

- Při ladění Unity někdy dojde k chybě.

- Při ladění, se zablokuje někdy Unity.

- Krokování do proměnné a z metody v některých případech se chová nesprávně, zejména v iterátory nebo v rámci příkazů přepínače.

## <a name="report-errors"></a>Hlášení chyb

 Pomozte nám zlepšovat kvalitu Visual Studio Tools for Unity odesíláním zpráv o chybách, když dochází k chybám, zablokuje nebo jiné chyby. To pomáhá nám prozkoumat a řešit problémy ve Visual Studio Tools for Unity. Děkuju!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak ohlásit chybu, když Visual Studio zamrzne

 Existují sestavy, které Visual Studio zamrzne někdy při ladění pomocí Visual Studio Tools for Unity, ale potřebujeme víc dat, abyste pochopili tento problém. Pomůžete nám prozkoumat pomocí následujících kroků.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Pro sestavu, která sadě Visual Studio se zablokuje při ladění se sadou Visual Studio Tools for Unity

*Ve Windows:*

1. Otevřete novou instanci sady Visual Studio.

1. Otevřete dialogu připojit k procesu. V nové instanci sady Visual Studio, v hlavní nabídce zvolte **ladění**, **připojit k procesu**.

1. Připojte ladicí modul k zmrazené instanci sady Visual Studio. V **připojit k procesu** dialogového okna, vyberte zmrazené instanci sady Visual Studio z **procesy k dispozici** tabulku a pak zvolte **připojit** tlačítko.

1. Pozastavte ladicí program. V nové instanci sady Visual Studio, v hlavní nabídce zvolte **ladění**, **příkaz Pozastavit vše**, nebo stačí stisknout kombinaci kláves **Ctrl + Alt + Break**.

1. Vytvoření výpisu podprocesu. V příkazovém řádku zadejte následující příkaz a stiskněte klávesu **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Možná budete muset provést **příkaz** okno viditelné první. V sadě Visual Studio, zvolte v hlavní nabídce **zobrazení**, **ostatní Windows**, **příkazové okno**.

*Na počítači Mac:*

1. Otevřete terminál a získejte identifikátor PID sady Visual Studio pro Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Spusťte ladicí program lldb:

    ```shell
    lldb
    ```

1. Připojení k sadě Visual Studio pro Mac instance pomocí PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Získat trasování zásobníku pro všechna vlákna:

    ```shell
    bt all
    ```

Nakonec odešlete výpisu vlákna do [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), spolu s popis co jste dělali při začal být zmrazené sady Visual Studio.
