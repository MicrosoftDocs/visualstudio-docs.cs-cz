---
title: Řešení chyb (nasazení ClickOnce)
description: Tento článek popisuje běžné chyby, ke kterým může dojít při nasazení aplikace ClickOnce a popisuje kroky pro vyřešení každého problému.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af462178cf18d57afa6b51aedaba0004615ebb6f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349258"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Řešení konkrétních chyb v nasazeních ClickOnce
V tomto článku jsou uvedené běžné chyby, ke kterým může dojít při nasazování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace a popisuje kroky k vyřešení jednotlivých problémů.

## <a name="general-errors"></a>Obecné chyby

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Když se pokusíte najít soubor aplikace, nedojde k žádnému vyvolání nebo vykreslí XML v aplikaci Internet Explorer nebo se zobrazí dialogové okno spustit nebo Uložit jako.
 Tato chyba je pravděpodobně způsobena typy obsahu (známé také jako typy MIME), které nejsou na serveru nebo klientovi správně registrovány.

 Nejdřív se ujistěte, že je server nakonfigurovaný tak, aby přidružil příponu *. Application* s typem obsahu application/x-MS-Application.

 Pokud je server nakonfigurován správně, ověřte, zda je v počítači nainstalováno .NET Framework 2,0. Pokud je nainstalovaná .NET Framework 2,0 a stále se tento problém zobrazuje, zkuste odinstalovat a znovu nainstalovat .NET Framework 2,0 pro opětovné registraci typu obsahu v klientovi.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Chybová zpráva říká, že nelze načíst aplikaci. Soubory chybějící v nasazení "nebo" stahování aplikace bylo přerušeno, vyhledejte chyby sítě a opakujte akci později. "
 Tato zpráva znamená, že jeden nebo více souborů, na které odkazují [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty, nelze stáhnout. Nejjednodušší způsob, jak tuto chybu ladit, je zkusit stáhnout adresu URL, která říká, že se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nedá stáhnout. Tady jsou některé možné příčiny:

- Pokud soubor protokolu říká "(403) zakázáno" nebo "(404) Nenalezeno", "Ověřte, zda je webový server nakonfigurován tak, aby neblokoval stahování tohoto souboru. Další informace najdete v tématu [problémy s konfigurací serveru a klienta v nasazeních ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Pokud je soubor *. config* zablokovaný serverem, přečtěte si část "Chyba stahování při pokusu o instalaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, která má soubor. config" dále v tomto článku.

- Určete, jestli k této chybě došlo, protože `deploymentProvider` Adresa URL v manifestu nasazení odkazuje na jiné místo, než je adresa URL, která se používá pro aktivaci.

- Zajistěte, aby byly na serveru přítomny všechny soubory. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] protokol by měl sdělit, který soubor nebyl nalezen.

- Podívejte se, jestli nedochází k problémům se síťovým připojením. Tato zpráva se zobrazí, pokud klientský počítač přešel do režimu offline během stahování.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Chyba stahování při pokusu o instalaci aplikace ClickOnce, která má soubor. config
 Ve výchozím nastavení zahrnuje Visual Basic aplikace založené na Windows App.config soubor. Dojde k potížím, když se uživatel pokusí o instalaci z webového serveru, který používá systém Windows Server 2003, protože tento operační systém zablokuje instalaci souborů *. config* z bezpečnostních důvodů. Chcete-li povolit instalaci souboru *. config* , klikněte v dialogovém okně **Možnosti publikování** na **použít příponu souboru. deploy** .

 Také musíte nastavit typy obsahu (známé také jako typy MIME) pro soubory. Application,. manifest a. deploy. Další informace najdete v dokumentaci k webovému serveru.

 Další informace najdete v části Windows Server 2003: uzamčené typy obsahu v tématu [problémy s konfigurací serveru a klienta v nasazeních ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Chybová zpráva: aplikace je nesprávně naformátovaná; Soubor protokolu obsahuje hodnotu signatura XML je neplatná.
 Ujistěte se, že jste aktualizovali soubor manifestu a znovu jste ho podepsali. Znovu publikujte aplikaci pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebo použijte Mage pro opětovné podepsání aplikace.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Aktualizovali jste aplikaci na serveru, ale klient nestáhne aktualizaci.
 Tento problém lze vyřešit provedením jedné z následujících úloh:

- Prověřte `deploymentProvider` adresu URL v manifestu nasazení. Ujistěte se, že aktualizujete bity ve stejném umístění, `deploymentProvider` na které odkazuje.

- Ověřte interval aktualizace v manifestu nasazení. Pokud je tento interval nastavený na pravidelný interval, například jednou za každých šest hodin, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] neprojde aktualizace, dokud tento interval neuplyne. Můžete změnit manifest pro vyhledávání aktualizace při každém spuštění aplikace. Změna intervalu aktualizace je pohodlnější možnost během doby vývoje, která umožňuje ověřit instalaci aktualizací, ale zpomaluje aktivaci aplikace.

- Zkuste znovu spustit aplikaci v nabídce Start. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mohla být zjištěna aktualizace na pozadí, ale zobrazí výzvu k instalaci bitů při další aktivaci.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Během aktualizace se zobrazí chyba, která obsahuje následující položku protokolu: "odkaz v nasazení neodpovídá identitě definované v manifestu aplikace".
 K této chybě může dojít, protože jste ručně upravili manifesty nasazení a aplikace a způsobili, že popis identity sestavení v jednom manifestu není synchronizován s druhým. Identita sestavení se skládá z jeho názvu, verze, jazykové verze a tokenu veřejného klíče. Prověřte popisy identit v manifestech a opravte případné rozdíly.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>První aktivace z místního disku nebo disku CD-ROM je úspěšná, ale následná aktivace z nabídky Start neproběhne úspěšně.
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pro příjem aktualizací aplikace používá adresu URL poskytovatele nasazení. Ověřte, zda je umístění, na které adresa URL odkazuje, správné.

#### <a name="error-cannot-start-the-application"></a>Chyba: "nelze spustit aplikaci"
 Tato chybová zpráva obvykle znamená, že při instalaci této aplikace do úložiště došlo k potížím [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Buď má aplikace chybu, nebo je úložiště poškozené. Soubor protokolu vám může sdělit, kde došlo k chybě.

 Postupujte následovně:

- Ověřte, že identita manifestu nasazení, identita manifestu aplikace a identita hlavního nástroje EXE aplikace jsou všechny jedinečné.

- Ověřte, že cesty k souborům nejsou delší než 100 znaků. Pokud vaše aplikace obsahuje cesty k souborům, které jsou moc dlouhé, možná byste překročili omezení maximální cesty, kterou můžete uložit. Zkuste zkrátit cesty a znovu nainstalovat.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Nedodržují se nastavení nastavení privatePath v konfiguračním souboru aplikace.
 Aby bylo možné používat nastavení PrivatePath (prozjišťovací cesty pro Bing), musí aplikace požádat o úplné oprávnění důvěryhodnosti. Zkuste změnit manifest aplikace, aby požadoval úplný vztah důvěryhodnosti, a akci opakujte.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Během odinstalace se zobrazí zpráva oznamující, že se nepodařilo odinstalovat aplikaci.
 Tato zpráva obvykle znamená, že aplikace již byla odebrána nebo je úložiště poškozeno. Po kliknutí na tlačítko **OK** bude položka **Přidat nebo odebrat program** odebrána.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Během instalace se zobrazí zpráva oznamující, že nejsou nainstalované závislosti platformy.
 Chybí předpoklad v globální mezipaměti sestavení (GAC), kterou aplikace potřebuje ke spuštění.

## <a name="publishing-with-visual-studio"></a>Publikování pomocí sady Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>Publikování v aplikaci Visual Studio se nezdařilo
 Ujistěte se, že máte právo na publikování na serveru, na který cílíte. Pokud jste například přihlášeni k počítači terminálového serveru jako běžný uživatel, ne jako správce, pravděpodobně nebudete mít k publikování na místním webovém serveru potřebná práva.

 Pokud publikujete s adresou URL, ujistěte se, že cílový počítač má povolená rozšíření serveru FrontPage.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Chybová zpráva: nelze vytvořit web \<site> . Komponenty pro komunikaci s rozšířeními serveru FrontPage nejsou nainstalovány.
 Ujistěte se, že na počítači, ze kterého publikujete, máte nainstalovanou komponentu Microsoft Visual Studio Web Authoring. Pro uživatele Express není tato součást nainstalována ve výchozím nastavení. Další informace najdete na webu [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Chybová zpráva: Nepodařilo se najít soubor Microsoft. Windows. Common-Controls, Version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , Type = Win32.
 Tato chybová zpráva se zobrazí při pokusu o publikování aplikace WPF s povolenými vizuálními styly. Chcete-li vyřešit tento problém, přečtěte si téma [Postupy: publikování aplikace WPF s povolenými vizuálními styly](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>Použití Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Pokusili jste se podepsat certifikát v úložišti certifikátů a přijatou prázdnou zprávu.
 V dialogovém okně **podepisování** musíte:

- Vyberte **podepsat s uloženým certifikátem** a

- Vyberte certifikát ze seznamu; první certifikát není výchozím výběrem.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Kliknutím na tlačítko nepodepisovat dojde k výjimce.
 Tento problém je známá chyba. Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty musí být podepsány. Stačí vybrat jednu z možností podepisování a pak kliknout na tlačítko **OK**.

## <a name="additional-errors"></a>Další chyby
 V následující tabulce jsou uvedeny některé běžné chybové zprávy, které uživatel klientského počítače může obdržet, když uživatel nainstaluje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci. Každá chybová zpráva je uvedena vedle popisu nejpravděpodobnější příčiny chyby.

| Chybová zpráva | Popis |
| - | - |
| Aplikaci nelze spustit. Obraťte se na vydavatele aplikace.<br /><br /> Aplikaci nelze spustit. Požádejte o pomoc dodavatele aplikace. | Jedná se o obecné chybové zprávy, ke kterým dochází, když aplikaci nelze spustit a žádný jiný důvod není možné najít. Často to znamená, že aplikace je nějakým způsobem poškozená nebo že [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je úložiště poškozené. |
| Nelze pokračovat. Aplikace je nesprávně naformátovaná. Kontaktujte vydavatele aplikace a požádejte ho o pomoc.<br /><br /> Ověření aplikace nebylo úspěšné. Nelze pokračovat.<br /><br /> Soubory aplikace nelze načíst. Soubory poškozené v nasazení. | Jeden ze souborů manifestu v nasazení není syntakticky platný nebo obsahuje hodnotu hash, která nemůže být odsouhlasena s odpovídajícím souborem. Tato chyba může také znamenat, že manifest vložený do sestavení je poškozen. Znovu vytvořte nasazení a znovu zkompilujte aplikaci nebo Najděte a opravte chyby ručně v manifestech. |
| Aplikaci nelze načíst. Chyba ověřování.<br /><br /> Instalace aplikace se nezdařila. Nelze najít soubory aplikace na serveru. Požádejte o pomoc vydavatele aplikace nebo svého správce. | Jeden nebo více souborů v nasazení nelze stáhnout, protože nemáte oprávnění pro přístup k nim. To může být způsobeno chybou 403 zakázáno webovým serverem, ke kterému může dojít v případě, že jeden ze souborů v nasazení skončí s příponou, která webový server považuje za chráněný soubor. Adresář, který obsahuje jeden nebo více souborů aplikace, může také vyžadovat uživatelské jméno a heslo, aby bylo možné získat přístup. |
| Aplikaci nelze stáhnout. V aplikaci chybí požadované soubory. Požádejte o pomoc dodavatele aplikace nebo správce systému. | Jeden nebo více souborů uvedených v manifestu aplikace nelze na serveru nalézt. Ověřte, že jste nahráli všechny závislé soubory nasazení, a zkuste to znovu. |
| Stažení aplikace nebylo úspěšné. Ověřte připojení k síti nebo se obraťte na správce systému nebo poskytovatele síťové služby. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Nelze navázat síťové připojení k serveru. Prověřte dostupnost serveru a stav vaší sítě. |
| URLDownloadToCacheFile se nezdařilo s HRESULT ' \<number> '. Při pokusu o stažení došlo k chybě \<file> . | Pokud má uživatel nastavenou možnost Upřesnit zabezpečení aplikace Internet Explorer "Zobrazit upozornění v případě změny mezi zabezpečeným a nezabezpečeným režimem" v cílovém počítači nasazení a v případě, že se adresa URL instalace aplikace ClickOnce přesměruje z nezabezpečeného na zabezpečenou lokalitu (nebo naopak), instalace selže, protože upozornění na Internet Explorer je přerušeno.<br /><br /> Tuto chybu můžete vyřešit provedením jedné z následujících úloh:<br /><br /> – Vymaže možnost zabezpečení.<br />-Ujistěte se, že není adresa URL instalace přesměrována takovým způsobem, který mění režimy zabezpečení.<br />– Odeberte přesměrování úplně a nasměrujte na vlastní adresu URL nastavení. |
| Při zápisu na pevný disk došlo k chybě. Na disku není k dispozici dostatek místa. Požádejte o pomoc dodavatele aplikace nebo správce systému. | To může znamenat nedostatek místa na disku pro uložení aplikace, ale může také znamenat obecnější vstupně-výstupní chybu při pokusu o uložení souborů aplikace na jednotku. |
| Aplikaci nelze spustit. Na disku není dostatek volného místa. | Pevný disk je plný. Uvolněte místo a zkuste aplikaci spustit znovu. |
| Probíhá pokus o načtení příliš velkého počtu nasazených aktivací najednou. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] omezuje počet různých aplikací, které mohou být spuštěny ve stejnou dobu. To je hlavně z důvodu ochrany proti škodlivým pokusům o provedla útok DOS na místní [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] službu. uživatelé, kteří se pokusí spustit stejnou aplikaci opakovaně, v rychlém úspěchu, budou mít jenom jednu instanci aplikace. |
| V síti nelze aktivovat zástupce. | Zástupce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace lze spustit pouze na místním pevném disku. Nelze je spustit otevřením adresy URL, která odkazuje na soubor zástupce na vzdáleném serveru. |
| Aplikace je příliš velká pro spuštění online v částečném vztahu důvěryhodnosti. Požádejte o pomoc dodavatele aplikace nebo správce systému. | Aplikace, která běží v částečném vztahu důvěryhodnosti, nemůže být větší než polovina velikosti online kvóty aplikací, která je standardně 250 MB. |

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)