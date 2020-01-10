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
ms.openlocfilehash: dc84fc135e59a43a05ce66186c4a44e9e31f8f2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851054"
---
# <a name="install-visual-studio-2015"></a>Instalace sady Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato stránka obsahuje podrobné informace, které vám pomůžou s instalací **Visual Studio 2015**, naší integrované sady nástrojů podporujících produktivitu pro vývojáře. Přidali jsme také odkazy, které vám pomůžou rychle k informacím [funkce](https://www.visualstudio.com/news/vs2015-vs.aspx), [edice](https://visualstudio.microsoft.com/en-US/products/compare-visual-studio-products-vs), [požadavky na systém](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [stáhne](https://visualstudio.microsoft.com/downloads/), a další.

## <a name="quick-links"></a>Rychlé odkazy

Předtím, než jsme proniknout do podrobností, tady je seznam našich nejčastěji požadované odkazy.

|||
|------------------|----------------|
|![Stáhnout Visual Studio](../install/media/downloads.png "Stažené položky") |**Soubory ke stažení**: K instalaci sady Visual Studio 2015, můžete stáhnout spustitelný soubor produkt z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) stránce (požadován odběr), nebo pomocí instalačního média z zabalený produkt. [Další informace o tom, jak aktuální nebo předchozí verze sady Visual Studio si můžete stáhnout](https://www.visualstudio.com/vs/older-downloads/).|
|![Další informace o funkcích](../install/media/features.png "Funkce") |**Funkce**: Další informace o funkcích v sadě Visual Studio 2015, najdete v článku zpráva k vydání verze pro [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), a [ S aktualizací 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Zjistěte, co je v jednotlivých SKU.](../install/media/sku.png "SKU") |**SKU**: co je k dispozici v každé edici sady Visual Studio 2015, najdete v tématu naše [porovnání nabídek Visual Studia](https://visualstudio.microsoft.com/en-US/products/compare-visual-studio-products-vs) stránky.|
|![Zobrazit požadavky na systém](../install/media/system-requirements.png "Požadavky na systém") |**Požadavky na systém**: Chcete-li zobrazit systémové požadavky pro jednotlivé edice aplikace Visual Studio 2015, najdete v článku [Kompatibilita sady Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) stránky.|
|![Vyhledání kódu Product Key](../install/media/product-keys.png "Kódy Product Key") |**Kódy Product Key**: Vyhledání kódu product key, najdete v článku [jak: Vyhledejte Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) tématu.|
|![Přečtěte si o licencování](../install/media/licensing.png "Licencování") |**Licencování**: Přečtěte si informace o licencování možnosti pro jednotlivce nebo podnikových zákazníků, najdete v článku [licence Visual Studio a MSDN](https://www.microsoft.com/download/details.aspx?id=13350) dokument white paper.|

## <a name="custom"></a>Výchozí vs. vlastní nastavení
 Když nainstalujete sadu Visual Studio 2015, můžete zahrnout nebo vyloučit součásti, které byste použili každý den. To znamená, že výchozí instalaci se často menší a rychleji než vlastní instalace nainstalovat. Také znamená, že spousta komponent, které byly nainstalované ve výchozím nastavení v předchozích verzích, nyní jsou považovány za vlastních komponent, které je nutné explicitně vybrat v této verzi.

 ![Dialogové okno instalace sady Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Vlastní komponenty zahrnují Visual C++, Visual F#, SQL Server Data Tools, nástrojů pro různé platformy mobilních a sady SDK a sad SDK třetích stran a rozšíření. Některé z těchto komponent vlastní programy můžete nainstalovat později, i pokud nevyberete je při počátečním nastavení.

> [!NOTE]
> Vlastní instalace automaticky obsahuje součásti, které jsou ve výchozí instalaci.

 Úplný seznam vlastních komponent vypadá takto:

|Sady funkcí|Komponenty|
|------------------|----------------|
|**Aktualizace**|Visual Studio 2015 Update 3|
|**Programovací jazyky**|Visual C++ –<br />Visual F#<br />Python Tools for Visual Studio|
|**Windows a vývoj pro Web**|Nástroje pro publikování ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Nástroje Microsoft Web Developer Tools<br />Nástroje Powershellu pro Visual Studio (3. stran)<br />Vývojová sada pro Silverlight<br />Nástroje pro vývoj aplikací univerzální Windows<br />Nástroje systému Windows 10 a sady SDK<br />Windows 8.1 a Windows Phone 8.0/8.1 nástrojů<br />Windows 8.1 nástrojů a sad SDK|
|**Vývoj pro různé platformy mobilních**|C# / .NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Vývoj mobilní Visual C++ pro iOS / Android<br />Clang with Microsoft CodeGen|
|**Běžné nástroje a Software Development Kit**|Android Native Development Kit (3. stran)<br /> Sada SDK pro Android [3. stran]<br />Rozhraní API instalace sady Android SDK (3. stran)<br />Apache Ant (3. stran)<br /> Java SE Development Kit (3. stran)<br /> Joyent Node.js (3. stran)|
|**Běžné nástroje**|Git pro Windows (3. stran)<br />Rozšíření GitHub pro Visual Studio (3. stran)<br /> Visual Studio Extensibility Tools|

## <a name="installing"></a> Instalace sady Visual Studio
 Visual Studio můžete nainstalovat pomocí instalačního média (DVD), pomocí služby předplatného sady Visual Studio z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) webu, stáhněte si instalační program, který web z [sady Visual Studio Soubory ke stažení](https://visualstudio.microsoft.com/downloads/) webu, nebo tak, že vytvoříte rozložení pro offline instalaci (najdete v článku [vytvořit Offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) stránky pro další podrobnosti).

> [!IMPORTANT]
> Je potřeba mít oprávnění správce k instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ale nepotřebujete je, aby používaly [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po její instalaci.

 Váš účet místního správce musí mít následující oprávnění povolit, aby nainstalovat vše, co v sadě Visual Studio.

|Zobrazovaný název objektu místních zásad|Uživatelská práva|
|--------------------------------------|----------------|
|Zálohování souborů a adresářů|SeBackupPrivilege|
|Ladění programů|SeDebugPrivilege|
|Správa protokolu auditování a zabezpečení|SeSecurityPrivilege|

 Další informace o tomto požadavku účet místního správce, najdete v článku znalostní báze Knowledge Base, [instalace systému SQL Server selže, pokud účet použitý k instalaci nemá určitá uživatelská oprávnění](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a> Pomocí instalačního média
 Chcete-li nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], v kořenovém adresáři [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalačním médiu, spusťte instalační soubor pro vydání chcete:

|Edice|Instalační soubor|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a> Stahování z webu produktu
 Přejděte [stahování sady Visual Studio](https://visualstudio.microsoft.com/downloads/) stránky a zvolte edici sady Visual Studio, kterou chcete.

### <a name="downloading-from-your-subscription-service"></a>Stahuje se z předplatného služby
 Přejděte [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) stránky a zvolte edici sady Visual Studio, kterou chcete.

### <a name="BKMK_Offline"></a> Vytvoření rozvržení aplikace offline instalaci
 Pokud nemáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalační médium, nebo nemáte předplatné sady Visual Studio, nebo nechcete nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] použít webovou Instalační službu, můžete provést "odpojené" instalaci tak, že vytvoříte, která se označuje jako offline Instalace rozložení. Další informace najdete v tématu [vytvoření v režimu Offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) stránky.

## <a name="enterprise"></a> Nasazení sady Visual Studio v podniku
 Informace o tom, jak nasadit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přes síť, najdete v článku [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a> Instalace sady Visual Studio ve virtualizovaném prostředí
 **Video problémy s Hyper-V**

 Pokud používáte systém Windows Server 2008 R2 s technologií Hyper-V a urychlování pomocí grafického adaptéru, může docházet ke zpomalování systému.

 Další informace naleznete na následující stránce na webu Microsoftu: [může snížit výkon videa, když Windows Server 2008 nebo Windows Server 2008 R2 na základě počítače má povolenou roli Hyper-V a akcelerovaný grafický adaptér nainstalovaný](https://support.microsoft.com/kb/961661).

 **Emulace zařízení s technologií Hyper-V**

 Při instalaci sady Visual Studio 2015 na skutečný hardware bez virtualizace, můžete funkce, které umožňují emulace systému Windows a zařízení s Androidem pomocí technologie Hyper-V. Pokud instalujete do technologie Hyper-V, nebudete mít k emulaci Windows nebo zařízení s Androidem. Je to proto, že samotné virtuální počítače jsou emulátorů a nelze aktuálně hostování virtuálních počítačů uvnitř jiného virtuálního počítače. Alternativním řešením je, aby skutečné Windows nebo zařízení s Androidem, na které můžete přímo nasadit a ladit aplikaci.

## <a name="optionalComponents"></a> Instalaci volitelné součásti
 Pokud chcete nainstalovat součásti, které jste možná vybrali při původní instalaci, použijte následující postup.

#### <a name="to-install-optional-components"></a>K instalaci volitelné součásti

1. V **ovládací panely**na **programy a funkce** zvolte edici produktu, ke kterému chcete přidat jednu nebo více komponent a pak zvolte **změnu**.

2. V Průvodci instalací zvolte **změnit**a poté vyberte komponenty, které chcete nainstalovat.

3. Zvolte **Další**a pak postupujte podle zbývajících pokynů.

## <a name="helpContent"></a> Instalace offline obsah nápovědy
 Po instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], další obsah nápovědy si můžete stáhnout tak, že bude k dispozici v režimu offline.

#### <a name="to-install-or-uninstall-help-content"></a>Instalace nebo odinstalace obsahu nápovědy

1. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nabídky vyberte možnosti **pomáhají**, **přidat nebo odebrat obsah nápovědy**.

2. Na **spravovat obsah** karty **Microsoft Help Viewer**, vyberte zdroj instalace obsahu nápovědy.

3. Pokud hledáte konkrétní kolekci nápovědy, zadejte název nebo klíčové slovo v **hledání** textové pole a poté stiskněte klávesu **Enter**.

4. Vedle názvu kolekce nápovědy, které chcete, aby, zvolte **přidat** nebo **odebrat** odkaz.

5. Klikněte na tlačítko **aktualizace** tlačítko.

   Další informace o tom, jak nainstalovat nebo nasadit offline nápovědu najdete v článku [pomáhají Příručka pro správce prohlížeč](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a> Kontrola aktualizací Service Release a aktualizací produktů
 Vzhledem k tomu, že ne všechna rozšíření jsou kompatibilní, Visual Studio neprovádí automatický upgrade rozšíření při upgradu z předchozí verze. Rozšíření je nutné přeinstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo vydavatele softwaru.

#### <a name="to-automatically-check-for-service-releases"></a>Automatické zjišťování aktualizací Service Release

1. V panelu nabídky zvolte **nástroje**, **možnosti**.

2. V **možnosti** dialogového okna rozbalte **prostředí**a pak vyberte **rozšíření a aktualizace**. Ujistěte se, **automaticky vyhledávat aktualizace** zaškrtávací políčko zaškrtnuto a klikněte na tlačítko **OK**.

## <a name="registering-visual-studio"></a>Registrace aplikace Visual Studio

1. V panelu nabídky zvolte **pomáhají**, **o**.

     **o** identifikační číslo produktu (PID) se zobrazí dialogové okno. Identifikátor PID a účet Windows přihlašovací údaje (například Hotmail nebo Outlook.com e-mailovou adresu a heslo) budete potřebovat k registraci produktu.

2. V panelu nabídky zvolte **pomáhají**, **registrovat produkt**.

## <a name="repair"></a> Oprava sady Visual Studio

#### <a name="to-repair-visual-studio"></a>Oprava aplikace Visual Studio

1. V **ovládací panely**na **programy a funkce** zvolte edici produktu, kterou chcete opravit a klikněte na tlačítko **změnu**.

2. V Průvodci instalací zvolte **opravit**, zvolte **Další**a pak postupujte podle zbývajících pokynů.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Oprava aplikace Visual Studio v tichém nebo pasivním režimu (tedy oprava ze zdroje)

1. V počítači s nainstalovanou sadou Visual Studio otevřete okno příkazového řádku systému Windows.

2. Zadejte následující parametry:

     *DVDRoot* \\< Instalační_soubor\> \</quiet&#124;/passive > [/ norestart] / opravit

## <a name="troubleshooting"></a> Řešení potíží instalace
 Tyto prostředky použijte k získání nápovědy pro problémy s instalací a instalací:

- [Visual Studio nastavení a instalace](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) fóra. Přečtěte si otázky a odpovědi od jiných uživatelů z komunity systému Visual Studio. Pokud nenajdete, co potřebujete, můžete zadat vlastní otázky.

- [Microsoft Support for Visual Studio](https://support.microsoft.com/ph/1117) webu. Přečtěte si články znalostní báze a naučte se, jak kontaktovat podporu společnosti Microsoft za účelem získání informací o problémech s instalací systému Visual Studio.

## <a name="relatedTopics"></a> Související témata

|Název|Popis|
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
