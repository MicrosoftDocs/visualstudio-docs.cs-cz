---
title: Ladění pomocí ladicího programu za běhu | Microsoft Docs
description: Ladění pomocí ladicího programu za běhu v Visual Studio. Ladění za běhu se může spustit automaticky Visual Studio, když dojde k chybám nebo chybám aplikace.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bdd35056706491ace6e5e6b2f7c3f6a45464d2e
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729244"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Ladění pomocí ladicího programu za běhu v Visual Studio

Ladění za běhu se může spustit automaticky Visual Studio, když aplikace běží mimo Visual Studio nebo dojde k chybě. S laděním za běhu můžete testovat aplikace mimo Visual Studio a otevřít Visual Studio a zahájit ladění, když dojde k problému.

Ladění za běhu funguje u desktopových aplikací pro Windows. Nefunguje pro univerzální aplikace pro Windows ani pro spravovaný kód hostovaný v nativní aplikaci, jako jsou vizualizéry.

> [!TIP]
> Pokud chcete jenom zabránit zobrazení dialogového okna Ladicí program za běhu, ale nemáte nainstalované Visual Studio, podívejte se na zakázání ladicího programu za [běhu.](../debugger/just-in-time-debugging-in-visual-studio.md) Pokud jste už Visual Studio nainstalovali, možná budete muset zakázat ladění za běhu [z registru Systému Windows.](#disable-just-in-time-debugging-from-the-windows-registry)

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Povolení nebo zakázání ladění za běhu v Visual Studio

>[!NOTE]
>Pokud chcete povolit nebo zakázat ladění za běhu, musíte Visual Studio jako správce. Povolením nebo zakázáním ladění za běhu se nastaví klíč registru a ke změně tohoto klíče se mohou potřebná oprávnění správce. Pokud chcete Visual Studio jako správce, klikněte pravým tlačítkem na aplikaci Visual Studio a zvolte **Spustit jako správce.**

Ladění za běhu můžete nakonfigurovat v dialogovém Visual Studio  >  **Nástroje** (nebo  >  Možnosti ladění).

**Povolení nebo zakázání ladění za běhu:**

1. V nabídce **Nástroje** **nebo Ladit** vyberte **Možnosti**  >  **Ladění**  >  **za běhu**.

   ![Povolení nebo zakázání ladění JIT](../debugger/media/dbg-jit-enable-or-disable.png "Povolit nebo zakázat ladění JIT")

1. V poli **Povolit** ladění za běhu pro tyto typy kódu vyberte typy kódu, které má ladění za běhu ladit: **Spravované,** Nativní nebo **Skript**.

1. Vyberte **OK**.

Pokud povolíte ladicí program za běhu, ale neotevře se, když dojde k chybě nebo chybám aplikace, přečtěte si téma [řešení ladění za běhu](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deaktivace ladění za běhu z registru systému Windows

Ladění za běhu se může pořád povolit i v případě, že už není v počítači nainstalovaná aplikace Visual Studio. Pokud již není nainstalována aplikace Visual Studio, můžete ladění za běhu zakázat úpravou registru systému Windows.

**Chcete-li zakázat ladění za běhu úpravou registru:**

1. V nabídce **Start** systému Windows spusťte **Editor registru** (*regedit.exe*).

2. V okně **Editoru registru** vyhledejte a odstraňte následující položky registru:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Klíč registru JIT](../debugger/media/dbg-jit-registry.png "Klíč registru JIT")

3. Pokud je v počítači spuštěný 64 operační systém, odstraňte také následující položky registru:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Ujistěte se, že neodstraňujte ani neměníte žádné jiné klíče registru.

5. Zavřete okno **Editor registru** .

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Povolit ladění za běhu formuláře Windows

Ve výchozím nastavení mají aplikace Windows Form obslužné rutiny výjimky nejvyšší úrovně, která umožňuje, aby aplikace běžela i v případě, že je možné ji obnovit. Pokud model Windows Forms aplikace vyvolá neošetřenou výjimku, zobrazí se následující dialogové okno:

![Neošetřená výjimka Windows Form](../debugger/media/windowsformsunhandledexception.png "Neošetřená výjimka Windows Form")

Pokud chcete povolit ladění za běhu místo standardního zpracování chyb Windows Form, přidejte tato nastavení:

- V `system.windows.forms` části souboru *machine.config* *\<app name> nebo.exe.config* nastavte hodnotu `jitDebugging` na `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- V aplikaci C++ Windows Form také nastavte na `DebuggableAttribute` v `true` souboru *.config* nebo ve vašem kódu. Pokud kompilujete [s /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) a bez [/Og](/cpp/build/reference/og-global-optimizations), kompilátor nastaví tento atribut za vás. Pokud ale chcete ladit ne optimalizované sestavení verze, musíte ho nastavit přidáním následujícího řádku do souboru `DebuggableAttribute` *AssemblyInfo.cpp* vaší aplikace:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Další informace naleznete v tématu <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Použití ladění za běhu
Tento příklad vás provede laděním za běhu, když aplikace vyvolá chybu.

- Pokud chcete postupovat Visual Studio, musíte mít nainstalovanou instalaci. Pokud nemáte verzi Visual Studio, můžete si stáhnout [bezplatnou verzi Visual Studio Community Edition.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)

- Ujistěte se, že je [](#BKMK_Enabling) v části Nástroje Možnosti Ladění za běhu povolené  >    >    >  **ladění za běhu.**

V tomto příkladu vytvoříme konzolovou aplikaci v jazyce C# v Visual Studio která vyvolá [výjimku NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. V Visual Studio konzolovou aplikaci C# (**Soubor** nový projekt  >    >    >  **Konzolová aplikace Visual C#**) s názvem  >   *ThrowsNullException*. Další informace o vytváření projektů v Visual Studio tématu [Návod: Vytvoření jednoduché aplikace](../get-started/csharp/tutorial-wpf.md).

1. Když se projekt otevře v Visual Studio, otevřete *soubor Program.cs.* Nahraďte metodu Main() následujícím kódem, který vytiskne řádek do konzoly a potom vyvolá výjimku NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Pokud chcete sestavit řešení, zvolte konfiguraci **Ladit** (výchozí) nebo **Vypustit** a pak vyberte **Sestavit**  >  **znovu sestavit řešení.**

   > [!NOTE]
   > - Pro **úplné ladění** zvolte Konfigurace ladění.
   > - Pokud vyberete [možnost Konfigurace](../debugger/how-to-set-debug-and-release-configurations.md) verze, je nutné vypnout [Pouze můj kód](../debugger/just-my-code.md) tento postup fungovat. V **části Nástroje**  >  **Možnosti**  >  **Ladění** zrušte výběr možnosti Povolit **Pouze můj kód**.

   Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

1. Otevřete sestavenou aplikaci *ThrowsNullException.exe* ve složce projektu C# (*. ..\ThrowsNullException\ThrowsNullException\bin\Debug* nebo *. ..\ThrowsNullException\ThrowsNullException\bin\Release*).

   Mělo by se zobrazit následující příkazové okno:

   ![Snímek obrazovky konzoly pro ThrowsNullException.exe, která vyvolá neošetřenou výjimku s nulovým odkazem (System. NullReferenceException).](../debugger/media/throwsnullexceptionconsole.png)

1. Otevře se dialogové okno **zvolit ladicí program za běhu** .

   ![Snímek obrazovky dialogového okna zvolit ladicí program za běhu, které se zobrazí po zobrazení výjimky v okně konzoly ThrowsNullException.exe.](../debugger/media/justintimedialog.png)

   V části **dostupné ladicí programy** vyberte možnost **\<your preferred Visual Studio version/edition> Nová instance**, pokud ještě není vybraná.

1. Vyberte **OK**.

   Projekt ThrowsNullException se otevře v nové instanci sady Visual Studio, přičemž provádění se zastavilo na řádku, který vyvolal výjimku:

   ![Snímek projektu ThrowsNullException v aplikaci Visual Studio s zvýrazněním řádku zdrojového kódu, který vyvolal výjimku.](../debugger/media/nullreferencesecondinstance.png)

V tomto okamžiku můžete spustit ladění. Pokud jste ladění reálné aplikace, museli byste zjistit, proč kód vyvolává výjimku.

> [!CAUTION]
> Pokud vaše aplikace obsahuje nedůvěryhodný kód, zobrazí se dialogové okno upozornění zabezpečení, které vám umožní rozhodnout, zda chcete pokračovat v ladění. Než budete pokračovat v ladění, rozhodněte se, jestli kód důvěřujete. Napsali jste kód sami? Pokud je aplikace spuštěná na vzdáleném počítači, znáte název procesu? Pokud je aplikace spuštěná místně, zvažte možnost spouštění škodlivého kódu v počítači. Pokud se rozhodnete, že je kód důvěryhodný, vyberte **OK**. V opačném případě vyberte **Zrušit**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Řešení ladění za běhu

Pokud se ladění za běhu nespustí, když aplikace selže, i když je povolená v aplikaci Visual Studio:

- Zasílání zpráv o chybách systému Windows může na vašem počítači převezme zpracování chyb.

  Pokud chcete tento problém vyřešit, pomocí Editoru registru  přidejte hodnotu **DWORD** **Disabled** s hodnotou **1** do následujících klíčů registru:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Pro 64bitové počítače): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Další informace najdete v tématu [. Nastavení WER](/windows/desktop/wer/wer-settings).

- Známý problém s Windows může způsobit selhání ladicího programu za běhu.

  Opravou je přidání **hodnoty DWORD** **Auto** s daty **hodnoty** **1** do následujících klíčů registru:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Pro 64bitové počítače): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Během ladění za běhu se můžou zobrazit následující chybové zprávy:

- **Nelze se připojit k procesu, který havaruje. Zadaný program není program systému Windows ani MS-DOS.**

    Ladicí program se pokusil připojit k procesu spuštěnému pod jiným uživatelem.

    Pokud chcete tento problém vyřešit, otevřete v Visual Studio připojit k procesu ladění (nebo stiskněte  >   **Ctrl**  +  **Alt**  +  **P)** a v seznamu Dostupné procesy vyhledejte proces, který **chcete ladit.** Pokud název procesu neznáme, vyhledejte ID procesu v dialogovém **Visual Studio ladicího** programu za běhu. V seznamu Dostupné procesy **vyberte** proces a vyberte **Připojit.** Výběrem **ne** zavřete dialogové okno ladicího programu za běhu.

- **Ladicí program se nepokusil spustit, protože není přihlášený žádný uživatel.**

    Ke konzole není přihlášený žádný uživatel, takže neexistuje žádná uživatelská relace pro zobrazení dialogového okna ladění za běhu.

    Pokud chcete tento problém vyřešit, přihlaste se k počítači.

- **Třída není zaregistrovaná.**

    Ladicí program se pokusil vytvořit třídu COM, která není registrována, pravděpodobně v důsledku problému s instalací.

    Chcete-li tento problém vyřešit, použijte Instalační program pro Visual Studio k přeinstalaci nebo opravě instalace sady Visual Studio.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Možnosti, ladění, dialogové okno za běhu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Upozornění zabezpečení: připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
