---
title: DA0007 – Vyhněte se použití výjimek pro tok řízení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 6dd7261b1cb3a39d792cd3129b18a4a271191be0
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328216"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Vyhnutí se použití výjimek pro tok řízení

|||
|-|-|
|ID pravidla|DA0007|
|Kategorie|Využití .NET Framework|
|Metody profilace|Vše|
|Zpráva|Dojde k trvalému vyjímka vysokého počtu výjimek. Zvažte snížení použití výjimek v logice programu.|
|Typ zprávy|Upozornění|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit alespoň 25 vzorků.

## <a name="cause"></a>Příčina
 V datech profilování byla volána vysoká míra .NET Framework obslužných rutin výjimek. Zvažte použití jiné logiky toku řízení k omezení počtu výjimek, které jsou vyvolány.

## <a name="rule-description"></a>Popis pravidla
 Zatímco použití obslužných rutin výjimek k zachycení chyb a dalších událostí, které přerušují provádění programu je dobrým postupem, použití obslužné rutiny výjimky v rámci regulární logiky spuštění programu může být nákladné a mělo by se jim vyhnout. Ve většině případů by měly být výjimky používány pouze za okolnosti, ke kterým dochází zřídka a nejsou očekávány. Výjimky by se neměly používat k vrácení hodnot jako součásti typického toku programu. V mnoha případech se můžete vyhnout vyvolávání výjimek pomocí ověřování hodnot a použití podmíněné logiky k zastavení provádění příkazů, které způsobují problém.

 Další informace naleznete v části [Správa výjimek](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) **kapitoly 5 – zlepšení výkonu spravovaného kódu** v tématu **zlepšení výkonu a škálovatelnosti aplikace .NET** v knihovně **Microsoft Patterns and Practices** Library na webu MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvojitým kliknutím na zprávu v okně Seznam chyb přejdete do zobrazení značky. Vyhledá sloupec, který obsahuje měření **výjimky .NET CLR ( @ProcessInstance ) \\ Počet vyvolaných za sekundu v Excelu** . Určete, zda existují konkrétní fáze provádění programu, kde je zpracování výjimek více častější než jiné. Pomocí profilu vzorkování se pokuste identifikovat příkazy throw a bloky try/catch, které generují časté výjimky. V případě potřeby přidejte logiku k blokům catch, které vám pomohou pochopit, které výjimky jsou často zpracovávány. Pokud je to možné, nahraďte často spouštěné příkazy throw nebo catch bloky pomocí jednoduché logiky řízení toku nebo ověřovacího kódu.

 Například pokud jste chtěli zjistit, že vaše aplikace zpracovává časté výjimky DivideByZeroException, přidání logiky do programu pro kontrolu odregistrů s nulovými hodnotami zvyšuje výkon aplikace.
