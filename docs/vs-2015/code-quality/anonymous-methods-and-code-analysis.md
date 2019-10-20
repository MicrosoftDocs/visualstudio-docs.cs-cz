---
title: Anonymní metody a analýza kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652226"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonymní metody a analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Anonymní metoda* je metoda, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametru delegáta.

 Toto téma vysvětluje, jak analýza kódu zpracovává upozornění a metriky, které jsou přidruženy k anonymním metodám.

## <a name="anonymous-methods-declared-in-a-member"></a>Anonymní metody deklarované ve členovi
 Upozornění a metriky pro anonymní metodu, která je deklarována v členu, jako je například metoda nebo přistupující objekt, jsou přidruženy ke členu, který deklaruje metodu. Nejsou přidruženy ke členu, který volá metodu.

 Například v následující třídě by všechna upozornění, která jsou nalezena v deklaraci **anonymousMethod** , měla být vyvolána proti **– Metoda1** a nikoli **Method2**.

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
 Upozornění a metriky anonymní metody, která je deklarována jako vložené přiřazení k poli, jsou přidruženy k konstruktoru. Pokud je pole deklarováno jako `static` (`Shared` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), jsou upozornění a metriky spojeny s konstruktorem třídy; v opačném případě jsou přidruženy k konstruktoru instance.

 Například v následující třídě budou všechna upozornění, která jsou nalezena v deklaraci **anonymousMethod1** , vyvolána proti implicitně generovanému výchozímu konstruktoru **třídy**. Ty, které se nacházejí v **anonymousMethod2** , se použijí proti implicitně generovanému konstruktoru třídy.

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

 Třída může obsahovat vloženou anonymní metodu, která přiřadí hodnotu poli s více konstruktory. V tomto případě jsou upozornění a metriky asociovány se všemi konstruktory, pokud tento konstruktor řetězí k jinému konstruktoru ve stejné třídě.

 Například v následující třídě by všechna upozornění, která jsou nalezena v deklaraci **anonymousMethod** , měla být vyvolána proti **třídě (int)** a **třídě (String)** , ale nikoli proti **třídě ()** .

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

 I když se to může zdát neočekávaně, dojde k tomu proto, že kompilátor výstupuje jedinečnou metodu pro každý konstruktor, který není zřetězený na jiný konstruktor. Z důvodu tohoto chování musí být jakékoli porušení, ke kterému dochází v **anonymousMethod** , potlačeno samostatně. To také znamená, že pokud je zaveden nový konstruktor, upozornění, která byla dříve potlačena před **třídou (int)** a **třídou (String)** , musí být také potlačena proti novému konstruktoru.

 Tento problém můžete obejít jedním ze dvou způsobů. Můžete deklarovat **anonymousMethod** ve společném konstruktoru, který všechny konstruktory řetězí. Nebo ho můžete deklarovat v inicializační metodě, která je volána všemi konstruktory.

## <a name="see-also"></a>Viz také
 [Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
