---
title: ClickOnce – zabezpečení a nasazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd089b57fb50d20c8805c932b0043bb8c0dba82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926446"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce – zabezpečení a nasazení
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je technologie nasazení, která vám umožní vytvořit automatických aktualizací aplikace založené na Windows, které mohou být nainstalovány a spuštěny vyžadují minimální interakci uživatele. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poskytuje plnou podporu pro publikování a aktualizace aplikací nasazených pomocí technologie ClickOnce, pokud jste vytvořili projekt v jazyce Visual Basic a Visual C#. Informace o nasazení aplikací v jazyce Visual C++, naleznete v tématu [ClickOnce – nasazení pro aplikace Visual C++](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení překonává tři hlavní problémy v nasazení:  
  
- **Chcete-li vyřešit potíže při aktualizaci aplikace.** Pomocí nasazení Instalační služby systému Windows při každé aktualizaci aplikace, uživatel může nainstalovat aktualizaci, soubor msp a použijte ji pro u nainstalovaného produktu; s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, můžete poskytnout aktualizace automaticky. Jsou staženy pouze ty části aplikace, které se změnily a plná aktualizovaná aplikace se znovu z nové složky vedle sebe.  
  
- **Dopad na počítači uživatele.** Pomocí nasazení Instalační služby systému Windows aplikace se často spoléhat na sdílené komponenty, s potenciálními konfliktu verzí; s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, každá aplikace je samostatná a nelze v konfliktu s jinými aplikacemi.  
  
- **Oprávnění zabezpečení.** Nasazení Instalační služby systému Windows vyžaduje oprávnění pro správu a umožňuje pouze omezený uživatelský instalaci. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení umožňuje uživatelům bez oprávnění správce k instalaci a udělí jenom ty zabezpečení přístupu kódu potřebná oprávnění pro aplikaci.  
  
  V minulosti těchto problémů může někdy dojít vývojáři rozhodnout vytvářet webové aplikace namísto aplikace pro systém Windows, byste museli obětovat bohatého uživatelského rozhraní pro usnadnění instalace. Pomocí aplikace nasazené pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], máte to nejlepší z obou technologií.  
  
## <a name="what-is-a-clickonce-application"></a>Co je aplikace ClickOnce?  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je všechny Windows Presentation Foundation (*.xbap*), Windows Forms (*.exe*), konzolové aplikace (*.exe*), nebo řešení pro Office (*.dll*) publikované pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie. Můžete publikovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci třemi různými způsoby: z webové stránky, ze síťových sdílených složek nebo z média, například na disku CD-ROM. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace může v počítači koncového uživatele nainstalován a spustit místně i v případě, že je počítač v režimu offline, nebo ho můžete spustit v režimu pouze v režimu online, bez nutnosti trvale nic instalace v počítači koncového uživatele. Další informace najdete v tématu [volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace může být automatických aktualizací; tyto novější verze, které jsou k dispozici a automaticky nahradit všechny aktualizované soubory můžete zkontrolovat. Vývojář můžete určit chování aktualizací; Správce sítě můžete také řídit strategie, například označení aktualizace jako povinné aktualizace. Aktualizace můžete také vrátit zpět na starší verzi koncovým uživatelem nebo správcem. Další informace najdete v tématu [volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Protože [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace jsou izolovány instalaci nebo spuštění [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nelze přerušit stávající aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace jsou samostatné; Každý [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je nainstalovaná a spustit z zabezpečení jednotlivých uživatelů, mezipaměti podle aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace běží v zónách zabezpečení Internetu nebo intranetu. V případě potřeby aplikace můžete požádat o oprávnění se zvýšenými oprávněními zabezpečení. Další informace najdete v tématu [zabezpečení ClickOnce applications](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Jak funguje zabezpečení ClickOnce  
 Základní [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zabezpečení je založeno na certifikáty, zásady zabezpečení přístupu kódu a vztahu důvěryhodnosti ClickOnce.  
  
### <a name="certificates"></a>Certifikáty  
 Authenticode certifikáty se používají k ověření pravosti vydavatele. Pomocí technologie Authenticode pro nasazení aplikace ClickOnce pomáhá zabránit vydávání sama sebe jako legitimní program pocházejí z důvěryhodného zdroje a zavedené škodlivý program. Volitelně se certifikáty lze také použít k podepsání aplikace a manifesty nasazení prokázat, že soubory nebylo manipulováno. Další informace najdete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md). Certifikáty lze použít také ke konfiguraci klientských počítačů, aby seznam důvěryhodných vydavatelů. Pokud aplikace pochází z důvěryhodného vydavatele, je možné nainstalovat bez nutnosti zásahu uživatele. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Kód přístupu secrity pomáhá omezit přístupu k chráněným prostředkům. Ve většině případů můžete omezit oprávnění zón Internetu a místního intranetu. Použití **zabezpečení** stránku **ProjectDesigner** požádat o zóně vhodný pro aplikaci. Můžete také ladit aplikace s omezenými oprávněními k emulaci činnost koncového uživatele. Další informace najdete v tématu [zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Výzvy důvěryhodnosti ClickOnce  
 Pokud aplikace požaduje více oprávnění než umožňuje zóny, koncový uživatel může vyzváni k provedení rozhodnutí důvěryhodnosti. Koncový uživatel mohl určit, pokud jsou důvěryhodné pro spuštění aplikace ClickOnce, jako je aplikace Windows Forms, aplikace Windows Presentation Foundation, konzolové aplikace, aplikace prohlížeče XAML a řešení pro systém Office. Další informace najdete v tématu [postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Jak funguje nasazení ClickOnce  
 Základní [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení architektura je založená na dvou souborů manifestu XML: manifest aplikace a manifest nasazení. Soubory se používají k popisu nainstalovanou aplikací ClickOnce z způsob, jakým se aktualizuje a kdy jsou aktualizovány.  
  
### <a name="publish-clickonce-applications"></a>Publikování aplikací ClickOnce  
 Popisuje manifest aplikace samotná aplikace. To zahrnuje sestavení, závislosti a soubory, které tvoří aplikaci, požadovaná oprávnění a umístění, kde budou k dispozici aktualizace. Vývojář aplikace autory manifest aplikace pomocí Průvodce publikováním v sadě Visual Studio nebo Manifest Generation and Editing Tool (*Mage.exe*) v [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Další informace najdete v tématu [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Manifest nasazení popisuje, jak je aplikace nasazená. To zahrnuje umístění manifestu aplikace a verze aplikace, které by klienti měli spouštět.  
  
### <a name="deploy-clickonce-applications"></a>Nasazení aplikací ClickOnce  
 Po jeho vytvoření, manifest nasazení zkopírován do umístění nasazení. To může být webového serveru, sdíleného síťového umístění nebo média, například z disku CD. Manifest aplikace a všechny soubory aplikace jsou zkopírovány také do umístění nasazení, která je určená v manifestu nasazení. To může být stejné jako umístění pro nasazení, nebo může být jiné umístění. Při použití **Průvodce publikováním** v sadě Visual Studio, operace kopírování se provádí automaticky.  
  
### <a name="install-clickonce-applications"></a>Instalace aplikací ClickOnce  
 Po nasazení do umístění nasazení, koncovým uživatelům můžete stáhnout a nainstalovat aplikaci kliknutím na ikonu představující soubor manifestu nasazení na webové stránce nebo ve složce. Ve většině případů se zobrazí koncovému uživateli se jednoduché dialogové okno s výzvou k potvrzení instalace, po které instalací a spuštění aplikace bez dalšího zásahu uživatele. V případech, kdy aplikace vyžaduje zvýšenou úroveň oprávnění nebo pokud aplikace není podepsán důvěryhodným certifikátem dialogové okno také žádá uživatele, aby udělil oprávnění, než mohla pokračovat instalace. I když instalace ClickOnce jsou jednotlivé uživatele, zvýšení úrovně oprávnění může být vyžadováno, pokud jsou požadavky, které vyžadují oprávnění správce. Další informace o zvýšenou úroveň oprávnění najdete v tématu [zabezpečení ClickOnce applications](../deployment/securing-clickonce-applications.md).  
  
 Certifikáty může být důvěryhodné na úrovni počítače nebo podniku tak, že můžete provést tichou instalaci aplikace ClickOnce podepsané důvěryhodným certifikátem. Další informace o důvěryhodných certifikátů najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
 Aplikace mohou být přidány do daného uživatele **Start** nabídky a **přidat nebo odebrat programy** skupiny **ovládací panely**. Na rozdíl od jiných technologií nasazení není nic přidáno do **Program Files** složky nebo registru a žádná práva pro správu se vyžadují pro instalaci  
  
> [!NOTE]
>  Je také možné zabránit aplikaci v přidávaný do **Start** nabídky a **přidat nebo odebrat programy** skupiny, ve skutečnosti chová jako webová aplikace. Další informace najdete v tématu [volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="update-clickonce-applications"></a>Aktualizace aplikací ClickOnce  
 Když vývojáři aplikace vytvořit aktualizovanou verzi aplikace, vygenerovat nový manifest aplikace a zkopírujte soubory do umístění nasazení – obvykle na stejné úrovni složku pro původní nasazení aplikace. Správce aktualizuje manifest nasazení tak, aby odkazoval na umístění novou verzi aplikace.  
  
> [!NOTE]
>  **Průvodce publikováním** v sadě Visual Studio lze použít k provedení těchto kroků.  
  
 Kromě nasazení umístění manifestu nasazení také obsahuje umístění aktualizace (webové stránky nebo síťové sdílené), kde bude aplikace ověřovat aktualizované verze. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publikování** vlastnosti se používají k určení, kdy a jak často by měla aplikace vyhledávat aktualizace. Chování aktualizace se dá nastavit v manifestu nasazení nebo ji lze zobrazit jako volby uživatele v uživatelském rozhraní aplikace prostřednictvím [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rozhraní API. Kromě toho **publikovat** vlastnosti mohou být použity, proveďte aktualizace povinné nebo vrátit zpět na předchozí verzi. Další informace najdete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instalační programy třetích stran  
 Instalační program ClickOnce a nainstalujte komponenty třetích stran spolu s vaší aplikace můžete přizpůsobit. Musíte mít Distribuovatelný balíček (soubor .exe nebo .msi) a Popis balíčku s manifestu produktu jazykově neutrální a specifické pro jazyk balíček manifestu. Další informace najdete v tématu [vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Nástroje ClickOnce tools  
 V následující tabulce jsou uvedeny nástroje, vám pomůže generovat, upravit, přihlaste a znovu podepište manifesty aplikace a nasazení.  
  
|Nástroj|Popis|  
|----------|-----------------|  
|[Stránka Zabezpečení, Návrhář projektu](../ide/reference/security-page-project-designer.md)|Příznaky manifesty aplikace a nasazení.|  
|[Stránka Publikovat, Návrhář projektu](../ide/reference/publish-page-project-designer.md)|Generuje a úpravy manifestů aplikací a nasazení pro aplikace Visual Basic a Visual C#.|  
|[*Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Generuje manifesty aplikace a nasazení aplikací Visual Basic, Visual C# a Visual C++.<br /><br /> Podepíše a znovu podepíše manifesty aplikace a nasazení.<br /><br /> Můžete spouštět z dávkových skriptů a příkazový řádek.|  
|[*MageUI.exe* (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Generuje a úpravy manifestů aplikací a nasazení.<br /><br /> Podepíše a znovu podepíše manifesty aplikace a nasazení.|  
|[Generateapplicationmanifest – úloha](../msbuild/generateapplicationmanifest-task.md)|Generuje manifest aplikace.<br /><br /> Můžete spustit z nástroje MSBuild. Další informace najdete v tématu [MSBuild reference](../msbuild/msbuild-reference.md).|  
|[Generatedeploymentmanifest – úloha](../msbuild/generatedeploymentmanifest-task.md)|Generuje manifest nasazení.<br /><br /> Můžete spustit z nástroje MSBuild. Další informace najdete v tématu [MSBuild reference](../msbuild/msbuild-reference.md).|  
|[Signfile – úloha](../msbuild/signfile-task.md)|Příznaky manifesty aplikace a nasazení.<br /><br /> Můžete spustit z nástroje MSBuild. Další informace najdete v tématu [MSBuild reference](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Vyvíjejte vlastní aplikaci a generovat manifesty aplikace a nasazení.|  
  
 V následující tabulce jsou uvedeny verze rozhraní .NET Framework, které jsou potřeba pro podporu aplikací ClickOnce v těchto prohlížečích.  
  
|Prohlížeč|Verze rozhraní .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, VERZE 3.5 SP1, 4|  
|Firefox|2.0 SP1, VERZE 3.5 SP1, 4|  
  
## <a name="see-also"></a>Viz také:  
 [ClickOnce – nasazení v systému Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Nasazování komponent COM s ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Vytváření aplikací ClickOnce z příkazového řádku](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Ladění aplikací ClickOnce používajících System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)