---
title: 'CA2118: Revize použití SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 900abe516ebd07cf5a8849f269f915623500731e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859702"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Revize použití SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ nebo člen má <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atribut.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> mění výchozí chování zabezpečení systému pro členy vykonávající nespravovaný kód pomocí modelu COM interop nebo vyvolání platformy. Obecně platí, systém provede [Data a modelování](/dotnet/framework/data/index) oprávnění pro nespravovaný kód. Tomuto požadavku dojde za běhu pro každé vyvolání členu a zkontroluje každý volající v zásobníku volání o oprávnění. Pokud atribut je k dispozici, systém provede [požadavky propojení](/dotnet/framework/misc/link-demands) oprávnění: se kontroluje oprávnění bezprostředního volajícího, když volající je zkompilován JIT Kompilátorem.

 Tento atribut slouží především ke zvýšení výkonu, ačkoliv nárůst výkonu může být spojen s významnými riziky zabezpečení. Pokud umístit atribut na veřejné členy, které volají metody nativní volající v zásobníku volání (jiné než bezprostředního volajícího) není nutné nespravovaný kód oprávnění k provedení nespravovaného kódu. V závislosti na veřejný člen akce a zpracování vstupních mohl nedůvěryhodných volajících pro přístup k funkcím, obvykle s omezením pomocí specifikátoru pro důvěryhodného kódu.

 Rozhraní .NET Framework spoléhá na kontroly zabezpečení, aby volající získat přímý přístup do adresního prostoru aktuální proces. Protože tento atribut obchází normální zabezpečení, váš kód představuje vážné ohrožení, pokud je možné číst nebo zapsat do paměti procesu. Mějte na paměti, že riziko není omezena pouze na metody, které záměrně poskytují přístup ke zpracování v paměti. je také k dispozici ve všech scénářích, kde škodlivý kód můžete dosáhnout přístup žádným způsobem, například tím, že poskytuje překvapivé, chybný nebo není platný vstup.

 Výchozí zásady zabezpečení neuděluje oprávnění nespravovaného kódu na sestavení, pokud je spuštěn v místním počítači nebo je členem jedné z následujících skupin:

- Moje skupina počítačů zóny kódu

- Microsoft Strong Name kódová skupina

- Skupiny kódu silného názvu ECMA

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pečlivě zkontrolujte kód a ujistěte se, že tento atribut je nezbytně nutné. Pokud nejste obeznámeni s spravovaný kód zabezpečení nebo není srozumitelný bezpečnostních důsledcích pomocí tohoto atributu, odeberte ho z vašeho kódu. Pokud je vyžadován atribut, musíte zajistit, že volající speciálně nemůžete použít kód. Pokud váš kód nemá oprávnění k provedení nespravovaného kódu, tento atribut nemá žádný vliv a měly by se odebrat.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že váš kód neposkytuje volající přístup k nativním operace nebo prostředky použité destruktivním způsobem.

## <a name="example-1"></a>Příklad 1
 Následující příklad poruší toto pravidlo.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Příklad 2
 V následujícím příkladu `DoWork` metoda poskytuje cestu veřejně přístupné kódu do metody vyvolání platformy `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Příklad 3
 V následujícím příkladu, veřejnou metodu `DoDangerousThing` způsobí, že je porušení pravidel. Chcete-li vyřešit porušení zásad, `DoDangerousThing` třeba privátní a přístup k němu můžete použít veřejnou metodu zabezpečena pomocí požadavku zabezpečení, jak je znázorněno v `DoWork` metody.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Data a modelování](/dotnet/framework/data/index)
- [Požadavky propojení](/dotnet/framework/misc/link-demands)