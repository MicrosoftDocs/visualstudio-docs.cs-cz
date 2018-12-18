---
title: Vzdálené ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ac1bbe2cc1832d0b34706f88b4df583d117149c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799272"
---
# <a name="remote-debugging"></a>Vzdálené ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete ladit aplikace Visual Studio, který byl nasazen na jiný počítač.  K tomu použijete vzdálený ladicí program sady Visual Studio.  
  
 Zde uvedené informace platí pro aplikace klasické pracovní plochy Windows a aplikací ASP.NET.  Informace o vzdáleném ladění aplikací Windows Store a aplikace Azure najdete v tématu [vzdálené ladění pro aplikace z Windows Store a Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Stáhnout nástroje remote tools  
Můžete buď stáhnout nástroje remote tools přímo v zařízení nebo na serveru, který chcete ladit, nebo můžete získat nástroje remote tools v hostitelském počítači s nainstalovanou sadu Visual Studio.

### <a name="to-download-and-install-the-remote-tools"></a>Ke stažení a instalaci nástrojů remote tools
  
1.  Na zařízení nebo server počítač, který chcete ladit (nikoli na počítači sadu Visual Studio) získáte správná verze nástrojů remote tools.

    |Version|Odkaz|Poznámky|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se k bezplatné Visual Studio Dev Essentials skupiny nebo jenom se můžete přihlásit pomocí platné předplatné sady Visual Studio. Pak znovu otevřete odkaz v případě potřeby. Kdykoli stáhněte verzi, která odpovídá operačního systému zařízení (x 86, x64 nebo verzi ARM)|
    |Visual Studio 2015 (starší)|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se k bezplatné Visual Studio Dev Essentials skupiny nebo jenom se můžete přihlásit pomocí platné předplatné sady Visual Studio. Pak znovu otevřete odkaz v případě potřeby.|
    |Visual Studio 2013|[Vzdálené nástroje](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Stáhněte si stránku v dokumentaci k sadě Visual Studio 2013|
    |Visual Studio 2012|[Vzdálené nástroje](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Stáhněte si stránku v dokumentaci k sadě Visual Studio 2012|
  
2.  Na stránce pro stahování zvolte verzi nástrojů, který odpovídá operačnímu systému (x 86, x64 nebo verzi ARM) a stáhněte si nástroje remote tools.
  
    > [!IMPORTANT]
    >  Doporučujeme že nainstalovat nejnovější verzi nástrojů remote tools, která odpovídá verzi sady Visual Studio. Verze se nedoporučuje.  
    >   
    >  Kromě toho musíte nainstalovat nástroje remote tools, které mají stejnou architekturu jako operační systém, na kterém chcete nainstalovat. Jinými slovy Pokud chcete ladit 32bitovou aplikaci na vzdáleném počítači s 64bitovým operačním systémem, musíte nainstalovat 64bitová verze produktu remote tools na vzdáleném počítači.  
  
3.  Po dokončení stahování spustitelného souboru, postupujte podle pokynů k instalaci aplikace na vzdáleném počítači. Zobrazit [instalační pokyny](#bkmk_setup)

Pokud se pokusíte zkopírovat vzdálený ladící program (msvsmon.exe) ke vzdálenému počítači a spusťte ho, mějte na paměti, která **Průvodce konfigurací vzdáleného ladicího programu** (**rdbgwiz.exe**) je nainstalována pouze v případě, že si stáhnout nástroje a budete možná muset použít Průvodce pro konfiguraci později, zejména v případě, že chcete, aby vzdálený ladicí program ke spuštění jako služba. Další informace najdete v tématu [(volitelné) konfigurovat vzdálený ladicí program jako službu](#bkmk_configureService) níže.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Spuštění vzdáleného ladicího programu ze sdílené složky

Můžete najít vzdáleného ladicího programu (**msvsmon.exe**) na počítači s Visual Studio 2015 Community, Professional nebo Enterprise už nainstalovaná. Pro většinu scénářů je nejjednodušší způsob, jak nastavit vzdálené ladění spusťte vzdálený ladící program (msvsmon.exe) ze sdílené složky. Omezení využití najdete na stránce nápovědy vzdáleného ladicího programu (**Nápověda / využití** v vzdálený ladicí program).

1. Najít **msvsmon.exe** v adresáři odpovídající verzi sady Visual Studio. Pro Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Sdílené složky **vzdálený ladicí program** složky v počítači, Visual Studio.

3. Na vzdáleném počítači, spusťte **msvsmon.exe**. Postupujte podle [instalační pokyny](#bkmk_setup).

> [!TIP] 
> Instalace pomocí příkazového řádku a příkazový řádek, naleznete na stránce nápovědy pro **msvsmon.exe** zadáním ``msvsmon.exe /?`` na příkazovém řádku na počítači s nainstalovanou sadu Visual Studio (nebo můžete přejít na **Nápověda / využití**v vzdálený ladicí program).

  
## <a name="supported-operating-systems"></a>Podporované operační systémy  
 Vzdáleném počítači musí běžet některý z následujících operačních systémů:  
  
-   Windows 10  
  
-   Windows 8 nebo 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 nebo Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Podporované hardwarové konfigurace  
  
-   Procesor 1,6 GHz nebo rychlejší  
  
-   1 GB paměti RAM (1,5 GB při spouštění ve virtuálním počítači)  
  
-   1 GB volného místa na disku  
  
-   Pevný disk 5400 ot/min  
  
-   Grafická karta s rozhraním DirectX 9 a rozlišením 1024 × 768 nebo vyšším  
  
## <a name="network-configuration"></a>Konfigurace sítě  
 Vzdálený počítač a počítač Visual Studio musí být připojeny přes síť, v pracovní skupině nebo v domácí skupině, jinak připojeny přímo pomocí kabelu Ethernet. Není podporováno ladění přes Internet.  
  
## <a name="bkmk_setup"></a>Nastavení vzdáleného ladicího programu  
 Musí mít oprávnění správce na vzdáleném počítači  
  
1. Vyhledejte aplikaci vzdálený ladicí program. (Otevřete nabídku Start, vyhledejte **vzdálený ladicí program**.)
  
    Pokud používáte vzdálený ladicí program na vzdáleném serveru, můžete klikněte pravým tlačítkem na aplikaci vzdálený ladicí program a zvolte **spustit jako správce** (nebo můžete spustit vzdálený ladicí program jako službu). Pokud vy nespouštíte na vzdáleném serveru, stačí spusťte normálně.
  
2. Při spuštění nástroje remote tools poprvé (nebo předtím, než jste ji nakonfigurovali), **konfigurace vzdáleného ladění** dalog dialogové okno.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Pokud není nainstalováno rozhraní API služby Windows (který se stane pouze v systému Windows Server 2008 R2), zvolte **nainstalovat** tlačítko.  
  
4. Vyberte typy sítí, chcete, aby na použití nástrojů remote tools. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojené do domény, je třeba zvolit první položku. Pokud jsou tyto počítače připojeny přes domácí nebo pracovní skupině, musíte zvolit druhý nebo třetí položka podle potřeby.  
  
5. Zvolte **konfigurovat vzdálené ladění** ke konfiguraci brány firewall a spusťte nástroj.  
  
6. Po dokončení konfigurace se zobrazí v okně vzdáleného ladicího programu.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Vzdálený ladicí program je nyní čeká na připojení. Poznamenejte si název serveru a port číslo, které se zobrazí, protože ho budete potřebovat později pro konfiguraci v sadě Visual Studio.  
  
   Po dokončení ladění a potřeba zastavit vzdáleného ladicího programu, klikněte na tlačítko **souboru / ukončit** v okně. Můžete restartovat z **Start** nabídky nebo z příkazového řádku:  
  
   **\<Visual Studio Instalační adresář > \Common7\IDE\Remote ladicí program\\< x86, x64 nebo Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurace vzdáleného ladicího programu  
 Některé aspekty konfigurace vzdáleného ladicího programu můžete změnit po prvním spuštění po spuštění.
  
- Chcete-li mohli ostatní uživatelé připojit ke vzdálenému ladicímu programu, zvolte **nástroje / oprávnění**. K udělení nebo odebrání oprávnění je potřeba mít oprávnění správce.

  > [!IMPORTANT]
  > Můžete spustit vzdálený ladicí program uživatelského účtu, který se liší od uživatelského účtu, který používáte na počítači aplikace Visual Studio, ale musíte přidat jiný uživatelský účet oprávnění vzdáleného ladicího programu. 

   Alternativně můžete spustit vzdálený ladicí program z příkazového řádku pomocí **/ allow \<uživatelské jméno >** parametr: **msvsmon / allow \< username@computer>**.
  
- Chcete-li změnit režim ověřování nebo číslo portu, nebo můžete zadat hodnotu časového limitu pro nástroje remote tools: Zvolte **Nástroje / možnosti**.  
  
   Seznam čísel portů používaných ve výchozím nastavení, najdete v části [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  >  Můžete také spustit nástroje Remote Tools v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Zvolte režim bez ověřování jenom v případě, že jste si jisti, že síť není ohroženy škodlivými nebo nevyžádanými daty.

##  <a name="bkmk_configureService"></a> (Volitelné) Konfigurovat vzdálený ladicí program jako službu
 Pro ladění v technologii ASP.NET a jiné prostředí serveru, musíte buď spustit vzdálený ladicí program jako správce nebo, je vždy spuštěn, chcete-li spustit vzdálený ladicí program jako službu.
  
 Pokud chcete nakonfigurovat vzdálený ladicí program jako službu, postupujte podle těchto kroků.  
  
1. Najít **Průvodce konfigurací vzdáleného ladicího programu** (rdbgwiz.exe). (To je samostatná aplikace od vzdáleného ladicího programu.) Je dostupná jenom při instalaci nástrojů remote tools. Nenainstaluje se sadou Visual Studio.  
  
2. Spustíte Průvodce konfigurací. Po první stránka se zobrazí, klikněte na tlačítko **Další**.  
  
3. Zkontrolujte, **spustit Visual Studio 2015 vzdálený ladicí program jako službu** zaškrtávací políčko.  
  
4. Přidáte název uživatelského účtu a hesla.  
  
    Budete muset přidat **přihlásit jako službu** uživatele přímo k tomuto účtu. (Najít **místní zásady zabezpečení** (secpol.msc) v **Start** stránky nebo okna (nebo typ **secpol** z příkazového řádku). Po zobrazení dialogového okna, dvakrát klikněte na panel **přiřazení uživatelských práv**, vyhledejte **přihlásit jako službu** v pravém podokně. Poklepejte na něj. Přidat uživatelský účet **vlastnosti** okno a klikněte na tlačítko **OK**.) Klikněte na tlačítko **Další**.  
  
5. Vyberte typ sítě, mají komunikovat nástroje remote tools. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojené do domény, měli byste zvolit první položku. Pokud jsou tyto počítače připojeny přes domácí nebo pracovní skupině, měli byste zvolit položky druhý nebo třetí. Klikněte na tlačítko **Další**.  
  
6. Pokud tuto službu můžete spustit, zobrazí se **byly úspěšně dokončeny Visual Studio Debugger Průvodce konfigurací vzdáleného**. Pokud službu nelze spustit, zobrazí se **se nepodařilo dokončit Visual Studio Debugger Průvodce konfigurací vzdáleného**. Stránce se zobrazuje také několik tipů pro získání služba spustí.  
  
7. Klikněte na tlačítko **Dokončit**.  
  
   V tomto okamžiku vzdálený ladicí program je spuštěn jako služba. Můžete to ověřit tak, že přejdete do **ovládací panely / Services** a hledáte **Visual Studio 2015 vzdálený ladicí program**.  
  
   Můžete zastavit a spustit službu vzdálený ladicí program z **ovládací panely / Services**.  

## <a name="remote-debug-an-aspnet-application"></a>Vzdálené ladění aplikací ASP.NET  
 Nasazení aplikace ASP.NET ke vzdálenému počítači se službou IIS má jiný postup, v závislosti na operačním systému a verze služby IIS. Pro vzdálené počítače se systémem Windows Server 2008 nebo Windows Server 2012, které služby IIS 7.5 nebo novější verzi, najdete [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Když provádíte ladění aplikace v ASP.NET Core, najdete [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). Různé kroky jsou nutné k publikování ASP.NET Core ve službě IIS. Po úspěšném publikování aplikace ASP.NET Core můžete vzdáleného ladění [stejně jako ostatní aplikace v ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), s tím rozdílem, že budete muset připojit k procesu je dnx.exe místo w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Vzdálené ladění projektu Visual C++  
 V následujícím postupu, název a cestu k projektu je C:\remotetemp\MyMfc a je název vzdáleného počítače **MJO DL**.  
  
1. Vytvoření aplikace knihovny MFC s názvem **mymfc.**  
  
2. Nastavit zarážku někde v aplikaci, která je snadno dosaženo, například v **MainFrm.cpp**, na začátku `CMainFrame::OnCreate`.  
  
3. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. Otevřít **ladění** kartu.  
  
4. Nastavte **ladicí program ke spuštění** k **vzdálený ladicí program Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Proveďte změny následujících vlastností:  
  
   |Nastavení|Hodnota|
   |-|-|  
   |Vzdálený příkaz|C:\remotetemp\mymfc.exe|  
   |Pracovní adresář|C:\remotetemp|  
   |Název vzdáleného serveru|MJO DL:*číslo_portu*|  
   |připojení|Vzdálený s ověřováním Windows|  
   |Typ ladicího programu|Pouze nativní|  
   |Adresář nasazení|C:\remotetemp.|  
   |Další soubory k nasazení|C:\data\mymfcdata.txt.|  
  
    Pokud nasadíte další soubory (volitelné), složka musí existovat v obou počítačích.  
  
6. V Průzkumníku řešení klikněte pravým tlačítkem na řešení a zvolte **nástroje Configuration Manager**.  
  
7. Pro **ladění** konfigurace, vyberte **nasadit** zaškrtávací políčko.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Spustit ladění (**ladění / spuštění ladění**, nebo **F5**).  
  
9. Spustitelný soubor je automaticky nasadí do vzdáleného počítače.  
  
10. Pokud se zobrazí výzva, zadejte přihlašovací údaje k síti pro připojení ke vzdálenému počítači.  
  
     Požadované přihlašovací údaje jsou specifické pro konfiguraci zabezpečení vaší sítě. Například v počítači domény, může vybrat si certifikát zabezpečení nebo zadejte název domény a heslo. Na počítači mimo doménu, můžete například zadat název počítače a platné uživatelské jméno účtu, jako je třeba <strong>MJO-DL\name@something.com</strong>, spolu s správné heslo.  
  
11. V počítači, Visual Studio měli byste vidět zastavením spuštění na zarážce.  
  
    > [!TIP]
    >  Alternativně můžete nasadit soubory jako samostatný krok. V **Průzkumníku řešení klikněte** klikněte pravým tlačítkem myši **mymfc** uzel a klikněte na tlačítko **nasadit**.  
  
    Pokud máte souborům bez kódu, které je potřeba v aplikaci použít, budete muset zahrnout je do projektu sady Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumníka řešení**, klikněte na tlačítko **Add / novou složku**.) Pak přidejte soubory do složky (v **Průzkumníku řešení**, klikněte na tlačítko **přidat nebo existující položky**, vyberte soubory.). Na **vlastnosti** stránky pro každý soubor, nastavte **kopírovat do výstupního adresáře** k **vždy Kopírovat**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Vzdálené ladění projektu Visual C# nebo Visual Basic  
 Ladicí program nemůže nasadit Visual C# nebo Visual Basic desktopové aplikace ke vzdálenému počítači, ale můžete stále ladit vzdáleně následujícím způsobem. Následující postup předpokládá, že chcete ladit v počítači s názvem **MJO DL**, jak je znázorněno v předchozí ilustraci.
  
1. Vytvoření projektu WPF s názvem **MyWpf**.  
  
2. Nastavte zarážku někde v kódu, který je snadno dosaženo.  
  
    Může například nastavit zarážku v rutině tlačítka. Uděláte to tak, otevřete soubor MainWindow.xaml a přidejte ovládací prvek tlačítko z panelu nástrojů a potom dvakrát klikněte na tlačítko otevřít její obslužná rutina.
  
3. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **vlastnosti**.  
  
4. Na **vlastnosti** zvolte **ladění** kartu.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Ujistěte se, **pracovní adresář** textové pole je prázdné.  
  
6. Zvolte **použít vzdálený počítač**a typ **MJO-DL:4020** v textovém poli. (4020 je číslo portu se zobrazují v okně vzdáleného ladicího programu).  
  
7. Ujistěte se, že **povolit ladění nativního kódu** není vybraná.  
  
8. Sestavte projekt.  
  
9. Vytvoření složky na vzdáleném počítači, který se stejnou cestou jako **ladění** složky v počítači aplikace Visual Studio:  **\<zdrojová_cesta_operačního_systému > \MyWPF\MyWPF\bin\Debug**.  
  
10. Zkopírujte spustitelný soubor, který jste právě sestavili ze sady Visual Studio do nově vytvořené složky na vzdáleném počítači.
  
    > [!CAUTION]
    >  Nedovolte, aby byly změny v kódu nebo opětovné sestavení (nebo je nutné tento krok opakovat). Spustitelný soubor, který jste zkopírovali do vzdáleného počítače se musí přesně odpovídat, místní zdroje a symbolů.

    Můžete zkopírovat projektu ručně, pomocí příkazu Xcopy, Robocopy, Powershellu nebo jiné možnosti.
  
11. Ujistěte se, že vzdálený ladicí program je spuštěn na cílovém počítači. (Pokud není, vyhledejte **vzdálený ladicí program** v **Start** nabídky. ) V okně vzdáleného ladicího programu vypadá takto.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. V sadě Visual Studio spustit ladění (**ladění / spuštění ladění**, nebo **F5**).  
  
13. Pokud se zobrazí výzva, zadejte přihlašovací údaje k síti pro připojení ke vzdálenému počítači.  
  
     Požadované přihlašovací údaje se liší v závislosti na konfiguraci zabezpečení vaší sítě. V počítači domény, můžete například zadat název domény a heslo. Na počítači mimo doménu, můžete například zadat název počítače a platné uživatelské jméno účtu, jako je třeba <strong>MJO-DL\name@something.com</strong>, spolu s správné heslo.

     Měli byste vidět, že hlavní okno aplikace WPF je otevřít na vzdáleném počítači.
  
14. V případě potřeby proveďte akce na zarážce. Měli byste vidět, že zarážka je aktivní. Pokud tomu tak není, ještě nebyly načteny symboly pro aplikaci. Zkuste to znovu a pokud to nepomůže, získejte informace o načítání symbolů a jak řešit je na [soubory symbolů principy a sady Visual Studio symbol nastavení](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Na počítač s Visual Studio měli byste vidět, že vykonávání se zastavilo na zarážku.
  
    Pokud máte souborům bez kódu, které je potřeba v aplikaci použít, budete muset zahrnout je do projektu sady Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumníka řešení**, klikněte na tlačítko **Add / novou složku**.) Pak přidejte soubory do složky (v **Průzkumníku řešení**, klikněte na tlačítko **přidat nebo existující položky**, vyberte soubory.). Na **vlastnosti** stránky pro každý soubor, nastavte **kopírovat do výstupního adresáře** k **vždy Kopírovat**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení se vzdálený symboly ladění  
 Je třeba mít na ladění vašeho kódu se symboly, které vytvoříte na počítači aplikace Visual Studio. Výkon vzdáleného ladícího programu je mnohem lépe při použití místní symboly.  Pokud je nutné použít vzdálené symboly, budete muset říct sledování vzdáleného ladění hledat symboly ve vzdáleném počítači.  
  
 Od verze Visual Studio 2013 Update 2, vám pomůže následující msvsmon přepínač příkazového řádku pomocí vzdáleného symbolů pro spravovaný kód: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Další informace najdete v tématu nápovědy vzdáleného ladění (stisknutím klávesy **F1** v okně vzdáleného ladicího programu, nebo klikněte na tlačítko **Nápověda / využití**). Další informace najdete [.NET změny vzdálené načítání symbolů v sadě Visual Studio 2012 a 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Vzdálené ladění pro aplikace z Windows Store a Azure  
 Informace o vzdáleném ladění s aplikacemi pro Windows Store naleznete v tématu [ladění a testování aplikací pro Windows Store ve vzdáleném zařízení z aplikace Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Informace o ladění v Azure najdete v jednom z těchto témat:  
  
-   [Ladění cloudové služby nebo virtuálního počítače v sadě Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Ladění v rozhraní .NET back-end v sadě Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Úvod do vzdáleného ladění na webech Azure ([1. část](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [2. část](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [3. část](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Viz také  
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)   
 [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)



