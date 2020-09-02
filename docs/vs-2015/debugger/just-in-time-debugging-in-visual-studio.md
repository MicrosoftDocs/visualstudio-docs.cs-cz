---
title: Ladění za běhu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690599"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Ladění za běhu v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění za běhu spustí Visual Studio automaticky, když dojde k výjimce nebo chybě v aplikaci, která běží mimo aplikaci Visual Studio. To vám umožní otestovat aplikaci, když není spuštěná aplikace Visual Studio, a při výskytu problému zahájit ladění pomocí sady Visual Studio.

Ladění za běhu funguje pro desktopové aplikace pro Windows. Nefunguje pro univerzální aplikace pro Windows a nefunguje pro spravovaný kód, který je hostovaný v nativní aplikaci, jako jsou například nástroje pro vizualizace.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> Zobrazí se dialogové okno ladicí program za běhu při pokusu o spuštění aplikace?

Akce, které byste měli provést po zobrazení dialogového okna program pro ladění za běhu sady Visual Studio, závisí na tom, co se pokoušíte provést:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Pokud se chcete zbavit dialogového okna a spustit aplikaci pouze normálně

1. (Pokročilí uživatelé) Pokud máte nainstalovanou aplikaci Visual Studio (nebo jste ji dříve nainstalovali a odebrali), [zakažte ladění za běhu](#BKMK_Enabling) a zkuste aplikaci znovu spustit.

2. Pokud používáte webovou aplikaci v aplikaci Internet Explorer, zakažte ladění skriptů.

    Zakáže ladění skriptů v dialogovém okně Možnosti Internetu. K tomu můžete přistupovat z **ovládacích panelů**  /  **síť a**  /  **Možnosti** Internetu (přesný postup závisí na vaší verzi Windows a Internet Exploreru).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Znovu otevřete webovou stránku, na které jste narazili na chybu. Pokud se tím problém nevyřeší, obraťte se na vlastníka webové aplikace, aby problém vyřešil.

4. Pokud používáte jiný typ aplikace pro Windows, budete se muset obrátit na vlastníka aplikace a opravit chybu a pak znovu nainstalovat opravenou verzi aplikace.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Pokud chcete opravit nebo ladit chybu (pokročilí uživatelé)

- Chcete-li zobrazit podrobné informace o chybě a pokusu o ladění, je nutné mít [nainstalovanou aplikaci Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) . Podrobné pokyny najdete v tématu [použití JIT](#BKMK_Using_JIT) . Pokud nemůžete chybu vyřešit a opravit aplikaci, požádejte vlastníka aplikace, aby chybu vyřešil.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Povolení nebo zakázání ladění za běhu
 Můžete povolit nebo zakázat ladění za běhu z dialogového okna **Nástroje/možnosti** aplikace Visual Studio.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Povolení nebo zakázání ladění za běhu

1. Otevřete sadu Visual Studio. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. V dialogovém okně **Možnosti** vyberte složku **ladění** .

3. Ve složce **ladění** **Vyberte stránku za běhu.**

4. V poli **Povolit ladění za běhu těchto typů kódu** zaškrtněte nebo zrušte zaškrtnutí příslušných typů programů: **spravované**, **nativní**nebo **skript**.

    Chcete-li zakázat ladění za běhu, je-li povoleno, je nutné spustit s oprávněními správce. Povolením ladění za běhu nastavíte klíč registru a ke změně tohoto klíče se vyžadují oprávnění správce.

5. Klikněte na **OK**.

   Ladění za běhu se může pořád povolit i v případě, že už není v počítači nainstalovaná aplikace Visual Studio. Pokud není nainstalována aplikace Visual Studio, nelze zakázat ladění za běhu z dialogového okna **Možnosti** aplikace Visual Studio. V takovém případě můžete ladění za běhu zakázat úpravou registru systému Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Postup vypnutí ladění za běhu úpravou registru

1. V nabídce **Start** vyhledejte a spusťte příkaz. `regedit.exe`

2. V okně **Editoru registru** vyhledejte a odstraňte následující položky registru:

    - HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\DbgManagedDebugger

3. Pokud je v počítači spuštěný 64 operační systém, odstraňte také následující položky registru:

    - HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\DbgManagedDebugger

4. Je potřeba dbát na to, aby nedošlo k náhodnému odstranění nebo změně dalších klíčů registru.

5. Zavřete okno **Editor registru** .

> [!NOTE]
> Pokud se snažíte zakázat ladění za běhu pro aplikaci na straně serveru a tyto kroky problém nevyřeší, vypněte v nastavení aplikace IIS ladění na straně serveru a zkuste to znovu.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Povolení ladění za běhu formuláře Windows

1. Ve výchozím nastavení mají model Windows Forms aplikace obslužnou rutinu výjimky nejvyšší úrovně, která umožňuje programu pokračovat v běhu, pokud jej lze obnovit. Například pokud vaše aplikace model Windows Forms vyvolá neošetřenou výjimku, zobrazí se dialogové okno podobné následujícímu:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Chcete-li povolit ladění model Windows Forms aplikace za běhu, je nutné provést následující další kroky:

2. Nastavte `jitDebugging` hodnotu na `true` v `system.windows.form` části machine.config nebo *\<application name>*.exe.config souboru:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. Ve formulářové aplikaci C++ Windows je také nutné nastavit `DebuggableAttribute` v souboru. config nebo ve vašem kódu. Pokud kompilujete pomocí [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) a bez [/og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), kompilátor tento atribut nastaví za vás. Chcete-li ladit neoptimalizované sestavení pro vydání, je však nutné nastavit toto sami. To můžete provést přidáním následujícího řádku do souboru AssemblyInfo. cpp vaší aplikace:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Další informace naleznete v tématu <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Použít ladění za běhu
 V této části se dozvíte, co se stane, když spustitelný soubor vyvolá výjimku.

 Abyste mohli postupovat podle těchto kroků, musíte mít nainstalovanou aplikaci Visual Studio. Pokud nemáte Visual Studio, můžete si stáhnout bezplatnou [edici Visual Studio 2015 Community](https://visualstudio.microsoft.com/vs/older-downloads/).

 Při instalaci sady Visual Studio je ladění za běhu povoleno ve výchozím nastavení.

 Pro účely této části vytvoříme konzolovou aplikaci v jazyce C# v aplikaci Visual Studio, která vyvolá <xref:System.NullReferenceException> .

 V aplikaci Visual Studio vytvořte konzolovou aplikaci v jazyce C# (**soubor/nový/projekt/Visual C#/Konzolová aplikace**) s názvem **ThrowsNullException**. Další informace o vytváření projektů v aplikaci Visual Studio naleznete v tématu [Návod: Vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Po otevření projektu v aplikaci Visual Studio otevřete soubor Program.cs. Metodu Main () nahraďte následujícím kódem, který vytiskne čáru do konzoly a poté vyvolá výjimku NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Aby tento postup fungoval v [konfiguraci vydané verze](../debugger/how-to-set-debug-and-release-configurations.md), je potřeba vypnout [pouze můj kód](../debugger/just-my-code.md). V aplikaci Visual Studio klikněte na **Nástroje/možnosti**. V dialogovém okně **Možnosti** vyberte **ladění**. Odstraňte kontrolu z **pouze můj kód povolit**.

 Sestavte řešení (v aplikaci Visual Studio klikněte na **sestavit nebo znovu sestavit řešení**). Můžete zvolit buď ladění, nebo konfiguraci vydané verze. Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

 Proces sestavení vytvoří spustitelný ThrowsNullException.exe. Můžete ji najít ve složce, ve které jste vytvořili projekt C#: **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** nebo **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 Dvakrát klikněte na ThrowsNullException.exe. Mělo by se zobrazit příkazové okno takto:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Po několika sekundách se zobrazí okno s chybou:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Neklepejte na tlačítko **Storno**. Po několika sekundách by se měla zobrazit dvě tlačítka, **ladit** a **ukončit program**. Klikněte na položku **ladit**.

> [!CAUTION]
> Pokud vaše aplikace obsahuje nedůvěryhodný kód, zobrazí se dialogové okno s upozorněním zabezpečení. Toto dialogové okno umožňuje rozhodnout, zda chcete pokračovat v ladění. Než budete pokračovat v ladění, rozhodněte se, zda kód důvěřujete. Napsali jste kód sami? Důvěřujete programátor? Pokud je aplikace spuštěná na vzdáleném počítači, znáte název procesu? I v případě, že je aplikace spuštěna místně, neznamená to nutně, že může být důvěryhodná. Zvažte možnost spouštění škodlivého kódu v počítači. Pokud se rozhodnete, že kód, který se chystáte ladit, je důvěryhodný, klikněte na tlačítko **ladit**. V opačném případě klikněte na **neladit**.

 Zobrazí se okno **ladění za běhu sady Visual Studio** :

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 V části **možné ladicí programy**byste měli vidět, že je vybraná **nová instance Microsoft Visual Studio 2015** řádek. Pokud už není vybraná, vyberte ho hned teď.

 V dolní části okna v části chcete **ladit pomocí vybraného ladicího programu?** klikněte na **Ano**.

 Projekt ThrowsNullException se otevře v nové instanci sady Visual Studio, přičemž provádění se zastavilo na řádku, který vyvolá výjimku:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 V tomto okamžiku můžete spustit ladění. Pokud se jednalo o skutečnou aplikaci, museli byste zjistit, proč kód vyvolává výjimku.

## <a name="just-in-time-debugging-errors"></a>Chyby ladění za běhu
 Pokud se dialogové okno nezobrazí, když dojde k chybě programu, může to být způsobeno Zasílání zpráv o chybách systému Windowsmi nastaveními v počítači. Další informace najdete v tématu [. Nastavení WER](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Může se zobrazit následující chybové zprávy, které jsou přidruženy k ladění za běhu.

- **Nepovedlo se připojit k procesu selhání. Zadaný program není program systému Windows nebo MS-DOS.**

     K této chybě dochází, když se pokusíte připojit k procesu spuštěnému jako jiný uživatel.

     Chcete-li tento problém obejít, spusťte aplikaci Visual Studio, otevřete dialogové okno **připojit k procesu** z nabídky **ladění** a v seznamu **procesy k dispozici** vyhledejte proces, který chcete ladit. Pokud neznáte název procesu, podívejte se do dialogového okna **ladicí program za běhu sady Visual Studio** a poznamenejte si ID procesu. Vyberte proces v seznamu **procesy k dispozici** a klikněte na **připojit**. V dialogovém okně **programu pro ladění za běhu sady Visual Studio** kliknutím na tlačítko **ne** zavřete dialogové okno.

- **Ladicí program nemohl být spuštěn, protože není přihlášen žádný uživatel.**

     K této chybě dojde, když se ladění za běhu pokusí spustit aplikaci Visual Studio na počítači, ve kterém není k konzole přihlášen žádný uživatel. Vzhledem k tomu, že není přihlášen žádný uživatel, není k dispozici žádná uživatelská relace pro zobrazení dialogového okna pro ladění za běhu.

     Pokud chcete tento problém vyřešit, přihlaste se do počítače.

- **Třída není zaregistrovaná.**

     Tato chyba označuje, že ladicí program se pokusil vytvořit třídu COM, která není registrována, pravděpodobně v důsledku problému s instalací.

     Chcete-li tento problém vyřešit, přeinstalujte nebo opravte instalaci sady Visual Studio pomocí instalační diskety.

## <a name="see-also"></a>Viz také
 [Ladicí program zabezpečení](../debugger/debugger-security.md) ladění [základy](../debugger/debugger-basics.md) [ladění za běhu, ladění, dialogové okno Možnosti](../debugger/just-in-time-debugging-options-dialog-box.md) [Upozornění zabezpečení: připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015) .
