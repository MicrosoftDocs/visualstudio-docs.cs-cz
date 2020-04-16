---
title: Poradce při potížích s nasazením řešení Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444931"
---
# <a name="troubleshoot-office-solution-deployment"></a>Poradce při potížích s nasazením řešení Office
  Toto téma obsahuje informace o řešení běžných problémů, se kterými se můžete setkat při nasazování řešení sady Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Poradce při potížích s řešeními Office pomocí prohlížeče událostí
 Pomocí prohlížeče událostí v systému Windows můžete zobrazit chybové zprávy zachycené [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci nebo odinstalaci řešení Office. Tyto zprávy z protokolování událostí můžete použít k vyřešení problémů s instalací a nasazením. Další informace naleznete v [tématu Protokolování událostí pro řešení Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Změna názvu sestavení způsobuje konflikty
 Pokud změníte hodnotu **Název sestavení** na stránce **Aplikace** **Návrháře projektu** poté, co jste již nasadili řešení, nástroje pro publikování upraví instalační balíček tak, aby měl jeden soubor *Setup.exe* a dva manifesty nasazení. Pokud nasadíte dva soubory manifestu, může dojít k následujícím podmínkám:

- Pokud koncový uživatel nainstaluje obě verze, aplikace načte oba doplňky VSTO.

- Pokud byl doplněk VSTO nainstalován před změnou názvu sestavení, koncový uživatel nikdy neobdrží aktualizace.

  Chcete-li se těmto podmínkám vyhnout, neměňte hodnotu **název sestavení** řešení po nasazení řešení.

## <a name="check-for-updates-takes-a-long-time"></a>Kontrola aktualizací trvá dlouho
 Visual Studio 2010 Tools for Office runtime poskytuje položku registru, kterou mohou správci použít k nastavení hodnoty časového limitu pro stahování manifestů a řešení.

#### <a name="to-set-the-time-out-value"></a>Nastavení hodnoty časového času

1. V registru přejděte na následující klíč:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. V podklíči **AddInTimeout** nastavte hodnotu časového výpadku v milisekundách.

     Pokud podklíč **AddInTimeout** neexistuje, vytvořte ho jako DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nelze aktualizovat nebo publikovat do sdílené síťové složky
 Řešení sady Office, která jsou ve sdílené síťové složce, mohou během aktualizací zobrazit zavádějící zprávu, pokud je soubor *Setup.exe* řešení během publikování aktualizace uzamčen. Zpráva může říkat následující: "Nelze přidat 'setup.exe' na web. Soubor setup.exe již na tomto webu existuje."

 Chcete-li zabránit zamykání souborů, můžete sdílet jen pro koncové uživatele. Pokud jsou však dokumenty ve sdílené složce, stanou se také pro koncové uživatele jen pro čtení.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Požadavky na sadu Microsoft Office nejsou nainstalovány
 Jako požadavky, které jsou [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]nasazeny s řešením sady Office, můžete do instalačního balíčku přidat rozhraní .NET Framework, a primární interop sestavy sady Office. Informace o instalaci primárních sestav interop naleznete v [tématu Konfigurace počítače pro vývoj řešení sady Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) a [postup: Instalace primárních sestavení mezi opasky Sady Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publikování pomocí Localhost může způsobit problémy s instalací
 Použijete-li `http://localhost` jako umístění publikování nebo instalace řešení na úrovni dokumentu, **Průvodce publikováním** nepřevede řetězec na skutečný název počítače. V takovém případě musí být řešení nainstalováno ve vývojovém počítači. Chcete-li, aby nasazená řešení používala službu IIS ve vývojovém počítači, použijte plně kvalifikovaný název pro všechna umístění HTTP/HTTPS/FTP namísto localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Sestavení uložená v mezipaměti jsou načtena namísto aktualizovaných sestavení
 Fusion, zavaděč sestavení rozhraní .NET Framework, načte kopii sestavení v mezipaměti, když je výstupní cesta projektu ve sdílené síťové složce, sestavení je podepsáno silným názvem a verze vlastního nastavení sestavení se nezmění. Pokud aktualizujete sestavení, které splňuje tyto podmínky, aktualizace se nezobrazí při příštím spuštění projektu, protože je načtena kopie uložená v mezipaměti.

 Visual Studio můžete nakonfigurovat tak, aby Fusion stáhne sestavení při každém spuštění projektu.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Stažení sestavení namísto načítání kopií uložených v mezipaměti

1. Na řádku nabídek zvolte **Project**, _ProjectName_**Properties**.

2. Na stránce **Aplikace** zvolte **Informace o sestavení**.

3. Nastavte číslo revize, třetí pole **verze sestavy**, na\*zástupný znak ( ). Například "1.0.*".  Pak zvolte tlačítko **OK.**

   Po změně verze sestavení můžete pokračovat v podepisování sestavení silným názvem a Fusion načte nejnovější verzi vlastního nastavení.

 [!NOTE]
> Počínaje Visual Studio 2017, pokud se pokusíte použít zástupné znaky ve verzi sestavení dojde k chybě sestavení.  Důvodem je, že zástupné znaky ve verzi sestavení přeruší funkci Deterministic MSBuild. Budete vyzváni k odebrání zástupných znaků z verze sestavení nebo zakázat determinismus.  Další informace o deterministické funkci naleznete v [tématu: Společné vlastnosti projektu MSBuild](../msbuild/common-msbuild-project-properties.md) a [Přizpůsobení sestavení](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Instalace se nezdaří, pokud identifikátor URI má znaky, které nejsou US-ASCII
 Při publikování řešení Sady Office do umístění HTTP/HTTPS/FTP, cesta nemůže mít žádné znaky Unicode, které nejsou v US-ASCII. Tyto znaky mohou způsobit nekonzistentní chování v instalačním programu. Pro instalační cestu použijte znaky US-ASCII.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Při publikování a instalaci řešení do vývojového počítače se zobrazí výzva k ručnímu odinstalaci.
 Když vytváříte řešení Office, vytvořená verze se automaticky zaregistruje. Pokud jste dříve publikovali a nainstalovali stejné [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] řešení do vývojového počítače, zjistí, že instalační cesta pro publikovanou verzi a postavenou verzi se liší po dalším vytvoření, opětovném vytvoření nebo publikování řešení. Chybová zpráva říká, že vlastní nastavení nelze nainstalovat, protože je aktuálně nainstalována jiná verze, kterou nelze z tohoto umístění upgradovat. Klíče registru jsou aktualizovány při každém opětovném vytvoření řešení. Proto je nutné odinstalovat předchozí verzi před publikováním, ladění nebo spuštění nové verze.

 Chcete-li zabránit zobrazení zprávy, vytvořte ve vývojovém počítači jiný uživatelský účet a otestujte nasazení. Alternativně můžete odinstalovat verzi ze seznamu nainstalovaných programů v počítači před dalším publikováním, laděním nebo znovusestavně řešením.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nezachycená výjimka nebo metoda nebyla nalezena chyba při instalaci řešení
 Při instalaci řešení Office otevřením manifestu nasazení (soubor *u.vsto),* aplikace, dokumentu nebo sešitu sady Office se mohou zobrazit chybové zprávy pro následující podmínky:

- Metoda nebyla nalezena.

- MissingMethodException.

- Nezachycená výjimka.

  Chcete-li těmto chybovém zprávám zabránit, nainstalujte řešení spuštěním instalačního programu.

  Při instalaci řešení bez spuštění instalačního programu instalační program nekontroluje ani nenainstaluje požadavky. Instalační program zkontroluje správnou verzi požadavků a podle potřeby je nainstaluje.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Klíče registru manifestu pro doplňky se po sestavení projektu limitované edice InstallShield změní.
 Klíč registru manifestu, který je součástí instalačního programu doplňku VSTO, se při vytváření projektu limitované edice InstallShield někdy změní z *.vsto* na *.dll.manifest.*

 Chcete-li tento problém vyřešit, vytvořte projekt InstallShield Limitovaná edice v jiném řešení nebo použijte CompanyName.AddinName jako hodnotu klíče registru, který obsahuje název doplňku VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalační služba ClickOnce pro vaše řešení Office nenainstaluje primární meziop sestavení
 Při spuštění instalačního programu, který clickonce vytvoří pro vaše řešení sady Office, instalační program pro primární meziop sestavení sady Office (PIA) spustí pouze v případě, že již nejsou nainstalovány žádné PIA.

 Pokud instalační program nenainstaluje pia správně, nainstalujte je ručně spuštěním instalačního souboru s názvem *o2007pia.msi* z instalačního adresáře.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Přeinstalace řešení Office způsobí výjimku argumentu mimo rozsah
 Při přeinstalaci řešení sady <xref:System.ArgumentOutOfRangeException> Office se může zobrazit výjimka s následující chybovou zprávou: Zadaný argument byl mimo rozsah platných hodnot.

 K této situaci dochází, pokud se písmena velikosti URL pro umístění instalace liší. Tato chyba by se například zobrazit, `http://fabrikam.com/ExcelSolution.vsto` pokud jste nainstalovali `http://fabrikam.com/excelsolution.vsto` řešení sady Office od prvního okamžiku a potom použít podruhé.

 Chcete-li zabránit zobrazení zprávy, použijte při instalaci řešení Sady Office stejné pouzdro.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nelze nainstalovat řešení ClickOnce otevřením manifestu nasazení z webu
 Uživatelé mohou nainstalovat řešení Office otevřením manifestu nasazení z webu. Některé instalace Internetové informační služby (IIS) však příponu *.vsto* název souboru blokují. Před nasazením řešení sady Office je nutné definovat typ MIME ve službě IIS.

 Informace o definování typu MIME ve správě IIS 7 naleznete v [tématu Přidání typu MIME (IIS7).](https://technet.microsoft.com/library/cc725608(WS.10).aspx)

 Nastavte rozšíření na **.vsto** a typ MIME na **application/x-ms-vsto**.

## <a name="see-also"></a>Viz také

- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)
