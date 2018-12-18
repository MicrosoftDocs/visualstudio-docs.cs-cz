---
title: Sada pravidel spravovaná doporučená pravidla pro spravovaný kód | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 33c35304643d0743b5da53a75cae9a01125b7da6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296098"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Sada pravidel Spravovaná doporučená pravidla pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít doporučená pravidla spravované Microsoft sadu pravidel, která se soustředí na nejdůležitější problémy v spravovaného kódu, včetně možných bezpečnostních děr, selhání aplikace a jiných důležitých chyb logiky a návrhu. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše projekty.  
  
|Pravidlo|Popis|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, které vlastní uvolnitelné pole by měly být uvolnitelné|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Deklarujte správně obslužné rutiny událostí|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Označte sestavení pomocí atributu AssemblyVersionAttribute|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody rozhraní by měla být volatelné podřízenými typy|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, které vlastní nativní prostředky by měly být uvolnitelné|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Neskrývejte metody třídy base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementuje správně IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Nevyvolávejte výjimky v neočekávaných umístěních|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Vyhněte se duplicitním akcelerátorům|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Vstupní body volání nespravovaného by měly existovat|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Volání nespravovaných kódů by neměly být viditelné|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy automatického rozložení by neměly být viditelné modelu COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Volejte GetLastError ihned po volání nespravovaného kódu|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody registrace modelu COM by si měly odpovídat|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Deklarujte správně volání nespravovaných kódů|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Odstraňte prázdné finalizační metody|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Pole hodnot by měla být přenosná|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarace volání nespravovaného kódu by měla být přenosná|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nepoužívejte zámky na objekty se slabou identitou|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Zkontrolujte dotazy SQL pro chyby zabezpečení|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Určete zařazování pro argumenty řetězce volání nespravovaného|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revize deklarativních zabezpečení na hodnotách|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Ukazatelé by neměli být viditelné|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpečené typy by neměly vystavovat pole|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpečení metody by mělo být nadmnožinou typu|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody APTCA by měly volat pouze metody APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA by měl rozšířit pouze základní typy APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nezveřejňujte nepřímo metody s požadavky propojení|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Požadavky na přepsání odkazu musejí být identické s bází|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Zabalte ohroženou klauzuli finally do vnějšího bloku try|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Požadavky propojení typů vyžadují dědičnost požadavků|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy kritické pro zabezpečení nemusejí podporovat účast na ekvivalenci typů|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Výchozí konstruktory nesmějí být kritické jako výchozí konstruktory základního typu|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegáti musí mít vazbu k metodám s konzistentní transparentností|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody musejí při přepisování základních metod zachovávat konzistentní transparentnost|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparentní metody musejí obsahovat pouze ověřitelné IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparentní metody nesmějí volat metody s atributem suppressunmanagedcodesecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparentní metody nesmějí vyhovovat LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy musí být alespoň tak kritický jako jeho základní typy a rozhraní|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparentní metody nemusejí podporovat použití zabezpečení nepodmíněné výrazy|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparentní metody nesmějí provádět volání do nativního kódu|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Znovu vyvolejte pro zachování podrobností zásobníku|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Neuvolňujte objekty několikrát|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializujte vloženou hodnotu statických polí|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Neoznačujte obsluhované součásti pomocí WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Uvolnitelné pole by mělo být uvolněno|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Nevolejte přepisovatelné metody v konstruktorech|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Uvolnitelné typy by měly deklarovat finalizační metodu|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizační metody by měly volat finalizační metodu třídy base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementovat Serializační konstruktory|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Přetižte operátor equals při přepsání ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Vstupní body označit Windows Forms pomocí STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Označte všechna neserializovatelná pole|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Volání metody třídy base na typech ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Označte typy ISerializable pomocí SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementujte správně metody serializace|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementujte správně ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Poskytněte správné argumenty metodě formátování|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testujte správně NaN|



