---
title: Vytváření aplikací ClickOnce pro ostatní k nasazení | Microsoft Docs
description: Přečtěte si o aplikacích ClickOnce hostovaných zákazníky vyvinutých v .NET Framework 3,5 a předchozích verzích .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9554cad786669ae4aa3b9aa84ecd6b996ee196f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888469"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Vytváření aplikací ClickOnce k nasazení dalšími osobami
Ne všichni vývojáři, kteří vytvářejí nasazení ClickOnce, naplánují nasazení samotných aplikací. Mnohé z nich pouze zabalí své aplikace pomocí ClickOnce a pak je předají do zákazníka, jako je například velká společnost. Zákazník se bude zodpovědná za hostování aplikace v příslušné síti. Toto téma popisuje některé problémy, které jsou součástí těchto nasazení ve verzích .NET Framework před verzí 3,5. Pak popisuje nové řešení, které je k dispozici, pomocí nové funkce použít manifest pro vztah důvěryhodnosti v .NET Framework 3,5. Nakonec se dokončí s doporučenými strategiemi pro vytváření nasazení ClickOnce pro zákazníky, kteří stále používají starší verze .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problémy související se vytvářením nasazení pro zákazníky
 K několika problémům dochází, když plánujete dodat nasazení zákazníkovi. První problém se týká podepisování kódu. Aby bylo možné je nasadit v síti, manifest nasazení a manifest aplikace nasazení ClickOnce musí být podepsány pomocí digitálního certifikátu. Tím se vyvolá otázka, jestli při podepisování manifestů použít certifikát vývojáře nebo certifikát zákazníka.

 Otázka, kterou certifikát použít, je kritická, protože identita aplikace ClickOnce je založena na digitálním podpisu manifestu nasazení. Pokud vývojář podepíše manifest nasazení, může to způsobit konflikty, pokud je zákazník velká společnost a více než jedna divize společnosti nasadí přizpůsobenou verzi aplikace.

 Řekněme například, že Adventure Works má finanční oddělení a oddělení lidských zdrojů. Obě oddělení licencují aplikaci ClickOnce od společnosti Microsoft Corporation, která generuje sestavy z dat uložených v databázi SQL. Společnost Microsoft poskytuje každému oddělení verzi aplikace, která je přizpůsobená pro svá data. Pokud jsou aplikace podepsané stejným certifikátem Authenticode, může se uživatel, který se pokusí použít obě aplikace, narazit na chybu, protože ClickOnce by poznamenala druhou aplikaci shodnou s prvním. V takovém případě by zákazník mohl vyskytnout nepředvídatelné a nežádoucí vedlejší účinky, které zahrnují ztrátu všech dat uložených místně aplikací.

 Dalším problémem, který souvisí s podepisováním kódu `deploymentProvider` , je prvek v manifestu nasazení, který dává technologii ClickOnce, kde se hledají aktualizace aplikace. Tento prvek musí být přidán do manifestu nasazení před jeho podepsáním. Pokud je tento prvek přidán později, manifest nasazení musí být podepsán znovu.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Vyžadovat od zákazníka podpis manifestu nasazení
 Jedním z řešení tohoto problému při nejedinečných nasazeních je, že vývojář manifest aplikace podepisuje a zákazník podepíše manifest nasazení. I když tento přístup funguje, zavádí jiné problémy. Vzhledem k tomu, že certifikát Authenticode musí zůstat chráněným prostředkem, zákazník nemůže pouze udělit vývojáři certifikát k podepsání nasazení. I když zákazník může podepsat samotný manifest nasazení pomocí nástrojů volně dostupných v sadě .NET Framework SDK, může to vyžadovat více technických znalostí, než je zákazník ochotný nebo schopný poskytnout. V takových případech vývojář většinou vytvoří aplikaci, web nebo jiný mechanismus, pomocí kterého může zákazník odeslat svou verzi aplikace k podepisování.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Dopad podepisování zákazníka na zabezpečení aplikace ClickOnce
 I v případě, že vývojář a zákazník souhlasí, že by měl podepsat manifest aplikace tím, že má za to, že má za to, že se bude vztahovat i na nasazení důvěryhodné aplikace, vyvolá další problémy, které obklopují identitu aplikace. (Další informace o této funkci najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).) Řekněme, že Adventure Works chce nakonfigurovat své klientské počítače tak, aby každá aplikace, kterou jim poskytuje Microsoft Corporation, běžela s úplným vztahem důvěryhodnosti. Pokud Adventure Works podepíše manifest nasazení, pak ClickOnce použije bezpečnostní podpis společnosti Adventure Worker k určení úrovně důvěryhodnosti aplikace.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Vytváření zákaznických nasazení pomocí manifestu aplikace pro vztah důvěryhodnosti
 ClickOnce v .NET Framework 3,5 obsahuje novou funkci, která vývojářům a zákazníkům poskytuje nové řešení do scénáře, jak by měly být manifesty podepsány. Manifest aplikace ClickOnce podporuje nový element s názvem `<useManifestForTrust>` , který vývojářům umožňuje označit, že digitální podpis manifestu aplikace je vhodné použít k rozhodování o důvěryhodnosti. Vývojář používá nástroje pro vytváření balíčků ClickOnce, jako je *Mage.exe*, *MageUI.exe* a Visual Studio – pro zahrnutí tohoto prvku do manifestu aplikace a také pro vložení názvu vydavatele a názvu aplikace do manifestu.

 Při použití nástroje `<useManifestForTrust>` nemusí být manifest nasazení podepsán certifikátem Authenticode vydaným certifikační autoritou. Místo toho je možné ho podepsat pomocí certifikátu podepsaného svým držitelem. Certifikát podepsaný svým držitelem je vygenerovaný zákazníkem nebo vývojářem pomocí standardních nástrojů .NET Framework SDK a pak se aplikuje na manifest nasazení pomocí standardních nástrojů pro nasazení ClickOnce. Další informace najdete v tématu [Makecert](/windows/desktop/SecCrypto/makecert).

 Použití certifikátu podepsaného svým držitelem pro manifest nasazení přináší několik výhod. Vyloučením nutnosti, aby zákazník získal nebo vytvořil vlastní certifikát Authenticode, `<useManifestForTrust>` zjednodušuje nasazení pro zákazníka, zatímco vývojářům umožňuje zachovat svoji vlastní identitu na základě vaší aplikace. Výsledkem je sada podepsaných nasazení, která jsou bezpečnější a mají jedinečné identity aplikací. Tím se eliminuje možný konflikt, ke kterému může dojít při nasazování stejné aplikace na více zákazníků.

 Podrobné informace o tom, jak vytvořit nasazení ClickOnce s `<useManifestForTrust>` povolenou, najdete v tématu [Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje Opětovné podepsání a které zachovává informace o značkách](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Jak funguje manifest aplikace pro vztah důvěryhodnosti v době běhu
 Chcete-li získat lepší informace o použití manifestu aplikace pro vztah důvěryhodnosti v době běhu, vezměte v úvahu následující příklad. Aplikace ClickOnce, která cílí na .NET Framework 3,5, je vytvořena společností Microsoft. Manifest aplikace používá `<useManifestForTrust>` prvek a je podepsán společností Microsoft. Adventure Works podepisuje manifest nasazení pomocí certifikátu podepsaného svým držitelem. Klienti Adventure Works jsou nakonfigurováni tak, aby důvěřovali všem aplikacím podepsaným společností Microsoft.

 Když uživatel klikne na odkaz na manifest nasazení, ClickOnce nainstaluje aplikaci do počítače uživatele. Informace o certifikátu a nasazení identifikují aplikaci jedinečnou pro technologii ClickOnce v klientském počítači. Pokud se uživatel pokusí nainstalovat stejnou aplikaci znovu z jiného umístění, ClickOnce může tuto identitu použít k určení toho, že aplikace již na klientovi existuje.

 Dále ClickOnce prověřuje certifikát Authenticode, který se používá k podepsání manifestu aplikace, který určuje úroveň důvěryhodnosti, kterou bude ClickOnce udělovat. Vzhledem k tomu, že společnost Adventure Works nakonfigurovala své klienty tak, aby důvěřovaly jakékoli aplikaci podepsané společností Microsoft, je této aplikaci ClickOnce udělen úplný vztah důvěryhodnosti. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Vytvořit zákaznická nasazení pro starší verze
 Co když vývojář nasazuje aplikace ClickOnce pro zákazníky, kteří používají starší verze .NET Framework? Následující části shrnují několik doporučených řešení společně s výhodami a nevýhodami každého z nich.

### <a name="sign-deployments-on-behalf-of-customer"></a>Podepsat nasazení jménem zákazníka
 Jednou z možných strategií nasazení je, aby vývojář vytvořil mechanismus pro podepisování nasazení jménem svých zákazníků pomocí vlastního privátního klíče zákazníka. To brání vývojáři v nutnosti spravovat soukromé klíče nebo více balíčků pro nasazení. Vývojář jenom nabízí stejné nasazení pro každého zákazníka. Je až zákazník, aby ho přizpůsobil pro své prostředí pomocí podpisové služby.

 Jednou z nevýhod této metody je čas a výdaje, které jsou potřeba k její implementaci. I když taková služba může být sestavena pomocí nástrojů, které jsou k dispozici v sadě .NET Framework SDK, přidá k životnímu cyklu produktu další dobu vývoje.

 Jak bylo popsáno dříve v tomto tématu, Další nevýhodou je, že každá verze aplikace zákazníka bude mít stejnou identitu aplikace, což by mohlo vést ke konfliktům. Pokud se to týká, může vývojář změnit pole název, které se používá při generování manifestu nasazení, aby každou aplikaci měl jedinečný název. Tím se vytvoří samostatná identita pro každou verzi aplikace a odstraní se případné konflikty identity. Toto pole odpovídá `-Name` argumentu pro Mage.exe a do pole **název** na kartě **název** v MageUI.exe.

 Řekněme například, že vývojář vytvořil aplikaci s názvem Application1. Namísto vytvoření jediného nasazení s polem s názvem nastaveným na Application1 může vývojář vytvořit několik nasazení s variantou specifickou pro konkrétního zákazníka, jako je například Application1-Customer, Application1-CustomerB atd.

### <a name="deploy-using-a-setup-package"></a>Nasazení pomocí instalačního balíčku
 Druhou možnou strategii nasazení je vygenerování projektu instalace společnosti Microsoft, který provede počáteční nasazení aplikace ClickOnce. To může být k dispozici v jednom z několika různých formátů: jako instalační program MSI jako spustitelný soubor instalace (. EXE) nebo jako soubor CAB spolu se skriptem Batch.

 Pomocí této techniky vývojář poskytne zákazníkům nasazení, které zahrnuje soubory aplikace, manifest aplikace a manifest nasazení, který slouží jako šablona. Zákazník by měl spustit instalační program, který jim vyzve k zadání adresy URL pro nasazení (Server nebo umístění sdílené složky, ze kterého uživatelé nainstalují aplikaci ClickOnce) a také digitální certifikát. Instalační aplikace se také může zobrazit výzva k zadání dalších možností konfigurace ClickOnce, jako je například interval kontroly aktualizace. Po shromáždění těchto informací Instalační program vygeneruje skutečný manifest nasazení, podepíše ho a publikuje aplikaci ClickOnce na určené místo na serveru.

 Existují tři způsoby, jak může zákazník podepsat manifest nasazení v této situaci:

1. Zákazník může použít platný certifikát vydaný certifikační autoritou (CA).

2. Jako variantu tohoto přístupu se může zákazník rozhodnout podepsat svůj manifest nasazení pomocí certifikátu podepsaného svým držitelem. Nevýhodou tohoto problému je, že aplikace zobrazí slova "Neznámý vydavatel", když se uživatel zeptá, jestli ho má nainstalovat. Výhodou je však, že brání menším zákazníkům, aby strávili časem a penězům potřebným pro certifikát vydaný certifikační autoritou.

3. Nakonec může vývojář do instalačního balíčku zahrnout vlastní certifikát podepsaný svým držitelem. To představuje potenciální problémy s identitou aplikace, které jsou popsány dříve v tomto tématu.

   Nevýhodou metody projektu nasazení instalace je čas a výdaj potřebný k vytvoření vlastní aplikace nasazení.

### <a name="have-customer-generate-deployment-manifest"></a>Nechat zákazníka generovat manifest nasazení
 Třetí možnou strategii nasazení je předání pouze souborů aplikace a manifestu aplikace zákazníkovi. V tomto scénáři je zákazník zodpovědný za použití sady .NET Framework SDK k vygenerování a podepsání manifestu nasazení.

 Nevýhodou této metody je, že vyžaduje, aby zákazník nainstaloval nástroje .NET Framework SDK a aby měl vývojáře nebo správce systému, který je kvalifikovaný při jejich používání. Někteří zákazníci si můžou vyžádat řešení, které vyžaduje malé nebo žádné technické úsilí na jejich straně.

## <a name="see-also"></a>Viz také
- [Nasazení aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje Opětovné podepsání a které zachovává informace o značkách](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)