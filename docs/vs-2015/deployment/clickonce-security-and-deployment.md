---
title: Zabezpečení a nasazení ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 592bf358c24bee146290e8b3a00e28a0870f452d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263805"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce – zabezpečení a nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je technologie nasazení, která umožňuje vytvářet samoobslužné aplikace pro Windows, které se dají nainstalovat a spustit s minimální interakcí uživatelů. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje úplnou podporu pro publikování a aktualizaci aplikací nasazených pomocí technologie ClickOnce, pokud jste vytvořili projekty pomocí Visual Basic a Visual C#. Informace o nasazení Visual C++ch aplikací naleznete v tématu [nasazení ClickOnce pro Visual C++ aplikace](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení přináší tři hlavní problémy v nasazení:  
  
- **Problémy při aktualizaci aplikací.** Při nasazení Microsoft Instalační služba systému Windows, když je aplikace aktualizovaná, může uživatel nainstalovat aktualizaci, soubor MSP a použít ho na nainstalovaný produkt. s [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazením můžete aktualizace poskytovat automaticky. Stáhnou se jenom ty části aplikace, které se změnily, a pak se znovu nainstaluje plná aktualizovaná aplikace z nové souběžné složky.  
  
- **Dopad na počítač uživatele.** Při nasazení Instalační služba systému Windows aplikace často spoléhají na sdílené součásti, a to s potenciálem pro konflikty verzí. v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] případě nasazení je každá aplikace samostatná a nemůže narušovat jiné aplikace.  
  
- **Oprávnění zabezpečení.** Nasazení Instalační služba systému Windows vyžaduje oprávnění správce a povoluje jenom omezené uživatelské instalace. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení umožňuje uživatelům bez oprávnění správce instalovat a udělit pouze oprávnění zabezpečení přístupu ke kódu, která jsou nezbytná pro aplikaci.  
  
  V minulosti se tyto problémy někdy způsobily vývojářům, kteří se chtějí rozhodnout vytvořit webové aplikace namísto aplikací pro Windows a zmírnit tak bohatě uživatelské rozhraní pro usnadnění instalace. Pomocí aplikací, které jsou nasazené pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , můžete mít ty nejlepší z obou technologií.  
  
## <a name="what-is-a-clickonce-application"></a>Co je aplikace ClickOnce?  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Aplikace je jakýkoli Windows Presentation Foundation (. XBAP), model Windows Forms (. exe), konzolová aplikace (. exe) nebo řešení Office (. dll) publikované pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologie. Aplikaci můžete publikovat [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] třemi různými způsoby: z webové stránky, ze sdílené síťové složky nebo z média, jako je například CD-ROM. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Aplikaci lze nainstalovat do počítače koncového uživatele a spustit místně i v případě, že je počítač v režimu offline nebo je možné jej spustit v režimu pouze online, aniž by bylo nutné trvale instalovat cokoli v počítači koncového uživatele. Další informace najdete v tématu [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace může být samoobslužná aktualizace. můžou vyhledat novější verze, jakmile budou k dispozici, a automaticky nahradí všechny aktualizované soubory. Vývojář může určit chování aktualizace; Správce sítě může také řídit strategie aktualizace, například označit aktualizaci jako povinnou. Aktualizace je také možné vrátit zpět na předchozí verzi koncovým uživatelem nebo správcem. Další informace najdete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Vzhledem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] k tomu, že aplikace jsou izolované, instalace nebo spuštění [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nemůže přerušit stávající aplikace. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace jsou samostatně obsaženy. Každá [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace je nainstalována pro a spouštěna z zabezpečené mezipaměti pro jednotlivé uživatele a aplikace. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace běží v zónách zabezpečení Internet nebo intranet. V případě potřeby může aplikace požádat o zvýšená oprávnění zabezpečení. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Jak funguje zabezpečení ClickOnce  
 Základní [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zabezpečení je založeno na certifikátech, zásadách zabezpečení přístupu ke kódu a na výzvu vztahu důvěryhodnosti ClickOnce.  
  
### <a name="certificates"></a>Certifikáty  
 Certifikáty Authenticode slouží k ověření pravosti vydavatele aplikace. Pomocí technologie Authenticode pro nasazení aplikace pomáhá ClickOnce zabránit škodlivému programu v stojímeě jako legitimní program pocházející z vytvořeného, důvěryhodného zdroje. V případě potřeby lze certifikáty použít také k podepsání manifestů aplikace a nasazení, aby bylo možné prokázat, že soubory nebyly úmyslně poškozeny. Další informace naleznete v tématu [ClickOnce a Authenticode](../deployment/clickonce-and-authenticode.md). Certifikáty lze také použít ke konfiguraci klientských počítačů tak, aby měly seznam důvěryhodných vydavatelů. Pokud aplikace pochází z důvěryhodného vydavatele, dá se nainstalovat bez zásahu uživatele. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Zabezpečení přístupu kódu pomáhá omezit přístup tohoto kódu k chráněným prostředkům. Ve většině případů můžete zvolit zóny Internet nebo místní intranet pro omezení oprávnění. Použijte stránku **zabezpečení** v **ProjectDesigner** k vyžádání zóny vhodné pro aplikaci. Můžete také ladit aplikace s omezenými oprávněními a emulovat činnost koncového uživatele. Další informace najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Dotaz na vztah důvěryhodnosti pro ClickOnce  
 Pokud aplikace požaduje více oprávnění, než je tato zóna povolena, může být koncový uživatel vyzván, aby si vyžádal rozhodnutí o důvěryhodnosti. Koncový uživatel se může rozhodnout, jestli aplikace ClickOnce jako model Windows Forms aplikace, Windows Presentation Foundation aplikace, konzolové aplikace, aplikace prohlížeče XAML a řešení pro Office mají důvěryhodné spouštění. Další informace naleznete v tématu [How to: Configure a Behavior pro zobrazení výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Jak funguje nasazení ClickOnce  
 Základní [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] architektura nasazení vychází ze dvou souborů MANIFESTU XML: manifestu aplikace a manifestu nasazení. Soubory se používají k popisu, kde jsou aplikace ClickOnce nainstalovány, jak jsou aktualizovány a kdy jsou aktualizovány.  
  
### <a name="publishing-clickonce-applications"></a>Publikování aplikací ClickOnce  
 Manifest aplikace popisuje samotnou aplikaci. To zahrnuje sestavení, závislosti a soubory, které tvoří aplikaci, požadovaná oprávnění a umístění, kde budou k dispozici aktualizace. Vývojář aplikace autoři manifestu aplikace pomocí Průvodce publikováním v aplikaci Visual Studio nebo Manifest Generation and Editing Tool (Mage.exe) v [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Manifest nasazení popisuje, jak je aplikace nasazena. To zahrnuje umístění manifestu aplikace a verzi aplikace, kterou by klienti měli spouštět.  
  
### <a name="deploying-clickonce-applications"></a>Nasazení aplikací ClickOnce  
 Po vytvoření se manifest nasazení zkopíruje do umístění nasazení. Může to být webový server, síťová sdílená složka nebo médium, jako je například CD. Manifest aplikace a všechny soubory aplikace jsou také zkopírovány do umístění nasazení, které je zadáno v manifestu nasazení. To může být stejné jako umístění nasazení, nebo může být jiné umístění. Při použití **Průvodce publikováním** v aplikaci Visual Studio se operace kopírování provádějí automaticky.  
  
### <a name="installing-clickonce-applications"></a>Instalace aplikací ClickOnce  
 Po nasazení do umístění nasazení mohou koncoví uživatelé aplikaci stáhnout a nainstalovat kliknutím na ikonu představující soubor manifestu nasazení na webové stránce nebo ve složce. Ve většině případů se koncovému uživateli zobrazí jednoduché dialogové okno s výzvou, aby uživatel zkontroloval instalaci. po instalaci pokračuje a aplikace se spustí bez dalšího zásahu. V případech, kdy aplikace vyžaduje zvýšená oprávnění, nebo pokud aplikace není podepsaná důvěryhodným certifikátem, dialogové okno také vyzve uživatele k udělení oprávnění, než může instalace pokračovat. I když jsou ClickOnce instalovány pro jednotlivé uživatele, může být vyžadováno zvýšení oprávnění, pokud existují požadavky, které vyžadují oprávnění správce. Další informace o zvýšených oprávněních naleznete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certifikáty mohou být důvěryhodné na úrovni počítače nebo podniku tak, aby aplikace ClickOnce podepsané důvěryhodným certifikátem mohly být bezobslužně nainstalovány. Další informace o důvěryhodných certifikátech naleznete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
 Aplikaci lze přidat do nabídky **Start** uživatele a do skupiny **Přidat nebo odebrat programy** v **Ovládacích panelech**. Na rozdíl od jiných technologií nasazení není nic přidáno do složky **Program Files** ani do registru a k instalaci nejsou potřeba žádná práva správce.  
  
> [!NOTE]
> Je také možné zabránit tomu, aby se aplikace přidala do nabídky **Start** a skupiny **Přidat nebo odebrat programy** , aby se chovala jako webová aplikace. Další informace najdete v tématu [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Aktualizují se aplikace ClickOnce.  
 Když vývojáři aplikace vytvoří aktualizovanou verzi aplikace, vygenerují nový manifest aplikace a zkopírují soubory do umístění nasazení (obvykle do složky na stejné úrovni) do původní složky nasazení aplikace. Správce aktualizuje manifest nasazení tak, aby odkazoval na umístění nové verze aplikace.  
  
> [!NOTE]
> K provedení těchto kroků lze použít **Průvodce publikováním** v aplikaci Visual Studio.  
  
 Kromě umístění nasazení obsahuje manifest nasazení také umístění aktualizace (webová stránka nebo síťová sdílená složka), kde aplikace kontroluje aktualizované verze. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Vlastnosti **publikování** se používají k určení, kdy a jak často by měla aplikace vyhledávat aktualizace. Chování aktualizace může být zadáno v manifestu nasazení nebo může být prezentováno jako volby uživatele v uživatelském rozhraní aplikace prostřednictvím [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rozhraní API. Kromě toho mohou být použity vlastnosti **publikování** , aby byly aktualizace povinné nebo vráceny zpět na předchozí verzi. Další informace najdete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instalátory třetích stran  
 Můžete přizpůsobit instalační program ClickOnce pro instalaci komponent jiných výrobců společně s vaší aplikací. Musíte mít redistribuovatelný balíček (soubor. exe nebo. msi) a popsat balíček pomocí jazykově neutrálního manifestu produktu a manifestu konkrétního jazykového balíčku. Další informace najdete v tématu [vytváření balíčků zaváděcího nástroje](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Nástroje ClickOnce  
 V následující tabulce jsou uvedeny nástroje, které můžete použít ke generování, úpravám, podepisování a opětovnému podepisování manifestů aplikace a nasazení.  
  
|Nástroj|Popis|  
|----------|-----------------|  
|[Stránka Zabezpečení, návrhář projektu](../ide/reference/security-page-project-designer.md)|Podepíše manifesty aplikace a nasazení.|  
|[Publikovat stránku, návrhář projektu](../ide/reference/publish-page-project-designer.md)|Generuje a upravuje manifesty aplikace a nasazení pro aplikace Visual Basic a Visual C#.|  
|[Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Generuje manifesty aplikace a nasazení pro aplikace Visual Basic, Visual C# a Visual C++.<br /><br /> Podepíše a znovu podepíše manifesty aplikace a nasazení.<br /><br /> Lze spustit ze skriptů Batch a příkazového řádku.|  
|[MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|Generuje a upravuje manifesty aplikace a nasazení.<br /><br /> Podepíše a znovu podepíše manifesty aplikace a nasazení.|  
|[GenerateApplicationManifest – – úloha](../msbuild/generateapplicationmanifest-task.md)|Generuje manifest aplikace.<br /><br /> Dá se spustit z MSBuild. Další informace naleznete v tématu [referenční](../msbuild/msbuild-reference.md)dokumentace nástroje MSBuild.|  
|[GenerateDeploymentManifest – – úloha](../msbuild/generatedeploymentmanifest-task.md)|Vygeneruje manifest nasazení.<br /><br /> Dá se spustit z MSBuild. Další informace naleznete v tématu [referenční](../msbuild/msbuild-reference.md)dokumentace nástroje MSBuild.|  
|[SignFile – – úloha](../msbuild/signfile-task.md)|Podepíše manifesty aplikace a nasazení.<br /><br /> Dá se spustit z MSBuild. Další informace naleznete v tématu [referenční](../msbuild/msbuild-reference.md)dokumentace nástroje MSBuild.|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Vývoj vlastní aplikace pro generování manifestů aplikace a nasazení.|  
  
 Následující tabulka ukazuje .NET Framework verze, která je nutná k podpoře aplikací ClickOnce v těchto prohlížečích.  
  
|Prohlížeč|Verze rozhraní .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2,0, 3,0, 3,5, 3,5 SP1, 4|  
|Firefox|2,0 SP1, 3,5 SP1, 4|  
  
## <a name="see-also"></a>Viz také  
 [Nasazení ClickOnce v systému Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Nasazení komponent modelu COM pomocí technologie ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Sestavování aplikací ClickOnce z příkazového řádku](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Ladění aplikací ClickOnce používajících System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
