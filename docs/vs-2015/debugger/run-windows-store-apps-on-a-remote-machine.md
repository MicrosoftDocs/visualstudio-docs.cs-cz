---
title: Spouštění aplikací pro Windows Store ve vzdáleném počítači | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e53e05d9df5a7bbdca5fd8a9b74dd9325dc7aae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794806"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Spouštění aplikací pro Windows Store ve vzdáleném počítači
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí jenom pro Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aplikace Visual Studio Remote Tools umožňuje spouštět, ladit, profilovat a testovat aplikaci pro Windows Store, která běží na jednom zařízení z druhého počítače se systémem Visual Studio. Spuštění na vzdáleném zařízení může být obzvláště efektivní, pokud počítač s aplikací Visual Studio nepodporuje funkce, které jsou specifické pro aplikace pro Windows Store, jako je dotykové ovládání, geografické umístění a fyzická orientace. Toto téma popisuje postupy pro konfiguraci a spuštění vzdálené relace.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu  
 Můžete se dozvědět:  
  
 [Požadavky](#BKMK_Prerequisites)  
  
 [Zabezpečení](#BKMK_Security)  
  
 [Jak se připojit přímo ke vzdálenému zařízení](#BKMK_DirectConnect)  
  
 [Instalace nástrojů Remote Tools](#BKMK_Installing_the_Remote_Tools)  
  
 [Spouští se monitorování vzdáleného ladicího programu.](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Konfigurace vzdáleného ladicího programu](#BKMK_ConfigureRemoteDebugger)  
  
 [Konfigurace projektu sady Visual Studio pro vzdálené ladění](#BKMK_ConnectVS)  
  
- [Volba vzdáleného zařízení pro projekty v jazyce C# a Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Volba vzdáleného zařízení pro projekty JavaScript a C++](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Spuštění relace vzdáleného ladění](#BKMK_RunRemoteDebug)  
  
## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Požadovaný  
 Ladění na vzdáleném zařízení:  
  
- Vzdálené zařízení a počítač s aplikací Visual Studio musí být připojeny přes síť nebo připojeny přímo pomocí kabelu Ethernet. Ladění po Internetu není podporováno.  
  
- Na vzdáleném zařízení musí být nainstalována licence vývojáře.  
  
- Na vzdáleném zařízení musí být spuštěny součásti vzdáleného ladění.  
  
- Abyste mohli nakonfigurovat bránu firewall během instalace, musíte být správcem vzdáleného zařízení. Ke spuštění nebo připojení ke vzdálenému ladicímu programu musíte mít uživatelský přístup ke vzdálenému zařízení.  
  
## <a name="security"></a><a name="BKMK_Security"></a> Bezpečnost  
 Ve výchozím nastavení používá vzdálený ladicí program ověřování systému Windows.  
  
> [!WARNING]
> Můžete také spustit vzdálený ladicí program v režimu bez ověřování, ale tento režim se důrazně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Na možnost Režim bez ověřování klikněte pouze v případě, že jste si jisti, že není síť ohrožena škodlivými nebo nevyžádanými daty.  
  
## <a name="how-to-connect-directly-to-a-remote-device"></a><a name="BKMK_DirectConnect"></a> Jak se připojit přímo ke vzdálenému zařízení  
 Pokud se chcete připojit přímo ke vzdálenému zařízení, připojte počítač se sadou Visual Studio k zařízení se standardním kabelem Ethernet. Pokud zařízení nemá port sítě Ethernet, můžete k připojení k kabelu použít adaptér USB na Ethernet.  
  
## <a name="installing-the-remote-tools"></a><a name="BKMK_Installing_the_Remote_Tools"></a> Instalace nástrojů Remote Tools  
  
> [!NOTE]
> **Verze a aktualizace**  
>   
> **Remote Tools for Visual Studio 2015** nejsou podporovány pro předchozí verze sady Visual Studio.  
>   
> Doporučujeme nainstalovat aktualizaci verze Remote Tools for Visual Studio 2015, která odpovídá verzi aktualizace instalace sady Visual Studio.  
>   
> Ladicí program VS je kompatibilní s libovolnou kombinací verzí VS 2015 a nástroji Remote Tools for VS 2015. Nejnovější funkce v aplikaci Visual Studio však vyžadují používání nejaktuálnější verzi sady Visual Studio a nástrojů Remote Tools.  
>   
> Další diagnostické nástroje mohou vyžadovat stejné verze nástrojů Remote Tools a Visual Studio.  
  
 **Instalace komponent vzdáleného ladění na vzdáleném zařízení**  
  
 Pro spuštění nebo uložení instalačního programu pro nástroje Remote Tools vyberte jeden z odkazů v této tabulce, který odpovídá vaší verzi sady Visual Studio:  
  
|Verze|Odkaz|Poznámky|
|-|-|-|
|Visual Studio 2015 Update 3|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se ke skupině Free Visual Studio Dev Essentials nebo se můžete přihlásit jenom pomocí platného předplatného sady Visual Studio. V případě potřeby pak propojení znovu otevřete. Vždy stáhnout verzi, která odpovídá operačnímu systému zařízení (verze x86, x64 nebo ARM)|
|Visual Studio 2015 (starší verze)|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se ke skupině Free Visual Studio Dev Essentials nebo se můžete přihlásit jenom pomocí platného předplatného sady Visual Studio. V případě potřeby pak propojení znovu otevřete. Vždy stáhnout verzi, která odpovídá operačnímu systému zařízení (verze x86, x64 nebo ARM)|
|Visual Studio 2013|[Vzdálené nástroje](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Stránka pro stažení v dokumentaci k Visual Studio 2013|
  
 Můžete zvolit, zda chcete stáhnout instalační program nebo ho chcete ihned spustit. Když spustíte instalační program, přijměte uživatelskou smlouvu a pak zvolte možnost **nainstalovat**.  
  
 Ve výchozím nastavení se komponenty vzdáleného ladění instalují do složky **C:\Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger** .  
  
## <a name="starting-the-remote-debugger-monitor"></a><a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Spouští se monitorování vzdáleného ladicího programu.  
  
> [!NOTE]
> Vzhledem k tomu, že vzdálený ladicí program nakonfiguruje bránu firewall tak, aby umožňovala komunikaci s hostitelem sady Visual Studio, musíte být správcem vzdáleného zařízení při prvním spuštění vzdáleného ladicího programu.  
  
 Po instalaci nástrojů Remote Tools klikněte na obrazovce **Start** na možnost **vzdálený ladicí program** . **Konfigurace vzdáleného ladění** se zobrazí při prvním spuštění vzdáleného ladicího programu.  
  
 V dialogovém okně **Konfigurace vzdáleného ladění** :  
  
1. Pokud není nainstalováno rozhraní API webových služeb systému Windows, klikněte na tlačítko **nainstalovat** .  
  
2. Ve skupině **konfigurovat bránu Windows Firewall** vyberte sítě, kterým chcete povolená připojení. Povolené jsou jenom ty sítě, ke kterým je zařízení aktuálně připojené. Musíte zvolit aspoň jednu síť.  
  
3. Vyberte možnost **Konfigurovat vzdálené ladění** a nastavte možnosti brány firewall a spusťte vzdálený ladicí program.  Otevřete dialogové okno **sledování vzdáleného ladění sady Visual Studio** , abyste uživatelům poskytli oprávnění ke vzdáleným nástrojům a nastavili další pokročilé možnosti.  
  
4. Zobrazí se dialogové okno **sledování vzdáleného ladění sady Visual Studio** . Uživatelům můžete udělit oprávnění ke vzdáleným nástrojům a nastavit další možnost Upřesnit z tohoto dialogového okna.  
  
## <a name="configuring-the-remote-debugger"></a><a name="BKMK_ConfigureRemoteDebugger"></a> Konfigurace vzdáleného ladicího programu  
 Pomocí dvou nástrojů můžete změnit konfiguraci vzdáleného ladicího programu.  
  
1. V nabídce **nástroje** v **aplikaci Visual Studio sledování vzdáleného ladění**:  
  
   1. Vyberte **Možnosti** pro změnu čísla portu, režimu ověřování nebo intervalu časového limitu vzdáleného ladicího programu.  
  
   2. Chcete-li přidat nebo odebrat uživatele, kteří mají oprávnění pro vzdálené ladění, vyberte možnost **oprávnění** .  
  
       > [!NOTE]
       > Oprávnění musí být udělena každému uživatelskému účtu, který je vzdáleně laděn.  
  
   Pomocí Průvodce nastavením **vzdáleného ladicího programu** můžete nastavit pokročilé možnosti vzdáleného ladicího programu. Průvodce spustíte tak, že na obrazovce Start kliknete na možnost **Průvodce nastavením vzdáleného ladicího programu** .  
  
2. Na stránce **konfigurace Visual Studio Remote Debugger** můžete zvolit spuštění vzdáleného ladícího programu jako služby. Ve většině případů se spuštění jako služba nevyžaduje.  
  
3. Na stránce **konfigurovat bránu Windows Firewall pro ladění** můžete přidat nebo odebrat typy sítí, ke kterým se má vzdálený ladicí program připojit. Povolené jsou jenom ty sítě, ke kterým je zařízení aktuálně připojené. Musíte zvolit aspoň jednu síť.  
  
## <a name="configuring-the-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Konfigurace projektu sady Visual Studio pro vzdálené ladění  
 Ve vlastnostech projektu zadáte vzdálené zařízení, ke kterému se chcete připojit. Postup se liší v závislosti na programovacím jazyce. Můžete zadat síťový název vzdáleného zařízení, nebo ho můžete vybrat v dialogovém okně vybrat připojení vzdáleného ladicího programu.  
  
 ![Dialogové okno vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Dialogové okno obsahuje seznam pouze těch zařízení, která jsou v místní podsíti počítače Visual Studio a používají vzdálený ladicí program.  
  
> [!TIP]
> Pokud máte potíže s připojením ke vzdálenému zařízení, zkuste zadat IP adresu zařízení. Chcete-li zjistit IP adresu zařízení, otevřete příkazové okno a zadejte příkaz **ipconfig**. IP adresa je uvedená jako **adresa IPv4**.  
  
### <a name="choosing-the-remote-device-for-c-and-visual-basic-projects"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Volba vzdáleného zařízení pro projekty v jazyce C# a Visual Basic  
 ![Vlastnosti spravovaného projektu pro vzdálené ladění](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1. Vyberte název projektu v Průzkumník řešení a potom v místní nabídce zvolte možnost **vlastnosti** .  
  
2. Vyberte **ladit**.  
  
3. V seznamu **cílový seznam zařízení** vyberte možnost **vzdálený počítač** .  
  
4. Zadejte síťový název vzdáleného zařízení do pole **vzdálený počítač** nebo zvolte **Najít** pro výběr zařízení z dialogového okna **Vybrat připojení vzdáleného ladicího programu** .  
  
### <a name="choosing-the-remote-device-for-javascript-and-c-projects"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Volba vzdáleného zařízení pro projekty JavaScript a C++  
 ![Vlastnosti projektu v jazyce C&#43;&#43; pro vzdálené ladění](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1. Vyberte název projektu v Průzkumník řešení a potom v místní nabídce zvolte možnost **vlastnosti** .  
  
2. Rozbalte uzel **Vlastnosti konfigurace** a pak vyberte **ladění**.  
  
3. Pro spuštění seznamu vyberte možnost **vzdálený ladicí program** z **ladicího programu** .  
  
4. V poli **název počítače** zadejte síťový název vzdáleného zařízení nebo zvolte šipku dolů v poli pro výběr zařízení z dialogového okna **Vybrat připojení vzdáleného ladicího programu** .  
  
## <a name="running-a-remote-debugging-session"></a><a name="BKMK_RunRemoteDebug"></a> Spuštění relace vzdáleného ladění  
 Můžete spustit, zastavit a přejít ke vzdálené relaci ladění stejným způsobem jako místní relace. Než začnete s laděním, ujistěte se, že Sledování vzdáleného ladění běží na vzdáleném zařízení.  
  
 Pak zvolte **Spustit ladění** v nabídce **ladění** (klávesnice: F5). Projekt se znovu zkompiluje a pak se na vzdáleném zařízení nasadí na a začal. Ladicí program pozastaví provádění na zarážekch a můžete krokovat s vaším kódem. Klikněte na **Zastavit ladění** , aby se ukončila relace ladění a zavřela se Vzdálená aplikace. Další informace najdete v tématu [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Testování aplikací pro Store pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
