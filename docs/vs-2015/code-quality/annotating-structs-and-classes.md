---
title: Přidávání poznámek ke strukturám a třídám | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77271579"
---
# <a name="annotating-structs-and-classes"></a>Zadávání poznámek ke strukturám a třídám
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Členy struktury a třídy lze opatřit poznámkami pomocí anotací, které fungují jako invariantní – jsou považovány za pravdivé při jakémkoli volání funkce nebo vstupní/výstupní funkci, která zahrnuje ohraničující strukturu jako parametr nebo výslednou hodnotu.  
  
## <a name="struct-and-class-annotations"></a>Poznámky ke struktuře a třídě  
  
- `_Field_range_(low, high)`  
  
     Pole je v rozsahu (včetně) z `low` na `high` .  Odpovídá `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` použitému objektu s poznámkou s použitím odpovídajících podmínek před nebo po.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Pole, které má zapisovatelné velikosti v prvcích (nebo bajtech), jak je uvedeno v `size` .  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Pole, které má zapisovatelné velikosti v prvcích (nebo bajtech), jak je uvedeno v rámci `size` , a `count` z těchto prvků (bajtů), které lze číst.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Pole, které má čitelné i zapisovatelné velikosti v prvcích (nebo bajtech), jak je uvedeno v `size` .  
  
- `_Struct_size_bytes_(size)`  
  
     Pole, které má čitelné i zapisovatelné velikosti v prvcích (nebo bajtech), jak je uvedeno v `size` .  
  
     Platí pro strukturu nebo deklaraci třídy.  Označuje, že platný objekt tohoto typu může být větší než deklarovaný typ, s počtem bajtů určených parametrem `size` .  Příklad:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Velikost vyrovnávací paměti v bajtech parametru `pM` typu je pak považována za `MyStruct *` :  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení vad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
