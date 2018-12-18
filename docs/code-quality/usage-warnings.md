---
title: Upozornění využití
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e83421cefd78582c05f20d1efc936ba60c1fc47
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927056"
---
# <a name="usage-warnings"></a>Upozornění využití
Upozornění využití podporovat správné použití rozhraní .NET Framework.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1801: Revize nepoužitých parametrů](../code-quality/ca1801-review-unused-parameters.md)|Podpis metody obsahuje parametr, který není použit v těle metody.|
|[CA1806: Neignorujte výsledky metody](../code-quality/ca1806-do-not-ignore-method-results.md)|Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije.|
|[CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Metoda, která je implementace metody Dispose nevyvolá GC. Funkce SuppressFinalize; nebo volá metodu, která není implementace metody Dispose GC. Funkce SuppressFinalize; nebo volání metod GC. Funkce SuppressFinalize a předává něco jiného než tento (Me v jazyce Visual Basic).|
|[CA2200: Znovu vyvolejte pro zachování podrobností zásobníku](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Výjimka je explicitně zadané v příkazu throw výjimku je znovu. Zadáním výjimky v příkazu throw je znovu vyvolána výjimka, dojde ke ztrátě seznam volání metod mezi původní metoda, která vrátila výjimku a aktuální metoda.|
|[CA2201: Nevyvolávejte vyhrazené typy výjimek](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Díky tomu původní chyba obtížné zjistit a ladění.|
|[CA2202: Neuvolňujte objekty několikrát](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání metody System.IDisposable.Dispose nebo ekvivalentní metody pro uvolnění (například metoda Close() u některých typů) stejného objektu.|
|[CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Řetězcový literál v těle metody obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA2205: Použijte spravované ekvivalenty rozhraní Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Vyvolání platformy metoda je definovaný a metodu s ekvivalentní funkce existuje v knihovně tříd rozhraní .NET Framework.|
|[CA2207: Inicializujte vloženou hodnotu statických polí](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte.|
|[CA2208: Vytvořte správně instance výjimky argumentu](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena.|
|[CA2211: Nekonstantní pole by nemělo být viditelné](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Statická pole, která nejsou konstantami ani nejsou jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k toto pole je třeba pečlivě kontrolovat a vyžaduje pokročilé techniky programování pro synchronizaci přístup k objektu třídy.|
|[CA2212: Neoznačujte obsluhované součásti pomocí WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Metoda v typ, který dědí z System.EnterpriseServices.ServicedComponent označena System.Web.Services.WebMethodAttribute. Protože atribut WebMethodAttribute a metoda ServicedComponent mají konfliktní chování a požadavky na kontext a tok transakcí, bude chování metody v některých případech nesprávné.|
|[CA2213: Uvolnitelné pole by mělo být uvolněno](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu.|
|[CA2214: Nevolejte přepisovatelné metody v konstruktorech](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Když Konstruktor volá virtuální metodu, je možné, že nebyl proveden v konstruktoru pro instanci, která volá metodu.|
|[CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose.|
|[CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typ, který implementuje System.IDisposable a má pole, které naznačují použití nespravovaných prostředků, neimplementuje finalizační metody podle Object.Finalize.|
|[CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Externě viditelné výčet je označena pomocí FlagsAttribute a má jednu nebo více hodnot, které nejsou zajišťuje dvě nebo kombinaci jiné definované hodnoty výčtu.|
|[CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Metoda GetHashCode vrací hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako například tabulku hash. Dva objekty, které jsou stejného typu a jsou stejné, musí vrátit stejnou hodnotu hash.|
|[CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Díky tomu původní chyba obtížné zjistit a ladění.|
|[CA2220: Finalizační metody by měly volat finalizační metodu třídy Base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizační metoda musí být šířena přes hierarchii dědičnosti. Chcete-li to zaručit, musí typy zavolat metodu Finalize své základní třídy ve své vlastní metodě Finalize.|
|[CA2221: Finalizační metody by měly být chráněné](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizační metody musí použít modifikátor přístupu family.|
|[CA2222: Nesnižujte viditelnost zděděného členu](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Modifikátor přístupu byste neměli měnit u zděděných členů. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody.|
|[CA2223: Členy by se měly lišit o více než návratový typ](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Přestože modul CLR (Common Language Runtime) umožňuje používat návratové typy k rozlišení mezi jinak identickými členy, tato funkce není ve specifikaci CLS, ani není běžnou funkcí v programovacích jazycích rozhraní .NET.|
|[CA2224: Přepište Equals při přetížení operátoru rovnosti](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Implementuje operátor rovnosti veřejného typu, ale nemůže přepsat Object.Equals.|
|[CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Člen s názvem alternativní poskytuje přístup ke stejné funkce jako operátor a je k dispozici pro vývojáře, kteří programu v jazycích, které nepodporují přetížené operátory.|
|[CA2226: Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Typ implementuje rovnosti nebo operátor nerovnosti a neimplementuje opačné operátor.|
|[CA2227: Vlastnosti kolekce by měly být pouze pro čtení](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy.|
|[CA2228: Nedodávejte nevydané formáty prostředku](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Soubory prostředků, které byly vytvořené pomocí předprodejní verze rozhraní .NET Framework nemusí být použitelná pro podporované verze rozhraní .NET Framework.|
|[CA2229: Implementovat serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)|Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.|
|[CA2230: Použijte parametry pro proměnné argumenty](../code-quality/ca2230-use-params-for-variable-arguments.md)|Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání VarArgs místo klíčového slova params.|
|[CA2231: Přetižte operátor equals při přepsání ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Hodnotový typ přepisuje metodu Object.Equals, ale neimplementuje operátor rovnosti.|
|[CA2232: Označte vstupní bod modelu Windows Forms pomocí STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Atribut STAThreadAttribute znamená, že model vláken aplikace COM je jednovláknový apartment (STA). Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně.|
|[CA2233: Operace by neměly přetéct](../code-quality/ca2233-operations-should-not-overflow.md)|Aritmetické operace nebude prováděna bez první ověření operandy, abyste měli jistotu, že výsledek operace není mimo rozsah možných hodnot pro typy dat zahrnutých.|
|[CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“.  Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri.|
|[CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Neserializovatelný typ pole instance je deklarován v serializovatelném typu.|
|[CA2236: Volejte metody třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Chcete-li napravit porušení tohoto pravidla, zavolejte metodu GetObjectData základního typu nebo konstruktor serializace z odpovídající metody nebo konstruktoru odvozeného typu.|
|[CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Rozpoznala modul common language runtime jako serializable, musí být typy označen atributem SerializableAttribute i v případě, že typ používá vlastní serializace rutiny prostřednictvím implementace rozhraní ISerializable.|
|[CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost.|
|[CA2239: Poskytujte metody deserializace pro nepovinné pole](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Typ obsahuje pole, která je označena atributem System.Runtime.Serialization.OptionalFieldAttribute a typ neposkytuje zpracování metody deaktivace serializace událostí.|
|[CA2240: Implementujte správně ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)|Opravit porušení toto pravidlo, zajistěte metody GetObjectData viditelné a přepisovatelné a zkontrolujte, že všechna pole instance jsou součástí procesu serializace nebo explicitně označené atributem NonSerializedAttribute.|
|[CA2241: Poskytněte správné argumenty metodě formátování](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Formát argument předaný System.String.Format neobsahuje položku formátu, která odpovídá na všechny argumenty objektu a naopak.|
|[CA2242: Testujte správně NaN](../code-quality/ca2242-test-for-nan-correctly.md)|Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double).|
|[CA2243: Literály řetězce atributu by se měly správně analyzovat](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Parametr literálu řetězce atributu není správně analyzovat adresu URL, identifikátor GUID nebo verzi.|