---
title: Anonymní metody a analýza kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 73ff8dfca29f1ed9896462725886baa87e729100
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280160"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonymní metody a analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Anonymní metoda* je metoda, která nemá žádný název. Anonymní metody se nejčastěji používají k předání bloku kódu jako parametr delegátu.  
  
 Toto téma vysvětluje, jak analýzy kódu zpracovává upozornění a metriky, které jsou spojeny s anonymními metodami.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Anonymní metody s deklarací v člena  
 Upozornění a metriky pro anonymní metody, která je deklarována v členu, například metoda nebo přístupový objekt, jsou spojeny s člena, který deklaruje metodu. Nejsou přidružené člena, který volá metodu.  
  
 Například ve třídě následující upozornění, které se nacházejí v deklaraci **anonymousMethod** by měla být zvýšena proti **– metoda1** a ne **Method2**.  
  
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
 Upozornění a metriky pro anonymní metody, která je deklarována jako vložené přiřazení k poli jsou spojeny s konstruktoru. Pokud toto pole je deklarován jako `static` (`Shared` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), upozornění a metriky jsou spojené s konstruktoru třídy; jinak vrátí hodnotu, jsou spojeny se konstruktor instance.  
  
 Například ve třídě následující upozornění, které se nacházejí v deklaraci **anonymousMethod1** proti implicitně generovaný výchozí konstruktor třídy, bude vyvolána **třídy**. Vzhledem k tomu nalezené v **anonymousMethod2** se uplatňuje třídy implicitně generovaný konstruktor.  
  
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
  
 Třída může obsahovat vložené anonymní metody, který přiřazuje hodnotu pole, která má víc konstruktorů. V takovém případě metriky a upozorněními jsou spojeny s všechny konstruktory není-li tento konstruktor zřetězený jiný konstruktor ve stejné třídě.  
  
 Například ve třídě následující upozornění, které se nacházejí v deklaraci **anonymousMethod** by měla být zvýšena proti **Class(int)** a **Class(string)** ale Ne před **Class()**.  
  
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
  
 I když to může zdát neočekávané, tomu dochází, protože kompilátor výstupy metodu jedinečný pro každý konstruktoru, které nejsou zřetězené do jiného konstruktoru. Kvůli tomuto chování nedodržení, která nastane v **anonymousMethod** musí být potlačeno samostatně. To také znamená, že pokud je nový konstruktor zavedená, upozornění, které byly dříve potlačeny proti **Class(int)** a **Class(string)** musí také být potlačeno proti nový konstruktor.  
  
 Můžete alternativně vyřešit tento problém v jednom ze dvou způsobů. Můžete deklarovat **anonymousMethod** v běžných konstruktor, který všechny konstruktory řetězce. Nebo můžete ji deklarovat v inicializační metoda, která je volána všechny konstruktory.  
  
## <a name="see-also"></a>Viz také  
 [Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)



