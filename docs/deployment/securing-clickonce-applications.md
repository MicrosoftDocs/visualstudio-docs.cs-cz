---
title: Zabezpečování aplikací ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/17/2017
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56a49bf9cbf2c43cd7692592b53b9aca2b256313
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080337"
---
# <a name="secure-clickonce-applications"></a>Zabezpečení aplikací ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace jsou v souladu s omezením zabezpečení přístupu kódu v rozhraní .NET Framework pomáhají omezit přístupu k chráněným prostředkům a operacím. Z tohoto důvodu je důležité, že chápete důsledky zabezpečení přístupu kódu k zápisu vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace odpovídajícím způsobem. K omezení přístupu mohou vaše aplikace používat plnou důvěryhodnost nebo částečné zóny, jako jsou zóny pro Internet a Intranet.  
  
 Dále lze použít technologii ClickOnce využívající certifikáty k ověření pravosti vydavatele a podepisování manifestů aplikace a nasazení, která ověřuje, zda se soubory nebylo manipulováno. Podepisování je volitelný krok, který usnadňuje změnu souborů aplikace po vytvoření manifestů. Bez podepsaných manifestů je však obtížné zajistit, aby nebylo s instalačním programem manipulováno při bezpečnostních útocích prostředníkem. Chcete-li aplikaci zabezpečit, doporučujeme vám, abyste podepsali manifesty aplikace a nasazení.  
  
## <a name="zones"></a>Zóny  
 Aplikace, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie jsou omezeny na sadu oprávnění a akcí, které jsou definovány zónou zabezpečení. Zóny zabezpečení jsou definovány v aplikaci Internet Explorer a jsou založeny na umístění aplikace. V následující tabulce jsou uvedena výchozí oprávnění na základě umístění nasazení:  
  
|Umístění nasazení|Zóna zabezpečení|  
|-------------------------|-------------------|  
|Spuštění z webu|Zóna Internetu|  
|Instalace z webu|Zóna Internetu|  
|Instalace ze sdíleného síťového umístění|Zóna Místního intranetu|  
|Instalace z disku CD-ROM|Plná důvěryhodnost|  
  
 Výchozí oprávnění jsou založena na umístění, ze kterého byla nasazena původní verze aplikace; aktualizace aplikace tato oprávnění zdědí. Pokud je aplikace nakonfigurována pro vyhledání aktualizací z webového nebo síťového umístění a je k dispozici novější verze, mohou původní instalace namísto oprávnění plné důvěryhodnosti přijímat oprávnění pro zónu Internetu nebo Intranetu. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Pro počítače, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Chcete-li konfigurovat nasazení důvěryhodné aplikace, lze certifikát nainstalovat na úrovni počítače nebo podniku. Další informace najdete v tématu [postupy: Přidání důvěryhodného vydavatele na klientský počítač pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Zásady zabezpečení přístupu kódu  
 Oprávnění pro aplikaci jsou určena nastavením v [ \<trustInfo > Element](../deployment/trustinfo-element-clickonce-application.md) elementu v manifestu aplikace. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky generuje tyto informace podle nastavení v projektu **zabezpečení** stránku vlastností. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace jsou udělena pouze specifická oprávnění, která aplikace požaduje. V případech, kdy například přístup k souborům vyžaduje oprávnění plné důvěryhodnosti, pokud aplikace požaduje oprávnění přístupu k souborům, bude uděleno pouze oprávnění přístupu k souborům, nikoli oprávnění plné důvěryhodnosti. Při vývoji vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, ujistěte se, zda požadujete pouze konkrétní oprávnění, které aplikace potřebuje. Ve většině případů můžete nastavit omezení aplikace na částečnou důvěryhodnost pomocí zóny Internetu a Místního intranetu. Další informace najdete v tématu [postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Pokud aplikace požaduje vlastní oprávnění, můžete vytvořit vlastní zónu. Další informace najdete v tématu [postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Pokud použijete oprávnění, které není součástí výchozího oprávnění nastaveného pro zónu, ze které je aplikace nasazena, zobrazí se koncovému uživateli při instalaci nebo aktualizaci výzva k udělení oprávnění. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Na počítačích, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva.  
  
 Jako vývojář se musíte přesvědčit, zda lze aplikaci spustit i s příslušnými oprávněními. Pokud aplikace po spuštění požádá o oprávnění mimo zónu, může se zobrazit výjimka zabezpečení. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] umožňuje ladit aplikaci v cílové zóně zabezpečení. a poskytuje pomoc při vývoji bezpečných aplikací. Další informace najdete v tématu [postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Další informace o zabezpečení přístupu kódu a technologii ClickOnce naleznete v tématu [zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certifikát pro podpis kódu  
 K publikování aplikace pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, můžete podepsat manifesty aplikace a nasazení aplikace pomocí dvojice veřejného/soukromého klíče. Nástroje pro podepsání manifestu jsou k dispozici na **podepisování** stránku **Návrháře projektu**. Další informace najdete v tématu [stránka podepisování, Návrhář projektu](../ide/reference/signing-page-project-designer.md). Alternativně můžete manifesty můžete podepsat pomocí souboru klíče při procesu publikování pomocí Průvodce publikováním.  
  
 Po podepsání manifestů jsou informace o vydavateli aplikace založené na signatuře technologie Authenticode zobrazeny uživateli při instalaci v dialogovém okně oprávnění, a to proto, aby uživatel věděl, že aplikace pochází z důvěryhodného zdroje.  
  
 Další informace o technologii ClickOnce a certifikátech najdete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Ověřování založené na formulářích ASP.NET  
 Pokud chcete řídit kterým nasazením mají jednotliví uživatelé mít přístup, neměli byste povolit anonymní přístup k [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nasazené na webovém serveru. Místo toho byste měli povolit uživatelům přístup k nainstalovaným nasazením na základě identity uživatele pomocí ověřování systému Windows.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nepodporuje ověřování založené na formulářích ASP.NET, protože používá trvalé soubory cookie. Tyto představovat bezpečnostní riziko, protože jsou uloženy v mezipaměti aplikace Internet Explorer a mohou být zneužity. Proto pokud nasazujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, není podporován žádný scénář ověřování kromě ověřování Windows.  
  
## <a name="pass-arguments"></a>Předání argumentů  
 K posouzení další bezpečnostní dochází, pokud je nutné předat argumenty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] umožňuje vývojářům zadat řetězec dotazu aplikacím nasazeným prostřednictvím webu. Řetězec dotazu má formu řady párů názvu a hodnoty na konci adresy URL určených ke spuštění aplikace:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Argumenty řetězce dotazu jsou zakázány. Aby se mohly, atribut `trustUrlParameters` musí být nastavena v manifestu nasazení aplikace. Tuto hodnotu můžete nastavit od [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a z MageUI.exe. Podrobné pokyny o postupu povolení předávání řetězce dotazu naleznete v tématu [postupy: načtení informací řetězce dotazu do online aplikace ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Nikdy byste neměli předávat argumenty načtené pomocí řetězce dotazu do databáze nebo příkazového řádku bez ověřování argumentů a zajištění jejich bezpečnosti. Nebezpečné argumenty jsou argumenty s řídicími znaky databáze nebo příkazového řádku, které by mohly umožnit uživateli se zlými úmysly manipulaci s aplikací a provádění libovolných příkazů.  
  
> [!NOTE]
>  Argumenty řetězce dotazu jsou pouze způsobem předávání argumentů [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] při spuštění aplikace. Argumenty nelze předat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace z příkazového řádku.  
  
## <a name="deploying-obfuscated-assemblies"></a>Nasazení obfuskovaných sestavení  
 Visual Studio zahrnuje bezplatnou [PreEmptive ochranu – nástroj Dotfuscator Community Edition](../ide/dotfuscator/index.md), který můžete použít k ochraně vašich aplikací ClickOnce pomocí obfuskace kódu a aktivní ochranná opatření.  Podrobnosti najdete v tématu [ClickOnce část uživatelské příručce nástroje Dotfuscator Community Edition](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Viz také:  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)