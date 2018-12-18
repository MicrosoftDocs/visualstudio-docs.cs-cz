---
title: 'DA0038: Vysoká míra kolizí zámků | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54788c20552380d22df8bad783d5012ac7157899
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922052"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Vysoká míra konfliktů zámků

|||  
|-|-|  
|Id pravidla|DA0038|  
|Kategorie|Použití rozhraní .NET framework|  
|Metoda profilace|Vzorkování<br /><br /> Instrumentace<br /><br /> Paměť .NET|  
|Zpráva|Dochází k vysoké míře sporů zámků platformy .NET. Zjistěte důvod pro tento spor zámku spuštěním profilace souběžnosti.|  
|Typ pravidla|Informace o|  

 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit alespoň 25 vzorky k aktivaci tohoto pravidla.  

## <a name="cause"></a>příčina  
 Systém údaje o výkonu, která se shromažďují se data profilace označuje, že výrazně vysoké míře sporů zámků došlo k chybě při spuštění aplikace. Vezměte v úvahu profilaci znovu pomocí metody profilace souběžného zpracování najít příčinu sporů.  

## <a name="rule-description"></a>Popis pravidla  
 Uzamčení se používají k ochraně důležitých části kódu, který musí být prováděny sériově jedním vláknem v daný okamžik v vícevláknové aplikace. Microsoft .NET Common Language Runtime (CLR) poskytuje úplnou sadu synchronizace a zamykání primitiv. Například jazyk C# podporuje příkaz lock (SyncLock v jazyce Visual Basic). Spravované aplikace může volat metody Monitor.Enter a Monitor.Exit v System.Threading – obor názvů pro získání a uvolnění zámku přímo. Rozhraní .NET Framework podporuje další synchronizace a zamykání primitiv, včetně tříd, které podporují mutexů ReaderWriterLocks a semafory. Další informace najdete v tématu [přehled primitiv synchronizace](http://go.microsoft.com/fwlink/?LinkId=177867) v rozhraní .NET Framework Developer's Guide na webové stránce MSDN. Tříd rozhraní .NET Framework jsou samotné Vrstvená na nižší úrovni synchronizační služby integrovaná do operačního systému Windows. Patří mezi ně objektů kritických části a mnoho různých čekání a funkce signalizace události. Další informace najdete v tématu [synchronizace](http://go.microsoft.com/fwlink/?LinkId=177869) část Win32 a COM Development v MSDN Library  

 Umístění sdílené paměti, které musí být změněny použití propojené operace jsou základní třídy rozhraní .NET Framework i nativních objektů Windows, které jsou používány k synchronizaci a zamykání. Propojené operace použití specifické pro hardware pokyny, které pracují na umístění sdílené paměti, chcete-li změnit jejich stav pomocí atomických operací. Atomické operace jsou zaručena konzistence do všech procesorů v počítači. Zámky a popisovačů WaitHandles jsou objekty .NET, které automaticky používají propojené operace, když jsou nastavit nebo obnovit. Mohou existovat jiné sdílené paměti datové struktury v aplikaci, která vyžaduje také použití propojené operace, aby bylo možné aktualizovat způsobem bezpečným pro vlákno. Další informace naleznete v tématu [propojený operace](http://go.microsoft.com/fwlink/?LinkId=177870) v části rozhraní.NET Framework na webu knihovny MSDN.  

 Synchronizace a zamykání jsou mechanismus používaný k zajištění vícevláknové aplikace můžete spustit správně. Každé vlákno vícevláknové aplikace je jednotka nezávislá spuštění, který je naplánován nezávisle operačním systému. Kolize zámků vyvolá se při každém vlákně, které se pokouší získat zámek je zpožděna, protože jiné vlákno drží zámek.  

 Často jsou vnořené zámky. Vnoření nastane, pokud vlákno provádění kritický oddíl provádí funkci, která se pak vyžaduje další zámek. Některé objemu vnoření zámek nevyhnutelné. Kritický oddíl, může volat metodu rozhraní .NET Framework, která závisí na zámků za účelem zajištění, že je bezpečná pro vlákno. Volání z některé důležité části ve vaší aplikaci do metody rozhraní Framework, která také uzamkne pomocí různých zámek popisovače způsobí, že zámky vnořit. Vnořené podmínky zamykání může vést k, které je známo, že obtížné unravel a opravit problémy s výkonem.  

 Toto pravidlo vyvolá při měření v průběhu spuštění profilování označuje, že je příliš vysoký počet zámků. Zámků zpoždění spuštění vlákna, která čekají na zámek. Dokonce i poměrně malý objem kolize zámků při testech jednotek nebo v zátěžových testech, které běží na hardwaru nižší by mělo být vypátráno.  

> [!NOTE]
>  Jestliže je míra ohlášené zámků v Profilování dat příliš vysoké [DA0039: velmi vysoká míra kolizí zámků](../profiling/da0039-very-high-rate-of-lock-contentions.md) místo tuto zprávu s informacemi o se aktivuje upozornění.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu, přejděte [značky](../profiling/marks-view.md) zobrazení dat profilování.  Najít **.NET CLR LocksAndThreads\Contention sazba za sekundu** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde je těžší než ostatní fáze kolize zámků.  

 Toto pravidlo je vyvoláno pouze v případě, že nepoužíváte metoda profilace souběžného zpracování. Metoda profilace souběžného zpracování je vždycky ten nejlepší nástroj určený pro diagnostiku problémů s výkonem související s kolize zámků ve vaší aplikaci. Shromažďování dat o chování aplikace při zamykání profilace souběžného zpracování. Jedná se o zámky, které jsou často ve sporných principy, jak dlouho doba provádění vlákna je zpožděno. čekání na zámků sporných a podílející jaký specifický kód. Souběžnost profily shromáždí data na všech zamknout sporů, včetně chování při zamykání nativní zařízení Windows, tříd rozhraní .NET Framework a další knihovny třetích stran aplikace odkazy. Informace o souběžnost profilování z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, viz [sběr dat souběžnosti podproces procesu a](../profiling/collecting-thread-and-process-concurrency-data.md). Odkazy na informace o souběžnost profilování z příkazového řádku naleznete **použít metodu souběžného shromažďovat data prostředku konflikty a podproces aktivity** část [použití metody profilování příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).