---
title: Ladění za běhu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0b89dd1e0a395e034fa2321269e4174da359b336
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052336"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Ladění za běhu v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění za běhu spustí sadu Visual Studio automaticky dojde k výjimce nebo selhání v aplikaci, která běží mimo sadu Visual Studio. To umožňuje testovat aplikaci, když není spuštěná sada Visual Studio a začít ladění pomocí sady Visual Studio, když dojde k potížím.

Ladění Just-In-Time funguje pro aplikace klasické pracovní plochy Windows. Nefunguje pro Windows Universal apps a nefunguje pro spravovaný kód, který je hostován v nativní aplikaci, například pro Vizualizátory.

## <a name="BKMK_Scenario"></a> Nebyla Just-in-Time debugger dialogové okno zobrazí při pokusu o spuštění aplikace?

Akce, které byste měli provést, když se zobrazí sadě Visual Studio Just-in-Time dialogové okno ladicího programu závisí na co se pokoušíte provést:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Pokud chcete vyřadit z dialogových oken a právě tuto aplikaci spustit normálně

1. (Pokročilé uživatele) Pokud máte nainstalovanou sadu Visual Studio (nebo byl dříve nainstalovaná a tento alias odebrali), [zakázání Just-in-Time ladění](#BKMK_Enabling) a pokuste se znovu spusťte aplikaci.

2. Pokud používáte webovou aplikaci v aplikaci Internet Explorer, zakážete ladění skriptů.

    Zakážete ladění skriptů v dialogovém okně Možnosti Internetu. Dostanete z **ovládací panely** / **síť a Internet** / **Možnosti Internetu** (přesný postup závisí na vaší verzi Windows a Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Znovu otevřete webovou stránku, kde jste našli chybu. Pokud se tím problém nevyřeší, obraťte se na vlastníka webové aplikace k vyřešení problému.

4. Pokud používáte jiný typ aplikace pro Windows, je potřeba požádejte vlastníka aplikace chybu opravte a potom znovu nainstalovat tuto opravenou verzi aplikace.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Pokud chcete opravit nebo ladění chyby (pokročilým uživatelům)

- Musíte mít [nainstalovanou sadu Visual Studio](https://www.microsoft.com/download/details.aspx?id=48146) Chcete-li zobrazit podrobné informace o této chybě a zkuste ho ladit. Zobrazit [pomocí JIT](#BKMK_Using_JIT) podrobné pokyny. Pokud nelze vyřešit chyby a opravit aplikaci, obraťte se na vlastníka aplikace tuto chybu napravíme.

##  <a name="BKMK_Enabling"></a> Povolení nebo zakázání Just-In-Time ladění
 Můžete povolit nebo zakázat Just-In-Time ladění ze sady Visual Studio **Nástroje / možnosti** dialogové okno.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Povolení nebo zakázání Just-In-Time ladění

1. Otevřít Visual Studio. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2. V **možnosti** dialogové okno, vyberte **ladění** složky.

3. V **ladění** složky, vyberte **Just-In-Time** stránky.

4. V **povolit ladění za běhu tyto typy kódu** pole, zaškrtněte nebo zrušte zaškrtnutí odpovídajících typů programů: **spravované**, **nativní**, nebo **skript**.

    Zakázat Just-In-Time ladění, jakmile bylo povoleno, musí běžet s oprávněními správce. Povolení Just-In-Time ladění nastaví klíč registru, a chcete-li změnit tento klíč jsou požadována oprávnění správce.

5. Klikněte na tlačítko **OK**.

   Ladění Just-In-Time může být stále povoleno i v případě, že ve vašem počítači je již nainstalované sady Visual Studio. Pokud není nainstalována sada Visual Studio, už se nedá vypnout Just-In-Time ladění ze sady Visual Studio **možnosti** dialogové okno. V takovém případě můžete zakázat Just-In-Time ladění pomocí úpravy registru Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Chcete-li zakázat Just-In-Time ladění pomocí úpravy registru

1.  Na **Start** nabídky, vyhledejte a spusťte `regedit.exe`

2.  V **Editor registru** okna, vyhledejte a odstraňte položky registru postupujte podle:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger

3.  Pokud počítač používá 64bitový operační systém, odstraňte také následující položky registru:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Je třeba dbát na náhodnému odstranění nebo změně jiných klíčů registru.

5.  Zavřít **Editor registru** okna.

> [!NOTE]
>  Pokud chcete zakázat Just-In-Time ladění pro aplikace na straně serveru a tyto kroky nepomohly problém vyřešit, vypněte ladění na straně serveru v nastavení aplikace služby IIS a zkuste to znovu.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Chcete-li povolit Just-In-Time ladění formuláře Windows

1.  Ve výchozím nastavení mají aplikace Windows Forms obslužnou rutinu výjimky nejvyšší úrovně, která umožňuje program nadále spouštět, pokud jej lze obnovit. Například pokud aplikace Windows Forms vyvolá neošetřenou výjimku, zobrazí se dialogové okno vypadat asi takto:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     K povolení Just-In-Time ladění aplikace modelu Windows Forms, je třeba provést následující kroky:

2.  Nastavte `jitDebugging` hodnota, která se `true` v `system.windows.form` část souboru machine.config nebo  *\<název_aplikace >*. exe.config souboru:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  V aplikaci C++ formuláře Windows, musíte taky nastavit `DebuggableAttribute` v souboru .config nebo ve vašem kódu. Pokud kompilujete s [/zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) a bez [/og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), kompilátor nastaví tento atribut za vás. Pokud chcete ladit neoptimalizované verzi sestavení, ale musíte nastavit sami. Můžete to udělat tak, že přidáte následující řádek, který jste už souboru AssemblyInfo.cpp aplikace:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Další informace naleznete v tématu <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Použijte ladění Just-In-Time
 Tato část popisuje, co se stane, když se vyvolá výjimku, spustitelný soubor.

 Musíte mít Visual Studio nainstalovali postupovat podle následujících kroků. Pokud nemáte Visual Studio, si můžete stáhnout bezplatnou [Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146).

 Při instalaci sady Visual Studio Just-In-Time ve výchozím nastavení je povoleno ladění.

 Pro účely tohoto oddílu uděláme konzolovou aplikaci C# v sadě Visual Studio, který vyvolá <xref:System.NullReferenceException>.

 Ve Visual Studiu Vytvořte konzolovou aplikaci C# (**soubor / nový / Project / Visual C# / Konzolová aplikace**) s názvem **ThrowsNullException**. Další informace o vytváření projektů v sadě Visual Studio najdete v tématu [návod: vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Po otevření projektu v sadě Visual Studio otevřete soubor Program.cs. Nahraďte následující kód, který vytiskne řádek ke konzole a potom vyvolá NullReferenceException metodu Main():

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  Aby se tento postup provést [konfiguraci vydané verze](../debugger/how-to-set-debug-and-release-configurations.md), musí si vypnout [pouze můj kód](../debugger/just-my-code.md). V sadě Visual Studio, klikněte na tlačítko **Nástroje / možnosti**. V **možnosti** dialogového okna, vyberte **ladění**. Zrušte zaškrtnutí z **povolit volbu pouze vlastní kód**.

 Sestavte řešení (v sadě Visual Studio, zvolte **sestavení / Rebuild řešení**). Můžete ladit nebo konfiguraci vydané verze. Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

 Proces sestavení vytvoří spustitelný soubor ThrowsNullException.exe. Najdete ho ve složce, ve které jste vytvořili projekt C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** nebo **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Dvakrát klikněte ThrowsNullException.exe. Měli byste vidět okno příkazového řádku takto:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Za několik sekund zobrazí se okno aplikace Chyba:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Neklikejte na **zrušit**! Za několik sekund, měli byste vidět dvě tlačítka **ladění** a **ukončit program**. Klikněte na tlačítko **ladění**.

> [!CAUTION]
>  Pokud vaše aplikace obsahuje nedůvěryhodný kód, zobrazí se dialogové okno s upozorněním zabezpečení. Toto dialogové okno umožňuje rozhodnout, jestli chcete pokračovat v ladění. Než budete pokračovat s laděním, rozhodněte, zda kódu důvěřujete. Napsali jste kód sami? Důvěřujete kodéru? Pokud aplikace běží na vzdáleném počítači, poznáváte název procesu? I v případě, že aplikace běží místně, který nemusí nutně znamenat, že jí lze důvěřovat. Zvažte možnost škodlivý kód spuštěný ve vašem počítači. Pokud se rozhodnete, že kód Chystáte se ladit, je důvěryhodný, klikněte na tlačítko **ladění**. V opačném případě klikněte na tlačítko **Neladit**.

 **Ladicí program za běhu sady Visual Studio** okno se zobrazí:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 V části **možné ladící programy**, měli byste vidět, který **novou instanci sady Microsoft Visual Studio 2015** vybraný řádek. Pokud již není vybraná, vyberte ji.

 V dolní části okna v části **chcete ladit pomocí vybraný ladicí program?**, klikněte na tlačítko **Ano**.

 ThrowsNullException projekt otevře v nové instanci sady Visual Studio, s provádění zastaveno na řádku, která vyvolala výjimku:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 V tomto okamžiku ladění lze spustit. Pokud to aplikace skutečný, je třeba zjistit, proč kód způsobující výjimku.

## <a name="just-in-time-debugging-errors"></a>Chyby ladění Just-In-Time
 Pokud dialogové okno se nezobrazí, pokud dojde k chybě programu, pravděpodobně z důvodu nastavení zasílání zpráv o chybách Windows ve vašem počítači. Další informace najdete v tématu [. Nastavení zasílání](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Může se zobrazit následující chybové zprávy, které jsou spojeny s Just-In-Time ladění.

-   **Nelze se připojit k havarujícímu procesu. Uvedený program není program Windows nebo MS-DOS.**

     K této chybě dochází, když se pokusíte připojit k procesu spuštěnému jako jiný uživatel.

     Chcete-li tento problém vyřešit, spusťte aplikaci Visual Studio, otevřete **připojit k procesu** dialogové **ladění** nabídky a najděte proces, který chcete ladit v **procesy k dispozici**seznamu. Pokud neznáte název procesu, podívejte se na **ladicí program za běhu sady Visual Studio** dialogové okno a poznamenejte si ID procesu. Vyberte proces v **procesy k dispozici** seznamu a klikněte na tlačítko **připojit**. V **ladicí program za běhu sady Visual Studio** dialogového okna, klikněte na tlačítko **ne** zavřete dialogové okno.

-   **Ladicí program nelze spustit, protože není přihlášen žádný uživatel.**

     Tato chyba nastane, pokud Just-In-Time ladění pokusí o spuštění sady Visual Studio na počítači tam, kde neexistuje žádný uživatel přihlášený ke konzole. Protože je přihlášen žádný uživatel, neexistuje žádná uživatelská relace k zobrazení Just-In-Time ladění, dialogové okno.

     Chcete-li tento problém vyřešit, přihlaste se do počítače.

-   **Třída není zaregistrována.**

     Tato chyba označuje, že ladicí program se pokusil vytvořit třídu COM, která není registrována, pravděpodobně z důvodu potíží při instalaci.

     Chcete-li tento problém vyřešit, použijte instalační disk a přeinstalujte nebo opravte instalaci sady Visual Studio.

## <a name="see-also"></a>Viz také
 [Zabezpečení ladicího programu](../debugger/debugger-security.md) [základy ladicího programu](../debugger/debugger-basics.md) [Just-In-Time, ladění, dialogové okno Možnosti](../debugger/just-in-time-debugging-options-dialog-box.md) [upozornění zabezpečení: připojení k procesu vlastněnému nedůvěryhodným uživatelským může být nebezpečné. Pokud následující údaje vypadají podezřele nebo si nejste jistí, k tomuto procesu se nepřipojujte.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)
