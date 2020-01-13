---
title: 'DA0039: velmi vysoká míra kolizí zámků | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fcb38184a1d432ca036be88c4d957c0e4d4f419
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917165"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Velmi vysoká míra kolizí zámků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [DA0039: velmi vysoká míra kolizí zámků](/visualstudio/profiling/da0039-very-high-rate-of-lock-contentions).  
  
|||  
|-|-|  
|Id pravidla|DA0039|  
|Kategorie|Využití .NET Framework|  
|Metody profilace|Vzorkování<br /><br /> Instrumentace<br /><br /> Paměť .NET|  
|Zpráva|Dochází k velmi vysoké míře sporů zámků .NET. Vyzkoumejte důvod pro tento spor zámku spuštěním profilu souběžnosti.|  
|Typ pravidla|Upozornění|  
  
 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit alespoň 25 vzorků.  
  
## <a name="cause"></a>příčina  
 Data o výkonu systému shromážděná s daty profilace znamenají, že během provádění aplikace došlo k nadměrné vysoké míře kolizí zámků. Zvažte znovu profilaci pomocí metody profilace souběžnosti, abyste zjistili příčinu sporů.  
  
## <a name="rule-description"></a>Popis pravidla  
 Zámky slouží k ochraně kritických oddílů kódu, které musí být spuštěny v jednom vlákně v čase v aplikaci s více vlákny. Modul runtime CLR (Common Language Runtime) platformy Microsoft .NET poskytuje úplnou sadu synchronizačních a uzamykání primitiv. Například C# jazyk podporuje příkaz lock (SyncLock in Visual Basic). Spravovaná aplikace může volat metody `Monitor.Enter` a `Monitor.Exit` v oboru názvů System. Threading pro získání a uvolnění zámku přímo. .NET Framework podporuje další prvky synchronizace a zamykání, včetně tříd, které podporují mutexy, ReaderWriterLocks a semafory. Další informace najdete v tématu [Přehled primitiv synchronizace](https://msdn.microsoft.com/library/ms228964.aspx) v příručce pro vývojáře .NET Framework na webu MSDN. .NET Framework třídy jsou samy vrstveny na nižší úrovni synchronizačních služeb, které jsou integrované v operačním systému Windows. Patří mezi ně důležité objekty oddílu a mnoho různých funkcí čekání a signalizace událostí. Další informace najdete v části [synchronizace](https://msdn.microsoft.com/library/ms686353.aspx) pro vývoj v systémech Win32 a com v knihovně MSDN.  
  
 Základními .NET Framework třídy i nativní objekty Windows, které se používají pro synchronizaci a uzamykání, jsou sdílené paměťové umístění, které se musí změnit pomocí propojených operací. Propojené operace používají pro změnu jejich stavu pomocí atomických operací pokyny specifické pro hardware, které pracují na umístěních sdílené paměti. U atomických operací je zaručena konzistence v rámci všech procesorů v počítači. Zámky a WaitHandles jsou objekty .NET, které automaticky používají propojené operace při jejich nastavení nebo resetování. V aplikaci mohou být k dispozici další struktury dat sdílené paměti, které také vyžadují, abyste používali propojené operace, aby je bylo možné aktualizovat pouze v bezpečném vlákně. Další informace najdete v tématu [propojené operace](https://msdn.microsoft.com/library/sbhbke0y.aspx) v části .NET Framework v knihovně MSND.  
  
 Synchronizace a uzamykání jsou mechanismy, pomocí kterých se zajišťuje správné spouštění aplikací s více vlákny. Každé vlákno aplikace s více vlákny je nezávislá jednotka spuštění, která je naplánována nezávisle na operačním systému. K kolizí zámků dochází pokaždé, když je vlákno, které se pokouší získat zámek, zpožděno, protože zámek zadrží jiné vlákno.  
  
 Zámky jsou často vnořené. K vnořování dochází, když vlákno spouštějící kritickou část provede funkci, která pak vyžaduje jiný zámek. Určité množství vnoření zámku je nenevyhnutelné. Vaše kritická část může volat .NET Framework metodu, která spoléhá na zámky, aby bylo zajištěno, že je bezpečná pro přístup z více vláken. Volání z některé důležité části aplikace do metody rozhraní, která také zamkne pomocí jiného popisovače zámku, způsobí vnoření zámků. Vnořené podmínky zamykání můžou vést k problémům s výkonem, které jsou obvykle odlaďuje obtížné Unravel a opravit.  
  
 Toto pravidlo je vyvoláno, když měření prováděná během profilace poukazují na nadměrné vysoké množství kolizí zámků. U kolizí zámků dochází ke zpoždění provádění vláken, která čekají na zámek. Měla by se prozkoumat i poměrně malá část kolizí zámků v testech jednotek nebo zátěžové testy, které běží na nižším koncovém hardwaru.  
  
> [!NOTE]
> Pokud je počet hlášených kolizí zámků v datech profilace značný, ale ne nadměrný, DA0038: místo této zprávy upozornění se aktivuje zpráva s informacemi o kolizí kolizí ( [Vysoká míra kolizí zámků](../profiling/da0038-high-rate-of-lock-contentions.md) ).  
  
## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění  
 Dvojitým kliknutím na zprávu přejdete do zobrazení [značky](../profiling/marks-view.md) dat profilace.  Vyhledá sloupec **LocksAndThreads\Contention .NET CLR počet přenosů/s** . Určete, zda existují konkrétní fáze provádění programu, kde je těžší kolize zámku než jiné fáze.  
  
 Toto pravidlo je aktivováno pouze v případě, že nepoužíváte metodu profilace souběžnosti. Metoda profilace souběžného zpracování je nejlepším nástrojem, který slouží k diagnostice problémů s výkonem souvisejících s uzamčením kolizí ve vaší aplikaci. Shromážděte data profilace souběžnosti, abyste pochopili chování aplikace při zamykání. To zahrnuje porozumění, které zámky jsou silně ovlivněny, jak dlouho je doba spuštění vlákna zpožděná čekáním na zavedené zámky a jaký konkrétní kód je implicated. Profily souběžnosti shromažďují data o všech sporech zámků, včetně chování při zamykání nativních zařízení s Windows, .NET Framework tříd a dalších knihoven třetích stran, na které vaše aplikace odkazuje. Informace o shromažďování souběžnosti z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) najdete v tématu [shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md). Odkazy na informace o profilaci souběžnosti z příkazového řádku naleznete v části **použití metody souběžnosti ke shromáždění dat o kolize prostředků a dat aktivity vlákna** v tématu [použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
