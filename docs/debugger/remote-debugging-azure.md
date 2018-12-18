---
title: Vzdálené ladění ASP.NET Core ve službě IIS a Azure | Dokumentace Microsoftu
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 821da7c5d131acea62e944055ec6c450e4bc5154
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101105"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Vzdálené ladění ASP.NET Core ve službě IIS v Azure v sadě Visual Studio 2017

Tato příručka vysvětluje, jak nastavit a konfigurace aplikace Visual Studio 2017 ASP.NET Core, nasaďte ji do služby IIS pomocí Azure a připojení vzdáleného ladicího programu ze sady Visual Studio.

Doporučeným způsobem, jak vzdálené ladění na Azure závisí na vašem scénáři:

* Ladění ASP.NET Core ve službě Azure App Service, naleznete v tématu [aplikace Azure ladění pomocí ladicího programu snímků](../debugger/debug-live-azure-applications.md). Toto je doporučená metoda.
* Ladění ASP.NET Core ve službě Azure App Service pomocí tradičnější funkce ladění, postupujte podle kroků v tomto tématu (naleznete v části [vzdálené ladění ve službě Azure App Service](#remote_debug_azure_app_service)).

    V tomto scénáři je nutné nasadit aplikaci do Azure ze sady Visual Studio, ale není potřeba ruční instalace nebo konfigurace služby IIS nebo vzdálený ladicí program (tyto součásti jsou reprezentovány s tečkované čáry), jak je znázorněno na následujícím obrázku.

    ![Vzdálený ladicí program komponenty](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Chcete-li ladit službu IIS na Virtuálním počítači Azure, postupujte podle kroků v tomto tématu (naleznete v části [vzdáleného ladění na Virtuálním počítači Azure](#remote_debug_azure_vm)). Díky tomu můžete použít vlastní konfiguraci služby IIS, ale postup instalace a nasazení je složitější.

    Pro virtuální počítač Azure je nutné nasadit aplikaci do Azure ze sady Visual Studio a také musíte ručně nainstalovat roli služby IIS a vzdálený ladicí program, jak je znázorněno na následujícím obrázku.

    ![Vzdálený ladicí program komponenty](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Ladění ASP.NET Core v Azure Service Fabric, naleznete v tématu [ladění vzdálené aplikace Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Nezapomeňte odstranit prostředky Azure, které vytvoříte, když jste dokončili kroky v tomto kurzu. Tímto způsobem můžete se vyhnout zbytečným poplatkům za něj.


### <a name="requirements"></a>Požadavky

Ladění mezi dvěma počítači připojený prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latencí nebo připojení s malou šířkou pásma, jako je například telefonického Internetu, nebo přes Internet napříč zeměmi se nedoporučuje a může selhat nebo být příliš pomalé. Úplný seznam požadavků, najdete v části [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Vytvoření aplikace ASP.NET Core v systému Visual Studio 2017 

1. Vytvoření nové aplikace ASP.NET Core. (Zvolte **soubor > Nový > projekt**a pak vyberte **Visual C# > Web > Webová aplikace ASP.NET Core**).

    V **ASP.NET Core** části šablony vyberte **webovou aplikaci**.

2. Ujistěte se, že **ASP.NET Core 2.0** je vybrána, který **povolit podporu Dockeru** je **není** vybrané a že **ověřování** je nastavena na **Bez ověřování**.

3. Pojmenujte projekt **MyASPApp** a klikněte na tlačítko **OK** k vytvoření nového řešení.

4. Otevřete soubor About.cshtml.cs a nastavte zarážku v `OnGet` – metoda (ve starších šablonách HomeController.cs místo toho otevřít a nastavit zarážku v `About()` metoda).

## <a name="remote_debug_azure_app_service"></a> Vzdálené ladění ASP.NET Core do služby Azure App Service

Ze sady Visual Studio můžete rychle publikovat a ladit aplikaci tak, aby plně zřízené instance služby IIS. Ale přednastavení konfiguraci služby IIS a nelze ho upravit. Podrobnější pokyny najdete v článku [nasazení webové aplikace ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Pokud je nutné přizpůsobit služby IIS, zkuste ladění [virtuálního počítače Azure](#remote_debug_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>K nasazení aplikace a vzdálené ladění pomocí Průzkumníka serveru

1. V sadě Visual Studio, klikněte pravým tlačítkem na uzel projektu a zvolte **publikovat**.

    Pokud jste dříve nakonfigurovali všech profilů publikování **publikovat** otevře se podokno. Klikněte na tlačítko **nový profil**.

1. Zvolte **služby Azure App Service** z **publikovat** dialogu **vytvořit nový**a postupujte podle pokynů k publikování.

    Podrobné pokyny najdete v tématu [nasazení webové aplikace ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikování do Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Otevřít **Průzkumníka serveru** (**zobrazení** > **Průzkumníka serveru**), klikněte pravým tlačítkem na instanci App Service a zvolte **připojit ladicí program**.

1. Ve spuštěné aplikaci ASP.NET, kliknutím na odkaz **o** stránky.

    Zarážka by měla být dosažena v sadě Visual Studio.

    Je to! Zbývající kroky v tomto tématu se vztahují na vzdálené ladění na Virtuálním počítači Azure.

## <a name="remote_debug_azure_vm"></a> Vzdálené ladění ASP.NET Core na Virtuálním počítači Azure

Můžete vytvořit virtuální počítač Azure pro Windows Server a potom nainstalovat a nakonfigurovat službu IIS a další požadované softwarové komponenty. To trvá déle než nasazení do služby Azure App Service a vyžaduje, abyste postupovali podle pokynů v tomto kurzu.

Nejprve, postupujte podle kroků popsaných v [instalace a spuštění služby IIS](/azure/virtual-machines/windows/quick-create-portal).

Při otevření portu 80 ve skupině zabezpečení sítě také otevřete port 4022 pro vzdálený ladicí program. Tímto způsobem není nutné jej spustit později.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikace už běží ve službě IIS na virtuálním počítači Azure?

Tento článek obsahuje kroky k nastavení základní konfiguraci služby IIS na Windows serveru a nasazení aplikace v sadě Visual Studio. Tyto kroky jsou zahrnuty, abyste měli jistotu, že server má požadované součásti nainstalované, že aplikace může běžet správně a že budete chtít vzdáleného ladění.

* Pokud vaše aplikace běží ve službě IIS a chcete jenom chcete stáhnout vzdálený ladicí program a spusťte ladění, přejděte na [stáhněte a nainstalujte nástroje remote tools v systému Windows Server](#BKMK_msvsmon).

* Pokud potřebujete pomoc, abyste měli jistotu, že vaše aplikace je nastavené, nasazení a fungování ve službě IIS, takže můžete ladit, postupujte podle všech kroků v tomto tématu.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualizovat nastavení zabezpečení prohlížeče ve Windows serveru

Pokud je povolená konfigurace rozšířeného zabezpečení aplikace Internet Explorer (je povolená ve výchozím nastavení), budete muset přidat některé domény jako důvěryhodné servery, které chcete stáhnout, některé součásti webového serveru. Přidat důvěryhodné servery tak, že přejdete do **Možnosti Internetu > zabezpečení > důvěryhodných serverů > servery**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Když si stáhnete software, se může zobrazit žádosti o udělení oprávnění k načítání různých skriptů na webu a prostředky. Některé z těchto zdrojů nejsou vyžadovány, ale pro zjednodušení procesu, klikněte na tlačítko **přidat** po zobrazení výzvy.

### <a name="install-aspnet-core-on-windows-server"></a>Nainstalujte aplikaci ASP.NET Core v systému Windows Server

1. Nainstalujte [.NET Core Windows serveru, který hostuje](https://aka.ms/dotnetcore-2-windowshosting) sady v hostitelském systému. Sady nainstaluje modul Runtime .NET Core, .NET Core Library a že modul ASP.NET Core. Další podrobné pokyny najdete v tématu [publikování do služby IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Pokud systém nemá připojení k Internetu, získejte a nainstalujte *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* před instalací sady .NET Core Windows serveru, který hostuje.

3. Restartování systému (nebo když spouští **net stop byla /y** následovaný **net start w3svc** z příkazového řádku ke sbírání změnit CESTU v systému).

## <a name="choose-a-deployment-option"></a>Vyberte možnost nasazení

Pokud potřebujete nápovědu k nasazení aplikace do služby IIS, zvažte tyto možnosti:

* Nasazení vytvořením soubor nastavení publikování ve službě IIS a importu nastavení v sadě Visual Studio. V některých případech to je rychlý způsob nasazení vaší aplikace. Když vytvoříte soubor nastavení publikování, oprávnění se automaticky nastaví ve službě IIS.

* Nasazení publikování do místní složky a zkopírování výstupu upřednostňovanou metodou do složky připravené aplikace ve službě IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Volitelné) Nasazení pomocí souboru nastavení publikování

Tuto možnost můžete použít vytvořit soubor nastavení publikování a importujte ho do sady Visual Studio.

> [!NOTE]
> Tato metoda nasazení používá, nasazení webu. Pokud chcete nakonfigurovat nasazení webu ručně v sadě Visual Studio namísto importu nastavení, můžete nainstalovat webové nasazení 3.6 místo 3.6 webové nasazení pro servery hostující. Nicméně pokud ručně nakonfigurujete nasazení webu, budete muset Ujistěte se, že složka aplikace na serveru se nakonfigurují správné hodnoty a oprávnění (viz [konfigurace webu ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalace a konfigurace nasazení webu pro hostování servery v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvořit soubor nastavení publikování ve službě IIS v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v sadě Visual Studio a nasazení

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Jakmile se aplikace nasadí úspěšně, by se měl spustit automaticky. Pokud aplikace ze sady Visual Studio nespustí, spusťte aplikaci ve službě IIS. Pro ASP.NET Core, budete muset Ujistěte se, že se fond aplikací pro pole **DefaultAppPool** je nastavena na **bez spravovaného kódu**.

1. V **nastavení** dialogové okno, povolte ladění kliknutím **Další**, zvolte **ladění** konfigurace a klikněte na tlačítko **odebrat další soubory v určení** pod **publikování souboru** možnosti.

    > [!NOTE]
    > Pokud vyberete možnost konfigurace vydané verze, můžete zakázat ladění v *web.config* souboru při publikování.

1. Klikněte na tlačítko **Uložit** a pak znovu publikovat aplikaci.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Volitelné) Nasazení na základě publikování do místní složky

Tuto možnost můžete použít k nasazení své aplikace, pokud chcete zkopírovat do služby IIS pomocí Powershellu, RoboCopy, aplikace nebo chcete ručně zkopírovat soubory.

### <a name="BKMK_deploy_asp_net"></a> Konfigurace webu ASP.NET na počítač s Windows serverem

Při importu nastavení publikování, můžete tuto část přeskočit.

1. Otevřít **Správce Internetové informační služby (IIS)** a přejděte na **lokality**.

2. Klikněte pravým tlačítkem myši **výchozí webový server** uzel a vyberte možnost **přidat aplikaci**.

3. Nastavte **Alias** pole **MyASPApp** a pole fondu aplikací a **bez spravovaného kódu**. Nastavte **fyzická cesta** k **C:\Publish** (kde později nasadíte projekt ASP.NET).

4. Vybrání ve Správci služby IIS lokality vyberte **upravit oprávnění**a ujistěte se, že IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro fond aplikací je oprávněný uživatel s oprávněními Číst a spouštět.

    Pokud nevidíte jeden z těchto uživatelů s přístupem, projděte si kroky pro přidání IUSR jako uživatel s oprávněním Číst a spouštět.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Volitelné) Publikujte a nasaďte aplikaci publikováním do místní složky ze sady Visual Studio

Pokud nepoužíváte nasazení webu, musíte publikovat a nasazení aplikace pomocí systému souborů nebo jiných nástrojů. Můžete začít tak, že vytvoříte balíček pomocí systému souborů a pak nasadit balíček ručně nebo použít jiné nástroje, jako je PowerShell, RoboCopy nebo příkazu XCopy. V této části předpokládáme, že jsou ručně kopírování balíčku, pokud nepoužíváte, nasazení webu.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Stáhněte a nainstalujte nástroje remote tools v systému Windows Server

V tomto kurzu se používá Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Nastavení vzdáleného ladicího programu v systému Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změnit režim ověřování, nebo číslo portu pro vzdálené ladění, naleznete v tématu [konfigurovat vzdálený ladicí program](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Připojení k aplikaci ASP.NET ze sady Visual Studio

1. Na počítači aplikace Visual Studio otevřete řešení, které se pokoušíte ladit (**MyASPApp** pokud postupujete kroky v tomto článku).
2. V sadě Visual Studio, klikněte na tlačítko **ladit > připojit k procesu** (Ctrl + Alt + P).

    > [!TIP]
    > V sadě Visual Studio 2017, můžete znovu připojit do stejného procesu dříve připojena k pomocí **ladit > znovu připojit k procesu...** (Shift + Alt + P). 

3. Nastavit pole kvalifikátor  **\<název vzdáleného počítače >: 4022**.
4. Klikněte na tlačítko **aktualizovat**.
    Měli byste vidět některé procesy, které se zobrazí v **procesy k dispozici** okna.

    Pokud se nezobrazí všechny procesy, použijte adresu IP místo názvu vzdáleného počítače (port, který se vyžaduje). Můžete použít `ipconfig` v příkazovém řádku k získání adresy IPv4.

    Pokud chcete použít **najít** tlačítko, možná budete muset [otevřete UDP port 3702](#bkmk_openports) na serveru.

5. Zkontrolujte **Zobrazit procesy všech uživatelů**.

6. Zadejte první písmeno názvu procesu a rychle najít *dotnet.exe* (pro ASP.NET Core).
   
   Pro aplikace ASP.NET Core, názvem předchozího procesu byla *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klikněte na tlačítko **připojit**.

8. Otevřete web, vzdáleném počítači. V prohlížeči přejděte na **http://\<název vzdáleného počítače >**.
    
    Zobrazí se webová stránka ASP.NET.
9. Ve spuštěné aplikaci ASP.NET, kliknutím na odkaz **o** stránky.

    Zarážka by měla být dosažena v sadě Visual Studio.

### <a name="bkmk_openports"></a> Řešení potíží: Otevřete požadované porty ve Windows serveru

Ve většině nastavení jsou otevřené požadované porty instalace technologie ASP.NET a vzdálený ladicí program. Nicméně pokud řešíte potíže s nasazením a je hostovaná aplikace za bránou firewall, můžete ověřit, že jsou otevřené správné porty.

Na Virtuálním počítači Azure, musíte otevřít porty prostřednictvím [skupinu zabezpečení sítě](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic). 

Požadované porty:

- 80 – požadováno pro službu IIS
- 4022 – požadováno pro vzdálené ladění ze sady Visual Studio 2017 (viz [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md) Další informace).
- UDP 3702 – port (volitelné) zjišťování umožňuje **najít** tlačítko při připojování vzdáleného ladicího programu v sadě Visual Studio.

Kromě toho by měl tyto porty otevřít již instalace technologie ASP.NET:
- 8172 – (volitelné) požadované pro nasazení webu k nasazování aplikací ze sady Visual Studio

