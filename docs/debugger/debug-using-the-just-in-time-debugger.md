---
title: Ladění pomocí ladicího programu za běhu | Microsoft Docs
description: Ladění pomocí ladicího programu za běhu v aplikaci Visual Studio. Ladění za běhu může Visual Studio spouštět automaticky, když dojde k chybám nebo selháním aplikace.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a03afa64d19e3ccd0efbb170b4305049f6bfee30
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761339"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Ladění pomocí ladicího programu za běhu v aplikaci Visual Studio

Ladění za běhu může Visual Studio spouštět automaticky, když aplikace běží mimo Visual Studio chyby nebo selhání. S laděním za běhu můžete testovat aplikace mimo sadu Visual Studio a otevřít Visual Studio a začít ladit, když dojde k problému.

Ladění za běhu funguje pro desktopové aplikace pro Windows. Nefunguje pro univerzální aplikace pro Windows ani pro spravovaný kód, který je hostovaný v nativní aplikaci, jako jsou například nástroje pro vizualizace.

> [!TIP]
> Pokud chcete pouze zastavit dialogové okno ladicí program za běhu, ale nemáte nainstalovanou aplikaci Visual Studio, přečtěte si téma [zakázání ladicího programu za běhu](../debugger/just-in-time-debugging-in-visual-studio.md). Pokud jste nainstalovali aplikaci Visual Studio, může být nutné [Zakázat ladění za běhu z registru systému Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Povolení nebo zakázání ladění za běhu v aplikaci Visual Studio

>[!NOTE]
>Pokud chcete povolit nebo zakázat ladění za běhu, musíte spustit aplikaci Visual Studio jako správce. Povolení nebo zakázání ladění za běhu nastaví klíč registru a oprávnění správce se může vyžadovat ke změně tohoto klíče. Chcete-li otevřít aplikaci Visual Studio jako správce, klikněte pravým tlačítkem myši na aplikaci Visual Studio a vyberte možnost **Spustit jako správce**.

Ladění za běhu můžete nakonfigurovat z dialogového okna možnosti **nástrojů** sady Visual Studio  >   (nebo   >  **Možnosti** ladění).

**Chcete-li povolit nebo zakázat ladění za běhu:**

1. V nabídce **nástroje** nebo **ladění** vyberte **Možnosti**  >  **ladění**  >  **za běhu**.

   ![Povolit nebo zakázat ladění JIT](../debugger/media/dbg-jit-enable-or-disable.png "Povolit nebo zakázat ladění JIT")

1. V poli **Povolit ladění za běhu pro tyto typy kódu** vyberte typy kódu, které chcete ladit za běhu, pro ladění: **spravované**, **nativní** a **/nebo.**

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

- V `system.windows.forms` části *machine.config* nebo *\<app name>.exe.config* souboru nastavte `jitDebugging` hodnotu na `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- Ve formulářové aplikaci C++ Windows také nastavte `DebuggableAttribute` na hodnotu `true` v souboru *. config* nebo ve vašem kódu. Pokud kompilujete pomocí [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) a bez [/og](/cpp/build/reference/og-global-optimizations), kompilátor tento atribut nastaví za vás. Pokud chcete ladit neoptimalizované sestavení pro vydání, je však nutné nastavit `DebuggableAttribute` přidáním následujícího řádku do souboru *AssemblyInfo. cpp* vaší aplikace:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Další informace naleznete v tématu <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Použít ladění za běhu
Tento příklad vás provede laděním za běhu, když aplikace vyvolá chybu.

- Abyste mohli postupovat podle těchto kroků, musíte mít nainstalovanou aplikaci Visual Studio. Pokud nemáte Visual Studio, můžete si stáhnout bezplatnou [edici Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Ujistěte se, že je [povoleno](#BKMK_Enabling) ladění za běhu v **nástrojích**  >  **Možnosti**  >  **ladění** za  >  **běhu**.

V tomto příkladu vytvoříte konzolovou aplikaci v jazyce C# v aplikaci Visual Studio, která vyvolá [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. V aplikaci Visual Studio vytvořte konzolovou aplikaci v jazyce C# (**soubor**  >  **Nový**  >  **projekt**  >  **Visual C#**  >  **Konzolová aplikace**) s názvem *ThrowsNullException*. Další informace o vytváření projektů v aplikaci Visual Studio naleznete v tématu [Návod: Vytvoření jednoduché aplikace](../get-started/csharp/tutorial-wpf.md).

1. Po otevření projektu v aplikaci Visual Studio otevřete soubor *program.cs* . Metodu Main () nahraďte následujícím kódem, který vytiskne čáru do konzoly a poté vyvolá výjimku NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Chcete-li sestavit řešení, zvolte buď **ladění** (výchozí) nebo konfigurace **verze** , a pak vyberte **sestavení znovu**  >  **Sestavit řešení**.

   > [!NOTE]
   > - Pro úplné ladění vyberte možnost konfigurace **ladění** .
   > - Pokud vyberete možnost konfigurace [vydané verze](../debugger/how-to-set-debug-and-release-configurations.md) , je nutné vypnout [pouze můj kód](../debugger/just-my-code.md) , aby tento postup fungoval. V části **nástroje**  >    >  **ladění** možností vyberte možnost **Povolit pouze můj kód**.

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

- Zasílání zpráv o chybách systému Windows mohl převzít zpracování chyb v počítači.

  Chcete-li tento problém vyřešit, použijte Editor registru a přidejte **hodnotu DWORD** **disabled** s **hodnotou data** **1** do následujících klíčů registru:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Pro 64 počítače): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Další informace najdete v tématu [. Nastavení WER](/windows/desktop/wer/wer-settings).

- Známý problém se systémem Windows může způsobit selhání ladicího programu za běhu.

  Opravou je přidání **hodnoty DWORD** **auto**, s **hodnotou data** **1**, do následujících klíčů registru:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Pro 64 počítače): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Během ladění za běhu se může zobrazit tato chybová zpráva:

- **Nepovedlo se připojit k procesu selhání. Zadaný program není program systému Windows nebo MS-DOS.**

    Ladicí program se pokusil připojit k procesu spuštěnému v rámci jiného uživatele.

    Pokud chcete tento problém obejít, otevřete v aplikaci Visual Studio příkaz **ladit**  >  **připojit k procesu** a v seznamu **procesy k dispozici** vyhledejte proces, který chcete ladit. Pokud neznáte název procesu, vyhledejte ID procesu v dialogovém okně **ladicí program pro dobu běhu sady Visual Studio** . Vyberte proces v seznamu **procesy k dispozici** a vyberte **připojit**. Pokud chcete zavřít dialogové okno ladicí program za běhu, vyberte **ne** .

- **Ladicí program nemohl být spuštěn, protože není přihlášen žádný uživatel.**

    K konzole není přihlášený žádný uživatel, takže není k dispozici žádná uživatelská relace pro zobrazení dialogového okna pro ladění za běhu.

    Pokud chcete tento problém vyřešit, přihlaste se do počítače.

- **Třída není zaregistrovaná.**

    Ladicí program se pokusil vytvořit třídu COM, která není registrována, pravděpodobně v důsledku problému s instalací.

    Chcete-li tento problém vyřešit, použijte Instalační program pro Visual Studio k přeinstalaci nebo opravě instalace sady Visual Studio.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Možnosti, ladění, dialogové okno za běhu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Upozornění zabezpečení: připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
