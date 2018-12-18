---
title: 'CA2118: Revize použití SuppressUnmanagedCodeSecurityAttribute | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d4cee2d7758f467a13875f89a9534ceb0d883b5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904476"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Revize použití SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ nebo člen má <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atribut.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> mění výchozí chování zabezpečení systému pro členy vykonávající nespravovaný kód pomocí modelu COM interop nebo vyvolání platformy. Obecně platí, systém provede [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oprávnění pro nespravovaný kód. Tomuto požadavku dojde za běhu pro každé vyvolání členu a zkontroluje každý volající v zásobníku volání o oprávnění. Pokud atribut je k dispozici, systém provede [požadavky propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) oprávnění: se kontroluje oprávnění bezprostředního volajícího, když volající je zkompilován JIT Kompilátorem.

 Tento atribut slouží především ke zvýšení výkonu, ačkoliv nárůst výkonu může být spojen s významnými riziky zabezpečení. Pokud umístit atribut na veřejné členy, které volají metody nativní volající v zásobníku volání (jiné než bezprostředního volajícího) není nutné nespravovaný kód oprávnění k provedení nespravovaného kódu. V závislosti na veřejný člen akce a zpracování vstupních mohl nedůvěryhodných volajících pro přístup k funkcím, obvykle s omezením pomocí specifikátoru pro důvěryhodného kódu.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Spoléhá na kontroly zabezpečení, aby volající získat přímý přístup do adresního prostoru aktuální proces. Protože tento atribut obchází normální zabezpečení, váš kód představuje vážné ohrožení, pokud je možné číst nebo zapsat do paměti procesu. Mějte na paměti, že riziko není omezena pouze na metody, které záměrně poskytují přístup ke zpracování v paměti. je také k dispozici ve všech scénářích, kde škodlivý kód můžete dosáhnout přístup žádným způsobem, například tím, že poskytuje překvapivé, chybný nebo není platný vstup.

 Výchozí zásady zabezpečení neuděluje oprávnění nespravovaného kódu na sestavení, pokud je spuštěn v místním počítači nebo je členem jedné z následujících skupin:

-   Moje skupina počítačů zóny kódu

-   Microsoft Strong Name kódová skupina

-   Skupiny kódu silného názvu ECMA

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pečlivě zkontrolujte kód a ujistěte se, že tento atribut je nezbytně nutné. Pokud nejste obeznámeni s spravovaný kód zabezpečení nebo není srozumitelný bezpečnostních důsledcích pomocí tohoto atributu, odeberte ho z vašeho kódu. Pokud je vyžadován atribut, musíte zajistit, že volající speciálně nemůžete použít kód. Pokud váš kód nemá oprávnění k provedení nespravovaného kódu, tento atribut nemá žádný vliv a měly by se odebrat.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že váš kód neposkytuje volající přístup k nativním operace nebo prostředky použité destruktivním způsobem.

## <a name="example"></a>Příklad
 Následující příklad poruší toto pravidlo.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Příklad
 V následujícím příkladu `DoWork` metoda poskytuje cestu veřejně přístupné kódu do metody vyvolání platformy `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Příklad
 V následujícím příkladu, veřejnou metodu `DoDangerousThing` způsobí, že je porušení pravidel. Chcete-li vyřešit porušení zásad, `DoDangerousThing` třeba privátní a přístup k němu můžete použít veřejnou metodu zabezpečena pomocí požadavku zabezpečení, jak je znázorněno v `DoWork` metody.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Pokyny pro zabezpečené kódování](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [optimalizace zabezpečení](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



