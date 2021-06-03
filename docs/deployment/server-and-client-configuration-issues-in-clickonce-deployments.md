---
title: Problémy s konfigurací serveru nebo klienta (ClickOnce)
description: Přečtěte si o problémech s konfigurací serveru a klienta, které mohou ovlivnit nasazení vaší aplikace ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f0361816d0621f52e9f95f4159dd0d46f4f5951
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352004"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problémy s konfigurací serveru a klienta v nasazeních ClickOnce
Pokud na Windows Serveru použijete službu Internetová informační služba (IIS) a vaše nasazení obsahuje typ souboru, který Systém Windows nerozpozná, například soubor aplikace Microsoft Word, služba IIS odmítne tento soubor přenést a vaše nasazení nebude úspěšné.

 Kromě toho některé webové servery a software webových aplikací, například , obsahují seznam souborů a typů souborů, které [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nelze stáhnout. Například zabrání [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stahování všech souborů *Web.config* souborů. Tyto soubory mohou obsahovat citlivé informace, jako jsou uživatelská jména a hesla.

 I když by toto omezení nemělo způsobovat žádné problémy při stahování základních souborů, jako jsou manifesty a sestavení, může vám toto omezení bránit ve stahování datových souborů zahrnutých [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rámci vaší aplikace. V nástroji můžete tuto chybu vyřešit odebráním obslužné rutiny, která zakáže stahování takových souborů ze správce [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] konfigurace služby IIS. Další podrobnosti najdete v dokumentaci k serveru SLUŽBY IIS.

 Některé webové servery můžou blokovat soubory s příponami *jako.dll*, *.config* a *.mdf*. Aplikace založené na systému Windows obvykle obsahují soubory s některými z těchto přípon. Pokud se uživatel pokusí spustit aplikaci, která přistupuje k blokovanému souboru na webovém [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] serveru, dojde k chybě. Místo odblokování všech přípon souborů publikuje každý soubor [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace s příponou *souboru .deploy* ve výchozím nastavení. Správce proto musí nakonfigurovat webový server tak, aby odblokuje následující tři přípony souborů:

- *.application*

- *.manifest*

- *.deploy*

  Tuto možnost však můžete zakázat vymazáním možnosti Použít příponu souboru **".deploy"** v dialogovém okně Možnosti publikování [.](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))V takovém případě musíte nakonfigurovat webový server tak, aby odblokuje všechny přípony souborů používané v aplikaci.

  Budete muset nakonfigurovat *.manifest*, *.application* a *.deploy,* například pokud používáte službu IIS, ve které nemáte nainstalovaný .NET Framework, nebo pokud používáte jiný webový server (například Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce a SSL (Secure Sockets Layer) (SSL)
 Aplikace bude přes SSL fungovat správně, s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] výjimkou případů, Internet Explorer vyvolá výzvu týkající se certifikátu SSL. Výzva může být vyvolána, pokud je s certifikátem něco v pořádku, například když se názvy lokalit neshodují nebo pokud vypršela platnost certifikátu. Pokud chcete pracovat přes připojení SSL, ujistěte se, že je certifikát aktuální a že data certifikátu odpovídají datům [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lokality.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce a ověřování proxy serverem
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] poskytuje podporu pro integrované ověřování proxy ve Windows počínaje .NET Framework 3.5. Nejsou vyžadovány machine.config direktivy specifické pro jazyk . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] neposkytuje podporu pro jiné ověřovací protokoly, jako je Basic nebo Digest.

 Pokud chcete tuto funkci povolit, můžete .NET Framework opravu hotfix pro verzi 2.0. Další informace najdete v tématu OPRAVA: Chybová zpráva při pokusu o instalaci aplikace ClickOnce, kterou jste vytvořili v [.NET Framework 2.0,](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)do klientského počítače, který je nakonfigurovaný pro použití proxy server: Vyžaduje se ověření proxy serverem.

 Další informace najdete v [ \<defaultProxy> elementu (nastavení sítě).](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)

## <a name="clickonce-and-web-browser-compatibility"></a>Kompatibilita Technologie ClickOnce a webového prohlížeče
 V současné době se instalace spustí jenom v případě, že je adresa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] URL manifestu nasazení otevřená pomocí Internet Explorer. Nasazení, jehož adresa URL se spustí z jiné aplikace, jako je systém Microsoft Office Outlook, se úspěšně spustí pouze v případě, Internet Explorer je nastaven jako výchozí webový prohlížeč.

> [!NOTE]
> Mozilla Firefox se podporuje, pokud poskytovatel nasazení není prázdný nebo je nainstalované technologie Microsoft .NET Framework Assistant. Toto rozšíření je součástí .NET Framework 3.5 SP1. V případě podpory XBAP se v případě potřeby aktivuje modul plug-in NPWPF.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Aktivace aplikací ClickOnce prostřednictvím skriptování prohlížeče
 Pokud jste vyvinuli vlastní webovou stránku, která spouští aplikaci pomocí aktivního skriptování, můžete zjistit, že se aplikace na některých počítačích [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nebude spouštět. Internet Explorer obsahuje nastavení s názvem **Automatické výzvy** ke stažení souborů , které toto chování ovlivňuje. Toto nastavení je dostupné na **kartě Zabezpečení** v nabídce **Možnosti,** která toto chování ovlivňuje. Nazývá se Automatické **výzvy ke stažení souborů a** je uvedená pod kategorií **Stažené** soubory. Vlastnost je u intranetových **webových** stránek ve  výchozím nastavení nastavená na Povolit a pro internetové webové stránky je ve výchozím nastavení nastavená na Hodnotu Zakázat. Pokud je toto nastavení nastavené na **Hodnotu Disable**(Zakázat), všechny pokusy o aktivaci aplikace prostřednictvím kódu programu (například přiřazením její adresy URL k [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `document.location` vlastnosti) se zablokují. Za těchto okolností mohou uživatelé spouštět aplikace pouze prostřednictvím stahování iniciované uživatelem, například kliknutím na hypertextový odkaz nastavený na adresu URL aplikace.

## <a name="additional-server-configuration-issues"></a>Další problémy s konfigurací serveru

##### <a name="administrator-permissions-required"></a>Požadovaná oprávnění správce
 Pokud publikujete pomocí protokolu HTTP, musíte mít na cílovém serveru oprávnění správce. Služba IIS vyžaduje tuto úroveň oprávnění. Pokud ne publikujete pomocí protokolu HTTP, potřebujete oprávnění k zápisu pouze do cílové cesty.

##### <a name="server-authentication-issues"></a>Problémy s ověřováním serveru
 Když publikujete na vzdálený server, který má vypnutý anonymní přístup, zobrazí se následující upozornění:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Ověřování protokolem NTLM (NT challenge-response) můžete nastavit tak, aby fungovalo, pokud web zobrazí výzvu k zadání jiných přihlašovacích údajů, než jsou vaše výchozí přihlašovací údaje, a v dialogovém okně zabezpečení po zobrazení výzvy kliknete na OK, pokud chcete zadané přihlašovací údaje uložit pro budoucí relace.  Toto alternativní řešení ale nebude fungovat pro základní ověřování.

## <a name="use-third-party-web-servers"></a>Použití webových serverů třetích stran
 Pokud nasazujete aplikaci z jiného webového serveru než IIS, může dojít k problému, pokud server vrací nesprávný typ obsahu pro soubory klíčů, jako je [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest nasazení a manifest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. Pokud chcete tento problém vyřešit, podívejte se do dokumentace nápovědy k webovému serveru o tom, jak na server přidat nové typy obsahu, a ujistěte se, že jsou na místě všechna mapování přípon názvů souborů uvedená v následující tabulce.

|Přípona názvu souboru|Typ obsahu|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce a mapované jednotky
 Pokud použijete Visual Studio k publikování aplikace ClickOnce, nemůžete zadat mapovanou jednotku jako umístění instalace. Aplikaci ClickOnce ale můžete upravit tak, aby se instaloval z mapované jednotky pomocí generátoru manifestu a editoru (Mage.exe a MageUI.exe). Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) a [MageUI.exe (Manifest Generation and Editing Tool, grafický klient).](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Pro instalaci aplikací se nepodporuje protokol FTP
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podporuje instalaci aplikací z libovolného webového serveru nebo souborového serveru HTTP 1.1. Instalace aplikací protokol FTP (File Transfer Protocol) nepodporuje protokol FTP. Protokol FTP můžete použít pouze k publikování aplikací. Následující tabulka shrnuje tyto rozdíly:

| Typ adresy URL | Description |
|----------| - |
| ftp:// | Aplikaci můžete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publikovat pomocí tohoto protokolu. |
| http:// | Aplikaci můžete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nainstalovat pomocí tohoto protokolu. |
| https:// | Aplikaci můžete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nainstalovat pomocí tohoto protokolu. |
| File:// | Aplikaci můžete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nainstalovat pomocí tohoto protokolu. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall
 Ve výchozím nastavení windows XP SP2 povoluje bránu Windows Firewall. Pokud vyvíjíte aplikaci na počítači s nainstalovaným systémem Windows XP, stále můžete publikovat a spouštět aplikace z místního serveru se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spuštěnou službou IIS. K serveru se spuštěnou službou IIS však nelze získat přístup z jiného počítače, pokud neotevřete bránu Windows Firewall. Pokyny ke správě brány Windows Firewall najdete v nápovědě k Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Povolení rozšíření serveru FrontPage
 Pro publikování aplikací na webový server Windows, který používá protokol HTTP, se vyžaduje rozšíření frontpage serveru od Microsoftu.

 Ve výchozím nastavení windows Server nemá nainstalovaná rozšíření FrontPage Serveru. Pokud chcete použít k publikování na webový server Windows Server, který používá PROTOKOL HTTP s rozšířeními frontpage serveru, musíte nejprve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nainstalovat rozšíření frontpage serveru. Instalaci můžete provést pomocí nástroje pro správu serveru ve Windows Serveru.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: Uzamčené typy obsahu
 Služba IIS v systému uzamkne všechny typy souborů s výjimkou určitých známých typů obsahu [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] (například *.htm*, *.html,* *.txt* atd.). Pokud chcete povolit nasazení aplikací pomocí tohoto serveru, musíte změnit nastavení služby IIS tak, aby bylo možné stahovat soubory typu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *.application*, *.manifest* a všechny ostatní vlastní typy souborů používané vaší aplikací.

 Pokud nasazujete pomocí serveru služby IIS, *spusťteinetmgr.exe* a přidejte nové typy souborů pro výchozí webovou stránku:

- Pro *přípony .application* a *.manifest* by měl být typ MIME "application/x-ms-application". U jiných typů souborů by typ MIME měl být "application/octet-stream".

- Pokud vytvoříte typ MIME s příponou " " a typem \<em> MIME "application/octet-stream", umožní stažení souborů odblokovaných typů souborů. (Blokované typy souborů, jako jsou *\* .aspx* a *\* .asmx,* ale není možné stáhnout.)

  Konkrétní pokyny ke konfiguraci typů MIME na Windows Serveru najdete v tématu Postup přidání typu [MIME na web nebo do aplikace](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>Mapování typů obsahu
 Při publikování přes protokol HTTP by typ obsahu (označované také jako typ MIME) pro *soubor .application* měl být application/x-ms-application. Pokud máte na .NET Framework nainstalovanou sadu 2.0, nastaví se tato možnost automaticky. Pokud není nainstalovaný, musíte pro kořenovou složku aplikace (nebo celý server) vytvořit přidružení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] typu MIME.

 Pokud nasazujete pomocí serveru služby IIS, spusťte <em>nástroj inetmgr.</em> exe a přidejte nový typ obsahu application/x-ms-application pro *příponu .application.*

## <a name="http-compression-issues"></a>Problémy s kompresí HTTP
 Pomocí nástroje můžete provádět stahování pomocí komprese HTTP, technologie webového serveru, která pomocí algoritmu GZIP komprimuje datový proud před odesláním [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] streamu klientovi. Klient –v tomto případě [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] – dekomprimuje datový proud před čtením souborů.

 Pokud používáte službu IIS, můžete snadno povolit kompresi HTTP. Pokud ale povolíte kompresi HTTP, je povolená pouze pro určité typy souborů– konkrétně pro HTML a textové soubory. Pokud chcete povolit kompresi pro sestavení (*.dll*), XML (*.xml*), manifesty nasazení (*.application*) a manifesty aplikací (*.manifest*), musíte přidat tyto typy souborů do seznamu typů, které má služba IIS komprimovat. Dokud do nasazení přidáte typy souborů, budou komprimovány pouze textové soubory a soubory HTML.

 Podrobné pokyny pro službu IIS najdete v tématu [Určení dalších typů dokumentů pro kompresi HTTP.](/troubleshoot/iis/content-types-http-compression)

## <a name="see-also"></a>Viz také
- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)
