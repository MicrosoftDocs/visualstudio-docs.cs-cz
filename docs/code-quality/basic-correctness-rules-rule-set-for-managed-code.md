---
title: Sada pravidel Základní pravidla správnosti pro spravovaný kód
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5bbd43b47e104dc775629e0e517ba8c47c2a49ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900627"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Sada pravidel Základní pravidla správnosti pro spravovaný kód
Sada pravidel základní pravidla správnosti se zaměřuje na logických a běžných chyb využití Framework rozhraní API. Základní pravidla správnosti zahrnují pravidla v sadě pravidel minimální doporučená pravidla. Další informace najdete v tématu [sada pravidel spravovaná doporučená pravidla pro spravovaný kód](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) by měla obsahovat toto pravidlo nastavit rozšíření seznam upozornění, že minimální doporučená pravidla sestavy.

 Následující tabulka popisuje všechna pravidla v sadě pravidel základní pravidla správnosti společnosti Microsoft.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, které vlastní uvolnitelné pole by měly být uvolnitelné|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Označte sestavení pomocí atributu AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody rozhraní by měla být volatelné podřízenými typy|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, které vlastní nativní prostředky by měly být uvolnitelné|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Přesunout P/vyvolá do třídy NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Neskrývejte metody třídy base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementujte správně IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Není vyvolání výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Vstupní body P/Invoke by měla existovat.|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/by neměla být viditelné|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Volejte GetLastError ihned po P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Deklarujte správně|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Odstraňte prázdné finalizační metody|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Typ pole hodnot by měla být přenosná|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarace P/Invoke by měla být přenosná|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nepoužívejte zámky na objekty se slabou identitou|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Zkontrolujte dotazy SQL pro chyby zabezpečení|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Určete kódování pro argumenty řetězce P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Zkontrolujte deklarativní zabezpečení u typů hodnot|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Ukazatelé by neměli být viditelné|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpečení metody by měla být nadmnožinou typu|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA by měl rozšířit pouze základní typy APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nevystavujte nepřímo metody s požadavky propojení|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Požadavky na přepsání odkazu musí být identické s bází|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Zabalte ohroženou finally do vnějšího bloku try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Požadavky propojení typů vyžadují dědičnost požadavků|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy kritické pro zabezpečení nemusejí podporovat účast na ekvivalenci typů|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Výchozí konstruktory nesmějí být kritické jako výchozí konstruktory základního typu|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegáti musí vytvořit vazbu k metodám s konzistentní transparentností|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody musí při přepisování základních metod zachovávat konzistentní transparentnost|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparentní metody musejí obsahovat pouze ověřitelné IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparentní metody nesmějí volat metody s atributem suppressunmanagedcodesecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparentní metody nesmějí vyhovovat LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparentní metody nemusejí podporovat použití zabezpečení vyhodnotí|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparentní metody nesmějí provádět volání do nativního kódu|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Znovu vyvolejte pro zachování podrobností zásobníku|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Neodstraňovat objekty více než jednou.|
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
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Typy označit ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementujte správně metody serializace|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementujte správně ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Poskytněte správné argumenty metodě formátování|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testujte správně NaN|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Výčty by měly mít nulovou hodnotu|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Přetížení operátoru rovnosti na přetížení sčítání a odečítání|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nepředávejte literály jako lokalizované parametry|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizujte řetězce na velká písmena|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Neignorujte výsledky metody|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Volání GC. Funkce SuppressFinalize správně|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Vlastnosti by neměly vracet pole|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testujte prázdné řetězce pomocí délky řetězce|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Použijte pouze API z cílové rozhraní|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Odeberte volání do globálního katalogu. Funkce KeepAlive|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Použijte SafeHandle pro zapouzdření nativních prostředků|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Zachycení výjimky bez CLSCompliant v obecné obslužné rutiny|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nedeklarujte čtení pouze proměnlivé odkazové typy|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Pole polí by neměly jen pro čtení|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Zabezpečené vyhodnotí|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Volání GC. KeepAlive při použití nativních zdrojů|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Zapečeťte metody, které vyhovují privátním rozhraním|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpečte Serializační konstruktory|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statické konstruktory by měly být privátní|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Konstanty kritické pro zabezpečení musejí být transparentní|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Použijte spravované ekvivalenty rozhraní Win32 API|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Metody Dispose by měly volat uvolnění třídy base|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizační metody by měly být chráněné.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nesnižujte viditelnost zděděného členu|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Členy by se měly lišit o více než návratový typ|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Přepište equals při přetížení operátoru rovnosti|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operátory by měly mít symetrické přetížení|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Vlastnosti kolekce by měl jen pro čtení|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Poskytují metody deserializace pro nepovinné pole|