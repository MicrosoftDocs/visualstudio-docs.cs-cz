---
title: Vzdálené ladění ASP.NET na počítači se službou IIS
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: cd2b787fe546b9c53332fcdc548d3da829759755
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173912"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Vzdálené ladění ASP.NET na vzdáleném počítači IIS
Chcete-li ladit aplikaci ASP.NET, která byla nasazena do služby IIS, nainstalujte a spusťte nástroje Remote Tools v počítači, kde jste nasadili aplikaci, a pak se připojte k spuštěné aplikaci ze sady Visual Studio.

![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Tato příručka vysvětluje, jak nastavit a nakonfigurovat aplikaci Visual Studio ASP.NET MVC 4.5.2, jak ji nasadit do služby IIS a jak připojit vzdálený ladicí program ze sady Visual Studio.

> [!NOTE]
> Pro vzdálené ladění ASP.NET Core místo toho si přečtěte téma [vzdálené ladění ASP.NET Core na počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Pro Azure App Service můžete snadno nasadit a ladit v předkonfigurovaných instancích služby IIS pomocí [Snapshot Debugger](../debugger/debug-live-azure-applications.md) (vyžaduje se .NET 4.6.1) nebo [připojením ladicího programu z Průzkumník serveru](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2017.
::: moniker-end

Tyto postupy byly testovány na těchto konfiguracích serveru:
* Windows Server 2012 R2 a IIS 8 (pro Windows Server 2008 R2 se serverové kroky liší)

## <a name="network-requirements"></a>Požadavky sítě

Vzdálený ladicí program je podporován na Windows serveru počínaje verzí Windows Server 2008 Service Pack 2. Úplný seznam požadavků najdete v tématu [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Ladění mezi dvěma počítači připojenými prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latenci nebo připojení s nízkou šířkou pásma, jako je například telefonické připojení k Internetu nebo přes Internet v zemích, se nedoporučuje a může být neúspěšné nebo nepřijatelně pomalé.

## <a name="app-already-running-in-iis"></a>Už je aplikace spuštěná ve službě IIS?

Tento článek obsahuje kroky pro nastavení základní konfigurace služby IIS na Windows serveru a nasazení aplikace ze sady Visual Studio. Tyto kroky jsou zahrnuty, abyste se ujistili, že server má nainstalované požadované součásti, že aplikace funguje správně a že jste připraveni ke vzdálenému ladění.

* Pokud je vaše aplikace spuštěná ve službě IIS a vy chcete stáhnout vzdálený ladicí program a spustit ladění, použijte ke [Stažení a instalaci nástrojů Remote Tools na Windows Server](#BKMK_msvsmon).

* Pokud chcete zajistit, aby se vaše aplikace nastavila, nasadila a běžela správně ve službě IIS, abyste mohli ladit, postupujte podle všech kroků v tomto tématu.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Vytvoření aplikace ASP.NET 4.5.2 na počítači se systémem Visual Studio

1. Vytvořte novou aplikaci MVC ASP.NET.

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 zadejte **CTRL + Q** pro otevření vyhledávacího pole, zadejte **ASP.NET**, zvolte **šablony**a pak zvolte **vytvořit novou webovou aplikaci v ASP.NET (.NET Framework)**. V dialogovém okně, které se zobrazí, pojmenujte projekt **MyASPApp**a pak zvolte **vytvořit**. Vyberte **MVC** a zvolte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud to chcete provést v aplikaci Visual Studio 2017, zvolte **soubor > nový > projekt**a pak vyberte **Webová aplikace Visual C# > web > ASP.NET**. V části šablony **ASP.NET 4.5.2** vyberte **MVC**. Ujistěte se, že není vybraná **možnost povolit podporu Docker** a že **ověřování** je nastaveno na **bez ověřování**. Pojmenujte projekt **MyASPApp**.)
    ::: moniker-end

2. Otevřete soubor *HomeController.cs* a nastavte zarážku v `About()` metodě.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Instalace a konfigurace služby IIS na Windows serveru

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizace nastavení zabezpečení prohlížeče na Windows serveru

Pokud je v Internet Exploreru povolená konfigurace rozšířeného zabezpečení (ve výchozím nastavení je povolená), možná budete muset přidat některé domény jako důvěryhodné servery, abyste si mohli stáhnout některé součásti webového serveru. Přidejte důvěryhodné servery tak, že v části **Možnosti internetu > zabezpečení > důvěryhodné servery > lokality**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Po stažení softwaru můžete získat žádosti o udělení oprávnění k načtení různých skriptů a prostředků webu. Některé z těchto prostředků se nevyžadují, ale pro zjednodušení procesu klikněte po zobrazení výzvy na **Přidat** .

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a>Instalace ASP.NET 4,5 na Windows Server

Pokud potřebujete podrobnější informace k instalaci ASP.NET ve službě IIS, přečtěte si téma [IIS 8,0 Using ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. V levém podokně Správce serveru vyberte **IIS**. Klikněte pravým tlačítkem na server a vyberte **Správce služby Internetová informační služba (IIS)**.

1. Pomocí instalačního programu webové platformy (WebPI) nainstalujte ASP.NET 4,5 (z uzlu Server v systému Windows Server 2012 R2 zvolte možnost **získat nové součásti webové platformy** a pak vyhledejte ASP.NET).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Pokud používáte Windows Server 2008 R2, nainstalujte místo toho ASP.NET 4 pomocí tohoto příkazu:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ aspnet_regiis. exe – IR**

2. Restartujte systém (nebo spusťte příkaz **net stop** , který následuje po příkazu **net start w3svc** z příkazového řádku pro výběr změny systémové cesty).

## <a name="choose-a-deployment-option"></a>Zvolit možnost nasazení

Pokud potřebujete pomáhat s nasazením aplikace do služby IIS, zvažte tyto možnosti:

* Nasaďte je vytvořením souboru nastavení publikování ve službě IIS a importem nastavení v aplikaci Visual Studio. V některých scénářích je to rychlý způsob, jak aplikaci nasadit. Při vytváření souboru nastavení publikování se oprávnění automaticky nastaví ve službě IIS.

* Nasazení provedete publikováním do místní složky a zkopírováním výstupu upřednostňovanou metodou do připravené složky aplikace ve službě IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Volitelné Nasazení pomocí souboru nastavení publikování

Tuto možnost můžete použít k vytvoření souboru nastavení publikování a importování do sady Visual Studio.

> [!NOTE]
> Tato metoda nasazení používá Nasazení webu, který musí být nainstalován na serveru. Pokud chcete Nasazení webu nakonfigurovat ručně místo importu nastavení, můžete místo Nasazení webu 3,6 pro hostitelské servery nainstalovat Nasazení webu 3,6. Pokud však Nasazení webu nakonfigurujete ručně, budete se muset ujistit, že je složka aplikace na serveru nakonfigurovaná se správnými hodnotami a oprávněními (viz část [Konfigurace webu ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalace a konfigurace Nasazení webu pro hostitelské servery na Windows serveru

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvoření souboru s nastavením publikování ve službě IIS na Windows serveru

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v aplikaci Visual Studio a nasazení

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud se aplikace nespustí ze sady Visual Studio, spusťte aplikaci ve službě IIS.

1. V dialogovém okně **Nastavení** Povolte ladění kliknutím na tlačítko **Další**, zvolte konfiguraci **ladění** a pak zvolte **odebrat další soubory v cílovém umístění** v možnostech **publikování souboru** .

    > [!IMPORTANT]
    > Pokud zvolíte konfiguraci vydané verze, zakážete ladění v souboru *Web. config* při publikování.

1. Klikněte na **Uložit** a znovu publikujte aplikaci.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Volitelné Nasazení publikováním do místní složky

Tuto možnost můžete použít k nasazení aplikace, pokud chcete zkopírovat aplikaci do služby IIS pomocí PowerShellu, nástroje Robocopy nebo chcete soubory ručně zkopírovat.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurace webu ASP.NET na počítači se systémem Windows Server

1. Otevřete Průzkumníka Windows a vytvořte novou složku **C:\Publish**, kde budete později nasazovat projekt ASP.NET.

2. Pokud ještě není otevřený, otevřete **správce Internetová informační služba (IIS)**. (V levém podokně Správce serveru vyberte **IIS**. Klikněte pravým tlačítkem na server a vyberte **Internetová informační služba (Správce služby IIS)**.)

3. V části **připojení** v levém podokně přejdete na **lokality**.

4. Vyberte **výchozí web**, zvolte **základní nastavení**a nastavte **fyzickou cestu** na **C:\Publish**.

5. Klikněte pravým tlačítkem myši na uzel **výchozí web** a vyberte **Přidat aplikaci**.

6. Nastavte pole **alias** na **MyASPApp**, přijměte výchozí fond aplikací (**DefaultAppPool**) a nastavte **fyzickou cestu** na **C:\Publish**.

7. V části **připojení**vyberte **fondy aplikací**. Otevřete **DefaultAppPool** a nastavte pole fond aplikací na **ASP.NET v 4.0** (ASP.NET 4,5 není možností pro fond aplikací).

8. V lokalitě vybrané ve Správci služby IIS vyberte možnost **Upravit oprávnění**a ujistěte se, že je IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro fond aplikací autorizovaný uživatel s oprávněním ke čtení &. Pokud žádné z těchto uživatelů nejsou k dispozici, přidejte účty IUSR jako uživatele s právy pro čtení & oprávnění k provádění.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikování a nasazení aplikace publikováním do místní složky ze sady Visual Studio

Aplikaci můžete publikovat a nasadit také pomocí systému souborů nebo jiných nástrojů.

1. (ASP.NET 4.5.2) Ujistěte se, že v souboru Web. config je uvedena správná verze rozhraní .NET.  Pokud například cílíte na ASP.NET 4.5.2, ujistěte se, že je tato verze uvedená v souboru Web. config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Verze by měla být například 4,0, pokud instalujete ASP.NET 4 místo 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Stažení a instalace nástrojů Remote Tools na Windows serveru

Stáhněte si verzi nástrojů Remote Tools, které odpovídají vaší verzi sady Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Nastavení vzdáleného ladicího programu na Windows serveru

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změňte režim ověřování nebo číslo portu vzdáleného ladicího programu. Další informace najdete v tématu [Konfigurace vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

Informace o spuštění vzdáleného ladícího programu jako služby najdete v tématu [spuštění vzdáleného ladícího programu jako služby](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Připojení k aplikaci ASP.NET z počítače s Visual Studiem

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

5. Zaškrtávací políčka **Zobrazit procesy všech uživatelů**.

6. Zadejte první písmeno názvu procesu pro rychlé vyhledání **W3wp. exe** pro ASP.NET 4,5.

    Pokud máte více procesů, které zobrazují **W3wp. exe**, podívejte se do sloupce **uživatelské jméno** . V některých scénářích se ve sloupci **uživatelské jméno** zobrazí název vašeho fondu aplikací, například **Služba IIS APPPOOL\DefaultAppPool**. Pokud se zobrazí fond aplikací, snadný způsob, jak identifikovat správný proces, je vytvořit nový pojmenovaný fond aplikací pro instanci aplikace, kterou chcete ladit, a pak ji můžete snadno najít ve sloupci **uživatelské jméno** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klikněte na **připojit** .

8. Otevřete web vzdáleného počítače. V prohlížeči, navštivte **http:// \<remote computer name> **.

    Měla by se zobrazit webová stránka ASP.NET.
9. Ve spuštěné aplikaci ASP.NET klikněte na odkaz na stránku **o** aplikaci.

    Zarážka by měla být dosaženo v aplikaci Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Řešení potíží: otevření požadovaných portů na Windows serveru

Ve většině nastavení jsou požadované porty otevřené instalací ASP.NET a vzdáleného ladicího programu. Je ale možné, že budete muset ověřit, že jsou porty otevřené.

> [!NOTE]
> Na virtuálním počítači Azure musíte otevřít porty přes [skupinu zabezpečení sítě](/azure/virtual-machines/windows/nsg-quickstart-portal).

Požadované porty:

* 80 – vyžadováno pro službu IIS
::: moniker range=">=vs-2019"
* 4024 – vyžadováno pro vzdálené ladění ze sady Visual Studio 2019 (Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022 – vyžadováno pro vzdálené ladění ze sady Visual Studio 2017 (Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* Při připojování ke vzdálenému ladicímu programu v aplikaci Visual Studio vám port pro zjišťování s protokolem UDP 3702 – (nepovinný) vám umožní tlačítko **Najít** .

1. Chcete-li otevřít port na Windows serveru, otevřete nabídku **Start** a vyhledejte **bránu Windows Firewall s pokročilým zabezpečením**.

2. Pak zvolte **příchozí pravidla > nového pravidla > portu**. Zvolte **Další** a v **části konkrétní místní porty**zadejte číslo portu, klikněte na **Další**, pak na **Povolit připojení**, klikněte na další a pro příchozí pravidlo přidejte název (**IIS**, **nasazení webu**nebo **msvsmon**).

    Pokud potřebujete další podrobnosti o konfiguraci brány Windows Firewall, přečtěte si téma [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Vytvořte další pravidla pro ostatní požadované porty.