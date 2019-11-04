---
title: Instalace a použití za bránou firewall nebo proxy server
description: Zkontrolujte adresy URL, porty a protokoly, které byste mohli chtít přidat do seznamu povolených adres, nebo je otevřete, pokud vaše organizace používá bránu firewall nebo proxy server
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 12b8f29f80f80a4322dc6a4cf43061696db6f370
ms.sourcegitcommit: 4b911e768601992ad42dd5911dc6a01e1fe48588
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73413565"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Nainstalujte a použijte Visual Studio a služby Azure za bránou firewall nebo proxy server

Pokud vy nebo vaše organizace používáte bezpečnostní opatření, jako je brána firewall nebo proxy server, pak jsou k dispozici adresy URL domény, které byste mohli chtít přidat do seznamu povolených portů a porty a protokoly, které byste mohli chtít otevřít, abyste měli k dispozici nejlepší prostředí při instalaci a používání nástroje.  Visual Studio a služby Azure.

* **[Instalace sady Visual Studio](#install-visual-studio)** : tyto tabulky obsahují adresy URL domény, které se mají přidat do seznamu povolených aplikací, abyste měli přístup ke všem komponentám a úlohám, které chcete.

* **[Použijte Visual Studio a služby Azure](#use-visual-studio-and-azure-services)** : Tato tabulka obsahuje adresy URL domény, které se mají přidat do seznamu povolených položek a porty a protokoly, které se mají otevřít, abyste měli přístup ke všem funkcím a službám, které chcete.

> [!NOTE]
> Tento článek byl napsán pro Visual Studio ve Windows, ale některé informace platí i pro [instalaci Visual Studio pro Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) za bránou firewall nebo proxy server.

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Adresy URL, které se mají přidat do seznamu povolených

Vzhledem k tomu, že Instalační program pro Visual Studio stahuje soubory z různých domén a jejich serverů pro stahování, tady jsou adresy URL domény, které byste mohli chtít přidat do seznamu povolených položek jako důvěryhodné v uživatelském rozhraní nebo ve skriptech nasazení.

#### <a name="microsoft-domains"></a>Domény Microsoft

| Domain | Účel |
| - | - |
| go.microsoft.com | Nastavení překladu adresy URL |
| aka.ms | Nastavení překladu adresy URL |
| download.visualstudio.microsoft.com | Umístění pro stažení balíčků pro instalaci |
| download.microsoft.com | Umístění pro stažení balíčků pro instalaci |
| download.visualstudio.com | Umístění pro stažení balíčků pro instalaci |
| dl.xamarin.com | Umístění pro stažení balíčků pro instalaci |
| xamarin-downloads.azureedge.net | Umístění seznamu pro stažení balíčků Android SDK |
| marketplace.visualstudio.com | Umístění pro stažení rozšíření sady Visual Studio |
| visualstudio.microsoft.com | Umístění dokumentace |
| docs.microsoft.com | Umístění dokumentace |
| msdn.microsoft.com | Umístění dokumentace |
| Webová\.microsoft.com | Umístění dokumentace |
| \*. windows.net | Umístění pro přihlášení |
| \*. microsoftonline.com | Umístění pro přihlášení |
| \*. live.com | Umístění pro přihlášení |
| | |

#### <a name="non-microsoft-domains"></a>Domény jiných společností než Microsoft

| Domain | Nainstaluje tyto úlohy. |
| - | - |
| archive.apache.org | Vývoj pro mobilní zařízení pomocí JavaScriptu (Cordova) |
| cocos2d-x.org | Vývoj her v C++ (Cocos) |
| download.epicgames.com | Vývoj her pomocí C++ (modul Unreal) |
| download.oracle.com | Vývoj pro mobilní zařízení pomocí JavaScriptu (Java SDK) <br /><br />Vývoj pro mobilní zařízení pomocí .NET (Java SDK) |
| download.unity3d.com | Vývoj her pomocí Unity (Unity) |
| netstorage.unity3d.com | Vývoj her pomocí Unity (Unity) |
| dl.google.com | Vývoj pro mobilní zařízení pomocí JavaScriptu (Android SDK a NDK, emulátor) <br /><br />Vývoj pro mobilní zařízení pomocí .NET (Android SDK a NDK, emulátor) |
| Webová\.incredibuild.com | Vývoj her v C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Vývoj her v C++ (IncrediBuild) |
| Webová\.python.org | Vývoj v Pythonu (Python) <br /><br />Aplikace pro datové vědy a analýzy (Python) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Použití sady Visual Studio a služeb Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Adresy URL, které se mají přidat do seznamu povolených a portů a protokolů k otevření

Pokud chcete mít jistotu, že máte přístup ke všemu, co potřebujete, když používáte Visual Studio nebo služby Azure za bránou firewall nebo proxy server, tady jsou adresy URL, které byste měli přidat do seznamu povolených položek, a porty a protokoly, které byste mohli chtít otevřít.

| Služba nebo scénář | Koncový bod DNS | Protokol | Přístavní | Popis |
| - | - | - | - | - |
| Adresa URL<br>řešení | go.microsoft.com<br><br>aka.ms | | | Slouží k zkrácení adres URL, které se pak předají do delších adres URL. |
| Úvodní stránka | vsstartpage.blob.core.windows.net | | 443 | Slouží k zobrazení příspěvků vývojáře zobrazených na úvodní stránce (pouze Visual Studio 2017). |
| Cílová<br> Zveřejnění <br>Služba | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443 | Slouží k filtrování globálního seznamu oznámení do seznamu, který se vztahuje pouze na konkrétní typy počítačů nebo scénářů použití. |
| klapk <br>aktualizovat kontrolu | marketplace.visualstudio.com<br><br>&#42;. windows.net <br>&#42;. microsoftonline.com <br>&#42;. live.com | | 443 | Slouží k poskytování oznámení v případě, že je k dispozici aktualizace nainstalovaného rozšíření. <br><br> Používá se jako přihlašovací umístění. |
| Projekt AI <br>Integrace | az861674.vo.msecnd.net | | 443<br> | Slouží ke konfiguraci nových projektů k odesílání dat o využití do vašeho registrovaného Application Insights účtu. |
| Čočka kódu | codelensprodscus1su0. app.<br>codelens.visualstudio.com | | 443 | Slouží k zadání informací v editoru týkající se poslední aktualizace souboru, časové osy změn, pracovních položek, ke kterým jsou změny přidruženy, autorů a dalších. |
| Zkušební <br>povolení funkcí | visualstudio-devdiv-c2s.msedge.net | | 80 | Slouží k aktivaci experimentálních nových funkcí nebo změn funkcí. |
| Identita "BADGE" <br>(uživatelské jméno a avatar)<br>and <br>Nastavení roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net | | 443 | Slouží k zobrazení jména a miniatury uživatele v integrovaném vývojovém prostředí. <br><br> Slouží k zajištění, že nastavení změny roamingu z jednoho počítače na jiný. |
| Vzdálená nastavení | az700632.vo.msecnd.net | | 443 | Slouží k vypnutí rozšíření, u kterých se říká, že způsobují problémy v aplikaci Visual Studio. |
| Nástroje systému Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | Https | 443 | Používá se pro scénáře Windows App Storu. |
| Schéma JSON <br>Zjišťování <br><br>Schéma JSON <br>Definice<br><br>Schéma JSON <br>Podpora pro <br>Prostředky Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http<br>Https<br><br>http<br><br>Https | 80<br>443 <br><br> 443<br><br>443 | Slouží ke zjištění a stažení schémat JSON, která může uživatel použít při úpravách dokumentů JSON. <br><br>Slouží k získání schématu meta-ověření pro JSON.<br><br>Slouží k získání aktuálního schématu pro šablony nasazení Azure Resource Manager. |
| Balíček NPM <br>zjištění | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | Https<br><br>http/s<br><br>Https | 443<br><br>80/443<br><br>443 | Vyžaduje se pro hledání balíčků NPM a používá se pro instalaci balíčku skriptu na straně klienta ve webových projektech. |
| Balíček Bower<br> ikony<br><br>Balíček Bower <br>nápovědě | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>Https<br>http<br>Https | 80<br><br>443<br>80<br>443 | Poskytuje výchozí ikonu balíčku Bower.  <br><br>Poskytuje možnost Hledat balíčky Bower |
| NuGet<br><br>Balíček NuGet<br> zjištění | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | Https<br><br>http/s | 443<br><br>80/443<br> | Slouží k ověření podepsaných balíčků NuGet.<br><br>Vyžadováno pro hledání balíčků a verzí NuGet |
| Informace o úložišti GitHub | api.github.com | Https | 443 | Požadováno pro získání dalších informací o balíčcích Bower |
| Web Lintery | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http | 80 | |
| Cookiecutter<br>Šablona Průzkumníka<br>zjištění <br><br>Cookiecutter <br>Projekt Průzkumníka<br> Vytvořena | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | Https | 443<br> | Používá se ke zjišťování online šablon z našeho doporučeného informačního kanálu a z úložišť GitHubu. <br><br>Používá se k vytvoření projektu ze šablony cookiecutter, která vyžaduje jednorázovou instalaci cookiecutter sady Python na vyžádání z indexu balíčku Pythonu (PyPI). |
| Balíček Pythonu <br>zjištění<br><br>Balíček Pythonu <br>management<br><br>Nový <br>Python <br> projekt <br>šablony | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | Https | 443 | Poskytuje možnost Hledat balíčky PIP.<br><br>Používá se k automatické instalaci PIP, pokud chybí. <br><br>Používá se k překladu následujících nových šablon projektů Pythonu na adresy URL šablon cookiecutter:<br> – Projekt klasifikátoru<br>-Clustering – projekt <br> – Regresní projekt <br> – PyGame pomocí PyKinect <br> – Projekt Pyvot |
| Web Office <br>doplněk <br> Zřetel <br>Ověření <br>Služba | verificationservice.osi.office.net | Https | 443 | Slouží k ověření manifestů pro webové Doplňky Office. |
| SharePoint a <br>Doplňky pro Office | sharepoint.com | Https | 443 | Používá se k publikování a testování SharePointu a doplňků Office na SharePointu Online. |
| Správce pracovního postupu <br>Testovací služba<br> Hostitel | | http | 12292 | Pravidlo brány firewall, které se automaticky vytvoří pro testování doplňků pro SharePoint s pracovními postupy |
| Automaticky shromážděné <br>statistiky spolehlivosti <br>a jiné <br>Prostředí pro zákazníky <br>Programy zlepšování softwaru (CEIP)<br> pro sadu Azure SDK a <br>pro nástroje SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | Https | 443 | Slouží k odeslání statistiky spolehlivosti (data selhání/zablokování) od uživatele do Microsoftu. Pokud je povolený Zasílání zpráv o chybách systému Windows, budou se skutečné výpisy paměti a zablokování pořád nahrávat. Potlačí se jenom statistické informace; <br>Používá se k odhalení anonymních způsobů použití pro rozšíření sady Azure Tools SDK do sady Visual Studio a pro vzory využití nástrojů SQL pro Visual Studio. |
| Visual Studio <br> Prostředí pro zákazníky <br>Program zlepšování softwaru (CEIP) <br><br>PerfWatson. exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | Https | 443 | Slouží ke shromažďování anonymních způsobů používání a protokolů chyb. <br><br>Používá se ke sledování problémů zablokování uživatelského rozhraní. |
| Vytváření a<br>Správa <br>Prostředky Azure | management.azure.com <br>management.core.windows.net | Https | 443 | Používá se k vytváření webů Azure nebo jiných prostředků pro podporu publikování webových aplikací, Azure Functions a WebJobs. |
| Aktualizované nástroje publikování webu <br>kontroly a rozšíření <br>Doporučit | marketplace.visualstudio.com | Https | 443 | Používá se pro kontrolu dostupnosti aktualizovaných nástrojů pro publikování. Pokud je tato možnost zakázaná, nemusí se zobrazit možné Doporučené rozšíření pro publikování na webu. |
| Aktualizovaný prostředek Azure <br>Informace o vytvoření koncového bodu | \*. blob.core.windows.net | Https | 443 | Používá se k aktualizaci koncových bodů používaných k vytváření prostředků Azure pro určité služby Azure. Pokud je zakázané, místo toho se použije poslední stažený nebo sestavená umístění koncových bodů. |
| Vzdálené ladění a <br>Vzdálené profilování <br>Azure websites | &#42;. cloudapp.net <br> &#42;. azurewebsites.net | | 4022 | Slouží k připojení vzdáleného ladicího programu k Azure websites. Pokud je tato akce zakázaná, připojení vzdáleného ladicího programu k webům Azure nebude fungovat. |
| Služba Active Directory <br>Zapisovací | graph.windows.net | Https | 443 | Slouží ke zřízení nových aplikací Azure Active Directory. Používá se také poskytovatelem služby MSGraph, který je připojen k Office 365. |
| Azure Functions <br>Aktualizace rozhraní příkazového řádku <br>Zda | functionscdn.azureedge.net | Https | 443 | Používá se ke kontrole aktualizovaných verzí Azure Functions CLI. V případě zakázání se místo toho použije kopie v mezipaměti (nebo kopie převedená Azure Functions komponent) rozhraní příkazového řádku. |
| Cordova | npmjs.org<br>gradle.org | http/s | 80/443 | HTTP se používá pro stahování Gradle během sestavování; Pomocí protokolu HTTPS se zahrnou moduly plug-in Cordova v projektech. |
| Průzkumník cloudu | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;koncový bod správy&#62;<br>Obecné cloudové Expy <br>3. &#60;koncový bod grafu&#62;<br>Obecné cloudové Expy<br>4. &#60;koncový bod účtu úložiště&#62;<br>Uzly úložiště <br>5. &#60;Azure Portal adres URL&#62;<br>Obecné cloudové Expy <br>6. &#60;koncové body trezoru klíčů&#62; <br>Azure Resource Manager uzly virtuálních počítačů<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric vzdálené ladění a trasování ETW | <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7: TCP | 1.19080<br>2.443 <br>3.443 <br>4.443 <br>5.443 <br>6.443 <br>7. Dynamic | 1. Příklad: test12.eastus.cloudapp.com<br>2. načítá odběry a načítá nebo spravuje prostředky Azure.<br>3. načte Azure Stack předplatná<br>4. spravuje prostředky úložiště (například: mystorageaccount.blob.core.windows.net).<br>5. možnost otevřít v portálu kontextová nabídka (otevře prostředek v Azure Portal)<br>6. vytvoří a použije trezory klíčů pro ladění virtuálních počítačů (například: myvault.vault.azure.net). <br><br>7. dynamicky přiděluje blok portů na základě počtu uzlů v clusteru a dostupných portů. <br><br>Blok portů se pokusí získat třikrát počet uzlů s minimálním počtem 10 portů.<br><br>Pro trasování streamování se provede pokus o získání bloku portů z 810. Pokud je již použit některý z těchto bloků portů, je proveden pokus o získání dalšího bloku a tak dále. (Nástroj pro vyrovnávání zatížení je prázdný, porty od 810 se pravděpodobně používají.) <br><br>Podobně jako u ladění jsou rezervované čtyři sady bloků portů: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86:31399,<br>-fileUploadPort: 32398<br> |
| Cloudové služby | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;. blob.Core.Windows.NET <br>&#42;. queue.core.windows.net<br>&#42;. table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;cloudová služba&#62;uživatele. cloudapp.NET <br> &#60;virtuální počítač&#62;uživatele. &#60;region&#62;. Azure.com | 1. RDP <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. TCP | 1.3389 <br><br> 2.443 <br><br> 3.443 <br><br>4.443 <br><br>5.443 <br><br> 6. a) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1. Vzdálená plocha pro Cloud Services virtuálního počítače <br><br> 2. součást účtu úložiště v konfiguraci privátní diagnostiky <br><br> 3. Azure Portal <br><br> 4. Průzkumník serveru-Azure Storage &#42; je zákazník nazvaný účet úložiště  <br><br> 5. odkazy na otevření portálu &#47; stáhnout soubor nastavení publikování certifikátu &#47; odběru <br><br>6. a) konektor místní port pro vzdálené ladění pro cloudovou službu a virtuální počítač<br> 6. b) veřejný port konektoru pro vzdálené ladění pro cloudovou službu a virtuální počítač <br> 6. c) místní port pro přeposílání pro vzdálené ladění pro cloudovou službu a virtuální počítač <br> 6. d) veřejný port pro přeposílání pro vzdálené ladění pro cloudovou službu a virtuální počítač  <br> 6. e) místní port odeslání souboru pro vzdálené ladění pro cloudovou službu a virtuální počítač <br> 6. f) veřejný port odeslání souboru pro vzdálené ladění pro cloudovou službu a virtuální počítač |
| Service Fabric | 1. <br>OCS. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; Vault.Azure.NET<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42;. vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42;. visualstudio.com | Https | 443 | 1. dokumentace <br><br> 2. vytvoření funkce clusteru <br><br>3. &#42; jedná se o název trezoru klíčů Azure (příklad:-test11220180112110108.Vault.Azure.NET  <br><br>  4. &#42; je dynamický (příklad: vsspsextprodch1su1.vsspsext.VisualStudio.com) |
| Snímek <br>Ladicí program | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.NET <br> 4. &#42;SCM.azurewebsites.NET<br>5. api.nuget.org/v3/index.json <br>6. msvsmon (. exe) | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1.443<br> 2.443<br>3.80  <br>4.443<br> 5.443<br> 6.4022 (závislá verze sady Visual Studio) | 1. soubor dotazu. JSON pro velikost SKU služby App Service <br>2. různá volání Azure RM <br>3. Web zahřívání volání prostřednictvím  <br>4. cílový App Service Kudu koncový bod zákazníka <br>5. dotazování verze rozšíření webu publikovaného v nuget.org <br>6. kanál vzdáleného ladění |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | Https | 443 | Slouží k zobrazení, odeslání, spuštění a správě úloh ASA. <br><br> Používá se k procházení clusterů HDI a odesílání, diagnostikování a ladění úloh HDI. |
| Azure Data Lake | &#42;. azuredatalakestore.net <br>&#42;. azuredatalakeanalytics.net | Https | 443 | Slouží ke kompilaci, odesílání, zobrazování, diagnostice a ladění úloh. používá se k procházení souborů ADLS. slouží k nahrání a stažení souborů. |
| Služba balení | [Account]. VisualStudio. com <br/> [účet].\*. visualstudio.com <br/> \*. blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | Https | 443 | \*. npmjs.org, \*. nuget.org a \*. nodejs.org jsou požadovány pouze pro některé scénáře úloh sestavení (například instalační program nástroje NuGet, instalační program nástroje Node) nebo pokud máte v úmyslu použít veřejné nadřazené služby s vašimi informačními kanály. Další tři domény jsou vyžadovány pro základní funkce služby vytváření balíčků. |
| Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | | Slouží k připojení pomocí Azure DevOps Services |
| | | | | |

## <a name="troubleshoot-network-related-errors"></a>Řešení chyb souvisejících se sítí

V některých případech může při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server běžet chyba související se sítí nebo proxy serverem. Další informace o řešeních pro tyto chybové zprávy najdete v tématu [řešení potíží s chybami sítě při instalaci nebo použití stránky sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) .

## <a name="get-support"></a>Získat podporu

Nabízíme [**živý chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), který umožňuje problémy související s instalací.

Tady je několik dalších možností podpory:

* Nahlaste problémy s produktem prostřednictvím nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) , který se zobrazí v instalační program pro Visual Studio i v integrovaném vývojovém prostředí sady Visual Studio.
* Navrhněte funkci, Sledujte problémy s produkty a vyhledejte odpovědi v [komunitě vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/).
* Využijte svůj účet [GitHub](https://github.com/) ke komunikaci s námi a dalšími vývojáři sady Visual Studio v [konverzaci Visual studia v komunitě gitteru](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Viz také:

* [Požadavky na připojení pro Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Řešení chyb souvisejících se sítí v aplikaci Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Nainstalovat za bránou firewall nebo proxy server (Visual Studio pro Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
