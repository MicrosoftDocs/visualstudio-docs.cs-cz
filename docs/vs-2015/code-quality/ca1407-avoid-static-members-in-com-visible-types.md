---
title: 'CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 436a8614c18c296c072d91116143306d898f0436
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538850"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ, který je konkrétně označen jako viditelný pro model COM (Component Object Model) obsahuje `public``static` metodu.

## <a name="rule-description"></a>Popis pravidla
 Model COM nepodporuje `static` metody.

 Toto pravidlo ignoruje přístupové objekty vlastností a událostí, metody přetížení operátoru nebo metody, které jsou označeny pomocí <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributu nebo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributu.

 Ve výchozím nastavení jsou následující prvky viditelné v modelu COM: sestavení, veřejné typy, členy veřejné instance ve veřejných typech a všechny členy typů veřejné hodnoty.

 Aby toto pravidlo bylo provedeno, musí být na úrovni sestavení <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavena na `false` a třída <xref:System.Runtime.InteropServices.ComVisibleAttribute> musí být nastavena na `true` , jak ukazuje následující kód.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte návrh tak, aby používal metodu instance, která poskytuje stejné funkce jako `static` metoda.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že klient modelu COM nevyžaduje přístup k funkcím, které poskytuje metoda, je bezpečné potlačit upozornění od tohoto pravidla `static` .

## <a name="example-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Následující příklad ukazuje `static` metodu, která porušuje toto pravidlo.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Komentáře
 V tomto příkladu nelze volat metodu **Book. FromPages** z modelu COM.

## <a name="example-fix"></a>Příklad opravy

### <a name="description"></a>Popis
 Chcete-li opravit porušení v předchozím příkladu, můžete změnit metodu na metodu instance, která ale v této instanci nedává smysl. Lepším řešením je výslovně použít `ComVisible(false)` tuto metodu, aby bylo jasné, že nepůjde z modelu COM vyjasnit jiným vývojářům.

 Následující příklad se vztahuje <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> na metodu.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Vyhněte se neveřejným polím v typech hodnot viditelných modulem COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Viz také
 [Spolupráce s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
