---
title: 'DA0039: Velmi vysoká míra tvrzení lock | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f64f717bf87fb4636c7c2f4e6f11a08236d08ada
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779360"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Velmi vysoká míra tvrzení o zámku

|||
|-|-|
|Id pravidla|DA0039 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metody profilování|Vzorkování<br /><br /> Instrumentace<br /><br /> Paměť .NET|
|Zpráva|Dochází k velmi vysoké rychlosti konfliktů zámků .NET. Zkontrolujte důvod tohoto konfliktu zámku spuštěním profilu souběžnosti.|
|Typ pravidla|Upozornění|

 Při profilování pomocí vzorkování, .NET paměti nebo metody tvrzení prostředků, je nutné shromáždit alespoň 25 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která jsou shromažďována s daty profilování označuje, že během provádění aplikace došlo k příliš vysoké míře konfliktů zámků. Zvažte profilování znovu pomocí metody profilování souběžnosti k nalezení příčiny tvrzení.

## <a name="rule-description"></a>Popis pravidla
 Zámky se používají k ochraně kritických částí kódu, které musí být prováděny sériově jedním vláknem najednou v aplikaci s více vlákny. Microsoft .NET Common Language Run-time (CLR) poskytuje úplnou sadu synchronizace a zamykání primitiv. Například jazyk C# podporuje příkaz lock (SyncLock v jazyce Visual Basic). Spravovaná aplikace může volat metody Monitor.Enter a Monitor.Exit v oboru názvů System.Threading, aby získala a uvolnila zámek přímo. Rozhraní .NET Framework podporuje další synchronizaci a zamykání primitiv, včetně tříd, které podporují Mutexes, ReaderWriterLocks a Semafory. Další informace naleznete v [tématu Přehled primitiv synchronizace](/dotnet/standard/threading/overview-of-synchronization-primitives) v příručce pro vývojáře rozhraní .NET Framework na webu MSDN. Třídy rozhraní .NET Framework jsou samy vrstvené přes nižší úroveň synchronizačních služeb integrovaných do operačního systému Windows. Patří mezi ně kritické objekty řezu a mnoho různých Wait a události signalizační funkce. Další informace naleznete v části [Synchronizace](/windows/win32/sync/synchronization) win32 a vývoj com v knihovně MSDN.

 Základní třídy rozhraní .NET Framework a nativní objekty systému Windows, které se používají pro synchronizaci a zamykání, jsou sdílená umístění paměti, která musí být změněna pomocí propojených operací. Propojené operace používají hardwarově specifické pokyny, které pracují na umístění sdílené paměti, ke změně stavu pomocí atomických operací. Atomové operace jsou zaručeně konzistentní ve všech procesorech v počítači. Zámky a WaitHandles jsou objekty .NET, které automaticky používají propojené operace, když jsou nastaveny nebo resetovány. V aplikaci mohou existovat další struktury dat sdílené paměti, které také vyžadují použití propojených operací, aby byly aktualizovány bezpečným způsobem pro přístup z více vláken. Další informace naleznete v [tématu Interlocked Operations](/dotnet/api/system.threading.interlocked) v části Rozhraní .NET framework knihovny MSDN.

 Synchronizace a zamykání jsou mechanismy používané k zajištění, že aplikace s více vlákny se spouštějí správně. Každé vlákno vícevláknové aplikace je nezávislá prováděcí jednotka, která je naplánována nezávisle operačním systémem. Ke konfliktu zámku dochází vždy, když podproces, který se pokouší získat zámek je zpožděn, protože jiné vlákno drží zámek.

 Zámky jsou často vnořené. K vnoření dochází, když vlákno provádějící kritický oddíl provádí funkci, která pak vyžaduje jiný zámek. Určité množství vnoření zámku je nevyhnutelné. Kritická část může volat metodu rozhraní .NET Framework, která závisí na zámky k zajištění, že je bezpečné pro přístup z více vláken. Volání z některé kritické části ve vaší aplikaci do Framework metoda, která také uzamkne pomocí jiného popisovače zámku způsobí, že zámky vnoření. Vnořené podmínky uzamčení může vést k problémům s výkonem, které jsou notoricky obtížné rozluštit a opravit.

 Toto pravidlo je aktivována při měření během profilování spustit označují, že je příliš vysoké množství zámek kolize. Konflikty zámku zpoždění provádění podprocesů, které čekají na zámek. Dokonce i poměrně malé množství uzamčení kolize v jednotkových testech nebo v zátěžových testech spuštěných na hardwaru nižší konec by měly být zkoumány.

> [!NOTE]
> Pokud rychlost hlášené konflikty zámku v datech profilování je významné, ale není nadměrné, [DA0038: Vysoká rychlost uzamčení tvrzení](../profiling/da0038-high-rate-of-lock-contentions.md) informační zpráva je aktivována namísto této varovné zprávy.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu přejděte do zobrazení [Značky](../profiling/marks-view.md) dat profilování.  Vyhledejte sloupec **Zámky a vlákna .NET CLR\Míra konfliktů / s.** Zjistěte, zda existují určité fáze provádění programu, kde je konflikt zámku těžší než jiné fáze.

 Toto pravidlo je aktivována pouze v případě, že nepoužíváte metodu profilování souběžnosti. Metoda profilování souběžnosti je nejlepším nástrojem, který se používá k diagnostice problémů s výkonem souvisejících s konflikty zámku ve vaší aplikaci. Shromažďovat data profilování souběžnosti pochopit chování uzamčení vaší aplikace. To zahrnuje pochopení, které zámky jsou silně tvrdil, jak dlouho je zpožděna doba provádění podprocesu čekání na tvrdil zámky a jaký konkrétní kód je zapletený. Profily souběžnosti shromažďuje data o všech konfliktech zámků, včetně chování uzamčení nativních zařízení systému Windows, tříd rozhraní .NET Framework a všech ostatních knihoven třetích stran, na které vaše aplikace odkazuje. Informace o profilování souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z rozhraní IDE naleznete v [tématu Shromažďování dat souběžnosti podprocesu a zpracování souběžnosti](../profiling/collecting-thread-and-process-concurrency-data.md). Odkazy na informace o profilování souběžnosti z příkazového řádku naleznete v části **Použití metody souběžnosti ke shromažďování konfliktů prostředků a dat o aktivitě podprocesu** v části [Use profilování metod z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
