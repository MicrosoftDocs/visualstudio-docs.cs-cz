---
title: Instalace sady Visual Studio 2015 | Dokumenty společnosti Microsoft
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445074"
---
# <a name="install-visual-studio-2015"></a>Instalace sady Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato stránka obsahuje podrobné informace, které vám pomohou s instalací **Sady Visual Studio 2015**, naší integrované sady nástrojů pro zvýšení produktivity pro vývojáře. Také jsme zahrnuli odkazy, které vám rychle poskytnou informace o [funkcích](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [požadavcích na systém](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [stahování](https://visualstudio.microsoft.com/vs/older-downloads/)a další.

## <a name="quick-links"></a>Rychlé odkazy

Než se podíváme do podrobností, zde je seznam našich nejčastěji požadovaných odkazů.

|||
|------------------|----------------|
|![Stažení sady Visual Studio](../install/media/downloads.png "Soubory ke stažení") |**Ke stažení**: Chcete-li nainstalovat Visual Studio 2015, můžete stáhnout spustitelný soubor produktu ze stránky [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (vyžadováno předplatné) nebo použít instalační médium z krabicového produktu. [Přečtěte si další informace o stažení aktuálních nebo předchozích verzí sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Další informace o funkcích](../install/media/features.png "Funkce") |**Funkce:** Další informace o funkcích sady Visual Studio 2015 naleznete v poznámkách k verzi [pro RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), Update [2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)a [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Zobrazit systémové požadavky](../install/media/system-requirements.png "Systémové požadavky") |**Systémové požadavky**: Chcete-li zobrazit systémové požadavky pro každé vydání Sady Visual Studio 2015, podívejte se na stránku [Cílení a kompatibilita platformy Visual Studia 2015.](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)|
|![Vyhledání kódu Product Key](../install/media/product-keys.png "Product Keys") |**Kódy Product Key**: Informace o tom, jak najít kód Product Key, naleznete v tématu [Postup: Vyhledání kódu Product Key sady Visual Studio.](../install/how-to-locate-the-visual-studio-product-key.md)|
|![Další informace o licencování](../install/media/licensing.png "Licencování") |**Licencování**: Informace o možnostech licencování pro jednotlivce i podnikové zákazníky naleznete v [dokumentu White Paper o licencování Visual Studia 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Výchozí vs. vlastní instalace
 Při instalaci sady Visual Studio 2015 můžete zahrnout nebo vyloučit součásti, které byste používali denně. To znamená, že výchozí instalace bude často menší a instalace rychleji než vlastní instalace. To také znamená, že mnoho součástí, které byly nainstalovány ve výchozím nastavení v předchozích verzích jsou nyní považovány za vlastní součásti, které je nutné explicitně vybrat v této verzi.

 ![Dialogové okno Nastavení visual studia 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Vlastní součásti zahrnují visual c++, visual f#, sql server datové nástroje, mobilní nástroje pro různé platformy a sady SDK a sady SDK a rozšíření třetích stran. Pokud je během počátečníinstalace nevyberete, můžete některou z vlastních součástí nainstalovat později.

> [!NOTE]
> Vlastní instalace automaticky zahrnuje součásti, které jsou ve výchozí instalaci.

 Úplný seznam vlastních součástí je následující:

|Sady funkcí|Komponenty|
|------------------|----------------|
|**Aktualizace**|Visual Studio 2015 Update 3|
|**Programovací jazyky**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Vývoj systému Windows a webu**|Nástroje pro publikování clickonce<br />LightSwitch<br />Nástroje pro vývojáře sady Microsoft Office<br />Datové nástroje serveru Microsoft SQL Server<br /> Nástroje pro vývojáře webu společnosti Microsoft<br />Nástroje prostředí PowerShell pro visual studio (třetí strana)<br />Sada pro vývoj Silverlight<br />Univerzální nástroje pro vývoj aplikací pro Windows<br />Nástroje a sady SDK pro Windows 10<br />Nástroje pro Windows 8.1 a Windows Phone 8.0/8.1<br />Nástroje a sady SDK pro Windows 8.1|
|**Mobilní rozvoj napříč platformami**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Vizuální vývoj mobilních aplikací pro iOS / Android<br />Clang with Microsoft CodeGen|
|**Běžné sady nástrojů a vývoje softwaru**|Android Native Development Kit (3rd Party)<br /> Android SDK [třetí strana]<br />Android SDK Instalační API (3rd Party)<br />Apache Ant (3. strana)<br /> Java SE Development Kit (3. strana)<br /> Joyent Node.js (3. strana)|
|**Běžné nástroje**|Git pro Windows (3. strana)<br />Rozšíření GitHub pro Visual Studio (3. strana)<br /> Nástroje pro rozšiřitelnost sady Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a>Instalace sady Visual Studio
 Visual Studio můžete nainstalovat pomocí instalačních médií (DVD), pomocí služby předplatného sady Visual Studio z webu [My.VisualStudio.com,](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) stažením webovéinstalační [služby](https://visualstudio.microsoft.com/vs/older-downloads/) z webu sady Visual Studio Ke stažení nebo vytvořením rozložení instalace offline (další podrobnosti najdete na stránce [Vytvoření offline instalace sady Visual Studio).](../install/create-an-offline-installation-of-visual-studio.md)

> [!IMPORTANT]
> K instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]potřebujete pověření správce. Po instalaci je však nepotřebujete k použití. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

 K instalaci všeho v sadě Visual Studio musí být povolena následující oprávnění správce.

|Zobrazovaný název objektu místní zásady|Uživatelské právo|
|--------------------------------------|----------------|
|Záložní soubory a adresáře|Oprávnění SeBackupPrivilege|
|Ladit programy|Sedebugprivilege|
|Spravovat auditování a protokol zabezpečení|Oprávnění SeSecurityPrivilege|

 Další informace o tomto požadavku na účet místního správce naleznete v článku znalostní báze Knowledge Base, [instalace serveru SQL Server se nezdaří, pokud instalační účet nemá určitá uživatelská práva](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Použití instalačního média
 Chcete-li nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]program , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spusťte v kořenovém adresáři instalačního média instalační soubor požadované edice:

|Edice|Instalační soubor|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Stáhnout z webových stránek produktu
 Navštivte stránku [Stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) a vyberte požadovanou edici sady Visual Studio.

### <a name="download-from-your-subscription-service"></a>Stažení ze služby předplatného
 Navštivte [stránku My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) a vyberte požadovanou edici sady Visual Studio.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Vytvoření rozložení instalace offline
 Pokud nemáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalační médium nebo nemáte předplatné sady Visual Studio nebo nechcete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalovat pomocí webového instalačního programu, můžete provést "odpojenou" instalaci vytvořením takzvaného rozložení instalace offline. Další informace naleznete na stránce [Vytvoření offline instalace sady Visual Studio.](../install/create-an-offline-installation-of-visual-studio.md)

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Nasazení Sady Visual Studio v rozlehlé síti
 Informace o nasazení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v síti naleznete v [příručce visual studio administrator guide](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Instalace Sady Visual Studio ve virtualizovaném prostředí
 **Problémy s videem s technologieí Hyper-V**

 Pokud používáte systém Windows Server 2008 R2 s technologií Hyper-V a urychlování pomocí grafického adaptéru, může docházet ke zpomalování systému.

 Další informace naleznete [v tématu Výkon videa může snížit, pokud je v počítači se systémem Windows Server 2008 nebo Windows Server 2008 R2 povolena role Hyper-V a nainstalován zrychlený grafický adaptér](https://support.microsoft.com/kb/961661).

 **Emulace zařízení pomocí technologie Hyper-V**

 Když nainstalujete Visual Studio 2015 na skutečný hardware bez virtualizace, můžete si vybrat funkce, které umožňují emulaci zařízení se systémem Windows a Android pomocí technologie Hyper-V. Při instalaci do technologie Hyper-V nebudete moci emulovat zařízení se systémem Windows nebo Android. Důvodem je, že emulátory jsou samy o sobě virtuální počítače a aktuálně nelze hostovat virtuální počítač uvnitř jiného virtuálního počítače. Řešení je mít skutečné Windows nebo Android zařízení, do kterých můžete přímo nasadit a ladit aplikace.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Instalace volitelných součástí
 Chcete-li nainstalovat součásti, které jste pravděpodobně nevybrali během původní instalace, použijte následující postup.

#### <a name="to-install-optional-components"></a>Instalace volitelných součástí

1. V **Ovládacích panelech**vyberte na stránce **Programy a funkce** edici produktu, do které chcete přidat jednu nebo více součástí, a pak zvolte **Změnit**.

2. V Průvodci instalací zvolte **Změnit**a pak zvolte součásti, které chcete nainstalovat.

3. Zvolte **Další**a postupujte podle zbývajících pokynů.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Instalace obsahu nápovědy offline
 Po instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]můžete stáhnout další obsah nápovědy, aby byl k dispozici offline.

#### <a name="to-install-or-uninstall-help-content"></a>Instalace nebo odinstalace obsahu nápovědy

1. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řádku nabídek zvolte **Nápověda**, **Přidat a odebrat obsah nápovědy**.

2. Na kartě **Správa obsahu** v **prohlížeči nápovědy společnosti Microsoft**vyberte zdroj instalace obsahu nápovědy.

3. Pokud hledáte konkrétní kolekci nápovědy, zadejte název nebo klíčové slovo do textového pole **Hledat** a stiskněte **Enter**.

4. Vedle názvu požadované kolekce nápovědy zvolte odkaz **Přidat** nebo **Odebrat.**

5. Klepněte na tlačítko **Aktualizovat.**

   Další informace o instalaci nebo nasazení offline nápovědy naleznete v [průvodci správcem prohlížeče nápovědy](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Kontrola vydání služeb a aktualizací produktů
 Vzhledem k tomu, že ne všechna rozšíření jsou kompatibilní, Visual Studio není automaticky upgradovat rozšíření při upgradu z předchozích verzí. Rozšíření je nutné přeinstalovat z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo od vydavatele softwaru.

#### <a name="to-automatically-check-for-service-releases"></a>Automatické zjišťování aktualizací Service Release

1. Na řádku nabídek zvolte **Nástroje**, **Možnosti**.

2. V dialogovém okně **Možnosti** rozbalte **položku Prostředí**a pak vyberte **Položku Rozšíření a aktualizace**. Zkontrolujte, zda je zaškrtnuté políčko **Automaticky zaškrtávat aktualizace,** a pak zvolte **OK**.

## <a name="register-visual-studio"></a>Registrace sady Visual Studio

1. Na řádku nabídek zvolte **Nápověda**, **O .**

     V dialogovém okně **Informace** se zobrazí identifikační číslo produktu (PID). K registraci produktu budete potřebovat přihlašovací údaje k účtu PID a Windows (například službu Hotmail nebo Outlook.com e-mailovou adresu a heslo).

2. Na řádku nabídek zvolte **Nápověda**, **Registrovat produkt**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Oprava sady Visual Studio

#### <a name="to-repair-visual-studio"></a>Oprava aplikace Visual Studio

1. V **Ovládacích panelech**vyberte na stránce **Programy a funkce** edici produktu, kterou chcete opravit, a pak zvolte **Změnit**.

2. V průvodci instalací zvolte **Opravit**, zvolte **Další**a postupujte podle zbývajících pokynů.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Oprava sady Visual Studio v tichém nebo pasivním režimu (to znamená opravit ze zdroje)

1. V počítači s nainstalovanou sadou Visual Studio otevřete okno příkazového řádku systému Windows.

2. Zadejte následující parametry:

     < *Instalační* soubor\> \\ \< `norestart` *DVDRoot* `/quiet|/passive` DVDRoot> [/ ]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Poradce při potížích s instalací
 Pomocí těchto zdrojů získáte nápovědu k problémům s instalací a instalací:

- [Fórum pro nastavení a instalaci sady Visual Studio.](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) Přečtěte si otázky a odpovědi od jiných uživatelů z komunity systému Visual Studio. Pokud nenajdete, co potřebujete, můžete zadat vlastní otázky.

- [Získejte pomoc s visual studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Vyhledejte články znalostní báze (KB) a zjistěte, jak kontaktovat podporu společnosti Microsoft s informacemi o problémech s instalací sady Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Příbuzná témata

|Nadpis|Popis|
|-----------|-----------------|
|[Vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Popisuje, jak nainstalovat visual studio, pokud nejste připojeni k Internetu.
|[Instalace verzí sady Visual Studio vedle sebe](../install/install-visual-studio-versions-side-by-side.md)|Obsahuje informace o instalaci více verzí sady Visual Studio v jednom počítači.|
|[Instalace sady Visual Studio pomocí parametrů příkazového řádku](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Zobrazí seznam parametrů příkazového řádku, které lze použít při instalaci sady Visual Studio z příkazového řádku.|
|[Odinstalace sady Visual Studio](../install/uninstall-visual-studio.md)|Popisuje způsob odinstalace sady Visual Studio.|
|[Příručka správce sady Visual Studio](../install/visual-studio-administrator-guide.md)|Obsahuje informace o možnostech nasazení pro sadu Visual Studio.|
|[Knihovna obrázků Visual Studia](../designers/the-visual-studio-image-library.md)|Poskytuje informace o instalaci grafiky, kterou lze použít v aplikacích Visual Studio.|
|[Začínáme s vývojem pomocí jazyka Visual C++](../ide/get-started-developing-with-visual-studio.md)|Obsahuje informace a odkazy, které vám pomohou používat visual studio efektivněji.|

## <a name="see-also"></a>Viz také

- [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)
