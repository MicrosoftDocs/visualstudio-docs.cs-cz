---
title: Řešení konkrétních chyb v nasazeních ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d0b7e53eba21372641bad683c442e796648a4765
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213639"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Řešení konkrétních chyb v nasazeních ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma uvádí následující běžné chyby, které se mohou vyskytnout při nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace a popisuje kroky k vyřešení jednotlivých problémů.  
  
## <a name="general-errors"></a>Obecné chyby  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Při pokusu o vyhledání souboru .application nedojde k žádné akci, nebo XML se vykreslí v aplikaci Internet Explorer nebo se zobrazí dialogové okno spustit nebo uložit jako  
 Tato chyba je pravděpodobně způsobeno typy obsahu (označované také jako typy MIME) není správně zaregistrována na serveru nebo klienta.  
  
 Nejprve se ujistěte, že je server nakonfigurován pro přidružení k obsahu typ "application/x-ms-application" příponu .application.  
  
 Pokud je server nakonfigurován správně, ujistěte se, že [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] je nainstalovaná ve vašem počítači. Pokud [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] je nainstalován, a stále dochází k tomuto problému, zkuste odinstalace a opětovné instalace [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] pro opětovné zaregistrování typu obsahu na straně klienta.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Říká chybová zpráva "Nepodařilo se načíst aplikace. Soubory v nasazení chybí"nebo"stažení aplikace byla přerušena, zkontrolujte chyby sítě a zkuste to znovu později"  
 Tato zpráva znamená, že jeden nebo více souborů se na ně odkazovat [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty nelze stáhnout. Nejjednodušší způsob, jak ladění této chyby je pokus stáhnout adresu URL, která [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] říká nelze stáhnout. Tady jsou některé možné příčiny:  
  
-   Pokud soubor protokolu říká "zakázáno (403)" nebo "(404) Not found" Ověřte, že webový server je nakonfigurován tak, aby neblokovala stažení tohoto souboru. Další informace najdete v tématu [serveru a problémy s konfigurací klienta v nasazeních ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Pokud soubor .config je blokován nastavením serveru, najdete v části "Chyba stahování při pokusu o instalaci [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci, která obsahuje soubor .config" dále v tomto tématu.  
  
-   Určení, zda situaci došlo, protože `deploymentProvider` odkazuje adresy URL v manifestu nasazení do jiného umístění než adresa URL pro aktivaci.  
  
-   Ujistěte se, že všechny soubory jsou k dispozici na serveru. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] protokolu by měl zjistíte soubor, který nebyl nalezen.  
  
-   Podívejte se, jestli jsou problémy se síťovým připojením; Tato zpráva se zobrazí-li klientský počítač přešel do režimu offline během stahování.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Chyba při pokusu o instalaci aplikace ClickOnce, která obsahuje soubor .config stahování  
 Ve výchozím nastavení aplikace pro Windows v jazyce Visual Basic zahrnuje soubor App.config. Bude problém když se uživatel pokusí nainstalovat z webového serveru, který používá Windows Server 2003, protože daný operační systém blokuje instalaci souborech .config z bezpečnostních důvodů. Chcete-li soubor .config k instalaci, klikněte na tlačítko **použít příponu ".deploy"** v **možnosti publikování** dialogové okno.  
  
 Je třeba také nastavit typy obsahu (označované také jako typy MIME) odpovídajícím způsobem pro .application .manifest a .deploy souborů. Další informace naleznete v dokumentaci webového serveru.  
  
 Další informace najdete v tématu "Windows Server 2003: Locked-Down typy obsahu" v [serveru a problémy s konfigurací klienta v nasazeních ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Chybová zpráva: "Aplikace je v nesprávném formátu;" Soubor protokolu obsahuje "XML podpis je neplatný."  
 Nezapomeňte aktualizovat soubor manifestu a podepsat znovu. Znovu publikujte aplikaci s použitím [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo aplikaci znovu podepsat pomocí bitové kopii.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Aktualizovat aplikaci na serveru, ale klient nestáhne aktualizace  
 Tento problém může vyřešit provedením jedné z následujících úloh:  
  
-   Zkontrolujte `deploymentProvider` adresy URL v manifestu nasazení. Ujistěte se, že aktualizujete bitů ve stejném umístění, která `deploymentProvider` odkazuje na.  
  
-   Zkontrolujte interval aktualizace v manifestu nasazení. Pokud tento interval je nastaven jako pravidelný interval, jako je například jednou každých 6 hodin [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nebudou zjišťovat aktualizace až do uplynutí tohoto intervalu. Můžete změnit manifest vyhledávat aktualizace pokaždé, když spuštění aplikace. Změna intervalu aktualizace je vhodná možnost při vývoji ověření probíhá instalace aktualizací, ale může zpomalit aktivace aplikací.  
  
-   Zkuste znovu spustit aplikaci v nabídce Start. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] může být zjištěny aktualizace na pozadí, ale zobrazí výzvu k instalaci na další aktivace.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Při aktualizaci zobrazí chybová zpráva, která má následující záznam protokolu: "odkaz v nasazení neodpovídá identitě definované v manifestu aplikace"  
 K této chybě může dojít, protože jste ručně upravit manifesty nasazení a aplikace a způsobit popis identity sestavení v jednom manifestu přestane být synchronní k ostatním. Identita sestavení se skládá z jeho název, verzi, jazykovou verzi a token veřejného klíče. Popisy identity ve vaší manifesty zkontrolujte a opravte případné rozdíly.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Úspěšná aktivace z místního disku nebo disku CD-ROM poprvé, ale následné aktivace z nabídky Start selže  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Adresa URL poskytovatele nasazení se používá pro příjem aktualizací pro aplikaci. Ověřte, zda je umístění, které se adresa URL odkazuje na správný.  
  
#### <a name="error-cannot-start-the-application"></a>Chyba: "nelze spustit aplikaci"  
 Tato chybová zpráva obvykle indikuje, že dojde k nějakému problému instalaci této aplikace do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ukládat. Aplikace došlo k chybě nebo úložišti je poškozen. Soubor protokolu můžete zjistit, kde došlo k chybě.  
  
 Měli byste provést následující:  
  
-   Ověřte, zda jsou všechny jedinečné identity v manifestu nasazení, identita manifestu aplikace a identitu hlavní aplikace EXE.  
  
-   Ověřte, že vaše cesty k souborům nejsou delší než 100 znaků. Pokud vaše aplikace obsahuje, které jsou příliš dlouhé cesty k souborům, může být delší než omezení na maximální délku cesty, které můžete ukládat. Zkuste, zkrácení cesty a znovu nainstalujte.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Nastavení PrivatePath v konfiguračním souboru aplikace se neuplatňují.  
 Pokud chcete použít nastavení PrivatePath (definovaných cest Fusion), musíte aplikaci požádat o oprávnění úplný vztah důvěryhodnosti. Zkuste změnit manifestu aplikace k vyžádání úplný vztah důvěryhodnosti a pak to zkuste znovu.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Při odinstalaci se zobrazí zpráva, "Se nepodařilo odinstalovat aplikaci"  
 Tato zpráva obvykle znamená, že aplikace již byla odebrána nebo úložišti je poškozen. Po kliknutí na **OK**, **přidat nebo odebrat programy** položka bude odebrána.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Při instalaci zobrazí se zpráva s upozorněním, že nejsou nainstalovány závislostí platformy  
 Chybí předpoklad v mezipaměti GAC (globální mezipaměť sestavení), které aplikace potřebuje, aby bylo možné spustit.  
  
## <a name="publishing-with-visual-studio"></a>Publikování pomocí sady Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Publikování v sadě Visual Studio selže  
 Ujistěte se, že máte právo publikovat na server, na které cílíte. Například pokud jsou přihlášení k počítači terminálového serveru jako běžný uživatel, ne jako správce, pravděpodobně nemáte oprávnění nutná k publikování na místním webovém serveru.  
  
 Pokud publikujete pomocí adresy URL, ujistěte se, že má cílový počítač povolena rozšíření serveru FrontPage.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Chybová zpráva: Nelze vytvořit na webu '\<lokality >'. Komponenty pro komunikaci s rozšíření serveru FrontPage nejsou nainstalovány.  
 Ujistěte se, že máte Microsoft Visual Studio pro vytváření součást webové nainstalované v počítači, které publikujete z. Pro uživatele, Express tato součást není nainstalována ve výchozím nastavení. Další informace najdete na webu [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Chybová zpráva: Nelze najít soubor ' Microsoft.Windows.Common – ovládací prvky, verze=  6.0.0.0, Culture=\*, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, typ = win32.  
 Při pokusu o publikování aplikace WPF s povolenými vizuálními styly, zobrazí se tato chybová zpráva. Chcete-li vyřešit tento problém, naleznete v tématu [postupy: publikování aplikace WPF s vizuální styly povoleny](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Pomocí bitové kopii  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Pokusili jste se přihlásit pomocí certifikátu v úložišti certifikátů a přijatou zprávu prázdné pole  
 V **podepisování** dialogové okno, musíte:  
  
-   Vyberte **přihlašování pomocí uloženého certifikátu**, a  
  
-   Vyberte certifikát ze seznamu. první certifikát není výchozí výběr.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Kliknutím na tlačítko "Není znak" způsobí výjimku  
 Tento problém se o známý problém. Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jsou vyžadovány k podpisu manifestů. Stačí vybrat jednu z možností podepisování a potom klikněte na tlačítko **OK**.  
  
## <a name="additional-errors"></a>Další chyby  
 V následující tabulce jsou uvedeny některé běžné chybové zprávy, které klientské počítače uživatele může zobrazit, když uživatel nainstaluje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Každá chybová zpráva je uvedená vedle popis nejvíce pravděpodobné příčiny chyby.  
  
|Chybová zpráva|Popis|  
|-------------------|-----------------|  
|Aplikaci nelze spustit. Kontaktujte vydavatele aplikace.<br /><br /> Nelze spustit aplikaci. Požádejte o pomoc dodavatele aplikace.|Toto jsou obecné chybové zprávy, které nastaly, když aplikaci nelze spustit, a najdete žádné konkrétní důvod. Často to znamená, že aplikace je nějakým způsobem poškozen, nebo že [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] úložiště je poškozen.|  
|Nelze pokračovat. Aplikace je v nesprávném formátu. Potřebujete pomoc, kontaktujte vydavatele aplikace.<br /><br /> Ověření aplikace nebylo úspěšné. Nelze pokračovat.<br /><br /> Nepovedlo se načíst soubory aplikace. Soubory v nasazení jsou poškozeny.|Jeden ze souborů manifestu v nasazení je syntakticky neplatný nebo obsahuje hodnotu hash, který nelze sjednotit pomocí odpovídající soubor. Tato chyba může také znamenat, že do manifestu vložen do sestavení je poškozený. Znovu vytvořte nasazení a znovu zkompilovat aplikaci, nebo najít a opravit chyby ručně v vaše manifesty.|  
|Nejde načíst aplikace. Došlo k chybě ověřování.<br /><br /> Instalace aplikace nebyla úspěšná. Nelze nalézt soubory aplikace na serveru. Obraťte se na vydavatele aplikace nebo svého správce o pomoc.|Jeden nebo více souborů v nasazení nejde stáhnout, protože nemáte oprávnění pro přístup k nim. Příčinou může být Chyba 403 Zakázáno vrácený webový server, který může dojít, pokud jeden ze souborů ve vašem nasazení končí rozšíření, které je webový server, ji považovat za chráněný soubor. Adresář, který obsahuje jeden nebo více souborů aplikace může také vyžadovat uživatelské jméno a heslo pro přístup k.|  
|Aplikaci nelze stáhnout. Aplikace chybí požadované soubory. Požádejte o pomoc dodavatele aplikace nebo správce systému.|Jeden nebo více souborů uvedených v manifestu aplikace se nenašel na serveru. Ověřte, že jste nahráli závislé soubory všechna nasazení a zkuste to znovu.|  
|Stažení aplikace nebylo úspěšné. Zkontrolujte síťové připojení nebo kontaktujte správce systému či poskytovatele síťových služeb.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Nelze navázat připojení k síti na serveru. Zkontrolujte dostupnost serveru a stavu sítě.|  
|URLDownloadToCacheFile se nezdařila s chybou HRESULT "\<číslo >'. Došlo k chybě při pokusu o stažení "\<soubor >".|Pokud uživatel nastavil možnost rozšířeného zabezpečení aplikace Internet Explorer "Varovat, pokud se mění mezi zabezpečené a není zabezpečený režim" v cílovém počítači nasazení a adresy URL instalační program instaluje aplikace ClickOnce je přesměrován ze nezabezpečený do zabezpečeného webu (nebo a naopak), instalace se nezdaří, protože ji přeruší upozornění v Internet Exploreru.<br /><br /> Chcete-li tento problém vyřešit, proveďte jednu z následujících akcí:<br /><br /> -Zrušte výběr možnosti zabezpečení.<br />– Ujistěte se, že adresa URL nastavení není přesměrován takovým způsobem, který změní režim zabezpečení.<br />-Přesměrování úplně odeberte a přejděte na adresu URL samotný instalační program.|  
|Zápis na disk došlo k chybě. Může být nedostatek místa k dispozici na disku. Požádejte o pomoc dodavatele aplikace nebo správce systému.|To může naznačovat nedostatek místa na disku pro uložení aplikace, ale může také znamenat další obecné vstupně-výstupní chybě při ukládání souborů aplikace na jednotku.|  
|Nelze spustit aplikaci. Na disku není dostatek volného místa.|Pevný disk je plný. Vyčistěte místo a zkuste aplikaci znovu spustit.|  
|Příliš mnoha nasazených aktivací se pokoušíte načíst najednou.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] omezí počet různé aplikace, které lze spustit ve stejnou dobu. Toto je z velké části a pomáhá chránit před škodlivým pokusy k zahájení útoky s cílem odepření služby na místní [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uživatelé, kteří opakovaně, spusťte stejnou aplikaci rychle po sobě, bude pouze skončit s jednou instancí služby; nebyla úspěšná aplikace.|  
|Klávesové zkratky nelze aktivovat přes síť.|Zástupce [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci lze spustit pouze na místním pevném disku. Není možné spustit tak, že otevřete adresu URL, která odkazuje na místní soubor na vzdáleném serveru.|  
|Aplikace je příliš velká pro spuštění online v částečném vztahu důvěryhodnosti. Požádejte o pomoc dodavatele aplikace nebo správce systému.|Aplikace, která běží v částečném vztahu důvěryhodnosti, nemůže být větší než polovina velikosti online aplikace kvótu, která je 250 MB ve výchozím nastavení.|  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



