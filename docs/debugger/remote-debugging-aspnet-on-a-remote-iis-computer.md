---
title: Vzdálené ladění ASP.NET Core na počítači vzdálené služby IIS | Dokumentace Microsoftu
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: bcb0db3a6eab91c517ce731ddf6e201d5a73f1f8
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101066"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Vzdálené ladění ASP.NET Core na počítači vzdálené služby IIS v sadě Visual Studio 2017
Chcete-li ladit aplikaci ASP.NET, která byla nasazena do služby IIS, nainstalovat a spustit nástroje remote tools v počítači, kam jste nasadili aplikaci a potom připojit k vaší běžící aplikaci v sadě Visual Studio.

![Vzdálený ladicí program komponenty](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Tato příručka vysvětluje, jak nastavit a konfigurovat Visual Studio 2017 ASP.NET Core, nasaďte ji do služby IIS a připojení vzdáleného ladicího programu ze sady Visual Studio. Vzdálené ladění ASP.NET 4.5.2, najdete v článku [vzdálené ladění ASP.NET na počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Můžete také nasadit a ladit ve službě IIS pomocí Azure. Pro službu Azure App Service můžete snadno nasadit a ladění na předem nakonfigurované instance služby IIS a vzdálený ladicí program pomocí [Snapshot Debugger](../debugger/debug-live-azure-applications.md) nebo [připojování ladicího programu z Průzkumníka serveru](../debugger/remote-debugging-azure.md).

Tyto postupy jsme otestovali na tyto konfigurace serveru:
* Windows Server 2012 R2 a služby IIS 8
* Windows Server 2016 a IIS 10

## <a name="requirements"></a>Požadavky

Ladění mezi dvěma počítači připojený prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latencí nebo připojení s malou šířkou pásma, jako je například telefonického Internetu, nebo přes Internet napříč zeměmi se nedoporučuje a může selhat nebo být příliš pomalé. Úplný seznam požadavků, najdete v části [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplikace už běží ve službě IIS?

Tento článek obsahuje kroky k nastavení základní konfiguraci služby IIS na Windows serveru a nasazení aplikace v sadě Visual Studio. Tyto kroky jsou zahrnuty, abyste měli jistotu, že server vyžaduje, že aplikace může běžet správně a že budete chtít vzdáleného ladění nainstalovány součásti.

* Pokud vaše aplikace běží ve službě IIS a chcete jenom chcete stáhnout vzdálený ladicí program a spusťte ladění, přejděte na [stáhněte a nainstalujte nástroje remote tools v systému Windows Server](#BKMK_msvsmon).

* Pokud potřebujete pomoc, abyste měli jistotu, že vaše aplikace je nastavené, nasazení a fungování ve službě IIS, takže můžete ladit, postupujte podle všech kroků v tomto tématu.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Vytvoření aplikace ASP.NET Core v systému Visual Studio 2017 

1. Vytvoření nové aplikace ASP.NET Core. (**Soubor > Nový > projekt**a pak vyberte **Visual C# > Web > Webová aplikace ASP.NET Core**).

    V **ASP.NET Core** části šablony vyberte **webovou aplikaci**.

2. Ujistěte se, že **ASP.NET Core 2.0** je vybrána, který **povolit podporu Dockeru** je **není** vybrané a že **ověřování** je nastavena na **Bez ověřování**.

3. Pojmenujte projekt **MyASPApp** a klikněte na tlačítko **OK** k vytvoření nového řešení.

4. Otevřete soubor About.cshtml.cs a nastavte zarážku v `OnGet` – metoda (ve starších šablonách HomeController.cs místo toho otevřít a nastavit zarážku v `About()` metoda).

## <a name="bkmk_configureIIS"></a> Instalace a konfigurace služby IIS v systému Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizovat nastavení zabezpečení prohlížeče ve Windows serveru

Pokud je povolená konfigurace rozšířeného zabezpečení aplikace Internet Explorer (je povolená ve výchozím nastavení), budete muset přidat některé domény jako důvěryhodné servery, které chcete stáhnout, některé součásti webového serveru. Přidat důvěryhodné servery tak, že přejdete do **Možnosti Internetu > zabezpečení > důvěryhodných serverů > servery**. Přidejte následující domény.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Když si stáhnete software, se může zobrazit žádosti o udělení oprávnění k načítání různých skriptů na webu a prostředky. Některé z těchto zdrojů nejsou vyžadovány, ale pro zjednodušení procesu, klikněte na tlačítko **přidat** po zobrazení výzvy.

## <a name="install-aspnet-core-on-windows-server"></a>Nainstalujte aplikaci ASP.NET Core v systému Windows Server

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

1. Otevřete Průzkumníka Windows a vytvořte novou složku **C:\Publish**, kde bude později nasadit projekt ASP.NET.

2. Pokud ho ještě není otevřený, otevřete **Správce Internetové informační služby (IIS)**. (V levém podokně ve Správci serveru vyberte **IIS**. Klikněte pravým tlačítkem na server a vyberte **Správce Internetové informační služby (IIS)**.)

3. V části **připojení** v levém podokně přejděte do **lokality**.

4. Vyberte **výchozí webový server**, zvolte **základní nastavení**a nastavte **fyzická cesta** k **C:\Publish**.

4. Klikněte pravým tlačítkem myši **výchozí webový server** uzel a vyberte možnost **přidat aplikaci**.

5. Nastavte **Alias** pole **MyASPApp**, přijměte výchozí nastavení fondu aplikací (**DefaultAppPool**) a nastavte **fyzická cesta** k  **C:\Publish**.

6. V části **připojení**vyberte **fondy aplikací**. Otevřít **DefaultAppPool** a nastavte pole fond aplikací na **bez spravovaného kódu**.

7. Klikněte pravým tlačítkem na nový web ve Správci služby IIS, zvolte **upravit oprávnění**a ujistěte se, že IUSR, IIS_IUSRS nebo uživatel nakonfigurovaný pro přístup do webové aplikace je oprávněný uživatel s oprávněními Číst a spouštět.

    Pokud nevidíte jeden z těchto uživatelů s přístupem, projděte si kroky pro přidání IUSR jako uživatel s oprávněním Číst a spouštět.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikujte a nasaďte aplikaci publikováním do místní složky ze sady Visual Studio

Můžete také publikovat a nasazení aplikace pomocí systému souborů nebo jiných nástrojů.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Stáhněte a nainstalujte nástroje remote tools v systému Windows Server

V tomto kurzu se používá Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a> Nastavení vzdáleného ladicího programu v systému Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změnit režim ověřování, nebo číslo portu pro vzdálené ladění, naleznete v tématu [konfigurovat vzdálený ladicí program](../debugger/remote-debugging.md#configure_msvsmon).

Informace o spouštění vzdálený ladicí program jako službu, naleznete v tématu [spustit vzdálený ladicí program jako službu](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Připojení k aplikaci ASP.NET ze sady Visual Studio

1. Na počítači aplikace Visual Studio otevřete řešení, které se pokoušíte ladit (**MyASPApp** jestli dodržujete všechny kroky v tomto článku).
2. V sadě Visual Studio, klikněte na tlačítko **ladit > připojit k procesu** (Ctrl + Alt + P).

    > [!TIP]
    > V sadě Visual Studio 2017, můžete znovu připojit do stejného procesu dříve připojena k pomocí **ladit > znovu připojit k procesu...** (Shift + Alt + P). 

3. Nastavit pole kvalifikátor  **\<název vzdáleného počítače >: 4022**.
4. Klikněte na tlačítko **aktualizovat**.
    Měli byste vidět některé procesy, které se zobrazí v **procesy k dispozici** okna.

    Pokud se nezobrazí všechny procesy, použijte adresu IP místo názvu vzdáleného počítače (port, který se vyžaduje). Můžete použít `ipconfig` v příkazovém řádku k získání adresy IPv4.

    Pokud chcete použít **najít** tlačítko, možná budete muset [otevřete UDP port 3702](#bkmk_openports) na serveru.

5. Zkontrolujte **Zobrazit procesy všech uživatelů**.
6. Zadejte první písmeno názvu procesu a rychle najít **dotnet.exe** (pro ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klikněte na tlačítko **připojit**.

8. Otevřete web, vzdáleném počítači. V prohlížeči přejděte na **http://\<název vzdáleného počítače >**.
    
    Zobrazí se webová stránka ASP.NET.

9. Ve spuštěné aplikaci ASP.NET, kliknutím na odkaz **o** stránky.

    Zarážka by měla být dosažena v sadě Visual Studio.

## <a name="bkmk_openports"></a> Řešení potíží: Otevřete požadované porty ve Windows serveru

Ve většině nastavení jsou otevřené požadované porty instalace technologie ASP.NET a vzdálený ladicí program. Ale budete muset ověřit, že jsou otevřené porty.

> [!NOTE]
> Na Virtuálním počítači Azure, musíte otevřít porty prostřednictvím [skupinu zabezpečení sítě](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic).

Požadované porty:

- 80 – požadováno pro službu IIS
- 4022 – požadováno pro vzdálené ladění ze sady Visual Studio 2017 (viz [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md) podrobné informace.
- 8172 – (volitelné) požadované pro nasazení webu k nasazování aplikací ze sady Visual Studio.
- UDP 3702 – port (volitelné) zjišťování umožňuje **najít** tlačítko při připojování vzdáleného ladicího programu v sadě Visual Studio.

1. Chcete-li otevřít port v systému Windows Server, otevřete **spustit** nabídky, vyhledejte **brány Windows Firewall s pokročilým zabezpečením**.

2. Klikněte na tlačítko **příchozí pravidla > nové pravidlo > portu**a potom klikněte na tlačítko **Další**. (UDP 3702 zvolte **odchozí pravidla** místo.)

3. V části **určité místní porty**, zadejte číslo portu, klikněte na tlačítko **Další**.

4. Klikněte na tlačítko **povolit připojení**, klikněte na tlačítko **Další**.

5. Vyberte jeden nebo více typů sítě pro povolení portu a klikněte na tlačítko **Další**.

    Typ, který jste vybrali musí zahrnovat sítě, ke kterému je připojený vzdáleného počítače.
6. Přidat název (například **IIS**, **Webdeploy**, nebo **msvsmon**) pro příchozí pravidlo a klikněte na tlačítko **Dokončit**.

    Měli byste vidět nové pravidlo v seznamu pravidel příchozí nebo odchozí pravidla.

    Pokud chcete další informace o konfiguraci brány Windows Firewall, najdete v článku [konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Vytvořte další pravidla pro požadované porty.
