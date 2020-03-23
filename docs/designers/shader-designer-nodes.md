---
title: Uzly návrháře shaderů
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23877f9b94b498d87a89ae8e657aa2fe52984953
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72634930"
---
# <a name="shader-designer-nodes"></a>Uzly Návrhářshaderu
Články v této části dokumentace obsahují informace o různých uzlech Návrháře shaderu, které můžete použít k vytvoření grafických efektů.

## <a name="nodes-and-node-types"></a>Typy uzlů a uzlů
Návrhář shaderu představuje vizuální efekty jako graf. Tyto grafy jsou sestaveny z uzlů, které jsou speciálně vybrány a propojeny přesným způsobem k dosažení zamýšleného účinku. Každý uzel představuje informace nebo matematické funkce a připojení mezi nimi představují, jak informace toky prostřednictvím grafu k vytvoření výsledku. Návrhář shaderu poskytuje šest různých typů uzlů – filtry, uzly textury, parametry, konstanty, uzly nástrojů a matematické uzly – a několik jednotlivých uzlů patří ke každému typu. Tyto typy uzlů a uzlů jsou popsány v jiných článcích v této části. Další informace naleznete v odkazech na konci tohoto dokumentu.

## <a name="node-structure"></a>Struktura uzlů
Všechny uzly jsou tvořeny kombinací společných prvků. Každý uzel má alespoň jeden výstupní terminál na pravé straně (s výjimkou konečného barevného uzlu, který představuje výstup shaderu). Uzly, které představují výpočty nebo vzorkovače textur, mají vstupní terminály na levé straně, ale uzly, které představují informace, nemají žádné vstupní terminály. Výstupní terminály jsou připojeny ke vstupním svorkám a přesouvají informace z jednoho uzlu do druhého.

### <a name="promotion-of-inputs"></a>Podpora vstupů
Vzhledem k tomu, že návrhář shaderu musí nakonec vygenerovat zdrojový kód HLSL, aby byl efekt možné použít ve hře nebo aplikaci, vztahují se uzly Návrháře shaderu pravidlům propagace typů, která používá HLSL. Vzhledem k tomu, že grafický hardware pracuje především s hodnotami `int` s `float`plovoucí `float` desetinnou desetinnou hodnotou, je povýšení typu mezi různými typy – například z do nebo z do `double`– neobvyklé. Místo toho, protože grafický hardware používá stejnou operaci na více částí informací najednou, může dojít k jinému druhu propagace, ve kterém je prodloužena kratší z počtu vstupů tak, aby odpovídala velikosti nejdelší vstup. Způsob jeho prodloužení závisí na typu vstupu a také na samotné operaci:

- **Pokud je menší typ skalární hodnotou, pak:**

     Hodnota skaláru je replikována do vektoru, který se rovná velikosti většího vstupu. Například skalární vstup 5.0 se stane vektorem (5.0, 5.0, 5.0), pokud je největším vstupem operace vektor se třemi prvky, bez ohledu na to, co je operace.

- **Pokud je menší typ vektor a operace je\*multiplikativní ( , /, %, atd.), pak:**

     Hodnota vektoru je zkopírována do počátečních prvků vektoru, který se rovná velikosti většího vstupu, a koncové prvky jsou nastaveny na hodnotu 1,0. Například vektorový vstup (5.0, 5.0) se stane vektorem (5.0, 5.0, 1.0, 1.0), když se vynásobí vektorem se čtyřmi prvky. Tím se zachová třetí a čtvrtý prvk výstupu pomocí multiplikativní identity 1.0.

- **Pokud menší typ je vektor a operace je aditivní (+, -, a tak dále), pak:**

     Hodnota vektoru je zkopírována do počátečních prvků vektoru, který se rovná velikosti většího vstupu, a koncové prvky jsou nastaveny na 0,0. Například vektorový vstup (5.0, 5.0) se stane vektorem (5.0, 5.0, 0.0, 0.0), když je přidán do vektoru se čtyřmi prvky. Tím se zachová třetí a čtvrtý prvk výstupu pomocí aditivní identity 0.0.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Uzly konstanty](../designers/constant-nodes.md)|Popisuje uzly, které můžete použít k reprezentaci literálových hodnot a interpolovaných informací o stavu vrcholu ve výpočtech shaderu. Vzhledem k tomu, že stav vrcholu je interpolován – a proto se pro každý obrazový bod liší – každá instance shaderu obrazových bodů obdrží jinou verzi konstanty.|
|[Uzly parametru](../designers/parameter-nodes.md)|Popisuje uzly, které můžete použít k reprezentaci polohy kamery, vlastností materiálu, parametrů osvětlení, času a dalších informací o stavu aplikace ve výpočtech shaderu.|
|[Uzly textury](../designers/texture-nodes.md)|Popisuje uzly, které můžete použít k vzorkování různých typů textur a geometrií a k vytváření nebo transformaci souřadnic textury běžnými způsoby.|
|[Matematické uzly](../designers/math-nodes.md)|Popisuje uzly, které můžete použít k provádění algebraických, logických, trigonometrických a dalších matematických operací, které se mapují přímo na pokyny HLSL.|
|[Uzly nástroje](../designers/utility-nodes.md)|Popisuje uzly, které můžete použít k provádění běžných výpočtů osvětlení a dalších běžných operací, které nejsou mapovány přímo na pokyny HLSL.|
|[Uzly filtrů](../designers/filter-nodes.md)|Popisuje uzly, které můžete použít k filtrování textur a filtrování barev.|
