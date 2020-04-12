---
title: Instalace a použití za bránou firewall nebo proxy serverem
description: Zkontrolujte adresy URL domény, porty a protokoly, které můžete chtít přidat do seznamu povolených adres nebo otevřít, pokud vaše organizace používá bránu firewall nebo proxy server
ms.date: 02/01/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 025cf432912d38976507c93545e7c38b44d86fd8
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223655"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalace a použití sady Visual Studio a služeb Azure Services za bránou firewall nebo proxy serverem

Pokud vy nebo vaše organizace používá bezpečnostní opatření, jako je brána firewall nebo proxy server, pak existují adresy URL domény, které můžete chtít přidat do "seznamu povolených" a porty a protokoly, které můžete chtít otevřít, abyste měli co nejlepší zkušenosti při instalaci a používání sady Visual Studio a služby Azure.

* **[Instalace sady Visual Studio](#install-visual-studio)**: Tyto tabulky obsahují adresy URL domény, které chcete přidat do seznamu povolených adres, abyste měli přístup ke všem požadovaným součástem a úlohám.

* **[Použití Sady Visual Studio a služeb Azure:](#use-visual-studio-and-azure-services)** Tato tabulka obsahuje adresy URL domény, které chcete přidat do seznamu povolených adres, a porty a protokoly, které chcete otevřít, abyste měli přístup ke všem funkcím a službám, které chcete.

> [!NOTE]
> Tento článek byl napsán pro Visual Studio v systému Windows, ale některé informace jsou také použitelné pro [instalaci sady Visual Studio for Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za bránu firewall nebo proxy server.

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL, které chcete přidat do seznamu povolených adres

Vzhledem k tomu, že Instalační služba sady Visual Studio stahuje soubory z různých domén a jejich serverů pro stahování, tady jsou adresy URL domény, které můžete chtít přidat do seznamu povolených adres jako důvěryhodné v rozhraní UI nebo ve skriptech nasazení.

#### <a name="microsoft-domains"></a>Domény Společnosti Microsoft

| Domain (Doména) | Účel |
| - | - |
| go.microsoft.com | Nastavení překladu adres URL |
| aka.ms | Nastavení překladu adres URL |
| download.visualstudio.microsoft.com | Umístění pro stažení instalačních balíčků |
| download.microsoft.com | Umístění pro stažení instalačních balíčků |
| download.visualstudio.com | Umístění pro stažení instalačních balíčků |
| dl.xamarin.com | Umístění pro stažení instalačních balíčků |
| xamarin-downloads.azureedge.net | Umístění seznamu seznam ů sad Android SDK |
| marketplace.visualstudio.com | Umístění pro stažení rozšíření Visual Studio Extensions |
| \*.gallerycdn.vsassets.io  | Umístění pro stažení rozšíření Visual Studio Extensions |
| visualstudio.microsoft.com | Umístění dokumentace |
| docs.microsoft.com | Umístění dokumentace |
| msdn.microsoft.com | Umístění dokumentace |
| www\.microsoft.com | Umístění dokumentace |
| \*.windows.net | Přihlašovací lokace |
| \*.microsoftonline.com | Přihlašovací lokace |
| \*.live.com | Přihlašovací lokace |
| | |

#### <a name="non-microsoft-domains"></a>Domény jiných společností než Microsoft

| Domain (Doména) | Nainstaluje tyto úlohy. |
| - | - |
| archive.apache.org | Vývoj mobilních zařízení pomocí JavaScriptu (Cordova) |
| cocos2d-x.org | Vývoj her s C++ (Cocos) |
| download.epicgames.com | Vývoj her s C++ (Unreal Engine) |
| download.oracle.com | Vývoj mobilních zařízení pomocí JavaScriptu (Java SDK) <br /><br />Vývoj mobilních zařízení pomocí rozhraní .NET (Java SDK) |
| download.unity3d.com | Vývoj her s Unity (Unity) |
| netstorage.unity3d.com | Vývoj her s Unity (Unity) |
| dl.google.com | Vývoj mobilních zařízení pomocí JavaScriptu (Android SDK a NDK, Emulátor) <br /><br />Vývoj mobilních zařízení s rozhraním .NET (Android SDK a NDK, Emulátor) |
| www\.incredibuild.com | Vývoj her s C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Vývoj her s C++ (IncrediBuild) |
| www\.python.org | Vývoj Pythonu (Python) <br /><br />Datové vědy a analytické aplikace (Python) |
| developerservices2.apple.com | Zřizování Xamarin.iOS |
| developer.apple.com | Zřizování Xamarin.iOS |
| appstoreconnect.apple.com | Zřizování Xamarin.iOS |
| idmsa.apple.com | Zřizování Xamarin.iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Použití Visual Studia a služeb Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL, které chcete přidat do seznamu povolených adres, a porty a protokoly, které chcete otevřít

Chcete-li se ujistit, že máte přístup ke všemu, co chcete při použití sady Visual Studio nebo služby Azure za bránou firewall nebo proxy serverem, tady jsou adresy URL, které byste měli přidat do seznamu povolených adres a porty a protokoly, které můžete chtít otevřít.

| Služba nebo scénář | Koncový bod DNS | Protocol (Protokol)<br/>/Port | Popis |
| - | - | -: | - | - |
| zprostředkovatele identity<br>řešení | go.microsoft.com<br><br>aka.ms | | Slouží ke zkrácení adres URL, které se pak přemisí na delší adresy URL |
| Úvodní stránka | vsstartpage.blob.core.windows.net | 443 | Slouží k zobrazení zpráv pro vývojáře zobrazených na úvodní stránce (pouze Visual Studio 2017) |
| Targeted<br> Oznámení <br>Služba | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Slouží k filtrování globálního seznamu oznámení do seznamu, který je použitelný pouze pro určité typy počítačů/scénářů použití. |
| Linka <br>kontrola aktualizace | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Slouží k poskytování oznámení, pokud má nainstalované rozšíření k dispozici aktualizaci. <br><br> Používá se jako přihlašovací umístění |
| Projekt AI <br>Integrace | az861674.vo.msecnd.net | 443<br> | Slouží ke konfiguraci nových projektů pro odesílání dat o využití do registrovaného účtu Application Insights. |
| Kód objektivu | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Slouží k poskytnutí informací v editoru o tom, kdy byl soubor naposledy aktualizován, časové ose změn, pracovních položkách, ke kterým jsou změny přidruženy, autorech a dalších |
| Experimentální <br>funkce povolující | visualstudio-devdiv-c2s.msedge.net | 80 | Slouží k aktivaci experimentálních nových funkcí nebo změn funkcí. |
| Identifikační "odznak" <br>(uživatelské jméno a avatar)<br>a <br>Nastavení roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Slouží k zobrazení jména uživatele a avatar v IDE <br><br> Používá se k zajištění toho, aby se změny nastavení přecvačiovaly z jednoho počítače do druhého. |
| Vzdálená nastavení | az700632.vo.msecnd.net | 443 | Slouží k vypnutí rozšíření, o kterých je známo, že způsobují problémy v sadě Visual Studio. |
| Nástroje systému Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Používá se pro scénáře obchodu s aplikacemi pro Windows |
| Schéma JSON <br>Zjišťování <br><br>Schéma JSON <br>Definice<br><br>Schéma JSON <br>Podpora pro <br>Prostředky Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Slouží ke zjišťování a stahování schémat JSON, která může uživatel použít při úpravách dokumentů JSON. <br><br>Používá se k získání metavalidačního schématu pro JSON.<br><br>Slouží k získání aktuálního schématu pro šablony nasazení Azure Resource Manageru. |
| Balíček NPM <br>zjištění | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | Požadováno pro vyhledávání balíčků NPM a používá se pro instalaci balíčku skriptů na straně klienta ve webových projektech |
| Bower balíček<br> ikony<br><br>Bower balíček <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Poskytuje výchozí ikonu balíčku bower  <br><br>Poskytuje možnost vyhledávat balíčky Bower |
| NuGet<br><br>Balíček NuGet<br> zjištění | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | Slouží k ověření podepsaných balíčků NuGet.<br><br>Vyžadováno pro vyhledávání balíčků a verzí NuGet |
| Informace o úložišti GitHub | api.github.com | https/443 | Vyžadováno pro získání dalších informací o bowerových balíčcích |
| Webové lintery | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Cookiecutter<br>Šablona Průzkumníka<br>zjištění <br><br>Cookiecutter <br>Projekt Průzkumníka<br> Vytvoření | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Používá se k objevování online šablon z našeho doporučeného zdroje a z úložišť GitHub <br><br>Slouží k vytvoření projektu ze šablony cookiecutter, která vyžaduje jednorázovou instalaci balíčku cookiecutter Python z indexu balíčku Pythonu (PyPI) |
| Balíček Pythonu <br>zjištění<br><br>Balíček Pythonu <br>správa<br><br>Nová <br>Python <br> projekt <br>šablony | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Poskytuje možnost vyhledávat pip balíčky<br><br>Používá se k automatické instalaci pipu, pokud chybí <br><br>Používá se k vyřešení následujících nových šablon projektu Pythonu na adresy URL šablony cookiecutter:<br> - Projekt klasifikátoru<br>- Clustering projekt <br> - Regresní projekt <br> - PyGame pomocí PyKinect <br> - Projekt Pyvot |
| Office web <br>doplněk <br> Manifest <br>Ověření <br>Služba | verificationservice.osi.office.net | https/443 | Slouží k ověření manifestů pro webové doplňky Office |
| SharePoint a <br>Doplňky pro Office | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | Slouží k publikování a testování doplňků SharePointu a Office na SharePointu Online a Office 365 |
| Správce pracovních postupů <br>Testovací služba<br> Hostitel | | http/12292 | Pravidlo brány firewall, které je vytvořeno automaticky pro testování doplňků služby SharePoint pomocí pracovních postupů |
| Automaticky shromažďovány <br>statistika spolehlivosti <br>a další <br>Zákaznická zkušenost <br>Programy zlepšování (CEIP)<br> pro Azure SDK a <br>pro nástroje SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Slouží k odesílání statistik spolehlivosti (data selhání/zablokování) od uživatele společnosti Microsoft. Skutečné výpisy stavu/zablokování budou odeslány, pokud je povoleno zasílání zpráv o chybách systému Windows. budou potlačeny pouze statistické informace; <br>Slouží k odhalení anonymních vzorců využití rozšíření Sady Azure Tools SDK do sady Visual Studio a pro vzory využití nástrojů SQL do sady Visual Studio. |
| Visual Studio <br> Zákaznická zkušenost <br>Program zlepšování (Program zlepšování programu Zlepšování softwaru a služeb na základě <br><br>Soubor PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Slouží ke shromažďování anonymních vzorců použití a chybových protokolů. <br><br>Slouží ke sledování problémů se zmrazením ui. |
| Tvorba a<br>Řízení <br>Prostředky Azure | management.azure.com <br>management.core.windows.net | https/443 | Používá se k vytváření webů Azure nebo jiných prostředků pro podporu publikování webových aplikací, funkcí Azure nebo webových úloh. |
| Aktualizované nástroje pro publikování na webu <br>kontroly a rozšíření <br>Doporučení | marketplace.visualstudio.com | https/443 | Používá se pro kontrolu dostupnosti aktualizovaných nástrojů pro publikování. Pokud je zakázáno, nemusí být zobrazeno potenciální doporučené rozšíření pro publikování na webu. |
| Aktualizovaný prostředek Azure <br>Informace o koncovém bodu vytvoření | \*.blob.core.windows.net | https/443 | Slouží k aktualizaci koncových bodů používaných pro vytváření prostředků Azure pro určité služby Azure. Pokud je zakázáno, místo toho se použijí poslední stažená nebo vytvořená umístění koncového bodu. |
| Vzdálené ladění a <br>Vzdálené profilování <br>Weby Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Používá se pro připojení vzdáleného ladicího programu k webům Azure. Pokud je zakázáno, připojení vzdáleného ladicího programu k webům Azure nebude fungovat |
| Active Directory <br>Graph | graph.windows.net | https/443 | Slouží ke zřizování nových aplikací služby Azure Active Directory. Používá ho také poskytovatel služeb připojený k Office 365 MSGraph |
| Azure Functions <br>Aktualizace cli <br>Zaškrtnout | functionscdn.azureedge.net | https/443 | Používá se pro kontrolu aktualizovaných verzí příkazového příkazu funkce Azure. Pokud je zakázáno, bude místo toho použita kopie (nebo kopie přenášená komponentou Azure Functions) příkazového příkazového příkazu. |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | HTTP se používá pro gradle stahování během sestavení; HTTPS se používá k zahrnutí plug-inů Cordova do projektů |
| Průzkumník cloudu | 1. &#60;&#62; shlukových bodů <br>Service Fabric <br>2. &#60;koncový bod&#62;<br>Obecný cloud ový exp <br>3.&#62; koncového bodu grafu &#60;<br>Obecný cloud ový exp<br>4. &#60;koncového bodu účtu úložiště&#62;<br>Uzly úložiště <br>5.&#62; adres URL portálu Azure &#60;<br>Obecný cloud ový exp <br>6. &#60;koncové body trezoru klíčů&#62; <br>Uzly virtuálních mís v Azure Správce prostředků<br>7. &#60;&#62; PublicIPAddressOfCluster<br>Service Fabric Vzdálené ladění a ETW stopy | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7.tcp/dynamický | 1. Příklad: test12.eastus.cloudapp.com<br>2. Načte předplatná a načítá/spravuje prostředky Azure<br>3. Načte předplatná Azure Stack<br>4. Spravuje prostředky úložiště (příklad: mystorageaccount.blob.core.windows.net)<br>5. Možnost kontextové nabídky "Otevřít na portálu" (otevře prostředek na webu Azure Portal)<br>6. Vytvoří a použije trezory klíčů pro ladění virtuálních klíčů (Příklad: myvault.vault.azure.net) <br><br>7. Dynamicky přiděluje blok portů na základě počtu uzlů v clusteru a dostupných portů. <br><br>Blok portu se pokusí získat trojnásobek počtu uzlů s minimálně 10 porty.<br><br>Pro trasování streamování je proveden pokus o získání bloku portu z 810. Pokud některý z tohoto bloku portu je již použit, pak je proveden pokus získat další blok a tak dále. (Je výloha zatížení je prázdný, pak porty z 810 jsou s největší pravděpodobností používány) <br><br>Podobně pro ladění jsou vyhrazeny čtyři sady portů bloků: <br>- konektorPort: 30398, <br>- forwarderPort: 31398, <br>- spediční Portx86: 31399,<br>- souborUploadPort: 32398<br> |
| Cloud Services | 1. PRV<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;cloudové služby uživatele&#62;.cloudapp.net <br> &#60;oblast virtuálního počítače&#62;.&#60;uživatele&#62;.azure.com | 1. <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Virtuální počítač Vzdálené plochy ke cloudovým službám <br><br> 2. Součástí účtu úložiště konfigurace soukromé diagnostiky <br><br> 3. Portál Azure <br><br> 4. Průzkumník serveru – &#42; úložiště Azure je účet úložiště s názvem zákazník  <br><br> 5. Odkazy na otevření portálu &#47; Stáhnout certifikát odběru &#47; soubor nastavení publikování <br><br>6. a) Konektor místní port pro vzdálené ladění pro cloudovou službu a virtuální hod<br> 6. b) Konektor veřejného portu pro vzdálené ladění pro cloudovou službu a virtuální mísu <br> 6. c) Místní port pro předávání pro vzdálené ladění pro cloudovou službu a virtuální mísu <br> 6. d) Veřejný port pro předávání pro vzdálené ladění pro cloudovou službu a virtuální mísu  <br> 6. e) Místní port pro nahrávání souborů pro vzdálené ladění pro cloudovou službu a virtuální mísu <br> 6. f) Veřejný port pro nahrávání souborů pro vzdálené ladění pro cloudovou službu a virtuální virtuální mísu |
| Service Fabric | 1. <br>Ocs. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; visualstudio.com | https/443 | 1. Dokumentace <br><br> 2. Vytvoření funkce clusteru <br><br>3. &#42; je název trezoru klíčů Azure (příklad: - test11220180112110108.vault.azure.net  <br><br>  4. &#42; je dynamický (Příklad: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Snímek <br>Ladicí program | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. Ip adresa vzdálené služby/serverů/fqdn | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6.<br> 4022 (závisí na verzi sady Visual Studio) | 1. Soubor souboru .json pro velikost skladové položky aplikační služby <br>2. Různá volání Azure RM <br>3. Zahřívač stránek přes  <br>4. Cílový koncový bod služby App Service Kudu zákazníka <br>5. Verze rozšíření webu dotazu publikovaná v nuget.org <br>6. [Vzdálené ladění](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Slouží k zobrazení, odeslání, spuštění a správě úloh ASA <br><br> Používá se k procházení clusterů HDI a k odesílání, diagnostice a ladění úloh HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Slouží ke kompilaci, odeslání, zobrazení, diagnostice a ladění úloh; slouží k procházení souborů ADLS; slouží k nahrávání a stahování souborů |
| Balicí služba | [účet].visualstudio.com <br/> [účet]. \*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | \*.npmjs.org, \*.nuget.org a \*.nodejs.org jsou vyžadovány pouze pro určité scénáře úloh sestavení (například: NuGet Tool Installer, Node Tool Installer) nebo pokud máte v úmyslu používat veřejné upstream s informačníkanály. Další tři domény jsou vyžadovány pro základní funkce služby Packaging. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Používá se k propojení se službami Azure DevOps Services |
| Komunita vývojářů | sendvsfeedback2.azurewebsites.net/api | https/443 | Používá se k volání developer komunity Zpětná vazba nástroj API (moje problémy, vyhledávání, hlasování, komentář, odeslat, nahrát, pokračovat) |
| Intellicode | \*.intellicode.vsengsaas.visualstudio.com | https/443 | Slouží k volání api Intellicode |
| Live Share | \*.liveshare.vsengsaas.visualstudio.com| https/443 | Používá se k volání live share API |
| Visual Studio Online | \*.online.visualstudio.com | https/443 | Slouží k volání online api sady Visual Studio. |
| Automatické pořízení typu JavaScript | registry.npmjs.org | https/443 | Slouží k instalaci definic typů typu TypeScript, které poskytují intellisense pro oblíbené knihovny JavaScriptu. |
| Licenční služba předplatných sady Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licencování/práva zákazníků | https/443 | Licencování pro online aktivaci |
| Ladicí program | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon. \*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Používá se pro stahování bitů ladicího programu pro ladění .NET Core na Unixu / macOS přes SSH <br><br>2. <br>Používá se pro stahování bitů ladicího programu pro vzdálené ladění kontejnerů Windows Docker.<br><br> 3. Používá se pro krokování zdroje rozhraní .NET Framework <br><br> 4. <br>(Pokud se uživatel přihlásí) Používá se pro stahování symbolů publikovaných na nuget.org serveru symbolů.<br><br> 5. (Pokud se uživatel rozhodne) Používá se pro stahování symbolů MS a binárních souborů, může být také potřeba pro ladění spravovaného kódu v výpisech |
| Visual Studio Online| \*.online.visualstudio.com | https/443 | Slouží k volání online api sady Visual Studio. |
| Publikování aplikací pro Android Xamarin | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Používá se k interakci se službou Google Play Store publikovat nebo nahrávat aplikace Xamarin Pro Android přímo z Visual Studia. |
| Azure Container Registry | *.azurecr.io | https/443 | Přístup k registrům kontejnerů hostovaným v Azure pro konfiguraci kanálů CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Poradce při potížích souvisejících se sítí

Někdy můžete spustit v síti nebo proxy související chyby při instalaci nebo použití sady Visual Studio za bránou firewall nebo proxy server. Další informace o řešeních těchto chybových zpráv naleznete na [stránce Poradce při potížích se sítí při instalaci nebo použití](troubleshooting-network-related-errors-in-visual-studio.md) stránky sady Visual Studio.

## <a name="get-support"></a>Získat podporu

Nabízíme možnost podpory [**instalačního chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (pouze v angličtině) pro problémy související s instalací.

Zde je několik dalších možností podpory:

* Oznamte nám problémy s produktem prostřednictvím nástroje [Nahlásit problém,](../ide/how-to-report-a-problem-with-visual-studio.md) který se zobrazí v instalačním programu sady Visual Studio i v ide sady Visual Studio.
* Navrhněte funkci, sledujte problémy s produkty a najděte odpovědi v [komunitě pro vývojáře sady Visual Studio](https://developercommunity.visualstudio.com/).
* Pomocí svého účtu [GitHub](https://github.com/) můžete mluvit s námi a dalšími vývojáři Visual Studia v [konverzaci ve Visual Studiu v komunitě Gitter](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Viz také

* [Požadavky na připojení pro Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Poradce při potížích se sítí v sadě Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace za bránu firewall nebo proxy server (Visual Studio pro Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
