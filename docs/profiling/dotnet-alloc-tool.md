---
title: Analýza využití paměti pro objekty .NET | Microsoft Docs
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
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75898467"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analýza využití paměti pomocí nástroje pro přidělování objektů .NET

Můžete zjistit, kolik paměti vaše aplikace používá a jaké cesty kódu přidělují nejvíc paměti pomocí nástroje pro přidělování objektů .NET.

Po spuštění nástroje můžete zobrazit cesty provádění funkce, kde jsou objekty přiděleny, abyste mohli trasovat zpět do kořenového adresáře stromu volání, který zabírá nejvíc paměti.

## <a name="setup"></a>Instalace

1. Otevřete Profiler výkonu (**ALT + F2)** v aplikaci Visual Studio.
2.  Zaškrtněte políčko **sledování přidělování objektů .NET** .

![Centrum diagnostiky](../profiling/media/diaghub.png "Centrum diagnostiky")

> [!NOTE]
> Ve výchozím nastavení je vybrán projekt po spuštění jako **cíl analýzy** , ale lze jej změnit na běžící proces, spustitelné soubory, spuštěné aplikace a nainstalované aplikace otevřením rozevírací nabídky **změnit cíl** a následným výběrem z dostupných možností.

   Nástroj pro přidělování objektů .NET v současné době nepodporuje spustitelné soubory prostřednictvím rozevírací nabídky. K použití tohoto nástroje budete muset projít systémem projektu exe. Pokud to chcete provést, zavřete aktuální řešení (**soubor** -> **Zavřít řešení**) a potom stiskněte **soubor** -> **otevřete projekt nebo řešení** – > vyberte soubor. exe.

![Cíl analýzy](../profiling/media/analysistarget.png "Cíl analýzy")

3. Kliknutím na tlačítko **Spustit** nástroj spustíte.

![Zastavit shromažďování](../profiling/media/stopcollection.png "Zastavit shromažďování")

4. Jakmile se nástroj spustí, Projděte si požadovaný scénář ve vaší aplikaci a potom stisknutím tlačítka **Zastavit shromažďování** nebo zavřením aplikace zobrazte data.
5. Klikněte na kartu **přidělení** a měli byste vidět obrázek podobný tomu, který vidíte níže.

![Vyhrazen](../profiling/media/allocation.png "přidělení")

Gratulujeme. Nyní můžete analyzovat přidělování paměti objektů.

## <a name="understand-your-data"></a>Pochopení vašich dat

### <a name="collection"></a>Shromažďování

![Kolekce](../profiling/media/collection.png "Shromažďování")

Zobrazení kolekce umožňuje zobrazit, kolik objektů bylo shromážděno během uvolňování paměti a kolik bylo zachováno. Toto zobrazení také poskytuje několik výsečových grafů k vizualizaci shromážděných a předaných objektů podle typu.

- **Shromážděný** sloupec zobrazuje počet objektů, které byly shromážděny systémem uvolňování paměti.
- Sloupec **, ve kterém** se nachází po spuštění systému uvolňování paměti, zobrazuje počet objektů, které byly zachovány.

### <a name="allocation"></a>přidělení

![Rozšířené přidělení](../profiling/media/allocationexpanded.png "Rozšířené přidělení")

Zobrazení přidělení umožňuje zobrazit umístění objektů, které přiděluje paměť a kolik paměti tyto objekty přiděluje.

- Sloupec **název** je seznam různých tříd a struktur, které zabírají paměť. Každá položka v rámci sloupce je uzel, který lze rozbalit, pokud položky v této kategorii zabírají paměť. (Jenom zobrazení**přidělení** )
- Sloupec **celkem (přidělení)** zobrazuje počet objektů v rámci určitého typu přidělení, které zabírají paměť. (Zobrazení**přidělení**, **strom volání**a **funkce** )
- Sloupec **vlastní (přidělení)** zobrazuje počet objektů v rámci jednotlivé položky, které zabírají paměť. (Zobrazení**přidělení**, **strom volání**a **funkce** )
- Všechny tři tyto sloupce jsou seřaditelné. V případě sloupce **název** se položky seřadí abecedně (dopředu nebo zpětně). Pro **celkovou** a **samostatnou (přidělení)** můžete seřadit číselně (buď stále, nebo klesající).
- Sloupce **Celková velikost (bajty)** a **samo Size (bajty)** nejsou ve výchozím nastavení zapnuté. Pokud je chcete povolit, klikněte pravým tlačítkem na sloupce **název**, **Celkový** nebo **samo (přidělení)** a pak je přidejte do grafu kliknutím na možnost **Celková velikost** a **Velikost** . Tyto dva sloupce se podobají **součtům (přidělení)** a **sobě samým (přidělením)** s tím rozdílem, že místo zobrazení počtu objektů, které vycházejí z paměti, zobrazuje celkové množství paměti v bajtech, které tyto objekty zabírají. [Jenom zobrazení přidělení]

### <a name="call-tree"></a>Strom volání

![Strom volání](../profiling/media/calltree.png "Strom volání")

Zobrazení **stromu volání** umožňuje zobrazit cesty spuštění funkce obsahující objekty, které přiděluje mnoho paměti.

- Sloupec **název funkce** zobrazuje proces nebo název funkce obsahující objekty, které přiděluje paměť na základě úrovně uzlu, který kontrolujete.
- Sloupce **celkem** a **samo (přidělení)** zobrazují stejné informace jako zobrazení **přidělení** .
- Ve sloupci **název modulu** se zobrazuje modul, který obsahuje funkci nebo proces, který je volán.

![Kritická cesta](../profiling/media/hotpath.png "Kritická cesta")

- Tlačítko **Rozbalit cestu k Hotu zvýrazní cestu** spuštění funkce, která obsahuje velký počet objektů, které přiděluje paměť. Algoritmus začíná uživatelem vybraným uzlem zájmu a zvýrazňuje cestu s největším přidělením a provede při jejich vyšetřování identifikátor GUID uživatele.
- Tlačítko **Zobrazit horkou cestu** přepíná nebo vypíná ikony plamene, které označují, který uzel je součástí kritické **cesty**.

### <a name="functions"></a>Funkce

![Funkce](../profiling/media/functions.png "Funkce")

V zobrazení **Functions (funkce** ) se zobrazují procesy, moduly a funkce, které přiděluje paměť.

- Ve sloupci **název** se zobrazí procesy jako uzly nejvyšší úrovně. Pod procesy jsou moduly a v části moduly jsou funkce.
- Sloupce **celkem** a **samo (přidělení)** zobrazují stejné informace jako zobrazení **přidělení** .

Všechny zobrazení **přidělení**, **strom volání**a **funkce** všechny obsahují možnosti **Zobrazit pouze můj kód**, **Zobrazit nativní kód**a možnosti **hledání** :

![Panel filtru](../profiling/media/filterbar.png "Panel filtru")

- **Zobrazit pouze můj kód** sbalí systémy, rozhraní a další neuživatelský kód a do **[externí kód]** snímky, aby bylo možné zaměřit uživatelský kód na. Další informace naleznete v tématu [ladění uživatelského kódu pomocí pouze můj kód](../debugger/just-my-code.md).
- **Zobrazit nativní kód** zobrazí nativní kód v rámci analytického cíle včetně neuživatelského kódu, je-li vybrán.
- **Pole Filtr** vám umožňuje vyfiltrovat sloupec název nebo název **funkce** **na základě** parametru, který zadáte. Stačí zadat v poli a tabulka by měla vyfiltrovat, aby se zobrazily jenom typy, které obsahují poskytnutý řetězec.
