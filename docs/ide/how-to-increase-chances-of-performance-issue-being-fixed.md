---
title: Jak můžete zvýšit pravděpodobnost vyřešeného problému s výkonem
description: Další informace a osvědčené postupy pro odesílání problémů s výkonem v aplikaci Visual Studio
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: d61e7f47fde06c12b6b133ced76e5a8d72d220b0
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74528432"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Jak zvýšit pravděpodobnost vyřešeného problému s výkonem

Nástroj "[nahlásit problém](https://aka.ms/vs-rap)" se v aplikaci Visual Studio často používá k hlášení rozsahu problémů. Tým sady Visual Studio se zaměřuje na chyby a zpomalení v důsledku zpětné vazby uživatelů a řeší problémy, které mají vliv na širokou škálu uživatelů Swath. Dalším možným lístkem zpětné vazby je, tím pravděpodobněji bude diagnostikována a rychlejší vyřešena produktovým týmem. V tomto dokumentu jsou popsány osvědčené postupy při oznamování chyb nebo zpomalení, aby bylo možné je lépe dělat.

## <a name="general-best-practices"></a>Obecné osvědčené postupy

Visual Studio je velká, složitá platforma, která podporuje spoustu jazyků, typů projektů, platforem a dalších. Jak je to provedeno, je funkce, která je nainstalována a aktivní v relaci, nainstalovaná rozšíření, nastavení aplikace Visual Studio, konfigurace počítače a nakonec tvar kódu, který je upravován. Vzhledem k počtu proměnných je obtížné zjistit, zda má sestava problému od jednoho uživatele stejný základní problém jako hlášení problému od jiného uživatele, a to i v případě, že viditelný příznak je stejný. Vzhledem k tomu, že zde jsou některé osvědčené postupy, abyste měli jistotu, že vaše konkrétní zpráva o problému má vyšší pravděpodobnost diagnostikovat.

**Zadejte podle potřeby název, který je možné použít**

Vyhledejte jedinečné signatury zjištěného problému a v nadpisu uveďte co nejvíce. Pokud je Nadpis popisný, je méně pravděpodobný, že uživatelé s nesouvisejícími problémy (ale stejný povrchový příznak) budou hlasovat nebo *komentovat svůj lístek* , takže by tím bylo obtížnější diagnostiku problému.

**V případě nejistých chyb Zaprotokolujte novou zprávu o problému.**

Mnohé problémy nemusí mít k dispozici žádný rozlišující podpis ani kroky pro reprodukování. V takových případech je nová sestava lepší než při hlasování nebo komentář k jiné sestavě, která hlásí podobný vnější *příznak*. V závislosti na typu sestavy zahrňte do sestavy další diagnostické soubory, jak je popsáno dále v tomto dokumentu.

**Osvědčené postupy specifické pro problém**

Popsané níže jsou problémy, které je obtížné diagnostikovat bez dobrých diagnostických souborů. Po určení případu, který nejlépe popisuje váš problém, postupujte podle kroků pro zpětnou vazbu, které jsou specifické pro tento případ.

-   [Selhání:](#crashes) Dojde k chybě při neočekávaném ukončení procesu (Visual Studio).

-   [Nereagující rychlost:](#unresponsiveness) VS přestane po delší dobu reagovat.

-   [Problémy s pomalým výkonem:](#slowness-and-high-cpu-issues) Všechny konkrétní akce v VS jsou pomalejší než požadované

-   [Vysoký procesor:](#slowness-and-high-cpu-issues) Rozšířená období neočekávaného vysokého využití procesoru

## <a name="crashes"></a>Chybě
Dojde k chybě při neočekávaném ukončení procesu (Visual Studio).

**Přímo reprodukovatelná selhání**

Přímo reprodukovatelná selhání jsou případy, které mají následující vlastnosti:

- Může být pozorována podle známé sady kroků

- Může být pozorováno na více počítačích (Pokud je k dispozici)

- Může být reprodukována v ukázkovém kódu nebo projektu, který lze propojit nebo poskytnout jako součást zpětné vazby (Pokud postup zahrnuje otevření projektu nebo dokumentu)

V případě těchto potíží postupujte podle kroků v části[Jak nahlásit problém](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)a nezapomeňte zahrnout:

-   Kroky pro reprodukování problému

-   Samostatný projekt reprodukci, jak je popsáno výše. Pokud není možné samostatně reprodukci, uveďte prosím:

    -   Jazyk otevřených projektů (C\#, C++atd.)

    -   Druh projektu (Konzolová aplikace, ASP.NET atd.)


> [!NOTE]
> Nejužitečnější **Váš názor:** V tomto případě je nejužitečnější zpětná vazba sada kroků pro reprodukování problému spolu s ukázkovým zdrojovým kódem.

**Neznámá selhání**

Pokud si nejste jistí, co způsobuje vaše havárie nebo jsou náhodná, můžete zachytit výpisy v místním počítači pokaždé, když dojde k selhání sady Visual Studio, a připojit je k oddělení položek zpětné vazby. Pokud chcete uložit výpisy do místní paměti při zhroucení sady Visual Studio, spusťte následující příkazy v okně příkazu Správce:

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

Podle potřeby upravte počet výpisů a složku s výpisem paměti. Další informace o těchto nastaveních najdete [tady](https://docs.microsoft.com/windows/win32/wer/collecting-user-mode-dumps?redirectedfrom=MSDN).

> [!NOTE]
> Výpisy zachycené pomocí Správce úloh mají pravděpodobně nesprávný bitová verze, což snižuje jejich použitelnost. Postup, který je popsaný výše, je upřednostňovaným způsobem, jak zachytit výpis haldy. Pokud chcete použít Správce úloh, zavřete ten, který je právě spuštěný, spusťte 32bitový Správce úloh (% windir%\\syswow64\\volby Správce úloh. exe) a z něj Shromážděte výpisy haldy.

> [!NOTE] 
> Každý soubor s výpisem paměti vytvořený touto metodou bude mít velikost až 4 GB. Nezapomeňte nastavit DumpFolder na umístění s odpovídajícím prostorem na disku nebo upravit DumpCount správně.

Pokaždé, když Visual Studio selže, vytvoří soubor s výpisem stavu **devenv. exe. [ Number] soubor dmp** v nakonfigurovaném umístění.

Pak použijte Visual Studio "nahlásit problém..." zapnut. Umožní vám připojit příslušný výpis paměti.

1.  Vyhledejte soubor s výpisem paměti pro chybu, kterou vytváříte (vyhledejte soubor se správným časem vytvoření).

2.  Pokud je to možné, před odesláním zpětné vazby soubor zip (\*. zip) zmenšete jeho velikost.

3.  Postupujte podle kroků v části[Jak nahlásit problém](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)a připojit výpis haldy k nové položce zpětné vazby.

> [!NOTE] 
> Nejužitečnější **Váš názor:** V tomto případě je nejužitečnou zpětnou vazbou výpis paměti zachycený v době selhání.

## <a name="unresponsiveness"></a>Zablokování
VS přestane po delší dobu reagovat.

**Přímá rereprodukovatelná odezva**

Jak je popsáno v odpovídající části týkající se havárií, pro problémy, které je možné snadno reprodukovat, vidět na více počítačích a které je možné považovat za drobný vzorek, jsou nejužitečnější sestavy zpětné vazby, které obsahují kroky pro reprodukci problému a zahrnují Ukázkový zdrojový kód, který demonstruje problém.

**Neznámá neodezva**

Pokud je nereagující manifest sám nepředvídatelným způsobem, spusťte na dalším výskytu novou instanci sady Visual Studio a nahlaste problém z této instance.
Na [obrazovce Record (záznam)](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)nezapomeňte vybrat relaci sady Visual Studio, která se přestala reagovat.

Pokud byla instance sady Visual Studio, která se přestala reagovat, spuštěna v režimu správce, pak by se druhá instance musela spustit také v režimu správce.

>[!NOTE] 
> Nejužitečnější **Váš názor:** V tomto případě je nejužitečnou zpětnou vazbou výpis paměti zachycený v době nereagující.

## <a name="slowness-and-high-cpu-issues"></a>Zpomalení a vysoké problémy s PROCESORem

Díky tomu, že dochází k potížím s zpomalení nebo vysokým využitím procesoru, je trasování výkonu zaznamenané, zatímco probíhá pomalá operace nebo vysoká událost procesoru.

>[!NOTE] 
> Pokud je to možné, izolujte každý scénář v samostatné konkrétní sestavě zpětné vazby.
Pokud je například psaní a navigace pomalé, postupujte podle následujících kroků na základě problému. Díky tomu může produktový tým izolovat příčinu konkrétních problémů.

Nejlepších výsledků při zaznamenávání výkonu získáte pomocí následujících kroků:

1.  Pokud ještě není spuštěný, máte k dispozici kopii sady Visual Studio, kde bude problém reprodukován.

    -   Máte všechno nastavené pro reprodukování problému. Pokud například potřebujete, aby určitý projekt byl načten se specifickým otevřeným souborem, ujistěte se, že oba tyto kroky byly dokončeny, než budete pokračovat.

    -   Pokud neoznamujete problém, *který je specifický* pro načtení řešení, zkuste počkat 5-10 minut (nebo více, v závislosti na velikosti řešení) po otevření řešení před zavedením trasování výkonu. Proces načtení řešení vytvoří velké množství dat, takže čekání na několik minut nám pomůže soustředit se na konkrétní problém, který vytváříte.

2.  Spustit druhou kopii sady Visual Studio *bez otevřeného řešení*

3.  V nové kopii sady Visual Studio otevřete nástroj **nahlásit problém** .

4.  Postupujte podle kroků v tématu [postup nahlášení problému](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) , dokud nedosáhnete kroku "poskytnutí trasování a výpis paměti haldy (volitelné)".

5.  Vyberte, chcete-li zaznamenat první kopii sady Visual Studio (u kterých došlo k potížím s výkonem) a spusťte záznam.

    -   Zobrazí se aplikace záznam postupu a začne se nahrávat.

    -   **Během nahrávání** proveďte problematickou akci v první kopii sady Visual Studio. Je nám obtížné opravit konkrétní problémy s výkonem, pokud se neobjeví v zaznamenaném čase.

    -   Pokud je akce kratší než 30 sekund a lze ji snadno opakovat, opakujte akci, abyste mohli problém dále prověřit.

    -   Ve většině případů je trasování 60 sekund dostačující k předvedení problémů, zejména v případě, že problematická akce byla naposled (nebo byla opakována) po dobu delší než 30 sekund. Dobu trvání lze upravit podle potřeby pro zachycení chování, které chcete opravit.

6.  Po dokončení operace pomalé nebo vysoké události procesoru, kterou chcete ohlásit, klikněte na tlačítko Zastavit záznam v záznamu postupu. Zpracování trasování výkonu může trvat několik minut.

7.  Po dokončení bude vaše zpětná vazba obsahovat několik příloh. Připojte všechny další soubory, které mohou přispět k reprodukování problému (ukázkový projekt, snímky obrazovky, videa atd.).

8.  Odešlete zpětnou vazbu.

Při nahrávání trasování výkonu se v případě, že pomalá operace nebo vysoký procesor, který vytváříte, stane na konci, a poté záznam ihned zastaví. Pokud je shromažďováno příliš mnoho informací, nejstarší informace budou přepsány. Pokud trasování není po zajímavé operaci brzy zastaveno (během několika sekund), užitečná data trasování se přepíší.

Nepřipojujte přímo trasování výkonu k existujícím položkám zpětné vazby na webu komunity pro vývojáře. Vyžádání nebo poskytnutí dalších informací je podporovaný pracovní postup v integrovaném nastavování nástroje pro problémy se sestavou sestav sady Visual Studio. Pokud se vyžaduje trasování výkonu, aby bylo možné vyřešit předchozí položku zpětné vazby, nastavíme stav položky zpětné vazby na "Potřebujeme další informace", na kterou lze reagovat stejným způsobem jako nahlášení nového problému. Podrobné pokyny najdete v [části "potřebné informace"](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) v dokumentu nástroje pro nahlášení problému.

> [!NOTE] 
> Nejužitečnější **Váš názor:** Pro téměř všechny problémy s pomalými a vysokými nároky na procesor je nejužitečnější popis toho, co jste se snažili udělat, spolu s trasováním výkonu (\*. ETL. zip), které během této doby zachycuje chování.

**Rozšířené trasování výkonu**

Ve většině scénářů jsou pro většinu scénářů dostačující možnosti shromažďování dat v nástroji Report-a-problém. Existují však situace, kdy je zapotřebí větší kontrola shromažďování trasování (například trasování s větší vyrovnávací pamětí), v takovém případě PerfView je skvělý nástroj k použití. Postup ručního zaznamenávání trasování výkonu pomocí nástroje PerfView najdete na stránce [nahrávání trasování výkonu se](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) stránkou PerfView.

## <a name="see-also"></a>Viz také:

* [Možnosti zpětné vazby v aplikaci Visual Studio](../ide/feedback-options.md)
* [Nahlášení problému s Visual Studio pro Mac](/visualstudio/mac/report-a-problem)
* [Nahlásit problém sC++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Komunita vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/)
* [Soukromí dat komunity vývojářů](developer-community-privacy.md)
