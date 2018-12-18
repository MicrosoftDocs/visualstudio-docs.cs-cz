---
title: 'CA2153: Vyhněte se zpracování výjimek v poškozeném stavu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5043c8cb9cefb8ffdb600083ba2dc4bb49d5e3f5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547516"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Vyhněte se zpracování výjimek v poškozeném stavu

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

[Poškozený stav výjimek (rozšíření na straně klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) znamenat, že paměť poškození existuje v procesu. Toto zachycení nepovolí selhání procesu může vést k ohrožení zabezpečení, pokud útočník lze umístit do oblasti paměti poškozená zneužití.

## <a name="rule-description"></a>Popis pravidla

Rozšíření na straně klienta Určuje, že stav procesu byl poškozený a není zachycena v systému. V poškozeném stavu scénáři obecné obslužné rutiny pouze zachytí výjimku Pokud označíte metodu správné `HandleProcessCorruptedStateExceptions` atribut. Ve výchozím nastavení [Common Language Runtime (CLR)](/dotnet/standard/clr) nebude volat obslužné rutiny catch pro rozšíření na straně klienta.

Povolení proces při selhání bez zachycování tyto druhy výjimek je nejbezpečnější možnosti, jako i protokolování kódu můžou útočníci zneužít ohrožená místa chyby poškození paměti.

Toto upozornění se aktivuje při zachycování rozšíření na straně klienta pomocí obecné obslužné rutině, která zachytává všechny výjimky, jako je například catch(exception) nebo catch (bez specifikací výjimek).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Pokud chcete vyřešit toto upozornění, proveďte jednu z následujících akcí:

- Odeberte `HandleProcessCorruptedStateExceptions` atribut. To obnoví na výchozí chování za běhu, ve kterém nejsou předán obslužné rutiny zachytávání rozšíření na straně klienta.

- Odeberte obslužnou rutinu obecný zachytávací in preference of obslužných rutin, které zachytit specifické výjimky typy. To může zahrnovat rozšíření na straně klienta za předpokladu, že kód obslužné rutiny můžete bezpečně jejich zpracování (vzácného).

- V obslužné rutiny catch, který zajišťuje výjimky je předán do volajícího a bude mít za následek ukončení spuštěného procesu znovu vyvolejte rozšíření na straně klienta.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad pseudo kódu

### <a name="violation"></a>Porušení

Pseudo následující kód znázorňuje, zjistí toto pravidlo.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Řešení 1

Odebrání atributu HandleProcessCorruptedExceptions zajistí, že k výjimkám nebude zpracován.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Řešení 2

Odebrat obslužnou rutinu obecný zachytávací a zachytit pouze typy určité výjimky.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Řešení 3

Znovu vyvolá výjimku.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```