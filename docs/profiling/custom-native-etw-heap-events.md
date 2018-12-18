---
title: Trasování událostí pro Windows vlastní nativní události haldy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 98fc473a9459aa6d1a1d7c10be7b6f240a4ab7d0
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744987"
---
# <a name="custom-native-etw-heap-events"></a>Vlastní nativní události haldy Trasování událostí pro Windows

Visual Studio obsahuje řadu [profilování a diagnostické nástroje](../profiling/profiling-feature-tour.md), včetně nativní paměť profileru.  Tento profiler zavěšení [události trasování událostí pro Windows](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) od poskytovatele haldy a poskytuje analýzu toho, jak je že paměti přidělovány a využívány.  Ve výchozím nastavení tento nástroj může analyzovat jenom přidělení provedených od standardní haldy Windows a rozdělení mimo tuto nativní haldě nezobrazí.

Existuje mnoho případy, ve kterých můžete chtít použít vlastní vlastní haldy a vyhnout se nároky na přidělení ze standardní haldy.  Například můžete použít [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) alokace velké množství paměti při spuštění této aplikace nebo hry, a potom spravovat vlastní bloky v tomto seznamu.  V tomto scénáři zobrazoval pouze nástroj profiler paměti tohoto počáteční přidělení a ne vlastní správu provést uvnitř bloku paměti.  Nicméně pomocí zprostředkovatele vlastní nativní haldy trasování událostí pro Windows, můžete nechat nástroj vědět o rozdělení, které provádíte mimo standardní haldy.

Například v projektu takto kde `MemoryPool` je vlastní haldy jednu alokovanou byste měli jenom v haldě Windows:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Snímek ze [využití paměti](../profiling/memory-usage.md) nástroj bez vlastního haldy sledování by zobrazil pouze jeden bajt 8192 přidělení a žádné vlastní přidělení prováděné ve fondu:

![Přidělení haldy. Windows](media/heap-example-windows-heap.png)

Provedením následujících kroků jsme můžete použít stejný nástroj ke sledování usgae paměti v haldě naši vlastní.

## <a name="how-to-use"></a>Jak používat

Tuto knihovnu je možné snadno v jazyce C a C++.

1. Zahrnout hlavičku pro vlastní haldy zprostředkovatele trasování událostí pro Windows:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Přidat `__declspec(allocator)` dekoratéru pro všechny funkce v správce hald, který vrací ukazatel na nově přidělenou haldy paměti.  Tohoto dekoratéru umožňuje nástroji pro zajištění správné identifikace typu paměti se vrací.  Příklad:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > Tohoto dekoratéru oznamuje kompilátoru, že tato funkce je volání alokátoru.  Každé volání funkce se výstupní adresy callsite, velikost instrukcí volání a ID typu nového objektu do nového `S_HEAPALLOCSITE` symbol.  Při přidělení zásobník volání Windows bude generovat události trasování událostí pro Windows pomocí těchto informací.  Nástroj profiler paměti vás zásobník volání, hledá odpovídající návratovou adresu `S_HEAPALLOCSITE` symbolů a typeId informace v symbolu se používá k zobrazení běhového typu přidělení.
   >
   > Stručně řečeno, to znamená, že volání, která vypadá jako `(B*)(A*)MyMalloc(sizeof(B))` se zobrazí v nástroji jako typ `B`, nikoli `void` nebo `A`.

1. Pro C++, vytvořte `VSHeapTracker::CHeapTracker` objekt poskytnutí názvu pro haldu, která se zobrazí v nástroji pro profilování:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Pokud používáte C, použijte `OpenHeapTracker` namísto toho funkci.  Tato funkce vrátí popisovač, který budete používat při volání další funkce sledování:
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Při přidělování paměti používá vaši vlastní funkci zavolat `AllocateEvent` (C++) nebo `VSHeapTrackerAllocateEvent` (C) metodu ukazatel na paměť a jejich velikost, ke sledování přidělení paměti:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   or

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nezapomeňte k označení funkce vlastního alokátoru s `__declspec(allocator)` dekoratér popsané výše.

1. Při rušení přidělení paměti pomocí svoji funkci, zavolejte `DeallocateEvent` (C++) nebo `VSHeapTracerDeallocateEvent` – funkce (C), předávání v ukazateli na paměti, ke sledování navracení zpět:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   nebo:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Při opětovném přidělování paměti pomocí svoji funkci, zavolejte `ReallocateEvent` (C++) nebo `VSHeapReallocateEvent` (C) metodu ukazatel na nové paměti, velikost rozdělení a ukazatel na staré paměti:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   nebo:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. A konečně, zavřete a vyčištění sledování vlastní haldy v jazyce C++, použijte `CHeapTracker` destruktor, ručně nebo prostřednictvím standardních pravidel oboru, nebo `CloseHeapTracker` funkce v C:

   ```cpp
   delete pHeapTracker;
   ```

   nebo:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Sledovat využití paměti
Pomocí těchto volání na místě využití vlastních haldy lze nyní sledovat pomocí standardní **využití paměti** nástroje v sadě Visual Studio.  Další informace o tom, jak tento nástroj použít, najdete v tématu [využití paměti](../profiling/memory-usage.md) dokumentaci. Zkontrolujte, jestli že je povolená profilace haldy pomocí snímků, jinak se nezobrazí využití vlastních haldy, zobrazí. 

![Povolit profilaci haldy](media/heap-enable-heap.png)

Chcete-li zobrazit váš vlastní haldy sledování, použijte **haldy** rozevírací seznam umístěný v pravém horním rohu **snímku** oknu změnit zobrazení z *halda NT* vlastní haldy jako s názvem dříve.

![Výběr haldy](media/heap-example-custom-heap.png)

Pomocí výše uvedeného příkladu kódu s `MemoryPool` vytváření `VSHeapTracker::CHeapTracker` objektu a na našem vlastním `allocate` teď volá metodu `AllocateEvent` metodu, zobrazí se výsledek tohoto vlastního přidělení zobrazující tři instance součet 24 bajtů, všechny typ `Foo`.

Výchozí hodnota *halda NT* haldy vypadá a to stejně jako dříve, a uveďte naše `CHeapTracker` objektu.

![Halda NT sledovací modul](media/heap-example-windows-heap.png)

I s standardní haldou Windows můžete také použít tento nástroj můžete porovnat snímky a vyhledejte nevracení a poškozením v důsledku vlastních haldy, která je popsána v hlavním [využití paměti](../profiling/memory-usage.md) dokumentaci.

> [!TIP]
> Visual Studio obsahuje taky **využití paměti** nástroj v **profilaci výkonu** sadu nástrojů, který je povolený z **ladění**  >   **Profiler výkonu** klikněte na možnost nebo **Alt**+**F2** klávesové kombinace.  Tato funkce neobsahuje haldy sledování a nebudou zobrazovat vlastní haldy, jak je popsáno zde.  Pouze **diagnostické nástroje** okno, které můžete povolit **ladění** > **Windows** > **zobrazit diagnostické nástroje**  nabídky, nebo **Ctrl**+**Alt**+**F2** klávesové kombinace, obsahuje tato funkce.

## <a name="see-also"></a>Viz také:
[Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)  
[Využití paměti](../profiling/memory-usage.md)
