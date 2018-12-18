---
title: Vytváření aplikací ClickOnce z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: c9a9b2e248e4f10e9b5d3f045c67a9622edd2c2b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220014"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Vytváření aplikací ClickOnce z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], můžete sestavovat projekty z příkazového řádku, i když jsou vytvořeny v integrovaném vývojovém prostředí (IDE). Ve skutečnosti můžete znovu sestavit projekt vytvořený s [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] na jiném počítači, který má pouze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nainstalované. Díky tomu můžete pro reprodukci pomocí automatizovaného procesu sestavení, například v Centrální sestavení testovacího prostředí nebo pomocí pokročilé techniky nad rámec sestavení projektu, samotný skriptování.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Použití nástroje MSBuild pro reprodukci nasazení aplikací ClickOnce  
 Při vyvolání msbuild/target: publish na příkazovém řádku informuje systém MSBuild se projekt sestavil a vytvářet [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace ve složce publikování. Jedná se o ekvivalent pro výběr **publikovat** příkazu v integrovaném vývojovém prostředí.  
  
 Tento příkaz spustí msbuild.exe, který se nachází na cestu v příkazovém řádku prostředí sady Visual Studio.  
  
 "Cíl" je o tom, jak zpracovat příkaz indikátor nástroji MSBuild. Klíče cíle jsou cíl "sestavení" a "publikovat" target. Cíl sestavení je ekvivalentní k výběru sestavení v integrovaném vývojovém prostředí příkazu (nebo stisknutím klávesy F5). Pokud chcete svůj projekt sestavit, můžete toho dosáhnout zadáním `msbuild`. Tento příkaz funguje, protože cíl sestavení je výchozí cíl pro všechny projekty generovány podle [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. To znamená, že není potřeba explicitně zadat cíl sestavení. Proto se zadáním `msbuild` je stejné operace jako zadáním `msbuild /target:build`.  
  
 `/target:publish` Příkaz sděluje MSBuild, který má být vyvolán cíl publikování. Cíl publikování závisí na cíl sestavení. To znamená, že operace publikování je nadstavbou jazyka operace sestavení. Například pokud jste provedli změnu do jedné zdrojové soubory jazyka Visual Basic nebo C#, odpovídající sestavení by automaticky znovu sestavit pomocí operace publikování.  
  
 Informace o generování úplného [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení pomocí nástroje příkazového řádku Mage.exe k vytvoření vašeho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu naleznete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Vytvoření a vytvoření základní aplikace ClickOnce pomocí nástroje MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Vytvoření a publikování ClickOnce projektu  
  
1. Klikněte na tlačítko **nový projekt** z **souboru** nabídky. **Nový projekt** zobrazí se dialogové okno.  
  
2. Vyberte **aplikace Windows** a pojmenujte ho `CmdLineDemo`.  
  
3. Z **sestavení** nabídky, klikněte na tlačítko **publikovat** příkazu.  
  
    Tento krok zajistí, že projekt je správně nakonfigurované k vytvoření [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace.  
  
    Zobrazí se Průvodce publikováním.  
  
4. V Průvodci publikování klikněte na tlačítko **Dokončit**.  
  
    Visual Studio vygeneruje a zobrazí výchozí webová stránka volá Publish.htm.  
  
5. Uložte projekt a poznamenejte si umístění složky, ve kterém jsou uložená.  
  
   Výše uvedených kroků vytvořte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projektu, která byla publikována poprvé. Nyní můžete reprodukovat sestavení mimo rozhraní IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Chcete-li reprodukovat sestavení z příkazového řádku  
  
1. Ukončení [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. Z Windows **Start** nabídky, klikněte na tlačítko **všechny programy**, pak **sady Microsoft Visual Studio**, pak **Visual Studio Tools**, pak **Příkazový řádek sady visual Studio**. To by měl otevřete příkazový řádek v kořenové složce aktuálního uživatele.  
  
3. V **příkazový řádek sady Visual Studio**, změňte aktuální adresář na umístění projektu, který jste právě vytvořili. Zadejte například `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Chcete-li odebrat existující soubory vytvořené v "Vytvoření a publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projektu," typ `rmdir /s publish`.  
  
    Tento krok je volitelný, ale zajišťuje, že se nové soubory byly všechny vytvořený sestavením příkazového řádku.  
  
5. Typ `msbuild /target:publish`.  
  
   Výše uvedené kroky vytvoří úplný [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace v podsložce s názvem projektu **publikovat**. CmdLineDemo.application je [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení. Složka CmdLineDemo_1.0.0.0 obsahuje soubory CmdLineDemo.exe a CmdLineDemo.exe.manifest [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace. Setup.exe je zaváděcí nástroj, který ve výchozím nastavení je nastavena k instalaci [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. DotNetFX obsahuje distribuovatelné součásti pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Toto je celá sada soubory, které potřebujete k nasazení vaší aplikace prostřednictvím webu nebo název UNC nebo disk CD/DVD.  
  
## <a name="publishing-properties"></a>Vlastnosti publikování  
 Při publikování aplikace ve výše uvedených postupů následující vlastnosti jsou vloženy do souboru projektu pomocí Průvodce publikováním. Tyto vlastnosti přímo ovlivňují způsob, jakým [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace se vytvářejí.  
  
 V CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
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
  
 Některé z těchto vlastností příkazového řádku můžete přepsat beze změny samotného souboru projektu. Například následující staví [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace bez zaváděcího nástroje:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Vlastnosti publikování jsou řízeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z **publikovat**, **zabezpečení**, a **podepisování** stránek vlastností **Návrhář projektu** . Níže je uveden popis vlastnosti publikování, spolu s údajem o každé nastavení na různých stránkách vlastností návrháře aplikaci:  
  
- `AssemblyOriginatorKeyFile` Určuje soubor klíče používaný k podepisování vaší [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty aplikací. Stejný klíč lze také přiřadit silný název sestavení. Tato vlastnost nastavena na **podepisování** stránku **Návrháře projektu**.  
  
  Následující vlastnosti jsou nastaveny na **zabezpečení** stránky:  
  
- **Povolení nastavení zabezpečení ClickOnce** Určuje, zda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestů. Při počátečním vytvoření projektu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] generování manifestu je vypnuto ve výchozím nastavení. V Průvodci se automaticky zapne tento příznak Pokud publikujete poprvé.  
  
- **TargetZone** určuje úroveň důvěryhodnosti emitovat do vaší [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace. Možné hodnoty jsou "Internet", "LocalIntranet" a "Vlastní". Internet a LocalIntranet způsobí, že výchozí sadu oprávnění pro emitovat do vaší [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace. LocalIntranet je výchozí nastavení, a to v podstatě znamená, že úplný vztah důvěryhodnosti. Určuje, že pouze oprávnění, které jsou výslovně uvedené v souboru základní app.manifest se emitovat do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace. Soubor app.manifest se částečný soubor manifestu, který obsahuje jenom definice informace o vztahu důvěryhodnosti. Je skrytý soubor, automaticky přidá do vašeho projektu při konfiguraci oprávnění na **zabezpečení** stránky.  
  
  Následující vlastnosti jsou nastaveny na **publikovat** stránky:  
  
- `PublishUrl` je umístění, kde aplikace bude publikována v integrovaném vývojovém prostředí. Vložení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace, pokud `InstallUrl` nebo `UpdateUrl` je zadána vlastnost.  
  
- `ApplicationVersion` Určuje verzi modulu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Toto je verze čtyřmístné číslo. Pokud je poslední číslice "*", pak bude `ApplicationRevision` dosazeny hodnoty do manifestu vložen v okamžiku sestavení.  
  
- `ApplicationRevision` Určuje revizi. To je celé číslo, které zvýší pokaždé, když publikujete v integrovaném vývojovém prostředí. Všimněte si, že není automaticky zvýší pro sestavení provést na příkazovém řádku.  
  
- `Install` Určuje, zda je aplikace nainstalovaná aplikace nebo spuštění z webové aplikace.  
  
- `InstallUrl` (není vidět) je umístění, kde budou uživatelé instalovat aplikaci. -Li zadána, tato hodnota je zapsaný do zaváděcí nástroj setup.exe, pokud `IsWebBootstrapper` je povolena vlastnost. Je také vložit do manifestu aplikace, pokud `UpdateUrl` není zadán.  
  
- `SupportUrl` (není vidět) je umístění propojené v **přidat nebo odebrat programy** dialogové okno pro aplikace nainstalované.  
  
  Následující vlastnosti jsou nastaveny **aktualizace aplikace** dialogové okno, k němu přistupovat z **publikovat** stránky.  
  
- `UpdateEnabled` Určuje, zda by měla aplikace vyhledávat aktualizace.  
  
- `UpdateMode` Určuje popředí aktualizace nebo aktualizace na pozadí.  
  
- `UpdateInterval` Určuje, jak často by měla aplikace vyhledávat aktualizace.  
  
- `UpdateIntervalUnits` Určuje, zda `UpdateInterval` je hodnota v jednotkách, které hodin, dnů nebo týdnů.  
  
- `UpdateUrl` (není vidět) je umístění, ze které bude aplikace přijímat aktualizace. Je-li zadána, tato hodnota je vložen do manifestu aplikace.  
  
- Následující vlastnosti jsou nastaveny **možnosti publikování** dialogové okno, k němu přistupovat z **publikovat** stránky.  
  
- `PublisherName` Určuje název vydavatele zobrazí v řádku tento příkaz zobrazí při instalaci nebo spuštění aplikace. V případě aplikace nainstalované je také použít k určení názvu složky na **Start** nabídky.  
  
- `ProductName` Určuje název produktu, zobrazí v řádku tento příkaz zobrazí při instalaci nebo spuštění aplikace. V případě aplikace nainstalované je také použít k určení názvu odkazu na **Start** nabídky.  
  
- Následující vlastnosti jsou nastaveny **požadavky** dialogové okno, k němu přistupovat z **publikovat** stránky.  
  
- `BootstrapperEnabled` Určuje, jestli se má generovat setup.exe zaváděcí nástroj.  
  
- `IsWebBootstrapper` Určuje, zda funguje zaváděcí nástroj setup.exe prostřednictvím webu nebo v režimu na disku.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL a UpdateURL  
 V následující tabulce jsou uvedeny čtyři možnosti adresa URL pro nasazení ClickOnce.  
  
|Možnost adresy URL|Popis|  
|----------------|-----------------|  
|`PublishURL`|Povinné, pokud se publikování aplikace ClickOnce k webovému serveru.|  
|`InstallURL`|Volitelné. Tato adresa URL možnost nastavte, pokud se liší od instalace lokality `PublishURL`. Například můžete nastavit `PublishURL` skupinu a cesta k serveru FTP `InstallURL` na adresu URL webu.|  
|`SupportURL`|Volitelné. Tato adresa URL možnost nastavte, pokud se liší od webu podpory `PublishURL`. Například můžete nastavit `SupportURL` na webu podpory vaší společnosti zákazníka.|  
|`UpdateURL`|Volitelné. Tato adresa URL možnost nastavte, pokud se liší od umístění aktualizace `InstallURL`. Například můžete nastavit `PublishURL` skupinu a cesta k serveru FTP `UpdateURL` na adresu URL webu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



