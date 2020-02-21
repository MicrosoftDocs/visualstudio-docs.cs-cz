---
title: Instalace a použití za bránou firewall nebo proxy server
description: Zkontrolujte adresy URL, porty a protokoly, které byste mohli chtít přidat do seznamu povolených adres, nebo je otevřete, pokud vaše organizace používá bránu firewall nebo proxy server
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
ms.openlocfilehash: 4058c75b2282b6fb77c3026c3667a470d6b9fd92
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476873"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalace a používání sady Visual Studio a služeb Azure za bránou firewall nebo proxy serverem

Pokud vy nebo vaše organizace používáte bezpečnostní opatření, jako je brána firewall nebo proxy server, pak jsou k dispozici adresy URL domény, které byste mohli chtít přidat do seznamu povolených portů a porty a protokoly, které byste mohli chtít otevřít, abyste měli k dispozici nejlepší prostředí při instalaci a používání nástroje.  Visual Studio a služby Azure.

* **[Instalace sady Visual Studio](#install-visual-studio)** : tyto tabulky obsahují adresy URL domény, které se mají přidat do seznamu povolených aplikací, abyste měli přístup ke všem komponentám a úlohám, které chcete.

* **[Použijte Visual Studio a služby Azure](#use-visual-studio-and-azure-services)** : Tato tabulka obsahuje adresy URL domény, které se mají přidat do seznamu povolených položek a porty a protokoly, které se mají otevřít, abyste měli přístup ke všem funkcím a službám, které chcete.

> [!NOTE]
> Tento článek byl napsán pro Visual Studio ve Windows, ale některé informace platí i pro [instalaci Visual Studio pro Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za bránou firewall nebo proxy server.

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL, které se mají přidat do seznamu povolených

Vzhledem k tomu, že Instalační program pro Visual Studio stahuje soubory z různých domén a jejich serverů pro stahování, tady jsou adresy URL domény, které byste mohli chtít přidat do seznamu povolených položek jako důvěryhodné v uživatelském rozhraní nebo ve skriptech nasazení.

#### <a name="microsoft-domains"></a>Microsoft domains

| Domain (Doména) | Účel |
| - | - |
| go.microsoft.com | Nastavení adresy URL řešení |
| aka.ms | Nastavení adresy URL řešení |
| download.visualstudio.microsoft.com | Nastavit umístění stahování balíčků |
| download.microsoft.com | Nastavit umístění stahování balíčků |
| download.visualstudio.com | Nastavit umístění stahování balíčků |
| dl.xamarin.com | Nastavit umístění stahování balíčků |
| xamarin-downloads.azureedge.net | Umístění seznamu pro stažení balíčků Android SDK |
| marketplace.visualstudio.com | Umístění pro stahování rozšíření sady Visual Studio |
| \*. gallerycdn.vsassets.io  | Umístění pro stahování rozšíření sady Visual Studio |
| VisualStudio.microsoft.com | Dokumentace k umístění |
| docs.microsoft.com | Dokumentace k umístění |
| msdn.microsoft.com | Dokumentace k umístění |
| Webová\.microsoft.com | Dokumentace k umístění |
| \*.windows.net | Místo přihlášení |
| \*.microsoftonline.com | Místo přihlášení |
| \*.live.com | Místo přihlášení |
| | |

#### <a name="non-microsoft-domains"></a>Domény od jiných výrobců

| Domain (Doména) | Nainstaluje tyto úlohy |
| - | - |
| archive.apache.org | Vývoj mobilních aplikací pomocí jazyka JavaScript (Cordova) |
| cocos2d-x.org | Vývoj her v C++ (Kokosové ostrovy) |
| download.epicgames.com | Vývoj her v C++ (Unreal Engine) |
| download.oracle.com | Vývoj mobilních aplikací pomocí jazyka JavaScript (Java SDK) <br /><br />Vývoj mobilních aplikací pomocí .NET (Java SDK) |
| download.unity3d.com | Vývoj her pomocí Unity (Unity) |
| netstorage.unity3d.com | Vývoj her pomocí Unity (Unity) |
| dl.google.com | Vývoj mobilních aplikací pomocí jazyka JavaScript (sady Android SDK a sada NDK, emulátor) <br /><br />Vývoj mobilních aplikací pomocí .NET (sady Android SDK a sada NDK, emulátor) |
| Webová\.incredibuild.com | Vývoj her v C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Vývoj her v C++ (IncrediBuild) |
| Webová\.python.org | Vývoj v jazyce Python (Python) <br /><br />Pro datové vědy a analytické aplikace (Python) |
| developerservices2.apple.com | Zřizování Xamarin. iOS |
| developer.apple.com | Zřizování Xamarin. iOS |
| appstoreconnect.apple.com | Zřizování Xamarin. iOS |
| idmsa.apple.com | Zřizování Xamarin. iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Použijte sadu Visual Studio a službami Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL, které se mají přidat do seznamu povolených a portů a protokolů k otevření

Pokud chcete mít jistotu, že máte přístup ke všemu, co potřebujete, když používáte Visual Studio nebo služby Azure za bránou firewall nebo proxy server, tady jsou adresy URL, které byste měli přidat do seznamu povolených položek, a porty a protokoly, které byste mohli chtít otevřít.

| Služba nebo scénáři | Koncový bod DNS | Protocol (Protokol) | Port | Popis |
| - | - | - | - | - |
| zprostředkovatele identity<br>řešení | go.microsoft.com<br><br>aka.ms | | | Používá ke zkrácení adresy URL, které se pak přeloží do delší adresy URL |
| Úvodní stránka | vsstartpage.blob.core.windows.net | | 443 | Slouží k zobrazení příspěvků vývojáře zobrazených na úvodní stránce (pouze Visual Studio 2017). |
| Cílem<br> Oznámení <br>Služba | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | | 443<br><br>443 | Slouží k filtrování globální seznam oznámení do seznamu, který se vztahuje pouze na konkrétní typy počítačů nebo použití scénáře |
| Linka <br>Kontrola aktualizací | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | | 443 | Používá k poskytování oznámení, když má nainstalovaná rozšíření k dispozici aktualizace. <br><br> Použít jako umístění přihlášení |
| Projekt AI <br>Integrace | az861674.vo.msecnd.net | | 443<br> | Slouží ke konfiguraci nových projektů k odesílání dat o využití do účtu registrované služby Application Insights |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | | 443 | Použít k zadání informací v editoru o poslední aktualizace souboru, na časové ose změn, pracovní položky, které jsou přidružené změny, autory a další |
| Experimentální <br>povolení funkce | visualstudio-devdiv-c2s.msedge.net | | 80 | Použít k aktivaci experimentální nové funkce nebo funkce změny |
| Identita "oznámení" BADGE "" <br>(uživatelské jméno a avatara)<br>a <br>Nastavení roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | | 443 | Slouží k zobrazení jméno a avatara uživatele v prostředí IDE <br><br> Používá k zajištění toho, že změny nastavení přesouvat z jednoho počítače do jiného |
| Nastavení vzdáleného přístupu | az700632.vo.msecnd.net | | 443 | Umožňuje vypnout rozšíření, které způsobují problémy v sadě Visual Studio |
| Nástroje pro Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | HTTPS | 443 | Používá pro scénáře Windows app store |
| Schéma JSON <br>Zjišťování <br><br>Schéma JSON <br>Definice<br><br>Schéma JSON <br>Podpora pro <br>Prostředky Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | HTTP<br>HTTPS<br><br>HTTP<br><br>HTTPS | 80<br>443 <br><br> 443<br><br>443 | Umožňuje vyhledat a stáhnout schémat JSON, které může uživatel používat při úpravách dokumentů JSON <br><br>Používá k získání meta-schéma pro formát JSON<br><br>Používá k získání aktuálního schématu pro šablony nasazení Azure Resource Manageru |
| Balíček NPM <br>zjištění | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | HTTPS<br><br>HTTP/s<br><br>HTTPS | 443<br><br>80/443<br><br>443 | Vyžaduje se pro vyhledávání balíčků NPM a použitý k instalaci balíčku skriptu na straně klienta v webové projekty |
| Balíčků bower<br> ikony<br><br>Balíčků bower <br>search | Bower.IO <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.IO | HTTP<br><br>HTTPS<br>HTTP<br>HTTPS | 80<br><br>443<br>80<br>443 | Poskytuje výchozí ikonu balíčku bower  <br><br>Umožňuje vyhledat balíčky Bower |
| NuGet<br><br>Balíček NuGet<br> zjištění | api.nuget.org <br>www.nuget.org <br>Nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | HTTPS<br><br>HTTP/s | 443<br><br>80/443<br> | Použít k ověření podepsané balíčky NuGet.<br><br>Vyžaduje se pro vyhledávání balíčků NuGet a verze |
| Informace o úložišti Githubu | api.github.com | HTTPS | 443 | Vyžaduje se pro získání dalších informací o balíčky bower |
| Linterů Web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | HTTP | 80 | |
| Cookiecutter<br>Průzkumník šablony<br>zjištění <br><br>Cookiecutter <br>Explorer project<br> Vytvoření | api.github.com <br>RAW.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | HTTPS | 443<br> | Používá se ke zjišťování online šablon z našeho doporučeného informačního kanálu a z úložišť GitHubu. <br><br>Umožňuje vytvořit projekt z šablony cookiecutter, která vyžaduje jednorázovou podle potřeby instalaci Pythonu balíčku cookiecutteru z indexu balíčků Pythonu (PyPI) |
| Balíček Pythonu <br>zjištění<br><br>Balíček Pythonu <br>správa<br><br>Nová <br>Python <br> project <br>šablon | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | HTTPS | 443 | Umožňuje vyhledat balíčky pip<br><br>Umožňuje automaticky instalovat modul pip, pokud není nalezena <br><br>Používá se k překladu následujících nových šablon projektů Pythonu na adresy URL šablon cookiecutter:<br> -Projekt klasifikace<br>-Projekt clusteringu <br> -Projekt regrese <br> -PyGame využívající PyKinect <br> -Projekt Pyvot |
| Office web <br>doplněk <br> Manifest <br>Ověření <br>Služba | verificationservice.osi.office.net | HTTPS | 443 | Používá se k ověření manifesty doplňků pro web Office |
| SharePoint a <br>Doplňky pro Office | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | HTTPS | 443 | Používá se k publikování a testování doplňků pro SharePoint a Office do SharePointu Online a Office 365. |
| Správce pracovních postupů <br>Testování služby<br> Hostitel | | HTTP | 12292 | Pravidlo brány firewall, která se automaticky vytvořily pro testování Sharepointových doplňků s pracovními postupy |
| Automaticky shromažďovat <br>spolehlivost statistiky <br>a další <br>Prostředí pro zákazníky <br>Programů zlepšování (uživatelů CEIP)<br> pro sadu Azure SDK a <br>nástroje SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | HTTPS | 443 | Používá k odeslání spolehlivost statistiky (při selhání a zablokování data) od uživatele společnosti Microsoft. Skutečné zhroucení nebo zablokování dumps budou odeslány stále, pokud je povoleno zasílání zpráv o chybách Windows; jenom statistické informace o potlačeno; <br>Umožňuje zobrazit vzory anonymní používání rozšíření Azure Tools SDK pro Visual Studio a vzorce používání SQL nástrojů sady Visual Studio |
| Visual Studio <br> Prostředí pro zákazníky <br>Program zlepšování softwaru a (uživatelů CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | HTTPS | 443 | Používá ke shromažďování anonymních vzorců používání a protokoly chyb <br><br>Slouží ke sledování problémů zablokování uživatelského rozhraní |
| Vytvoření a<br>Správa <br>Prostředky Azure | management.azure.com <br>management.core.windows.net | HTTPS | 443 | Použít pro vytvoření Azure Websites nebo další prostředky pro podporu publikování webových aplikací Azure Functions a WebJobs |
| Publikování aktualizované webové nástroje <br>kontroly a rozšíření <br>Doporučení | marketplace.visualstudio.com | HTTPS | 443 | Ke kontrole dostupnost aktualizovat nástroje pro publikování. Pokud je zakázané, se nemusí zobrazit potenciální doporučená rozšíření pro publikování na webu |
| Aktualizované prostředků Azure <br>Informace o vytvoření koncového bodu | \*.blob.core.windows.net | HTTPS | 443 | Použít k aktualizaci koncových bodů použitých pro vytváření prostředků Azure pro určité služby Azure. Pokud je zakázané, poslední stáhnout nebo součástí koncového bodu, který se místo toho používají umístění |
| Vzdálené ladění a <br>Vzdálené profilování <br>Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Používá se pro připojení vzdáleného ladicího programu na Azure Websites. Pokud je zakázané, nebudou fungovat připojení vzdáleného ladicího programu na Azure Websites |
| Active Directory <br>Graph | graph.windows.net | HTTPS | 443 | Používají ke zřízení nových aplikací Azure Active Directory. Také používá zprostředkovatel připojené služby Office 365 MSGraph- |
| Azure Functions <br>Aktualizace rozhraní příkazového řádku <br>Zaškrtnout | functionscdn.azureedge.net | HTTPS | 443 | Používá se pro kontrolu pro aktualizované verze Azure Functions CLI. Pokud je zakázané, kopie v mezipaměti (nebo kopii provádět součástí Azure Functions) rozhraní příkazového řádku se použije místo toho |
| Cordova | npmjs.org<br>gradle.org | HTTP/s | 80/443 | Protokol HTTP se používá pro Gradle stahování během sestavování; Protokol HTTPS se používá k zahrnout v projektech Cordova-Plugin |
| Průzkumník cloudu | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;koncový bod správy&#62;<br>Obecné cloudové Exp <br>3. &#60;koncový bod grafu&#62;<br>Obecné cloudové Exp<br>4. &#60;koncový bod účtu úložiště&#62;<br>Uzly úložiště <br>5. &#60;webu azure portal adresy URL&#62;<br>Obecné cloudové Exp <br>6. &#60;klíče trezoru koncových bodů&#62; <br>Uzly virtuálních počítačů Azure Resource Manageru<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric vzdálené ladění a trasování ETW | <br>1. protokol https<br>2. protokol https<br>3. protokol https<br>4. protokol https<br>5. protokol https<br>6. protokol https<br>7: tcp | 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dynamické | 1. Příklad: test12.eastus.cloudapp.com<br>2. načítá odběry a načítá nebo spravuje prostředky Azure.<br>3. načte Azure Stack předplatná<br>4. spravuje prostředky úložiště (například: mystorageaccount.blob.core.windows.net).<br>5. možnost otevřít v portálu kontextová nabídka (otevře prostředek v Azure Portal)<br>6. vytvoří a použije trezory klíčů pro ladění virtuálních počítačů (například: myvault.vault.azure.net). <br><br>7. dynamicky přiděluje blok portů na základě počtu uzlů v clusteru a dostupných portů. <br><br>Port blokování se pokusí získat třikrát počet uzlů s minimálně 10 portů.<br><br>Pro trasování streamování je proveden pokus o získání portu blok z 810. Pokud některý z tohoto bloku port je již použit, je proveden pokus o získání další blok, a tak dále. (Nástroj pro vyrovnávání zatížení je prázdný, pak se pravděpodobně používají porty z 810) <br><br>Podobně pro ladění, jsou vyhrazené čtyři sady bloků porty: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86: 31399,<br>-fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;uživatele cloudovou službu&#62;. cloudapp.net <br> &#60;user's VM&#62;.&#60;region&#62;.azure.com | 1. rdp <br><br> 2. protokol https <br><br> 3. protokol https <br><br> 4. protokol https <br><br> 5. protokol https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6.) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1. Vzdálená plocha pro Cloud Services virtuálního počítače <br><br> 2. součást účtu úložiště v konfiguraci privátní diagnostiky <br><br> 3. Azure Portal <br><br> 4. Průzkumník serveru-Azure Storage &#42; je zákazník nazvaný účet úložiště  <br><br> 5. odkazy na otevření portálu &#47; stáhnout soubor nastavení publikování certifikátu &#47; odběru <br><br>6.) konektoru místní port pro vzdálené ladění pro cloudovou službu a virtuálních počítačů<br> 6. b) konektoru veřejný port pro vzdálené ladění pro cloudovou službu a virtuálních počítačů <br> 6. c) předávání místní port pro vzdálené ladění pro cloudovou službu a virtuálních počítačů <br> 6. d) předávání veřejný port pro vzdálené ladění pro cloudovou službu a virtuálních počítačů  <br> 6. e) soubor uživatele nahrávajícího místní port pro vzdálené ladění pro cloudovou službu a virtuálních počítačů <br> 6. f) soubor uživatele nahrávajícího veřejný port pro vzdálené ladění pro cloudovou službu a virtuálních počítačů |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | HTTPS | 443 | 1. dokumentace <br><br> 2. vytvoření funkce clusteru <br><br>3. &#42; jedná se o název trezoru klíčů Azure (příklad:-test11220180112110108.Vault.Azure.NET  <br><br>  4. &#42; je dynamický (příklad: vsspsextprodch1su1.vsspsext.VisualStudio.com) |
| Snímek <br>Ladicí program | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;. azurewebsites.NET <br> 4. &#42;. SCM.azurewebsites.NET<br>5. api.nuget.org/v3/index.json <br>6. Vzdálená služba/servery IP adresa/plně kvalifikovaný název domény | 1. protokol https <br>2. protokol https  <br>3. http <br>4. protokol https <br>5. protokol https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (závislé verze sady visual Studio) | 1. soubor dotazu. JSON pro velikost SKU služby App Service <br>2. různá volání Azure RM <br>3. Web zahřívání volání prostřednictvím  <br>4. cílový App Service Kudu koncový bod zákazníka <br>5. dotazování verze rozšíření webu publikovaného v nuget.org <br>6. [vzdálené ladění](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | HTTPS | 443 | Slouží k zobrazení, odeslání, spouštět a spravovat úlohy Azure Stream Analytics <br><br> Umožňuje procházet clusterů Hdinsight a odešlete, Diagnostika a ladění úloh HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | HTTPS | 443 | Použít ke kompilaci, odeslat, zobrazení, Diagnostika a ladění úloh; Umožňuje procházet soubory ADLS; použít k nahrávání a stahování souborů |
| Vytváření balíčků služby | [account].visualstudio.com <br/> [účet].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> DIST.nuget.org <br/> Nuget.org | HTTPS | 443 | \*. npmjs.org, \*. nuget.org a \*. nodejs.org jsou požadovány pouze pro některé scénáře úloh sestavení (například instalační program nástroje NuGet, instalační program nástroje Node) nebo pokud máte v úmyslu použít veřejné nadřazené služby s vašimi informačními kanály. Tři domény jsou požadovány pro základní funkce služby balení. |
| Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | | Použít k připojení ke službám Azure DevOps |
| Komunita vývojářů | sendvsfeedback2.azurewebsites.net/api | HTTPS | 443 | Slouží k volání rozhraní API nástrojů pro zpětnou vazbu komunity vývojářů (moje problémy, hledání, hlasování, komentář, odeslání, nahrání, pokračování). |
| Intellicode | \*. intellicode.vsengsaas.visualstudio.com | HTTPS | 443 | Slouží k volání rozhraní Intellicode API. |
| Live Share | \*. liveshare.vsengsaas.visualstudio.com| HTTPS | 443 | Slouží k volání rozhraní API Live Share. |
| Visual Studio Online | \*. online.visualstudio.com | HTTPS | 443 | Používá se pro volání rozhraní API služby Visual Studio Online. |
| Automatické získání typu JavaScriptu | registry.npmjs.org | HTTPS | 443 | Slouží k instalaci definic typů TypeScript pro poskytování IntelliSense pro oblíbené knihovny JavaScriptu. |
| Licenční služba předplatných sady Visual Studio | app.vssps.visualstudio.com/apis/Licensing/ClientRights | HTTPS | 443 | Licencování pro online aktivaci |
| Ladicí program | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/OneCore.msvsmon.\*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | HTTPS | 443 | 1. <br>Používá se ke stahování bitů ladicího programu pro ladění .NET Core v systému UNIX/MacOS přes SSH. <br><br>2. <br>Používá se ke stahování bitů ladicího programu pro vzdálené ladění kontejneru Windows Docker.<br><br> 3. používá se pro krokování zdrojových prostředků .NET Framework <br><br> 4. <br>(Pokud uživatel výslovný) Používá se pro stahování symbolů publikovaných na serveru symbolů nuget.org.<br><br> 5. (Pokud se uživatel výslovný), který se používá pro stahování symbolů a binárních souborů MS, může být taky potřeba pro ladění spravovaného kódu ve výpisech paměti. |
| Visual Studio Online| \*. online.visualstudio.com | HTTPS | 443 | Používá se pro volání rozhraní API služby Visual Studio Online. |
| Publikování aplikace Xamarin Android | \*. googleapis.com <br/> play.google.com <br/>accounts.google.com | HTTPS | 443 | Slouží k interakci se službou Obchod Google Play k publikování a nahrávání aplikací pro Xamarin Android přímo ze sady Visual Studio. |
| Azure Container Registry | *. azurecr.io | HTTPS | 443 | Přístup k registrům kontejnerů hostovaným v Azure pro konfiguraci kanálů CICD |
| | | | | |

## <a name="troubleshoot-network-related-errors"></a>Řešení potíží s chybami související se sítí

V některých případech může být spustíte chyby související s sítě nebo proxy server při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server. Další informace o řešeních pro tyto chybové zprávy najdete v tématu [řešení potíží s chybami sítě při instalaci nebo použití stránky sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) .

## <a name="get-support"></a>Získat podporu

Nabízíme [**živý chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), který umožňuje problémy související s instalací.

Tady je několik dalších možností podpory:

* Nahlaste problémy s produktem prostřednictvím nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) , který se zobrazí v instalační program pro Visual Studio i v integrovaném vývojovém prostředí sady Visual Studio.
* Navrhněte funkci, Sledujte problémy s produkty a vyhledejte odpovědi v [komunitě vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/).
* Využijte svůj účet [GitHub](https://github.com/) ke komunikaci s námi a dalšími vývojáři sady Visual Studio v [konverzaci Visual studia v komunitě gitteru](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Viz také

* [Požadavky na připojení pro Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Řešení chyb souvisejících se sítí v aplikaci Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Nainstalovat za bránou firewall nebo proxy server (Visual Studio pro Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
