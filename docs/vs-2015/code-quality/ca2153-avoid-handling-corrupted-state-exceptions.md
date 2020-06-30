---
title: 'CA2153: Vyhněte se zpracování výjimek poškozených stavů | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 27d837c09e5f2f90796c149bf58d1114d7e6352d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546312"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Vyhněte se zpracování výjimek v poškozeném stavu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 [Poškozené výjimky stavu (rozšíření)](https://msdn.microsoft.com/magazine/dd419661.aspx) označují, že v procesu existuje poškození paměti. Pokud by útočník mohl zneužít do poškozené oblasti paměti, může to místo toho zachytit, než umožní selhání procesu způsobit chyby zabezpečení.

## <a name="rule-description"></a>Popis pravidla
 Rozšíření na straně serveru označuje, že stav procesu je poškozený a nebyl zachycen systémem. V případě poškozeného stavu je obecná obslužná rutina zachycena pouze v případě, že svou metodu označíte pomocí správného `HandleProcessCorruptedStateExceptions` atributu. Ve výchozím nastavení nebude modul [CLR (Common Language Runtime)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) vyvolat obslužné rutiny catch pro rozšíření.

 Povolení selhání procesu bez zachycení těchto typů výjimek je nejbezpečnější možností, protože i kód protokolování může útočníkům umožnit zneužít chyby poškození paměti.

 Toto upozornění se aktivuje při zachycení rozšíření pomocí obecné obslužné rutiny, která zachytává všechny výjimky, například catch (Exception) nebo catch (bez specifikace výjimek).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li vyřešit toto upozornění, proveďte jednu z následujících akcí:

 1. Odeberte `HandleProcessCorruptedStateExceptions` atribut. Vrátí se k výchozímu chování modulu runtime, kde rozšíření nejsou předány obslužným rutinám catch.

 2. Odeberte obslužnou rutinu obecné catch v předvolbách obslužných rutin, které zachycují konkrétní typy výjimek.  To může zahrnovat rozšíření za předpokladu, že kód obslužné rutiny může bezpečně zpracovat (velmi zřídka).

 3. Znovu vyvolejte rozšíření v popisovači catch, který zajistí, že je výjimka předána volajícímu a bude mít za následek ukončení běžícího procesu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code

### <a name="violation"></a>Selhání
 Následující pseudo kód ilustruje vzor zjištěný tímto pravidlem.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Řešení 1
 Odebráním atributu HandleProcessCorruptedExceptions se zajistí, že výjimky nebudou zpracovány.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Řešení 2
 Odeberte obslužnou rutinu General catch a zachyťte pouze konkrétní typy výjimek.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Řešení 3
 Znovu vyvolejte výjimku.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```
