---
title: Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 66c67c9c1a395c0684567acfed78c207422b59ba
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31902269"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód
Můžete použít sadu a zaměřit se na snadněji pochopit a používat váš kód pravidel základní pravidla obecných zásad návrhu společnosti Microsoft. Toto pravidlo nastavte, pokud projekt obsahuje kód knihovny, nebo pokud chcete vynutit osvědčené postupy pro kód, který se snadnou údržbou by měla obsahovat.

 Základní pravidla obecných zásad návrhu zahrnují všechna pravidla v sadě pravidel Microsoft minimální Recommeded pravidla. Seznam minimální pravidla najdete v tématu [sada pravidel spravovaná doporučená pravidla pro spravovaný kód](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).

 Následující tabulka popisuje všechna pravidla v sadě pravidel základní pravidla obecných zásad návrhu společnosti Microsoft.

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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Nedeklarujte statické členy v obecných typech|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Nevystavujte obecné seznamy|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Použít obecné události instance obslužné rutiny|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Obecné metody by měly poskytnout parametr typu|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Vyhněte se nadbytečným parametrům na obecných typech|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Nevnořujte obecné typy v signaturách členu|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Použijte obecné typy, kde je to vhodné|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Výčty by měly mít nulovou hodnotu|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Kolekce musí implementovat obecné rozhraní|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Zvažte předání základních typů jako parametrů|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Abstraktní typy by neměly mít konstruktory|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Přetížení operátoru rovnosti na přetížení sčítání a odečítání|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Označte sestavení pomocí atributu CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Označte sestavení pomocí atributu ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Označte atributy pomocí AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Definujte přístupové objekty pro argumenty atributu|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indexery by neměly být multidimenzionální|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Použití vlastností, kde je to vhodné|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Nahraďte opakované argumenty parametry pole|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Výchozí parametry by se neměla používat.|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Označte výčty pomocí FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Úložiště výčtu by měl být Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Používání událostí, kde je to vhodné|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Není catch nezachycujte výjimky obecného typu|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementujte standardní konstruktory výjimky|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Vnořené typy by neměly být viditelné|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Implementace ICollection mají členy silného typu|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Přepište metody srovnatelných typů|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Enumerátory by měly být silného typu|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Seznamy jsou silného typu|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Poskytněte zprávu ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Použijte celočíselný nebo řetězcový argument pro indexery|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Vlastnosti by neměly být pouze pro zápis|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Nepřetěžujte operátor rovnosti na odkazových typech|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Nedeklarujte chráněné členy v zapečetěných typech|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Nedeklarujte virtuální členy v zapečetěných typech|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Deklarujte typy v oborech názvů|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Nedeklarujte viditelná pole instance|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Statický vlastník typů by měl být zapečetěný|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Statický vlastník typů by neměly mít konstruktory|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parametry identifikátoru URI by neměly být řetězce|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Identifikátor URI návratové hodnoty by neměly být řetězce|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Vlastnosti identifikátoru URI by neměly být řetězce|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Volání řetězec přetížení identifikátoru URI volá přetížení System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Typy by neměly rozšířit určité základní typy|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Členové by neměli zveřejňovat určité konkrétní typy|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Výjimky by měly být veřejné|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Názvy proměnných by neměly odpovídat názvům polí|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Vyhněte se nadměrné složitosti|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identifikátory by se měly lišit o více než případu|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Identifikátory by neměly odpovídat klíčová slova|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Zkontrolujte nepoužité parametry|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Odeberte nepoužívané místní hodnoty|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Vyhněte se nadměrným|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inicializace odkazový typ statického pole vloženě|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Vyhněte se nevolanému místnímu kódu|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Vyhněte se nevytvořeným interní třídy|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Vyhněte se nezapečetěným atributům|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Dáváte přednost Vícenásobná pole více než multidimenzionální|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Přepište rovná se a operátor rovnosti na hodnotových typech|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Vlastnosti by neměly vracet pole|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testujte prázdné řetězce pomocí délky řetězce|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Označte členy jako statické|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Vyhněte se nepoužitým privátním polím|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Není vyvolat vyhrazené typy výjimek|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Použijte spravované ekvivalenty rozhraní Win32 API|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Vytvoření správně instance výjimky argumentu|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Nekonstantní pole by neměly být viditelné|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Neoznačujte výčty pomocí FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Není vyvolání výjimky v klauzulích výjimky|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizační metody by měly být chráněné.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nesnižujte viditelnost zděděného členu|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Členy by se měly lišit o více než návratový typ|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Přepište equals při přetížení operátoru rovnosti|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Přetížení operátoru mají pojmenované alternativy|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operátory by měly mít symetrické přetížení|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Vlastnosti kolekce by měl jen pro čtení|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Použijte parametry pro proměnné argumenty|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Předejte objekty System.Uri namísto řetězců|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Poskytují metody deserializace pro nepovinné pole|