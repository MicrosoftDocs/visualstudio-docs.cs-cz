---
title: Diagnostikování prodlev uživatelského rozhraní rozšíření v aplikaci Visual Studio | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: e8b35a566eb0f2457d6eb8ae3a33235df2a64cd3
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849152"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Postupy: Diagnostika zpoždění uživatelského rozhraní způsobená rozšířeními

Když uživatelské rozhraní přestane reagovat, Visual Studio prohledá volání zásobníku vlákna uživatelského rozhraní počínaje listem a pracuje směrem k základnímu. Pokud sada Visual Studio zjistí, že rámec zásobníku volání patří do modulu, který je součástí nainstalovaného a povoleného rozšíření, zobrazí se oznámení.

![Oznámení o zpoždění uživatelského rozhraní (nereagující)](media/ui-delay-notification-in-vs.png)

Oznámení informuje uživatele o tom, že zpoždění uživatelského rozhraní (tj. neschopnost reakce v uživatelském rozhraní) bylo pravděpodobně výsledkem kódu z rozšíření. Poskytuje také uživateli možnosti pro zakázání rozšíření nebo budoucích oznámení pro toto rozšíření.

Tento dokument popisuje, jak můžete diagnostikovat, co ve vašem kódu rozšíření způsobuje oznámení o zpoždění uživatelského rozhraní.

> [!NOTE]
> Nepoužívejte experimentální instanci sady Visual Studio k diagnostice zpoždění uživatelského rozhraní. Některé části analýzy zásobníku volání požadované pro upozornění na zpoždění uživatelského rozhraní jsou při použití experimentální instance vypnuté, což znamená, že se nezobrazují oznámení o zpoždění uživatelského rozhraní.

Přehled procesu diagnostiky je následující:
1. Identifikujte scénář triggeru.
2. Restartujte VS s přihlášením aktivity.
3. Spustit trasování ETW.
4. Aktivujte oznámení, aby se zobrazilo znovu.
5. Zastavit trasování ETW.
6. Projděte si protokol aktivit a Získejte ID zpoždění.
7. Analyzujte trasování ETW pomocí ID zpoždění z kroku 6.

V následujících částech budeme projít tyto kroky podrobněji.

## <a name="identify-the-trigger-scenario"></a>Identifikace scénáře triggeru

Chcete-li diagnostikovat zpoždění uživatelského rozhraní, musíte nejprve určit, co (sekvence akcí) způsobí, že aplikace Visual Studio zobrazí oznámení. Je tak možné, že budete moci oznámení aktivovat později s zapnutým protokolováním.

## <a name="restart-vs-with-activity-logging-on"></a>Restartování VS s přihlášením aktivity

Visual Studio může generovat "protokol aktivit", který poskytuje informace užitečné při ladění problému. Chcete-li zapnout protokolování aktivit v aplikaci Visual Studio, otevřete aplikaci Visual Studio s možností příkazového řádku `/log`. Po spuštění sady Visual Studio se protokol aktivit uloží do následujícího umístění:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Další informace o tom, jak najít ID instance VS, najdete v tématu [Nástroje pro zjišťování a správu instancí sady Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Později tento protokol aktivit použijeme k získání dalších informací o zpožděních uživatelského rozhraní a souvisejících oznámeních.

## <a name="starting-etw-tracing"></a>Spouští se trasování ETW.

[PerfView](https://github.com/Microsoft/perfview/) můžete použít ke shromáždění trasování ETW. PerfView poskytuje snadno použitelné rozhraní pro shromažďování trasování ETW a pro jeho analýzu. K shromáždění trasování použijte následující příkaz:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Tím povolíte poskytovatele "Microsoft-VisualStudio", který je poskytovatelem sady Visual Studio použito pro události související s oznámeními o zpoždění uživatelského rozhraní. Určuje také klíčové slovo pro zprostředkovatele jádra, které PerfView může použít ke generování zobrazení **zásobníků času vlákna** .

## <a name="trigger-the-notification-to-appear-again"></a>Aktivovat oznámení, aby se zobrazila znovu

Jakmile PerfView spustí shromažďování trasování, můžete použít sekvenci akcí triggeru (z kroku 1), aby se oznámení zobrazilo znovu. Po zobrazení oznámení můžete zastavit shromažďování trasování, aby PerfView zpracovalo a vygenerovalo výstupní trasovací soubor.

## <a name="stop-etw-tracing"></a>Zastavit trasování ETW

Chcete-li zastavit shromažďování trasování, jednoduše použijte tlačítko **Zastavit shromažďování** v okně PerfView. Po zastavení shromažďování dat trasování PerfView automaticky zpracuje události ETW a vygeneruje výstupní trasovací soubor.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Projděte si protokol aktivit a Získejte ID zpoždění.

Jak bylo zmíněno dříve, můžete najít protokol aktivit na adrese *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.XML*. Pokaždé, když Visual Studio rozpozná zpoždění uživatelského rozhraní rozšíření, zapíše uzel do protokolu aktivit s `UIDelayNotifications` jako zdroj. Tento uzel obsahuje čtyři části informací o zpoždění uživatelského rozhraní:

- ID zpoždění uživatelského rozhraní, pořadové číslo, které jedinečně identifikuje zpoždění uživatelského rozhraní v relaci VS
- ID relace, které jedinečně identifikuje vaši relaci Visual studia od začátku do ukončení
- Bez ohledu na to, jestli se pro zpoždění uživatelského rozhraní zobrazilo oznámení
- Rozšíření, které pravděpodobně způsobilo zpoždění uživatelského rozhraní

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Ne všechny prodlevy uživatelského rozhraní mají za následek oznámení. Proto byste měli vždycky ověřit **zobrazené oznámení?** hodnota, která správně identifikuje správné zpoždění uživatelského rozhraní.

Po nalezení správné prodlevy uživatelského rozhraní v protokolu aktivit zapište ID zpoždění uživatelského rozhraní zadané v uzlu. Pomocí ID vyhledáte odpovídající událost ETW v dalším kroku.

## <a name="analyze-the-etw-trace"></a>Analýza trasování ETW

Pak otevřete trasovací soubor. Můžete to provést buď pomocí stejné instance PerfView, nebo spuštěním nové instance a nastavením cesty k aktuální složce v levém horním rohu okna do umístění trasovacího souboru.

![Nastavení cesty ke složce v PerfView](media/perfview-set-path.png)

Pak vyberte trasovací soubor v levém podokně a otevřete ho kliknutím pravým tlačítkem nebo místní nabídky na **otevřít** .

> [!NOTE]
> Ve výchozím nastavení PerfView vytvoří výstup archivu zip. Když otevřete *Trace. zip*, automaticky dekomprimuje archiv a otevře trasování. Tuto možnost můžete přeskočit zrušením kontroly pole **zip** během shromažďování trasování. Pokud ale plánujete přenos a používání trasování v různých počítačích, důrazně doporučujeme před zrušením kontroly pole **zip** . Bez této možnosti se požadovaná soubory PDB pro sestavení Ngen nebudou doprovázet s trasováním, takže symboly ze sestavení Ngen nebudou na cílovém počítači přeloženy. (Další informace o soubory PDB pro Ngen sestavení najdete v [tomto blogovém příspěvku](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) .)

Zpracování PerfView a otevření trasování může trvat několik minut. Jakmile je trasování otevřené, zobrazí se v něm seznam různých zobrazení.

![Souhrnné zobrazení PerfView trasování](media/perfview-summary-view-events-selected.png)

Nejprve použijeme zobrazení **události** k získání časového rozsahu zpoždění uživatelského rozhraní:

1. Otevřete zobrazení **události** tak, že v trasování vyberete uzel `Events` a vyberete **otevřít** z místní nabídky nebo kliknutím pravým tlačítkem myši.
2. V levém podokně vyberte "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`".
3. Stiskněte klávesu ENTER

Výběr se použije a v pravém podokně se zobrazí všechny události `ExtensionUIUnresponsiveness`.

![Výběr událostí v zobrazení událostí](media/perfview-event-selection.png)

Každý řádek v pravém podokně odpovídá zpoždění uživatelského rozhraní. Událost obsahuje hodnotu "Delay ID", která by se měla shodovat s ID zpoždění v protokolu aktivit z kroku 6. Vzhledem k tomu, že `ExtensionUIUnresponsiveness` je vyvolána na konci zpoždění uživatelského rozhraní, časové razítko události (zhruba) označí čas ukončení zpoždění uživatelského rozhraní. Událost také obsahuje dobu trvání prodlevy. Po spuštění zpoždění uživatelského rozhraní můžeme odčítat dobu trvání od koncového časového razítka a získat tak časové razítko.

![Výpočet časového rozsahu prodlevy uživatelského rozhraní](media/ui-delay-time-range.png)

Na předchozím snímku obrazovky je například časové razítko události 12 125,679 a doba trvání prodlevy je 6 143,085 (MS). Tedy,
* Zpoždění spuštění je 12 125,679-6 143,085 = 5 982,594.
* Časový rozsah doby zpoždění uživatelského rozhraní je 5 982,594 až 12 125,679.

Jakmile budeme mít časový rozsah, můžeme zavřít zobrazení **událostí** a otevřít zobrazení **zásobníků času vláken (se StartStop aktivitami)** . Toto zobrazení je obzvlášť užitečné, protože často rozšíření blokující vlákno uživatelského rozhraní jsou pouze čekat na jiná vlákna nebo na vstupně-výstupní operaci. To znamená, že zobrazení **zásobníku procesoru** , což je možnost přejít k pro většinu případů, nemusí zachytit čas, který vlákno zachytí, protože během této doby nevyužívá procesor. **Zásobníky času vlákna** vyřeší tento problém tím, že správně zobrazují čas zablokování.

![Doba vlákna (s aktivitami StartStop) uzel zásobníků v zobrazení souhrnu PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Během otevírání zobrazení **zásobníků času vlákna** vyberte proces **devenv** pro spuštění analýzy.

![Zobrazení zásobníků času vlákna pro analýzu zpoždění uživatelského rozhraní](media/ui-delay-thread-time-stacks.png)

V zobrazení **zásobníky času vlákna** v levém horním rohu stránky můžete nastavit časový rozsah na hodnoty, které jsme vypočítali v předchozím kroku, a stisknout **ENTER** , aby se zásobníky upravily na tento časový rozsah.

> [!NOTE]
> Určení vlákna, které je podprocesem uživatelského rozhraní (spuštění), může být neintuitivní při spuštění shromažďování trasování po otevření sady Visual Studio. Nicméně první prvky v zásobníku uživatelského rozhraní (spuštění) jsou nejvíce pravděpodobně knihovny DLL operačního systému (*Ntdll. dll* a *Kernel32. dll*) následované `devenv!?` a potom `msenv!?`. Tato sekvence může přispět k identifikaci vlákna uživatelského rozhraní.

 ![Identifikace spouštěcího vlákna](media/ui-delay-startup-thread.png)

Toto zobrazení můžete také dál filtrovat tak, že zahrnete jenom zásobníky, které obsahují moduly z vašeho balíčku.

* Pokud chcete odebrat jakékoli seskupení přidané ve výchozím nastavení, nastavte **GroupPats** na prázdný text.
* Nastavte **IncPats** tak, aby zahrnoval část názvu sestavení spolu s existujícím filtrem procesu. V takovém případě by měl být **devenv; UIDelayR2**.

![Nastavení GroupPath a IncPath v zobrazení zásobníků času vlákna](media/perfview-tts-group-path-inc-path.png)

PerfView má podrobné pokyny v nabídce **help** , kterou můžete použít k identifikaci kritických bodů výkonu v kódu. Kromě toho následující odkazy poskytují další informace o tom, jak používat rozhraní API pro vlákna sady Visual Studio k optimalizaci kódu:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

Nové nástroje Visual Studio static Analyzer for Extensions (balíček NuGet [tady](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)) poskytují pokyny k osvědčeným postupům pro psaní efektivních rozšíření. Podívejte se na seznam [analyzátorů vs SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) a [analyzátorů vláken](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Pokud se vám nedaří vyřešit nereagující z důvodu závislostí, které neovládáte (například pokud vaše rozšíření musí volat synchronní služby VS Services ve vlákně uživatelského rozhraní), chceme o něm získat informace. Pokud jste členem našeho programu Visual Studio partner program, můžete nás kontaktovat odesláním žádosti o podporu pro vývojáře. V opačném případě použijte k odeslání vašeho názoru nástroj nahlásit problém a přidejte `"Extension UI Delay Notifications"` do nadpisu. Uveďte také podrobný popis analýzy.
