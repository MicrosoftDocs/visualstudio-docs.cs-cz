---
title: Přehled výkonnostní relace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b71f507e783552e066d41fe74e63fbc6b6146338
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750048"
---
# <a name="performance-session-overview"></a>Přehled výkonnostní relace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento přehled popisuje základní informace o vytváření profilů. Vývojáři, kteří teprve začínáte pracovní výkonu se zobrazí jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jim být tak produktivní rychle a zvýšit výkon jejich kód mohou pomoci nástroje pro profilaci. Vývojáři, kteří mají zkušenosti s profilace můžete získat přehled o konkrétních nástrojů pro profilaci sady funkcí a procesy.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profilace nástroje vám pomůžou identifikovat problémy s výkonem ve zdrojovém kódu a porovnat výkon jednotlivých řešení. Profilace průvodcích nástroje a nastavení výchozí vám může poskytnout okamžitý přehled o mnoho problémů s výkonem. Funkce a možnosti nástrojů pro profilaci poskytují přesnou kontrolu nad procesu profilace. Tento ovládací prvek obsahuje přesné cílení na části kódu, shromažďování informací o časování blokových a zahrnutí další data o výkonu procesoru a systému ve vašich datech.  
  
 Následující kroky tvoří základní proces pomocí nástrojů pro profilaci sady:  
  
1. Výkonnostní relaci nakonfigurujte tak, že určíte metodu shromažďování a data, která chcete shromažďovat.  
  
2. Spuštěním aplikace v relaci výkonu shromažďování dat profilace.  
  
3. Analýza dat identifikovat problémy s výkonem.  
  
4. Upravit kód v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) pro zvyšuje výkon aplikace kódu  
  
5. Shromažďování dat profilace na změny kódu a porovnat data profilování původní a změněná data.  
  
6. Vygenerujte sestavu, která dokumentuje zvýšení výkonu.  
  
   Pro práci s informacemi, které poskytuje profilace, měli byste mít informace o symbolech pro binární soubory, které chcete profil a binární soubory operačního systému Windows k dispozici.  
  
## <a name="configure-the-performance-session"></a>Konfigurace relace výkonu  
 Pro konfiguraci relace profilování, vyberte metodu profilace chcete použít a data, která chcete shromažďovat. Nástroje pro profilaci **Průvodce výkonem** může vás provede základní konfigurace a stránky vlastností relace výkonu můžete přidat další možnosti:  
  
- Profilování metody patří vzorkování, trasování a přidělení paměti.  
  
- Hodnoty data zahrnují čas, procesoru a čítače výkonu operačního systému a události aplikace, jako jsou chyby stránek a přechody jádra.  
  
  Můžete nakonfigurovat v relaci výkonu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu jako součást řešení projektu, nebo libovolný binární soubory prostřednictvím profilu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Na stránce vlastností relace výkonu možné určit vlastnosti relace nebo můžete použít Průvodce Profilováním.  
  
## <a name="collect-profiling-data"></a>Shromažďovat Data profilování  
 Spustit shromažďování dat z profilování **prohlížeč výkonu**. Můžete pozastavit a obnovit, profilace a omezit tak množství dat, která shromažďujete. Můžete také připojit k procesu, který je již spuštěn.  
  
 Co nejdříve po spuštění aplikace **ovládacího prvku sběru dat** okno se zobrazí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Z **ovládacího prvku sběru dat** můžete Profilovat konkrétní části vaší aplikace pomocí pozastavování a obnovování procesu shromažďování. Můžete také použít **ovládacího prvku sběru dat** okno vkládání značek do data, která se shromažďují. Značky jsou uživatelem definované datové body, které se zobrazují v zobrazení profilu a, který můžete použít k filtrování dat profilování.  
  
 Pokud je cílová aplikace ukončena, nástrojů pro profilaci generuje souboru dat profilování (*.vsp) a zobrazuje souhrnnou sestavu zobrazit v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí.  
  
## <a name="analyze-the-data-and-identify-performance-issues"></a>Data analyzovat a identifikovat problémy s výkonem  
 Po ukončení profilování, data se analyzují a zobrazí se souhrn v nástrojích pro profilaci **sestavu výkonu** zobrazení windows. Zásobník volání a jednotlivých funkcí cílové aplikace jsou shromažďována data profilování. Sestava, zobrazení analýzy výkonu pro rozsahy dat procesy, vlákna, moduly, funkce a řádky zdrojového kódu aplikace. Data profilování pro funkci následující hodnoty:  
  
- Celkový čas, který byl vynaložen ve funkci a funkce podřízený, které byly volány – funkce (včetně hodnoty).  
  
- Čas, který byl stráven spouštěním pouze kódu ve funkci (výhradní hodnoty).  
  
  Více než 12 různá zobrazení umožňují snadno analyzovat data profilace nejefektivnějším způsobem. Přizpůsobení zobrazení umožňují filtrovat a řadit data a vyhledávat funkce, které by mohly způsobovat problémy s výkonem. Filtrování horká cesta obsahuje okamžité zvýraznění Nejaktivnější cest v zobrazení stromu volání a modulu.  
  
## <a name="modify-the-application-code"></a>Upravit kód aplikace  
 Po jedné nebo více problémů s výkonem relevantní nenaleznete, kód lze upravovat pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí a potom shromažďovat data profilování pro vaše změny.  
  
## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Shromažďovat Data profilování znovu a porovnávejte Data mezi spuštění profilování  
 Zobrazení sestavy profilování porovnání nástrojů zobrazí rozdíl v modulu, funkce nebo řádku výkon mezi dvěma vybraných souborů dat profilování. Můžete zadat profilování datových hodnot, které chcete porovnat, a můžete přepínat mezi zobrazením porovnání a zobrazení jednotlivých souborů.  
  
## <a name="generate-a-report-of-the-results"></a>Generování sestavy s výsledky  
 Řádky žádné zobrazení sestav výkonu můžete vložit do e-mailů a tabulky a můžete vygenerovat hlášení, které obsahují data pro jedno nebo více zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Návod: Identifikace problémů s výkonem](../profiling/walkthrough-identifying-performance-problems.md)



