---
title: Vzdálené ladění ASP.NET jádro ve službě IIS a Azure | Dokumenty společnosti Microsoft
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385496"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Vzdálené ladění ASP.NET jádro ve službě IIS v Azure ve Visual Studiu

Tato příručka vysvětluje, jak nastavit a nakonfigurovat aplikaci Visual Studio ASP.NET Core, nasadit ji do služby IIS pomocí Azure a připojit vzdálený ladicí program z Visual Studia.

Doporučený způsob vzdáleného ladění v Azure závisí na vašem scénáři:

* Pokud chcete ladit ASP.NET core ve službě Azure App Service, přečtěte si informace o [ladění aplikací Azure pomocí ladicího programu snímků](../debugger/debug-live-azure-applications.md). Toto je doporučená metoda.
* Chcete-li ladit ASP.NET core ve službě Azure App Service pomocí tradičnějších funkcí ladění, postupujte podle kroků v tomto tématu (viz část [Vzdálené ladění ve službě Azure App Service).](#remote_debug_azure_app_service)

    V tomto scénáři je nutné nasadit aplikaci z Visual Studia do Azure, ale není nutné ručně nainstalovat nebo nakonfigurovat službu IIS nebo vzdálený ladicí program (tyto součásti jsou reprezentovány tečkovanými čarami), jak je znázorněno na následujícím obrázku.

    ![Součásti vzdáleného ladicího programu](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Chcete-li ladit službu IIS na virtuálním počítači Azure, postupujte podle kroků v tomto tématu (viz část [Vzdálené ladění na virtuálním počítači Azure).](#remote_debug_azure_vm) To umožňuje použít přizpůsobenou konfiguraci služby IIS, ale kroky nastavení a nasazení jsou složitější.

    Pro virtuální počítač Azure je nutné nasadit aplikaci z Visual Studia do Azure a také je potřeba ručně nainstalovat roli služby IIS a vzdálený ladicí program, jak je znázorněno na následujícím obrázku.

    ![Součásti vzdáleného ladicího programu](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Ladění ASP.NET jádra v Azure Service Fabric, najdete [v tématu ladění vzdálené aplikace Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Nezapomeňte odstranit prostředky Azure, které vytvoříte po dokončení kroků v tomto kurzu. Tímto způsobem se můžete vyhnout zbytečným poplatkům.

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"
Visual Studio 2019 je nutné postupovat podle kroků uvedených v tomto článku.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 je nutné postupovat podle kroků uvedených v tomto článku.
::: moniker-end

### <a name="network-requirements"></a>Síťové požadavky

Ladění mezi dvěma počítači připojenými prostřednictvím serveru proxy není podporováno. Ladění přes připojení s vysokou latencí nebo nízkou šířkou pásma, jako je například telefonický Internet nebo přes Internet v různých zemích, se nedoporučuje a může selhat nebo být nepřijatelně pomalé. Úplný seznam požadavků naleznete v tématu [Požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Vytvoření aplikace ASP.NET Core v počítači sady Visual Studio

1. Vytvořte novou aplikaci ASP.NET Core.

    ::: moniker range=">=vs-2019"
    Ve Visual Studiu 2019 otevřete vyhledávací pole **stisknutím kombinace kláves Ctrl + Q,** zadejte **asp.net**, zvolte **Šablony**a pak zvolte Vytvořit nový ASP.NET **základní webovou aplikaci**. V zobrazeném dialogovém okně pojmenujte projekt **MyASPApp**a pak zvolte **Vytvořit**. Dále zvolte **Webová aplikace (Model-View-Controller)** a pak zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V Sadě Visual Studio 2017 zvolte **Soubor > Nový > Project**a pak vyberte Visual **C# > Web > ASP.NET Core Web Application**. V části ASP.NET základní šablony vyberte **webovou aplikaci (Model-View-Controller).** Ujistěte se, že je vybrána ASP.NET Core 2.1, že není vybraná možnost **Povolit podporu Dockeru** a že **je možnost Ověřování** nastavena na možnost Žádné **ověřování**. Název projektu **MyASPApp**.
    ::: moniker-end

1. Otevřete soubor About.cshtml.cs a nastavte `OnGet` zarážku v metodě (ve starších šablonách otevřete HomeController.cs místo toho a nastavte zarážku v metodě). `About()`

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Vzdálené ladění ASP.NET jádro ve službě Azure App Service

Z Visual Studia můžete rychle publikovat a ladit aplikaci na plně zřízené instance služby IIS. Konfigurace služby IIS je však přednastavena a nelze ji přizpůsobit. Podrobnější pokyny najdete [v tématu Nasazení webové aplikace ASP.NET Core do Azure pomocí Visual Studia](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Pokud potřebujete přizpůsobit službu IIS, zkuste ladění na [virtuálním počítači Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Nasazení aplikace a vzdáleného ladění pomocí Průzkumníka Cloud

1. V sadě Visual Studio klikněte pravým tlačítkem myši na uzel projektu a zvolte **Publikovat**.

    Pokud jste dříve nakonfigurovali profily publikování, zobrazí se podokno **Publikovat.** Klepněte na **položku Nový profil**.

1. Zvolte **Azure App Service** z dialogového okna **Publikovat,** vyberte **Vytvořit nový**a postupujte podle pokynů k vytvoření profilu.

    Podrobné pokyny najdete [v tématu Nasazení webové aplikace ASP.NET Core do Azure pomocí Visual Studia](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikování do Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. V okně Publikovat zvolte **Upravit konfiguraci** a přepněte na konfiguraci ladění a pak zvolte **Publikovat**.

   K ladění aplikace je vyžadována konfigurace ladění.

1. Otevřete **Průzkumníka cloudu** (**Zobrazení** > **Průzkumníka cloudu),** klikněte pravým tlačítkem myši na instanci služby App Service a zvolte **Připojit ladicí program**.

   Pokud Průzkumník cloudu není k dispozici, otevřete místo toho Průzkumníka serveru. Potom klikněte pravým tlačítkem myši na instanci služby App Service v Průzkumníkovi serveru a zvolte **Připojit ladicí program**.

1. V aplikaci běžící ASP.NET klikněte na odkaz na stránku **Informace.**

    Zarážka by měla být přístupů v sadě Visual Studio.

    A to je vše! Zbývající kroky v tomto tématu platí pro vzdálené ladění na virtuálním počítači Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Vzdálené ladění ASP.NET jádro na virtuálním počítači Azure

Můžete vytvořit virtuální počítač Azure pro Windows Server a pak nainstalovat a nakonfigurovat službu IIS a další požadované softwarové součásti. To trvá déle než nasazení do služby Azure App Service a vyžaduje, abyste postupovali podle zbývajících kroků v tomto kurzu.

Tyto postupy byly testovány v těchto konfiguracích serveru:
* Windows Server 2012 R2 a Služba IIS 8
* Windows Server 2016 a Služba IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikace, která už běží ve službě IIS na virtuálním počítači Azure?

Tento článek obsahuje kroky k nastavení základní konfigurace služby IIS na serveru se systémem Windows a nasazení aplikace z visual studia. Tyto kroky jsou zahrnuty, abyste se ujistili, že server má nainstalovány požadované součásti, že aplikace může pracovat správně a že jste připraveni ke vzdálenému ladění.

* Pokud je vaše aplikace spuštěná ve službě IIS a chcete si stáhnout vzdálený ladicí program a spustit ladění, přejděte na [stáhnout a nainstalovat vzdálené nástroje v systému Windows Server](#BKMK_msvsmon).

* Pokud chcete pomoct s ujistěte se, že vaše aplikace je nastavená, nasazená a spuštěná správně ve službách IIS, abyste mohli ladit, postupujte podle všech kroků v tomto tématu.

  * Než začnete, postupujte podle všech kroků popsaných v [části Instalace a spuštění služby IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Při otevření portu 80 ve skupině zabezpečení sítě otevřete také [správný port](#bkmk_openports) pro vzdálený ladicí program (4024 nebo 4022). Tak to nebudeš muset později otevřít.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualizace nastavení zabezpečení prohlížeče v systému Windows Server

Pokud je v aplikaci Internet Explorer povolena konfigurace rozšířeného zabezpečení (ve výchozím nastavení je povolena), bude pravděpodobně nutné přidat některé domény jako důvěryhodné servery, abyste mohli stáhnout některé součásti webového serveru. Důvěryhodné servery můžete přidat tak, že přejdete na web **Možnosti internetu > > důvěryhodné servery > servery**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Při stahování softwaru můžete získat žádosti o udělení oprávnění k načtení různých skriptů a prostředků webových stránek. Některé z těchto prostředků nejsou povinné, ale pro zjednodušení procesu, klepněte na tlačítko **Přidat** po zobrazení výzvy.

### <a name="install-aspnet-core-on-windows-server"></a>Instalace ASP.NET jádra na Windows Server

1. Nainstalujte balíček [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) do hostitelského systému. Balíček nainstaluje modul .NET Core Runtime, knihovnu .NET Core library a ASP.NET Core Module. Podrobnější pokyny naleznete v tématu [Publikování do iis](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Pokud systém nemá připojení k Internetu, získejte a nainstalujte sadu *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* před instalací sady .NET Core Windows Server Hosting.

3. Restartujte systém (nebo spustit **net stop byl /y** následovaný **net start w3svc** z příkazového řádku vyzvednout změnu systému PATH).

## <a name="choose-a-deployment-option"></a>Volba možnosti nasazení

Pokud potřebujete pomoc s nasazením aplikace do služby IIS, zvažte tyto možnosti:

* Nasaďte se vytvořením souboru nastavení publikování ve službách IIS a importem nastavení v sadě Visual Studio. V některých případech se jedná o rychlý způsob nasazení aplikace. Při vytváření souboru nastavení publikování se ve službě IIS automaticky nastaví oprávnění.

* Nasaďte publikováním do místní složky a zkopírováním výstupu upřednostňovanou metodou do připravené složky aplikace ve službě IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Nepovinné) Nasazení pomocí souboru nastavení publikování

Tuto možnost můžete použít k vytvoření souboru nastavení publikování a importovat jej do sady Visual Studio.

> [!NOTE]
> Tato metoda nasazení používá nasazení webu. Chcete-li nakonfigurovat nasazení webu ručně v sadě Visual Studio namísto importu nastavení, můžete místo nasazení webu 3.6 pro hostitelské servery nainstalovat web deploy 3.6. Pokud však nakonfigurujete nasazení webu ručně, budete se muset ujistit, že složka aplikace na serveru je nakonfigurována se správnými hodnotami a oprávněními (viz [Konfigurace webu ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalace a konfigurace nasazení webu pro hostování serverů v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvoření souboru nastavení publikování ve službě IIS v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v Sadě Visual Studio a nasazení

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud se aplikace nespustí z Visual Studia, spusťte ji ve správě IIS. Pro ASP.NET jádra, musíte se ujistit, že pole fondu aplikací pro **DefaultAppPool** je nastavena na **žádný spravovaný kód**.

1. V dialogovém okně **Nastavení** povolte ladění klepnutím na tlačítko **Další**, zvolte konfiguraci **ladění** a pak v části možnosti **Publikování souboru** zvolte **Odebrat další soubory v cíli.**

    > [!NOTE]
    > Pokud zvolíte konfiguraci release, zakážete ladění v souboru *web.config* při publikování.

1. Klikněte na **Uložit** a potom aplikaci znovu publikujte.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Nepovinné) Nasazení publikováním do místní složky

Tuto možnost můžete použít k nasazení aplikace, pokud chcete zkopírovat aplikaci do služby IIS pomocí PowerShellu, RoboCopy nebo chcete ručně zkopírovat soubory.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurace webu ASP.NET Core v počítači se systémem Windows Server

Pokud importujete nastavení publikování, můžete tento oddíl přeskočit.

1. Otevřete **Správce Internetové informační služby (IIS)** a přejděte na web **servery**.

2. Klepněte pravým tlačítkem myši na výchozí uzel **webu** a vyberte přidat **aplikaci**.

3. Nastavte pole **Alias** na **MyASPApp** a pole Fond aplikací na **Bez spravovaného kódu**. Nastavte **fyzickou cestu** do **C:\Publish** (kde později nasadíte projekt ASP.NET Core).

4. S vybraným webem ve Správci služby IIS zvolte **Upravit oprávnění**a ujistěte se, že IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro fond aplikací je oprávněným uživatelem s právy pro čtení & spuštění.

    Pokud nevidíte jeden z těchto uživatelů s přístupem, projděte kroky k přidání IUSR jako uživatele s právy ke čtení & spuštění.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Nepovinné) Publikování a nasazení aplikace publikováním v místní složce z Visual Studia

Pokud nepoužíváte nasazení webu, musíte publikovat a nasadit aplikaci pomocí systému souborů nebo jiných nástrojů. Můžete začít vytvořením balíčku pomocí systému souborů a potom balíček nasadit ručně nebo použít jiné nástroje, jako je PowerShell, RoboCopy nebo XCopy. V této části předpokládáme, že ručně kopírujete balíček, pokud nepoužíváte nasazení webu.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Stažení a instalace vzdálených nástrojů v systému Windows Server

Stáhněte si verzi vzdálených nástrojů, která odpovídá vaší verzi sady Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Nastavení vzdáleného ladicího programu v systému Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změnit režim ověřování nebo číslo portu pro vzdálený ladicí program, přečtěte si informace [o konfiguraci vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Připojení k aplikaci ASP.NET z počítače sady Visual Studio

1. V počítači sady Visual Studio otevřete řešení, které se pokoušíte ladit (**MyASPApp,** pokud postupujte podle kroků v tomto článku).
2. V sadě Visual Studio klikněte na **ladění > připojit k procesu** (Ctrl + Alt + P).

    > [!TIP]
    > V sadě Visual Studio 2017 a novějších verzích můžete znovu připojit ke stejnému procesu, ke kterému jste dříve připojili pomocí **ladění > znovu připojit k procesu...** (Shift+Alt+P).

3. Nastavte pole Kvalifikátor na ** \<název vzdáleného počítače>** a stiskněte **Enter**.

    Ověřte, zda aplikace Visual Studio přidá požadovaný port k názvu počítače, který se zobrazí ve formátu: ** \<název vzdáleného počítače>:port**

    ::: moniker range=">=vs-2019"
    V sadě Visual Studio 2019 byste měli vidět ** \<název vzdáleného počítače>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V sadě Visual Studio 2017 byste měli vidět ** \<název vzdáleného počítače>:4022**
    ::: moniker-end
    Je vyžadován port. Pokud číslo portu nevidíte, přidejte ho ručně.

4. Klikněte na **Aktualizovat**.
    Některé procesy by se měly zobrazit v okně **Dostupné procesy.**

    Pokud nevidíte žádné procesy, zkuste místo názvu vzdáleného počítače použít ip adresu (je vyžadován port). Můžete použít `ipconfig` v příkazovém řádku získat adresu IPv4.

    Pokud chcete použít tlačítko **Najít,** bude pravděpodobně nutné [otevřít port UDP 3702](#bkmk_openports) na serveru.

5. Zaškrtněte **políčko Zobrazit procesy od všech uživatelů**.

6. Zadejte první písmeno názvu procesu, abyste aplikaci rychle našli.

    * Vyberte **dotnet.exe** (pro .NET Core)

      Pokud máte více procesů zobrazujících **dotnet.exe**, zkontrolujte sloupec **Uživatelské jméno.** V některých případech se ve sloupci **Uživatelské jméno** zobrazí název fondu aplikací, například **IIS APPPOOL\DefaultAppPool**. Pokud se zobrazí fond aplikací, snadný způsob, jak identifikovat správný proces je vytvořit nový pojmenovaný fond aplikací pro instanci aplikace, kterou chcete ladit, a pak ho můžete snadno najít ve sloupci **Uživatelské jméno.**

    * V některých scénářích iis můžete najít název aplikace v seznamu procesů, například **MyASPApp.exe**. Místo toho se můžete připojit k tomuto procesu.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klepněte na **tlačítko Připojit**.

8. Otevřete web vzdáleného počítače. V prohlížeči přejděte na **http://\<název vzdáleného počítače>**.

    Měli byste vidět ASP.NET webové stránky.
9. V aplikaci běžící ASP.NET klikněte na odkaz na stránku **Informace.**

    Zarážka by měla být přístupů v sadě Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Poradce při potížích: Otevření požadovaných portů v systému Windows Server

Ve většině nastavení jsou požadované porty otevřeny instalací ASP.NET a vzdáleného ladicího programu. Pokud však řešíte problémy s nasazením a aplikace je hostována za bránou firewall, bude pravděpodobně nutné ověřit, zda jsou otevřené správné porty.

Na virtuálním počítači Azure je nutné otevřít porty prostřednictvím [skupiny zabezpečení sítě](/azure/virtual-machines/windows/nsg-quickstart-portal).

Požadované porty:

* 80 - Vyžadováno pro IIS
::: moniker range=">=vs-2019"
* 4024 – Vyžadováno pro vzdálené ladění z Visual Studia 2019 (další informace najdete v [tématu Přiřazení portů vzdáleného ladicího programu).](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022 – Vyžadováno pro vzdálené ladění z Visual Studia 2017 (další informace najdete v [tématu Přiřazení portů vzdáleného ladicího programu).](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
* UDP 3702 - (Volitelné) Discovery port umožňuje **najít** tlačítko při připojování ke vzdálenému ladicímu programu v sadě Visual Studio.

Kromě toho by tyto porty měly být již otevřeny ASP.NET instalace:
- 8172 – (volitelné) Vyžadováno pro nasazení webu k nasazení aplikace z Visual Studia
