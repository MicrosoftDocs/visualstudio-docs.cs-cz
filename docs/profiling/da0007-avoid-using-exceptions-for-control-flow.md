---
title: 'DA0007: Nepoužívejte výjimky pro tok řízení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26819be7cd001e87a6f94ac97d29c8a5e67f3932
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777696"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Vyhněte se použití výjimek pro tok řízení

|||
|-|-|
|Id pravidla|DA0007 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metody profilování|Všechny|
|Zpráva|Konzistentně jsou vyvolány vysoké množství výjimek. Zvažte snížení použití výjimek v programové logice.|
|Typ zprávy|Upozornění|

 Při profilování pomocí vzorkování, .NET paměti nebo metody tvrzení prostředků, je nutné shromáždit alespoň 25 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 V datech profilování byla volána vysoká míra obslužných rutin výjimek rozhraní .NET Framework. Zvažte použití jiné logiky toku ovládacího prvku ke snížení počtu výjimek, které jsou vyvolány.

## <a name="rule-description"></a>Popis pravidla
 Zatímco použití obslužné rutiny výjimek zachytit chyby a jiné události, které narušují spuštění programu je osvědčeným postupem, použití obslužné rutiny výjimky jako součást logiky provádění pravidelného programu může být nákladné a je třeba se vyhnout. Ve většině případů by výjimky by měly být použity pouze pro okolnosti, které se vyskytují zřídka a nejsou očekávány. Výjimky by neměly být použity k vrácení hodnot jako součást typického toku programu. V mnoha případech se můžete vyhnout vyvolání výjimek ověřením hodnot a použitím podmíněné logiky k zastavení provádění příkazů, které způsobují problém.

 Další informace naleznete v části [Správa výjimek](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) **kapitoly 5 – Zlepšení výkonu spravovaného kódu** ve zlepšení výkonu aplikací **.NET a škálovatelnosti** **knihovny Microsoft Patterns and Practices** v knihovně MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do zobrazení Značky. Najít sloupec, který obsahuje **.NET CLR@ProcessInstancevýjimky( )\\# excelů vyvolána / sec** měření. Zjistěte, zda existují určité fáze provádění programu, kde zpracování výjimek je častější než ostatní. Pomocí profil vzorkování, zkuste identifikovat příkazy throw a try/catch bloky, které generují časté výjimky. V případě potřeby přidejte logiku catch bloky, které vám pomohou pochopit, které výjimky jsou zpracovávány nejčastěji. Pokud je to možné, nahradit často spuštěné příkazy throw nebo catch bloky s jednoduchou logikou řízení toku nebo ověřovací kód.

 Například pokud jste zjistili, že vaše aplikace byla zpracování časté DivideByZeroException výjimky, přidání logiky do programu ke kontrole jmenovatele s nulovými hodnotami zlepšuje výkon aplikace.
