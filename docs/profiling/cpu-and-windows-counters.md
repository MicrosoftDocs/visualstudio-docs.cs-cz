---
title: Čítače PROCESORU a Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9accd3d0ab5ff1f7a3084d5973cace08e66396b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779546"
---
# <a name="cpu-and-windows-counters"></a>Čítače procesoru a systému Windows

Visual Studio Profiler umožňuje shromažďovat údaje o výkonu, které byly generovány operačního systému (čítače systému Windows) a údaje o výkonu, které byly generovány procesorové jednotky (čítače procesoru).

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Čítače Systému Windows

Čítače systému Windows jsou součástí diagnostické infrastruktury systému Windows, která poskytuje informace o výkonu operačního systému nebo aplikace, služby nebo ovladače. Čítače systému Windows závisí na konfiguraci aktuálního počítače a nemusí být k dispozici v jiných počítačích. Čítače výkonu systému Windows jsou shromažďovány v datových souborech profilování jako profilovací značky, které pak lze použít k filtrování zobrazení a sestav.

## <a name="cpu-counters"></a>Čítače procesoru

Čítače procesoru jsou funkcí procesoru počítače, které ukládají počet událostí souvisejících s hardwarem. Při shromažďování dat čítače procesoru pomocí metody profilování instrumentace jsou data připojena k datům pro funkce a moduly. Můžete shromažďovat více čítačů procesoru pomocí metody instrumentace. Při použití metody vzorkování vyberete jeden čítač, který se použije jako událost, která má být vzorkována.

Čítače výkonu jsou specifické pro procesor. Různé modely a verze procesoru mohou mít výrazně odlišné nastavení konfigurace, aby bylo možné povolit stejný čítač výkonu. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]Přenosná událost profileru odpojí některé běžné čítače výkonu od konkrétních procesorů a umožňují shromažďovat nebo vzorkovat obecné události výkonu.

Pokud chcete počítat konkrétní událost při použití profileru, například l2 mezipaměti mine, můžete vytvořit relaci výkonu kolem tohoto odesílatele události. Můžete to udělat na libovolném procesoru s mezipamětí L2. Relace výkonu lze přesunout z platformy na platformu bez úprav.

Profilování sady Visual Studio nadále podporuje konkrétní události pro konkrétní platformu. Například vývojář na platformě Pentium 4 může chtít počítat události, které jsou specifické pro architekturu NetBurst. Tato událost není přenosná, ale stále k dispozici pro vývojáře pro konkrétní relaci výkonu na konkrétní platformě.

## <a name="portable-and-platform-events"></a>Přenosné události a události na platformě

Přenosné události jsou skupinou čítačů procesoru, které nejsou specifické pro konkrétní procesor. Všechny ostatní čítače procesoru se nazývají události platformy a nemusí být podporovány na různých platformách.

 Čítače pro přenosnou událost i události platformy jsou definovány v . *xml,* kde jsou k dispozici specifické hodnoty, které souvisejí s čítači. Existuje více souborů pro různé procesory, protože data pro procesory Intel a AMD se například liší. Profiler [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] používá tyto informace k prezentaci vhodných čítačů, přenosných i platformních, pro uživatele pro měření výkonu.

### <a name="portable-events"></a>Přenosné události

Přenosné události obsahují následující události:

**Obecné události**

|Název události|Popis události|
|----------------|-----------------------|
|Instrukce v důchodu|Označuje počet instrukcí, které byly provedeny, dokud není událost dokončena.|
|Nezastavené cykly|Označuje pouze ty cykly, ve kterých procesor není zastaven, například čekání na vstupně-v.|

**Události front-endu**

|Název události|Popis události|
|----------------|-----------------------|
|ITLB mine|Označuje počet vyhledávání hledejte-stranou vyhledávání překladu, který vyústil v chybě.|

**Události pobočky**

|Název události|Popis události|
|----------------|-----------------------|
|Pobočky v důchodu|Označuje počet pokynů větve provedených do dokončení události.|
|Špatně předpovídané větve|Označuje chybně předpovídané větve, ke kterým dochází, protože procesor předpověděl nesprávnou cestu. Nesprávně předpovídané větve ovlivňují výkon, protože procesor musí zahodit veškerou provedenou práci a znovu začít na správné cestě.|

**Události paměti:**

|Název události|Popis události|
|----------------|-----------------------|
|Počet neúspěšných čtení mezipaměti L2|Označuje počet neúspěšných pokusů o čtení mezipaměť druhé úrovně.|
|Odkazy na čtení mezipaměti L2|Označuje počet odkazů na čtení mezipaměti druhé úrovně. Zahrnuje nepřístupy k zatížení a čtení pro vlastnictví (RFO) nepřístupných přístupů a přístupů.|

## <a name="view-available-counters"></a>Zobrazit dostupné čítače

Můžete seznam dostupných čítačů procesoru v ide sady Visual Studio v okně příkazového řádku.

### <a name="visual-studio-ui"></a>UI visual studia

Chcete-li vypsat dostupné čítače v počítači v rozhraní IDE sady Visual Studio, musíte mít otevřenou relaci výkonu profileru v Průzkumníku výkonu.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Zobrazení seznamu všech čítačů procesoru, které jsou podporovány na aktuální platformě

1. V Průzkumníku výkonu klikněte pravým tlačítkem myši na relaci výkonu a potom klikněte na **příkaz Vlastnosti**.

2. Proveďte jednu z těchto akcí:

   - Klepněte na **položku Vzorkování**a potom v seznamu **ukázkových** událostí vyberte **čítač Výkon.** Čítače procesoru jsou uvedeny v **seznamu Dostupné čítače výkonu**.

      **Poznámka:** Klepnutím na tlačítko **Storno** se vrátíte k předchozí konfiguraci vzorkování.

     -nebo-

   - Vyberte **čítače procesoru**a pak vyberte **Shromáždit čítače procesoru**. Čítače procesoru jsou uvedeny v **seznamu Dostupné čítače**.

      **Poznámka:** Klepnutím na tlačítko **Storno** se vrátíte k předchozí konfiguraci kolekce čítačů.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Zobrazení seznamu čítačů oken, které jsou podporovány na aktuální platformě

1. V Průzkumníku výkonu klikněte pravým tlačítkem myši na relaci výkonu a potom klikněte na **příkaz Vlastnosti**.

2. Klepněte na **položku Čítače systému Windows**.

3. Vyberte **možnost Shromáždit čítače systému Windows**.

4. Ze seznamu **Kategorie čítače** vyberte skupinu čítačů. Čítač systému Windows pro skupinu se zobrazí v seznamu.

     **Poznámka:** Klepnutím na tlačítko **Storno** se vrátíte k předchozí konfiguraci kolekce čítačů.

### <a name="command-line"></a>Příkazový řádek

Pomocí nástroje příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) můžete z příkazového řádku uvést čítače procesoru, které jsou k dispozici v počítači.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Seznam čítačů procesoru, které jsou podporovány na aktuální platformě

1. Otevřete okno příkazového řádku.

2. Typ

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd /querycounters**

     kde * \<visual studio performance tools directory>* je cesta k adresáři Nástroje pro výkon instalace sady Visual Studio. Chcete-li získat cestu k nástrojům výkonu, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md)
[Jak: Zvolte vzorkovací události:](../profiling/how-to-choose-sampling-events.md)
Shromažďovat data
[čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)[Postup: Shromažďování dat čítačů systému Windows](../profiling/how-to-collect-windows-counter-data.md)
