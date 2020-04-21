---
title: Zabezpečení aplikací ClickOnce | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 6743e08517a8b360d7635f11b6d3a0c0d84c780f
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649407"
---
# <a name="secure-clickonce-applications"></a>Zabezpečení aplikací ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikace podléhají omezením zabezpečení přístupu kódu v rozhraní .NET Framework, aby pomohly omezit přístup, který má kód k chráněným prostředkům a operacím. Z tohoto důvodu je důležité, abyste pochopili důsledky zabezpečení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] přístupu kódu k odpovídajícímzpůsobem zapsat aplikace. K omezení přístupu mohou vaše aplikace používat plnou důvěryhodnost nebo částečné zóny, jako jsou zóny pro Internet a Intranet.

 Dále lze použít technologii ClickOnce využívající certifikáty k ověření pravosti vydavatele a podepisování manifestů aplikace a nasazení, která ověřuje, zda se soubory nebylo manipulováno. Podepisování je volitelný krok, který usnadňuje změnu souborů aplikace po vytvoření manifestů. Bez podepsaných manifestů je však obtížné zajistit, aby nebylo s instalačním programem manipulováno při bezpečnostních útocích prostředníkem. Chcete-li aplikaci zabezpečit, doporučujeme vám, abyste podepsali manifesty aplikace a nasazení.

## <a name="zones"></a>Zóny
 Aplikace, které jsou [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazeny pomocí technologie jsou omezeny na sadu oprávnění a akcí, které jsou definovány zóny zabezpečení. Zóny zabezpečení jsou definovány v aplikaci Internet Explorer a jsou založeny na umístění aplikace. V následující tabulce jsou uvedena výchozí oprávnění na základě umístění nasazení:

|Umístění nasazení|Zóna zabezpečení|
|-------------------------|-------------------|
|Spuštění z webu|Zóna Internetu|
|Instalace z webu|Zóna Internetu|
|Instalace ze sdíleného síťového umístění|Zóna Místního intranetu|
|Instalace z disku CD-ROM|Plná důvěryhodnost|

 Výchozí oprávnění jsou založena na umístění, ze kterého byla nasazena původní verze aplikace; aktualizace aplikace tato oprávnění zdědí. Pokud je aplikace nakonfigurována pro vyhledání aktualizací z webového nebo síťového umístění a je k dispozici novější verze, mohou původní instalace namísto oprávnění plné důvěryhodnosti přijímat oprávnění pro zónu Internetu nebo Intranetu. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Pro počítače, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva. Další informace naleznete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md). Chcete-li konfigurovat nasazení důvěryhodné aplikace, lze certifikát nainstalovat na úrovni počítače nebo podniku. Další informace naleznete v [tématu How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Zásady zabezpečení přístupu kódu
 Oprávnění pro aplikaci jsou určena nastavením v elementu [ \<trustInfo> Element](../deployment/trustinfo-element-clickonce-application.md) manifestu aplikace. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automaticky generuje tyto informace na základě nastavení na stránce vlastností **zabezpečení** projektu. Aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jsou udělena pouze určitá oprávnění, která požaduje. V případech, kdy například přístup k souborům vyžaduje oprávnění plné důvěryhodnosti, pokud aplikace požaduje oprávnění přístupu k souborům, bude uděleno pouze oprávnění přístupu k souborům, nikoli oprávnění plné důvěryhodnosti. Při vývoji aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] byste se měli ujistit, že požadujete pouze konkrétní oprávnění, která aplikace potřebuje. Ve většině případů můžete nastavit omezení aplikace na částečnou důvěryhodnost pomocí zóny Internetu a Místního intranetu. Další informace naleznete v [tématu Postup: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Pokud aplikace požaduje vlastní oprávnění, můžete vytvořit vlastní zónu. Další informace naleznete v [tématu Postup: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

 Pokud použijete oprávnění, které není součástí výchozího oprávnění nastaveného pro zónu, ze které je aplikace nasazena, zobrazí se koncovému uživateli při instalaci nebo aktualizaci výzva k udělení oprávnění. Chcete-li zabránit v zobrazování výzev uživatelům, může správce systému zadat zásady nasazení technologie ClickOnce, které definují konkrétního vydavatele aplikace jako důvěryhodný zdroj. Na počítačích, na kterých je tato zásada nasazena, budou oprávnění udělena automaticky a uživateli nebude zobrazena žádná výzva.

 Jako vývojář se musíte přesvědčit, zda lze aplikaci spustit i s příslušnými oprávněními. Pokud aplikace po spuštění požádá o oprávnění mimo zónu, může se zobrazit výjimka zabezpečení. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]umožňuje ladit aplikaci v cílové zóně zabezpečení. a poskytuje pomoc při vývoji zabezpečených aplikací. Další informace naleznete v [tématu How to: Debug a ClickOnce application with restricted permissions](securing-clickonce-applications.md).

 Další informace o zabezpečení přístupu kódu a ClickOnce naleznete v [tématu Zabezpečení přístupu kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Podpisové certifikáty kódu
 Chcete-li publikovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci pomocí nasazení, můžete podepsat manifesty aplikace a nasazení pro aplikaci pomocí dvojice veřejného a soukromého klíče. Nástroje pro podepisování manifestu jsou k dispozici na stránce **Podepisování** **Návrháře projektu**. Další informace naleznete v [tématu Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md). Manifesty můžete také podepsat pomocí klíčového souboru během procesu publikování pomocí Průvodce publikováním.

 Po podepsání manifestů jsou informace o vydavateli aplikace založené na signatuře technologie Authenticode zobrazeny uživateli při instalaci v dialogovém okně oprávnění, a to proto, aby uživatel věděl, že aplikace pochází z důvěryhodného zdroje.

 Další informace o clickonce a certifikátech naleznete v [tématech ClickOnce a Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>ASP.NET ověřování založené na formulářích
 Pokud chcete řídit, ke kterým nasazením má každý uživatel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] přístup, neměli byste povolit anonymní přístup k aplikacím nasazeným na webovém serveru. Místo toho byste měli povolit uživatelům přístup k nainstalovaným nasazením na základě identity uživatele pomocí ověřování systému Windows.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]nepodporuje ověřování pomocí ASP.NET formulářů, protože používá trvalé soubory cookie. Ty představují bezpečnostní riziko, protože jsou umístěny v mezipaměti aplikace Internet Explorer a mohou být napadeny hackery. Proto pokud nasazujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, není podporován žádný scénář ověřování kromě ověřování systému Windows.

## <a name="pass-arguments"></a>Předat argumenty
 Další aspekt zabezpečení dochází, pokud máte předat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] argumenty do aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]umožňuje vývojářům zadat řetězec dotazu aplikacím nasazeným přes web. Řetězec dotazu má formu řady párů názvu a hodnoty na konci adresy URL určených ke spuštění aplikace:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Argumenty řetězce dotazu jsou zakázány. Chcete-li je `trustUrlParameters` povolit, musí být atribut nastaven v manifestu nasazení aplikace. Tuto hodnotu lze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nastavit z a z MageUI.exe. Podrobné kroky k povolení předávání řetězců dotazu naleznete v [tématu Postup: Načtení informací o řetězci dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Nikdy byste neměli předávat argumenty načtené pomocí řetězce dotazu do databáze nebo příkazového řádku bez ověřování argumentů a zajištění jejich bezpečnosti. Nebezpečné argumenty jsou argumenty s řídicími znaky databáze nebo příkazového řádku, které by mohly umožnit uživateli se zlými úmysly manipulaci s aplikací a provádění libovolných příkazů.

> [!NOTE]
> Argumenty řetězce dotazu jsou jediným způsobem, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jak předat argumenty aplikaci při spuštění. Argumenty nelze předat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci z příkazového řádku.

## <a name="deploying-obfuscated-assemblies"></a>Nasazení zamlžených sestavení
 Visual Studio obsahuje bezplatnou [preemptivní ochranu – komunitu Dotfuscator](../ide/dotfuscator/index.md), kterou můžete použít k ochraně aplikací ClickOnce prostřednictvím zamlžení kódu a aktivních ochranných opatření.  Podrobnosti naleznete [v části ClickOnce v uživatelské příručce komunity Dotfuscator](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)