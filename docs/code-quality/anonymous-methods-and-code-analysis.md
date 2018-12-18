---
title: Anonymní metody a analýza kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e069976badeffbce04b2f245277426441d3df2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31892700"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonymní metody a analýza kódu
*Anonymní metoda* je metoda, která nemá žádný název. Anonymní metody jsou nejčastěji sloužící k předávání blok kódu jako parametr delegáta.

 Toto téma vysvětluje, jak analýza kódu zpracovává upozornění a metriky, které jsou přidruženy anonymní metody.

## <a name="anonymous-methods-declared-in-a-member"></a>Anonymní metody, které jsou deklarované v člena
 Upozornění a metriky pro anonymní metodu, která je deklarován v členem, jako je metoda nebo přistupující objekt, jsou přidružena k členovi, který deklaruje metodu. Nejsou přidruženy člena, který volá metodu.

 Například v následující třídy, všechna upozornění, které se nacházejí v deklaraci **anonymousMethod** by měla být zvýšena proti **Method1** a není **Method2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Vložené anonymní metody
 Upozornění a metriky pro anonymní metodu, která je deklarován jako přiřazování vložené do pole jsou přidruženy k konstruktoru. Pokud toto pole je deklarován jako `static` (`Shared` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), upozornění a metriky jsou přidruženy konstruktoru třídy jinak, jsou spojeny s konstruktorem instance.

 Například v následující třídy, všechna upozornění, které se nacházejí v deklaraci **anonymousMethod1** proti implicitně generovaného výchozí konstruktor, bude vyvolána **třída**. Zatímco chyby nalezené v **anonymousMethod2** se použijí pro konstruktor implicitně vygenerované třídy.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

 Třída může obsahovat vložené anonymní metody, který přiřazuje hodnotu pole, které obsahuje několik konstruktorů. V takovém případě upozornění a metriky jsou přidruženi ke všechny konstruktory Pokud tento konstruktor řetězí jiný konstruktor ve stejné třídě.

 Například v následující třídy, všechna upozornění, které se nacházejí v deklaraci **anonymousMethod** by měla být zvýšena proti **Class(int)** a **Class(string)** ale nikoliv **Class()**.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

 I když to se může zdát neočekávané, tomu dochází, kompilátor výstupy jedinečný metoda pro každou konstruktor, který nejsou zřetězeny do jiný konstruktor. Z důvodu toto chování nedodržení k tomu dojde v **anonymousMethod** musí být potlačeno samostatně. To také znamená, že pokud je nový konstruktor zavádí, upozornění, které byly dříve potlačovány proti **Class(int)** a **Class(string)** musí potlačeny také proti nové konstruktoru.

 Můžete alternativně vyřešit tento problém v jednom ze dvou způsobů. Může deklarovat **anonymousMethod** v běžné konstruktoru, všechny konstruktory řetězu. Nebo se může deklarovat v inicializační metoda, která je volána, všechny konstruktory.

## <a name="see-also"></a>Viz také
 [Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)