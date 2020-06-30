---
title: Instalace sady Visual Studio 2015 | Microsoft Docs
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
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548041"
---
# <a name="install-visual-studio-2015"></a>Instalace sady Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato stránka obsahuje podrobné informace, které vám pomůžou s instalací sady **Visual Studio 2015**, naší integrované sady nástrojů pro produktivitu pro vývojáře. Také jsme zahrnuli odkazy, které vám umožní rychle získat informace o [funkcích](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [požadavcích na systém](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [souborech ke stažení](https://visualstudio.microsoft.com/vs/older-downloads/)a dalších.

## <a name="quick-links"></a>Rychlé odkazy

Než se budeme dig k podrobnostem, tady je seznam našich nejčastěji požadovaných odkazů.

|Nadpis|Popis|
|------------------|----------------|
|![Stažení sady Visual Studio](../install/media/downloads.png "Soubory ke stažení") |**Soubory ke stažení**: pro instalaci sady Visual Studio 2015 můžete stáhnout spustitelný soubor produktu ze stránky [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (vyžaduje předplatné) nebo použít instalační média z zabaleného produktu. [Přečtěte si další informace o tom, jak stáhnout aktuální nebo předchozí verze sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Další informace o funkcích](../install/media/features.png "Funkce") |**Funkce**: Další informace o funkcích v aplikaci Visual Studio 2015 najdete v poznámkách k verzi [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)a [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Zobrazit požadavky na systém](../install/media/system-requirements.png "Požadavky na systém") |**Požadavky na systém**: Chcete-li zobrazit požadavky na systém pro jednotlivé edice sady visual Studio 2015, přečtěte si stránku [cílení a kompatibilita platformy Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Vyhledání kódu Product Key](../install/media/product-keys.png "Kódy Product Key") |**Kódy Product**Key: Pokud chcete najít kód Product Key, přečtěte si téma [Postupy: vyhledání kódu Product Key pro Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Přečtěte si o licencování](../install/media/licensing.png "Licencování") |**Licencování**: informace o možnostech licencování pro jednotlivce nebo podnikové zákazníky najdete v [dokumentu White paper k licencování sady Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Výchozí vs. vlastní nastavení
 Při instalaci sady Visual Studio 2015 můžete zahrnout nebo vyloučit součásti, které byste použili každý den. To znamená, že výchozí instalace bude často menší a bude se instalovat rychleji než vlastní instalace. Také to znamená, že mnoho komponent, které byly nainstalovány ve výchozím nastavení v předchozích verzích, se nyní považují za vlastní komponenty, které musíte explicitně vybrat v této verzi.

 ![Dialogové okno instalace sady Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Vlastní komponenty zahrnují Visual C++, Visual F#, SQL Server nástrojů pro data, Mobile Tools a sady SDK pro různé platformy a sady SDK a rozšíření třetích stran. Jakékoli vlastní součásti můžete nainstalovat později, pokud je během počáteční instalace nevyberete.

> [!NOTE]
> Vlastní instalace automaticky zahrnuje součásti, které jsou ve výchozí instalaci.

 Úplný seznam vlastních komponent je následující:

|Sady funkcí|Komponenty|
|------------------|----------------|
|**Aktualizace**|Visual Studio 2015 Update 3|
|**Programovací jazyky**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Vývoj pro Windows a Web**|Nástroje pro publikování ClickOnce<br />LightSwitch<br />systém Microsoft Office Vývojářské nástroje<br />Nástroje pro Microsoft SQL Server dat<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (třetí strana)<br />Sada Silverlight Development Kit<br />Nástroje pro vývoj univerzálních aplikací pro Windows<br />Nástroje a sady SDK pro Windows 10<br />Nástroje Windows 8.1 a Windows Phone 8.0/8.1<br />Windows 8.1 nástroje a sady SDK|
|**Vývoj mobilních aplikací pro různé platformy**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ vývoj mobilních aplikací pro iOS/Android<br />Clang with Microsoft CodeGen|
|**Společné nástroje a sady pro vývoj softwaru**|Android Native Development Kit (třetí strana)<br /> Android SDK [třetí strana]<br />Rozhraní API pro instalaci Android SDK (třetí strana)<br />Apache Ant (třetí strana)<br /> Java SE Development Kit (třetí strana)<br /> Joyent Node.js (třetí strana)|
|**Běžné nástroje**|Git pro Windows (třetí strana)<br />Rozšíření GitHub pro Visual Studio (třetí strana)<br /> Visual Studio Extensibility Tools|

## <a name="install-visual-studio"></a><a name="installing"></a>Nainstalovat Visual Studio
 Sadu Visual Studio můžete nainstalovat pomocí instalačního média (DVD) pomocí služby předplatného sady Visual Studio na webu [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , stažením webového instalačního programu z webu pro [Stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) nebo vytvořením offline rozložení instalace (Další informace najdete na stránce [vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ).

> [!IMPORTANT]
> K instalaci je potřeba přihlašovací údaje správce [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Nepotřebujete je ale použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po instalaci.

 Aby bylo možné nainstalovat vše v aplikaci Visual Studio, musí mít váš účet místního správce oprávnění s následujícími oprávněními.

|Zobrazovaný název objektu místních zásad|Uživatelské právo|
|--------------------------------------|----------------|
|Zálohování souborů a adresářů|SeBackupPrivilege|
|Ladit programy|SeDebugPrivilege|
|Spravovat auditování a protokol zabezpečení|SeSecurityPrivilege|

 Další informace o požadavku na tento účet místního správce najdete v článku znalostní báze, [SQL Server instalace se nezdařila, pokud účet pro nastavení nemá určitá uživatelská práva](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Použít instalační média
 Pokud ho chcete nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , spusťte v kořenovém adresáři na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalačním médiu instalační soubor pro požadovanou edici:

|Edice|Instalační soubor|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Stažení z webu produktu
 Přejděte na stránku [soubory ke stažení pro sadu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) a vyberte požadovanou edici sady Visual Studio.

### <a name="download-from-your-subscription-service"></a>Stažení ze služby předplatného
 Navštivte stránku [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) a vyberte požadovanou edici sady Visual Studio.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Vytvoření offline rozložení instalace
 Pokud nemáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalační médium nebo nemáte předplatné sady Visual Studio nebo pokud ho nechcete instalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomocí webové instalační služby, můžete provést odpojenou instalaci tak, že vytvoříte, co se označuje jako offline rozložení instalace. Další informace naleznete na stránce [vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Nasazení sady Visual Studio v podniku
 Informace o tom, jak nasadit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přes síť, najdete v [příručce pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Instalace sady Visual Studio ve virtualizovaném prostředí
 **Problémy s videem s technologií Hyper-V**

 Pokud používáte systém Windows Server 2008 R2 s technologií Hyper-V a urychlování pomocí grafického adaptéru, může docházet ke zpomalování systému.

 Další informace najdete v tématu [výkon videa se může snížit, pokud je v počítači se systémem Windows server 2008 nebo Windows server 2008 R2 povolená role Hyper-V a je nainstalovaný akcelerovaný grafický adaptér](https://support.microsoft.com/kb/961661).

 **Emulace zařízení s technologií Hyper-V**

 Když nainstalujete sadu Visual Studio 2015 na skutečný hardware bez virtualizace, můžete zvolit funkce, které umožňují emulaci zařízení s Windows a Androidem, a to pomocí technologie Hyper-V. Při instalaci do technologie Hyper-V nebudete moci emulovat zařízení s Windows nebo Androidem. Důvodem je to, že emulátory jsou vlastními virtuálními počítači a momentálně nemůžete hostovat virtuální počítač v jiném virtuálním počítači. Alternativním řešením je mít skutečná zařízení s Windows nebo Androidem, na která můžete přímo nasadit a ladit svou aplikaci.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Nainstalovat volitelné součásti
 Pokud chcete nainstalovat součásti, které jste pravděpodobně nevybrali během původní instalace, použijte následující postup.

#### <a name="to-install-optional-components"></a>Instalace volitelných součástí

1. V nabídce **Ovládací panely**na stránce **programy a funkce** zvolte edici produktu, ke které chcete přidat jednu nebo více součástí, a poté zvolte možnost **změnit**.

2. V Průvodci instalací zvolte možnost **Upravit**a pak zvolte součásti, které chcete nainstalovat.

3. Klikněte na tlačítko **Další**a potom postupujte podle zbývajících pokynů.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Nainstalovat obsah offline v nápovědě
 Po instalaci nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete stáhnout další obsah, který bude k dispozici offline.

#### <a name="to-install-or-uninstall-help-content"></a>Instalace nebo odinstalace obsahu nápovědy

1. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řádku nabídek klikněte na tlačítko **help**, **Přidat a odebrat obsah obsahu Help**.

2. Na kartě **Spravovat obsah** **Microsoft Help Viewer**vyberte zdroj instalace pro obsah vaší aplikace Help.

3. Pokud hledáte konkrétní kolekci pro nápovědu, zadejte název nebo klíčové slovo do textového pole **Hledat** a stiskněte klávesu **ENTER**.

4. Vedle názvu požadované kolekce Help klikněte na odkaz **Přidat** nebo **Odebrat** .

5. Klikněte na tlačítko **aktualizovat** .

   Další informace o tom, jak nainstalovat nebo nasadit offline nápovědu, najdete v [příručce pro správce aplikace Help Viewer](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Vyhledat aktualizace Service Release a aktualizací produktů
 Vzhledem k tomu, že nejsou všechna rozšíření kompatibilní, Visual Studio při upgradu z předchozích verzí neprovede automatické upgradování rozšíření. Rozšíření je nutné přeinstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo vydavatele softwaru.

#### <a name="to-automatically-check-for-service-releases"></a>Automatické zjišťování aktualizací Service Release

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. V dialogovém okně **Možnosti** rozbalte položku **prostředí**a pak vyberte možnost **rozšíření a aktualizace**. Ujistěte se, že je zaškrtnuté políčko **automaticky zjišťovat aktualizace** a pak zvolte **OK**.

## <a name="register-visual-studio"></a>Registrace sady Visual Studio

1. Na řádku nabídek klikněte na možnost **help**, **informace o produktu**.

     V dialogovém okně **o** produktu se zobrazuje identifikační číslo produktu (PID). K registraci produktu budete potřebovat přihlašovací údaje identifikátoru PID a účtu systému Windows (například e-mailová adresa služby Hotmail nebo Outlook.com a heslo).

2. V řádku nabídek klikněte na tlačítko **help**, **Registrovat produkt**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Opravit Visual Studio

#### <a name="to-repair-visual-studio"></a>Oprava aplikace Visual Studio

1. V **Ovládacích panelech**na stránce **programy a funkce** zvolte edici produktu, kterou chcete opravit, a pak zvolte **změnit**.

2. V Průvodci instalací zvolte možnost **opravit**, klikněte na tlačítko **Další**a postupujte podle zbývajících pokynů.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Oprava sady Visual Studio v tichém nebo pasivním režimu (tj. oprava ze zdroje)

1. V počítači s nainstalovanou sadou Visual Studio otevřete okno příkazového řádku systému Windows.

2. Zadejte následující parametry:

     *DVDRoot* \\ DVDRoot < *Instalační soubor* \> \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Řešení potíží s instalací
 Pomocí těchto zdrojů můžete získat nápovědu k instalaci a potížím s instalací:

- Fórum pro instalaci [a instalaci sady Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Přečtěte si otázky a odpovědi od jiných uživatelů z komunity systému Visual Studio. Pokud nenajdete, co potřebujete, můžete zadat vlastní otázky.

- [Získejte pomoc se sadou Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Najdete v článcích znalostní báze Knowledge Base (KB) a Naučte se, jak kontaktovat podpora Microsoftu pro informace o problémech s instalací sady Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Příbuzná témata

|Nadpis|Popis|
|-----------|-----------------|
|[Vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Popisuje, jak nainstalovat Visual Studio, když nejste připojení k Internetu.
|[Souběžná instalace verzí sady Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Obsahuje informace o instalaci více verzí sady Visual Studio v jednom počítači.|
|[Použití parametrů příkazového řádku k instalaci sady Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Obsahuje seznam parametrů příkazového řádku, které lze použít při instalaci sady Visual Studio z příkazového řádku.|
|[Odinstalace sady Visual Studio](../install/uninstall-visual-studio.md)|Popisuje postup odinstalace sady Visual Studio.|
|[Příručka pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md)|Obsahuje informace o možnostech nasazení pro sadu Visual Studio.|
|[Knihovna obrázků sady Visual Studio](../designers/the-visual-studio-image-library.md)|Poskytuje informace o instalaci grafiky, kterou lze použít v aplikacích Visual Studio.|
|[Začínáme s vývojem pomocí jazyka Visual C++](../ide/get-started-developing-with-visual-studio.md)|Obsahuje informace a odkazy, které vám pomůžou používat Visual Studio efektivněji.|

## <a name="see-also"></a>Viz také

- [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)
