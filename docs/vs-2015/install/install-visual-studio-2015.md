---
title: Nainstalovat sadu Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298047"
---
# <a name="install-visual-studio-2015"></a>Nainstalovat sadu Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato stránka obsahuje podrobné informace, které vám pomůžou s instalací sady **Visual Studio 2015**, naší integrované sady nástrojů pro produktivitu pro vývojáře. Zahrnuli jsme také odkazy, které vám umožní rychle získat informace o [funkcích](https://www.visualstudio.com/news/vs2015-vs.aspx), [edicích](https://go.microsoft.com/fwlink/?LinkID=242142), [požadavcích na systém](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [souborech ke stažení](https://go.microsoft.com/fwlink/?LinkId=517106)a dalších.

## <a name="quick-links"></a>Rychlé odkazy

Předtím, než jsme proniknout do podrobností, tady je seznam našich nejčastěji požadované odkazy.

|||
|------------------|----------------|
|![Stáhnout Visual Studio](../install/media/downloads.png "Soubory ke stažení") |**Soubory ke stažení**: pro instalaci sady Visual Studio 2015 můžete stáhnout spustitelný soubor produktu ze stránky [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (vyžaduje předplatné) nebo použít instalační média z zabaleného produktu. [Přečtěte si další informace o tom, jak stáhnout aktuální nebo předchozí verze sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Další informace o funkcích](../install/media/features.png "Funkce") |**Funkce**: Další informace o funkcích v aplikaci Visual Studio 2015 najdete v poznámkách k verzi [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs)a [Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Zjistěte, co je v jednotlivých SKU.](../install/media/sku.png "SKU") |**SKU**: informace o tom, co je k dispozici v jednotlivých edicích sady visual Studio 2015, najdete na stránce [Porovnat nabídky sady Visual Studio](https://go.microsoft.com/fwlink/?LinkID=242142) .|
|![Zobrazit požadavky na systém](../install/media/system-requirements.png "Systémové požadavky") |**Požadavky na systém**: Chcete-li zobrazit požadavky na systém pro jednotlivé edice sady visual Studio 2015, přečtěte si stránku [Kompatibilita sady Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Vyhledání kódu Product Key](../install/media/product-keys.png "Kódy Product Key") |**Kódy Product**Key: Pokud chcete najít kód Product Key, přečtěte si téma [Postupy: vyhledání kódu Product Key pro Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Přečtěte si o licencování](../install/media/licensing.png "Licencování") |**Licencování**: informace o možnostech licencování pro jednotlivce nebo podnikové zákazníky najdete v dokumentu White paper k [licencování sady Visual Studio a MSDN](https://www.microsoft.com/download/details.aspx?id=13350) .|

## <a name="custom"></a>Výchozí vs. vlastní nastavení
 Když nainstalujete sadu Visual Studio 2015, můžete zahrnout nebo vyloučit součásti, které byste použili každý den. To znamená, že výchozí instalaci se často menší a rychleji než vlastní instalace nainstalovat. Také znamená, že spousta komponent, které byly nainstalované ve výchozím nastavení v předchozích verzích, nyní jsou považovány za vlastních komponent, které je nutné explicitně vybrat v této verzi.

 ![Dialogové okno instalace sady Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Vlastní komponenty zahrnují Visual C++, Visual F#, SQL Server Data Tools, nástrojů pro různé platformy mobilních a sady SDK a sad SDK třetích stran a rozšíření. Některé z těchto komponent vlastní programy můžete nainstalovat později, i pokud nevyberete je při počátečním nastavení.

> [!NOTE]
> Vlastní instalace automaticky obsahuje součásti, které jsou ve výchozí instalaci.

 Úplný seznam vlastních komponent vypadá takto:

|Sady funkcí|Komponenty|
|------------------|----------------|
|**Aktualizovány**|Visual Studio 2015 Update 3|
|**Programovací jazyky**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Vývoj pro Windows a Web**|Nástroje pro publikování ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Nástroje Microsoft Web Developer Tools<br />Nástroje Powershellu pro Visual Studio (3. stran)<br />Vývojová sada pro Silverlight<br />Nástroje pro vývoj aplikací univerzální Windows<br />Nástroje systému Windows 10 a sady SDK<br />Windows 8.1 a Windows Phone 8.0/8.1 nástrojů<br />Windows 8.1 nástrojů a sad SDK|
|**Vývoj mobilních aplikací pro různé platformy**|C# / .NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Vývoj mobilní Visual C++ pro iOS / Android<br />Clang with Microsoft CodeGen|
|**Společné nástroje a sady pro vývoj softwaru**|Android Native Development Kit (3. stran)<br /> Sada SDK pro Android [3. stran]<br />Rozhraní API instalace sady Android SDK (3. stran)<br />Apache Ant (3. stran)<br /> Java SE Development Kit (3. stran)<br /> Joyent Node.js (3. stran)|
|**Běžné nástroje**|Git pro Windows (3. stran)<br />Rozšíření GitHub pro Visual Studio (3. stran)<br /> Visual Studio Extensibility Tools|

## <a name="installing"></a>Instalace sady Visual Studio
 Sadu Visual Studio můžete nainstalovat pomocí instalačního média (DVD) pomocí služby předplatného sady Visual Studio na webu [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , stažením webového instalačního programu z webu pro [Stažení sady Visual Studio](https://go.microsoft.com/fwlink/?LinkId=517106) nebo vytvořením offline rozložení instalace (Další informace najdete na stránce [vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ).

> [!IMPORTANT]
> K instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]potřebujete přihlašovací údaje správce. Nepotřebujete je ale po instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] použít.

 Váš účet místního správce musí mít následující oprávnění povolit, aby nainstalovat vše, co v sadě Visual Studio.

|Zobrazovaný název objektu místních zásad|Uživatelská práva|
|--------------------------------------|----------------|
|Zálohování souborů a adresářů|SeBackupPrivilege|
|Ladění programů|SeDebugPrivilege|
|Správa protokolu auditování a zabezpečení|SeSecurityPrivilege|

 Další informace o požadavku na tento účet místního správce najdete v článku znalostní báze, [SQL Server instalace se nezdařila, pokud účet pro nastavení nemá určitá uživatelská práva](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a>Použití instalačního média
 Pokud chcete nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], v kořenovém adresáři na instalačním médiu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spusťte instalační soubor pro požadovanou edici:

|Edice|Instalační soubor|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a>Stahování z webu produktu
 Přejděte na stránku [soubory ke stažení pro sadu Visual Studio](https://go.microsoft.com/fwlink/?LinkId=517106) a vyberte požadovanou edici sady Visual Studio.

### <a name="downloading-from-your-subscription-service"></a>Stahuje se z předplatného služby
 Navštivte stránku [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) a vyberte požadovanou edici sady Visual Studio.

### <a name="BKMK_Offline"></a>Vytvoření offline rozložení instalace
 Pokud nemáte instalační médium [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo nemáte předplatné sady Visual Studio, nebo nechcete instalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomocí webové instalační služby, můžete provést odpojenou instalaci tak, že vytvoříte, co se označuje jako offline rozložení instalace. Další informace naleznete na stránce [vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="enterprise"></a>Nasazení sady Visual Studio v podniku
 Informace o tom, jak nasadit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přes síť, najdete v [příručce pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a>Instalace sady Visual Studio ve virtualizovaném prostředí
 **Problémy s videem s technologií Hyper-V**

 Pokud používáte systém Windows Server 2008 R2 s technologií Hyper-V a urychlování pomocí grafického adaptéru, může docházet ke zpomalování systému.

 Další informace naleznete na následující stránce na webu společnosti Microsoft: Pokud je v [počítači se systémem Windows server 2008 nebo Windows server 2008 R2 povolená role Hyper-V a je nainstalovaný akcelerovaný grafický adaptér, může dojít ke snížení výkonu videa](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Emulace zařízení s technologií Hyper-V**

 Při instalaci sady Visual Studio 2015 na skutečný hardware bez virtualizace, můžete funkce, které umožňují emulace systému Windows a zařízení s Androidem pomocí technologie Hyper-V. Pokud instalujete do technologie Hyper-V, nebudete mít k emulaci Windows nebo zařízení s Androidem. Je to proto, že samotné virtuální počítače jsou emulátorů a nelze aktuálně hostování virtuálních počítačů uvnitř jiného virtuálního počítače. Alternativním řešením je, aby skutečné Windows nebo zařízení s Androidem, na které můžete přímo nasadit a ladit aplikaci.

## <a name="optionalComponents"></a>Instalace volitelných součástí
 Pokud chcete nainstalovat součásti, které jste možná vybrali při původní instalaci, použijte následující postup.

#### <a name="to-install-optional-components"></a>K instalaci volitelné součásti

1. V nabídce **Ovládací panely**na stránce **programy a funkce** zvolte edici produktu, ke které chcete přidat jednu nebo více součástí, a poté zvolte možnost **změnit**.

2. V Průvodci instalací zvolte možnost **Upravit**a pak zvolte součásti, které chcete nainstalovat.

3. Klikněte na tlačítko **Další**a potom postupujte podle zbývajících pokynů.

## <a name="helpContent"></a>Instalace obsahu offline v nápovědě
 Po instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]můžete stáhnout další obsah, který bude k dispozici offline.

#### <a name="to-install-or-uninstall-help-content"></a>Instalace nebo odinstalace obsahu nápovědy

1. Na panelu nabídek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] klikněte na tlačítko **help**, **Přidat a odebrat obsah v nápovědě**.

2. Na kartě **Spravovat obsah** **Microsoft Help Viewer**vyberte zdroj instalace pro obsah vaší aplikace Help.

3. Pokud hledáte konkrétní kolekci pro nápovědu, zadejte název nebo klíčové slovo do textového pole **Hledat** a stiskněte klávesu **ENTER**.

4. Vedle názvu požadované kolekce Help klikněte na odkaz **Přidat** nebo **Odebrat** .

5. Klikněte na tlačítko **aktualizovat** .

   Další informace o tom, jak nainstalovat nebo nasadit offline nápovědu, najdete v [příručce pro správce aplikace Help Viewer](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a>Kontrola aktualizací Service Release a aktualizací produktů
 Vzhledem k tomu, že ne všechna rozšíření jsou kompatibilní, Visual Studio neprovádí automatický upgrade rozšíření při upgradu z předchozí verze. Rozšíření je nutné přeinstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo vydavatele softwaru.

#### <a name="to-automatically-check-for-service-releases"></a>Automatické zjišťování aktualizací Service Release

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. V dialogovém okně **Možnosti** rozbalte položku **prostředí**a pak vyberte možnost **rozšíření a aktualizace**. Ujistěte se, že je zaškrtnuté políčko **automaticky zjišťovat aktualizace** a pak zvolte **OK**.

## <a name="registering-visual-studio"></a>Registrace aplikace Visual Studio

1. Na řádku nabídek klikněte na možnost **help**, **informace o produktu**.

     V dialogovém okně **o** produktu se zobrazuje identifikační číslo produktu (PID). Identifikátor PID a účet Windows přihlašovací údaje (například Hotmail nebo Outlook.com e-mailovou adresu a heslo) budete potřebovat k registraci produktu.

2. V řádku nabídek klikněte na tlačítko **help**, **Registrovat produkt**.

## <a name="repair"></a>Oprava sady Visual Studio

#### <a name="to-repair-visual-studio"></a>Oprava aplikace Visual Studio

1. V **Ovládacích panelech**na stránce **programy a funkce** zvolte edici produktu, kterou chcete opravit, a pak zvolte **změnit**.

2. V Průvodci instalací zvolte možnost **opravit**, klikněte na tlačítko **Další**a postupujte podle zbývajících pokynů.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Oprava aplikace Visual Studio v tichém nebo pasivním režimu (tedy oprava ze zdroje)

1. V počítači s nainstalovanou sadou Visual Studio otevřete okno příkazového řádku systému Windows.

2. Zadejte následující parametry:

     *DVDRoot* \\< instalační soubor\> \</quiet&#124;/passive > [/norestart]/Repair

## <a name="troubleshooting"></a>Řešení potíží s instalací
 Tyto prostředky použijte k získání nápovědy pro problémy s instalací a instalací:

- Fórum pro instalaci [a instalaci sady Visual Studio](https://go.microsoft.com/fwlink/?LinkID=151190) . Přečtěte si otázky a odpovědi od jiných uživatelů z komunity systému Visual Studio. Pokud nenajdete, co potřebujete, můžete zadat vlastní otázky.

- [Podpora Microsoftu webu sady Visual Studio](https://go.microsoft.com/fwlink/?LinkID=251019) . Přečtěte si články znalostní báze a naučte se, jak kontaktovat podporu společnosti Microsoft za účelem získání informací o problémech s instalací systému Visual Studio.

## <a name="relatedTopics"></a>Příbuzná témata

|Titul|Popis|
|-----------|-----------------|
|[Vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Popisuje postup instalace sady Visual Studio, když nejsou připojeni k Internetu.
|[Souběžná instalace různých verzí sady Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Obsahuje informace o instalaci více verzí sady Visual Studio v jednom počítači.|
|[Instalace sady Visual Studio s použitím parametrů příkazového řádku](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Obsahuje seznam parametrů příkazového řádku, které můžete použít při instalaci sady Visual Studio z příkazového řádku.|
|[Odinstalace sady Visual Studio](../install/uninstall-visual-studio.md)|Popisuje postup odinstalace sady Visual Studio.|
|[Příručka správce sady Visual Studio](../install/visual-studio-administrator-guide.md)|Obsahuje informace o možnostech nasazení pro sadu Visual Studio.|
|[Knihovna obrázků sady Visual Studio](../designers/the-visual-studio-image-library.md)|Poskytuje informace o instalaci grafiky, kterou lze použít v aplikacích Visual Studio.|
|[Začínáme s vývojem pomocí jazyka Visual C++](../ide/get-started-developing-with-visual-studio.md)|Obsahuje informace a odkazy, které vám umožní efektivní pomocí sady Visual Studio.|

## <a name="see-also"></a>Viz také

- [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)