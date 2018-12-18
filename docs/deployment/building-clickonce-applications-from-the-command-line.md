---
title: Vytváření aplikací ClickOnce z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1484466e3d1b1a43a6ff28c2526dbb478ef7392d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853282"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Vytváření aplikací ClickOnce z příkazového řádku
V [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], můžete sestavovat projekty z příkazového řádku, i když jsou vytvořeny v integrovaném vývojovém prostředí (IDE). Ve skutečnosti můžete znovu sestavit projekt vytvořený s [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] na jiném počítači, který má pouze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nainstalované. Díky tomu můžete pro reprodukci pomocí automatizovaného procesu sestavení, například v Centrální sestavení testovacího prostředí nebo pomocí pokročilé techniky nad rámec sestavení projektu, samotný skriptování.  
  
## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Použití nástroje MSBuild pro reprodukci nasazení aplikací ClickOnce  
 Při vyvolání msbuild/target: publish na příkazovém řádku informuje systém MSBuild se projekt sestavil a vytvářet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace ve složce publikování. Jedná se o ekvivalent pro výběr **publikovat** příkazu v integrovaném vývojovém prostředí.  
  
 Tento příkaz spustí *msbuild.exe*, což je na cestě v příkazovém řádku prostředí sady Visual Studio.  
  
 "Cíl" je o tom, jak zpracovat příkaz indikátor nástroji MSBuild. Klíče cíle jsou cíl "sestavení" a "publikovat" target. Cíl sestavení je ekvivalentní k výběru sestavení v integrovaném vývojovém prostředí příkazu (nebo stisknutím klávesy F5). Pokud chcete svůj projekt sestavit, můžete toho dosáhnout zadáním `msbuild`. Tento příkaz funguje, protože cíl sestavení je výchozí cíl pro všechny projekty generovány podle [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. To znamená, že není potřeba explicitně zadat cíl sestavení. Proto se zadáním `msbuild` je stejné operace jako zadáním `msbuild /target:build`.  
  
 `/target:publish` Příkaz sděluje MSBuild, který má být vyvolán cíl publikování. Cíl publikování závisí na cíl sestavení. To znamená, že operace publikování je nadstavbou jazyka operace sestavení. Například pokud jste provedli změnu do jedné zdrojové soubory jazyka Visual Basic nebo C#, odpovídající sestavení by automaticky znovu sestavit pomocí operace publikování.  
  
 Informace o generování úplného [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí nástroje příkazového řádku Mage.exe k vytvoření vašeho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu naleznete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Vytvoření a vytvoření základní aplikace ClickOnce pomocí nástroje MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Vytvoření a publikování ClickOnce projektu  
  
1. Klikněte na tlačítko **nový projekt** z **souboru** nabídky. **Nový projekt** zobrazí se dialogové okno.  
  
2. Vyberte **aplikace Windows** a pojmenujte ho `CmdLineDemo`.  
  
3. Z **sestavení** nabídky, klikněte na tlačítko **publikovat** příkazu.  
  
    Tento krok zajistí, že projekt je správně nakonfigurované k vytvoření [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace.  
  
    Zobrazí se Průvodce publikováním.  
  
4. V Průvodci publikování klikněte na tlačítko **Dokončit**.  
  
    Visual Studio vygeneruje a zobrazí výchozí webová stránka volá *Publish.htm*.  
  
5. Uložte projekt a poznamenejte si umístění složky, ve kterém jsou uložená.  
  
   Výše uvedených kroků vytvořte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu, která byla publikována poprvé. Nyní můžete reprodukovat sestavení mimo rozhraní IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Chcete-li reprodukovat sestavení z příkazového řádku  
  
1. Ukončení [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2. Z Windows **Start** nabídky, klikněte na tlačítko **všechny programy**, pak **sady Microsoft Visual Studio**, pak **Visual Studio Tools**, pak **Příkazový řádek sady visual Studio**. To by měl otevřete příkazový řádek v kořenové složce aktuálního uživatele.  
  
3. V **příkazový řádek sady Visual Studio**, změňte aktuální adresář na umístění projektu, který jste právě vytvořili. Zadejte například `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Chcete-li odebrat existující soubory vytvořené v "Vytvoření a publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu," typ `rmdir /s publish`.  
  
    Tento krok je volitelný, ale zajišťuje, že se nové soubory byly všechny vytvořený sestavením příkazového řádku.  
  
5. Typ `msbuild /target:publish`.  
  
   Výše uvedené kroky vytvoří úplný [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace v podsložce s názvem projektu **publikovat**. *CmdLineDemo.application* je [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu nasazení. Složka *CmdLineDemo_1.0.0.0* obsahuje soubory *CmdLineDemo.exe* a *CmdLineDemo.exe.manifest*, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace. *Setup.exe* je zaváděcí nástroj, který ve výchozím nastavení je nastavena k instalaci [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. DotNetFX obsahuje distribuovatelné součásti pro [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Toto je celá sada soubory, které potřebujete k nasazení vaší aplikace prostřednictvím webu nebo název UNC nebo disk CD/DVD.  
  
## <a name="publish-properties"></a>Publikovat vlastnosti  
 Při publikování aplikace ve výše uvedených postupů následující vlastnosti jsou vloženy do souboru projektu pomocí Průvodce publikováním. Tyto vlastnosti přímo ovlivňují způsob, jakým [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace se vytvářejí.  
  
 V *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*:  
  
```xml  
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
  
 Některé z těchto vlastností příkazového řádku můžete přepsat beze změny samotného souboru projektu. Například následující staví [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace bez zaváděcího nástroje:  
  
```cmd  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Vlastnosti publikování jsou řízeny v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z **publikovat**, **zabezpečení**, a **podepisování** stránek vlastností **Návrhář projektu** . Níže je uveden popis vlastnosti publikování, spolu s údajem o každé nastavení na různých stránkách vlastností návrháře aplikaci:  
  
- `AssemblyOriginatorKeyFile` Určuje soubor klíče používaný k podepisování vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty aplikací. Stejný klíč lze také přiřadit silný název sestavení. Tato vlastnost nastavena na **podepisování** stránku **Návrháře projektu**.  
  
  Následující vlastnosti jsou nastaveny na **zabezpečení** stránky:  
  
- **Povolení nastavení zabezpečení ClickOnce** Určuje, zda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestů. Při počátečním vytvoření projektu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generování manifestu je vypnuto ve výchozím nastavení. V Průvodci se automaticky zapne tento příznak Pokud publikujete poprvé.  
  
- **TargetZone** určuje úroveň důvěryhodnosti emitovat do vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace. Možné hodnoty jsou "Internet", "LocalIntranet" a "Vlastní". Internet a LocalIntranet způsobí, že výchozí sadu oprávnění pro emitovat do vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace. LocalIntranet je výchozí nastavení, a to v podstatě znamená, že úplný vztah důvěryhodnosti. Určuje vlastní pouze oprávnění, které jsou výslovně uvedené v základní třídě *app.manifest* se emitovat do souboru [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace. *App.manifest* soubor je částečný soubor manifestu, který obsahuje jenom definice informace o vztahu důvěryhodnosti. Je skrytý soubor, automaticky přidá do vašeho projektu při konfiguraci oprávnění na **zabezpečení** stránky.  
  
  Následující vlastnosti jsou nastaveny na **publikovat** stránky:  
  
- `PublishUrl` je umístění, kde aplikace bude publikována v integrovaném vývojovém prostředí. Vložení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikace, pokud `InstallUrl` nebo `UpdateUrl` je zadána vlastnost.  
  
- `ApplicationVersion` Určuje verzi modulu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. Toto je verze čtyřmístné číslo. Pokud je poslední číslice "*", pak bude `ApplicationRevision` dosazeny hodnoty do manifestu vložen v okamžiku sestavení.  
  
- `ApplicationRevision` Určuje revizi. To je celé číslo, které zvýší pokaždé, když publikujete v integrovaném vývojovém prostředí. Všimněte si, že není automaticky zvýší pro sestavení provést na příkazovém řádku.  
  
- `Install` Určuje, zda je aplikace nainstalovaná aplikace nebo spuštění z webové aplikace.  
  
- `InstallUrl` (není vidět) je umístění, kde budou uživatelé instalovat aplikaci. Je-li zadána, tato hodnota je zapsaný do *setup.exe* zaváděcí nástroj Pokud `IsWebBootstrapper` je povolena vlastnost. Je také vložit do manifestu aplikace, pokud `UpdateUrl` není zadán.  
  
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
  
- `BootstrapperEnabled` Určuje, jestli se má generovat *setup.exe* zaváděcího nástroje.  
  
- `IsWebBootstrapper` Určuje, zda *setup.exe* zaváděcí nástroj funguje prostřednictvím webu nebo v režimu na disku.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL a UpdateURL  
 V následující tabulce jsou uvedeny čtyři možnosti adresa URL pro nasazení ClickOnce.  
  
|Možnost adresy URL|Popis|  
|----------------|-----------------|  
|`PublishURL`|Povinné, pokud se publikování aplikace ClickOnce k webovému serveru.|  
|`InstallURL`|Volitelné. Tato adresa URL možnost nastavte, pokud se liší od instalace lokality `PublishURL`. Například můžete nastavit `PublishURL` skupinu a cesta k serveru FTP `InstallURL` na adresu URL webu.|  
|`SupportURL`|Volitelné. Tato adresa URL možnost nastavte, pokud se liší od webu podpory `PublishURL`. Například můžete nastavit `SupportURL` na webu podpory vaší společnosti zákazníka.|  
|`UpdateURL`|Volitelné. Tato adresa URL možnost nastavte, pokud se liší od umístění aktualizace `InstallURL`. Například můžete nastavit `PublishURL` skupinu a cesta k serveru FTP `UpdateURL` na adresu URL webu.|  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)