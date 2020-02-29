---
title: Vzdálené ladění ASP.NET Core na vzdáleném počítači IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f3741f9b510450dabfea5c1df4eec4b2e0868b26
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181155"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Vzdálené ladění ASP.NET Core na vzdáleném počítači IIS v aplikaci Visual Studio

Chcete-li ladit aplikaci ASP.NET Core nasazenou do služby IIS, nainstalujte a spusťte nástroje Remote Tools v počítači, kde jste nasadili aplikaci, a pak se připojte k spuštěné aplikaci ze sady Visual Studio.

![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Tato příručka vysvětluje, jak nastavit a nakonfigurovat sadu Visual Studio ASP.NET Core, jak ji nasadit do služby IIS a jak připojit vzdálený ladicí program ze sady Visual Studio. Vzdálené ladění ASP.NET 4.5.2 najdete v tématu [vzdálené ladění ASP.NET na počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Službu IIS můžete také nasadit a ladit pomocí Azure. Pro Azure App Service můžete snadno nasadit a ladit v předkonfigurovaných instancích služby IIS a vzdáleném ladícím programu pomocí [Snapshot Debugger](../debugger/debug-live-azure-applications.md) nebo [připojením ladicího programu z Průzkumník serveru](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Předpoklady

::: moniker range=">=vs-2019"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
K provedení kroků uvedených v tomto článku se vyžaduje Visual Studio 2017.
::: moniker-end

Tyto postupy jsme otestovali na tyto konfigurace serveru:
* Windows Server 2012 R2 a IIS 8
* Windows Server 2016 a IIS 10

## <a name="network-requirements"></a>Síťové požadavky

Ladění mezi dvěma počítači připojený prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latencí nebo připojení s malou šířkou pásma, jako je například telefonického Internetu, nebo přes Internet napříč zeměmi se nedoporučuje a může selhat nebo být příliš pomalé. Úplný seznam požadavků najdete v tématu [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplikace už běží ve službě IIS?

Tento článek obsahuje kroky k nastavení základní konfiguraci služby IIS na Windows serveru a nasazení aplikace v sadě Visual Studio. Tyto kroky jsou zahrnuty, abyste měli jistotu, že server vyžaduje, že aplikace může běžet správně a že budete chtít vzdáleného ladění nainstalovány součásti.

* Pokud je vaše aplikace spuštěná ve službě IIS a vy chcete stáhnout vzdálený ladicí program a spustit ladění, použijte ke [Stažení a instalaci nástrojů Remote Tools na Windows Server](#BKMK_msvsmon).

* Pokud potřebujete pomoc, abyste měli jistotu, že vaše aplikace je nastavené, nasazení a fungování ve službě IIS, takže můžete ladit, postupujte podle všech kroků v tomto tématu.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Vytvoření aplikace ASP.NET Core v počítači se systémem Visual Studio

1. Vytvořte novou ASP.NET Core webovou aplikaci. 

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 zadejte **CTRL + Q** pro otevření vyhledávacího pole, zadejte **ASP.NET**, zvolte **šablony**a pak zvolte **vytvořit novou ASP.NET Core webovou aplikaci**. V dialogovém okně, které se zobrazí, pojmenujte projekt **MyASPApp**a pak zvolte **vytvořit**. Dále zvolte možnost **Webová aplikace (model-zobrazení-kontroler)** a pak zvolte možnost **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 zvolte možnost **soubor > nový > projekt**a pak vyberte možnost **Visual C# > Web > ASP.NET Core webová aplikace**. V části šablony ASP.NET Core vyberte možnost **Webová aplikace (model-zobrazení-kontroler)** . Ujistěte se, že je vybrána možnost ASP.NET Core 2,1, možnost **Povolit podporu Docker** není vybrána a toto **ověřování** je nastaveno na **bez ověřování**. Pojmenujte projekt **MyASPApp**.
    ::: moniker-end

4. Otevřete soubor About.cshtml.cs a nastavte zarážku v metodě `OnGet` (ve starších šablonách otevřete HomeController.cs místo toho a nastavte zarážku v metodě `About()`).

## <a name="bkmk_configureIIS"></a>Instalace a konfigurace služby IIS na Windows serveru

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizovat nastavení zabezpečení prohlížeče ve Windows serveru

Pokud je povolená konfigurace rozšířeného zabezpečení aplikace Internet Explorer (je povolená ve výchozím nastavení), budete muset přidat některé domény jako důvěryhodné servery, které chcete stáhnout, některé součásti webového serveru. Přidejte důvěryhodné servery tak, že v části **Možnosti internetu > zabezpečení > důvěryhodné servery > lokality**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Když si stáhnete software, se může zobrazit žádosti o udělení oprávnění k načítání různých skriptů na webu a prostředky. Některé z těchto prostředků se nevyžadují, ale pro zjednodušení procesu klikněte po zobrazení výzvy na **Přidat** .

## <a name="install-aspnet-core-on-windows-server"></a>Instalace ASP.NET Core v systému Windows Server

1. Nainstalujte [hostující sadu Windows serveru .NET Core](https://aka.ms/dotnetcore-2-windowshosting) do hostitelského systému. Svazek nainstaluje modul runtime .NET Core, knihovnu .NET Core a modul ASP.NET Core. Podrobné pokyny najdete v tématu [publikování do služby IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Pokud systém nemá připojení k Internetu, Stáhněte a nainstalujte *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* ještě před instalací hostující sady .NET Core Windows serveru.

3. Restartujte systém (nebo spusťte příkaz **net stop** , který následuje po příkazu **net start w3svc** z příkazového řádku pro výběr změny systémové cesty).

## <a name="choose-a-deployment-option"></a>Vyberte možnost nasazení

Pokud potřebujete nápovědu k nasazení aplikace do služby IIS, zvažte tyto možnosti:

* Nasazení vytvořením soubor nastavení publikování ve službě IIS a importu nastavení v sadě Visual Studio. V některých případech to je rychlý způsob nasazení vaší aplikace. Když vytvoříte soubor nastavení publikování, oprávnění se automaticky nastaví ve službě IIS.

* Nasazení publikování do místní složky a zkopírování výstupu upřednostňovanou metodou do složky připravené aplikace ve službě IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Volitelné) Nasazení pomocí souboru nastavení publikování

Tuto možnost můžete použít vytvořit soubor nastavení publikování a importujte ho do sady Visual Studio.

> [!NOTE]
> Tato metoda nasazení používá, nasazení webu. Pokud chcete nakonfigurovat nasazení webu ručně v sadě Visual Studio namísto importu nastavení, můžete nainstalovat webové nasazení 3.6 místo 3.6 webové nasazení pro servery hostující. Pokud však Nasazení webu nakonfigurujete ručně, budete se muset ujistit, že je složka aplikace na serveru nakonfigurovaná se správnými hodnotami a oprávněními (viz část [Konfigurace webu ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalace a konfigurace nasazení webu pro hostování servery v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvořit soubor nastavení publikování ve službě IIS v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v sadě Visual Studio a nasazení

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Jakmile se aplikace nasadí úspěšně, by se měl spustit automaticky. Pokud aplikace ze sady Visual Studio nespustí, spusťte aplikaci ve službě IIS. Pro ASP.NET Core se musíte ujistit, že je pole fond aplikací pro **DefaultAppPool** nastavené na **žádný spravovaný kód**.

1. V dialogovém okně **Nastavení** Povolte ladění kliknutím na tlačítko **Další**, zvolte konfiguraci **ladění** a pak zvolte **odebrat další soubory v cílovém umístění** v možnostech **publikování souboru** .

    > [!NOTE]
    > Pokud zvolíte konfiguraci vydané verze, zakážete ladění v souboru *Web. config* při publikování.

1. Klikněte na **Uložit** a znovu publikujte aplikaci.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Volitelné) Nasazení na základě publikování do místní složky

Tuto možnost můžete použít k nasazení aplikace, pokud chcete zkopírovat aplikaci do služby IIS pomocí PowerShellu, nástroje Robocopy nebo chcete soubory ručně zkopírovat.

### <a name="BKMK_deploy_asp_net"></a>Konfigurace ASP.NET Core webu na počítači se systémem Windows Server

1. Otevřete Průzkumníka Windows a vytvořte novou složku **C:\Publish**, kde budete později nasazovat projekt ASP.NET Core.

2. Pokud ještě není otevřený, otevřete **správce Internetová informační služba (IIS)** . (V levém podokně Správce serveru vyberte **IIS**. Klikněte pravým tlačítkem na server a vyberte **Internetová informační služba (Správce služby IIS)** .)

3. V části **připojení** v levém podokně přejdete na **lokality**.

4. Vyberte **výchozí web**, zvolte **základní nastavení**a nastavte **fyzickou cestu** na **C:\Publish**.

4. Klikněte pravým tlačítkem myši na uzel **výchozí web** a vyberte **Přidat aplikaci**.

5. Nastavte pole **alias** na **MyASPApp**, přijměte výchozí fond aplikací (**DefaultAppPool**) a nastavte **fyzickou cestu** na **C:\Publish**.

6. V části **připojení**vyberte **fondy aplikací**. Otevřete **DefaultAppPool** a nastavte pole fond aplikací na **žádný spravovaný kód**.

7. Pravým tlačítkem myši klikněte na novou lokalitu ve Správci služby IIS, vyberte možnost **Upravit oprávnění**a ujistěte se, že je IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro přístup k webové aplikaci autorizovaný uživatel s oprávněním ke čtení & ke spuštění.

    Pokud nevidíte některého z těchto uživatelů s přístupem, Projděte kroky pro přidání IUSR jako uživatele s právy ke čtení &.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikujte a nasaďte aplikaci publikováním do místní složky ze sady Visual Studio

Můžete také publikovat a nasazení aplikace pomocí systému souborů nebo jiných nástrojů.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Stažení a instalace nástrojů Remote Tools na Windows serveru

Stáhněte si verzi nástrojů Remote Tools, které odpovídají vaší verzi sady Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a>Nastavení vzdáleného ladicího programu na Windows serveru

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změňte režim ověřování nebo číslo portu vzdáleného ladicího programu. Další informace najdete v tématu [Konfigurace vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

Informace o spuštění vzdáleného ladícího programu jako služby najdete v tématu [spuštění vzdáleného ladícího programu jako služby](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a>Připojení k aplikaci ASP.NET z počítače s Visual Studiem

1. V počítači se systémem Visual Studio otevřete řešení, které se pokoušíte ladit (**MyASPApp** , pokud budete postupovat podle všech kroků v tomto článku).
2. V aplikaci Visual Studio klikněte na možnost **ladit > připojit k procesu** (CTRL + ALT + P).

    > [!TIP]
    > V aplikaci Visual Studio 2017 a novějších verzích se můžete znovu připojit ke stejnému procesu, ke kterému jste dříve připojeni pomocí příkazu **Debug > znovu připojit k procesu...** (Shift + Alt + P).

3. Nastavte pole Kvalifikátor na **\<název vzdáleného počítače >** a stiskněte klávesu **ENTER**.

    Ověřte, že Visual Studio přidá požadovaný port do názvu počítače, který se zobrazí ve formátu: **\<název vzdáleného počítače >:p** .

    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 byste měli vidět **\<název vzdáleného počítače >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 byste měli vidět **\<název vzdáleného počítače >: 4022**
    ::: moniker-end
    Port je povinný. Pokud se číslo portu nezobrazuje, přidejte ho ručně.

4. Klikněte na **Aktualizovat**.
    V okně **Dostupné procesy** by se měly zobrazit některé procesy.

    Pokud se nezobrazí všechny procesy, použijte adresu IP místo názvu vzdáleného počítače (port, který se vyžaduje). Adresu IPv4 můžete získat pomocí `ipconfig` na příkazovém řádku.

    Chcete-li použít tlačítko **Najít** , bude pravděpodobně nutné na serveru [otevřít port UDP 3702](#bkmk_openports) .

5. Zaškrtávací políčka **Zobrazit procesy všech uživatelů**.

6. Zadejte první písmeno názvu procesu pro rychlé vyhledání vaší aplikace.

    * Vyberte **dotnet. exe**.

      Pokud máte více procesů, které zobrazují **dotnet. exe**, podívejte se do sloupce **uživatelské jméno** . V některých scénářích se ve sloupci **uživatelské jméno** zobrazí název vašeho fondu aplikací, například **Služba IIS APPPOOL\DefaultAppPool**. Pokud se zobrazí fond aplikací, snadný způsob, jak identifikovat správný proces, je vytvořit nový pojmenovaný fond aplikací pro instanci aplikace, kterou chcete ladit, a pak ji můžete snadno najít ve sloupci **uživatelské jméno** .

    * V některých scénářích služby IIS můžete v seznamu procesů najít název vaší aplikace, například **MyASPApp. exe**. Místo toho se můžete připojit k tomuto procesu.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klikněte na **připojit**.

8. Otevřete web, vzdáleném počítači. V prohlížeči klikněte na **http://\<název vzdáleného počítače >** .

    Zobrazí se webová stránka ASP.NET.

9. Ve spuštěné aplikaci ASP.NET klikněte na odkaz na stránku **o** aplikaci.

    Zarážka by měla být dosažena v sadě Visual Studio.

## <a name="bkmk_openports"></a>Řešení potíží: otevření požadovaných portů na Windows serveru

Ve většině nastavení jsou otevřené požadované porty instalace technologie ASP.NET a vzdálený ladicí program. Ale budete muset ověřit, že jsou otevřené porty.

> [!NOTE]
> Na virtuálním počítači Azure musíte otevřít porty přes [skupinu zabezpečení sítě](/azure/virtual-machines/windows/nsg-quickstart-portal).

Požadované porty:

* 80 – požadováno pro službu IIS
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

3. Vytvořte další pravidla pro požadované porty.
