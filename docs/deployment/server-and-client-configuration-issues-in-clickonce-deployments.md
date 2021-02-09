---
title: Problémy s konfigurací serveru a klienta (ClickOnce)
description: Přečtěte si o problémech s konfigurací serveru a klienta, které mohou ovlivnit nasazení aplikace ClickOnce.
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
ms.openlocfilehash: 469749c28acdb90e835082dd05010102ab50e52b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877613"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problémy s konfigurací serveru a klienta v nasazeních ClickOnce
Pokud používáte službu Internetová informační služba (IIS) v systému Windows Server a vaše nasazení obsahuje typ souboru, který systém Windows nerozpoznal, například soubor aplikace Microsoft Word, služba IIS odmítne přenést daný soubor a vaše nasazení nebude úspěšné.

 Kromě toho některé webové servery a software webové aplikace, jako například [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , obsahují seznam souborů a typů souborů, které nelze stáhnout. Například [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zabraňuje stažení všech *Web.config* souborů. Tyto soubory mohou obsahovat citlivé informace, jako jsou uživatelská jména a hesla.

 I když toto omezení by nemělo způsobovat žádné problémy při stahování základních [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] souborů, jako jsou manifesty a sestavení, může toto omezení zabránit stažení datových souborů, které jsou součástí vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. V [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nástroji můžete tuto chybu vyřešit odebráním obslužné rutiny, která zakazuje stahování takových souborů ze Správce konfigurace služby IIS. Další podrobnosti najdete v dokumentaci k serveru služby IIS.

 Některé webové servery mohou blokovat soubory s příponami, například *. dll*, *. config* a *. mdf*. Aplikace založené na systému Windows obvykle obsahují soubory s některými z těchto rozšíření. Pokud se uživatel pokusí spustit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci, která přistupuje k blokovanému souboru na webovém serveru, bude výsledkem chyba. Místo odblokování všech přípon souborů [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publikuje každý soubor aplikace s příponou *. deploy* ve výchozím nastavení. Proto správce potřebuje jenom nakonfigurovat webový server, aby odblokoval následující tři přípony souborů:

- *. Application*

- *. manifest*

- *. deploy*

  Tuto možnost však můžete zakázat zrušením výběru možnosti **Přípona souboru ". deploy"** v [dialogovém okně Možnosti publikování](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)). v takovém případě je nutné nakonfigurovat webový server tak, aby odblokoval všechny přípony souborů používané v aplikaci.

  Budete muset nakonfigurovat *. manifest*, *. Application* a *. deploy*, například pokud používáte službu IIS, kde jste nenainstalovali .NET Framework, nebo pokud používáte jiný webový server (například Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce a SSL (Secure Sockets Layer) (SSL)
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aplikace bude pracovat přes SSL s výjimkou případů, kdy Internet Explorer vyvolá výzvu k certifikátu SSL. Pokud se jedná o problém s certifikátem, může být vyvolána výzva, například když se názvy lokalit neshodují nebo vypršela platnost certifikátu. Aby bylo možné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pracovat s připojením SSL, ujistěte se, že je certifikát aktuální a že data certifikátu odpovídají datům lokality.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce a ověřování proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] poskytuje podporu pro ověřování integrovaného proxy serveru Windows počínaje verzí .NET Framework 3,5. Nejsou vyžadovány žádné konkrétní direktivy machine.config. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] neposkytuje podporu pro jiné protokoly ověřování, jako je například Basic nebo Digest.

 K povolení této funkce můžete také použít opravu hotfix .NET Framework 2,0. Další informace najdete v tématu [Oprava: chybová zpráva při pokusu o instalaci aplikace ClickOnce, kterou jste vytvořili v .NET Framework 2,0, do klientského počítače, který je nakonfigurovaný tak, aby používal proxy server: "ověření proxy požadováno"](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that).

 Další informace naleznete v tématu [ \<defaultProxy> element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce a kompatibilita webového prohlížeče
 V současné době se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalace spustí jenom v případě, že se adresa URL manifestu nasazení otevře pomocí aplikace Internet Explorer. Nasazení, jehož adresa URL se spustí z jiné aplikace, například systém Microsoft Office Outlook, se spustí úspěšně jenom v případě, že je aplikace Internet Explorer nastavená jako výchozí webový prohlížeč.

> [!NOTE]
> Mozilla Firefox je podporovaná, pokud poskytovatel nasazení není prázdný nebo je nainstalované rozšíření Microsoft .NET Framework Assistant. Toto rozšíření je zabaleno pomocí .NET Framework 3,5 SP1. V případě podpory XBAP je modul plug-in NPWPF v případě potřeby aktivovaný.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Aktivace aplikací ClickOnce prostřednictvím skriptování v prohlížeči
 Pokud jste vytvořili vlastní webovou stránku, která spouští [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci pomocí aktivního skriptování, můžete zjistit, že se aplikace na některých počítačích nespustí. Internet Explorer obsahuje nastavení s názvem **Automatické dotazování pro stahování souborů**, což má vliv na toto chování. Toto nastavení je k dispozici na kartě **zabezpečení** v nabídce **Možnosti** , která má vliv na toto chování. Se nazývá **Automatické dotazování souborů ke stažení** a je uvedené pod kategorií **stažené položky** . Vlastnost je nastavená na **Povolit** ve výchozím nastavení pro intranetové webové stránky a **zakáže** se ve výchozím nastavení pro internetové webové stránky. Pokud je toto nastavení **zakázáno**, bude blokován jakýkoli pokus o aktivaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace programově (například přiřazením adresy URL k `document.location` Vlastnosti). V této situaci můžou uživatelé spouštět aplikace jenom prostřednictvím stahování iniciované uživatelem, například kliknutím na hypertextový odkaz, který je nastavený na adresu URL aplikace.

## <a name="additional-server-configuration-issues"></a>Další problémy s konfigurací serveru

##### <a name="administrator-permissions-required"></a>Jsou vyžadována oprávnění správce.
 Pokud publikujete pomocí protokolu HTTP, musíte mít na cílovém serveru oprávnění správce. Služba IIS vyžaduje tuto úroveň oprávnění. Pokud nepublikujete pomocí protokolu HTTP, budete potřebovat pouze oprávnění k zápisu do cílové cesty.

##### <a name="server-authentication-issues"></a>Problémy s ověřováním serveru
 Při publikování na vzdáleném serveru, který má vypnutý anonymní přístup, se zobrazí následující upozornění:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Ověřování protokolem NTLM (NT Challenge-Response) můžete provést, pokud se na webu zobrazí výzva k zadání přihlašovacích údajů, které nejsou výchozími přihlašovacími údaji, a v dialogovém okně zabezpečení klikněte na **OK** , když se zobrazí dotaz, jestli chcete zadané přihlašovací údaje uložit pro budoucí relace. Toto řešení ale nebude fungovat pro základní ověřování.

## <a name="use-third-party-web-servers"></a>Použití webových serverů třetích stran
 Pokud nasazujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci z jiného webového serveru než služby IIS, může dojít k potížím, pokud server vrací nesprávný typ obsahu pro klíčové [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory, jako je například manifest nasazení a manifest aplikace. Chcete-li vyřešit tento problém, přečtěte si dokumentaci k webovému serveru o tom, jak přidat nové typy obsahu na server a zda jsou uvedena všechna mapování přípon názvů souborů uvedená v následující tabulce.

|Přípona názvu souboru|Typ obsahu|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce a mapované jednotky
 Pokud používáte aplikaci Visual Studio k publikování aplikace ClickOnce, nelze jako umístění instalace zadat namapovanou jednotku. Aplikaci ClickOnce je však možné upravit tak, aby se instalovala z mapované jednotky pomocí generátoru a editoru manifestu (Mage.exe a MageUI.exe). Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) a [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokol FTP není podporován pro instalaci aplikací.
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podporuje instalaci aplikací z libovolného webového serveru s protokolem HTTP 1,1 nebo ze souborového serveru. Server FTP, protokol FTP (File Transfer Protocol), není podporován pro instalaci aplikací. Protokol FTP můžete použít pouze k publikování aplikací. Následující tabulka shrnuje tyto rozdíly:

| Typ adresy URL | Description |
|----------| - |
| ftp:// | Aplikaci můžete publikovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí tohoto protokolu. |
| http:// | Aplikaci můžete nainstalovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí tohoto protokolu. |
| https:// | Aplikaci můžete nainstalovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí tohoto protokolu. |
| file:// | Aplikaci můžete nainstalovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí tohoto protokolu. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Brána Windows Firewall
 Ve výchozím nastavení systém Windows XP SP2 povoluje bránu Windows Firewall. Pokud vyvíjíte aplikaci na počítači s nainstalovaným systémem Windows XP, budete moci publikovat a spouštět [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace z místního serveru, na kterém je spuštěna služba IIS. Nemůžete ale přistupovat k tomuto serveru, na kterém běží služba IIS, z jiného počítače, pokud neotevřete bránu Windows Firewall. Pokyny pro správu brány Windows Firewall najdete v nápovědě k systému Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: povolení rozšíření serveru FrontPage
 K publikování aplikací na webový server Windows, který používá protokol HTTP, se vyžaduje rozšíření serveru FrontPage od Microsoftu.

 Ve výchozím nastavení není v systému Windows Server nainstalováno rozšíření serveru FrontPage. Pokud chcete použít nástroj [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] k publikování na webový server Windows serveru, který používá protokol HTTP s rozšířeními FrontPage Server Extensions, musíte nejdřív nainstalovat rozšíření FrontPage Server Extensions. Instalaci můžete provést pomocí nástroje Správa serveru ve Windows serveru.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: uzamčené typy obsahu
 Služba IIS v [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] zamkne všechny typy souborů s výjimkou určitých známých typů obsahu (například *. htm*, *. html*, *. txt* atd.). Chcete-li povolit nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací pomocí tohoto serveru, je třeba změnit nastavení služby IIS, aby bylo možné stahovat soubory typu *. Application*, *. manifest* a jakékoli další vlastní typy souborů používané vaší aplikací.

 Pokud nasazujete pomocí serveru služby IIS, spusťte *inetmgr.exe* a přidejte nové typy souborů pro výchozí webovou stránku:

- Pro rozšíření *. Application* a *. manifest* by měl být typu MIME "application/x-MS-Application". U ostatních typů souborů by měl být typ MIME "Application/oktet-Stream".

- Pokud vytvoříte typ MIME s příponou \<em> a typem MIME "Application/oktet-Stream", bude možné stáhnout soubory neblokovaného typu souboru. (Nicméně blokované typy souborů, jako např *\* . aspx* a *\* . asmx* , se nedají stáhnout.)

  Konkrétní pokyny týkající se konfigurace typů MIME na Windows serveru najdete v tématu [Postup přidání typu MIME na web nebo do aplikace](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>Mapování typu obsahu
 Při publikování přes protokol HTTP by měl být typ obsahu (označovaný také jako typ MIME) pro soubor *. Application* aplikace "application/x-MS-Application". Pokud máte na serveru nainstalovanou .NET Framework 2,0, automaticky se nastaví. Pokud není tato instalace nainstalována, je třeba vytvořit přidružení typu MIME pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] virtuální kořenový adresář aplikace (nebo celý server).

 Pokud nasadíte pomocí serveru služby IIS, spusťte příkaz <em>inetmgr.</em> exe a přidejte nový typ obsahu "application/x-MS-Application" pro příponu *. Application* .

## <a name="http-compression-issues"></a>Problémy s kompresí HTTP
 Pomocí nástroje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] můžete provádět stahování, která používají kompresi HTTP, technologii webového serveru, která používá algoritmus gzip ke komprimaci datového proudu před odesláním datového proudu klientovi. Klient – v tomto případě [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] – dekomprimuje datový proud před čtením souborů.

 Pokud používáte službu IIS, můžete snadno povolit kompresi HTTP. Pokud však povolíte kompresi HTTP, je povolena pouze pro určité typy souborů – konkrétně HTML a textové soubory. Chcete-li povolit kompresi pro sestavení (*. dll*), XML (*. XML*), manifesty nasazení (*. Application*) a manifesty aplikace (*. manifest*), je nutné přidat tyto typy souborů do seznamu typů pro službu IIS pro komprimaci. Dokud do nasazení nepřidáte typy souborů, budou komprimovány pouze soubory textu a HTML.

 Podrobné pokyny pro službu IIS najdete v tématu [Určení dalších typů dokumentů pro kompresi HTTP](https://support.microsoft.com/help/234497).

## <a name="see-also"></a>Viz také
- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)
