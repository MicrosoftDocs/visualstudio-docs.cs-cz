---
title: Vzdálené ladění ASP.NET ve vzdálené službě IIS 7.5 počítače | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d249571830ac608bef12c4a47d0243de1859a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764075"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Vzdálené ladění ASP.NET na počítači vzdálené služby IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nasadit webové aplikace ASP.NET na počítači s Windows serverem a službou IIS a připravit prostředí pro vzdálené ladění. Tato příručka vysvětluje, jak nastavit a nakonfigurovat aplikaci s Visual Studio 2015 MVC 4.5.2, nasaďte ji do služby IIS a připojení vzdáleného ladicího programu ze sady Visual Studio.

Tyto postupy jsme otestovali na tyto konfigurace serveru:
* Windows Server 2012 R2 a služby IIS 10
* Windows Server 2008 R2 a služby IIS 7.5

Většinu informací v tomto článku platí také pro vzdálené ladění aplikace ASP.NET Core, s tím rozdílem, že nasazení aplikace v ASP.NET core je jiné a vyžaduje dodatečné kroky. Pokud chcete nasadit aplikace ASP.NET Core do služby IIS, je potřeba dokončit všechny oddíly [v tomto článku](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Předpoklady: Nainstalujte vzdálený ladicí program na počítač s Windows serverem

Pokyny ohledně toho, jak stáhnout vzdálený ladicí program na počítač s Windows serverem, najdete v části [vzdálené ladění](../debugger/remote-debugging.md).

Provádět vzdálené ladění aplikací ASP.NET, můžete spustit aplikaci vzdáleného ladícího programu jako správce nebo spustit vzdálený ladicí program jako službu. Podrobnosti o tom, jak spustit vzdálený ladicí program jako službu lze nalézt v [vzdálené ladění](../debugger/remote-debugging.md).

Po instalaci, ujistěte se, že vzdálený ladicí program je spuštěn na cílovém počítači. (Pokud není, vyhledejte **vzdálený ladicí program** v **Start** nabídky. ) V okně vzdáleného ladicího programu vypadá takto. (výchozí číslo portu je 4020)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Vytvoření aplikace na počítači aplikace Visual Studio  
  
1. Vytvoření nové aplikace MVC ASP.NET. (**Soubor / nový / Project**a pak vyberte **Visual C# / Web / webové aplikace ASP.NET** . V **ASP.NET 4.5.2** části šablony vyberte **MVC**. Ujistěte se, že **hostitel v cloudu** není vybraná v části Azure. Pojmenujte projekt **MyMVC**.)
1. Otevření souboru HomeController.cs a nastavte zarážku `About()` metody.
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **publikovat**.
1. Pro **vybrat cíl publikování**vyberte **vlastní** a název profilu **MyMVC**. Klikněte na tlačítko **Další**.
1. Na **připojení** kartu, nastavte **metodu publikování** pole **systému souborů** a **cílové umístění** pole do místního adresáře. Klikněte na tlačítko **Další**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Nastavení konfigurace **ladění**. Klikněte na tlačítko **publikovat**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Aplikace by měla publikována do místního adresáře.

## <a name="BKMK_deploy_asp_net"></a> Nasazení aplikace ASP.NET Windows Server ve vzdáleném počítači

 Této části se předpokládá, že počítač s Windows serverem už má službu IIS. Ve Windows serveru 2012 R2 najdete v článku [konfiguraci služby IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) povolit služby IIS. (Ostatní části tohoto článku můžete přeskočit Pokud se pokoušíte nasadit aplikace ASP.NET Core. Pro ASP.NET Core postupujte podle kroků v článku nasadíme aplikaci namísto zde popsané kroky.)
1. Instalace technologie ASP.NET použití komponenty webové platformy nainstalovat technologii ASP.NET 4.5 (z uzlu serveru ve Windows serveru 2012 R2, zvolte **získat nové komponenty webové platformy** a vyhledejte technologie ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    V systému Windows Server 2008 R2, nainstalujte místo toho pomocí tohoto příkazu ASP.NET 4: **\v4.0.30319\aspnet_regiis.exe C:\Windows\Microsoft.NET\Framework (64) – prostředí ir**
1. Zkopírujte adresář projektu ASP.NET ze sady Visual Studio do místního adresáře (který nazveme **C:\Publish**) na počítač s Windows serverem. Můžete zkopírovat projektu ručně, pomocí příkazu Xcopy, nasazení webu, Robocopy, Powershellu nebo jiné možnosti.

    > [!CAUTION]
    >  Pokud potřebujete provést změny v kódu nebo znovu sestavit, musíte znovu publikovat a opakujte tento krok. Spustitelný soubor, který jste zkopírovali do vzdáleného počítače se musí přesně odpovídat, místní zdroje a symbolů.
1. Ujistěte se, že soubor web.config obsahuje správnou verzi rozhraní .NET Framework.  Například je nainstalovaná ve výchozím nastavení v systému Windows Server 2008 R2 rozhraní .NET Framework verze 4.0.30319, ale jsme vytvořili ASP.NET 4.5.2 verze. Pokud aplikace technologie ASP.NET 4.0 běží na počítač s Windows serverem, musíte změnit verzi:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```
1. Otevřít **Správce Internetové informační služby (IIS)** a přejděte na **lokality**.
1. Klikněte pravým tlačítkem myši **výchozí webový server** uzel a vyberte možnost **přidat aplikaci**.
1. Nastavte **Alias** pole **MyMVC** a pole fondu aplikací a **ASP.NET v4.0** (ASP.NET 4.5 není možné zvolit pro fond aplikací). Nastavte **fyzická cesta** k **C:\Publish** (kde jste zkopírovali adresáři projektu ASP.NET).

    >[!NOTE] 
    > Pro aplikace ASP.NET Core, nastavte pole fond aplikací na **bez spravovaného kódu**.
1. Test nasazení kliknutím pravým tlačítkem myši **výchozí webový server** a vyberte **Procházet**.
    Pokud jste úspěšně nasadili aplikace, zobrazí se webové stránky.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Připojení k aplikaci ASP.NET ze sady Visual Studio

1. Na počítači, Visual Studio, otevřete **MyMVC** řešení.
1. V sadě Visual Studio, klikněte na tlačítko **ladění / připojit k procesu** (**Ctrl + Alt + P**).
1. Nastavit pole kvalifikátor  **\<název vzdáleného počítače >: 4020**.
1. Klikněte na tlačítko **aktualizovat**.
    Měli byste vidět některé procesy, které se zobrazí v **procesy k dispozici** okna.

    Pokud se nezobrazí všechny procesy, použijte adresu IP místo názvu vzdáleného počítače (port, který se vyžaduje). Použití `ipconfig` v příkazovém řádku k získání adresy IPv4.
1. Zkontrolujte **Zobrazit procesy všech uživatelů**.
1. Vyhledejte **w3wp.exe** a klikněte na tlačítko **připojit**.

     Chcete-li rychle vyhledat název procesu, zadejte první písmeno procesu.
     
    >[!NOTE]
    > Pro aplikace ASP.NET Core vyberte proces dnx.exe místo w3wp.exe. (Název tohoto procesu může změnit v nadcházející verzi.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Otevřete web, vzdáleném počítači. V prohlížeči přejděte na **http://\<název vzdáleného počítače >**.
    
    Zobrazí se webová stránka ASP.NET.
1. Na webové stránce ASP.NET, kliknutím na odkaz **o** stránky.

    Zarážka by měla být dosažena v sadě Visual Studio.



