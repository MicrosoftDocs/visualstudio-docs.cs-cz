---
title: Zabezpečení aplikací ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2610c1fef92bb77d150dad7972bb991b6ef4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686013"
---
# <a name="securing-clickonce-applications"></a>Zabezpečování aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace podléhají omezením zabezpečení přístupu kódu v .NET Framework pro omezení přístupu kódu k chráněným prostředkům a operacím. Z tohoto důvodu je důležité pochopit důsledky zabezpečení přístupu kódu k [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] odpovídajícímu zápisu aplikací. K omezení přístupu mohou vaše aplikace používat plnou důvěryhodnost nebo částečné zóny, jako jsou zóny pro Internet a Intranet.  
  
 Dále lze použít technologii ClickOnce využívající certifikáty k ověření pravosti vydavatele a podepisování manifestů aplikace a nasazení, která ověřuje, zda se soubory nebylo manipulováno. Podepisování je volitelný krok, který usnadňuje změnu souborů aplikace po vytvoření manifestů. Bez podepsaných manifestů je však obtížné zajistit, aby nebylo s instalačním programem manipulováno při bezpečnostních útocích prostředníkem. Chcete-li aplikaci zabezpečit, doporučujeme vám, abyste podepsali manifesty aplikace a nasazení.  
  
## <a name="zones"></a>Zóny  
 Aplikace, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologie, jsou omezeny na sadu oprávnění a akcí, které jsou definovány zónou zabezpečení. Zóny zabezpečení jsou definovány v aplikaci Internet Explorer a jsou založeny na umístění aplikace. V následující tabulce jsou uvedena výchozí oprávnění na základě umístění nasazení:  
  
|Umístění nasazení|Zóna zabezpečení|  
|-------------------------|-------------------|  
|Spuštění z webu|Zóna Internetu|  
|Instalace z webu|Zóna Internetu|  
|Instalace ze sdíleného síťového umístění|Zóna Místního intranetu|  
|Instalace z disku CD-ROM|Plná důvěryhodnost|  
  
 Výchozí oprávnění jsou založena na umístění, ze kterého byla nasazena původní verze aplikace; aktualizace aplikace tato oprávnění zdědí. Pokud je aplikace nakonfigurována pro vyhledání aktualizací z webového nebo síťového umístění a je k dispozici novější verze, mohou původní instalace namísto oprávnění plné důvěryhodnosti přijímat oprávnění pro zónu Internetu nebo Intranetu. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Pro počítače, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md). Chcete-li konfigurovat nasazení důvěryhodné aplikace, lze certifikát nainstalovat na úrovni počítače nebo podniku. Další informace najdete v tématu [Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Zásady zabezpečení přístupu kódu  
 Oprávnění pro aplikaci jsou určena nastavením v [ \<trustInfo> elementu elementu manifestu](../deployment/trustinfo-element-clickonce-application.md) aplikace. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky generuje tyto informace na základě nastavení na stránce vlastností **zabezpečení** projektu. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Aplikaci jsou udělena pouze konkrétní oprávnění, která požaduje. V případech, kdy například přístup k souborům vyžaduje oprávnění plné důvěryhodnosti, pokud aplikace požaduje oprávnění přístupu k souborům, bude uděleno pouze oprávnění přístupu k souborům, nikoli oprávnění plné důvěryhodnosti. Při vývoji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace byste měli mít jistotu, že požadujete pouze specifická oprávnění, která aplikace potřebuje. Ve většině případů můžete nastavit omezení aplikace na částečnou důvěryhodnost pomocí zóny Internetu a Místního intranetu. Další informace najdete v tématu [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Pokud aplikace požaduje vlastní oprávnění, můžete vytvořit vlastní zónu. Další informace najdete v tématu [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Pokud použijete oprávnění, které není součástí výchozího oprávnění nastaveného pro zónu, ze které je aplikace nasazena, zobrazí se koncovému uživateli při instalaci nebo aktualizaci výzva k udělení oprávnění. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Na počítačích, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva.  
  
 Jako vývojář se musíte přesvědčit, zda lze aplikaci spustit i s příslušnými oprávněními. Pokud aplikace po spuštění požádá o oprávnění mimo zónu, může se zobrazit výjimka zabezpečení. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umožňuje ladit aplikaci v cílové zóně zabezpečení. a poskytuje vám podporu při vývoji zabezpečených aplikací. Další informace naleznete v tématu [How to: Debug a aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Další informace o zabezpečení přístupu kódu a ClickOnce naleznete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certifikáty podepisování kódu  
 Chcete-li publikovat aplikaci pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, můžete podepsat manifest aplikace a nasazení pro aplikaci pomocí páru veřejného a privátního klíče. Nástroje pro podepsání manifestu jsou k dispozici na stránce **podepisování** v **Návrháři projektu**. Další informace naleznete v tématu [Podepisování stránky, Návrhář projektu](../ide/reference/signing-page-project-designer.md). Alternativně můžete manifesty podepsat pomocí souboru klíče během procesu publikování pomocí Průvodce publikováním.  
  
 Po podepsání manifestů jsou informace o vydavateli aplikace založené na signatuře technologie Authenticode zobrazeny uživateli při instalaci v dialogovém okně oprávnění, a to proto, aby uživatel věděl, že aplikace pochází z důvěryhodného zdroje.  
  
 Další informace o ClickOnce a certifikátech naleznete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Ověřování založené na formulářích ASP.NET  
 Pokud chcete určit, ke kterým nasazením mají jednotliví uživatelé přístup, neměli byste povolit anonymní přístup k [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacím nasazeným na webovém serveru. Místo toho byste měli povolit uživatelům přístup k nainstalovaným nasazením na základě identity uživatele pomocí ověřování systému Windows.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nepodporuje ověřování založené na formulářích ASP.NET, protože používá trvalé soubory cookie; představují bezpečnostní riziko, protože se nacházejí v mezipaměti aplikace Internet Explorer a můžou být napadené. Proto pokud nasazujete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, jakýkoli scénář ověřování kromě ověřování systému Windows není podporován.  
  
## <a name="passing-arguments"></a>Předávání argumentů  
 Další aspekty zabezpečení nastane, pokud musíte předat argumenty do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] umožňuje vývojářům zadat řetězec dotazu k aplikacím nasazeným přes web. Řetězec dotazu má formu řady párů názvu a hodnoty na konci adresy URL určených ke spuštění aplikace:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Argumenty řetězce dotazu jsou zakázány. Aby je bylo možné povolit, `trustUrlParameters` musí být atribut nastaven v manifestu nasazení aplikace. Tuto hodnotu lze nastavit z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a z MageUI.exe. Podrobné informace o tom, jak povolit předávání řetězců dotazů, naleznete v tématu [How to: načítají se informace o řetězci dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Nikdy byste neměli předávat argumenty načtené pomocí řetězce dotazu do databáze nebo příkazového řádku bez ověřování argumentů a zajištění jejich bezpečnosti. Nebezpečné argumenty jsou argumenty s řídicími znaky databáze nebo příkazového řádku, které by mohly umožnit uživateli se zlými úmysly manipulaci s aplikací a provádění libovolných příkazů.  
  
> [!NOTE]
> Argumenty řetězce dotazu jsou jediným způsobem, jak předat argumenty [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci při spuštění. Do aplikace nelze předat argumenty [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z příkazového řádku.  
  
## <a name="deploying-obfuscated-assemblies"></a>Nasazení obfuskovaných sestavení  
 Obfuskací aplikace pomocí nástroje Dotfuscator můžete zabránit ostatním uživatelům ve zpětné analýze kódu. Obfuskace sestavení však není integrována do integrovaného vývojového prostředí sady Visual Studio nebo procesu nasazení technologie ClickOnce. Proto budete muset provést obfuskaci mimo proces nasazení, případně pomocí kroku po sestavení. Po sestavení projektu byste měli následující kroky provést ručně mimo sadu Visual Studio:  
  
1. Provádění obfuskace pomocí nástroje Dotfuscator.  
  
2. Pro generování manifestů technologie ClickOnce a jejich podepsání použijte nástroje Mage.exe nebo MageUI.exe. Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) a [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3. Ručně publikujte (zkopírujte) soubory do zdrojového umístění nasazení (webový server, sdílené složky UNC nebo disk CD-ROM).  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
