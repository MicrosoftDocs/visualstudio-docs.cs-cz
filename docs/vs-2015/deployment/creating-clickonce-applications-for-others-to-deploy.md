---
title: Vytváření aplikací ClickOnce pro ostatní osobami | Dokumentace Microsoftu
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
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f2b7bb6c990567a483ab28d215019fe1b259d166
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862083"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Vytváření aplikací ClickOnce k implementaci dalšími osobami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ne všichni vývojáři, kteří vytvářejí nasazení ClickOnce v plánu nasadit samotnými aplikacemi. Mnohé z nich stačí zabalit svoje aplikace s použitím technologie ClickOnce a poté soubory pro zákazníka, jako je například velké korporace. Zákazník bude ten, který je zodpovědný za hostování aplikací ve své síti. Toto téma popisuje některé potíže spočívající v takovýchto nasazeních ve verzích rozhraní .NET Framework starší než verze 3.5. Popisuje pak k dispozici v rozhraní .NET Framework 3.5 pomocí nové funkce "použít manifest pro vztah důvěryhodnosti" nové řešení. A konečně dojde k závěru, informace o doporučených strategiích pro vytváření ClickOnce – nasazení pro zákazníky, kteří stále používají starší verze rozhraní .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problémy při vytváření nasazení pro zákazníky  
 Několik problémů dojít, když plánujete dodávat nasazení pro zákazníka. První problém se týká, podepisování kódu. Aby bylo možné nasadit v síti, manifest nasazení a manifest aplikace ClickOnce – nasazení musí obě být podepsané digitálním certifikátem. To vyvolá na otázku, jestli se má použít pro vývojáře nebo certifikát zákazníka při podepisování manifestů.  
  
 Na otázku, který certifikát bude použit je velmi důležité, protože identita aplikace ClickOnce je založena na digitální podpis manifestu nasazení. Pokud vývojář podepisuje manifest nasazení, může vést ke konfliktu Pokud zákazník je velká společnost a více než jedna dělení společnost nasadí upravenou verzi aplikace.  
  
 Řekněme například, že má společnosti Adventure Works finančního oddělení a oddělení lidských zdrojů. Obě oddělení licenci aplikace ClickOnce od Microsoft Corporation, která generuje sestavy z dat uložených ve službě SQL database. Microsoft poskytuje každé oddělení s verzí aplikace, který je přizpůsobený pro svá data. V případě aplikace jsou podepsané stejným certifikátem Authenticode, by uživatel, který se pokusí použít obě aplikace dojde k chybě, protože ClickOnce bude považovat druhou aplikaci jako stejný jako první. V takovém případě se může na základě zkušeností uživatelů neočekávané a nežádoucí vedlejší účinky, které zahrnují ztráty všechna data uložená místně aplikací.  
  
 Další problém týkající se k podepisování kódu je `deploymentProvider` elementu v manifestu nasazení, který informuje, kde hledat aktualizace aplikace ClickOnce. Tento element musí být přidán do manifestu nasazení před podepsáním ho. Pokud tento prvek je přidán později, musí být znovu podepsat manifest nasazení.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Vyžadování zákazníkovi podepsat Manifest nasazení  
 Jedno řešení tohoto problému nejedinečné nasazení je, aby pro vývojáře podepsat manifest aplikace a zákazník podepsat manifest nasazení. Přestože tento přístup funguje, přináší další problémy. Protože certifikát Authenticode musí zůstat chráněný prostředek, nemůže zákazník dát certifikát pro vývojáře k podepsání nasazení. Když zákazník může podepsat manifest nasazení sami pomocí volně dostupných nástrojů sady SDK rozhraní .NET Framework, to může vyžadovat další technické znalosti, než je zákazník ochoten nebo schopen poskytnout. V takových případech Vývojáři obvykle vytvoří aplikaci, webové stránky nebo jiný mechanismus, pomocí kterého zákazníka můžete odeslat jejich verze aplikace pro podepisování.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Dopad podepisování zákazníka na zabezpečení aplikací ClickOnce  
 I v případě, že vývojář a zákazník souhlas, že zákazník musí podepsat manifest aplikace, to vyvolá další problémy, které před a za identitu aplikace, zejména když se vztahuje na nasazení důvěryhodné aplikace. (Další informace o této funkci najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Řekněme, že společnosti Adventure Works chce nakonfigurovat své klientské počítače tak, aby všechny aplikace, které poskytuje k nim společnost Microsoft Corporation běží s úplným vztahem důvěryhodnosti. Pokud společnosti Adventure Works podepíše manifest nasazení, pak technologie ClickOnce použije k určení úrovně důvěryhodnosti aplikace bezpečnostní Adventure signaturu.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Vytvoření zákaznická nasazení s použitím Manifest aplikace pro vztah důvěryhodnosti  
 ClickOnce v rozhraní .NET Framework 3.5 obsahuje novou funkci, která poskytuje vývojářům a zákazníkům nové řešení pro scénář toho, jak by měl být podepsané manifesty. ClickOnce – manifest aplikace podporuje nový prvek s názvem `<useManifestForTrust>` , která umožňuje vývojář, abyste mohli označit, že digitální podpis manifestu aplikace je to, co má být použito pro rozhodování o důvěryhodnosti. Vývojář používá nástroje pro balení ClickOnce, jako je například Mage.exe a MageUI.exe, Visual Studio – zahrňte tento prvek v manifestu aplikace, jakož i pro vložení názvu vydavatele a název aplikace v manifestu.  
  
 Při použití `<useManifestForTrust>`, manifest nasazení nemusí podepisovat certifikátem Authenticode vydaný certifikační autoritou. Místo toho můžete být podepsány pomocí co se označuje jako certifikát podepsaný svým držitelem. Certifikát podepsaný svým držitelem vygeneruje zákazníka nebo vývojáři použít standardní nástroje rozhraní .NET Framework SDK a pak použije k manifestu nasazení pomocí nástroje pro standardní nasazení ClickOnce. Další informace najdete v tématu [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 Použití certifikátu podepsaného svým držitelem pro manifest nasazení nabízí několik výhod. Odstraněním potřeby zákazníků získat nebo vytvořit vlastní certifikát Authenticode `<useManifestForTrust>` zjednodušuje nasazení pro zákazník, a zároveň umožní vývojářům udržovat svoji vlastní identitu značky v aplikaci. Výsledkem je sada podepsaných nasazení, které jsou bezpečnější a mají jedinečné identity aplikace. Tím se eliminují potenciální konflikt, který může být z nasazení stejné aplikace na více zákazníků.  
  
 Podrobné informace o tom, jak vytvořit nasazení ClickOnce pomocí `<useManifestForTrust>` povolena, najdete v článku [návod: Ruční nasazení aplikace ClickOnce této nemá není vyžadují Re-Signing a zachová značky informací](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Jak Manifest aplikace pro vztah důvěryhodnosti pracuje v době běhu  
 Pokud chcete získat lepší přehled o fungování manifest aplikace pomocí vztahu důvěryhodnosti v době běhu, zvažte následující příklad. Aplikace ClickOnce, která cílí na rozhraní .NET Framework 3.5 je vytvořen microsoftem. Manifest aplikace používá `<useManifestForTrust>` elementu a je podepsán společností Microsoft. Společnosti Adventure Works podepíše manifest nasazení pomocí certifikátu podepsaného svým držitelem. Adventure Works, které jsou klienti nakonfigurováni na vztah důvěryhodnosti všechny aplikace podepsané microsoftem.  
  
 Po kliknutí odkaz na manifest nasazení ClickOnce nainstaluje aplikaci na počítači uživatele. Informace o certifikátu a nasazení určete jednoznačně aplikaci ClickOnce v klientském počítači. Pokud se uživatel pokusí znovu nainstalovat stejnou aplikaci z jiného umístění, můžete použít ClickOnce tuto identitu k určení, zda aplikace již existuje na straně klienta.  
  
 V dalším kroku ClickOnce kontroluje Authenticode certifikát, který se používá k podepsání manifestu aplikace, která určuje úroveň vztahu důvěryhodnosti, který udělí ClickOnce. Od společnosti Adventure Works nakonfiguroval svým klientům důvěřovat všechny aplikace podepsané microsoftem, je tato aplikace ClickOnce udělena úplná důvěryhodnost. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Vytváření zákaznických nasazení u starších verzí  
 Co když vývojář je nasazování aplikací ClickOnce pro zákazníky, kteří používají starší verze rozhraní .NET Framework? Následující části shrnují několik doporučených řešení, společně s výhody a nevýhody jednotlivých.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Nasazení přihlášení jménem zákazníka  
 Jednou z možných strategií je to možné nasazení je pro vývojáře k vytvoření mechanismus pro podepisování nasazení zastoupení svých zákazníků s využitím zákazníka vlastní privátní klíč. To zabrání tomu, aby vývojáři by bylo potřeba spravovat soukromé klíče nebo více balíčků nasazení. Vývojář poskytuje stejné nasazení pro každého zákazníka. Záleží zákazníkovi, přizpůsobit ho pro jejich prostředí pomocí podpisové služby.  
  
 Jednou z nevýhod tato metoda je čas a náklady, které jsou nutné k jeho implementaci. Když například služba může být sestaven pomocí nástrojů sady SDK rozhraní .NET Framework, přidá další dobu vývoje do životního cyklu produktu.  
  
 Jak je uvedeno výše v tomto tématu, jiné nevýhodou je, že každého zákazníka verzi aplikace bude mít stejnou identitu aplikace, které by mohly vést ke konfliktu. Pokud se jedná o problém, Vývojář můžete změnit název pole, které se používá při generování manifestu nasazení pro každou aplikaci zadejte jedinečný název. To vytvoří samostatné identity pro každou verzi aplikace a eliminovat možným konfliktům identity. Toto pole odpovídá `-Name` argument pro Mage.exe a **název** pole na **název** kartu v MageUI.exe.  
  
 Řekněme například, že vývojář vytvořil aplikaci s názvem Application1. Místo vytváření jedno nasazení s názvem pole nastavena na Application1, Vývojář můžete vytvářet několik nasazení s zákaznického variace tohoto názvu, jako je například CustomerA Application1, Application1 CustomerB a tak dále.  
  
### <a name="deploy-using-a-setup-package"></a>Nasazení pomocí instalačního balíčku  
 Druhou strategií možné nasazení řešení je vytvořit projekt Microsoft Setup k provedení počáteční nasazení aplikace ClickOnce. To lze zadat v jednom z několika různých formátech: jako nasazení MSI součásti, jako spustitelný soubor (. Soubor EXE), nebo jako soubor CAB (.cab) společně s dávkový skript.  
  
 Tímto způsobem vývojáře by zadejte zákazník nasazení, který obsahuje soubory aplikace, manifest aplikace a manifest nasazení, která slouží jako šablony. Zákazník spustí instalační program, který by k zadání jejich adresa URL nasazení (server nebo sdílenou složku umístění, odkud budou uživatelé instalovat aplikace ClickOnce), a také digitální certifikát. Instalační program aplikace může také rozhodnout výzvu k zadání další možnosti konfigurace ClickOnce, jako je například interval aktualizace zkontrolujte. Jakmile tyto informace jsou shromažďovány, instalační program by generování manifestu reálného nasazení, podepište ho a publikování aplikace ClickOnce do umístění určeného serveru.  
  
 Existují tři způsoby, že zákazník může podepsat manifest nasazení v této situaci:  
  
1. Zákazník může použít platný certifikát vydaný certifikační autoritou (CA).  
  
2. Jako variantou tento přístup můžete zákazníka k podepsání manifestu nasazení pomocí certifikátu podepsaného svým držitelem. Nevýhodou je, že by aplikace mají zobrazovat slova "Neznámého vydavatele", když uživateli se zobrazí výzva, jestli ji chtějí mít nainstalovanou. Výhodou je, že zabrání v menších zákazníci museli ztrácet čas a peníze, vyžaduje se pro certifikát vydaný certifikační autoritou.  
  
3. A konečně Vývojář můžete zahrnout vlastní certifikát podepsaný svým držitelem instalační balíček. To představuje potenciální problémy s identitou aplikace uvedené dříve v tomto tématu.  
  
   Nevýhodou metodu instalace nasazení projektu je nutné k vytvoření vlastního nasazení aplikace vynakládat čas a prostředky.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Jste zákazník generovat Manifest nasazení  
 Třetí strategií je to možné nasazení je předat pouze soubory aplikace a manifest aplikace vypnout zákazníka. V tomto scénáři zákazník zodpovídá za použití sady SDK rozhraní .NET Framework pro vygenerování a podepsání manifestu nasazení.  
  
 Nevýhodou této metody je, že vyžaduje zákazníka k instalaci nástrojů pro .NET Framework SDK a mít vývojář nebo správce systému, který je kvalifikován na jejich používání. Zákazníci, kteří mohou požadovat řešení, které vyžaduje žádné nebo téměř žádné technické úsilí na jejich část.  
  
## <a name="see-also"></a>Viz také  
 [Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podpisu](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Návod: Ruční nasazení aplikace ClickOnce, jež nevyžaduje opětovné podepsání a které zachovává údaje o poskytovateli](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)



