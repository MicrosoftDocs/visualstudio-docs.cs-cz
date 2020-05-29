---
title: Vzdálené ladění ASP.NET Core na vzdáleném počítači IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 4d2f2e2a698063dfb5ac6261d8a9b01a073d112e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173870"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Vzdálené ladění ASP.NET Core na vzdáleném počítači IIS v aplikaci Visual Studio

Chcete-li ladit aplikaci ASP.NET Core nasazenou do služby IIS, nainstalujte a spusťte nástroje Remote Tools v počítači, kde jste nasadili aplikaci, a pak se připojte k spuštěné aplikaci ze sady Visual Studio.

![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Tato příručka vysvětluje, jak nastavit a nakonfigurovat sadu Visual Studio ASP.NET Core, jak ji nasadit do služby IIS a jak připojit vzdálený ladicí program ze sady Visual Studio. Vzdálené ladění ASP.NET 4.5.2 najdete v tématu [vzdálené ladění ASP.NET na počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Službu IIS můžete také nasadit a ladit pomocí Azure. Pro Azure App Service můžete snadno nasadit a ladit v předkonfigurovaných instancích služby IIS a vzdáleném ladícím programu pomocí [Snapshot Debugger](../debugger/debug-live-azure-applications.md) nebo [připojením ladicího programu z Průzkumník serveru](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2017.
::: moniker-end

Tyto postupy byly testovány na těchto konfiguracích serveru:
* Windows Server 2012 R2 a IIS 8
* Windows Server 2016 a IIS 10
* Windows Server 2019 a IIS 10

## <a name="network-requirements"></a>Požadavky sítě

Ladění mezi dvěma počítači připojenými prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latenci nebo připojení s nízkou šířkou pásma, jako je například telefonické připojení k Internetu nebo přes Internet v zemích, se nedoporučuje a může být neúspěšné nebo nepřijatelně pomalé. Úplný seznam požadavků najdete v tématu [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Už je aplikace spuštěná ve službě IIS?

Tento článek obsahuje kroky pro nastavení základní konfigurace služby IIS na Windows serveru a nasazení aplikace ze sady Visual Studio. Tyto kroky jsou zahrnuty, abyste se ujistili, že server má nainstalované požadované součásti, že aplikace funguje správně a že jste připraveni ke vzdálenému ladění.

* Pokud je vaše aplikace spuštěná ve službě IIS a vy chcete stáhnout vzdálený ladicí program a spustit ladění, použijte ke [Stažení a instalaci nástrojů Remote Tools na Windows Server](#BKMK_msvsmon).

* Pokud chcete zajistit, aby se vaše aplikace nastavila, nasadila a běžela správně ve službě IIS, abyste mohli ladit, postupujte podle všech kroků v tomto tématu.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Vytvoření aplikace ASP.NET Core v počítači se systémem Visual Studio

1. Vytvořte novou ASP.NET Core webovou aplikaci. 

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 zadejte **CTRL + Q** pro otevření vyhledávacího pole, zadejte **ASP.NET**, zvolte **šablony**a pak zvolte **vytvořit novou ASP.NET Core webovou aplikaci**. V dialogovém okně, které se zobrazí, pojmenujte projekt **MyASPApp**a pak zvolte **vytvořit**. Dále zvolte možnost **Webová aplikace (model-zobrazení-kontroler)** a pak zvolte možnost **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 zvolte **soubor > nový > projekt**, a pak vyberte **Visual C# > webová aplikace Web > ASP.NET Core**. V části šablony ASP.NET Core vyberte možnost **Webová aplikace (model-zobrazení-kontroler)**. Ujistěte se, že je vybrána možnost ASP.NET Core 2,1, možnost **Povolit podporu Docker** není vybrána a toto **ověřování** je nastaveno na **bez ověřování**. Pojmenujte projekt **MyASPApp**.
    ::: moniker-end

4. Otevřete soubor About.cshtml.cs a nastavte zarážku v `OnGet` metodě (ve starších šablonách otevřete HomeController.cs místo toho a nastavte zarážku v `About()` metodě).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Instalace a konfigurace služby IIS na Windows serveru

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizace nastavení zabezpečení prohlížeče na Windows serveru

Pokud je v Internet Exploreru povolená konfigurace rozšířeného zabezpečení (ve výchozím nastavení je povolená), možná budete muset přidat některé domény jako důvěryhodné servery, abyste si mohli stáhnout některé součásti webového serveru. Přidejte důvěryhodné servery tak, že v části **Možnosti internetu > zabezpečení > důvěryhodné servery > lokality**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Po stažení softwaru můžete získat žádosti o udělení oprávnění k načtení různých skriptů a prostředků webu. Některé z těchto prostředků se nevyžadují, ale pro zjednodušení procesu klikněte po zobrazení výzvy na **Přidat** .

## <a name="install-aspnet-core-on-windows-server"></a>Instalace ASP.NET Core v systému Windows Server

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

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud se aplikace nespustí ze sady Visual Studio, spusťte aplikaci ve službě IIS, abyste ověřili, že funguje správně. V případě ASP.NET Core musíte také zajistit, aby pole fond aplikací pro **DefaultAppPool** bylo nastaveno na **žádný spravovaný kód**.

1. V dialogovém okně **Nastavení** Povolte ladění kliknutím na tlačítko **Další**, zvolte konfiguraci **ladění** a pak zvolte **odebrat další soubory v cílovém umístění** v možnostech **publikování souboru** .

    > [!IMPORTANT]
    > Pokud zvolíte konfiguraci vydané verze, zakážete ladění v souboru *Web. config* při publikování.

1. Klikněte na **Uložit** a znovu publikujte aplikaci.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Volitelné Nasazení publikováním do místní složky

Tuto možnost můžete použít k nasazení aplikace, pokud chcete zkopírovat aplikaci do služby IIS pomocí PowerShellu, nástroje Robocopy nebo chcete soubory ručně zkopírovat.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurace ASP.NET Core webu na počítači se systémem Windows Server

1. Otevřete Průzkumníka Windows a vytvořte novou složku **C:\Publish**, kde budete později nasazovat projekt ASP.NET Core.

2. Pokud ještě není otevřený, otevřete **správce Internetová informační služba (IIS)**. (V levém podokně Správce serveru vyberte **IIS**. Klikněte pravým tlačítkem na server a vyberte **Internetová informační služba (Správce služby IIS)**.)

3. V části **připojení** v levém podokně přejdete na **lokality**.

4. Vyberte **výchozí web**, zvolte **základní nastavení**a nastavte **fyzickou cestu** na **C:\Publish**.

4. Klikněte pravým tlačítkem myši na uzel **výchozí web** a vyberte **Přidat aplikaci**.

5. Nastavte pole **alias** na **MyASPApp**, přijměte výchozí fond aplikací (**DefaultAppPool**) a nastavte **fyzickou cestu** na **C:\Publish**.

6. V části **připojení**vyberte **fondy aplikací**. Otevřete **DefaultAppPool** a nastavte pole fond aplikací na **žádný spravovaný kód**.

7. Pravým tlačítkem myši klikněte na novou lokalitu ve Správci služby IIS, vyberte možnost **Upravit oprávnění**a ujistěte se, že je IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro přístup k webové aplikaci autorizovaný uživatel s oprávněním ke čtení & ke spuštění.

    Pokud nevidíte některého z těchto uživatelů s přístupem, Projděte kroky pro přidání IUSR jako uživatele s právy ke čtení &.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikování a nasazení aplikace publikováním do místní složky ze sady Visual Studio

Aplikaci můžete publikovat a nasadit také pomocí systému souborů nebo jiných nástrojů.

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

1. V počítači se systémem Visual Studio otevřete řešení, které se pokoušíte ladit (**MyASPApp** , pokud budete postupovat podle všech kroků v tomto článku).
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

5. Zaškrtávací políčka **Zobrazit procesy všech uživatelů**.

6. Zadejte první písmeno názvu procesu pro rychlé vyhledání vaší aplikace.

    * Pokud používáte [model hostování v rámci procesu](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) služby IIS, vyberte správný proces **W3wp. exe** . Počínaje platformou .NET Core 3 se jedná o výchozí nastavení.

    * V opačném případě vyberte proces **dotnet. exe** . (Toto je model hostování mimo proces.)

    Pokud máte více procesů, které zobrazují *W3wp. exe* nebo *dotnet. exe*, podívejte se do sloupce **uživatelské jméno** . V některých scénářích se ve sloupci **uživatelské jméno** zobrazí název vašeho fondu aplikací, například **Služba IIS APPPOOL\DefaultAppPool**. Pokud se zobrazí fond aplikací, ale není jedinečný, vytvořte nový pojmenovaný fond aplikací pro instanci aplikace, kterou chcete ladit, a pak ji můžete snadno najít ve sloupci **uživatelské jméno** .

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

2. Pak zvolte **příchozí pravidla > nové pravidlo > port**a pak klikněte na **Další**. (Pro UDP 3702 místo toho vyberte **odchozí pravidla** .)

3. V části **konkrétní místní porty**zadejte číslo portu a klikněte na **Další**.

4. Klikněte na možnost **Povolení připojení**, klikněte na tlačítko **Další**.

5. Vyberte jeden nebo více typů sítí, které chcete pro port povolit, a klikněte na tlačítko **Další**.

    Typ, který vyberete, musí zahrnovat síť, ke které je připojený vzdálený počítač.
6. Pro příchozí pravidlo přidejte název (například **IIS**, **nasazení webu**nebo **msvsmon**) a klikněte na **Dokončit**.

    V seznamu příchozí pravidla nebo odchozí pravidla by se mělo zobrazit nové pravidlo.

    Pokud potřebujete další podrobnosti o konfiguraci brány Windows Firewall, přečtěte si téma [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Vytvořte další pravidla pro ostatní požadované porty.
