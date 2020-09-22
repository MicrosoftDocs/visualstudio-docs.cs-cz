---
title: Pravidla spolehlivosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a35b9c49f2eb5655eeb67721b0fafdbbe1e087
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808269"
---
# <a name="reliability-rules"></a>Pravidla spolehlivosti

Pravidla spolehlivosti podporují spolehlivost knihovny a aplikace, jako je třeba správné využití paměti a vlákna.

|Pravidlo|Popis|
|----------|-----------------|
|[CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000.md)|Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah.|
|[CA2002: Nepoužívejte zámky u objektů se slabou identitou](../code-quality/ca2002.md)|Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt.|
|[CA2007: Nečekejte přímo na úlohu](../code-quality/ca2007.md)|Asynchronní metoda [čeká](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> přímo.|
|[CA2008: Nevytvářejte úlohy bez předání Plánovače úloh](../code-quality/ca2008.md)|Operace vytvoření nebo pokračování úlohy používá přetížení metody, které neurčuje <xref:System.Threading.Tasks.TaskScheduler> parametr.|
|[CA2009: Nevolejte ToImmutableCollection pro hodnotu ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable` Metoda byla nutně volána pro neproměnlivou kolekci z <xref:System.Collections.Immutable> oboru názvů.|
|[CA2011: Nepřiřazujte vlastnost v rámci její metody setter](../code-quality/ca2011.md) | Vlastnost byla omylem přiřazena hodnota v rámci vlastního [přístupového objektu set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[CA2012: Správně použít hodnoty ValueTask](../code-quality/ca2012.md) | ValueTasks vrácené z vyvolání členů mají být přímo očekávány.  Pokusí se využít ValueTask vícekrát nebo získat přímý přístup k jednomu výsledku před tím, než je známý k dokončení, může způsobit výjimku nebo poškození.  Ignorování takového ValueTask je pravděpodobně indikace funkční chyby a může snížit výkon. |
|[CA2013: Nepoužívejte ReferenceEquals s typy hodnot](../code-quality/ca2013.md) | Při porovnávání hodnot pomocí <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , jsou-li objA a objB typy hodnot, jsou zabaleny před předáním do <xref:System.Object.ReferenceEquals%2A> metody. To znamená, že i když obě objA a objB reprezentují stejnou instanci typu hodnoty, <xref:System.Object.ReferenceEquals%2A> metoda ale přesto vrátí hodnotu false. |
|[CA2014: Nepoužívejte stackalloc ve smyčce.](../code-quality/ca2014.md) | Prostor zásobníku přidělený stackalloc je vydaný jenom na konci vyvolání aktuální metody.  Použití ve smyčce může mít za následek neohraničený nárůst zásobníku a případné podmínky přetečení zásobníku. |
|[CA2015: nedefinujte finalizační metody pro typy odvozené z MemoryManager &lt; T&gt;](../code-quality/ca2015.md) | Přidání finalizační metody do typu odvozeného z <xref:System.Buffers.MemoryManager%601> může umožnit uvolnění paměti, pokud je stále používána <xref:System.Span%601> . |
|[CA2016: Přeposlat parametr CancellationToken metodám, které ho přijmou](ca2016.md) | Předejte `CancellationToken` parametr do metod, které jednu z nich přebírají, aby se zajistilo, že oznámení o zrušení operace budou správně šířena, nebo jestli se má explicitně předat označení, že se `CancellationToken.None` token nešíří. |
