---
title: Profilace výkonu aplikací služby SharePoint | Microsoft Docs
description: Profilujte výkon aplikací SharePoint, pokud jsou spuštěné pomalu nebo neefektivně. Pomocí funkcí profilace sady Visual Studio Najděte problematický kód.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d59f5b472f791f9774515cdb3e92cc4cf7f9f55b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860734"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilace výkonu aplikací služby SharePoint

Pokud vaše aplikace SharePoint pracuje pomalu nebo neefektivně, můžete použít funkce profilování v aplikaci Visual Studio k identifikaci problematického kódu a dalších prvků. Pomocí funkce testování zatížení můžete určit, jak má aplikace služby SharePoint provádět zátěž, například když mnoho uživatelů přistupuje k aplikaci současně. Spuštěním testů výkonnosti webu můžete měřit, jak aplikace provádí na webu. Pomocí programových testů uživatelského rozhraní můžete ověřit, zda celá aplikace služby SharePoint, včetně jejího uživatelského rozhraní, funguje správně. Použijete-li tyto testy společně, mohou vám pomohou identifikovat problémy s výkonem před nasazením aplikace.

## <a name="profile-tools-overview"></a>Přehled nástrojů pro profilaci

Profilace odkazuje na proces pozorování a zaznamenávání chování vaší aplikace při jejich spuštění. Po profilaci aplikace můžete odhalit problémy, jako jsou například kritická místa, neefektivní kód a problémy s přidělením paměti, což způsobuje, že aplikace běží pomalu nebo využívají příliš mnoho paměti. Profilování můžete například použít k identifikaci hotspotů ve vašem kódu, což jsou segmenty kódu, které jsou často volány a mohou zpomalit celkový výkon aplikace. Po identifikaci aktivních bodů je můžete často optimalizovat nebo eliminovat.

Můžete použít několik nástrojů pro profilaci v integrovaném vývojovém prostředí (IDE) k identifikaci a vyhledání těchto typů problémů s výkonem. Tyto nástroje fungují stejným způsobem pro projekty služby SharePoint, stejně jako pro jiné typy projektů aplikace Visual Studio. Průvodce výkonem Nástroje pro profilaci vás provede vytvořením relace výkonu, která používá testy, které zadáte. Výkonnostní relace je sada konfiguračních dat, která se používá ke shromažďování informací o výkonu z aplikace spolu s výsledky jednoho nebo více spuštění profilování. Relace výkonu jsou uloženy ve složce projektu a lze je zobrazit v **prohlížeč výkonu**. Další informace najdete v tématu [principy metod shromažďování výkonu](../profiling/understanding-performance-collection-methods.md).

Po vytvoření a spuštění analýzy profilů v aplikaci vám Sestava poskytne podrobnosti o jejím výkonu. Tato sestava může obsahovat položky, jako je například graf využití procesoru v čase, zásobník volání hierarchické funkce nebo strom volání. Přesný obsah sestavy se může lišit v závislosti na typu testu, který spustíte, jako je například vzorkování nebo instrumentace. Další informace najdete v tématu [přehled nástroje pro profilaci sestavy](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Proces relace výkonu

Chcete-li profilovat aplikaci, začněte pomocí Průvodce Nástroje pro profilaci výkon a vytvořte relaci výkonu. Na panelu nabídek vyberte možnost **analyzovat**, **Spustit Průvodce výkonem**. Při dokončování Průvodce zadáte požadované informace pro vaši relaci výkonu, například požadovanou metodu profilu, a aplikaci, kterou chcete profilovat. Další informace najdete v tématu [Postup: profilování webu nebo webové aplikace pomocí Průvodce výkonem](../profiling/how-to-collect-performance-data-for-a-web-site.md). Alternativně můžete použít možnosti příkazového řádku k nastavení a spuštění relace výkonu. Další informace najdete v tématu [použití nástroje pro profilaci z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md). Pokud chcete nakonfigurovat všechny aspekty relace výkonu ručně, přečtěte si téma [Postup: Ruční vytvoření relací výkonu pomocí nástroje pro profilaci](../profiling/how-to-manually-create-performance-sessions.md). Můžete také vytvořit relaci výkonu z testu jednotky tak, že v okně **výsledky testů** otevřete místní nabídku pro test jednotky a pak zvolíte možnost **vytvořit relaci výkonu**.

Po nastavení relace výkonu se konfigurace relace uloží, server se nakonfiguruje tak, aby poskytoval data profilace a aplikace se spustí. Při použití aplikace se data o výkonu zapisují do souboru protokolu. Relace výkonu jsou uvedené v **prohlížeč výkonu** ve složce **cíle** . Po dokončení relace výkonu se její sestava zobrazí ve složce **sestavy** v **prohlížeč výkonu**. Chcete-li zobrazit sestavu, otevřete ji v **prohlížeč výkonu**. Chcete-li zobrazit nebo nakonfigurovat vlastnosti relace výkonu, otevřete její místní nabídku v **prohlížeč výkonu** a zvolte možnost **vlastnosti**. Další informace o konkrétních vlastnostech relace výkonu najdete v tématu [Konfigurace relací výkonu pro nástroje pro profilaci](../profiling/configuring-performance-sessions.md). Informace o tom, jak interpretovat výsledky relace výkonu, najdete v tématu [analýza nástroje pro profilacich dat](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Zátěžový test

Můžete analyzovat výkon zátěže vašich aplikací vytvořením zátěžových testů a testů výkonnosti webu v aplikaci Visual Studio. Při vytváření zátěžového testu v aplikaci Visual Studio určíte kombinaci faktorů označovaných jako scénář a otestujete tak aplikaci. Tyto faktory zahrnují vzor zatížení, model kombinace testů, kombinaci testů, kombinaci sítí a kombinaci webového prohlížeče. Scénáře zátěžového testu mohou zahrnovat testy jednotek i testy výkonnosti webu.

Obrázek 1: Příklad výsledků zátěžového testování

![Spuštění zobrazení grafů zátěžového testu](../sharepoint/media/load-webgraphs.png "Spuštění zobrazení grafů zátěžového testu")

Testy webového výkonu simulují, jak může koncový uživatel pracovat s aplikací služby SharePoint. Testy výkonnosti webu můžete vytvořit zaznamenáváním požadavků HTTP v relaci prohlížeče nebo pomocí **zapisovače testu výkonnosti webu**. Webové požadavky se zobrazí v **Editor testu výkonnosti webu** po dokončení relace prohlížeče. Pak můžete ladit výsledky v **prohlížeči výsledky testů webového výkonu**. Testy výkonnosti webu můžete také vytvořit ručně pomocí **Editor testu výkonnosti webu**.

## <a name="test-user-interfaces"></a>Testovací uživatelská rozhraní

Programové testy uživatelského rozhraní automaticky zařídí svou aplikaci SharePoint prostřednictvím uživatelského rozhraní (UI). Tyto testy pokrývají ovládací prvky uživatelského rozhraní, jako jsou tlačítka a nabídky, k ověření, že fungují správně. Tento druh testování je zvláště užitečný v případě, že se ověřování nebo jiná logika provádí v uživatelském rozhraní, například na webové stránce. Můžete také použít programové testy uživatelského rozhraní k automatizaci ručních testů. Programové testy uživatelského rozhraní pro aplikace SharePoint vytvoříte stejným způsobem jako při vytváření testů pro jiné typy aplikací. Další informace naleznete v tématu [testování aplikací SharePoint 2010 pomocí programových testů uživatelského rozhraní](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Návod: profilování aplikace SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Ukazuje, jak provést analýzu profilu vzorkování v aplikaci SharePoint.|
|[Test výkonu aplikace před vydáním](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|Popisuje, jak vytvořit zátěžové testy, které vám pomůžou zátěžové testování aplikací SharePoint.|
|[Testy jednotek kódu](../test/unit-test-your-code.md)|Popisuje, jak najít logické chyby ve vašem kódu pomocí testů jednotek.|
|[Testování aplikací pro SharePoint 2010 pomocí programových testů uživatelského rozhraní](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|Popisuje postup testování uživatelského rozhraní aplikací služby SharePoint.|

## <a name="see-also"></a>Viz také

- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Zlepšení kvality kódu](../test/improve-code-quality.md)