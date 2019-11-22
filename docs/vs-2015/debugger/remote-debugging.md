---
title: Vzdálené ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300565"
---
# <a name="remote-debugging"></a>Vzdálené ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete ladit aplikace Visual Studio, který byl nasazen na jiný počítač.  K tomu použijete vzdálený ladicí program sady Visual Studio.  
  
 Zde uvedená informace platí pro aplikace klasické pracovní plochy systému Windows a aplikace ASP.NET.  Informace o vzdáleném ladění aplikací pro Windows Store a aplikací Azure najdete v tématu [vzdálené ladění v aplikacích pro Windows Store a Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Získání nástrojů Remote Tools  
Můžete buď stáhnout nástroje Remote Tools přímo na zařízení nebo na server, který chcete ladit, nebo můžete získat vzdálené nástroje z hostitelského počítače s nainstalovanou sadou Visual Studio.

### <a name="to-download-and-install-the-remote-tools"></a>Stažení a instalace nástrojů Remote Tools
  
1. Na zařízení nebo serveru, které chcete ladit (nikoli na počítači se sadou Visual Studio), Získejte správnou verzi nástrojů Remote Tools.

    |Version|Odkaz|Poznámky|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se ke skupině Free Visual Studio Dev Essentials nebo se můžete přihlásit jenom pomocí platného předplatného sady Visual Studio. V případě potřeby pak propojení znovu otevřete. Vždy stáhnout verzi, která odpovídá operačnímu systému zařízení (verze x86, x64 nebo ARM)|
    |Visual Studio 2015 (starší verze)|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se ke skupině Free Visual Studio Dev Essentials nebo se můžete přihlásit jenom pomocí platného předplatného sady Visual Studio. V případě potřeby pak propojení znovu otevřete.|
    |Visual Studio 2013|[Vzdálené nástroje](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Stránka pro stažení v dokumentaci k Visual Studio 2013|
    |Visual Studio 2012|[Vzdálené nástroje](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Stránka ke stažení v dokumentaci k sadě Visual Studio 2012|
  
2. Na stránce pro stažení vyberte verzi nástrojů, které odpovídají vašemu operačnímu systému (verze x86, x64 nebo ARM), a Stáhněte si nástroje Remote Tools.
  
    > [!IMPORTANT]
    > Doporučujeme nainstalovat nejnovější verzi nástrojů Remote Tools, které odpovídají vaší verzi sady Visual Studio. Neodpovídající verze se nedoporučují.  
    >   
    >  Kromě toho musíte nainstalovat nástroje Remote Tools, které mají stejnou architekturu jako operační systém, na který ho chcete nainstalovat. Jinými slovy, pokud chcete ladit 32 aplikace na vzdáleném počítači, na kterém běží 64 operační systém, musíte na vzdáleném počítači nainstalovat verzi 64 pro vzdálené nástroje.  
  
3. Po dokončení stahování spustitelného souboru postupujte podle pokynů k instalaci aplikace do vzdáleného počítače. Viz [pokyny k instalaci](#bkmk_setup) .

Pokud se pokusíte zkopírovat vzdálený ladicí program (Msvsmon. exe) do vzdáleného počítače a spustit jej, nezapomeňte, že **Průvodce konfigurací vzdáleného ladicího programu** (**rdbgwiz. exe**) je nainstalován pouze při stažení nástrojů a může být nutné použít Průvodce pro konfiguraci později, zejména pokud chcete, aby byl vzdálený ladicí program spuštěn jako služba. Další informace najdete v tématu [(volitelné) konfigurace vzdáleného ladicího programu jako služby](#bkmk_configureService) níže.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Spuštění vzdáleného ladicího programu ze sdílené složky

Vzdálený ladící program (**msvsmon. exe**) najdete na počítači, který je už nainstalovaný v rámci sady Visual Studio 2015 Community, Professional nebo Enterprise. Pro mnoho scénářů nejjednodušší způsob, jak nastavit vzdálené ladění, je spuštění vzdáleného ladicího programu (Msvsmon. exe) ze sdílené složky. Omezení použití najdete na stránce s nápovědu pro vzdálený ladicí program (**nápovědu nebo použití** ve vzdáleném ladicím programu).

1. Najít **msvsmon.exe** v adresáři odpovídající verzi sady Visual Studio. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Sdílené složky **vzdálený ladicí program** složky v počítači, Visual Studio.

3. Na vzdáleném počítači spusťte **msvsmon. exe**. Postupujte podle [instalační pokyny](#bkmk_setup).

> [!TIP] 
> Informace o instalaci a příkazovém řádku příkazového řádku najdete na stránce s nápovědu pro **msvsmon. exe** zadáním ``msvsmon.exe /?`` na příkazovém řádku počítače s nainstalovanou sadou Visual Studio (nebo v části vzdálený ladicí program můžete přejít na **nápovědu/použití** ).

## <a name="supported-operating-systems"></a>Podporované operační systémy  
 Ve vzdáleném počítači musí být spuštěný jeden z následujících operačních systémů:  
  
- Windows 10  
  
- Windows 8 nebo 8,1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 nebo Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Podporované konfigurace hardwaru  
  
- Procesor 1,6 GHz nebo rychlejší  
  
- 1 GB paměti RAM (1,5 GB při spouštění ve virtuálním počítači)  
  
- 1 GB volného místa na disku  
  
- Pevný disk 5400 ot/min  
  
- Grafická karta s rozhraním DirectX 9 a rozlišením 1024 × 768 nebo vyšším  
  
## <a name="network-configuration"></a>Konfigurace sítě  
 Vzdálený počítač a počítač se systémem Visual Studio musí být připojeny přes síť, pracovní skupinu nebo domácí skupinu nebo jinak připojeni přímo přes kabel Ethernet. Ladění přes Internet se nepodporuje.  
  
## <a name="bkmk_setup"></a>Nastavení vzdáleného ladicího programu  
 Musíte mít oprávnění správce na vzdáleném počítači.  
  
1. Vyhledejte aplikaci vzdáleného ladicího programu. (Otevřete nabídku Start a vyhledejte **vzdálený ladicí program**.)
  
    Pokud používáte vzdálený ladicí program na vzdáleném serveru, můžete kliknout pravým tlačítkem na aplikaci vzdáleného ladicího programu a zvolit **Spustit jako správce** (nebo můžete spustit vzdálený ladicí program jako službu). Pokud ho nepoužíváte na vzdáleném serveru, stačí ho spustit normálně.
  
2. Když spustíte vzdálené nástroje poprvé (nebo před tím, než ho nakonfigurujete), zobrazí se pole dalog **Konfigurace vzdáleného ladění** .  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Pokud není nainstalované rozhraní API služby systému Windows (k tomu dochází pouze v systému Windows Server 2008 R2), klikněte na tlačítko **instalovat** .  
  
4. Vyberte typy sítí, na kterých chcete používat nástroje Remote Tools. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojené přes doménu, musíte zvolit první položku. Pokud jsou počítače připojené prostřednictvím pracovní skupiny nebo domácí skupiny, musíte podle potřeby vybrat druhou nebo třetí položku.  
  
5. Vyberte možnost **Konfigurovat vzdálené ladění** a nakonfigurujte bránu firewall a spusťte nástroj.  
  
6. Po dokončení konfigurace se zobrazí okno vzdáleného ladicího programu.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Vzdálený ladicí program nyní čeká na připojení. Poznamenejte si název serveru a číslo portu, který se zobrazí, protože ho budete potřebovat později pro konfiguraci v aplikaci Visual Studio.  
  
   Až budete hotovi s laděním a potřebujete zastavit vzdálený ladicí program, klikněte na **soubor/konec** v okně. Můžete ji restartovat z nabídky **Start** nebo z příkazového řádku:  
  
   **\<instalační adresář sady Visual Studio > ladicího programu \Common7\IDE\Remote\\< x86, x64 nebo Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurace vzdáleného ladicího programu  
 Některé aspekty konfigurace vzdáleného ladicího programu můžete změnit po prvním spuštění po spuštění.
  
- Pokud chcete ostatním uživatelům povolit, aby se připojili ke vzdálenému ladicímu programu, vyberte **nástroje/oprávnění**. K udělení nebo odebrání oprávnění je potřeba mít oprávnění správce.

  > [!IMPORTANT]
  > Můžete spustit vzdálený ladicí program uživatelského účtu, který se liší od uživatelského účtu, který používáte na počítači aplikace Visual Studio, ale musíte přidat jiný uživatelský účet oprávnění vzdáleného ladicího programu. 

   Alternativně můžete spustit vzdálený ladicí program z příkazového řádku pomocí **/ allow \<uživatelské jméno >** parametr: **msvsmon / allow \< username@computer>** .
  
- Chcete-li změnit režim ověřování nebo číslo portu nebo zadat hodnotu časového limitu pro nástroje Remote Tools: zvolte **Nástroje/možnosti**.  
  
   Seznam čísel portů používaných ve výchozím nastavení, najdete v části [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Můžete také spustit nástroje Remote Tools v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Zvolte režim bez ověřování jenom v případě, že jste si jisti, že síť není ohroženy škodlivými nebo nevyžádanými daty.

## <a name="bkmk_configureService"></a> (Volitelné) Konfigurovat vzdálený ladicí program jako službu
 Pro ladění v technologii ASP.NET a jiné prostředí serveru, musíte buď spustit vzdálený ladicí program jako správce nebo, je vždy spuštěn, chcete-li spustit vzdálený ladicí program jako službu.
  
 Pokud chcete nakonfigurovat vzdálený ladicí program jako službu, postupujte podle těchto kroků.  
  
1. Najít **Průvodce konfigurací vzdáleného ladicího programu** (rdbgwiz.exe). (Jedná se o samostatnou aplikaci ze vzdáleného ladicího programu.) Je k dispozici pouze při instalaci nástrojů Remote Tools. Nenainstaluje se sadou Visual Studio.  
  
2. Spustíte Průvodce konfigurací. Po první stránka se zobrazí, klikněte na tlačítko **Další**.  
  
3. Zkontrolujte, **spustit Visual Studio 2015 vzdálený ladicí program jako službu** zaškrtávací políčko.  
  
4. Přidáte název uživatelského účtu a hesla.  
  
    K tomuto účtu možná budete muset přidat uživatelské právo **Přihlásit se jako služba** . (Na **úvodní** stránce nebo v okně Najděte **místní zásady zabezpečení** (secpol. msc) (nebo do příkazového řádku zadejte **secpol** ). Po zobrazení dialogového okna, dvakrát klikněte na panel **přiřazení uživatelských práv**, vyhledejte **přihlásit jako službu** v pravém podokně. Poklepejte na něj. Přidejte uživatelský účet do okna **vlastnosti** a klikněte na tlačítko **OK**.) Klikněte na tlačítko **Další**.  
  
5. Vyberte typ sítě, mají komunikovat nástroje remote tools. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojené do domény, měli byste zvolit první položku. Pokud jsou tyto počítače připojeny přes domácí nebo pracovní skupině, měli byste zvolit položky druhý nebo třetí. Klikněte na **Další**.  
  
6. Pokud tuto službu můžete spustit, zobrazí se **byly úspěšně dokončeny Visual Studio Debugger Průvodce konfigurací vzdáleného**. Pokud službu nelze spustit, zobrazí se **se nepodařilo dokončit Visual Studio Debugger Průvodce konfigurací vzdáleného**. Stránce se zobrazuje také několik tipů pro získání služba spustí.  
  
7. Klikněte na tlačítko **Dokončit**.  
  
   V tomto okamžiku vzdálený ladicí program je spuštěn jako služba. Můžete to ověřit tak, že v **Ovládacích panelech nebo službách** vyhledáte **vzdálený ladicí program sady Visual Studio 2015**.  
  
   Službu vzdáleného ladicího programu můžete zastavit a spustit z **ovládacích panelů nebo služeb**.  

## <a name="remote-debug-an-aspnet-application"></a>Vzdálené ladění aplikace v ASP.NET  
 Nasazení aplikace ASP.NET do vzdáleného počítače se službou IIS má různé kroky v závislosti na operačním systému a verzi služby IIS. Pro vzdálené počítače se systémem Windows Server 2008 nebo Windows Server 2012 s nainstalovanou službou IIS 7,5 nebo novějším se podívejte [na vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Pokud ladíte aplikaci ASP.NET Core, přečtěte si téma [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). K publikování ASP.NET Core ve službě IIS se vyžadují různé kroky. Po úspěšném publikování aplikace ASP.NET Core můžete vzdáleně ladit [stejně jako jiné aplikace ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), s tím rozdílem, že proces, ke kterému je potřeba připojit, je DNX. exe místo W3wp. exe.

## <a name="remote-debug-a-visual-c-project"></a>Vzdálené ladění projektu Visual C++  
 V následujícím postupu je název a cesta k projektu C:\remotetemp\MyMfc a název vzdáleného počítače je **mjo-DL**.  
  
1. Vytvořte aplikaci knihovny MFC s názvem **mymfc.**  
  
2. Nastavte zarážku někde v aplikaci, která je snadno dostupná, například v **mainfrm. cpp**na začátku `CMainFrame::OnCreate`.  
  
3. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. Otevřete kartu **ladění** .  
  
4. Nastavte **ladicí program na spouštění** pro **vzdálený ladicí program systému Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Proveďte následující změny vlastností:  
  
   |Nastavení|Hodnota|
   |-|-|  
   |Vzdálený příkaz|C:\remotetemp\mymfc.exe|  
   |Pracovní adresář|C:\remotetemp|  
   |Název vzdáleného serveru|MJO-DL:*číslo_portu*|  
   |Připojení|Vzdálený s ověřováním systému Windows|  
   |Typ ladicího programu|Pouze nativní|  
   |Adresář nasazení|C:\remotetemp.|  
   |Další soubory k nasazení|C:\data\mymfcdata.txt.|  
  
    Pokud nasadíte další soubory (volitelné), složka musí existovat na obou počítačích.  
  
6. V Průzkumník řešení klikněte pravým tlačítkem na řešení a vyberte možnost **Configuration Manager**.  
  
7. V případě konfigurace **ladění** zaškrtněte políčko **nasadit** .  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Spusťte ladění (**ladění/spuštění ladění**nebo **F5**).  
  
9. Spustitelný soubor se automaticky nasadí do vzdáleného počítače.  
  
10. Pokud se zobrazí výzva, zadejte přihlašovací údaje k síti pro připojení ke vzdálenému počítači.  
  
     Požadovaná pověření jsou specifická pro konfiguraci zabezpečení vaší sítě. Například v počítači domény můžete zvolit certifikát zabezpečení nebo zadat název domény a heslo. Na počítači mimo doménu, můžete například zadat název počítače a platné uživatelské jméno účtu, jako je třeba <strong>MJO-DL\name@something.com</strong>, spolu s správné heslo.  
  
11. V počítači se systémem Visual Studio by se mělo zobrazit, že je spuštění zastaveno na zarážce.  
  
    > [!TIP]
    > Případně můžete soubory nasadit jako samostatný krok. V **Průzkumník řešení** klikněte pravým tlačítkem na uzel **mymfc** a pak zvolte **nasadit**.  
  
    Pokud máte soubory bez kódu, které musí aplikace používat, je nutné je zahrnout do projektu aplikace Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumník řešení**klikněte na **přidat/nová složka**.) Pak přidejte soubory do složky (v **Průzkumník řešení**klikněte na **Přidat/existující položku**a pak vyberte soubory.). Na **vlastnosti** stránky pro každý soubor, nastavte **kopírovat do výstupního adresáře** k **vždy Kopírovat**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Vzdálené ladění vizuálu C# nebo Visual Basic projektu  
 Ladicí program nemůže nasadit Visual C# nebo Visual Basic desktopové aplikace ke vzdálenému počítači, ale můžete stále ladit vzdáleně následujícím způsobem. Následující postup předpokládá, že ho chcete ladit v počítači s názvem **mjo-DL**, jak je znázorněno na předchozím obrázku.
  
1. Vytvoření projektu WPF s názvem **MyWpf**.  
  
2. Nastavte zarážku někde v kódu, který je snadno dosaženo.  
  
    Může například nastavit zarážku v rutině tlačítka. Uděláte to tak, otevřete soubor MainWindow.xaml a přidejte ovládací prvek tlačítko z panelu nástrojů a potom dvakrát klikněte na tlačítko otevřít její obslužná rutina.
  
3. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **vlastnosti**.  
  
4. Na **vlastnosti** zvolte **ladění** kartu.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Ujistěte se, **pracovní adresář** textové pole je prázdné.  
  
6. Vyberte možnost **použít vzdálený počítač**a do textového pole zadejte **mjo-DL: 4020** . (4020 je číslo portu zobrazené v okně vzdáleného ladicího programu).  
  
7. Ujistěte se, že **povolit ladění nativního kódu** není vybraná.  
  
8. Sestavte projekt.  
  
9. Vytvoření složky na vzdáleném počítači, který se stejnou cestou jako **ladění** složky v počítači aplikace Visual Studio:  **\<zdrojová_cesta_operačního_systému > \MyWPF\MyWPF\bin\Debug**.  
  
10. Zkopírujte spustitelný soubor, který jste právě sestavili ze sady Visual Studio do nově vytvořené složky na vzdáleném počítači.
  
    > [!CAUTION]
    > Nedovolte, aby byly změny v kódu nebo opětovné sestavení (nebo je nutné tento krok opakovat). Spustitelný soubor, který jste zkopírovali do vzdáleného počítače se musí přesně odpovídat, místní zdroje a symbolů.

    Můžete zkopírovat projektu ručně, pomocí příkazu Xcopy, Robocopy, Powershellu nebo jiné možnosti.
  
11. Ujistěte se, že je na cílovém počítači spuštěný vzdálený ladicí program. (Pokud není, vyhledejte **vzdálený ladicí program** v nabídce **Start** . ) Okno vzdáleného ladicího programu vypadá takto.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. V aplikaci Visual Studio spusťte ladění (**ladění/spuštění ladění**nebo **F5**).  
  
13. Pokud se zobrazí výzva, zadejte přihlašovací údaje k síti pro připojení ke vzdálenému počítači.  
  
     Požadované přihlašovací údaje se liší v závislosti na konfiguraci zabezpečení vaší sítě. V počítači domény, můžete například zadat název domény a heslo. Na počítači mimo doménu, můžete například zadat název počítače a platné uživatelské jméno účtu, jako je třeba <strong>MJO-DL\name@something.com</strong>, spolu s správné heslo.

     Mělo by se zobrazit, že je hlavní okno aplikace WPF otevřeno na vzdáleném počítači.
  
14. V případě potřeby proveďte akce na zarážce. Měli byste vidět, že zarážka je aktivní. Pokud tomu tak není, symboly pro aplikaci se nenačte. Zkuste to znovu, a pokud to nefunguje, Získejte informace o načítání symbolů a o tom, jak je řešit, v tématu [Principy souborů symbolů a nastavení symbolů sady Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Na počítač s Visual Studio měli byste vidět, že vykonávání se zastavilo na zarážku.
  
    Pokud máte soubory bez kódu, které musí aplikace používat, je nutné je zahrnout do projektu aplikace Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumník řešení**klikněte na **přidat/nová složka**.) Pak přidejte soubory do složky (v **Průzkumník řešení**klikněte na **Přidat/existující položku**a pak vyberte soubory.). Na **vlastnosti** stránky pro každý soubor, nastavte **kopírovat do výstupního adresáře** k **vždy Kopírovat**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení se vzdálený symboly ladění  
 Měli byste být schopni ladit kód pomocí symbolů, které vygenerujete v počítači se sadou Visual Studio. Výkon vzdáleného ladicího programu je mnohem lepší při použití místních symbolů.  Pokud je nutné použít vzdálené symboly, je nutné oznámit sledování vzdáleného ladění, aby vyhledalo symboly na vzdáleném počítači.  
  
 Počínaje Visual Studio 2013 Update 2 můžete použít následující přepínač příkazového řádku msvsmon k použití vzdálených symbolů pro spravovaný kód: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Další informace naleznete v nápovědě pro vzdálené ladění (stiskněte klávesu **F1** v okně vzdáleného ladicího programu, nebo klikněte na tlačítko **Nápověda/použití**). Další informace najdete v informacích o [změnách vzdáleného načítání symbolů .NET v nástroji Visual Studio 2012 a 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)  
  
## <a name="bkmk_winstoreAzure"></a>Vzdálené ladění v aplikacích pro Windows Store a Azure  
 Informace o vzdáleném ladění s aplikacemi pro Windows Store naleznete v tématu [ladění a testování aplikací pro Windows Store na vzdáleném zařízení ze sady Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Informace o ladění v Azure najdete v jednom z těchto témat:  
  
- [Ladění cloudové služby nebo virtuálního počítače v aplikaci Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Ladění back-endu .NET v aplikaci Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Úvod ke vzdálenému ladění na webech Azure ([část 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [část 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [část 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Viz také  
 [Ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)   
 [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)
