---
title: Problémy s konfigurací klienta v nasazeních ClickOnce a server | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 444cfa375fd4e2059ddf6458224836cdec6ff18f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849432"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problémy s konfigurací serveru a klienta v nasazeních ClickOnce
Pokud používáte Internetové informační služby (IIS) v systému Windows Server a vaše nasazení obsahuje typ souboru, který se nedokáže rozpoznat Windows, jako je například Microsoft Word soubor, služba IIS odmítne přenášet tento soubor a nasazení se nezdaří.  

 Kromě toho některé webové servery a software webových aplikací, jako například [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], obsahují seznam souborů a typy souborů, které nejde stáhnout. Například [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zamezí se tím stahování všech *Web.config* soubory. Tyto soubory mohou obsahovat citlivé informace, jako jsou uživatelská jména a hesla.  

 Ačkoli toto omezení by nemělo způsobit žádné problémy pro stahování základní [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory, jako je například manifestů a sestavení, toto omezení může znemožnit stahování datových souborů, které jsou součástí vašeho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. V [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], tuto chybu lze vyřešit tak, že odeberete obslužná rutina, která zakazuje stahování těchto souborů ze Správce konfigurace služby IIS. Zobrazit další podrobnosti naleznete v dokumentaci serveru služby IIS.  

 Některé webové servery může blokovat soubory s příponami, například *.dll*, *.config*, a *.mdf*. Aplikace pro systém Windows obvykle zahrnují soubory pomocí některé z těchto rozšíření. Pokud se uživatel pokusí spustit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci, která přistupuje k zablokování souborů na webovém serveru, bude výsledkem chyba. Místo odblokování všechny přípony souborů, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] každý soubor aplikace se publikuje *.deploy* příponu souboru ve výchozím nastavení. Správce proto potřebuje nakonfigurovat webový server k odblokování tři soubory s následujícími příponami:  

- *.Application*  

- *.manifest*  

- *.deploy* 

  Ale můžete tuto možnost zakážete zrušením zaškrtnutí **použít příponu ".deploy"** možnost [dialogové okno publikování možnosti](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)), v takovém případě musíte nakonfigurovat webový server k odblokování všechny přípony souborů použít v aplikaci.  

  Budete muset nakonfigurovat *.manifest*, *.application*, a *.deploy*, například, pokud používáte IIS, kde jste dosud nenainstalovali [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], nebo pokud jste pomocí jiného webového serveru (např. Apache).  

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce a Secure Sockets Layer (SSL)  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace bude fungovat přes protokol SSL, s výjimkou případů, kdy aplikace Internet Explorer vyvolá řádku o certifikát SSL. Řádku tento příkaz může být je aktivována v případě, že něco špatného certifikát, jako je například, když nejsou shodné názvy webů nebo certifikátu vypršela. Chcete-li [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fungovat připojení přes protokol SSL, ujistěte se, že certifikát je aktuální, a že data certifikátu odpovídá data lokality.  

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce a proxy serveru ověřování  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] poskytuje podporu pro spuštění v rozhraní .NET Framework 3.5 Windows integrované ověřování proxy serveru. Žádné konkrétní machine.config direktivy jsou povinné. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] neposkytuje podporu pro dalších protokolů ověřování, jako je například základní nebo Digest.  

 Můžete také použít opravu hotfix na rozhraní .NET Framework 2.0 tuto funkci povolil. Další informace naleznete v tématu http://go.microsoft.com/fwlink/?LinkId=158730.  

 Další informace najdete v tématu [ \<defaultProxy > – element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce a webové prohlížeče kompatibility  
 V současné době [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zařízení se spustí jenom v případě, že adresa URL pro manifest nasazení se otevře pomocí aplikace Internet Explorer. Nasazení, jehož adresa URL se spustí z jiné aplikace, jako je například aplikace Microsoft Office Outlook se úspěšně spustí jenom v případě, že aplikace Internet Explorer je nastaven jako výchozí webový prohlížeč.  

> [!NOTE]
>  Mozilla Firefox se podporuje, pokud poskytovatel nasazení není prázdné nebo je nainstalované rozhraní Microsoft .NET Framework – Pomocník rozšíření. Toto rozšíření je součástí balíčku rozhraní .NET Framework 3.5 SP1. Pro podporu XBAP NPWPF modul plug-in se aktivuje v případě potřeby.  

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Aktivace aplikace ClickOnce pomocí prohlížeče skriptování  
 Pokud jste si vytvořili vlastní webovou stránku, která spustí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí aktivní skriptování, můžete zjistit, že aplikace se nespustí na některých počítačích. Aplikace Internet Explorer obsahuje nastavení, nazvané **Automatické dotazování pro stahování souborů**, což má vliv na toto chování. Toto nastavení je k dispozici na **zabezpečení** kartu v jeho **možnosti** nabídky, která má vliv na toto chování. Je volána **Automatické dotazování pro stahování souborů**, a je uvedena pod **stáhne** kategorie. Je nastavena na **povolit** ve výchozím nastavení pro intranet webových stránek a **zakázat** ve výchozím nastavení pro internetové webové stránky. Když toto nastavení je **zakázat**, žádný pokus o aktivaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace prostřednictvím kódu programu (například přiřazením jeho adresy URL `document.location` vlastnost) se zablokují. V této situaci uživatelé můžou spouštět aplikace jenom do uživatelem iniciované stahování, například kliknutím na hypertextový odkaz nastavený na adresu URL vaší aplikace.  

## <a name="additional-server-configuration-issues"></a>Další problémy konfigurace serveru  

##### <a name="administrator-permissions-required"></a>Požadována oprávnění správce  
 Pokud publikujete pomocí protokolu HTTP, musíte mít oprávnění správce na cílovém serveru. Službu IIS vyžaduje tuto úroveň oprávnění. Pokud nejsou publikování pomocí protokolu HTTP, pouze potřebujete oprávnění zapisovat na cílové cestě.  

##### <a name="server-authentication-issues"></a>Problémy s ověřováním serveru  
 Když publikujete na vzdálený server s přístupem "anonymní" vypnuté, zobrazí se následující upozornění:  

```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  

> [!NOTE]
>  Můžete provést ověřování protokolem NTLM (NT – výzva odezva) fungovat, pokud webu se výzva k zadání přihlašovacích údajů než výchozí pověření, a v dialogovém okně zabezpečení kliknete **OK** po zobrazení výzvy Pokud budete chtít uložte zadané přihlašovací údaje pro budoucí relace. Toto řešení však nebude fungovat pro základní ověřování.  

## <a name="use-third-party-web-servers"></a>Použijte webové servery třetích stran  
 Pokud provádíte nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace z webového serveru, než je služba IIS, vám může dojít k potížím Pokud server vrací nesprávný typ obsahu pro klíč [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory, jako je například manifest nasazení a manifest aplikace. Chcete-li tento problém vyřešit, najdete v nápovědě webový server dokumentace o tom, jak přidat nové typy obsahu na serveru a ujistěte se, že všechny mapování přípon názvů souborů uvedené v následující tabulce jsou na místě.  

|Přípona názvu souboru|Typ obsahu|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  

## <a name="clickonce-and-mapped-drives"></a>ClickOnce a namapované jednotky  
 Pokud používáte sadu Visual Studio k publikování aplikace ClickOnce, nelze zadat mapovanou jednotku jako umístění instalace. Však můžete upravit aplikaci ClickOnce, instalace z mapované jednotky pomocí generátor manifestu a Editor (Mage.exe a MageUI.exe). Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) a [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokol FTP není podporován pro instalaci aplikací  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podporuje instalaci aplikací z libovolné HTTP 1.1 webového nebo souborového serveru. FTP, File Transfer Protocol, není podporován pro instalaci aplikace. Publikování aplikací jenom pomocí funkce FTP. Následující tabulka shrnuje tyto rozdíly:  


| Typ adresy URL | Popis |
|----------| - |
| FTP: / / | Můžete publikovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí tohoto protokolu. |
| http:// | Můžete nainstalovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí tohoto protokolu. |
| https:// | Můžete nainstalovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí tohoto protokolu. |
| File:// | Můžete nainstalovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí tohoto protokolu. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Brány Windows Firewall  
 Ve výchozím nastavení povoluje bránu Windows Firewall Windows XP s aktualizací SP2. Pokud vyvíjíte aplikace na počítači s nainstalovaným Windows XP, budete stále moct publikovat a spustit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace z místního serveru, na kterém běží služby IIS. Však nelze přistupovat k serveru, na kterém běží služby IIS z jiného počítače, není-li otevřít bránu Windows Firewall. Pokyny pro správu brány Windows Firewall, naleznete v nápovědě Windows.  

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Povolte rozšíření serveru FrontPage  
 Rozšíření serveru FrontPage od Microsoftu se vyžaduje pro publikování aplikací na Windows server, který používá protokol HTTP.  

 Ve výchozím nastavení Windows Server nemá nainstalované rozšíření serveru FrontPage. Pokud chcete použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] publikovat na Windows serveru webový server, který používá protokol HTTP pomocí rozšíření serveru FrontPage, je nutné nainstalovat rozšíření serveru FrontPage nejprve. Instalaci můžete provést pomocí nástroje Správa serveru pro správu ve Windows serveru.  

## <a name="windows-server-locked-down-content-types"></a>Systému Windows Server: Typy obsahu uzamknuté  
 Služba IIS na [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] uzamyká všechny typy souborů s výjimkou určitých známých typů obsahu (například *.htm*, *.html*, *.txt*, a tak dále). Chcete-li povolit nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí tohoto serveru, budete muset změnit nastavení služby IIS umožňující stahování souborů typu *.application*, *.manifest*a všechny ostatní typy vlastního souboru používá vaše aplikace.  

 Pokud nasadíte pomocí serveru služby IIS, spusťte *inetmgr.exe* a přidat nové typy souborů pro výchozí webové stránky:  

- Pro *.application* a *.manifest* rozšíření, typ MIME by měl být "application/x-ms aplikace." Pro ostatní typy souborů by měl být typu MIME "application/octet-stream."  

- Pokud vytvoříte typ MIME s příponou "<em>" a "application/octet-stream" typ MIME bude možné soubory typu odblokuje soubor ke stažení. (Ale zablokuje typy souborů, jako je například *.aspx</em> a *.asmx* nelze stáhnout.)  

  Konkrétní pokyny ke konfiguraci typy MIME ve Windows serveru, najdete v článku znalostní báze Microsoft Knowledge Base KB326965, "IIS 6.0 neobsluhuje neznámé typy MIME" v [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  

## <a name="content-type-mappings"></a>Mapování typu obsahu  
 Při publikování přes protokol HTTP, typ obsahu (označované také jako typ MIME) *.application* soubor by měl být "application/x-ms aplikace." Pokud máte [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] nainstalovaná na serveru, se nastaví pro vás automaticky. Pokud to není nainstalován, pak budete muset vytvořit přidružení typu MIME pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] virtuální kořenový adresář aplikace (nebo celý server).  

 Pokud nasadíte pomocí serveru služby IIS, spusťte <em>inetmgr.</em> soubor EXE a přidejte nový typ "application/x-ms-application" obsahu pro *.application* rozšíření.  

## <a name="http-compression-issues"></a>Problémy komprese protokolu HTTP  
 S [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], můžete provádět souborů ke stažení, které používají komprese protokolu HTTP, technologii webového serveru, který používá algoritmus GZIP ke kompresi datového proudu před odesláním datový proud do klienta. Klient – v takovém případě [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]– dekomprimuje datového proudu před čtením soubory.  

 Pokud používáte službu IIS, můžete snadno povolit kompresi HTTP. Nicméně pokud je povolena komprese protokolu HTTP, je povolena pouze pro některé typy souborů – zejména, HTML a textové soubory. Chcete-li povolit kompresi pro sestavení (*.dll*), XML (*.xml*), manifesty nasazení (*.application*), manifesty aplikace a (*.manifest*), je nutné přidat tyto typy souborů k seznamu typů pro službu IIS zkomprimovat. Dokud nepřidáte typy souborů k nasazení, se zkomprimují pouze text nebo soubory HTML.  

 Podrobné pokyny pro službu IIS najdete v tématu [jak určit další dokumentů typy pro kompresi HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  

## <a name="see-also"></a>Viz také:  
 [Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Nezbytné součásti pro nasazení aplikace](../deployment/application-deployment-prerequisites.md)