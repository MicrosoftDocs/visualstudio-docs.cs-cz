---
title: Vlastní nativní události haldy ETW | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552937"
---
# <a name="custom-native-etw-heap-events"></a>Vlastní nativní události haldy Trasování událostí pro Windows

Visual Studio obsahuje celou řadu [profilování a diagnostické nástroje](../profiling/profiling-feature-tour.md), včetně nativní paměti profiler.  Tento profiler zavěsí [události ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) od zprostředkovatele haldy a poskytuje analýzu, jak je paměť přidělována a používána.  Ve výchozím nastavení může tento nástroj analyzovat pouze přidělení provedená ze standardní haldy systému Windows a žádná přidělení mimo tuto nativní haldu nebudou zobrazena.

Existuje mnoho případů, ve kterých můžete chtít použít vlastní haldy a vyhnout se režie přidělení ze standardní haldy.  Například můžete použít [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) přidělit velké množství paměti na začátku aplikace nebo hry a pak spravovat své vlastní bloky v rámci tohoto seznamu.  V tomto scénáři nástroj profiler paměti by vidět pouze, že počáteční přidělení a nikoli vlastní správu provedenou uvnitř bloku paměti.  Však pomocí vlastní nativní haldy ETW zprostředkovatele, můžete nechat nástroj vědět o všech přidělení, které provádíte mimo standardní haldy.

Například v projektu, jako `MemoryPool` je následující, kde je vlastní haldy, uvidíte pouze jedno přidělení na haldě systému Windows:

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

Snímek z nástroje [využití paměti](../profiling/memory-usage.md) bez vlastního sledování haldy by se zobrazoval pouze jeden 8192 bajt přidělení a žádné vlastní přidělení provádí fondu:

![Přidělení haldy systému Windows](media/heap-example-windows-heap.png)

Provedením následujících kroků, můžeme použít stejný nástroj ke sledování paměti usgae v naší vlastní haldy.

## <a name="how-to-use"></a>Způsob použití

Tuto knihovnu lze snadno použít v jazycích C a C++.

1. Zahrňte záhlaví pro vlastního zprostředkovatele haldy ETW:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Přidejte `__declspec(allocator)` decorator do libovolné funkce ve vašem správce vlastní haldy, který vrátí ukazatel na nově přidělené paměti haldy.  Tento dekorátor umožňuje nástroj správně identifikovat typ vrácené paměti.  Například:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Tento dekorátor řekne kompilátoru, že tato funkce je volání přidělování.  Každé volání funkce bude výstup adresy callsite, velikost instrukce volání a typeId nového objektu `S_HEAPALLOCSITE` na nový symbol.  Při přidělení zásobníku volání systémwindows vyzařuje událost ETW s těmito informacemi.  Nástroj profiler paměti prochází zásobníku volání hledá `S_HEAPALLOCSITE` zpáteční adresu odpovídající symbolu a typeId informace v symbolu se používá k zobrazení typu runtime přidělení.
   >
   > Stručně řečeno, to znamená, `(B*)(A*)MyMalloc(sizeof(B))` že volání, které vypadá, `B`se `void` v `A`nástroji zobrazí jako typ , ne nebo .

1. Pro C++ vytvořte `VSHeapTracker::CHeapTracker` objekt a zajistěte název haldy, která se zobrazí v nástroji profilování:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Pokud používáte C, `OpenHeapTracker` použijte funkci místo.  Tato funkce vrátí popisovač, který budete používat při volání jiných funkcí sledování:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Při přidělování paměti pomocí vlastní funkce volejte `AllocateEvent` metodu (C++) nebo `VSHeapTrackerAllocateEvent` (C) a předejte ukazatel paměti a její velikost, abyste sledovali přidělení:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   – nebo –

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nezapomeňte označit vlastní alokátor funkce s `__declspec(allocator)` decorator popsané dříve.

1. Při deallocating paměti pomocí vlastní `DeallocateEvent` funkce, volání (C++) nebo `VSHeapTracerDeallocateEvent` (C) funkce, předávání ukazatele do paměti, sledovat deallocation:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   nebo:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Při přerozdělování paměti pomocí vlastní funkce `ReallocateEvent` volejte metodu `VSHeapReallocateEvent` (C++) nebo (C) a předejte ukazatel na novou paměť, velikost přidělení a ukazatel na starou paměť:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   nebo:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Nakonec zavřete a vyčistěte vlastní nástroj pro sledování haldy v jazyce C++, použijte `CHeapTracker` destruktor, a to buď ručně, nebo pomocí standardních pravidel oboru, nebo `CloseHeapTracker` funkci v jazyce C:

   ```cpp
   delete pHeapTracker;
   ```

   nebo:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Sledování využití paměti
S těmito voláními na místě, vaše vlastní haldy využití lze nyní sledovat pomocí standardního nástroje **využití paměti** v sadě Visual Studio.  Další informace o použití tohoto nástroje naleznete v dokumentaci [k využití paměti.](../profiling/memory-usage.md) Ujistěte se, že jste povolili profilování haldy se snímky, jinak se nezobrazí vaše vlastní využití haldy.

![Povolit profilování haldy](media/heap-enable-heap.png)

Chcete-li zobrazit vlastní haldy sledování, použijte **rozbalovací haldy** se nachází v pravém horním rohu okna **snímek** změnit zobrazení z *NT haldy* na vlastní haldy, jak je uvedeno dříve.

![Výběr haldy](media/heap-example-custom-heap.png)

Pomocí výše uvedeného `MemoryPool` příkladu `VSHeapTracker::CHeapTracker` kódu, s `allocate` vytvořením `AllocateEvent` objektu a naší vlastní metody nyní volá metodu, nyní můžete zobrazit výsledek tohoto `Foo`vlastního přidělení, zobrazující tři instance v celkové výši 24 bajtů, všechny typu .

Výchozí *haldy haldy NT* vypadá stejně jako `CHeapTracker` dříve, s přidáním našeho objektu.

![NT Halda s trackerem](media/heap-example-windows-heap.png)

Stejně jako u standardní haldy systému Windows můžete také použít tento nástroj k porovnání snímků a vyhledejte nevracení a poškození vlastní haldy, která je popsána v hlavní dokumentaci [využití paměti.](../profiling/memory-usage.md)

> [!TIP]
> Visual Studio také obsahuje nástroj **využití paměti** v sadě nástrojů **Sledování profilování výkonu,** která je povolena z možnosti ladění**profilu** **výkonu** > nebo kombinace kláves **Alt**+**F2.**  Tato funkce nezahrnuje sledování haldy a nebude zobrazovat vlastní haldy, jak je popsáno zde.  Tuto funkci obsahuje pouze okno **Diagnostické nástroje,** které lze povolit pomocí nabídky **Ladicí** > **nástroje pro zobrazení systému** **Windows** > nebo kombinace klávesnice **Ctrl**+**Alt**+**F2.**

## <a name="see-also"></a>Viz také
[První pohled na profilovací nástroje](../profiling/profiling-feature-tour.md)
[Využití paměti](../profiling/memory-usage.md)
