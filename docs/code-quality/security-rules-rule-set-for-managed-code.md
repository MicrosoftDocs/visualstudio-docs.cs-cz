---
title: Sada pravidel Pravidla zabezpečení pro spravovaný kód
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6712454fad2acaf57b3cb4d8f1740366a396ec6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925039"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla zabezpečení pro spravovaný kód
Sada co nejvíce možné problémy zabezpečení, které jsou hlášeny pravidel pravidla zabezpečení Microsoft by měla obsahovat.

|Pravidlo|Popis|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Zkontrolujte dotazy SQL pro chyby zabezpečení|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Zachycení výjimky bez CLSCompliant v obecné obslužné rutiny|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Revize naléhavého zabezpečení|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nedeklarujte čtení pouze proměnlivé odkazové typy|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Pole polí by neměly jen pro čtení|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Zabezpečené vyhodnotí|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Zkontrolujte použití Odepřít a pouze povolit|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Zkontrolujte deklarativní zabezpečení u typů hodnot|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Zkontrolujte viditelné obslužné rutiny událostí|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Ukazatelé by neměli být viditelné|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpečení metody by měla být nadmnožinou typu|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Volání GC. KeepAlive při použití nativních zdrojů|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA by měl rozšířit pouze základní typy APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Zkontrolujte použití SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Zapečeťte metody, které vyhovují privátním rozhraním|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpečte Serializační konstruktory|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statické konstruktory by měly být privátní|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nevystavujte nepřímo metody s požadavky propojení|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Požadavky na přepsání odkazu musí být identické s bází|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Zabalte ohroženou finally do vnějšího bloku try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Požadavky propojení typů vyžadují dědičnost požadavků|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Konstanty kritické pro zabezpečení musejí být transparentní|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy kritické pro zabezpečení nemusejí podporovat účast na ekvivalenci typů|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Výchozí konstruktory nesmějí být kritické jako výchozí konstruktory základního typu|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegáti musí vytvořit vazbu k metodám s konzistentní transparentností|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody musí při přepisování základních metod zachovávat konzistentní transparentnost|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Sestavení úrovně 2 nesmějí obsahovat LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Členy nesmějí mít konfliktní poznámky transparentnosti|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparentní metody musejí obsahovat pouze ověřitelné IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparentní metody nesmějí volat metody s atributem suppressunmanagedcodesecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparentní metody nemusejí podporovat použití atributu HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparentní metody nesmějí vyhovovat LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Transparentní kód nemůže být chráněn pomocí LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparentní metody nemohou používat požadavky zabezpečení|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Transparentní kód nesmí načítat sestavení z bajtových polí|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparentní metody nesmějí být doplněny pomocí SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparentní metody nemusejí podporovat použití zabezpečení vyhodnotí|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparentní metody nesmějí provádět volání do nativního kódu|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Sestavení by měly mít platné silné názvy|