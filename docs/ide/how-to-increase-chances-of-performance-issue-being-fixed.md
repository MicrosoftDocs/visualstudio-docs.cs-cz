---
title: Jak můžete zvýšit pravděpodobnost, že bude problém s výkonem opraven
description: Další informace a doporučené postupy pro odesílání problémů s výkonem v sadě Visual Studio
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: 119de27298acafee7dc563a30246b18da42f9f29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918165"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Jak zvýšit pravděpodobnost, že bude problém s výkonem vyřešen

Nástroj["Nahlásit problém"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)je široce používán uživateli sady Visual Studio k hlášení řady problémů. Tým sady Visual Studio zjistí selhání a pomalost trendy zpětné vazby od uživatelů a řeší problémy, které mají vliv na široký pás uživatelů. Čím je konkrétní lístek zpětné vazby citlivější, tím je pravděpodobnější, že bude produktový tým rychle diagnostikován a vyřešen. Tento dokument popisuje osvědčené postupy při hlášení problémů s selháním nebo pomalostí, aby byly žalovatelné.

## <a name="general-best-practices"></a>Obecné osvědčené postupy

Visual Studio je velká, komplexní platforma, která podporuje velké množství jazyků, typů projektů, platforem a dalších. Jak to funguje, je funkce, které součásti jsou nainstalovány a aktivní v relaci, nainstalované rozšíření, nastavení sady Visual Studio, konfigurace počítače a nakonec tvar kódu, který je upravován. Vzhledem k počtu proměnných je obtížné zjistit, zda má zpráva o problému od jednoho uživatele stejný základní problém jako hlášení o problému od jiného uživatele, i když je viditelný příznak stejný. Vzhledem k tomu, že zde jsou některé osvědčené postupy, které zajistí, že vaše konkrétní zpráva o problému má vyšší pravděpodobnost, že bude diagnostikována.

**Uveďte co nejkonkrétnější název**

Vyhledejte odlišné podpisy pro problém, který je hlášen, a zahrňte co nejvíce v názvu. Pokud je název popisný, je méně pravděpodobné, že uživatelé s nesouvisejícími problémy (ale stejným povrchovým příznakem) budou hlasovat nebo komentovat váš lístek, čímž ztíží diagnózu *vašeho* problému.

**V případě pochybností se přihlásíte k nové zprávě o problému.**

Mnoho problémů nemusí mít žádný charakteristický podpis nebo kroky k reprodukci. V takových případech je nová zpráva lepší než hlasování nebo komentář k jiné zprávě, která hlásí podobný vnější *příznak*. V závislosti na typu sestavy zahrňte do sestavy další diagnostické soubory, jak je popsáno dále v tomto dokumentu.

**Osvědčené postupy specifické pro konkrétní problémy**

Níže jsou popsány problémy, které je obtížné diagnostikovat bez dobrých diagnostických souborů. Po identifikaci případu, který nejlépe popisuje váš problém, postupujte podle kroků zpětné vazby specifických pro tento případ.

-   [Pády:](#crashes) K chybě dojde, když proces (Visual Studio) neočekávaně ukončí.

-   [Nereagornost:](#unresponsiveness) VS přestane reagovat na delší dobu.

-   [Problémy s pomalostí:](#slowness-and-high-cpu-issues) Každá konkrétní akce ve VS je pomalejší, než je požadováno

-   [Vysoký procesor:](#slowness-and-high-cpu-issues) Prodloužená období neočekávaně vysokého využití procesoru

-   [Problémy mimo proces:](#out-of-process-issues) Problém způsobený satelitním procesem sady Visual Studio

## <a name="crashes"></a>Pády
K chybě dojde, když proces (Visual Studio) neočekávaně ukončí.

**Přímo reprodukovatelné pády**

Přímo reprodukovatelné pády jsou případy, které mají všechny následující charakteristiky:

- Lze pozorovat podle známého souboru kroků

- Lze pozorovat na více počítačích (pokud je k dispozici)

- Může být reprodukován v ukázkovém kódu nebo projektu, který může být propojen nebo poskytnut jako součást zpětné vazby (pokud kroky zahrnují otevření projektu nebo dokumentu)

V těchto problémech postupujte podle pokynů v části[Jak nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)a nezapomeňte uvést:

-   Kroky k reprodukci problému

-   Samostatný projekt repro, jak je popsáno výše. Pokud samostatná repro není možná, uveďte prosím:

    -   Jazyk otevřených projektů (C\#, C++atd.)

    -   Druh projektu (konzolová aplikace, ASP.NET atd.)


> [!NOTE]
> **Nejcennější zpětná vazba:** V tomto případě nejcennější zpětnou vazbu je sada kroků pro reprodukci problému spolu s ukázkovým zdrojovým kódem.

**Neznámé pády**

Pokud si nejste jisti, co způsobuje vaše pády nebo se zdají být náhodné, můžete zachytit výpisy místně pokaždé, když dojde k chybě sady Visual Studio a připojit je k samostatným položkám zpětné vazby. Chcete-li uložit výpisy místně při selhání sady Visual Studio, spusťte v okně příkazů správce následující příkazy:

```
reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\\CrashDumps"
```

Podle potřeby přizpůsobte počet výpisu a složku výpisu. Další informace o těchto nastaveních naleznete [zde](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Výpisy zachycené pomocí Správce úloh pravděpodobně budou nesprávné bitness, což je méně použitelné. Výše popsaný postup je upřednostňovaný způsob zachycení výpisu haldy. Pokud chcete použít Správce úloh, zavřete ten, který je aktuálně spuštěn, spusťte\\32bit Správce\\úloh (%windir% syswow64 taskmgr.exe) a sbírat výpis haldy odtud.

> [!NOTE] 
> Každý soubor s výpisem stavu paměti vytvořený touto metodou bude mít velikost až 4 GB. Ujistěte se, že nastavit DumpFolder do umístění s odpovídající místo na disku nebo upravit DumpCount odpovídajícím způsobem.

Pokaždé, když dojde k chybě sady Visual Studio, vytvoří soubor s výpisem stavu paměti **devenv.exe.[ číslo].dmp** v nakonfigurovaném umístění.

Potom použijte Visual Studio je "Nahlásit problém..." Funkce. To vám umožní připojit příslušný výpis.

1.  Vyhledejte soubor s výpisem stavu systému pro stav, který hlásíte (vyhledejte soubor se správným časem vytvoření)

2.  Pokud je to možné, zip soubor (.zip)\*snížit jeho velikost před odesláním zpětné vazby

3.  Postupujte podle pokynů v části[Jak nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)a připojte výpis haldy k nové položce zpětné vazby.

> [!NOTE] 
> **Nejcennější zpětná vazba:** V tomto případě nejcennější zpětnou vazbu je výpis haldy zachycené v době selhání.

## <a name="unresponsiveness"></a>Nerezistovna
VS přestane reagovat na delší dobu.

**Přímo reprodukovatelná nereagoznost**

Jak je popsáno v odpovídající části o haváriích, pro problémy, které lze snadno reprodukovat, vidět na více strojích a mohou být demonstrovány v malém vzorku, nejcennější zprávy o zpětné vazbě jsou ty, které obsahují kroky k reprodukci problému a zahrnují ukázkový zdrojový kód, který demonstruje problém.

**Neznámá nereagoza**

Pokud neodpovídá projevem nepředvídatelného způsobem, při dalším výskytu spusťte novou instanci sady Visual Studio a nahlaste problém z této instance.
Na [obrazovce "Záznam"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)nezapomeňte vybrat relaci sady Visual Studio, která neodpovídá.

Pokud visual studio instance, která neodpovídá byla spuštěna v režimu správce, pak druhá instance bude také nutné spustit v režimu správce.

>[!NOTE] 
> **Nejcennější zpětná vazba:** V tomto případě nejcennější zpětnou vazbu je výpis haldy zachycené v době neodpovídá.

## <a name="slowness-and-high-cpu-issues"></a>Pomalost a vysoké problémy s procesorem

Co dělá pomalost nebo vysoké využití procesoru problém nejvíce žalovatelné je sledování výkonu zachycené při pomalé operace nebo vysoké události procesoru probíhá.

>[!NOTE] 
> Pokud je to možné, izolujte každý scénář v samostatné, konkrétní sestavy zpětné vazby.
Pokud jsou například psaní a navigace pomalé, postupujte podle následujících kroků jednou za problém. To pomáhá produktový tým izolovat příčinu konkrétních problémů.

Nejlepších výsledků při zachycení výkonu dosáhnete takto:

1.  Pokud již není spuštěna, mít otevřenou kopii sady Visual Studio, kde budete problém reprodukovat

    -   Mít vše nastaveno pro reprodukci problému. Například pokud potřebujete konkrétní projekt, který má být načten s určitým souborem otevřít, ujistěte se, že oba tyto kroky jsou dokončeny před pokračováním.

    -   Pokud *nehlásíte* problém specifický pro načítání řešení, zkuste počkat 5-10 minut (nebo více, v závislosti na velikosti řešení) po otevření řešení před zaznamenáním sledování výkonu. Proces načítání řešení vytváří velké množství dat, takže čekání na několik minut nám pomáhá zaměřit se na konkrétní problém, který hlásíte.

2.  Spuštění druhé kopie sady Visual Studio *bez otevřeného řešení*

3.  V nové kopii sady Visual Studio otevřete nástroj **Nahlásit problém.**

4.  Postupujte podle kroků v [how to report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) until you reach the "Provide a trace and halap dump (optional)" step.

5.  Zvolte, zda chcete zaznamenat první kopii sady Visual Studio (ta, která se vyskytuje s problémem s výkonem) a spustit nahrávání.

    -   Aplikace Steps Recorder se zobrazí a začne nahrávat.

    -   **Během nahrávání** proveďte problematickou akci v první kopii sady Visual Studio. Je pro nás obtížné opravit konkrétní problémy s výkonem, pokud se neobjeví v zaznamenaném čase.

    -   Pokud je akce kratší než 30 sekund a lze ji snadno opakovat, opakujte akci, abyste problém dále demonstrovali.

    -   Ve většině případů je stopa 60 sekund dostatečná k prokázání problémů, zejména pokud problematická akce trvala (nebo byla opakována) po dobu delší než 30 sekund. Dobu trvání lze upravit podle potřeby zachytit chování, které chcete opravit.

6.  Klepněte na tlačítko "Stop Record" v záznamech kroků, jakmile je pomalá operace nebo událost vysokého procesoru, kterou chcete nahlásit, dokončena. Zpracování trasování výkonu může trvat několik minut.

7.  Po dokončení bude k vaší zpětné vazbě několik příloh. Připojte další soubory, které mohou pomoci reprodukovat problém (ukázkový projekt, snímky obrazovky, videa atd.).

8.  Odešlete zpětnou vazbu.

Při nahrávání sledování výkonu, pokud pomalé operace nebo vysoké cpu hlásíte skončí, pak okamžitě zastavit nahrávání. Pokud je shromážděno příliš mnoho informací, nejstarší informace se přepíší. Pokud trasování není zastavena brzy (během několika sekund) po zajímavé operace, užitečné trasování data přepsána.

Nepřipojujte přímo sledování výkonu ke stávajícím položkám zpětné vazby na webu Komunity vývojářů. Vyžádání nebo poskytnutí dalších informací je podporovaný pracovní postup ve integrovaném nástroji Sestavy problému sady Visual Studio. Pokud sledování výkonu je nutné k vyřešení předchozí položky zpětné vazby, nastavíme stav položky zpětné vazby na "Potřebujete více informací", na které lze odpovědět stejným způsobem jako nahlášení nového problému. Podrobné pokyny naleznete v [části "Potřebujete více informací"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) v dokumentu nástroje Nahlásit problém.

> [!NOTE] 
> **Nejcennější zpětná vazba:** Pro téměř všechny problémy s pomalostí / vysokým procesorem je nejcennější zpětnou vazbou popis\*na vysoké úrovni, co jste se snažili udělat, spolu s trasování výkonu (.etl.zip), který zachycuje chování během této doby.

**Pokročilé sledování výkonu**

Možnosti shromažďování trasování v nástroji Report-a-problem jsou dostatečné pro většinu scénářů. Ale jsou časy, kdy je potřeba větší kontrolu nad trace kolekce (například trasování s větší velikost vyrovnávací paměti), v takovém případě PerfView je skvělý nástroj pro použití. Kroky pro ruční záznam sledování výkonu pomocí nástroje PerfView lze nalézt na [sledování výkonu nahrávání s PerfView](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) stránky.

## <a name="out-of-process-issues"></a>Problémy mimo proces

> [!NOTE]
> Počínaje Visual Studio 2019 verze 16.3, mimoprocesprotokoly jsou automaticky připojeny ke zpětné vazbě odeslané pomocí nástroje Nahlásit problém. Pokud je však problém přímo reprodukovatelný, následující následující kroky mohou stále pomoci přidat další informace, které pomohou lépe diagnostikovat problém.

Existuje celá řada satelitních procesů, které běží paralelně s Visual Studio a poskytují různé funkce mimo hlavní proces sady Visual Studio. Pokud dojde k chybě v jednom z těchto satelitních procesů je obvykle vidět na straně Visual Studio jako 'StreamJsonRpc.RemoteInvocationException' nebo 'StreamJsonRpc.ConnectionLostException'.

Co dělá tyto typy problémů nejvíce žalovatelné je poskytnout další protokoly, které mohou být shromažďovány pomocí následujících kroků:

1.  Pokud se jedná o přímo reprodukovatelný problém, začněte odstraněním složky **%temp%/servicehub/logs.** Pokud tento problém nemůžete reprodukovat, ponechejte tuto složku beze změny a ignorujte následující odrážky:

    -   Nastavení proměnné globálního prostředí **ServiceHubTraceLevel** na **všechny**
    -   Reprodukujte problém.

2.  Stáhněte si nástroj Microsoft Visual Studio a Nástroj pro shromažďování protokolů rozhraní .NET Framework [zde](https://www.microsoft.com/download/details.aspx?id=12493).
3.  Spusťte nástroj. Tím se vyloží soubor ZIP na **%temp%/vslogs.zip**. Připojte tento soubor ke své zpětné vazbě.

## <a name="see-also"></a>Viz také

* [Možnosti zpětné vazby sady Visual Studio](../ide/feedback-options.md)
* [Nahlášení problému s Visual Studio pro Mac](/visualstudio/mac/report-a-problem)
* [Nahlášení problému s c++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Komunita vývojářů visual studia](https://developercommunity.visualstudio.com/)
* [Ochrana osobních údajů komunity vývojářů](developer-community-privacy.md)
