---
title: Vzdálené ladění ASP.NET na vzdáleném počítači IIS 7,5 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807152"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nasadit webovou aplikaci v ASP.NET do počítače se systémem Windows Server se službou IIS a nastavit ji pro vzdálené ladění. Tato příručka vysvětluje, jak nastavit a nakonfigurovat aplikaci Visual Studio 2015 MVC 4.5.2, jak ji nasadit do služby IIS a jak připojit vzdálený ladicí program ze sady Visual Studio.

Tyto postupy byly testovány na těchto konfiguracích serveru:
* Windows Server 2012 R2 a IIS 10
* Windows Server 2008 R2 a IIS 7,5

Většina informací v tomto článku platí taky pro vzdálené ladění aplikace ASP.NET Core, s výjimkou toho, že nasazení ASP.NET Core Apps se liší a vyžaduje další kroky. Pokud chcete nasadit aplikaci ASP.NET Core do služby IIS, budete muset dokončit všechny části [tohoto článku](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Požadavky: Instalace vzdáleného ladicího programu na počítač se systémem Windows Server

Pokyny ke stažení vzdáleného ladicího programu na počítač se systémem Windows Server najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

Chcete-li provést vzdálené ladění aplikací ASP.NET, můžete buď spustit aplikaci vzdáleného ladícího programu jako správce, nebo spustit vzdálený ladicí program jako službu. Podrobnosti o tom, jak spustit vzdálený ladicí program jako službu, najdete ve [vzdáleném ladění](../debugger/remote-debugging.md).

Po instalaci se ujistěte, že je na cílovém počítači spuštěný vzdálený ladicí program. (Pokud není, vyhledejte **vzdálený ladicí program** v nabídce **Start** . ) Okno vzdáleného ladicího programu vypadá takto. (výchozí číslo portu 4020)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Vytvoření aplikace na počítači se systémem Visual Studio  
  
1. Vytvořte novou aplikaci MVC ASP.NET. (**Soubor/nový/projekt**a pak vyberte **Webová aplikace Visual C#/web/ASP.NET** . V části šablony **ASP.NET 4.5.2** vyberte **MVC**. Ujistěte se, že v části Azure není vybraná možnost **hostitel v cloudu** . Pojmenujte projekt **MyMVC**.)
1. Otevřete soubor HomeController.cs a nastavte zarážku v `About()` metodě.
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **publikovat**.
1. Pro **možnost vybrat cíl publikování**vyberte **vlastní** a pojmenujte profil **MyMVC**. Klikněte na **Next** (Další).
1. Na kartě **připojení** nastavte v poli **Metoda publikování** na **systém souborů** a **cílové umístění** do místního adresáře. Klikněte na **Next** (Další).

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Nastavte konfiguraci pro **ladění**. Klikněte na **Publikovat**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Aplikace by měla být publikována do místního adresáře.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Nasazení aplikace ASP.NET na vzdáleném počítači se systémem Windows Server

 V této části se předpokládá, že počítač se systémem Windows Server již má povolenou službu IIS. V systému Windows Server 2012 R2 se podívejte na téma [Konfigurace služby IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) , která povoluje službu IIS. (Další části tohoto článku můžete přeskočit, pokud se nepokoušíte nasadit aplikaci ASP.NET Core. V případě ASP.NET Core postupujte podle kroků v článku nasazení aplikace namísto kroků popsaných zde.)
1. Instalace ASP.NET použijte komponenty webové platformy k instalaci ASP.NET 4,5 (z uzlu serveru v systému Windows Server 2012 R2 zvolte možnost **získat nové součásti webové platformy** a pak vyhledejte ASP.NET).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    V systému Windows Server 2008 R2 nainstalujte místo toho ASP.NET 4 pomocí tohoto příkazu:   **C:\Windows\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe-IR**
1. Zkopírujte adresář projektu ASP.NET z počítače se systémem Visual Studio do místního adresáře (který zavoláme **C:\Publish**) na počítači se systémem Windows Server. Projekt můžete kopírovat ručně, pomocí příkazu xcopy, Nasazení webu, Robocopy, PowerShellu nebo jiných možností.

    > [!CAUTION]
    > Pokud potřebujete provést změny v kódu nebo znovu sestavit, musíte znovu publikovat a opakovat tento krok. Spustitelný soubor, který jste zkopírovali do vzdáleného počítače, se musí přesně shodovat s vaším místním zdrojem a symboly.
1. Ujistěte se, že web.config soubor obsahuje seznam správné verze .NET Framework.  Například verze .NET Framework nainstalovaná ve výchozím nastavení v systému Windows Server 2008 R2 je 4.0.30319, ale vytvořili jsme verzi ASP.NET 4.5.2. Pokud je aplikace ASP.NET 4,0 spuštěná na počítači se systémem Windows Server, je nutné změnit verzi:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Otevřete **správce Internetová informační služba (IIS)** a pokračujte na **lokality**.
1. Klikněte pravým tlačítkem myši na uzel **výchozí web** a vyberte **Přidat aplikaci**.
1. V poli **alias** nastavte **MyMVC** a pole fond aplikací na **ASP.NET v 4.0** (ASP.NET 4,5 není možností pro fond aplikací). Nastavte **fyzickou cestu** na **C:\Publish** (kam jste zkopírovali adresář projektu ASP.NET).

    >[!NOTE] 
    > U aplikací ASP.NET Core nastavte pole fond aplikací na **žádný spravovaný kód**.
1. Otestujte nasazení tak, že kliknete pravým tlačítkem na **výchozí web** a vyberte **Procházet**.
    Pokud jste aplikaci úspěšně nasadili, zobrazí se webová stránka.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Připojení k aplikaci ASP.NET z počítače s Visual Studiem

1. V počítači se systémem Visual Studio otevřete řešení **MyMVC** .
1. V aplikaci Visual Studio klikněte na možnost **ladit/připojit k procesu** (**CTRL + ALT + P**).
1. Nastavte pole Kvalifikátor na ** \<remote computer name> : 4020**.
1. Klikněte na **Aktualizovat**.
    V okně **Dostupné procesy** by se měly zobrazit některé procesy.

    Pokud nevidíte žádné procesy, zkuste místo názvu vzdáleného počítače použít IP adresu (vyžaduje se port). `ipconfig`K získání adresy IPv4 použijte příkazový řádek.
1. Zaškrtávací políčka  **Zobrazit procesy všech uživatelů**.
1. Vyhledejte **w3wp.exe** a klikněte na **připojit**.

     Chcete-li rychle najít název procesu, zadejte první písmeno procesu.
     
    >[!NOTE]
    > V případě aplikace ASP.NET Core vyberte dnx.exe proces namísto w3wp.exe. (Tento název procesu se může v nadcházející verzi změnit.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Otevřete web vzdáleného počítače. V prohlížeči, navštivte **http:// \<remote computer name> **.
    
    Měla by se zobrazit webová stránka ASP.NET.
1. Na webové stránce ASP.NET klikněte na odkaz na stránku **o produktu** .

    Zarážka by měla být dosaženo v aplikaci Visual Studio.
