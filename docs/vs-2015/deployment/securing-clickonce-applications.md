---
title: Zabezpečování aplikací ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: ae5bd70a675798d971cb184038a7e036d04fc95a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247218"
---
# <a name="securing-clickonce-applications"></a>Zabezpečování aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace jsou v souladu s omezením zabezpečení přístupu kódu v rozhraní .NET Framework pomáhají omezit přístupu k chráněným prostředkům a operacím. Z tohoto důvodu je důležité, že chápete důsledky zabezpečení přístupu kódu k zápisu vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace odpovídajícím způsobem. K omezení přístupu mohou vaše aplikace používat plnou důvěryhodnost nebo částečné zóny, jako jsou zóny pro Internet a Intranet.  
  
 Dále lze použít technologii ClickOnce využívající certifikáty k ověření pravosti vydavatele a podepisování manifestů aplikace a nasazení, která ověřuje, zda se soubory nebylo manipulováno. Podepisování je volitelný krok, který usnadňuje změnu souborů aplikace po vytvoření manifestů. Bez podepsaných manifestů je však obtížné zajistit, aby nebylo s instalačním programem manipulováno při bezpečnostních útocích prostředníkem. Chcete-li aplikaci zabezpečit, doporučujeme vám, abyste podepsali manifesty aplikace a nasazení.  
  
## <a name="zones"></a>Zóny  
 Aplikace, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologie jsou omezeny na sadu oprávnění a akcí, které jsou definovány zónou zabezpečení. Zóny zabezpečení jsou definovány v aplikaci Internet Explorer a jsou založeny na umístění aplikace. V následující tabulce jsou uvedena výchozí oprávnění na základě umístění nasazení:  
  
|Umístění nasazení|Zóna zabezpečení|  
|-------------------------|-------------------|  
|Spuštění z webu|Zóna Internetu|  
|Instalace z webu|Zóna Internetu|  
|Instalace ze sdíleného síťového umístění|Zóna Místního intranetu|  
|Instalace z disku CD-ROM|Plná důvěryhodnost|  
  
 Výchozí oprávnění jsou založena na umístění, ze kterého byla nasazena původní verze aplikace; aktualizace aplikace tato oprávnění zdědí. Pokud je aplikace nakonfigurována pro vyhledání aktualizací z webového nebo síťového umístění a je k dispozici novější verze, mohou původní instalace namísto oprávnění plné důvěryhodnosti přijímat oprávnění pro zónu Internetu nebo Intranetu. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Pro počítače, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Chcete-li konfigurovat nasazení důvěryhodné aplikace, lze certifikát nainstalovat na úrovni počítače nebo podniku. Další informace najdete v tématu [postupy: Přidání důvěryhodného vydavatele na klientský počítač pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Zásady zabezpečení přístupu kódu  
 Oprávnění pro aplikaci jsou určena nastavením v [ \<trustInfo > Element](../deployment/trustinfo-element-clickonce-application.md) elementu v manifestu aplikace. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky generuje tyto informace podle nastavení v projektu **zabezpečení** stránku vlastností. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace jsou udělena pouze specifická oprávnění, která aplikace požaduje. V případech, kdy například přístup k souborům vyžaduje oprávnění plné důvěryhodnosti, pokud aplikace požaduje oprávnění přístupu k souborům, bude uděleno pouze oprávnění přístupu k souborům, nikoli oprávnění plné důvěryhodnosti. Při vývoji vaší [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, ujistěte se, zda požadujete pouze konkrétní oprávnění, které aplikace potřebuje. Ve většině případů můžete nastavit omezení aplikace na částečnou důvěryhodnost pomocí zóny Internetu a Místního intranetu. Další informace najdete v tématu [postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Pokud aplikace požaduje vlastní oprávnění, můžete vytvořit vlastní zónu. Další informace najdete v tématu [postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Pokud použijete oprávnění, které není součástí výchozího oprávnění nastaveného pro zónu, ze které je aplikace nasazena, zobrazí se koncovému uživateli při instalaci nebo aktualizaci výzva k udělení oprávnění. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Na počítačích, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva.  
  
 Jako vývojář se musíte přesvědčit, zda lze aplikaci spustit i s příslušnými oprávněními. Pokud aplikace po spuštění požádá o oprávnění mimo zónu, může se zobrazit výjimka zabezpečení. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umožňuje ladit aplikaci v cílové zóně zabezpečení. a poskytuje pomoc při vývoji bezpečných aplikací. Další informace najdete v tématu [postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Další informace o zabezpečení přístupu kódu a technologii ClickOnce naleznete v tématu [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certifikáty podepisování kódu  
 K publikování aplikace pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, můžete podepsat manifesty aplikace a nasazení aplikace pomocí dvojice veřejného/soukromého klíče. Nástroje pro podepsání manifestu jsou k dispozici na **podepisování** stránku **Návrháře projektu**. Další informace najdete v tématu [stránka podepisování, Návrhář projektu](../ide/reference/signing-page-project-designer.md). Alternativně můžete manifesty můžete podepsat pomocí souboru klíče při procesu publikování pomocí Průvodce publikováním.  
  
 Po podepsání manifestů jsou informace o vydavateli aplikace založené na signatuře technologie Authenticode zobrazeny uživateli při instalaci v dialogovém okně oprávnění, a to proto, aby uživatel věděl, že aplikace pochází z důvěryhodného zdroje.  
  
 Další informace o technologii ClickOnce a certifikátech najdete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Ověřování založené na formulářích ASP.NET  
 Pokud chcete řídit kterým nasazením mají jednotliví uživatelé mít přístup, neměli byste povolit anonymní přístup k [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nasazené na webovém serveru. Místo toho byste měli povolit uživatelům přístup k nainstalovaným nasazením na základě identity uživatele pomocí ověřování systému Windows.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nepodporuje ověřování založené na formulářích ASP.NET, protože používá trvalé soubory cookie. Tyto představovat bezpečnostní riziko, protože jsou uloženy v mezipaměti aplikace Internet Explorer a mohou být zneužity. Proto pokud nasazujete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, není podporován žádný scénář ověřování kromě ověřování Windows.  
  
## <a name="passing-arguments"></a>Předávání argumentů  
 K posouzení další bezpečnostní dochází, pokud je nutné předat argumenty do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] umožňuje vývojářům zadat řetězec dotazu aplikacím nasazeným prostřednictvím webu. Řetězec dotazu má formu řady párů názvu a hodnoty na konci adresy URL určených ke spuštění aplikace:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Argumenty řetězce dotazu jsou zakázány. Aby se mohly, atribut `trustUrlParameters` musí být nastavena v manifestu nasazení aplikace. Tuto hodnotu můžete nastavit od [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a z MageUI.exe. Podrobné pokyny o postupu povolení předávání řetězce dotazu naleznete v tématu [postupy: načtení informací řetězce dotazu do Online aplikace ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Nikdy byste neměli předávat argumenty načtené pomocí řetězce dotazu do databáze nebo příkazového řádku bez ověřování argumentů a zajištění jejich bezpečnosti. Nebezpečné argumenty jsou argumenty s řídicími znaky databáze nebo příkazového řádku, které by mohly umožnit uživateli se zlými úmysly manipulaci s aplikací a provádění libovolných příkazů.  
  
> [!NOTE]
>  Argumenty řetězce dotazu jsou pouze způsobem předávání argumentů [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] při spuštění aplikace. Argumenty nelze předat [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace z příkazového řádku.  
  
## <a name="deploying-obfuscated-assemblies"></a>Nasazení obfuskovaných sestavení  
 Obfuskací aplikace pomocí nástroje Dotfuscator můžete zabránit ostatním uživatelům ve zpětné analýze kódu. Obfuskace sestavení však není integrována do integrovaného vývojového prostředí sady Visual Studio nebo procesu nasazení technologie ClickOnce. Proto budete muset provést obfuskaci mimo proces nasazení, případně pomocí kroku po sestavení. Po sestavení projektu byste měli následující kroky provést ručně mimo sadu Visual Studio:  
  
1.  Provádění obfuskace pomocí nástroje Dotfuscator.  
  
2.  Pro generování manifestů technologie ClickOnce a jejich podepsání použijte nástroje Mage.exe nebo MageUI.exe. Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) a [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3.  Ručně publikujte (zkopírujte) soubory do zdrojového umístění nasazení (webový server, sdílené složky UNC nebo disk CD-ROM).  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



