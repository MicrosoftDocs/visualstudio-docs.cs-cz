---
title: Analýza využití paměti pro objekty .NET | Dokumenty společnosti Microsoft
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75898467"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analýza využití paměti pomocí nástroje pro alokaci objektů .NET

Můžete zjistit, kolik paměti vaše aplikace používá a jaké cesty kódu přidělují nejvíce paměti pomocí nástroje pro přidělení objektů .NET.

Po spuštění nástroje, můžete zobrazit cesty spuštění funkce, kde jsou přidělovány objekty, takže můžete trasovat zpět do kořenového adresáře stromu volání, který zabírají největší množství paměti.

## <a name="setup"></a>Nastavení

1. Otevřete profilovač výkonu (**Alt + F2)** v sadě Visual Studio.
2.  Zaškrtněte políčko **Sledování přidělení objektu .NET.**

![Diag Hub](../profiling/media/diaghub.png "Diag Hub")

> [!NOTE]
> Projekt spuštění je vybrán jako **cíl analýzy** ve výchozím nastavení, ale to lze změnit na spuštěný proces, spustitelné soubory, spuštěné aplikace a nainstalované aplikace otevřením rozevírací nabídky **Změnit cíl** a výběrem z dostupných možností.

   Nástroj pro přidělování objektů .NET aktuálně nepodporuje spustitelné soubory prostřednictvím rozevírací nabídky. Budete muset projít exe projektsystém u použití nástroje. Chcete-li to provést, zavřete aktuální řešení **(Řešení****zavření souboru)** -> a potom stiskněte **položku Soubor** -> **Otevřít projekt nebo řešení** -> vyberte soubor EXE.

![Cíl analýzy](../profiling/media/analysistarget.png "Cíl analýzy")

3. Klepnutím na tlačítko **Start** spusťte nástroj.

![Zastavit sběr](../profiling/media/stopcollection.png "Zastavit sběr")

4. Po spuštění nástroje si projděte požadovaný scénář v aplikaci a pak stiskněte **Stop Collection** nebo zavřete aplikaci, abyste viděli data.
5. Klikněte na kartu **Přidělení** a měli byste vidět obrázek podobný tomu, který je uveden níže.

![Přidělování](../profiling/media/allocation.png "Přidělování")

Blahopřejeme! Nyní můžete analyzovat přidělení paměti objektů.

## <a name="understand-your-data"></a>Pochopte svá data

### <a name="collection"></a>Kolekce

![Kolekce](../profiling/media/collection.png "Kolekce")

Zobrazení kolekce umožňuje zobrazit, kolik objektů byly shromážděny během uvolňování paměti a kolik byly zachovány. Toto zobrazení také poskytuje několik výsečových grafů pro vizualizaci shromážděných a přežívajících objektů podle typu.

- Shromážděné **Collected** sloupec zobrazuje počet objektů, které uvolňování shromážděných.
- Sloupec **Survived** zobrazuje počet objektů, které přežily po spuštění systému uvolňování paměti.

### <a name="allocation"></a>Přidělování

![Přidělení bylo rozšířeno.](../profiling/media/allocationexpanded.png "Přidělení bylo rozšířeno.")

Zobrazení přidělení umožňuje zobrazit umístění objektů, které jsou přidělování paměti a kolik paměti tyto objekty jsou přidělování.

- Název **Name** sloupec je seznam různých tříd a struktur, které zabírají paměť. Každá položka ve sloupci je uzel, který lze rozbalit, pokud existují položky v rámci této kategorie zabírají paměť. (Pouze zobrazení**přidělení)**
- **Sloupec Celkem (přidělení)** zobrazuje počet objektů v rámci určitého typu přidělení, které zabírají paměť. **(Přidělení,** **Strom volání**a zobrazení **funkcí)**
- Vlastní **(Přidělení)** sloupec zobrazuje počet objektů v rámci jednotlivé položky, která zabírají paměť. **(Přidělení,** **Strom volání**a zobrazení **funkcí)**
- Všechny tři tyto sloupce jsou seřazeny. V případě sloupce **Název** jsou položky seřazeny abecedně (dopředu nebo dozadu). V **případě součtu** **a vlastního (přidělení)** můžete řadit číselně (stále nebo snižovat).
- Sloupce **Celková velikost (bajty)** a **Vlastní velikost (Bajty)** nejsou ve výchozím nastavení zapnuté. Chcete-li je povolit, klikněte pravým tlačítkem myši na sloupce **Název**, **Celkem** nebo **Vlastní (Přidělení)** a potom klikněte na **možnosti Celková velikost** a **Vlastní velikost** a přidejte je do grafu. Dva sloupce jsou podobné **Total (Allocations)** a **Self (Allocations)** s tím rozdílem, že místo zobrazení počtu objektů zabírajících paměť, zobrazují celkové množství paměti v bajtů, které tyto objekty zabírají. [Pouze zobrazení přidělení]

### <a name="call-tree"></a>Strom volání

![Strom volání](../profiling/media/calltree.png "Strom volání")

Strom **volání** umožňuje zobrazit cesty spuštění funkce, které obsahují objekty, které přidělují velké množství paměti.

- Sloupec **Název funkce** zobrazuje proces nebo název funkce obsahující objekty, které přidělují paměť na základě úrovně uzlu, který kontrolujete.
- Sloupce **Součet** a **Vlastní (Přidělení)** zobrazují stejné informace jako zobrazení **Přidělení.**
- Sloupec **Název modulu** zobrazuje modul, který obsahuje funkci nebo proces, který volá.

![Horká cesta](../profiling/media/hotpath.png "Horká cesta")

- Tlačítko **Rozbalit aktivní cestu** zvýrazní cestu spuštění funkce, která obsahuje velké množství objektů, které přidělují paměť. Algoritmus začíná na uživatelem vybraném uzlu zájmu a zvýrazní cestu většiny přidělení, vedení uživatele v jejich šetření.
- Tlačítko **Zobrazit horkou cestu** zapíná nebo vypíná ikony plamene, které označují, který uzel je součástí horké **cesty**.

### <a name="functions"></a>Funkce

![Functions](../profiling/media/functions.png "Funkce")

Zobrazení **Funkce** zobrazuje procesy, moduly a funkce, které přidělují paměť.

- Sloupec **Název** zobrazuje procesy jako uzly nejvyšší úrovně. Pod procesy jsou moduly a pod moduly jsou funkce.
- Sloupce **Součet** a **Vlastní (Přidělení)** zobrazují stejné informace jako zobrazení **Přidělení.**

Všechny zobrazení **Přidělení**, **Strom volání**a **Funkce** obsahují možnosti Zobrazit pouze **můj kód**, **Zobrazit nativní kód**a **Hledat:**

![Pruh filtrů](../profiling/media/filterbar.png "Pruh filtrů")

- **Zobrazit pouze můj kód** sbalí systémy, architektury a další neuživatelský kód a do rámců **[Externí kód],** takže uživatelský kód může být zaměřen na. Další informace naleznete [v tématu Ladění uživatelského kódu pomocí kódu Jen můj kód](../debugger/just-my-code.md).
- **Zobrazit nativní kód** zobrazuje nativní kód v rámci cíle analýzy, včetně kódu, který není vybrán.
- **Pole Filtr** umožňuje filtrovat sloupec **Název** nebo **Název funkce** na základě zadaný parametr. Jednoduše zadejte do pole a tabulka by měla filtrovat dolů zobrazit pouze typy, které obsahují řetězec k dispozici.
