---
title: Aplikace Windows Store spustit ve vzdáleném počítači | Dokumentace Microsoftu
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
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a3be715f58d3ed80122dfdd3aaf879c7db8aebd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784543"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Spouštění aplikací pro Windows Store ve vzdáleném počítači
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pouze pro Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aplikace Visual Studio Remote Tools umožňuje spouštění, ladění, profilování a testování aplikací pro Windows Store, která běží na jednom zařízení z druhého počítače, na kterém běží Visual Studio. Spuštění na vzdáleném zařízení může být zvláště efektivní, když počítač Visual Studio nepodporuje funkce, které jsou specifické pro aplikace Windows Store, jako je například dotykového ovládání, geolokační a fyzická orientace. Toto téma popisuje postupy pro konfiguraci a spuštění vzdálené relace.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 Další:  
  
 [Požadované součásti](#BKMK_Prerequisites)  
  
 [Zabezpečení](#BKMK_Security)  
  
 [Jak se připojit přímo do vzdáleného zařízení](#BKMK_DirectConnect)  
  
 [Instalace vzdálených nástrojů](#BKMK_Installing_the_Remote_Tools)  
  
 [Spuštění sledování vzdáleného ladicího programu](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Konfigurace vzdáleného ladicího programu](#BKMK_ConfigureRemoteDebugger)  
  
 [Konfigurace projektu Visual Studio pro vzdálené ladění](#BKMK_ConnectVS)  
  
- [Volba vzdáleného zařízení pro projekty jazyka C# a Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Volba vzdáleného zařízení pro projekty jazyka JavaScript a C++](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Spuštění relace vzdáleného ladění](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> Požadované součásti  
 Ladění na vzdáleném zařízení:  
  
-   Vzdálené zařízení a počítač s aplikací Visual Studio musí být připojeny přes síť nebo připojeny přímo pomocí kabelu Ethernet. Ladění po Internetu není podporováno.  
  
-   Licence vývojáře musí být nainstalována na vzdáleném zařízení.  
  
-   Na vzdáleném zařízení musí být spuštěny součásti vzdáleného ladění.  
  
-   Musíte být správcem vzdáleného zařízení ke konfiguraci brány firewall během instalace. Musíte mít uživatelský přístup ke vzdálenému zařízení ke spuštění nebo připojení vzdáleného ladicího programu.  
  
##  <a name="BKMK_Security"></a> Zabezpečení  
 Ve výchozím nastavení používá vzdálený ladicí program ověřování Windows.  
  
> [!WARNING]
>  Můžete také spustit vzdálený ladicí program v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Na možnost Režim bez ověřování klikněte pouze v případě, že jste si jisti, že není síť ohrožena škodlivými nebo nevyžádanými daty.  
  
##  <a name="BKMK_DirectConnect"></a> Jak se připojit přímo do vzdáleného zařízení  
 Pro připojení přímo ke vzdálenému zařízení, připojte počítač Visual Studio k zařízení pomocí standardního ethernetového kabelu. Pokud zařízení nemá port Ethernetu, můžete použít adaptér USB pro připojení k kabel.  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> Instalace vzdálených nástrojů  
  
> [!NOTE]
>  **Verze a aktualizace**  
>   
>  **Remote Tools for Visual Studio 2015** nejsou podporovány v předchozích verzích sady Visual Studio.  
>   
>  Doporučujeme nainstalovat verzi aktualizace nástroje Remote Tools for Visual Studio 2015, která odpovídá verzi aktualizace instalace sady Visual Studio.  
>   
>  Ladicí program VS je kompatibilní s libovolnou kombinací verzí VS 2015 a nástrojů Remote Tools for VS 2015. Nejnovější funkce v aplikaci Visual Studio však vyžadují používání nejaktuálnější verzi sady Visual Studio a nástrojů Remote Tools.  
>   
>  Další diagnostické nástroje mohou vyžadovat stejné verze nástrojů Remote Tools a Visual Studio.  
  
 **Instalace komponent vzdáleného ladění na vzdáleném zařízení**  
  
 Ke spuštění nebo uložení instalačního programu pro nástroje remote tools, zvolte jeden z odkazů v této tabulce, která odpovídá verzi sady Visual Studio:  
  
|Version|Odkaz|Poznámky|
|-|-|-|
|Visual Studio 2015 Update 3|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se k bezplatné Visual Studio Dev Essentials skupiny nebo jenom se můžete přihlásit pomocí platné předplatné sady Visual Studio. Pak znovu otevřete odkaz v případě potřeby. Kdykoli stáhněte verzi, která odpovídá operačního systému zařízení (x 86, x64 nebo verzi ARM)|
|Visual Studio 2015 (starší)|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Pokud se zobrazí výzva, připojte se k bezplatné Visual Studio Dev Essentials skupiny nebo jenom se můžete přihlásit pomocí platné předplatné sady Visual Studio. Pak znovu otevřete odkaz v případě potřeby. Kdykoli stáhněte verzi, která odpovídá operačního systému zařízení (x 86, x64 nebo verzi ARM)|
|Visual Studio 2013|[Vzdálené nástroje](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Stáhněte si stránku v dokumentaci k sadě Visual Studio 2013|
  
 Můžete zvolit, zda chcete stáhnout instalační program nebo ho chcete ihned spustit. Když spustíte instalační program, přijměte uživatelskou smlouvu a klikněte na tlačítko **nainstalovat**.  
  
 Ve výchozím nastavení jsou komponenty vzdáleného ladění nainstalovány v **14.0\Common7\IDE\Remote C:\Program Files\Microsoft Visual Studio Debugger** složky.  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Spuštění sledování vzdáleného ladicího programu  
  
> [!NOTE]
>  Vzhledem k tomu, že vzdálené ladění nastaví konfiguraci brány firewall umožňující navázat komunikaci s hostitelem Visual Studio, musíte být správcem vzdáleného zařízení při prvním spuštění vzdáleného ladicího programu.  
  
 Po instalaci nástrojů Remote Tools, zvolte **vzdálený ladicí program** na **Start** obrazovky. **Konfigurace vzdáleného ladění** se zobrazí při prvním spuštění vzdáleného ladicího programu.  
  
 Na **konfigurace vzdáleného ladění** dialogové okno:  
  
1.  Pokud není nainstalováno rozhraní API webových služeb Windows, použijte tlačítko **instalace**  
  
2.  V **konfigurace brány Windows Firewall** zvolte položky, které chcete povolit připojení do sítě. Jsou povoleny pouze ty sítě, které zařízení je nyní připojen k. Musíte vybrat aspoň jednu síť.  
  
3.  Zvolte **konfigurovat vzdálené ladění** nastavit možnosti brány firewall a spustit vzdálený ladicí program.  Otevřít **Visual Studio Remote Debugging Monitor** dialogové okno uživatelům udělit oprávnění k nástrojům remote tools a nastavit další pokročilé možnosti.  
  
4.  **Visual Studio Remote Debugging Monitor** zobrazí se dialogové okno. Můžete uživatelům udělit oprávnění k nástrojům remote tools a nastavit rozšířenou možnost z tohoto dialogového okna.  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> Konfigurace vzdáleného ladicího programu  
 Použijete dva nástroje upravit konfiguraci vzdáleného ladicího programu.  
  
1. Na **nástroje** nabídku **Visual Studio Remote Debugging Monitor**:  
  
   1.  Zvolte **možnosti** Chcete-li změnit číslo portu, režimu ověřování nebo intervalu časového limitu vzdáleného ladicího programu.  
  
   2.  Zvolte **oprávnění** přidat nebo odebrat uživatele, kteří mají oprávnění pro vzdálené ladění.  
  
       > [!NOTE]
       >  Oprávnění musí být udělena pro každý uživatelský účet, který je vzdáleně laděn.  
  
   Můžete použít **Průvodce konfigurací vzdáleného ladicího programu** nastavíte rozšířené možnosti pro vzdálený ladicí program. Chcete-li spustit průvodce, zvolte **Průvodce konfigurací vzdáleného ladicího programu** na úvodní obrazovce.  
  
2. Na **konfigurovat Visual Studio Remote Debugger** stránky, můžete také spustit vzdálený ladicí program jako službu. Ve většině případů není spuštěná jako služba vyžaduje.  
  
3. Na **konfigurace brány Windows Firewall pro ladění** stránky, můžete přidat nebo odebrat typ sítí, které chcete připojit ke vzdálenému ladicímu programu. Jsou povoleny pouze ty sítě, které zařízení je nyní připojen k. Musíte vybrat aspoň jednu síť.  
  
##  <a name="BKMK_ConnectVS"></a> Konfigurace projektu Visual Studio pro vzdálené ladění  
 Zadáte vzdáleného zařízení pro připojení k ve vlastnostech projektu. Postup se liší v závislosti na programovacím jazyce. Můžete zadat název sítě vzdáleného zařízení nebo ho můžete vybrat v dialogovém okně vyberte připojení vzdáleného ladicího programu.  
  
 ![Dialogové okno Vyberte připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Dialogové okno obsahuje pouze zařízení, které jsou v místní podsíti počítače Visual Studio, která používají vzdálený ladicí program.  
  
> [!TIP]
>  Pokud máte potíže s připojením ke vzdálenému zařízení, zkuste zadat IP adresu zařízení. Pokud chcete zjistit IP adresu zařízení, otevřete okno příkazového řádku a zadejte **ipconfig**. IP adresa je uvedena jako **IPv4 adresu**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Volba vzdáleného zařízení pro projekty jazyka C# a Visual Basic  
 ![Spravovat vlastnosti projektu pro vzdálené ladění](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  V Průzkumníku řešení vyberte název projektu a klikněte na tlačítko **vlastnosti** z místní nabídky.  
  
2.  Vyberte **ladění**.  
  
3.  Zvolte **vzdálený počítač** z **cílové zařízení** seznamu.  
  
4.  Zadejte síťový název vzdáleného zařízení **vzdálený počítač** pole nebo zvolte **najít** pro výběr zařízení z **vyberte připojení vzdáleného ladicího programu** dialogové okno.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Volba vzdáleného zařízení pro projekty jazyka JavaScript a C++  
 ![C&#43; &#43; vlastnosti pro vzdálené ladění projektu](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  V Průzkumníku řešení vyberte název projektu a klikněte na tlačítko **vlastnosti** z místní nabídky.  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu a pak vyberte **ladění**.  
  
3.  Zvolte **vzdálený ladicí program** z **ladicí program ke spuštění** seznamu.  
  
4.  Zadejte síťový název vzdáleného zařízení **název počítače** pole nebo klikněte na šipku dolů v poli pro výběr ze zařízení **vyberte připojení vzdáleného ladicího programu** dialogové okno.  
  
##  <a name="BKMK_RunRemoteDebug"></a> Spuštění relace vzdáleného ladění  
 Spuštění, zastavení a procházení vzdálené ladicí relace stejným způsobem jako místní relaci. Před zahájením ladění, ujistěte se, že sledování vzdáleného ladění běží na vzdáleném zařízení.  
  
 Klikněte na tlačítko **spustit ladění** na **ladění** nabídce (klávesnice: F5). Projekt je znovu zkompilovat, pak nasadí do a spustit na vzdáleném zařízení. Ladicí program pozastaví provádění na zarážkách a můžete krokovat do, nad a z kódu. Zvolte **Zastavit ladění** ukončíte ladicí relaci a zavřete vzdálenou aplikaci. Další informace najdete v tématu [ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Testování aplikací pro Store pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)



