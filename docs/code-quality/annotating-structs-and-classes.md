---
title: Zadávání poznámek ke strukturám a třídám
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 0ebcd88df8508ae534ab51289016261193f54380
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271031"
---
# <a name="annotating-structs-and-classes"></a>Zadávání poznámek ke strukturám a třídám

Členy struktury a třídy lze opatřit poznámkami pomocí anotací, které fungují jako invariantní – jsou považovány za pravdivé při jakémkoli volání funkce nebo vstupní/výstupní funkci, která zahrnuje ohraničující strukturu jako parametr nebo výslednou hodnotu.

## <a name="struct-and-class-annotations"></a>Poznámky ke struktuře a třídě

- `_Field_range_(low, high)`

     Pole je v rozsahu (včetně) od `low` do `high`.  Ekvivalentem `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` použitým u objektu s poznámkou pomocí příslušných podmínek před nebo po odeslání.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Pole, které má zapisovatelné velikosti v prvcích (nebo bajtech), jak je určeno `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`, `_Field_size_bytes_part_(size, count)``_Field_size_bytes_part_opt_(size, count)`

     Pole, které má zapisovatelné velikosti v prvcích (nebo bajtech), jak je určeno `size`a `count` těch prvků (bajtů), které jsou čitelné.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Pole, které má čitelné i zapisovatelné velikosti v elementech (nebo bajtech), jak je určeno `size`.

- `_Field_z_`

     Pole, které má řetězec zakončený hodnotou null.

- `_Struct_size_bytes_(size)`

     Platí pro strukturu nebo deklaraci třídy.  Označuje, že platný objekt tohoto typu může být větší než deklarovaný typ, s počtem bajtů určených `size`.  Příklad:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Velikost vyrovnávací paměti v bajtech parametru `pM` typu `MyStruct *` je pak považována za:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Příklad

```cpp
#include <sal.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(__builtin_offsetof(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[]; // Using C99 Flexible array member
};
```

Poznámky k tomuto příkladu:

- `_Field_z_` je ekvivalentem `_Null_terminated_`.  `_Field_z_` pro pole název určuje, že pole název je řetězec zakončený hodnotou null.
- `_Field_range_` pro `bufferSize` určuje, že hodnota `bufferSize` by měla být v rozmezí od 1 do `MaxBufferSize` (včetně).
- Konečné výsledky `_Struct_size_bytes_` a `_Field_size_` poznámek jsou ekvivalentní. U struktur nebo tříd, které mají podobné rozložení, `_Field_size_` je snazší je číst a udržovat, protože má méně odkazů a výpočtů než ekvivalentní `_Struct_size_bytes_` anotace. `_Field_size_` nevyžaduje převod na velikost bajtu. Je-li velikost bajtu jedinou možností, například pro pole typu void, lze použít `_Field_size_bytes_`. Pokud existují `_Struct_size_bytes_` i `_Field_size_`, bude k dispozici pro nástroje. V případě nesouhlasu dvou poznámek se jedná o nástroj.

## <a name="see-also"></a>Viz také:

- [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Porozumění SAL](../code-quality/understanding-sal.md)
- [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
- [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)
- [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Vnitřní funkce](../code-quality/intrinsic-functions.md)
- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
