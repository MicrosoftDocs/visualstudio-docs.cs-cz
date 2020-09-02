---
title: Vlastní nativní události haldy ETW | Microsoft Docs
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb6f906cbfb715d67f6e10ddcecf094bc25821f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62552937"
---
# <a name="custom-native-etw-heap-events"></a>Vlastní nativní události haldy Trasování událostí pro Windows

Visual Studio obsahuje řadu nástrojů pro [profilaci a diagnostiku](../profiling/profiling-feature-tour.md), včetně nativního profileru paměti.  Tento Profiler zavěsí [události ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) od zprostředkovatele haldy a poskytuje analýzu způsobu přidělování a používání paměti.  Ve výchozím nastavení může tento nástroj analyzovat pouze přidělení ze standardní haldy systému Windows a jakékoli přidělení mimo tuto nativní haldu nebude zobrazeno.

Existuje mnoho případů, ve kterých můžete chtít použít vlastní haldu a vyhnout se tak režijním nákladům na standardní haldě.  Například můžete pomocí [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) přidělit velké množství paměti na začátku aplikace nebo hry a potom spravovat vlastní bloky v rámci tohoto seznamu.  V tomto scénáři nástroj profiler paměti uvidí jenom toto počáteční přidělení, a ne vaši vlastní správu provedenou v bloku paměti.  Pomocí vlastního zprostředkovatele ETW pro vlastní nativní haldu však můžete nástroj informovat o všech přiděleních, která provedete mimo standardní haldu.

Například v projektu, jako je například následující, kde `MemoryPool` je vlastní halda, se zobrazí pouze jedno přidělení v haldě systému Windows:

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

Snímek z nástroje [využití paměti](../profiling/memory-usage.md) bez vlastního sledování haldy by zobrazoval jenom jedno přidělení 8192 bajtů a žádné vlastní přidělení neprovádí fond:

![Přidělení haldy Windows](media/heap-example-windows-heap.png)

Provedením následujících kroků můžeme použít stejný nástroj ke sledování usgae paměti v naší vlastní haldě.

## <a name="how-to-use"></a>Způsob použití

Tuto knihovnu lze snadno použít v jazyce C a C++.

1. Zahrnout hlavičku vlastního zprostředkovatele ETW pro vlastní haldu:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Přidejte `__declspec(allocator)` dekoratér do libovolné funkce ve Správci vlastního haldy, která vrací ukazatel na nově přidělenou paměť haldy.  Tento dekoratér umožňuje nástroji správně identifikovat typ vracené paměti.  Příklad:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Tento dekoratér sděluje kompilátoru, že tato funkce je voláním přidělování.  Každé volání funkce vrátí adresu CallSite., velikost instrukcí volání a identifikátor typeId nového objektu na nový `S_HEAPALLOCSITE` symbol.  Po přidělení zásobník volání bude Windows generovat událost ETW s těmito informacemi.  Nástroj Profiler paměti provede zásobník volání hledání zpáteční adresy, která odpovídá `S_HEAPALLOCSITE` symbolu, a informace o typeId v symbolech slouží k zobrazení typu modulu runtime přidělení.
   >
   > V krátkém případě to znamená volání, které `(B*)(A*)MyMalloc(sizeof(B))` se bude zobrazovat v nástroji jako typ `B` , ne `void` nebo `A` .

1. V jazyce C++ vytvořte `VSHeapTracker::CHeapTracker` objekt, který poskytuje název haldy, která se zobrazí v nástroji pro profilaci:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Pokud používáte jazyk C, `OpenHeapTracker` místo toho použijte funkci.  Tato funkce vrátí popisovač, který budete používat při volání jiných sledovacích funkcí:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Při přidělování paměti pomocí vlastní funkce volejte `AllocateEvent` metodu (C++) nebo `VSHeapTrackerAllocateEvent` (C) a předejte ukazatel na paměť a její velikost, aby bylo možné sledovat přidělení:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   nebo

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nezapomeňte označit vlastní funkci přidělování pomocí `__declspec(allocator)` dekoratér popsaného výše.

1. Při navracení paměti pomocí vlastní funkce volejte `DeallocateEvent` funkci (C++) nebo `VSHeapTracerDeallocateEvent` (C) a předejte ukazatel na paměť pro sledování zrušení přidělení:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   nebo:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Při přerozdělení paměti pomocí vlastní funkce volejte `ReallocateEvent` metodu (C++) nebo `VSHeapReallocateEvent` (C), předejte ukazatel na novou paměť, velikost přidělení a ukazatel na starou paměť:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   nebo:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Nakonec, pokud chcete zavřít a vyčistit vlastní sledování haldy v jazyce C++, použijte `CHeapTracker` destruktor, buď ručně, nebo prostřednictvím standardních pravidel oboru, nebo `CloseHeapTracker` funkci v C:

   ```cpp
   delete pHeapTracker;
   ```

   nebo:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Sledování využití paměti
Pomocí tohoto volání se vlastní využití haldy teď dá sledovat pomocí nástroje standardní **využití paměti** v aplikaci Visual Studio.  Další informace o použití tohoto nástroje najdete v dokumentaci k [využití paměti](../profiling/memory-usage.md) . Ujistěte se, že jste povolili profilaci haldy se snímky, jinak se nezobrazí vaše vlastní využití haldy.

![Povolit profilaci haldy](media/heap-enable-heap.png)

Chcete-li zobrazit vlastní sledování haldy, použijte rozevírací seznam **halda** umístěný v pravém horním rohu okna **snímku** a změňte zobrazení z *haldy NT* na vlastní haldu, jak je uvedeno dříve.

![Výběr haldy](media/heap-example-custom-heap.png)

Pomocí výše uvedeného příkladu kódu s `MemoryPool` vytvořením `VSHeapTracker::CHeapTracker` objektu a naší vlastní `allocate` metody nyní voláte metodu. `AllocateEvent` nyní se můžete podívat na výsledek tohoto vlastního přidělení, který ukazuje tři instance celkem 24 bajtů, a to vše typu `Foo` .

Výchozí halda *haldy NT* vypadá stejně jako dříve s přidáním našeho `CHeapTracker` objektu.

![Halda NT s modulem Sledování](media/heap-example-windows-heap.png)

Stejně jako u standardní haldy systému Windows můžete také pomocí tohoto nástroje porovnat snímky a vyhledat nevracení a poškození ve vlastní haldě, které je popsáno v dokumentaci o využití hlavní [paměti](../profiling/memory-usage.md) .

> [!TIP]
> Sada Visual Studio obsahuje také nástroj **využití paměti** v sadě nástrojů pro **profilaci výkonu** , která je povolena v **Debug**  >  Možnosti nabídky**Profiler ladění výkonu** nebo kombinace kláves **ALT** + **F2** .  Tato funkce nezahrnuje sledování haldy a nezobrazí vlastní haldu, jak je popsáno zde.  Tato funkce obsahuje jenom okno **diagnostické nástroje** , které se dá povolit v nabídce **ladit**  >  **Windows**  >  **Zobrazit diagnostické nástroje** nebo kombinaci kláves **CTRL** + **+** + **F2** .

## <a name="see-also"></a>Viz také
[První pohled na nástroje](../profiling/profiling-feature-tour.md) 
 pro profilaci [Využití paměti](../profiling/memory-usage.md)
