---
title: Zabezpečení aplikací ClickOnce | Microsoft Docs
ms.date: 02/17/2017
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09d447a33e73c2f27598b027788b3cf1dcd2822b
ms.sourcegitcommit: 960bab34e126c9ca449560a76a839a8f8c3263fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82139634"
---
# <a name="secure-clickonce-applications"></a>Zabezpečení aplikací ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikace podléhají omezením zabezpečení přístupu kódu v .NET Framework pro omezení přístupu kódu k chráněným prostředkům a operacím. Z tohoto důvodu je důležité pochopit důsledky zabezpečení přístupu kódu k odpovídajícímu zápisu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací. K omezení přístupu mohou vaše aplikace používat plnou důvěryhodnost nebo částečné zóny, jako jsou zóny pro Internet a Intranet.

 Dále lze použít technologii ClickOnce využívající certifikáty k ověření pravosti vydavatele a podepisování manifestů aplikace a nasazení, která ověřuje, zda se soubory nebylo manipulováno. Podepisování je volitelný krok, který usnadňuje změnu souborů aplikace po vytvoření manifestů. Bez podepsaných manifestů je však obtížné zajistit, aby nebylo s instalačním programem manipulováno při bezpečnostních útocích prostředníkem. Chcete-li aplikaci zabezpečit, doporučujeme vám, abyste podepsali manifesty aplikace a nasazení.

## <a name="zones"></a>Zóny
 Aplikace, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie, jsou omezeny na sadu oprávnění a akcí, které jsou definovány zónou zabezpečení. Zóny zabezpečení jsou definovány v aplikaci Internet Explorer a jsou založeny na umístění aplikace. V následující tabulce jsou uvedena výchozí oprávnění na základě umístění nasazení:

|Umístění nasazení|Zóna zabezpečení|
|-------------------------|-------------------|
|Spuštění z webu|Zóna Internetu|
|Instalace z webu|Zóna Internetu|
|Instalace ze sdíleného síťového umístění|Zóna Místního intranetu|
|Instalace z disku CD-ROM|Plná důvěryhodnost|

 Výchozí oprávnění jsou založena na umístění, ze kterého byla nasazena původní verze aplikace; aktualizace aplikace tato oprávnění zdědí. Pokud je aplikace nakonfigurována pro vyhledání aktualizací z webového nebo síťového umístění a je k dispozici novější verze, mohou původní instalace namísto oprávnění plné důvěryhodnosti přijímat oprávnění pro zónu Internetu nebo Intranetu. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Pro počítače, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md). Chcete-li konfigurovat nasazení důvěryhodné aplikace, lze certifikát nainstalovat na úrovni počítače nebo podniku. Další informace najdete v tématu [Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Zásady zabezpečení přístupu kódu
 Oprávnění pro aplikaci jsou určena nastavením v elementu [ \<trustInfo> elementu](../deployment/trustinfo-element-clickonce-application.md) manifestu aplikace. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automaticky generuje tyto informace na základě nastavení na stránce vlastností **zabezpečení** projektu. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aplikaci jsou udělena pouze konkrétní oprávnění, která požaduje. V případech, kdy například přístup k souborům vyžaduje oprávnění plné důvěryhodnosti, pokud aplikace požaduje oprávnění přístupu k souborům, bude uděleno pouze oprávnění přístupu k souborům, nikoli oprávnění plné důvěryhodnosti. Při vývoji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace byste měli mít jistotu, že požadujete pouze specifická oprávnění, která aplikace potřebuje. Ve většině případů můžete nastavit omezení aplikace na částečnou důvěryhodnost pomocí zóny Internetu a Místního intranetu. Další informace najdete v tématu [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Pokud aplikace požaduje vlastní oprávnění, můžete vytvořit vlastní zónu. Další informace najdete v tématu [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

 Pokud použijete oprávnění, které není součástí výchozího oprávnění nastaveného pro zónu, ze které je aplikace nasazena, zobrazí se koncovému uživateli při instalaci nebo aktualizaci výzva k udělení oprávnění. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Na počítačích, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva.

 Jako vývojář se musíte přesvědčit, zda lze aplikaci spustit i s příslušnými oprávněními. Pokud aplikace po spuštění požádá o oprávnění mimo zónu, může se zobrazit výjimka zabezpečení. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]umožňuje ladit aplikaci v cílové zóně zabezpečení. a poskytuje vám podporu při vývoji zabezpečených aplikací. Další informace najdete v tématu [ladění aplikací ClickOnce používajících System. Deployment. Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md).

 Další informace o zabezpečení přístupu kódu a ClickOnce naleznete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Certifikáty pro podepisování kódu
 Chcete-li publikovat aplikaci pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, můžete podepsat manifest aplikace a nasazení pro aplikaci pomocí páru veřejného a privátního klíče. Nástroje pro podepsání manifestu jsou k dispozici na stránce **podepisování** v **Návrháři projektu**. Další informace naleznete v tématu [Podepisování stránky, Návrhář projektu](../ide/reference/signing-page-project-designer.md). Alternativně můžete manifesty podepsat pomocí souboru klíče během procesu publikování pomocí Průvodce publikováním.

 Po podepsání manifestů jsou informace o vydavateli aplikace založené na signatuře technologie Authenticode zobrazeny uživateli při instalaci v dialogovém okně oprávnění, a to proto, aby uživatel věděl, že aplikace pochází z důvěryhodného zdroje.

 Další informace o ClickOnce a certifikátech naleznete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>Ověřování založené na formulářích ASP.NET
 Pokud chcete určit, ke kterým nasazením mají jednotliví uživatelé přístup, neměli byste povolit anonymní přístup k [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacím nasazeným na webovém serveru. Místo toho byste měli povolit uživatelům přístup k nainstalovaným nasazením na základě identity uživatele pomocí ověřování systému Windows.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]nepodporuje ověřování založené na formulářích ASP.NET, protože používá trvalé soubory cookie; představují bezpečnostní riziko, protože se nacházejí v mezipaměti aplikace Internet Explorer a můžou být napadené. Proto pokud nasazujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, jakýkoli scénář ověřování kromě ověřování systému Windows není podporován.

## <a name="pass-arguments"></a>Předat argumenty
 Další aspekty zabezpečení nastane, pokud musíte předat argumenty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]umožňuje vývojářům zadat řetězec dotazu k aplikacím nasazeným přes web. Řetězec dotazu má formu řady párů názvu a hodnoty na konci adresy URL určených ke spuštění aplikace:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Argumenty řetězce dotazu jsou zakázány. Aby je bylo možné povolit, `trustUrlParameters` musí být atribut nastaven v manifestu nasazení aplikace. Tuto hodnotu lze nastavit z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a z MageUI. exe. Podrobné informace o tom, jak povolit předávání řetězců dotazů, naleznete v tématu [How to: načítají se informace o řetězci dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Nikdy byste neměli předávat argumenty načtené pomocí řetězce dotazu do databáze nebo příkazového řádku bez ověřování argumentů a zajištění jejich bezpečnosti. Nebezpečné argumenty jsou argumenty s řídicími znaky databáze nebo příkazového řádku, které by mohly umožnit uživateli se zlými úmysly manipulaci s aplikací a provádění libovolných příkazů.

> [!NOTE]
> Argumenty řetězce dotazu jsou jediným způsobem, jak předat argumenty [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci při spuštění. Do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nelze předat argumenty z příkazového řádku.

## <a name="deploying-obfuscated-assemblies"></a>Nasazení zavedených sestavení
 Součástí sady Visual Studio je bezplatná [komunita Dotfuscator na ochranu před](../ide/dotfuscator/index.md)zneužitím, kterou můžete použít k ochraně aplikací ClickOnce prostřednictvím zmatení kódu a aktivních ochranných opatření.  Podrobnosti najdete v [části ClickOnce v uživatelské příručce komunity Dotfuscator](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
