---
title: Vzdálené ladění ASP.NET Core ve službě IIS a Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 926bd4a6630d9d99726ee6c1479d04c476756c18
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2020
ms.locfileid: "92298751"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Vzdálené ladění ASP.NET Core ve službě IIS v Azure v aplikaci Visual Studio

Tato příručka vysvětluje, jak nastavit a nakonfigurovat aplikaci Visual Studio ASP.NET Core, jak ji nasadit do služby IIS pomocí Azure a jak připojit vzdálený ladicí program ze sady Visual Studio.

Doporučený způsob vzdáleného ladění v Azure závisí na vašem scénáři:

* Pokud chcete ladit ASP.NET Core Azure App Service, přečtěte si téma [ladění aplikací Azure pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md). Toto je doporučená metoda.
* Chcete-li ladit ASP.NET Core Azure App Service pomocí tradičních funkcí ladění, postupujte podle kroků v tomto tématu (viz část [vzdálený ladění v Azure App Service](#remote_debug_azure_app_service)).

    V tomto scénáři je nutné nasadit aplikaci ze sady Visual Studio do Azure, ale nemusíte ručně instalovat nebo konfigurovat službu IIS ani vzdálený ladicí program (tyto komponenty jsou reprezentovány s tečkami), jak je znázorněno na následujícím obrázku.

    ![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Pokud chcete ladit službu IIS na virtuálním počítači Azure, postupujte podle kroků v tomto tématu (viz část [vzdálený ladění na virtuálním počítači Azure](#remote_debug_azure_vm)). To vám umožní používat vlastní konfiguraci služby IIS, ale kroky pro instalaci a nasazení jsou složitější.

    V případě virtuálního počítače Azure je nutné nasadit aplikaci ze sady Visual Studio do Azure a také je nutné ručně nainstalovat roli služby IIS a vzdálený ladicí program, jak je znázorněno na následujícím obrázku.

    ![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Chcete-li ladit ASP.NET Core v Azure Service Fabric, přečtěte si téma [ladění vzdálené Service Fabric aplikace](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Nezapomeňte odstranit prostředky Azure, které vytvoříte po dokončení kroků v tomto kurzu. Tímto způsobem se můžete vyhnout zbytečnému navýšení poplatků.

## <a name="prerequisites"></a>Předpoklady

::: moniker range=">=vs-2019"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2017.
::: moniker-end

### <a name="network-requirements"></a>Požadavky sítě

Ladění mezi dvěma počítači připojenými prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latenci nebo připojení s nízkou šířkou pásma, jako je například telefonické připojení k Internetu nebo přes Internet v zemích, se nedoporučuje a může být neúspěšné nebo nepřijatelně pomalé. Úplný seznam požadavků najdete v tématu [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Vytvoření aplikace ASP.NET Core v počítači se systémem Visual Studio

1. Vytvořte novou ASP.NET Core aplikaci.

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 zadejte **CTRL + Q** pro otevření vyhledávacího pole, zadejte **ASP.NET**, zvolte **šablony**a pak zvolte **vytvořit novou ASP.NET Core webovou aplikaci**. V dialogovém okně, které se zobrazí, pojmenujte projekt **MyASPApp**a pak zvolte **vytvořit**. Dále zvolte možnost **Webová aplikace (model-zobrazení-kontroler)** a pak zvolte možnost **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 zvolte **soubor > nový > projekt**, a pak vyberte **Visual C# > webová aplikace Web > ASP.NET Core**. V části šablony ASP.NET Core vyberte možnost **Webová aplikace (model-zobrazení-kontroler)**. Ujistěte se, že je vybrána možnost ASP.NET Core 2,1, možnost **Povolit podporu Docker** není vybrána a toto **ověřování** je nastaveno na **bez ověřování**. Pojmenujte projekt **MyASPApp**.
    ::: moniker-end

1. Otevřete soubor About.cshtml.cs a nastavte zarážku v `OnGet` metodě (ve starších šablonách otevřete HomeController.cs místo toho a nastavte zarážku v `About()` metodě).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Vzdálené ladění ASP.NET Core na Azure App Service

Ze sady Visual Studio můžete rychle publikovat a ladit aplikaci do plně zřízené instance služby IIS. Konfigurace služby IIS je však přednastavená a nelze ji přizpůsobit. Podrobnější pokyny najdete v tématu [nasazení webové aplikace ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Pokud potřebujete možnost přizpůsobit IIS, vyzkoušejte si ladění na [virtuálním počítači Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Nasazení aplikace a vzdáleného ladění pomocí Průzkumníka cloudu

1. V aplikaci Visual Studio klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **publikovat**.

    Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Klikněte na **Nový profil**.

1. V dialogovém okně **publikovat** zvolte **Azure App Service** , vyberte **vytvořit novou**a podle pokynů vytvořte profil.

    Podrobné pokyny najdete v tématu [nasazení webové aplikace v ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikování do Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. V okně Publikovat zvolte možnost **Upravit konfiguraci** a přepněte na konfiguraci ladění a pak zvolte **publikovat**.

   Pro ladění aplikace je nutná konfigurace ladění.

1. Otevřete **Průzkumníka cloudu** (**Zobrazit**  >  **Průzkumníka cloudu**), klikněte pravým tlačítkem na instanci App Service a vyberte **připojit ladicí program**.

   Pokud není k dispozici Průzkumník cloudu, otevřete místo toho Průzkumník serveru. Potom klikněte pravým tlačítkem na instanci App Service v Průzkumník serveru a zvolte **připojit ladicí program**.

1. Ve spuštěné aplikaci ASP.NET klikněte na odkaz na stránku **o** aplikaci.

    Zarážka by měla být dosaženo v aplikaci Visual Studio.

    A to je vše! Zbývající kroky v tomto tématu se vztahují na vzdálené ladění na virtuálním počítači Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Vzdálené ladění ASP.NET Core na virtuálním počítači Azure

Můžete vytvořit virtuální počítač Azure pro Windows Server a pak nainstalovat a nakonfigurovat službu IIS a další požadované softwarové součásti. Trvá to déle než nasazení do Azure App Service a vyžaduje, abyste procházeli podle zbývajících kroků v tomto kurzu.

Tyto postupy byly testovány na těchto konfiguracích serveru:
* Windows Server 2012 R2 a IIS 8
* Windows Server 2016 a IIS 10
* Windows Server 2019 a IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikace už běží ve službě IIS na virtuálním počítači Azure?

Tento článek obsahuje kroky pro nastavení základní konfigurace služby IIS na Windows serveru a nasazení aplikace ze sady Visual Studio. Tyto kroky jsou zahrnuty, abyste se ujistili, že server má nainstalované požadované součásti, že aplikace funguje správně a že jste připraveni ke vzdálenému ladění.

* Pokud je vaše aplikace spuštěná ve službě IIS a vy chcete stáhnout vzdálený ladicí program a spustit ladění, použijte ke [Stažení a instalaci nástrojů Remote Tools na Windows Server](#BKMK_msvsmon).

* Pokud chcete zajistit, aby se vaše aplikace nastavila, nasadila a běžela správně ve službě IIS, abyste mohli ladit, postupujte podle všech kroků v tomto tématu.

  * Než začnete, postupujte podle kroků popsaných v tématu [instalace a spuštění služby IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Když otevřete port 80 ve skupině zabezpečení sítě, otevřete také [správný port](#bkmk_openports) pro vzdálený ladicí program (4024 nebo 4022). Tímto způsobem ho nebudete muset otevřít později. Pokud používáte Nasazení webu, otevřete také port 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualizace nastavení zabezpečení prohlížeče na Windows serveru

Pokud je v Internet Exploreru povolená konfigurace rozšířeného zabezpečení (ve výchozím nastavení je povolená), možná budete muset přidat některé domény jako důvěryhodné servery, abyste si mohli stáhnout některé součásti webového serveru. Přidejte důvěryhodné servery tak, že v části **Možnosti internetu > zabezpečení > důvěryhodné servery > lokality**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Po stažení softwaru můžete získat žádosti o udělení oprávnění k načtení různých skriptů a prostředků webu. Některé z těchto prostředků se nevyžadují, ale pro zjednodušení procesu klikněte po zobrazení výzvy na **Přidat** .

### <a name="install-aspnet-core-on-windows-server"></a>Instalace ASP.NET Core v systému Windows Server

1. Nainstalujte hostující sadu .NET Core do hostitelského systému. Svazek nainstaluje modul runtime .NET Core, knihovnu .NET Core a modul ASP.NET Core. Podrobné pokyny najdete v tématu [publikování do služby IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    Pro .NET Core 3 nainstalujte hostující sadu [.NET Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    Pro .NET Core 2 nainstalujte [hostování Windows serveru .NET Core](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Pokud systém nemá připojení k Internetu, Stáhněte a nainstalujte *[Microsoft Visual C++ 2015 Distribuovatelný](https://www.microsoft.com/download/details.aspx?id=53840)* před instalací hostitelské sady Windows serveru .NET Core.

3. Restartujte systém (nebo spusťte příkaz **net stop** , který následuje po příkazu **net start w3svc** z příkazového řádku pro výběr změny systémové cesty).

## <a name="choose-a-deployment-option"></a>Zvolit možnost nasazení

Pokud potřebujete pomáhat s nasazením aplikace do služby IIS, zvažte tyto možnosti:

* Nasaďte je vytvořením souboru nastavení publikování ve službě IIS a importem nastavení v aplikaci Visual Studio. V některých scénářích je to rychlý způsob, jak aplikaci nasadit. Při vytváření souboru nastavení publikování se oprávnění automaticky nastaví ve službě IIS.

* Nasazení provedete publikováním do místní složky a zkopírováním výstupu upřednostňovanou metodou do připravené složky aplikace ve službě IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Volitelné Nasazení pomocí souboru nastavení publikování

Tuto možnost můžete použít k vytvoření souboru nastavení publikování a importování do sady Visual Studio.

> [!NOTE]
> Tato metoda nasazení používá Nasazení webu, který musí být nainstalován na serveru. Pokud chcete Nasazení webu nakonfigurovat ručně místo importu nastavení, můžete místo Nasazení webu 3,6 pro hostitelské servery nainstalovat Nasazení webu 3,6. Pokud však Nasazení webu nakonfigurujete ručně, budete se muset ujistit, že je složka aplikace na serveru nakonfigurovaná se správnými hodnotami a oprávněními (viz část [Konfigurace webu ASP.NET](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Nakonfigurovat ASP.NET Core Web

1. Ve Správci služby IIS klikněte v levém podokně v části **připojení**na položku **fondy aplikací**. Otevřete **DefaultAppPool** a nastavte **verzi .NET CLR** na **žádný spravovaný kód**. To je nutné pro ASP.NET Core. Výchozí web používá rozhraní DefaultAppPool.

2. Zastavte a restartujte službu DefaultAppPool.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalace a konfigurace Nasazení webu pro hostitelské servery na Windows serveru

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvoření souboru s nastavením publikování ve službě IIS na Windows serveru

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v aplikaci Visual Studio a nasazení

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Pokud restartujete virtuální počítač Azure, IP adresa se může změnit.

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud se aplikace nespustí ze sady Visual Studio, spusťte aplikaci ve službě IIS, abyste ověřili, že funguje správně. V případě ASP.NET Core musíte také zajistit, aby pole fond aplikací pro **DefaultAppPool** bylo nastaveno na **žádný spravovaný kód**.

1. V dialogovém okně **Nastavení** Povolte ladění kliknutím na tlačítko **Další**, zvolte konfiguraci **ladění** a pak zvolte **odebrat další soubory v cílovém umístění** v možnostech **publikování souboru** .

    > [!IMPORTANT]
    > Pokud zvolíte konfiguraci vydané verze, zakážete ladění v souboru *web.config* při publikování.

1. Klikněte na **Uložit** a znovu publikujte aplikaci.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Volitelné Nasazení publikováním do místní složky

Tuto možnost můžete použít k nasazení aplikace, pokud chcete zkopírovat aplikaci do služby IIS pomocí PowerShellu, nástroje Robocopy nebo chcete soubory ručně zkopírovat.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Konfigurace ASP.NET Core webu na počítači se systémem Windows Server

Pokud importujete nastavení publikování, můžete tuto část přeskočit.

1. Otevřete **správce Internetová informační služba (IIS)** a pokračujte na **lokality**.

2. Klikněte pravým tlačítkem myši na uzel **výchozí web** a vyberte **Přidat aplikaci**.

3. Nastavte pole **alias** na **MyASPApp** a pole fond aplikací **bez spravovaného kódu**. Nastavte **fyzickou cestu** na **C:\Publish** (kde budete později nasazovat projekt ASP.NET Core).

4. V lokalitě vybrané ve Správci služby IIS vyberte možnost **Upravit oprávnění**a ujistěte se, že je IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro fond aplikací autorizovaný uživatel s oprávněním ke čtení &.

    Pokud nevidíte některého z těchto uživatelů s přístupem, Projděte kroky pro přidání IUSR jako uživatele s právy ke čtení &.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Volitelné Publikování a nasazení aplikace publikováním do místní složky ze sady Visual Studio

Pokud Nasazení webu nepoužíváte, musíte aplikaci publikovat a nasadit pomocí systému souborů nebo jiných nástrojů. Můžete začít vytvořením balíčku pomocí systému souborů a potom buď ručně nasadit balíček, nebo použít jiné nástroje, jako je PowerShell, Robocopy nebo XCopy. V této části předpokládáme, že balíček kopírujete ručně, pokud nepoužíváte Nasazení webu.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Stažení a instalace nástrojů Remote Tools na Windows serveru

Stáhněte si verzi nástrojů Remote Tools, které odpovídají vaší verzi sady Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Nastavení vzdáleného ladicího programu na Windows serveru

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změňte režim ověřování nebo číslo portu vzdáleného ladicího programu. Další informace najdete v tématu [Konfigurace vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Připojení k aplikaci ASP.NET z počítače s Visual Studiem

1. V počítači se systémem Visual Studio otevřete řešení, které se pokoušíte ladit (**MyASPApp** , pokud budete postupovat podle kroků uvedených v tomto článku).
2. V aplikaci Visual Studio klikněte na možnost **ladit > připojit k procesu** (CTRL + ALT + P).

    > [!TIP]
    > V aplikaci Visual Studio 2017 a novějších verzích se můžete znovu připojit ke stejnému procesu, ke kterému jste dříve připojeni pomocí příkazu **Debug > znovu připojit k procesu...** (Shift + Alt + P).

3. Nastavte pole Kvalifikátor na **\<remote computer name>** a stiskněte klávesu **ENTER**.

    Ověřte, že Visual Studio přidá požadovaný port do názvu počítače, který se zobrazí ve formátu: ** \<remote computer name> :p** .

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 byste měli vidět ** \<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 byste měli vidět ** \<remote computer name> : 4022**
    ::: moniker-end
    Port je povinný. Pokud se číslo portu nezobrazuje, přidejte ho ručně.

4. Klikněte na **Aktualizovat**.
    V okně **Dostupné procesy** by se měly zobrazit některé procesy.

    Pokud nevidíte žádné procesy, zkuste místo názvu vzdáleného počítače použít IP adresu (vyžaduje se port). `ipconfig`Adresu IPv4 můžete získat pomocí příkazu v příkazovém řádku.

    Chcete-li použít tlačítko **Najít** , bude pravděpodobně nutné na serveru [otevřít port UDP 3702](#bkmk_openports) .

5. Zaškrtávací políčka  **Zobrazit procesy všech uživatelů**.

6. Zadejte první písmeno názvu procesu pro rychlé vyhledání vaší aplikace.

    * Pokud používáte [model hostování v rámci procesu](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) služby IIS, vyberte správný proces **w3wp.exe** . Počínaje platformou .NET Core 3 se jedná o výchozí nastavení.

    * V opačném případě vyberte proces **dotnet.exe** . (Toto je model hostování mimo proces.)

    Pokud máte více procesů zobrazujících *w3wp.exe* nebo *dotnet.exe*, podívejte se do sloupce **uživatelské jméno** . V některých scénářích se ve sloupci **uživatelské jméno** zobrazí název vašeho fondu aplikací, například **Služba IIS APPPOOL\DefaultAppPool**. Pokud se zobrazí fond aplikací, ale není jedinečný, vytvořte nový pojmenovaný fond aplikací pro instanci aplikace, kterou chcete ladit, a pak ji můžete snadno najít ve sloupci **uživatelské jméno** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klikněte na **připojit**.

8. Otevřete web vzdáleného počítače. V prohlížeči, navštivte **http:// \<remote computer name> **.

    Měla by se zobrazit webová stránka ASP.NET.
9. Ve spuštěné aplikaci ASP.NET klikněte na odkaz na stránku **o** aplikaci.

    Zarážka by měla být dosaženo v aplikaci Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Řešení potíží: otevření požadovaných portů na Windows serveru

Ve většině nastavení jsou požadované porty otevřené instalací ASP.NET a vzdáleného ladicího programu. Pokud však řešíte problémy s nasazením a aplikace je hostována za bránou firewall, možná budete muset ověřit, že jsou otevřené správné porty.

Na virtuálním počítači Azure musíte otevřít porty přes [skupinu zabezpečení sítě](/azure/virtual-machines/windows/nsg-quickstart-portal).

Požadované porty:

* 80 – vyžadováno pro službu IIS
::: moniker range=">=vs-2019"
* 4024 – vyžadováno pro vzdálené ladění ze sady Visual Studio 2019 (Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022 – vyžadováno pro vzdálené ladění ze sady Visual Studio 2017 (Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* Při připojování ke vzdálenému ladicímu programu v aplikaci Visual Studio vám port pro zjišťování s protokolem UDP 3702 – (nepovinný) vám umožní tlačítko **Najít** .

Kromě toho by se už tyto porty měly otevřít pomocí instalace ASP.NET:
- 8172 – vyžaduje se Nasazení webu nasazení aplikace ze sady Visual Studio (volitelné)
