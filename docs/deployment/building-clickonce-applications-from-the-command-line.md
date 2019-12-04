---
title: Vytváření aplikací ClickOnce z příkazového řádku | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797197"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Vytváření aplikací ClickOnce z příkazového řádku
V [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]můžete sestavit projekty z příkazového řádku, a to i v případě, že jsou vytvořeny v integrovaném vývojovém prostředí (IDE). Ve skutečnosti můžete znovu sestavit projekt vytvořený pomocí [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] v jiném počítači, který má pouze nainstalovaný .NET Framework. To umožňuje reprodukování sestavení pomocí automatizovaného procesu, například v centrálním vývojovém prostředí, nebo pomocí pokročilých skriptovacích technik nad rámec sestavování samotného projektu.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Použití nástroje MSBuild k reprodukování nasazení aplikace ClickOnce
 Když vyvoláte MSBuild/target: Publish na příkazovém řádku, systém MSBuild určí, že projekt sestaví a vytvoří aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve složce pro publikování. Jedná se o ekvivalent výběru příkazu **publikovat** v integrovaném vývojovém prostředí (IDE).

 Tento příkaz spustí nástroj *MSBuild. exe*, který je v cestě v prostředí příkazového řádku sady Visual Studio.

 "Target" je indikátorem pro MSBuild, jak zpracovat příkaz. Klíčové cíle jsou cíle "Build" a cíl "publikovat". Cíl sestavení je ekvivalentem výběru příkazu Build (nebo stisknutím klávesy F5) v integrovaném vývojovém prostředí (IDE). Pokud chcete projekt sestavit pouze, můžete to dosáhnout zadáním `msbuild`. Tento příkaz funguje, protože cíl sestavení je výchozí cíl pro všechny projekty generované [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. To znamená, že nemusíte explicitně zadat cíl sestavení. Proto je zadání `msbuild` stejné operaci jako při zadávání `msbuild /target:build`.

 Příkaz `/target:publish` instruuje nástroj MSBuild, aby vyvolal cíl publikování. Cíl publikování závisí na cíli sestavení. To znamená, že operace publikování je nadmnožinou operace sestavení. Například pokud jste provedli změnu některého z vašich Visual Basic nebo C# zdrojových souborů, odpovídající sestavení bude automaticky znovu sestavena operací publikování.

 Informace o generování úplného nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí nástroje příkazového řádku Mage. exe pro vytvoření manifestu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Vytvoření a sestavení základní aplikace ClickOnce pomocí nástroje MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Vytvoření a publikování projektu ClickOnce

1. Otevřete Visual Studio a vytvořte nový projekt.

    Vyberte šablonu projektu **desktopová aplikace pro Windows** a pojmenujte projekt `CmdLineDemo`.

1. V nabídce **sestavení** klikněte na příkaz **publikovat** .

    Tento krok zajistí, že je projekt správně nakonfigurovaný tak, aby vytvořil nasazení aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

    Zobrazí se Průvodce publikováním.

1. V průvodci publikování klikněte na **Dokončit**.

    Visual Studio vygeneruje a zobrazí výchozí webovou stránku nazvanou *Publish. htm*.

1. Uložte projekt a poznamenejte si umístění složky, ve kterém je uložený.

   Výše uvedené kroky vytvoří projekt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], který byl poprvé publikován. Nyní můžete sestavení reprodukována mimo rozhraní IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Pro reprodukování sestavení z příkazového řádku

1. Konec [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. V nabídce **Start** systému Windows klikněte na **všechny programy**a pak **Microsoft Visual Studio**a pak **Visual Studio Tools**a příkazový **řádek Visual Studio**. To by mělo otevřít příkazový řádek v kořenové složce aktuálního uživatele.

3. V **příkazovém řádku sady Visual Studio**změňte aktuální adresář na umístění projektu, který jste právě vytvořili. Zadejte například příkaz `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Chcete-li odebrat existující soubory vytvořené v "k vytvoření a publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu", zadejte `rmdir /s publish`.

    Tento krok je nepovinný, ale zajišťuje, že se nové soubory vytvořily v sestavení příkazového řádku.

5. Typ `msbuild /target:publish`.

   Výše uvedené kroky vytvoří úplné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace v podsložce projektu s názvem **Publish**. *CmdLineDemo. Application* je manifest nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Složka *CmdLineDemo_1.0.0.0* obsahuje soubory *CmdLineDemo. exe* a *CmdLineDemo. exe. manifest*, manifest aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. *Setup. exe* je zaváděcí nástroj, který je ve výchozím nastavení nakonfigurován pro instalaci .NET Framework. Složka DotNetFX obsahuje distribuovatelné součásti pro .NET Framework. Toto je celá sada souborů, kterou potřebujete k nasazení aplikace přes web nebo přes UNC nebo CD/DVD.
   
> [!NOTE]
> Systém MSBuild používá možnost **PublishDir** k určení umístění pro výstup, například `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Vlastnosti publikování
 Při publikování aplikace ve výše uvedených postupech jsou následující vlastnosti vloženy do souboru projektu pomocí Průvodce publikováním. Tyto vlastnosti mají přímý vliv na to, jak se aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vyrábí.

 V *CmdLineDemo. vbproj* / *CmdLineDemo. csproj*:

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

 Jakoukoli z těchto vlastností můžete přepsat na příkazovém řádku bez změny samotného souboru projektu. Následující příklad vytvoří nasazení aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bez zaváděcího nástroje:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Vlastnosti publikování jsou ovládány v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ze stránek vlastností **publikování**, **zabezpečení**a **podepisování** v **Návrháři projektu**. Níže je uveden popis vlastností publikování spolu s uvedením toho, jak jsou jednotlivé vlastnosti nastaveny na různých stránkách vlastností návrháře aplikace:

- `AssemblyOriginatorKeyFile` určuje soubor klíče, který se používá k podepsání manifestů aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Stejný klíč lze také použít k přiřazení silného názvu sestavením. Tato vlastnost je nastavena na stránce **podepisování** v **Návrháři projektu**.

  Na stránce **zabezpečení** jsou nastaveny následující vlastnosti:

- **Povolit nastavení zabezpečení ClickOnce** určuje, jestli se generují [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty. Při počátečním vytvoření projektu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generování manifestu je ve výchozím nastavení vypnuté. Průvodce automaticky zapne tento příznak při prvním publikování.

- **TargetZone** určuje úroveň důvěryhodnosti, která se má vygenerovat do manifestu aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Možné hodnoty jsou "Internet", "LocalIntranet" a "vlastní". Internet a LocalIntranet způsobí, že se do manifestu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pošle výchozí nastavení oprávnění. LocalIntranet je výchozí a v podstatě znamená úplný vztah důvěryhodnosti. Vlastní určuje, že do manifestu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace se budou generovat jenom oprávnění explicitně zadaná v souboru *manifestu základní aplikace.* Soubor *App. manifest* je částečný soubor manifestu, který obsahuje jenom definice informací o důvěryhodnosti. Jedná se o skrytý soubor, který se automaticky přidá do projektu při konfiguraci oprávnění na stránce **zabezpečení** .

  Na stránce **publikovat** jsou nastaveny následující vlastnosti:

- `PublishUrl` je umístění, do kterého bude aplikace publikována v integrovaném vývojovém prostředí. Pokud není zadána vlastnost `InstallUrl` nebo `UpdateUrl`, je vložena do manifestu aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

- `ApplicationVersion` určuje verzi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. Toto je číslo verze se čtyřmi číslicemi. Pokud je poslední číslice "*", `ApplicationRevision` je nahrazena hodnotou vloženou do manifestu v čase sestavení.

- `ApplicationRevision` určuje revizi. Toto je celé číslo, které zvýší pokaždé, když publikujete v integrovaném vývojovém prostředí. Všimněte si, že se automaticky nezvyšuje pro sestavení prováděná na příkazovém řádku.

- `Install` určuje, zda je aplikace nainstalovaná aplikace nebo aplikace spouštěná z webu.

- `InstallUrl` (nezobrazený) je umístění, ze kterého budou uživatelé aplikaci instalovat. Je-li tento parametr zadán, je tato hodnota vypálena do zaváděcího nástroje *Setup. exe* , pokud je povolena vlastnost `IsWebBootstrapper`. Je také vložen do manifestu aplikace, pokud není zadána `UpdateUrl`.

- `SupportUrl` (nezobrazený) je umístění propojené v dialogovém okně **Přidat nebo odebrat programy** nainstalované aplikace.

  Následující vlastnosti jsou nastaveny v dialogovém okně **aktualizace aplikace** , ke kterým se dostanete ze stránky **publikování** .

- `UpdateEnabled` určuje, zda má aplikace vyhledat aktualizace.

- `UpdateMode` určuje aktualizace na popředí nebo aktualizace na pozadí.

- `UpdateInterval` určuje, jak často by měla aplikace vyhledávat aktualizace.

- `UpdateIntervalUnits` určuje, zda je hodnota `UpdateInterval` v jednotkách hodiny, dnů nebo týdnů.

- `UpdateUrl` (nezobrazený) je umístění, ze kterého bude aplikace přijímat aktualizace. Je-li tento parametr zadán, je tato hodnota vložena do manifestu aplikace.

  Následující vlastnosti jsou nastaveny v dialogovém okně **Možnosti publikování** , ke kterým se dostanete ze stránky **publikování** .

- `PublisherName` Určuje název vydavatele zobrazeného na příkazovém řádku, který se zobrazí při instalaci nebo spuštění aplikace. V případě nainstalované aplikace se také používá k určení názvu složky v nabídce **Start** .

- `ProductName` Určuje název produktu zobrazeného ve výzvě zobrazené při instalaci nebo spuštění aplikace. V případě nainstalované aplikace se také používá k zadání názvu zástupce v nabídce **Start** .

  Následující vlastnosti jsou nastaveny v dialogovém okně **předpoklady** , ke kterým se přistupoval ze stránky **publikování** .

- `BootstrapperEnabled` určuje, zda má být vygenerován zaváděcí *program Setup. exe* .

- `IsWebBootstrapper` určuje, zda zaváděcí nástroj *Setup. exe* funguje na webu nebo v režimu na disku.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL a UpdateURL
 V následující tabulce jsou uvedeny čtyři možnosti adresy URL pro nasazení ClickOnce.

|Možnost adresy URL|Popis|
|----------------|-----------------|
|`PublishURL`|Vyžaduje se, pokud publikujete aplikaci ClickOnce na web.|
|`InstallURL`|Volitelné. Tuto možnost adresy URL nastavte, pokud se instalační web liší od `PublishURL`. Můžete například nastavit `PublishURL` na cestu FTP a nastavit `InstallURL` na adresu URL webu.|
|`SupportURL`|Volitelné. Tuto možnost adresy URL nastavte, pokud se web podpory liší od `PublishURL`. Můžete například nastavit `SupportURL` na web zákaznické podpory vaší společnosti.|
|`UpdateURL`|Volitelné. Tuto možnost adresy URL nastavte, pokud se umístění aktualizace liší od `InstallURL`. Můžete například nastavit `PublishURL` na cestu FTP a nastavit `UpdateURL` na adresu URL webu.|

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
