---
title: Vytváření aplikací ClickOnce z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2625a8d4caa7dd53e9ce86395a98622f91d686b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155710"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Vytváření aplikací ClickOnce z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V nástroji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] můžete sestavit projekty z příkazového řádku, i když jsou vytvořeny v integrovaném vývojovém prostředí (IDE). Ve skutečnosti můžete znovu sestavit projekt vytvořený pomocí nástroje [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] v jiném počítači, který má pouze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nainstalovaný. To umožňuje reprodukování sestavení pomocí automatizovaného procesu, například v centrálním vývojovém prostředí, nebo pomocí pokročilých skriptovacích technik nad rámec sestavování samotného projektu.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Použití nástroje MSBuild k reprodukování nasazení aplikace ClickOnce  
 Když vyvoláte MSBuild/target: Publish na příkazovém řádku, sdělí systému MSBuild, aby projekt sestavil a vytvořil [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci ve složce pro publikování. Jedná se o ekvivalent výběru příkazu **publikovat** v integrovaném vývojovém prostředí (IDE).  
  
 Tento příkaz provede msbuild.exe, který je v cestě v prostředí příkazového řádku sady Visual Studio.  
  
 "Target" je indikátorem pro MSBuild, jak zpracovat příkaz. Klíčové cíle jsou cíle "Build" a cíl "publikovat". Cíl sestavení je ekvivalentem výběru příkazu Build (nebo stisknutím klávesy F5) v integrovaném vývojovém prostředí (IDE). Pokud chcete projekt sestavit pouze, můžete to dosáhnout zadáním `msbuild` . Tento příkaz funguje, protože cíl sestavení je výchozí cíl pro všechny projekty generované [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . To znamená, že nemusíte explicitně zadat cíl sestavení. Proto je psaní `msbuild` stejná operace jako při psaní `msbuild /target:build` .  
  
 `/target:publish`Příkaz instruuje nástroj MSBuild, aby vyvolal cíl publikování. Cíl publikování závisí na cíli sestavení. To znamená, že operace publikování je nadmnožinou operace sestavení. Například pokud jste provedli změnu jednoho ze zdrojových souborů Visual Basic nebo C#, odpovídající sestavení bude automaticky znovu sestavena operací publikování.  
  
 Informace o generování úplného [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení pomocí Mage.exe nástroje příkazového řádku pro vytvoření [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Vytvoření a sestavení základní aplikace ClickOnce pomocí nástroje MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Vytvoření a publikování projektu ClickOnce  
  
1. V nabídce **soubor** klikněte na **Nový projekt** . Zobrazí se dialogové okno **Nový projekt**.  
  
2. Vyberte **aplikace systému Windows** a pojmenujte ji `CmdLineDemo` .  
  
3. V nabídce **sestavení** klikněte na příkaz **publikovat** .  
  
    Tento krok zajistí, že je projekt správně nakonfigurovaný pro vytvoření [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace.  
  
    Zobrazí se Průvodce publikováním.  
  
4. V průvodci publikování klikněte na **Dokončit**.  
  
    Visual Studio vygeneruje a zobrazí výchozí webovou stránku nazvanou Publish.htm.  
  
5. Uložte projekt a poznamenejte si umístění složky, ve kterém je uložený.  
  
   Výše uvedený postup vytvoří [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projekt, který byl poprvé publikován. Nyní můžete sestavení reprodukována mimo rozhraní IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Pro reprodukování sestavení z příkazového řádku  
  
1. Ukončete [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
2. V nabídce **Start** systému Windows klikněte na **všechny programy**a pak **Microsoft Visual Studio**a pak **Visual Studio Tools**a příkazový **řádek Visual Studio**. To by mělo otevřít příkazový řádek v kořenové složce aktuálního uživatele.  
  
3. V **příkazovém řádku sady Visual Studio**změňte aktuální adresář na umístění projektu, který jste právě vytvořili. Zadejte například název `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Chcete-li odebrat existující soubory vytvořené v "pro vytvoření a publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projektu", "type `rmdir /s publish` .  
  
    Tento krok je nepovinný, ale zajišťuje, že se nové soubory vytvořily v sestavení příkazového řádku.  
  
5. Zadejte příkaz `msbuild /target:publish`.  
  
   Výše uvedené kroky vytvoří úplné [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace v podsložce projektu s názvem **Publish**. CmdLineDemo. Application je [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest nasazení. Složka CmdLineDemo_1.0.0.0 obsahuje soubory CmdLineDemo.exe a CmdLineDemo.exe. manifest, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace. Setup.exe je zaváděcí nástroj, který je ve výchozím nastavení nakonfigurován pro instalaci [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Složka DotNetFX obsahuje distribuovatelné součásti pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Toto je celá sada souborů, kterou potřebujete k nasazení aplikace přes web nebo přes UNC nebo CD/DVD.  
  
## <a name="publishing-properties"></a>Vlastnosti publikování  
 Při publikování aplikace ve výše uvedených postupech jsou následující vlastnosti vloženy do souboru projektu pomocí Průvodce publikováním. Tyto vlastnosti mají přímo vliv na to, jak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je aplikace vytvořená.  
  
 V CmdLineDemo. vbproj/CmdLineDemo. csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Jakoukoli z těchto vlastností můžete přepsat na příkazovém řádku bez změny samotného souboru projektu. Následující příklad vytvoří [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace bez zaváděcího nástroje:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Vlastnosti publikování jsou ovládány [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na stránkách **vlastností publikování**, **zabezpečení**a **podepisování** v **Návrháři projektu**. Níže je uveden popis vlastností publikování spolu s uvedením toho, jak jsou jednotlivé vlastnosti nastaveny na různých stránkách vlastností návrháře aplikace:  
  
- `AssemblyOriginatorKeyFile` Určuje soubor klíče, který se používá k podepsání [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestů aplikace. Stejný klíč lze také použít k přiřazení silného názvu sestavením. Tato vlastnost je nastavena na stránce **podepisování** v **Návrháři projektu**.  
  
  Na stránce **zabezpečení** jsou nastaveny následující vlastnosti:  
  
- **Povolit nastavení zabezpečení ClickOnce** určuje, jestli [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jsou vygenerované manifesty. Při počátečním vytvoření projektu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je generování manifestu ve výchozím nastavení vypnuto. Průvodce automaticky zapne tento příznak při prvním publikování.  
  
- **TargetZone** určuje úroveň důvěryhodnosti, která se má vygenerovat do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace. Možné hodnoty jsou "Internet", "LocalIntranet" a "vlastní". Internet a LocalIntranet způsobí, že se do manifestu aplikace pošle výchozí nastavení oprávnění [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . LocalIntranet je výchozí a v podstatě znamená úplný vztah důvěryhodnosti. Vlastní určuje, že do manifestu aplikace budou generována pouze oprávnění explicitně zadaná v souboru manifestu základní aplikace. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Soubor App. manifest je částečný soubor manifestu, který obsahuje jenom definice informací o důvěryhodnosti. Jedná se o skrytý soubor, který se automaticky přidá do projektu při konfiguraci oprávnění na stránce **zabezpečení** .  
  
  Na stránce **publikovat** jsou nastaveny následující vlastnosti:  
  
- `PublishUrl` je umístění, do kterého bude aplikace publikována v integrovaném vývojovém prostředí. Je vložen do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace, pokud `InstallUrl` `UpdateUrl` není zadána vlastnost nebo.  
  
- `ApplicationVersion` Určuje verzi [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Toto je číslo verze se čtyřmi číslicemi. Pokud je poslední číslice "*", pak `ApplicationRevision` je nahrazena hodnotou vloženou do manifestu v čase sestavení.  
  
- `ApplicationRevision` Určuje revizi. Toto je celé číslo, které zvýší pokaždé, když publikujete v integrovaném vývojovém prostředí. Všimněte si, že se automaticky nezvyšuje pro sestavení prováděná na příkazovém řádku.  
  
- `Install` Určuje, zda je aplikace nainstalovaná aplikace nebo aplikace spouštěná z webu.  
  
- `InstallUrl` (nezobrazený) je umístění, ze kterého budou uživatelé aplikaci instalovat. Je-li tento parametr zadán, je tato hodnota vypálena do zaváděcího nástroje setup.exe, pokud `IsWebBootstrapper` je vlastnost povolena. Je-li zadána, je také vložen do manifestu aplikace `UpdateUrl` .  
  
- `SupportUrl` (nezobrazený) je umístění propojené v dialogovém okně **Přidat nebo odebrat programy** nainstalované aplikace.  
  
  Následující vlastnosti jsou nastaveny v dialogovém okně **aktualizace aplikace** , ke kterým se dostanete ze stránky **publikování** .  
  
- `UpdateEnabled` Určuje, zda má aplikace vyhledat aktualizace.  
  
- `UpdateMode` Určuje aktualizace popředí nebo aktualizace na pozadí.  
  
- `UpdateInterval` Určuje, jak často by měla aplikace vyhledávat aktualizace.  
  
- `UpdateIntervalUnits` Určuje, zda `UpdateInterval` je hodnota v jednotkách hodiny, dny nebo týdny.  
  
- `UpdateUrl` (nezobrazený) je umístění, ze kterého bude aplikace přijímat aktualizace. Je-li tento parametr zadán, je tato hodnota vložena do manifestu aplikace.  
  
- Následující vlastnosti jsou nastaveny v dialogovém okně **Možnosti publikování** , ke kterým se dostanete ze stránky **publikování** .  
  
- `PublisherName` Určuje název vydavatele zobrazeného na příkazovém řádku, který se zobrazí při instalaci nebo spuštění aplikace. V případě nainstalované aplikace se také používá k určení názvu složky v nabídce **Start** .  
  
- `ProductName` Určuje název produktu zobrazený v příkazovém řádku, který se zobrazí při instalaci nebo spuštění aplikace. V případě nainstalované aplikace se také používá k zadání názvu zástupce v nabídce **Start** .  
  
- Následující vlastnosti jsou nastaveny v dialogovém okně **předpoklady** , ke kterým se přistupoval ze stránky **publikování** .  
  
- `BootstrapperEnabled` Určuje, zda se má generovat setup.exe zaváděcí nástroj.  
  
- `IsWebBootstrapper` Určuje, zda setup.exe zaváděcí nástroj funguje na webu nebo v režimu na disku.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL a UpdateURL  
 V následující tabulce jsou uvedeny čtyři možnosti adresy URL pro nasazení ClickOnce.  
  
|Možnost adresy URL|Popis|  
|----------------|-----------------|  
|`PublishURL`|Vyžaduje se, pokud publikujete aplikaci ClickOnce na web.|  
|`InstallURL`|Nepovinný parametr. Tuto možnost adresy URL nastavte, pokud se instalační web liší od `PublishURL` . Můžete například nastavit `PublishURL` cestu k serveru FTP a nastavit na `InstallURL` adresu URL webu.|  
|`SupportURL`|Nepovinný parametr. Tuto možnost adresy URL nastavte, pokud se web podpory liší od `PublishURL` . Můžete například nastavit na `SupportURL` Web zákaznická podpora vaší společnosti.|  
|`UpdateURL`|Nepovinný parametr. Nastavte tuto možnost adresy URL, pokud se umístění aktualizace liší od `InstallURL` . Můžete například nastavit `PublishURL` cestu k serveru FTP a nastavit na `UpdateURL` adresu URL webu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
