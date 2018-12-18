---
title: 'CA2153: Vyhněte se zpracování výjimek v poškozeném stavu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 00e475fa90e0a9976105e4c9c645746427366f32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869948"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Vyhněte se zpracování výjimek v poškozeném stavu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 [Poškozený stav výjimek (rozšíření na straně klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) znamenat, že paměť poškození existuje v procesu. Toto zachycení nepovolí selhání procesu může vést k ohrožení zabezpečení, pokud útočník lze umístit do oblasti paměti poškozená zneužití.

## <a name="rule-description"></a>Popis pravidla
 Rozšíření na straně klienta Určuje, že stav procesu byl poškozený a není zachycena v systému. V poškozeném stavu scénáři obecné obslužné rutiny pouze zachytí výjimku Pokud označíte metodu správné `HandleProcessCorruptedStateExceptions` atribut. Ve výchozím nastavení [Common Language Runtime (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) nebude volat obslužné rutiny catch pro rozšíření na straně klienta.

 Povolení proces při selhání bez zachycování tyto druhy výjimek je nejbezpečnější možnosti, jako i protokolování kódu můžou útočníci zneužít ohrožená místa chyby poškození paměti.

 Toto upozornění se aktivuje při zachycování rozšíření na straně klienta pomocí obecné obslužné rutině, která zachytává všechny výjimky, jako je například catch(exception) nebo catch (bez specifikací výjimek).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li vyřešit tato upozornění by měl proveďte jednu z následujících akcí:

 1. Odeberte `HandleProcessCorruptedStateExceptions` atribut. To obnoví na výchozí chování za běhu, ve kterém nejsou předán obslužné rutiny zachytávání rozšíření na straně klienta.

 2. Odeberte obslužnou rutinu obecný zachytávací in preference of obslužných rutin, které zachytit specifické výjimky typy.  To může zahrnovat rozšíření na straně klienta za předpokladu, že kód obslužné rutiny můžete bezpečně jejich zpracování (velmi výjimečných).

 3. Znovu vyvolejte rozšíření na straně klienta v obslužné rutiny catch, který zajišťuje výjimky je předán do volajícího a bude mít za následek ukončení spuštěného procesu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad pseudo kódu

### <a name="violation"></a>Porušení
 Pseudo následující kód znázorňuje, zjistí toto pravidlo.

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
 Odebrání atributu HandleProcessCorruptedExceptions zajistí, že k výjimkám nebude zpracován.

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
 Odebrat obslužnou rutinu obecný zachytávací a zachytit pouze typy určité výjimky.

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
 Opětovné vyvolání výjimky.

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



