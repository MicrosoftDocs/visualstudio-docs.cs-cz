---
title: Přehled výkonnostní relace | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778463"
---
# <a name="performance-session-overview"></a>Přehled výkonnostní relace
Tento přehled vysvětluje základy profilace. Vývojáři, kteří jsou novinkou v práci s výkonem, uvidí, jak může Nástroje pro profilaci pomáhat s tím, že se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rychle zvýší produktivita a zvýší výkon kódu. Vývojáři, kteří mají profilaci, mohou získat přehled o konkrétních Nástroje pro profilacich funkcích a procesech.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Nástroje pro profilaci vám pomůžou identifikovat problémy s výkonem ve zdrojovém kódu a porovnávat výkon možných řešení. Průvodci Nástroje pro profilaci a výchozí nastavení vám můžou poskytnout okamžitý přehled o mnoha problémech s výkonem. Funkce a možnosti Nástroje pro profilaci poskytují přesnou kontrolu nad procesem profilace. Tento ovládací prvek zahrnuje přesné cílení částí kódu, kolekci informací o časování na úrovni bloku a zahrnutí dalších dat o výkonu procesoru a systému do vašich dat.

 Následující kroky tvoří základní proces použití Nástroje pro profilaci:

1. Nakonfigurujte relaci výkonu zadáním metody kolekce a dat, která chcete shromažďovat.

2. Shromažďování dat profilování spuštěním aplikace v relaci výkonu.

3. Analyzujte data a Identifikujte problém s výkonem.

4. Úprava kódu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) pro zvýšení výkonu aplikace v kódu

5. Shromážděte data profilace ve změněném kódu a porovnejte data profilace původních a změněných dat.

6. Vygenerujte sestavu, která dokumentuje zvýšení výkonu.

   Pro práci s informacemi, které jsou poskytovány profilování, byste měli mít k dispozici informace o symbolech pro binární soubory, které chcete profilovat, a pro binární soubory operačního systému Windows.

## <a name="configure-the-performance-session"></a>Konfigurace výkonnostní relace
 Chcete-li konfigurovat relaci profilování, vyberte metodu profilace, kterou chcete použít, a data, která chcete shromažďovat. **Průvodce výkonem** nástroje pro profilaci vás provede základní konfigurací a pomocí stránek vlastností relace výkonu můžete přidat další možnosti:

- Metody profilování zahrnují vzorkování, trasování a přidělení paměti.

- Mezi hodnoty dat patří čas, čítače výkonu procesoru a operační systém a události aplikace, jako například chyby stránky a přechody jádra.

  Můžete nakonfigurovat relaci výkonu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu jako součást řešení projektu nebo vytvořit profil libovolných binárních souborů prostřednictvím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE). Vlastnosti relace můžete zadat na stránkách vlastností relace výkonu nebo můžete použít Průvodce profilací.

## <a name="collect-profiling-data"></a>Shromažďování dat profilace
 Můžete spustit shromažďování dat profilování z **prohlížeč výkonu**. Můžete pozastavit a obnovit profilování pro omezení množství shromažďovaných dat. Můžete se také připojit k procesu, který je již spuštěn.

 Jakmile se aplikace spustí, okno **ovládací prvek shromažďování dat** se zobrazí v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí. V okně **ovládací prvek shromažďování dat** můžete profilovat určité části aplikace tím, že se pozastavíte a znovu pokračujete v procesu shromažďování. Můžete také použít okno **ovládací prvek shromažďování dat** k vložení značek do shromažďovaných dat. Značky jsou uživatelsky definované datové body, které se zobrazují v zobrazeních profilu a které lze použít k filtrování dat profilování.

 Když se cílová aplikace ukončí, Nástroje pro profilaci vygeneruje soubor dat profilování (*. vsp) a zobrazí souhrnné zobrazení sestavy v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE).

## <a name="analyze-the-data-and-identify-performance-issues"></a>Analyzujte data a Identifikujte problémy s výkonem.
 Po ukončení běhu profilování se analyzují data a zobrazí se souhrn v oknech zobrazit **sestavu výkonu** nástroje pro profilaci. Data profilování jsou shromažďována pro zásobník volání a jednotlivé funkce cílové aplikace. Zobrazení sestav zobrazují analýzu výkonu pro rozsahy dat procesů, vláken, modulů, funkcí a řádků zdrojového kódu aplikace. K profilování hodnot dat pro funkci patří následující:

- Celkový čas strávený ve funkci a v podřízených funkcích, které byly volány funkcí (včetně hodnot).

- Čas strávený prováděním pouze kódu ve funkci (exkluzivní hodnoty).

  Více než dvanáct různých zobrazení vám umožní analyzovat data profilace nejúčinnějším způsobem. Zobrazení úprav umožňují filtrovat a řadit data a vyhledat funkce, které mohou způsobovat problémy s výkonem. Filtrování horké cesty poskytuje okamžité zvýraznění nejaktivnějších cest v zobrazení stromu volání a modulu.

## <a name="modify-the-application-code"></a>Úprava kódu aplikace
 Po izolování jednoho nebo více souvisejících problémů s výkonem můžete kód upravit pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí a potom shromáždit data profilování pro vaše změny.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Shromažďování dat profilování znovu a porovnání dat mezi spuštěnými profilací
 V zobrazení sestavy porovnání Nástroje pro profilaci se zobrazuje rozdíl mezi dvěma vybranými datovými soubory profilování v modulu, funkci nebo řádku. Můžete určit hodnoty dat profilování, které chcete porovnat, a můžete přepínat mezi zobrazením porovnání a zobrazeními jednotlivých souborů.

## <a name="generate-a-report-of-the-results"></a>Generování sestavy výsledků
 Do e-mailů a tabulek můžete vkládat řádky všech zobrazení sestav výkonu a můžete generovat sestavy obsahující data pro jedno nebo více zobrazení.

## <a name="see-also"></a>Viz také
- [Přehledy](../profiling/overviews-performance-tools.md)
- [Návod: Identifikace problémů s výkonem](beginners-guide-to-cpu-sampling.md)
