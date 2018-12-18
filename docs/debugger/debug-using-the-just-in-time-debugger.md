---
title: Ladění pomocí ladicího programu za běhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f66d3fdcd400be9356776647b0ead118e83d7108
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382741"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Ladění pomocí ladicího programu za běhu v sadě Visual Studio

Ladění Just-In-Time může spusťte sadu Visual Studio automaticky při aplikaci běžící mimo aplikaci Visual Studio chyby nebo selhání. Just-In-Time ladění můžete testovat aplikace mimo sadu Visual Studio a otevřete sadu Visual Studio pro zahájení ladění, když dojde k potížím.

Ladění Just-In-Time funguje pro aplikace klasické pracovní plochy Windows. To nebude fungovat pro univerzální aplikace pro Windows, nebo pro spravovaný kód, který je hostován v nativní aplikaci, například pro Vizualizátory.

> [!TIP]
> Pokud chcete zastavit ladicí program za běhu dialogových oken povolí, ale není nainstalované Visual Studio, naleznete v tématu [zakázat ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md). Pokud jste měli jednou nainstalovanou sadu Visual Studio, budete muset [zakázání Just-In-Time ladění z registru Windows](#disable-just-in-time-debugging-from-the-windows-registry). 

##  <a name="BKMK_Enabling"></a> Povolení nebo zakázání Just-In-Time ladění v sadě Visual Studio

>[!NOTE]
>K povolení nebo zakázání Just-In-Time ladění, musíte používat Visual Studio jako správce. Povolení nebo zakázání Just-In-Time ladění nastaví klíč registru, a chcete-li změnit tento klíč může být nutná oprávnění správce. Otevřít Visual Studio jako správce, klikněte pravým tlačítkem na aplikaci Visual Studio a zvolte **spustit jako správce**. 

Můžete nakonfigurovat Just-In-Time ladění ze sady Visual Studio **nástroje** > **možnosti** (nebo **ladění** > **možnosti**) Dialogové okno. 

**Povolení nebo zakázání Just-In-Time ladění:**

1. Na **nástroje** nebo **ladění** nabídce vyberte možnost **možnosti** > **ladění**  >   **Just-In-Time**.

   ![Povolení nebo zakázání ladění JIT](../debugger/media/dbg-jit-enable-or-disable.png "povolení nebo zakázání ladění za běhu")

1. V **povolit ladění za běhu pro tyto typy kódu** vyberte typy kódu, které chcete, aby Just-In-Time ladění pro ladění: **spravované**, **nativní**, a/nebo  **Skript**.
   
1. Vyberte **OK**.

Pokud povolíte Just-In-Time neotevře ladicího programu, ale když aplikaci dojde k chybě nebo chybám, naleznete v tématu [ladění za běhu řešení potíží s](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Zakázat Just-In-Time ladění z registru Windows

Ladění Just-In-Time může být stále povoleno i v případě, že ve vašem počítači je již nainstalované sady Visual Studio. Pokud už je nainstalované sady Visual Studio, můžete zakázat Just-In-Time ladění pomocí úpravy registru Windows.

**Chcete-li zakázat Just-In-Time ladění pomocí úpravy registru:**

1.  Z Windows **Start** nabídky, spusťte **Editor registru** (*regedit.exe*).

2.  V **Editor registru** okna, vyhledejte a odstraňte následující položky registru:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Klíč registru JIT](../debugger/media/dbg-jit-registry.png "klíč registru JIT")

3.  Pokud počítač používá 64bitový operační systém, odstraňte také následující položky registru:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Zajistěte, aby odstranění nebo změně jiných klíčů registru.

5.  Zavřít **Editor registru** okna.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Povolit Just-In-Time ladění formuláře Windows

Ve výchozím nastavení mají aplikace formuláře Windows obslužnou rutinu výjimky nejvyšší úrovně, ve kterém aplikace spouštět opakovaně, pokud jej lze obnovit. Pokud aplikace Windows Forms vyvolá neošetřenou výjimku, zobrazí následující dialogové okno:

![Formuláře Windows neošetřená výjimka](../debugger/media/windowsformsunhandledexception.png "formuláře Windows neošetřená výjimka")

Pokud chcete povolit Just-In-Time ladění místo standard pro zpracování chyb formuláře Windows, přidejte tato nastavení:

-  V `system.windows.forms` část *machine.config* nebo  *\<název aplikace >. exe.config* souboru `jitDebugging` hodnota, která se `true`:
    
    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```
    
-  V aplikaci C++ formuláře Windows, také nastavit `DebuggableAttribute` k `true` v *.config* souboru nebo ve vašem kódu. Pokud kompilujete s [/zi](/cpp/build/reference/z7-zi-zi-debug-information-format) a bez [/og](/cpp/build/reference/og-global-optimizations), kompilátor nastaví tento atribut za vás. Pokud chcete ladit neoptimalizované verzi sestavení, ale je nutné nastavit `DebuggableAttribute` přidáním následujícího řádku ve vaší aplikaci *AssemblyInfo.cpp* souboru:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```
   
   Další informace naleznete v tématu <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Použití Just-In-Time ladění
 Tento příklad vás provede Just-In-Time ladění, když aplikace vyvolá chybu.

 - Musíte mít Visual Studio nainstalovali postupovat podle následujících kroků. Pokud nemáte Visual Studio, si můžete stáhnout bezplatnou [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).
   
 - Ujistěte se, že Just-In-Time je ladění [povolené](#BKMK_Enabling) v **nástroje** > **možnosti** > **ladění**  >  **Just-In-Time**.

V tomto příkladu provede konzolovou aplikaci C# v sadě Visual Studio, který vyvolá [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. Ve Visual Studiu Vytvořte konzolovou aplikaci C# (**souboru** > **nový** > **projektu** > **Visual C#**  >  **Konzolovou aplikaci**) s názvem *ThrowsNullException*. Další informace o vytváření projektů v sadě Visual Studio najdete v tématu [návod: vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).
   
1. Po otevření projektu v sadě Visual Studio, otevřete *Program.cs* souboru. Nahraďte následující kód, který vytiskne řádek ke konzole a potom vyvolá NullReferenceException metodu Main():
   
   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```
   
1. Abyste mohli sestavit řešení, zvolte buď **ladění** (výchozí) nebo **vydání** konfigurace a pak vyberte **sestavení** > **znovu sestavit řešení** . 
   
   >[!NOTE]
   >- Zvolte **ladění** Konfigurace úplného ladicího prostředí. 
   >- Pokud vyberete [vydání](../debugger/how-to-set-debug-and-release-configurations.md) konfigurace, je nutné vypnout [pouze můj kód](../debugger/just-my-code.md) Dal tento postup fungovat. V části **nástroje** > **možnosti** > **ladění**, zrušte zaškrtnutí možnosti **povolit volbu pouze vlastní kód**.
   Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurace sestavení](../ide/understanding-build-configurations.md).
   
1. Otevřete sestavené aplikace *ThrowsNullException.exe* ve složce projektu C# (*...\ThrowsNullException\ThrowsNullException\bin\Debug* nebo *...\ThrowsNullException\ ThrowsNullException\bin\Release*). 
   
   Měli byste vidět následující příkazové okno:
   
   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")
   
1. **Zvolte ladicí program za běhu** otevře se dialogové okno.
   
   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")
   
   V části **dostupné ladicí programy**vyberte **novou instanci třídy \<vaše upřednostňovanou verzi nebo edici sady Visual Studio >**, pokud ještě není vybraná. 
   
1. Vyberte **OK**.
   
   ThrowsNullException projektu se otevře v nové instanci sady Visual Studio, s provádění zastaveno na řádku, který vyvolal výjimku:
   
   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

V tomto okamžiku ladění lze spustit. Kdybyste ladili skutečné aplikace, je třeba zjistit, proč kód způsobující výjimku.

> [!CAUTION]
> Pokud vaše aplikace obsahuje nedůvěryhodný kód, zobrazí se dialogové okno upozornění zabezpečení, které umožňuje rozhodnout, jestli chcete pokračovat v ladění. Než budete pokračovat, ladění, rozhodněte, zda kódu důvěřujete. Napsali jste kód sami? Pokud aplikace běží na vzdáleném počítači, poznáváte název procesu? Pokud je aplikace spuštěná místně, zvažte možnost škodlivý kód spuštěný ve vašem počítači. Pokud se rozhodnete je důvěryhodný kód, vyberte **OK**. V opačném případě vyberte **zrušit**.

## <a name="jit_errors"></a> Řešení potíží s Just-In-Time ladění 

Pokud Just-In-Time ladění nelze spustit Pokud dojde k chybě aplikace, i když je povolena v sadě Visual Studio:

- Zasílání zpráv o chybách Windows může být trvá déle než zpracování ve vašem počítači chyb. 
  
  Chcete-li vyřešit tento problém, pomocí Editoru registru pro přidání **hodnotu DWORD** z **zakázané**, s **údaj hodnoty** z **1**, do následujícího klíče registru:
  
  

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows zasílání zpráv o chybách**
    
  - (Pro 64bitové počítače): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows zasílání zpráv o chybách**
  
  Další informace najdete v tématu [. Nastavení zasílání](https://docs.microsoft.com/windows/desktop/wer/wer-settings).
  
- Může být příčinou známý problém Windows Just-In-Time debugger k selhání. 
  
  Vyřešit, je přidat **hodnotu DWORD** z **automaticky**, s **údaj hodnoty** z **1**, do následujícího klíče registru:
  
  
  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**
    
  - (Pro 64bitové počítače): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Může se zobrazit následující chybové zprávy během Just-In-Time ladění:

- **Nelze se připojit k havarujícímu procesu. Uvedený program není program Windows nebo MS-DOS.**

    Ladicí program se pokusil připojit k procesu spuštěnému pod jiným uživatelem.

    Chcete-li vyřešit tento problém v sadě Visual Studio, otevřete **ladění** > **připojit k procesu**a najít proces, který chcete ladit v **procesy k dispozici** seznam. Pokud neznáte název procesu, vyhledejte ID procesu v **ladicí program za běhu sady Visual Studio** dialogového okna. Vyberte proces v **procesy k dispozici** seznam a vyberte **připojit**. Vyberte **ne** Just-In-Time zavřete dialogové okno ladicího programu.

- **Ladicí program nelze spustit, protože není přihlášen žádný uživatel.**

    Neexistuje žádný uživatel přihlášený ke konzole, takže není žádná uživatelská relace k zobrazení Just-In-Time ladění dialogového okna.

    Chcete-li tento problém vyřešit, přihlaste se do počítače.

- **Třída není zaregistrována.**

    Ladicí program se pokusil vytvořit třídu COM, která není registrována, pravděpodobně z důvodu potíží při instalaci.

    Pokud chcete tento problém vyřešit, použijte instalační program sady Visual Studio a přeinstalujte nebo opravte instalaci sady Visual Studio.

## <a name="see-also"></a>Viz také:
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Základy ladicího programu](../debugger/getting-started-with-the-debugger.md)
- [Možnosti, ladění Just-In-Time dialogové okno](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud následující údaje vypadají podezřele nebo si nejste jistí, k tomuto procesu se nepřipojujte.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
