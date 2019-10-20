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
ms.openlocfilehash: 6996d210417a56dd83532c481aaa0dc80b9f23ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655239"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Typ, který je konkrétně označen jako viditelný pro model COM (Component Object Model) obsahuje metodu `public``static`.

## <a name="rule-description"></a>Popis pravidla
 Model COM nepodporuje metody `static`.

 Toto pravidlo ignoruje přístupové objekty vlastností a událostí, metody přetížení operátoru nebo metody, které jsou označeny pomocí atributu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> nebo atributu <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

 Ve výchozím nastavení jsou následující prvky viditelné v modelu COM: sestavení, veřejné typy, členy veřejné instance ve veřejných typech a všechny členy typů veřejné hodnoty.

 Pro toto pravidlo musí být <xref:System.Runtime.InteropServices.ComVisibleAttribute> na úrovni sestavení nastavená na `false` a třída-<xref:System.Runtime.InteropServices.ComVisibleAttribute> musí být nastavená na `true`, jak ukazuje následující kód.

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
 Chcete-li opravit porušení tohoto pravidla, změňte návrh tak, aby používal metodu instance, která poskytuje stejné funkce jako metoda `static`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že klient modelu COM nevyžaduje přístup k funkcím, které jsou poskytovány metodou `static`, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Následující příklad ukazuje metodu `static`, která toto pravidlo porušuje.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Komentáře
 V tomto příkladu nelze volat metodu **Book. FromPages** z modelu COM.

## <a name="example-fix"></a>Příklad opravy

### <a name="description"></a>Popis
 Chcete-li opravit porušení v předchozím příkladu, můžete změnit metodu na metodu instance, která ale v této instanci nedává smysl. Lepším řešením je explicitně použít `ComVisible(false)` na metodu, aby bylo jasné, že by nebylo možné z modelu COM vyjasnit jiným vývojářům, že tuto metodu nelze zobrazit.

 Následující příklad se vztahuje <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> na metodu.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1017: Označte sestavení pomocí atributu ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Viz také
 [Spolupráce s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
