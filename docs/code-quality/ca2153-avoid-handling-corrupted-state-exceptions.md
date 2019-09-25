---
title: Pravidlo analýzy kódu CA2153 pro výjimky v poškozených stavech
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36442ad0792ef712acd322d17688d8ceb21444cb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231896"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Vyhnout se zpracování výjimek poškozených stavů

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

[Poškozené výjimky stavu (rozšíření)](https://msdn.microsoft.com/magazine/dd419661.aspx) označují, že v procesu existuje poškození paměti. Pokud by útočník mohl zneužít do poškozené oblasti paměti, může to místo toho zachytit, než umožní selhání procesu způsobit chyby zabezpečení.

## <a name="rule-description"></a>Popis pravidla

Rozšíření na straně serveru označuje, že stav procesu je poškozený a nebyl zachycen systémem. V případě poškozeného stavu je obecná obslužná rutina zachycena pouze v případě, že označíte metodu <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> atributem. Ve výchozím nastavení modul [CLR (Common Language Runtime)](/dotnet/standard/clr) nevyvolává obslužné rutiny catch pro rozšíření.

Nejbezpečnější možností je dovolit selhání procesu bez zachycení těchto druhů výjimek. I kód protokolování může útočníkům umožnit zneužít chyby poškození paměti.

Toto upozornění se aktivuje při zachycení rozšíření pomocí obecné obslužné rutiny, která zachytává všechny výjimky `catch (System.Exception e)` , `catch` například nebo bez parametru Exception.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li vyřešit toto upozornění, proveďte jednu z následujících akcí:

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Odeberte atribut. Vrátí se k výchozímu chování modulu runtime, kde rozšíření nejsou předány obslužným rutinám catch.

- Odeberte obslužnou rutinu obecné catch v předvolbách obslužných rutin, které zachycují konkrétní typy výjimek. To může zahrnovat rozšíření, za předpokladu, že kód obslužné rutiny může bezpečně zpracovat (vzácná).

- Znovu vyvolejte rozšíření v popisovači catch, který předá výjimku volajícímu a měl by mít za následek ukončení běžícího procesu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code

### <a name="violation"></a>Selhání

Následující pseudo kód ilustruje vzor zjištěný tímto pravidlem.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Řešení 1 – odebrání atributu

<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Odebrání atributu zajistí, že vaše metoda nezpracovává poškozené výjimky stavu.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Řešení 2 – zachytávání specifických výjimek

Odeberte obslužnou rutinu General catch a zachyťte pouze konkrétní typy výjimek.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Řešení 3 – opětovné vyvolání

Znovu vyvolejte výjimku.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```