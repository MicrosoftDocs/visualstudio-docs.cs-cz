---
title: Rozšíření uživatelského rozhraní diagnostikování zpoždění v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1bf5dba23622c5dc3d964bdac19fec210aa60b1e
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639192"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Postupy: Diagnostika uživatelského rozhraní způsobených rozšířeními zpoždění

Když přestane reagovat uživatelské rozhraní, sady Visual Studio prozkoumá zásobníku volání vlákna uživatelského rozhraní, počínaje listu a funguje směrem k základní třídě. Pokud Visual Studio zjistí, že rámec zásobníku volání patří do modulu, který je součástí rozšíření nainstalované a povolené, zobrazuje oznámení o.

![Zpoždění uživatelského rozhraní (sekundový výpadek reakce) oznámení](media/ui-delay-notification-in-vs.png)

Oznámení informuje uživatele, že zpoždění uživatelského rozhraní (to znamená, sekundový výpadek reakce v uživatelském rozhraní) mohly být výsledek kódu z rozšíření. Poskytuje také uživatel s možnostmi zakázání rozšíření nebo budoucí oznámení pro toto rozšíření.

Tento dokument popisuje, jak můžete diagnostikovat, co ve vašem kódu rozšíření je příčinou oznámení zpoždění uživatelského rozhraní. 

> [!NOTE]
> Nepoužívejte experimentální instanci sady Visual Studio k diagnostikování zpoždění uživatelského rozhraní. Některé části zásobníku volání analýzy, vyžaduje se pro oznámení zpoždění uživatelského rozhraní jsou vypnuté, při použití experimentální instance, což znamená, že se nemusí zobrazit oznámení zpoždění uživatelského rozhraní.

Přehled procesu diagnostických vypadá takto:
1. Identifikace scénáře aktivační události.
2. Pomocí aktivit přihlašování restartujte VS.
3. Spusťte trasování událostí pro Windows.
4. Oznámení se zobrazí znovu aktivujte.
5. Zastavte trasování událostí pro Windows.
6. Vyhledejte v protokolu aktivit se získat ID zpoždění.
7. Analyzujte trasování událostí pro Windows trasování pomocí ID zpoždění v kroku 6.

V následujících částech si projdeme postup podrobněji.

## <a name="identify-the-trigger-scenario"></a>Identifikace scénáře aktivační událost

Diagnostikování zpoždění uživatelského rozhraní, musíte nejprve určit, jaké (posloupnost akcí) způsobí, že Visual Studio zobrazíte oznámení. Toto je v pořadí pro vás mohla k aktivaci oznámení později s zapnout protokolování.

## <a name="restart-vs-with-activity-logging-on"></a>Restartujte VS se aktivita přihlášení

Visual Studio můžete generovat "protokol aktivita", který poskytuje informace, které jsou užitečné při ladění chyby. Chcete-li v aktivitě protokolování v sadě Visual Studio, spusťte sadu Visual Studio s `/log` možnost příkazového řádku. Po spuštění sady Visual Studio protokolu aktivit se ukládají v následujícím umístění:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Další informace o způsobu, jakým lze hledají vaše VS ID instance najdete v tématu [nástroje pro zjišťování a správu instancí sady Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Použijeme tento protokol aktivit později a zjistěte další informace o opoždění v uživatelském rozhraní a související oznámení.

## <a name="starting-etw-tracing"></a>Spouští se trasování událostí pro Windows

Můžete použít [PerfView](https://github.com/Microsoft/perfview/) shromažďovat trasování ETW. PerfView poskytuje snadno použitelné rozhraní pro shromažďování trasování trasování událostí pro Windows a pro jeho analýzu. Chcete-li shromažďovat trasování, použijte následující příkaz:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

To umožňuje "Microsoft Visual Studio" poskytovatele, který se zprostředkovatel, který sada Visual Studio používá pro události související s oznámení zpoždění uživatelského rozhraní. Také určuje klíčové slovo pro zprostředkovatele jádra, pomocí nástroje PerfView můžete generovat **zásobníky vlákna čas** zobrazení.

## <a name="trigger-the-notification-to-appear-again"></a>Oznámení se zobrazí znovu aktivovat

Po zahájení shromažďování trasování PerfView můžete použít sekvenci akce aktivační událost (z kroku 1) pro oznámení se zobrazí znovu. Jakmile se zobrazí oznámení, můžete zastavit shromažďování trasování pro PerfView pro zpracování a vygenerovat výstupní soubor trasování.

## <a name="stop-etw-tracing"></a>Zastavit trasování událostí pro Windows

Chcete-li zastavit shromažďování trasování, jednoduše použijte **zastavit shromažďování** tlačítka v okně PerfView. Poté, co zastavíte shromažďování trasování, PerfView automaticky zpracuje události trasování událostí pro Windows a vygeneruje výstupní soubor trasování.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Zkontrolujte protokol aktivita k získání ID zpoždění

Jak už bylo zmíněno dříve, můžete najít protokolu aktivit se zapsaly *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*. Pokaždé, když sada Visual Studio zjistí rozšíření zpoždění uživatelského rozhraní, zapíše do protokolu aktivit s uzlem `UIDelayNotifications` jako zdroj. Tento uzel obsahuje čtyři druhy údajů o zpoždění uživatelského rozhraní:

- ID zpoždění uživatelského rozhraní, pořadové číslo, které jednoznačně identifikuje zpoždění uživatelského rozhraní v relaci VS
- ID relace, které je jedinečným identifikátorem od začátku až do zavření relace prostředí sady Visual Studio
- Určuje, jestli se zobrazilo oznámení, pro zpoždění uživatelského rozhraní
- Rozšíření, která pravděpodobné způsobila zpoždění uživatelského rozhraní

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
> Ne všechny uživatelské rozhraní se zpozdí za následek oznámení. Proto byste měli vždy zkontrolovat **oznámení zobrazí?** hodnotu pro zajištění správné identifikace správné zpoždění uživatelského rozhraní.

Po správném zpoždění uživatelského rozhraní najdete v protokolu aktivit, poznamenejte si ID zpoždění uživatelského rozhraní zadané v uzlu. Hledat odpovídající událost trasování událostí pro Windows v dalším kroku použijete ID.

## <a name="analyze-the-etw-trace"></a>Analyzovat trasování ETW

Trasovací soubor otevřete v dalším kroku. Můžete provést pomocí stejné instance PerfView nebo spouští novou instanci a nastavením aktuální cesta ke složce v levém horním rohu okna do umístění souboru trasování.

![Nastavení cesty ke složce v Perfview](media/perfview-set-path.png)

Potom vyberte soubor trasování v levém podokně a otevřete výběrem **otevřete** z nabídky klikněte pravým tlačítkem nebo kontext.

> [!NOTE]
> Ve výchozím nastavení výstupy PerfView archiv Zip. Když otevřete *trace.zip*, automaticky dekomprimuje archivu a otevře trasování. To můžete přeskočit zrušením **Zip** pole během kolekce trasování. Ale pokud máte v úmyslu přenosu a použít trasování na různých počítačích, důrazně doporučujeme před zrušením zaškrtnutí **Zip** pole. Bez této možnosti požadované soubory PDB pro Ngen sestavení nebude doprovázet trasování a proto nebudou symbolů ze sestavení Ngen přeloženy na cílovém počítači. (Viz [tento příspěvek na blogu](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) pro další informace o soubory PDB pro Ngen sestavení.) 

Může trvat několik minut, než PerfView pro zpracování a otevřít trasování. Po otevřít trasování se zobrazí pod ním seznam různých "zobrazení".

![Souhrnné zobrazení trasování nástroje PerfView](media/perfview-summary-view-events-selected.png)

Nejprve použijeme **události** zobrazení získat časový rozsah zpoždění uživatelského rozhraní:

1. Otevřít **události** zobrazení tak, že vyberete `Events` uzel pod trasování a zvolíte **otevřít** z nabídky klikněte pravým tlačítkem nebo kontext.
2. Vyberte "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" v levém podokně.
3. Stisknutím klávesy Enter

Použít výběr a všechny `ExtensionUIUnresponsiveness` události se zobrazí v pravém podokně.

![Výběr události v zobrazení události](media/perfview-event-selection.png)

Každý řádek v pravém podokně odpovídá zpoždění uživatelského rozhraní. Událost obsahuje hodnotu "Zpoždění ID", který by měl odpovídat ID zpoždění v protokolu aktivit v kroku 6. Protože `ExtensionUIUnresponsiveness` je vyvolána na konci zpoždění uživatelského rozhraní, časové razítko události (přibližně) značky koncového času zpoždění uživatelského rozhraní. Událost obsahuje také trvání zpoždění. Jsme odečtením doby trvání z časové razítko ukončení získat časové razítko při spuštění zpoždění uživatelského rozhraní.

![Výpočet čas range zpoždění uživatelského rozhraní](media/ui-delay-time-range.png)

Na předchozím snímku obrazovky například časové razítko události je 12,125.679 a doba zpoždění je 6,143.085 (ms). Tedy,
* Zpoždění začátku je 12,125.679 6,143.085 = 5,982.594.
* Časový rozsah zpoždění uživatelského rozhraní je 5,982.594 k 12,125.679.

Jakmile budeme mít časový rozsah, můžeme zavřít z celkového počtu **události** zobrazit a otevřít **zásobníky vlákna čas (s aktivitami StartStop)** zobrazení. Toto zobrazení je zvláště užitečný, protože často rozšíření, které blokují vlákna uživatelského rozhraní jsou pouze čeká na ostatní vlákna nebo vstupně-výstupní operace. Proto **procesoru zásobníku** zobrazení, které je nejvhodnější volbou pro většinu případů, nemusí zaznamenat čas vlákno stráví blokování vzhledem k tomu, že ho nepoužívá procesoru během této doby. **Zásobníky vlákna čas** tento problém řeší tím správně blokované znázorňující čas.

![Uzel čas (s aktivitami StartStop) zásobníky vlákna v zobrazení se souhrnnými PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Při otevírání **zásobníky vlákna čas** zobrazení, zvolte **devenv** procesu se spustit analýzu.

![Zobrazení zásobníků čas pro analýzu zpoždění uživatelského rozhraní vláknu](media/ui-delay-thread-time-stacks.png)

V **zásobníky vlákna čas** zobrazení, v levém horním rohu stránky, můžete nastavit časový rozsah na hodnoty jsme počítá v předchozím kroku a stiskněte klávesu **Enter** tak zásobníky upraveny tak, aby tento časový rozsah.

> [!NOTE]
> Určení, které vlákno je uživatelské rozhraní vlákno (spouštěcí) může být neintuitivní, pokud kolekce trasování spuštění po sady Visual Studio je již otevřen. První prvky v zásobníku vlákna uživatelského rozhraní (spuštění) jsou však nejpravděpodobnější vždy knihoven DLL operačního systému (*ntdll.dll* a *kernel32.dll*) následovaný `devenv!?` a potom `msenv!?` . Tato posloupnost pomáhá identifikovat vlákno uživatelského rozhraní.

 ![Identifikace spuštění vlákna](media/ui-delay-startup-thread.png)

Toto zobrazení můžete také dále filtrovat podle pouze včetně zásobníků, které obsahují moduly z vašeho balíčku.

* Nastavte **GroupPats** na prázdný text odebrat seskupení nepřidají ve výchozím nastavení.
* Nastavte **IncPats** zahrnout část název vašeho sestavení kromě existující filtr procesu. V takovém případě by měl být **devenv; UIDelayR2**.

![Nastavení GroupPath a IncPath v zobrazení vlákna zásobníky čas](media/perfview-tts-group-path-inc-path.png)

PerfView obsahuje podrobné pokyny v části **pomáhají** nabídky, která vám umožní identifikovat kritické body výkonu ve vašem kódu. Navíc následující odkazy obsahují další informace o tom, jak využít Visual Studio dělení na vlákna rozhraní API pro optimalizaci kódu:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

Nové analyzátory statické sady Visual Studio můžete také použít pro rozšíření (balíček NuGet [tady](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), která poskytnout Rady ohledně osvědčené postupy pro psaní efektivní rozšíření. Podívejte se do seznamu [VS SDK analyzátory](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) a [dělení na vlákna analyzátory](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Pokud nemůžete vyřešit sekundový výpadek reakce z důvodu závislosti není máte kontrolu nad (například pokud vaše rozšíření má volat synchronní služby VS na vlákně UI), rádi bychom vědět o něm. Pokud jste členem našeho programu partnerům pro Visual Studio, můžete nás kontaktovat odesláním žádosti o podporu pro vývojáře. V opačném případě pomocí nástroje "Nahlásit problém" odeslat zpětnou vazbu a zahrnují `"Extension UI Delay Notifications"` v názvu. Uvádějte prosím také podrobný popis analýzy.
