---
title: Řešení potíží s nasazením řešení pro systém Office
ms.date: 02/02/2017
ms.topic: troubleshooting
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
ms.openlocfilehash: 679a6e753e61ecb1af9097692a741c35e531c7cc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545740"
---
# <a name="troubleshoot-office-solution-deployment"></a>Řešení potíží s nasazením řešení pro systém Office
  Toto téma obsahuje informace o tom, jak řešit běžné problémy, se kterými se můžete setkat při nasazení řešení pro systém Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Řešení potíží s řešeními pro systém Office pomocí prohlížeče událostí
 Pomocí prohlížeče událostí ve Windows můžete zobrazit chybové zprávy zaznamenané [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci nebo odinstalaci řešení Office. Pomocí těchto zpráv z protokolovacího nástroje můžete vyřešit problémy s instalací a nasazením. Další informace najdete v tématu [protokolování událostí pro řešení Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Změna názvu sestavení způsobí konflikty.
 Pokud změníte hodnotu **názvu sestavení** na stránce **aplikace** **Návrháře projektu** poté, co jste již nasadili řešení, nástroj pro publikování změní instalační balíček tak, aby měl jeden *Setup.exe* soubor a dva manifesty nasazení. Pokud nasadíte dva soubory manifestu, může dojít k následujícím podmínkám:

- Pokud koncový uživatel nainstaluje obě verze, aplikace načte doplňky VSTO.

- Pokud byl doplněk VSTO nainstalovaný ještě před změnou názvu sestavení, koncový uživatel nebude dostávat aktualizace.

  Chcete-li předejít těmto podmínkám, neměňte hodnotu **názvu sestavení** řešení po nasazení řešení.

## <a name="check-for-updates-takes-a-long-time"></a>Kontrolovat aktualizace trvají dlouhou dobu
 Sada Visual Studio 2010 Tools for Office runtime poskytuje položku registru, kterou mohou správci použít k nastavení hodnoty časového limitu pro stahování manifestů a řešení.

#### <a name="to-set-the-time-out-value"></a>Nastavení hodnoty časového limitu

1. V registru přejděte na následující klíč:

     **HKEY_CURRENT_USER \Software\Microsoft\VSTA**

2. V podklíči **AddInTimeout** nastavte hodnotu časového limitu v milisekundách.

     Pokud podklíč **AddInTimeout** neexistuje, vytvořte jej jako DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nejde aktualizovat nebo publikovat do síťové sdílené složky.
 Řešení Office, která se nacházejí v síťové sdílené složce, můžou během aktualizací zobrazovat zavádějící zprávu, pokud je soubor *Setup.exe* řešení během publikování aktualizace uzamčený v procesu. Zpráva může znamenat následující: "nelze přidat ' setup.exe ' na web. Soubor ' setup.exe ' již v tomto webu existuje. "

 Chcete-li zabránit zamykání souborů, můžete nastavit sdílení pro koncové uživatele jen pro čtení. Pokud jsou však dokumenty ve sdílené složce, budou se koncovým uživatelům také načítat jen pro čtení.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Předpoklady pro systém Microsoft Office nejsou nainstalované.
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Do instalačního balíčku můžete přidat .NET Framework, a primární spolupracující sestavení sady Office, a to jako požadavky nasazené s vaším řešením pro systém Office. Informace o tom, jak nainstalovat primární spolupracující sestavení, najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) a [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publikování pomocí místního hostitele může způsobit problémy s instalací.
 Když použijete `http://localhost` jako umístění pro publikování nebo instalaci pro řešení na úrovni dokumentu, **Průvodce publikování** nepřevede řetězec na skutečný název počítače. V takovém případě musí být řešení nainstalované ve vývojovém počítači. Aby nasazená řešení používala službu IIS na vývojovém počítači, použijte plně kvalifikovaný název pro všechna umístění HTTP/HTTPS/FTP a nikoli localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Sestavení v mezipaměti jsou načtena místo aktualizovaných sestavení
 Fusion, .NET Framework zavaděč sestavení, načte kopii sestavení v mezipaměti, když je výstupní cesta projektu v síťové sdílené složce, sestavení je podepsáno silným názvem a verze sestavení přizpůsobení se nemění. Pokud aktualizujete sestavení, které splňuje tyto podmínky, aktualizace se nezobrazí při příštím spuštění projektu, protože je načtena kopie uložená v mezipaměti.

 Můžete nakonfigurovat aplikaci Visual Studio tak, aby fúze stahoval sestavení při každém spuštění projektu.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Stažení sestavení místo načtení kopií v mezipaměti

1. V panelu nabídek vyberte **projekt**,**vlastnosti** _ProjectName_.

2. Na stránce **aplikace** vyberte **informace o sestavení**.

3. Nastavte číslo revize, třetí pole **verze sestavení**, na zástupnou kartu ( \* ). Například "1,0. *".  Pak klikněte na tlačítko **OK** .

   Po změně verze sestavení můžete pokračovat v podepisování sestavení silným názvem a fúze načte nejnovější verzi vlastního nastavení.

 [!NOTE]
> Počínaje sadou Visual Studio 2017 Pokud se pokusíte použít zástupné karty v sestavení verze, dojde k chybě sestavení.  Je to proto, že zástupné znaky v sestavení verze přeruší deterministické funkce MSBuild. Budete vyzváni buď k odebrání zástupných znaků z verze sestavení, nebo zakázání determinismem.  Další informace o deterministické funkci najdete v tématech [běžné vlastnosti projektu MSBuild](../msbuild/common-msbuild-project-properties.md) a [přizpůsobení sestavení](../msbuild/customize-your-build.md) .

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Instalace se nezdařila, pokud identifikátor URI obsahuje znaky, které nejsou US-ASCII.
 Když publikujete řešení Office do umístění HTTP/HTTPS/FTP, cesta nemůže obsahovat žádné znaky Unicode, které nejsou v US-ASCII. Tyto znaky můžou v instalačním programu způsobit nekonzistentní chování. Pro instalační cestu použijte znaky US-ASCII.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Při publikování a instalaci řešení na vývojovém počítači se zobrazí výzva k ruční odinstalaci.
 Při sestavování řešení pro systém Office se sestavená verze automaticky zaregistruje. Pokud jste již dříve publikovali a nainstalovali stejné řešení do vašeho vývojového počítače, aplikace [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zjistí, že instalační cesta pro publikovanou verzi a sestavená verze se liší od dalšího sestavení, opětovného sestavení nebo publikování tohoto řešení. Chybová zpráva znamená "přizpůsobení nelze nainstalovat, protože je aktuálně nainstalována jiná verze a nelze ji upgradovat z tohoto umístění." Klíče registru se aktualizují pokaždé, když se znovu sestaví řešení. Proto je nutné před publikováním, laděním nebo spuštěním nové verze odinstalovat předchozí verzi.

 Chcete-li zabránit zobrazení zprávy, vytvořte na svém vývojovém počítači jiný uživatelský účet pro otestování nasazení. Alternativně můžete odinstalovat verzi ze seznamu nainstalovaných programů v počítači před dalším publikováním, laděním nebo opětovným sestavením řešení.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Při instalaci řešení došlo k chybě při nezachycené výjimce nebo metodě nebyla nalezena.
 Když nainstalujete řešení Office otevřením manifestu nasazení (soubor *. VSTO* ), aplikace Office, dokumentu nebo sešitu, můžou se zobrazit chybové zprávy pro následující podmínky:

- Metoda nebyla nalezena.

- MissingMethodException.

- Nezachycená výjimka.

  Chcete-li zabránit těmto chybovým zprávám, nainstalujte řešení spuštěním instalačního programu.

  Když nainstalujete řešení bez spuštění instalačního programu, instalační program nekontroluje ani neinstaluje požadavky. Instalační program zkontroluje správnou verzi požadavků a nainstaluje je podle potřeby.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Klíče registru manifestu pro doplňky se mění po sestavení projektu InstallShield s omezením edice
 Klíč registru manifestu, který je součástí instalačního programu doplňku VSTO, se někdy při vytváření projektu InstallShield s omezením verze změní z *. VSTO* na *. dll. manifest* .

 Pokud chcete tento problém obejít, vytvořte projekt InstallShield limit Edition v jiném řešení nebo použijte CompanyName. AddIn jako hodnotu klíče registru, který obsahuje název doplňku VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalační program ClickOnce pro vaše řešení Office neinstaluje primární spolupracující sestavení.
 Když spustíte instalační program, který ClickOnce vytvoří pro vaše řešení Office, instalační program pro primární spolupracující sestavení (PIA) pro Office se spustí jenom v případě, že už nejsou nainstalované žádné PIA.

 Pokud instalační program nenainstaluje PIA správně, nainstalujte je ručně spuštěním instalačního souboru s názvem *o2007pia.msi* z instalačního adresáře.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Přeinstalace řešení pro systém Office způsobí výjimku argumentu mimo rozsah.
 Při přeinstalaci řešení pro systém Office se <xref:System.ArgumentOutOfRangeException> může zobrazit výjimka s následující chybovou zprávou: zadaný argument byl mimo rozsah platných hodnot.

 K této situaci dochází, pokud se liší velikost písmen pro adresu URL umístění instalace. Tato chyba se může zobrazit například v případě, že jste poprvé nainstalovali řešení `http://fabrikam.com/ExcelSolution.vsto` pro Office a potom použili `http://fabrikam.com/excelsolution.vsto` podruhé.

 Aby se zabránilo zobrazování této zprávy, používejte při instalaci řešení Office stejnou velikost písmen.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nejde nainstalovat řešení ClickOnce otevřením manifestu nasazení z webu.
 Uživatelé mohou instalovat řešení pro systém Office otevřením manifestu nasazení z webu. Některé instalace služby Internetová informační služba (IIS) ale blokují příponu názvu souboru *. VSTO* . Musíte definovat typ MIME ve službě IIS před tím, než ho použijete k nasazení řešení pro Office.

 Informace o tom, jak ve službě IIS 7 definovat typ MIME, najdete v tématu [Přidání typu MIME (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Nastavte rozšíření na **. VSTO** a typ MIME na **Application/x-MS-VSTO**.

## <a name="see-also"></a>Viz také:

- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
