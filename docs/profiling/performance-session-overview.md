---
title: Přehled relace výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e7b23a7cbefeace19a3deaa5c1bfc05580081d39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778463"
---
# <a name="performance-session-overview"></a>Přehled výkonnostní relace
Tento přehled vysvětluje základy profilování. Vývojáři, kteří jsou na výkon [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] práce uvidí, jak profilování nástroje jim může pomoci rychle zvýšit produktivitu a zvýšit výkon jejich kódu. Vývojáři, kteří mají zkušenosti s profilováním, mohou získat přehled o konkrétních funkcích a procesech nástrojů profilování.

 Nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilování vám pomohou identifikovat problémy s výkonem ve zdrojovém kódu a porovnat výkon možných řešení. Průvodce nástroji profilování a výchozí nastavení vám mohou poskytnout okamžitý přehled o mnoha problémech s výkonem. Funkce a možnosti nástrojů profilování poskytují přesnou kontrolu nad procesem profilování. Tento ovládací prvek zahrnuje přesné cílení na části kódu, shromažďování informací o časování na úrovni bloku a zahrnutí dalších dat o výkonu procesoru a systému do dat.

 Následující kroky tvoří základní proces použití nástrojů profilování:

1. Nakonfigurujte relaci výkonu zadáním metody kolekce a dat, která chcete shromažďovat.

2. Shromažďovat data profilování spuštěním aplikace v relaci výkonu.

3. Analyzujte data k identifikaci problému s výkonem.

4. Úprava kódu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v integrovaném vývojovém prostředí (IDE) zvyšuje výkon aplikace kódu

5. Shromažďujte data profilování změněného kódu a porovnejte data profilování původních a změněných dat.

6. Vygenerujte sestavu, která dokumentuje zvýšení výkonu.

   Chcete-li pracovat s informacemi poskytovanými profilováním, měli byste mít k dispozici informace o symbolech pro binární soubory, které chcete profilovat, a pro binární soubory operačního systému Windows.

## <a name="configure-the-performance-session"></a>Konfigurace relace výkonu
 Chcete-li nakonfigurovat relaci profilování, vyberte metodu profilování, kterou chcete použít, a data, která chcete shromažďovat. **Průvodce výkonem** nástrojů profilování vás může provést základní konfigurací a pomocí stránek vlastností Relace výkonu můžete přidat další možnosti:

- Metody profilování zahrnují vzorkování, trasování a přidělení paměti.

- Mezi datové hodnoty patří čítače výkonu času, procesoru a operačního systému a události aplikace, jako jsou chyby stránek a přechody jádra.

  Můžete nakonfigurovat relaci výkonu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v projektu jako součást řešení projektu nebo profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] libovolné binární soubory prostřednictvím rozhraní IDE. Můžete zadat vlastnosti relace na stránkách vlastností Relace výkonu nebo můžete použít Průvodce profilováním.

## <a name="collect-profiling-data"></a>Shromažďování dat profilování
 Spuštění shromažďování dat profilování z **Průzkumníka výkonu**. Profilování můžete pozastavit a obnovit a omezit tak množství shromažďovacích dat. Můžete také připojit k procesu, který je již spuštěn.

 Jakmile se aplikace spustí, zobrazí se v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ide okno **řízení kolekce dat.** Z okna **Řízení kolekce dat** můžete profilovat určité části aplikace pozastavením a obnovením procesu shromažďování dat. Okno **Řízení kolekce dat** můžete také použít k vložení značek do shromažďovaných dat. Značky jsou uživatelem definované datové body, které jsou zobrazeny v zobrazeních profilu a které lze použít k filtrování dat profilování.

 Když se cílová aplikace vypne, nástroje profilování vygeneruje datový soubor profilování (*.vsp) a zobrazí zobrazení souhrnné sestavy v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ide.

## <a name="analyze-the-data-and-identify-performance-issues"></a>Analýza dat a identifikace problémů s výkonem
 Když ukončíte spuštění profilování, data se analyzují a v oknech sestavy **výkonu** nástroje profilování se zobrazí souhrn. Profilování dat jsou shromažďovány pro zásobník volání a jednotlivé funkce cílové aplikace. Zobrazení sestavy zobrazují analýzu výkonu pro oblasti dat procesů, vláken, modulů, funkcí a řádků zdrojového kódu aplikace. Profilování datových hodnot pro funkci zahrnuje následující:

- Celkový čas, který byl strávený ve funkci a v podřízených funkcích, které byly volány funkcí (včetně hodnot).

- Čas, který byl stráven prováděním pouze kódu ve funkci (výhradní hodnoty).

  Více než dvanáct různých zobrazení umožňuje analyzovat data profilování nejefektivnějším způsobem. Zobrazení vlastního nastavení umožňuje filtrovat a seřadit data a vyhledat funkce, které mohou způsobovat problémy s výkonem. Filtrování horké cesty poskytuje okamžité zvýraznění nejaktivnějších cest v zobrazení stromu volání a modulu.

## <a name="modify-the-application-code"></a>Úprava kódu aplikace
 Po izolované jeden nebo více relevantních problémů s výkonem můžete upravit kód pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ide a potom shromažďovat data profilování pro vaše změny.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Znovu shromažďujte data profilování a porovnejte data mezi spuštěními profilování
 Zobrazení sestavy porovnání nástrojů profilování zobrazuje rozdíl v výkonu modulu, funkce nebo linky mezi dvěma vybranými datovými soubory profilování. Můžete určit hodnoty dat profilování, které chcete porovnat, a můžete přepínat mezi zobrazením porovnání a zobrazeními jednotlivých souborů.

## <a name="generate-a-report-of-the-results"></a>Generovat sestavu výsledků
 Řádky libovolného zobrazení sestavy výkonu můžete vložit do e-mailů a tabulek a můžete generovat sestavy obsahující data pro jedno nebo více zobrazení.

## <a name="see-also"></a>Viz také
- [Přehledy](../profiling/overviews-performance-tools.md)
- [Návod: Identifikace problémů s výkonem](beginners-guide-to-cpu-sampling.md)
