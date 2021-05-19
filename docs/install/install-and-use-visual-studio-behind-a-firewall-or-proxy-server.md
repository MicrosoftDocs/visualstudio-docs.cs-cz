---
title: Instalace a použití za bránou firewall nebo proxy server
description: Zkontrolujte adresy URL domény, porty a protokoly, které můžete chtít přidat do seznamu povolení nebo otevřít, pokud vaše organizace používá bránu firewall nebo proxy server
ms.date: 05/07/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7e6df4c1e05d7f20ff59eeb3869947640942cedc
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973642"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalace a používání Visual Studio a služeb Azure za bránou firewall nebo proxy server

Pokud vy nebo vaše organizace používáte bezpečnostní opatření, jako je brána firewall nebo proxy server, pak existují adresy URL domény, které můžete chtít přidat do seznamu povolení a portů a protokolů, které můžete chtít otevřít, abyste měli nejlepší prostředí při instalaci a používání služeb Visual Studio a Azure.

* **[Install Visual Studio:](#install-visual-studio)** Tyto tabulky obsahují adresy URL domény, které se mají přidat do seznamu povolení, abyste měli přístup ke všem komponentám a úlohám, které chcete.

* Použít Visual Studio a **[služby Azure:](#use-visual-studio-and-azure-services)** Tato tabulka obsahuje adresy URL domény, které se mají přidat do seznamu povolení, a porty a protokoly, které se mají otevřít, abyste měli přístup ke všem funkcím a službám, které chcete.

> [!NOTE]
> Tento článek byl napsán Visual Studio ve Windows, ale některé informace platí také pro instalaci Visual Studio pro Mac [za](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) bránou firewall nebo proxy server.

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL, které se mají přidat do seznamu povolení

Vzhledem k tomu, Instalační program pro Visual Studio nástroj stahuje soubory z různých domén a jejich serverů pro stahování, tady jsou adresy URL domény, které můžete chtít přidat do seznamu povolení jako důvěryhodné v uživatelském rozhraní nebo ve skriptech nasazení.

#### <a name="microsoft-domains"></a>Domény Microsoftu

| Doména | Účel |
| - | - |
| go.microsoft.com | Nastavení překladu adres URL |
| aka.ms | Nastavení překladu adres URL |
| download.visualstudio.microsoft.com | Umístění pro stažení instalačních balíčků |
| download.microsoft.com | Umístění pro stažení instalačních balíčků |
| download.visualstudio.com | Umístění pro stažení instalačních balíčků |
| dl.xamarin.com | Umístění pro stažení instalačních balíčků |
| xamarin-downloads.azureedge.net | Umístění seznamu pro stažení balíčků Android SDK |
| marketplace.visualstudio.com | Umístění pro stažení rozšíření sady Visual Studio |
| \*. gallerycdn.vsassets.io  | Umístění pro stažení rozšíření sady Visual Studio |
| visualstudio.microsoft.com | Umístění dokumentace |
| docs.microsoft.com | Umístění dokumentace |
| msdn.microsoft.com | Umístění dokumentace |
| Webová \. Microsoft.com | Umístění dokumentace |
| \*.windows.net | Umístění pro přihlášení |
| \*.microsoftonline.com | Umístění pro přihlášení |
| \*.live.com | Umístění pro přihlášení |
| github-releases.githubusercontent.com | Vývoj pro Linux |
| az837173.vo.msecnd.net | Vývoj pomocí Azure Storage |
| | |

#### <a name="non-microsoft-domains"></a>Domény jiných společností než Microsoft

| Doména | Nainstaluje tyto úlohy. |
| - | - |
| archive.apache.org | Vývoj mobilních aplikací pomocí JavaScriptu (Cordova) |
| cocos2d-x.org | Vývoj her pomocí C++ (Cocos) |
| download.epicgames.com | Vývoj her pomocí C++ (Unreal Engine) |
| download.oracle.com | Vývoj mobilních aplikací pomocí JavaScriptu (Java SDK) <br /><br />Vývoj mobilních aplikací pomocí .NET (Java SDK) |
| download.unity3d.com | Vývoj her pomocí Unity (Unity) |
| netstorage.unity3d.com | Vývoj her pomocí Unity (Unity) |
| dl.google.com | Vývoj mobilních aplikací pomocí JavaScriptu (Android SDK a NDK, emulátor) <br /><br />Vývoj mobilních aplikací pomocí .NET (Android SDK a NDK, emulátor) |
| www \. – incredibuild.com | Vývoj her pomocí jazyka C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Vývoj her pomocí jazyka C++ (IncrediBuild) |
| www \. – python.org | Vývoj v Pythonu (Python) <br /><br />Aplikace pro datové vědy a analýzy (Python) |
| developerservices2.apple.com | Zřizování Xamarin. iOS |
| developer.apple.com | Zřizování Xamarin. iOS |
| appstoreconnect.apple.com | Zřizování Xamarin. iOS |
| idmsa.apple.com | Zřizování Xamarin. iOS |
| akamized.net | Content Delivery Network (technologie Akamai) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Použití sady Visual Studio a služeb Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL, které se mají přidat do seznamu povolených a portů a protokolů k otevření

Pokud chcete mít jistotu, že máte přístup ke všemu, co potřebujete, když používáte Visual Studio nebo služby Azure za bránou firewall nebo proxy server, tady jsou adresy URL, které byste měli přidat do seznamu povolených položek, a porty a protokoly, které byste mohli chtít otevřít.

| Služba nebo scénář | Koncový bod DNS | Protokol<br/>/Port | Popis |
| - | - | -: | - | - |
| URL<br>řešení | go.microsoft.com<br><br>aka.ms | | Slouží k zkrácení adres URL, které se pak předají do delších adres URL. |
| Úvodní stránka | vsstartpage.blob.core.windows.net | 443 | Slouží k zobrazení příspěvků vývojáře zobrazených na úvodní stránce (pouze Visual Studio 2017). |
| Targeted<br> Notification (Oznámení) <br>Služba | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Slouží k filtrování globálního seznamu oznámení na seznam, který se vztahuje pouze na konkrétní typy počítačů nebo scénářů použití. |
| Linka <br>kontrola aktualizací | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Slouží k poskytování oznámení, když má nainstalované rozšíření k dispozici aktualizaci. <br><br> Používá se jako přihlašovací umístění. |
| Projekt AI <br>Integrace | az861674.vo.msecnd.net | 443<br> | Slouží ke konfiguraci nových projektů pro odesílání dat o využití do registrovaného Application Insights účtu. |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Slouží k poskytování informací v editoru o tom, kdy byl soubor naposledy aktualizován, časové ose změn, pracovních položkách, ke které jsou změny přidruženy, o autorech a dalších položkách. |
| Experimentální <br>povolení funkce | visualstudio-devdiv-c2s.msedge.net | 80 | Slouží k aktivaci experimentálních nových funkcí nebo změn funkcí. |
| Identita "BADGE" <br>(uživatelské jméno a avatar)<br>a <br>Nastavení roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Slouží k zobrazení jména a miniatury uživatele v integrovaném vývojovém prostředí. <br><br> Slouží k zajištění, že nastavení změny roamingu z jednoho počítače na jiný. |
| Vzdálená nastavení | az700632.vo.msecnd.net | 443 | Slouží k vypnutí rozšíření, u kterých se říká, že způsobují problémy v aplikaci Visual Studio. |
| Nástroje systému Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Používá se pro scénáře Windows App Storu. |
| Schéma JSON <br>Zjišťování <br><br>Schéma JSON <br>Definice<br><br>Schéma JSON <br>Podpora pro <br>Prostředky Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Slouží ke zjišťování a stahování schémat JSON, která může uživatel použít při úpravách dokumentů JSON. <br><br>Slouží k získání schématu meta-validation pro JSON.<br><br>Slouží k získání aktuálního schématu pro šablony Azure Resource Manager nasazení. |
| Balíček NPM <br>zjišťování | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | Vyžaduje se pro hledání balíčků NPM a používá se pro instalaci balíčku skriptu na straně klienta ve webových projektech. |
| Balíček Bower<br> ikony<br><br>Balíček Bower <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Poskytuje výchozí ikonu balíčku Bower.  <br><br>Poskytuje možnost Hledat balíčky Bower |
| NuGet<br><br>Balíček NuGet<br> zjišťování | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | Slouží k ověření podepsaných balíčků NuGet.<br><br>Vyžaduje se pro vyhledávání balíčků a verzí NuGet. |
| Informace o úložišti GitHub | api.github.com | https/443 | Vyžaduje se pro získání dalších informací o balíčcích Bower. |
| Web Linters | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Cookiecutter<br>Šablona Průzkumníka<br>zjišťování <br><br>Cookiecutter <br>Projekt Průzkumníka<br> vytvořena | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Používá se ke zjišťování online šablon z našeho doporučeného informačního kanálu a z úložišť GitHubu. <br><br>Používá se k vytvoření projektu ze šablony cookiecutter, která vyžaduje jednorázovou instalaci cookiecutter sady Python na vyžádání z indexu balíčku Pythonu (PyPI). |
| Balíček Pythonu <br>zjišťování<br><br>Balíček Pythonu <br>správa<br><br>Nová <br>Python <br> projekt <br>šablony | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Poskytuje možnost Hledat balíčky PIP.<br><br>Používá se k automatické instalaci PIP, pokud chybí. <br><br>Používá se k překladu následujících nových šablon projektů Pythonu na adresy URL šablony cookiecutter:<br> – Projekt klasifikátoru<br>– Clustering Project <br> – Regresní projekt <br> – PyGame s využitím PyKinect <br> – Pyvot Project |
| Web Office <br>doplněk <br> Manifest <br>Ověření <br>Služba | verificationservice.osi.office.net | https/443 | Slouží k ověření manifestů pro webové doplňky Office. |
| SharePoint a <br>Doplňky pro Office | sharepoint.com<br> microsoft.com/microsoft-365<br> microsoftonline.com <br> outlook.com | https/443 | Slouží k publikování a testování doplňků pro SharePoint a Office na SharePointu Online a Microsoft 365 |
| Správce pracovních postupů <br>Testovací služba<br> Hostitel | | http/12292 | Pravidlo brány firewall, které se automaticky vytvoří pro testování doplňků pro SharePoint s pracovními postupy |
| Automaticky shromážděné <br>statistiky spolehlivosti <br>a jiné <br>Prostředí pro zákazníky <br>Programy zlepšování softwaru (CEIP)<br> pro sadu Azure SDK a <br>pro nástroje SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Slouží k odesílání statistik spolehlivosti (data o chybách/nereagujících) od uživatele do Microsoftu. Pokud je povoleno Zasílání zpráv o chybách systému Windows, budou odeslány skutečné výpisy chyb/nereagující. Potlačí se jenom statistické informace; <br>Slouží k odhalení způsobů využití rozšíření sady Azure Tools SDK pro sadu Visual Studio a ke vzorům využití pro nástroje SQL pro nástroj Visual Studio. |
| Visual Studio <br> Prostředí pro zákazníky <br>Program zlepšování softwaru (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Slouží ke shromažďování vzorů využití a protokolů chyb. <br><br>Slouží ke sledování problémů se zablokováním uživatelského rozhraní. |
| Vytvoření a<br>Správa služby <br>Prostředky Azure | management.azure.com <br>management.core.windows.net | https/443 | Používá se pro vytváření webů Azure nebo jiných prostředků pro podporu publikování webových aplikací, webových Azure Functions nebo webových úlohy. |
| Aktualizované nástroje pro publikování webu <br>kontroly a rozšíření <br>Doporučení | marketplace.visualstudio.com | https/443 | Slouží ke kontrole dostupnosti aktualizovaných nástrojů pro publikování. Pokud je zakázané, nemusí se zobrazit potenciální doporučené rozšíření pro publikování na webu. |
| Aktualizovaný prostředek Azure <br>Informace o vytvoření koncového bodu | \*.blob.core.windows.net | https/443 | Slouží k aktualizaci koncových bodů používaných k vytváření prostředků Azure pro určité služby Azure. Pokud je tato možnost zakázaná, použije se místo toho poslední stažená nebo integrovaná umístění koncových bodů. |
| Vzdálené ladění a <br>Vzdálené profilování <br>Azure websites | &#42;. cloudapp.net <br> &#42;. azurewebsites.net | 4022 | Slouží k připojení vzdáleného ladicího programu k Azure websites. Pokud je tato akce zakázaná, připojení vzdáleného ladicího programu k webům Azure nebude fungovat. |
| Active Directory <br>Graph | graph.windows.net | https/443 | Slouží ke zřízení nových aplikací Azure Active Directory. Používá se také Microsoft 365 poskytovatelem služeb připojeného k MSGraph. |
| Azure Functions <br>Aktualizace rozhraní příkazového řádku <br>Zaškrtnout | functionscdn.azureedge.net | https/443 | Používá se ke kontrole aktualizovaných verzí Azure Functions CLI. V případě zakázání se místo toho použije kopie v mezipaměti (nebo kopie převedená Azure Functions komponent) rozhraní příkazového řádku. |
| Cordova | npmjs.org<br>gradle.org | & http/80<br/>https/443 | HTTP se používá pro stahování Gradle během sestavování; Pomocí protokolu HTTPS se zahrnou moduly plug-in Cordova v projektech. |
| Průzkumník cloudu | 1. &#60;bod clusteru&#62; <br>Service Fabric <br>2. &#60;koncového bodu&#62;<br>General Cloud Exp <br>3. &#60;koncového bodu&#62;<br>General Cloud Exp<br>4. &#60;koncového bodu účtu&#62;<br>Uzly úložiště <br>5. &#60;Azure Portal adresy URL&#62;<br>General Cloud Exp <br>6. &#60;koncových bodů trezoru&#62; <br>Azure Resource Manager uzlů virtuálních počítače<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric vzdáleného ladění a trasování Trasování událostí pro Windows | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7. TCP/dynamická | 1. Příklad: test12.eastus.cloudapp.com<br>2. načítá odběry a načítá nebo spravuje prostředky Azure.<br>3. načte Azure Stack předplatná<br>4. spravuje prostředky úložiště (například: mystorageaccount.blob.core.windows.net).<br>5. možnost otevřít v portálu kontextová nabídka (otevře prostředek v Azure Portal)<br>6. vytvoří a použije trezory klíčů pro ladění virtuálních počítačů (například: myvault.vault.azure.net). <br><br>7. dynamicky přiděluje blok portů na základě počtu uzlů v clusteru a dostupných portů. <br><br>Blok portů se pokusí získat třikrát počet uzlů s minimálním počtem 10 portů.<br><br>Pro trasování streamování se provede pokus o získání bloku portů z 810. Pokud je již použit některý z těchto bloků portů, je proveden pokus o získání dalšího bloku a tak dále. (Nástroj pro vyrovnávání zatížení je prázdný, porty od 810 se pravděpodobně používají.) <br><br>Podobně jako u ladění jsou rezervované čtyři sady bloků portů: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86:31399,<br>-fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;cloudové služby uživatele&#62;.cloudapp.net <br> &#60;virtuálního počítače uživatele&#62;.&#60;a C3.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Připojení ke vzdálené ploše Cloud Services počítači <br><br> 2. Komponenta účtu úložiště v konfiguraci privátní diagnostiky <br><br> 3. Azure Portal <br><br> 4. Průzkumník serveru-Azure Storage &#42; je zákazníkem nazvaný účet úložiště  <br><br> 5. odkazy pro otevření portálu &#47; stáhnout certifikát odběru &#47; soubor nastavení publikování <br><br>6. a) konektor místní port pro vzdálené ladění pro cloudovou službu a virtuální počítač<br> 6. b) veřejný port konektoru pro vzdálené ladění pro cloudovou službu a virtuální počítač <br> 6. c) místní port pro přeposílání pro vzdálené ladění pro cloudovou službu a virtuální počítač <br> 6. d) veřejný port pro přeposílání pro vzdálené ladění pro cloudovou službu a virtuální počítač  <br> 6. e) místní port odeslání souboru pro vzdálené ladění pro cloudovou službu a virtuální počítač <br> 6. f) veřejný port odeslání souboru pro vzdálené ladění pro cloudovou službu a virtuální počítač |
| Service Fabric | 1. <br>doc. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42;. vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42;. visualstudio.com | https/443 | 1. Dokumentace <br><br> 2. Vytvoření funkce clusteru <br><br>3. &#42; je název trezoru klíčů Azure (příklad: – test11220180112110108.vault.azure.net  <br><br>  4. &#42; dynamické (příklad: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Snímek <br>Ladicí program | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.jsna <br>6. IP adresa/plně kvalifikovaný název domény vzdálené služby nebo serverů | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Předěl/<br> 4022 (Visual Studio verze) | 1. Dotazování na velikost SKU služby App Service v souboru .json <br>2. Různá volání Azure RM <br>3. Zahřejení lokality prostřednictvím  <br>4. cílový App Service Kudu koncový bod zákazníka <br>5. dotazování verze rozšíření webu publikovaného v nuget.org <br>6. [vzdálené ladění](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Slouží k zobrazení, odeslání, spuštění a správě úloh ASA. <br><br> Používá se k procházení clusterů HDI a odesílání, diagnostikování a ladění úloh HDI. |
| Azure Data Lake | &#42;. azuredatalakestore.net <br>&#42;. azuredatalakeanalytics.net | https/443 | Slouží ke kompilaci, odesílání, zobrazování, diagnostice a ladění úloh. používá se k procházení souborů ADLS. slouží k nahrání a stažení souborů. |
| Služba balení | [Account]. VisualStudio. com <br/> [účet]. \* . visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | Vlastnosti \* . npmjs.org, \* . NuGet.org a \* . NodeJS.org jsou vyžadovány pouze pro některé scénáře úloh sestavení (například instalační program nástroje NuGet, instalační program nástroje Node) nebo pokud máte v úmyslu použít veřejný nadřazený s vašimi kanály. Další tři domény jsou vyžadovány pro základní funkce služby vytváření balíčků. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Slouží k připojení k Azure DevOps Services |
| Azure Service Bus | \*.servicebus.windows.net | ampq/5671 a 5672, </br> sbmp/9350-9354, </br> http/80, </br> https/443 | Slouží k vytváření front, témat a odběrů. </br> Používá se také k odesílání a přijímání zpráv do a Service Bus front a témat. |
| Azure Cosmos DB | \*.documents.azure.com | https/443 | Slouží k volání základních rozhraní API databáze dokumentů. |
| Komunita vývojářů | sendvsfeedback2.azurewebsites.net/api | https/443 | Slouží k volání rozhraní API Developer Community Feedback Tool (moje problémy, hledání, hlasování, komentář, odeslání, nahrání, obnovení) |
| Intellicode | \*.intellicode.vsengsaas.visualstudio.com | https/443 | Slouží k volání rozhraní Intellicode API. |
| Live Share | \*. liveshare.vsengsaas.visualstudio.com| https/443 | Slouží k volání rozhraní API Live Share. |
| GitHub Codespaces | \*. online.visualstudio.com | https/443 | Slouží k volání rozhraní Codespaces API GitHubu. |
| Automatické získání typu JavaScriptu | registry.npmjs.org | https/443 | Slouží k instalaci definic typů TypeScript pro poskytování IntelliSense pro oblíbené knihovny JavaScriptu. |
| Licenční služba předplatných sady Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licencování/získal | https/443 | Licencování pro online aktivaci |
| Ladicí program | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>OneCore. msvsmon. \* .. věřitel<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Používá se ke stažení bitů ladicího programu pro ladění .NET Core v Unixu nebo macOS přes SSH. <br><br>2. <br>Slouží ke stahování bitů ladicího programu pro vzdálené ladění kontejnerů Dockeru ve Windows.<br><br> 3. Používá se pro krokování zdroje rozhraní .NET Framework. <br><br> 4. <br>(Pokud se uživatel přihlásí) Používá se ke stahování symbolů publikovaných nuget.org serveru symbolů.<br><br> 5. (Pokud se uživatel přihlásí) Používá se ke stahování symbolů MS a binárních souborů, může být také potřeba pro ladění spravovaného kódu ve výpisech paměti. |
| GitHub Codespaces| \*.online.visualstudio.com | https/443 | Slouží k volání rozhraní API Codespaces GitHubu. |
| Publikování aplikace Xamarin Android | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Používá se k interakci Obchod Google Play službou pro publikování a nahrávání aplikací Xamarin Android přímo z Visual Studio. |
| Visual Studio Search Service | data-ai.microsoft.com/search | https/443 | Slouží k zadání Search Service sady Visual Studio s podporou AI do `Ctrl+Q` vyhledávacího pole. |
| Azure Container Registry | *. azurecr.io | https/443 | Přístup k registrům kontejnerů hostovaným v Azure pro konfiguraci kanálů CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Řešení chyb souvisejících se sítí

V některých případech může při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server běžet chyba související se sítí nebo proxy serverem. Další informace o řešeních pro tyto chybové zprávy najdete v tématu [řešení potíží s chybami sítě při instalaci nebo použití stránky sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) .

## <a name="get-support"></a>Získání podpory

Nabízíme [**instalační chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), který umožňuje problémy související s instalací.

Tady je několik dalších možností podpory:

* Nahlaste problémy s produktem prostřednictvím nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) , který se zobrazí v instalační program pro Visual Studio i v integrovaném vývojovém prostředí sady Visual Studio.
* Navrhněte funkci, Sledujte problémy s produkty a vyhledejte odpovědi v [komunitě vývojářů sady Visual Studio](https://aka.ms/feedback/suggest?space=8).
* Využijte svůj účet [GitHub](https://github.com/) ke komunikaci s námi a dalšími vývojáři sady Visual Studio v [konverzaci Visual studia v komunitě gitteru](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Viz také

* [Požadavky na připojení pro Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Řešení chyb souvisejících se sítí v aplikaci Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Nainstalovat za bránou firewall nebo proxy server (Visual Studio pro Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
