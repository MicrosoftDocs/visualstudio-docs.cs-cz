---
title: Nastavení pravidel rozšířená pravidla správnosti pro spravovaný kód | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cebb3f492bb3aec873f503c2efcacb7220ec9739
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187421"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Sada pravidel Rozšířená pravidla správnosti pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada pravidel Microsoftu rozšířená pravidla správnosti maximalizuje logiku a framework chyby využití, které jsou hlášeny sadou analýzy kódu. Je kladen zvláštní důraz na konkrétní scénáře, jako je například interoperabilita modelů COM a mobilní aplikace. Měli byste zvážit, včetně toto pravidlo nastavte, pokud jeden z těchto scénářů vztahuje k vašemu projektu nebo pro nalezení dalších problémů ve vašem projektu.  
  
 Sada pravidel Microsoftu rozšířená pravidla správnosti obsahuje pravidla, která jsou v pravidel základní pravidla správnosti společnosti Microsoft nastavit. Základní pravidla správnosti obsahovat pravidla, která jsou v pravidle Microsoft Minimální doporučená pravidla nastavena. Další informace najdete v části [sada pravidel základní pravidla správnosti pro spravovaný kód](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) a [sada pravidel spravovaná doporučená pravidla pro spravovaný kód](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)  
  
 Následující tabulka popisuje všechna pravidla v sadě pravidel Microsoftu rozšířená pravidla správnosti.  
  
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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Výčty by měly mít nulovou hodnotu|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Přetižte operátor rovnosti při přetížení operátorů sčítání a odečítání|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nepředávejte literály jako lokalizované parametry|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizujte řetězce na velká písmena|  
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Neignorujte výsledky metody|  
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Volání uvolňování paměti. SuppressFinalize správně|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Vlastnosti by neměly vracet pole|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testujte prázdné řetězce pomocí délky řetězce|  
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Použijte pouze API z cíleného rozhraní|  
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Odeberte volání uvolňování paměti. KeepAlive|  
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Použijte SafeHandle pro zapouzdření nativních prostředků|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Zachycujte výjimky bez CLSCompliant v obecné obslužné rutině|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nedeklarujte čtení proměnlivé odkazové typy pouze|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Pole polí by neměly být pouze pro čtení|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Zabezpečte nepodmíněné výrazy|  
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Volání uvolňování paměti. KeepAlive při použití nativních zdrojů|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Zapečeťte metody, které vyhovují privátním rozhraním|  
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpečte Serializační konstruktory|  
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statické konstruktory by měly být privátní|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Konstanty kritické pro zabezpečení musejí být transparentní|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Použijte spravované ekvivalenty rozhraní Win32 API|  
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Metody Dispose by měly volat uvolnění třídy base|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizační metody by měly být chráněné|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nesnižujte viditelnost zděděného členu|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Členy by se měly lišit o více než návratový typ|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Přepište equals při přetížení operátoru rovnosti|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operátory by měly mít symetrické přetížení|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Vlastnosti kolekce by měly být jen pro čtení|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Poskytujte metody deserializace pro nepovinné pole|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementujte standardní konstruktory výjimky|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parametry identifikátoru URI by neměly být řetězce|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Identifikátor URI návratové hodnoty by neměly být řetězce|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Vlastnosti identifikátoru URI by neměly být řetězce|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Volání řetězcové přetížení identifikátoru URI volá přetížení System.Uri|  
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Vyhněte se přetížení ve viditelných rozhraních modelu COM|  
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6|  
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Vyhněte se statickým členům ve viditelných typech modelu COM|  
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Nepoužívejte AutoDual ClassInterfaceType|  
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Viditelné typy modelu COM by měly být vytvořitelné|  
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metody registrace modelu COM by neměly být viditelné|  
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Označte rozhraní ComSource jako IDispatch|  
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Vyhněte se neveřejným polím v hodnotách viditelných modelu COM|  
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Označte logické argumenty volání nespravovaného kódu pomocí MarshalAs|  
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nepoužívejte prioritu nečinného procesu|  
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Nepoužívejte časovače, které zabraňují změně stavu napájení|  
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Označte sestavení pomocí atributu NeutralResourcesLanguageAttribute|  
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Vyhněte se volání problematických metod|  
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Rozlišujte vlákénka od vláken|  
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Sestavení úrovně 2 nesmějí obsahovat LinkDemands|  
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Členy nesmějí mít konfliktní poznámky transparentnosti|  
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparentní metody nemusejí podporovat použití atributu HandleProcessCorruptingExceptions|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Transparentní kód nemůže být chráněn pomocí LinkDemands|  
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparentní metody nemohou používat požadavky zabezpečení|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Transparentní kód nesmí načítat sestavení z bajtových polí|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparentní metody nesmějí být doplněny pomocí SuppressUnmanagedCodeSecurityAttribute|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Literály by měly být zadány správně|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Nekonstantní pole by nemělo být viditelné|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Neoznačujte výčty pomocí FlagsAttribute|  
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Přepište GetHashCode při přepsání Equals|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Nevyvolávejte výjimky v klauzulích výjimky|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Přetížení operátoru mají pojmenované alternativy|  
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Nedodávejte nevydané formáty prostředku|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Použijte parametry pro proměnné argumenty|  
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Operace by neměly přetéct|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Předejte objekty System.Uri namísto řetězců|  
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Literály řetězce atributu by se měly správně analyzovat|



