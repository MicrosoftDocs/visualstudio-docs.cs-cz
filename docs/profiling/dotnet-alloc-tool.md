---
title: Analýza využití paměti pro objekty .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 81c15753b083256b97c9f67219b64565a8db8736
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247800"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Analýza využití paměti pomocí nástroje pro přidělování objektů .NET

Můžete zjistit, kolik paměti vaše aplikace používá a jaké cesty kódu přidělují nejvíc paměti pomocí nástroje pro přidělování objektů .NET.

Po spuštění nástroje můžete zobrazit cesty provádění funkce, kde jsou objekty přidělovány. Pak můžete trasovat zpět do kořenového adresáře stromu volání, který zabírá nejvíc paměti.

## <a name="setup"></a>Nastavení

1. Kliknutím na **ALT + F2** otevřete Profiler výkonu v aplikaci Visual Studio.

1. Zaškrtněte políčko **sledování přidělování objektů .NET** .

   ![Vybraný nástroj pro sledování přidělování objektů dotnet](../profiling/media/dotnetalloctoolselected.png "Vybraný nástroj pro sledování přidělování objektů dotnet")

1. Kliknutím na tlačítko **Spustit** nástroj spustíte.

1. Po spuštění nástroje si Projděte scénář, který chcete profilovat ve své aplikaci. Pak vyberte **Zastavit shromažďování** nebo zavřít aplikaci, aby se zobrazila vaše data.

   ![Okno, v němž je zastaveno shromažďování](../profiling/media/stopcollectionlighttheme.png "Okno, v němž je zastaveno shromažďování")

1. Vyberte kartu **přidělení** . obsah okna podobný následujícímu snímku obrazovky se zobrazí.

   ![Karta přidělení](../profiling/media/allocationview.png "Karta přidělení")

Nyní můžete analyzovat přidělování paměti objektů.

Během shromažďování může nástroj pro sledování zpomalit posouborovou aplikaci. Pokud je výkon nástroje pro sledování nebo aplikace pomalý a pokud nepotřebujete sledovat všechny objekty, můžete upravit vzorkovací frekvenci. Provedete to tak, že na stránce Souhrn profileru vyberete symbol ozubeného kolečka vedle nástroje pro sledování.

![Nastavení pro nástroj pro přidělování dotnet](../profiling/media/dotnetallocsettings.png "Nastavení pro nástroj pro přidělování dotnet")

Nastavte vzorkovací frekvenci na požadovanou sazbu. Tato změna pomáhá zrychlit výkon aplikace během shromažďování a analýzy.

![Upravená vzorkovací frekvence](../profiling/media/adjustedsamplingratedotnetalloctool.png "Upravená vzorkovací frekvence")

Další informace o tom, jak nástroj zvýšit efektivitu, najdete v tématu [optimalizace nastavení profileru](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Pochopení vašich dat

![Graf pro alokační nástroj dotnet](../profiling/media/graphdotnetalloc.png "Graf pro alokační nástroj dotnet")

V předchozím grafickém zobrazení zobrazuje horní graf počet aktivních objektů ve vaší aplikaci. Dolní **objekt rozdílového** grafu ukazuje procentuální změnu objektů aplikace. Červené pruhy označují, že došlo k uvolnění paměti.

![Filtrovaný graf doby přidělení dotnet](../profiling/media/graphdotnetalloctimefiltered.png "Filtrovaný graf doby přidělení dotnet")

Tabulková data můžete filtrovat, chcete-li zobrazit aktivitu pouze pro zadaný časový rozsah. Můžete také zvětšit nebo zmenšit graf.

### <a name="allocation"></a>Přidělování

![Rozšířené zobrazení přidělení](../profiling/media/allocationexpandedlight.png "Rozšířené zobrazení přidělení")

Zobrazení **přidělení** zobrazuje umístění objektů, které přiděluje paměť a kolik paměti tyto objekty přiděluje.

- Sloupec **typ**   je seznam tříd a struktur, které zabírají paměť. Poklikejte na typ pro zobrazení zpětného trasování jako opačného stromu volání. V zobrazení **přidělení** můžete zobrazit položky v rámci vybrané kategorie, které zabírají paměť.

- Sloupec **alokace**   zobrazuje počet objektů, které zabírají paměť v rámci konkrétního typu nebo funkce přidělení. Tento sloupec se zobrazí pouze v zobrazeních **přidělení**, **strom volání**a **funkce**   .

- Sloupce **bajtů**   a **Průměrná velikost (bajty)**   se ve výchozím nastavení nezobrazí. Pokud je chcete zobrazit, klikněte pravým tlačítkem myši na sloupec **typ**   nebo **přidělení**   a potom vyberte možnosti **bajtů**   a **Průměrná velikost (bajty)**,   které chcete přidat do grafu. 

   Tyto dva sloupce se podobají **součtům (přidělení)** a **sobě samým (přidělením)**, s výjimkou toho, že se místo počtu objektů, které zabírají paměť, zobrazuje velikost paměti, která je zavedená. Tyto sloupce se zobrazí pouze v zobrazení **přidělení** .

- Ve sloupci **název modulu**se   zobrazuje modul, který obsahuje funkci nebo proces, který je volán.

Všechny tyto sloupce jsou seřaditelné. Pro sloupce **typ** a **název modulu** můžete seřadit položky abecedně ve vzestupném nebo sestupném pořadí. Pro **přidělení**, **bajty**   a **průměrnou velikost (bajty)** můžete položky seřadit pomocí zvýšení nebo snížení číselné hodnoty.

#### <a name="symbols"></a>Symboly

Na kartách **přidělení**, **strom volání**a **funkce** se zobrazí následující symboly:

- ![Symbol typu hodnoty](../profiling/media/valuetypeicon.png "Symbol typu hodnoty") – typ hodnoty jako celé číslo

- ![Symbol kolekce hodnotových typů](../profiling/media/valuetypecollectionicon.png "Symbol shromažďování hodnot typu hodnoty") – kolekce typu hodnoty, jako je pole celých čísel

- ![Symbol referenčního typu](../profiling/media/referencetypeicon.png "Symbol referenčního typu") – odkazový typ jako řetězec

- ![Symbol kolekce referenčního typu](../profiling/media/referencetypecollectionicon.png "Symbol kolekce typu odkazu") – kolekce typu odkazu, jako je pole řetězců

### <a name="call-tree"></a>Strom volání

![Zobrazení stromu volání](../profiling/media/calltreelight.png "Zobrazení stromu volání")

Zobrazení **stromu volání**   ukazuje cesty provádění funkce, které obsahují objekty, které přiděluje mnoho paměti.

- Sloupec **název funkce**   zobrazuje proces nebo název funkce obsahující objekty, které přidělují paměť. Zobrazení vychází z úrovně uzlu, který kontrolujete.
- Sloupce **celkem (přidělení)** a **Celková velikost (bajty)**   zobrazují počet přidělených objektů a velikost paměti, která je využívána funkcí a všemi jinými funkcemi, které volá.
- Sloupce **samy (alokace)** a **samo Size (bajty)** zobrazují počet přidělených objektů a velikost paměti, kterou používá jedna vybraná funkce nebo typ přidělení.
- Sloupec **Průměrná velikost (bajty)** zobrazuje stejné informace jako v zobrazení **přidělení** .
- Ve sloupci **název modulu**se   zobrazuje modul, který obsahuje funkci nebo proces, který je volán.

   ![Rozbalení kritické cesty](../profiling/media/hotpathlight.png "Rozbalení kritické cesty")

- Tlačítko **Rozbalit cestu k Hotu zvýrazní cestu** spuštění funkce, která obsahuje mnoho objektů, které přiděluje paměť. Algoritmus se spustí na uzlu, který vyberete, a zvýrazní cestu největší alokace a provede vás při šetření.
- Tlačítko **Zobrazit horkou cestu** zobrazí nebo skryje plamenové symboly, které označují, které uzly jsou součástí cesty k Hot.

### <a name="functions"></a>Functions

![Zobrazení funkcí](../profiling/media/functionslight.png "Zobrazení funkcí")

V zobrazení **Functions (funkce** ) se zobrazují procesy, moduly a funkce, které přiděluje paměť.

- Ve sloupci **název** se zobrazí procesy jako uzly nejvyšší úrovně. Pod procesy jsou moduly a pod moduly funkce.
- Tyto sloupce zobrazují stejné informace jako v zobrazeních stromu **přidělení** a **volání** :

  - **Celkem (přidělení)**
  - **Samostatně (přidělení)**
  - **Celková velikost (bajty)**
  - **Velikost sebe (v bajtech)**
  - **Průměrná velikost (bajty)**

### <a name="collection"></a>Kolekce

![Zobrazení kolekce](../profiling/media/collectionlight.png "Zobrazení kolekce")

Zobrazení **kolekce** ukazuje, kolik objektů bylo shromážděno nebo uchováno během uvolňování paměti. Toto zobrazení také ukazuje výsečové grafy k vizualizaci shromážděných a předaných objektů podle typu.

- **Shromážděný** sloupec zobrazuje počet objektů, které byly shromážděny systémem uvolňování paměti.
- Sloupec **, ve kterém** se nachází po spuštění systému uvolňování paměti, zobrazuje počet objektů, které byly zachovány.

### <a name="filtering-tools"></a>Nástroje pro filtrování

Všechny zobrazení **přidělení**, **strom volání**a **funkce** všechny obsahují možnosti **Zobrazit pouze můj kód** a **Zobrazit nativní kód** a pole filtru.

- **Zobrazit pouze můj kód** sbalí systémy, rozhraní a jiný neuživatelský kód do snímků **[External Code]** , abyste se mohli soustředit jenom na váš kód. Další informace naleznete v tématu [ladění uživatelského kódu pomocí pouze můj kód](../debugger/just-my-code.md).
- **Zobrazit nativní kód** zobrazí nativní kód v rámci analytického cíle a může obsahovat neuživatelský kód.
- Pomocí pole Filtr můžete vyfiltrovat sloupec **název** nebo **funkce** na základě hodnoty, kterou zadáte. Do pole zadejte hodnotu řetězce. Tabulka pak zobrazí jenom typy, které obsahují tento řetězec.
