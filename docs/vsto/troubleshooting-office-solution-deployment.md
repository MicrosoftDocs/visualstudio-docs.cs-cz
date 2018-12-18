---
title: Řešení potíží s nasazením řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bba978da26a2aa7b7263fa5d2e88fa8acdc272f0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886000"
---
# <a name="troubleshoot-office-solution-deployment"></a>Řešení potíží s nasazením řešení pro systém Office
  Toto téma obsahuje informace o tom, jak řešit běžné problémy, které se mohou vyskytnout při nasazení řešení Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Řešení potíží s řešení pro systém Office s použitím prohlížeče události  
 Můžete v prohlížeči událostí ve Windows naleznete v chybových zprávách, které jsou zachyceny [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci nebo odinstalaci řešení Office. Tyto zprávy z protokolování událostí můžete použít k vyřešení instalace a problémů s nasazením. Další informace najdete v tématu [protokolování událostí pro řešení Office](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="change-the-assembly-name-causes-conflicts"></a>Změna názvu sestavení způsobí, že je v konfliktu  
 Pokud změníte **název sestavení** hodnota v **aplikace** stránku **Návrháře projektu** po nasazení řešení již, slouží k úpravě nástroje pro publikování Instalační balíček na některou *Setup.exe* souborů a dva manifesty nasazení. Pokud nasadíte dva soubory manifestu, může dojít k následující podmínky:  
  
- Pokud koncový uživatel nainstaluje obě verze, aplikace bude načten obou Add-ins VSTO.  
  
- Pokud doplňku VSTO byl nainstalován předtím, než došlo ke změně názvu sestavení, koncový uživatel nikdy přijímat aktualizace.  
  
  Aby se zabránilo těchto podmínek, neměňte řešení **název sestavení** hodnota po nasazení řešení.  
  
## <a name="check-for-updates-takes-a-long-time"></a>Zkontrolujte, zda aktualizace trvá moc dlouho  
 Visual Studio 2010 Tools for Office runtime obsahuje položky registru, která správcům umožňuje nastavit hodnotu časového limitu pro stahování manifestů a řešení.  
  
#### <a name="to-set-the-time-out-value"></a>Chcete-li nastavit hodnotu časového limitu  
  
1.  V registru přejděte na následující klíč:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**  
  
2.  V **AddInTimeout** podklíč, nastavte hodnotu časového limitu v milisekundách.  
  
     Pokud **AddInTimeout** podklíč neexistuje, vytvořte ho typu DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nelze aktualizovat nebo publikovat do sdíleného síťového umístění  
 Řešení pro systém Office, které jsou ve sdílené síti může zobrazit zavádějící zprávu při aktualizacích, pokud toto řešení *Setup.exe* soubor je uzamčen v procesu, když se publikuje aktualizace. Zpráva se může jednat následující: "nelze přidat"setup.exe"na webu. Soubor setup.exe už na tomto webu."  
  
 Zabraňte se zamykáním souborů, můžete nastavit sdílenou složku jen pro čtení koncovým uživatelům. Nicméně pokud dokumenty ve sdílené složce, také budou jen pro čtení koncovým uživatelům.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Požadavky pro Microsoft Office nejsou nainstalovány.  
 Rozhraní .NET Framework, můžete přidat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]a primární spolupracující sestavení Office do instalačního balíčku jako požadavky, které jsou nasazené v rámci řešení pro Office. Informace o postupu instalace primárních sestavení vzájemné spolupráce naleznete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) a [postupy: sestavení primární spolupráce Office nainstalovat](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publikovat pomocí "Localhost" může způsobit problémy s instalací  
 Při použití "<http://localhost>" jako umístění publikování nebo instalaci řešení na úrovni dokumentu, **Průvodce publikováním** nebude tak řetězec převést na název skutečné počítače. V takovém případě řešení musí být nainstalováno ve vývojovém počítači. Chcete-li nasazené řešení používají službu IIS na vývojovém počítači, místo localhost použijte plně kvalifikovaný název pro všechna místa protokolu HTTP/HTTPS nebo FTP.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>V mezipaměti sestavení nejsou načtena místo aktualizované sestavení  
 Zavaděč sestavení rozhraní .NET Framework Fusion načte kopii sestavení v mezipaměti, když výstupní cesta projektu je ve sdílené síti, je sestavení podepsáno pomocí silného názvu a nedojde ke změně verze sestavení vlastního nastavení. Při aktualizaci sestavení, které splňuje tyto podmínky, aktualizace se už nebude při příštím spuštění projektu, protože je načtena kopie v mezipaměti.  
  
 Visual Studio můžete nakonfigurovat tak, aby Fusion stáhne sestavení pokaždé, když spuštění projektu.  
  
### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Chcete-li stáhnout sestavení namísto načítání kopie v mezipaměti  
  
1. V panelu nabídky zvolte **projektu**, _ProjectName_**vlastnosti**.  
  
2. Na **aplikace** zvolte **informace o sestavení**.  
  
3. V prvním **verze sestavení** , zadejte hvězdičku (\*) a klikněte na tlačítko **OK** tlačítko.  
  
   Po změně verze sestavení, můžete pokračovat k podepsání sestavení silným názvem a Fusion načte nejnovější verzi vlastního nastavení.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Instalace selže, pokud identifikátor URI obsahuje znaky, které nejsou US-ASCII  
 Při publikování řešení Office na umístění protokolu HTTP/HTTPS nebo FTP, cesta nemůže obsahovat libovolné znaky Unicode, které nejsou v US-ASCII. Tyto znaky může způsobit nekonzistentní chování v instalačním programu. Používejte US-ASCII znaky pro cestu instalace.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Při publikování a instalaci řešení na vývojovém počítači, zobrazí se výzva k ruční odinstalaci  
 Při sestavování řešení pro Office, verze buildu se automaticky registruje. Pokud jste dříve publikované a nainstalována do stejného řešení na vývojovém počítači, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zjistí, že Instalační cesta pro vytvořené a publikované verze se liší, jakmile řešení dále vytvořen, znovu sestavit nebo publikovali. Chybová zpráva "přizpůsobení nelze nainstalovat, protože jiná verze je nainstalovaná a nedá se upgradovat z tohoto umístění." Klíče registru se aktualizují pokaždé, když se je znovu sestavit řešení. Proto před je nutné odinstalovat předchozí verzi publikovat, ladit nebo spouštět na novou verzi.  
  
 Chcete-li zabránit zobrazování zprávy, vytvořte další účet uživatele na vašem vývojovém počítači k otestování nasazení. Jako alternativu můžete odinstalovat verze ze seznamu nainstalovaných programů v počítači před dalším publikování, ladění nebo znovu sestavte řešení.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Došlo k nezachycené výjimce nebo metoda chyby při instalaci řešení nebyl nalezen  
 Při instalaci Office řešení pomocí otevření manifestu nasazení ( *.vsto* souboru), může se zobrazit Office aplikace, dokumentu nebo sešitu, chybové zprávy byly splněny následující podmínky:  
  
- Metoda nebyla nalezena.  
  
- MissingMethodException.  
  
- Došlo k nezachycené výjimce.  
  
  Chcete-li tyto chybové zprávy, nainstalujte řešení spuštěním instalačního programu.  
  
  Při instalaci řešení bez nutnosti spuštění instalačního programu Instalační program nebude kontrolovat nebo instalace požadovaných součástí. Instalační program zkontroluje požadavky na správnou verzi a nainstaluje je podle potřeby.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest klíče registru pro doplňky změnit, jakmile je vytvořen projekt InstallShield Limited Edition  
 Klíč registru manifestu, který je součástí instalace doplňku VSTO program někdy změny z *.vsto* k *. dll.manifest* při sestavení projekt InstallShield Limited Edition.  
  
 Chcete-li tento problém obejít, vytvoření projektu InstallShield Limited Edition v jiné řešení nebo použijte CompanyName.AddinName jako hodnotu klíče registru, který obsahuje název doplňku VSTO.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalační program ClickOnce pro řešení Office neinstaluje primárních sestavení vzájemné spolupráce  
 Když spustíte instalační program, který vytvoří ClickOnce pro řešení Office, instalační program pro Office primární sestavení interop (PIA) spustí jenom v případě, že žádná sestavení PIA jsou již nainstalovány.  
  
 Instalační program není správně nainstalováno PIA, je nainstalovat ručně spuštěním instalačního programu soubor, který je pojmenován *o2007pia.msi* z instalačního adresáře.  
  
## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Znovu nainstalujte Office řešení způsobí, že argument výjimka mimo rozsah  
 Při přeinstalaci řešení pro Office, <xref:System.ArgumentOutOfRangeException> výjimek se může zobrazit chybová zpráva: určený argument byl mimo rozsah platných hodnot.  
  
 K této situaci dochází v případě malých a velkých písmen pro adresu URL pro umístění instalace je odlišná. Například tato chyba objeví, pokud jste nainstalovali řešení pro Office v [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) poprvé a pak použít [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) podruhé.  
  
 Chcete-li zabránit zobrazování zprávy, použijte při instalaci řešení pro systém Office se stejnou velikostí písmen.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nelze nainstalovat z webu otevřou manifest nasazení ClickOnce řešení  
 Uživatelé mohou nainstalovat řešení pro systém Office pomocí otevření manifestu nasazení z webu. Nicméně některé instalace Internetové informační služby (IIS) blokovat *.vsto* příponu názvu souboru. Typ MIME musí definovat ve službě IIS, než ho použijete k nasazení řešení Office.  
  
 Informace o tom, jak definovat typ MIME ve službě IIS 7 najdete v tématu [přidat typ MIME (IIS7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Nastavení rozšíření **.vsto** a typ MIME **application/x-ms-vsto**.  
  
## <a name="see-also"></a>Viz také:  
 [Řešení potíží s nasazením ClickOnce](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  