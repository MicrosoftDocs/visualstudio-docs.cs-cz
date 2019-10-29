---
title: 'DA0038: vysoká míra kolizí zámků | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43b4ddedf68d082c8de50a38f759c5db0a594d00
ms.sourcegitcommit: bb5425b9c6d8fd7135d9584c2963831754071347
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73024670"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: vysoká míra kolizí zámků

|||
|-|-|
|ID pravidla|DA0038|
|Kategorie|Využití .NET Framework|
|Metoda profilace|Kontrol<br /><br /> Instrumentace<br /><br /> Paměť .NET|
|Zpráva|Dochází k vysoké míře sporů zámků .NET. Vyzkoumejte důvod pro tento spor zámku spuštěním profilu souběžnosti.|
|Typ pravidla|Informace o|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit alespoň 25 vzorků.

## <a name="cause"></a>příčina
 Data o výkonu systému shromážděná s daty profilace znamenají, že během provádění aplikace došlo k výraznému vysokému podílu kolizí zámků. Zvažte znovu profilaci pomocí metody profilace souběžnosti, abyste zjistili příčinu sporů.

## <a name="rule-description"></a>Popis pravidla
 Zámky slouží k ochraně kritických oddílů kódu, které musí být spuštěny v jednom vlákně v čase v aplikaci s více vlákny. Modul runtime CLR (Common Language Runtime) platformy Microsoft .NET poskytuje úplnou sadu synchronizačních a uzamykání primitiv. Například C# jazyk podporuje příkaz lock (SyncLock in Visual Basic). Spravovaná aplikace může zavolat monitor. k získání a uvolnění zámku použijte metody v oboru názvů System. Threading. .NET Framework podporuje další prvky synchronizace a zamykání, včetně tříd, které podporují mutexy, ReaderWriterLocks a semafory. Další informace najdete v tématu [Přehled primitiv synchronizace](/dotnet/standard/threading/overview-of-synchronization-primitives) v příručce pro vývojáře .NET Framework na webu MSDN. Třídy .NET Framework jsou samy vrstveny v rámci synchronizačních služeb nižší úrovně integrovaných do operačního systému Windows. Patří mezi ně důležité objekty oddílu a mnoho různých funkcí čekání a signalizace událostí. Další informace najdete v části [synchronizace](/windows/win32/sync/synchronization) pro vývoj v systémech Win32 a com v knihovně MSDN.

 Základními .NET Framework třídy i nativní objekty Windows, které se používají pro synchronizaci a uzamykání, jsou sdílené paměťové umístění, které se musí změnit pomocí propojených operací. Propojené operace používají pro změnu jejich stavu pomocí atomických operací pokyny specifické pro hardware, které pracují na umístěních sdílené paměti. U atomických operací je zaručena konzistence v rámci všech procesorů v počítači. Zámky a WaitHandles jsou objekty .NET, které automaticky používají propojené operace při jejich nastavení nebo resetování. V aplikaci mohou být k dispozici další struktury dat sdílené paměti, které také vyžadují, abyste používali propojené operace, aby je bylo možné aktualizovat pouze v bezpečném vlákně. Další informace najdete v tématu [propojené operace](/dotnet/api/system.threading.interlocked) v části .NET Framework v knihovně MSDN.

 Synchronizace a uzamykání jsou mechanismy, pomocí kterých se zajišťuje správné spouštění aplikací s více vlákny. Každé vlákno aplikace s více vlákny je nezávislá jednotka spuštění, která je naplánována nezávisle na operačním systému. K kolizí zámků dochází pokaždé, když je vlákno, které se pokouší získat zámek, zpožděno, protože zámek zadrží jiné vlákno.

 Zámky jsou často vnořené. K vnořování dochází, když vlákno spouštějící kritickou část provede funkci, která pak vyžaduje jiný zámek. Určité množství vnoření zámku je nenevyhnutelné. Vaše kritická část může volat .NET Framework metodu, která spoléhá na zámky, aby bylo zajištěno, že je bezpečná pro přístup z více vláken. Volání z některé důležité části aplikace do metody rozhraní, která také zamkne pomocí jiného popisovače zámku, způsobí vnoření zámků. Vnořené podmínky zamykání můžou vést k problémům s výkonem, které jsou obvykle odlaďuje obtížné Unravel a opravit.

 Toto pravidlo je vyvoláno, když měření prováděná během profilace poukazují na nadměrné vysoké množství kolizí zámků. U kolizí zámků dochází ke zpoždění provádění vláken, která čekají na zámek. Měla by se prozkoumat i poměrně malá část kolizí zámků v testech jednotek nebo zátěžové testy, které běží na nižším koncovém hardwaru.

> [!NOTE]
> Pokud je míra hlášených kolizí zámků v datech profilace příliš vysoká, je místo této informační zprávy aktivována [DA0039: velmi vysoká míra kolizí zámků](../profiling/da0039-very-high-rate-of-lock-contentions.md) .

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvojitým kliknutím na zprávu přejdete do zobrazení [značky](../profiling/marks-view.md) dat profilace.  Vyhledá sloupec **LocksAndThreads\Contention .NET CLR počet přenosů/s** . Určete, zda existují konkrétní fáze provádění programu, kde je těžší kolize zámku než jiné fáze.

 Toto pravidlo je aktivováno pouze v případě, že nepoužíváte metodu profilace souběžnosti. Metoda profilace souběžného zpracování je nejlepším nástrojem, který slouží k diagnostice problémů s výkonem souvisejících s uzamčením kolizí ve vaší aplikaci. Shromážděte data profilace souběžnosti, abyste pochopili chování aplikace při zamykání. To zahrnuje porozumění, které zámky jsou silně ovlivněny, jak dlouho je doba spuštění vlákna zpožděná čekáním na zavedené zámky a jaký konkrétní kód je implicated. Profily souběžnosti shromažďují data o všech sporech zámků, včetně chování při zamykání nativních zařízení s Windows, .NET Framework tříd a dalších knihoven třetích stran, na které vaše aplikace odkazuje. Informace o shromažďování souběžnosti z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) najdete v tématu [shromáždění dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md). Odkazy na informace o profilaci souběžnosti z příkazového řádku naleznete v části **použití metody souběžnosti ke shromáždění dat o kolize prostředků a dat aktivity vlákna** v tématu [použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).