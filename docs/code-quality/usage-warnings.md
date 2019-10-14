---
title: Upozornění využití
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305684"
---
# <a name="usage-warnings"></a>Upozornění využití

Upozornění použití podporují správné použití .NET.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1801: Zkontrolovat nepoužité parametry @ no__t-0|Podpis metody obsahuje parametr, který není použit v těle metody.|
|[CA1806: Neignorujte výsledky metody @ no__t-0.|Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije.|
|[CA1816: Vyvolejte GC. SuppressFinalize správně @ no__t-0|Metoda, která je implementací metody Dispose, nevolá uvolňování paměti. SuppressFinalize; nebo uvolňování paměti volá metodu, která není implementací metody Dispose. SuppressFinalize; nebo volání metody GC. SuppressFinalize a předává něco jiného (Me v jazyce Visual Basic).|
|[CA2200: Znovu vyvolat pro zachování podrobností zásobníku @ no__t-0|Výjimka je znovu vyvolána a je jednoznačně uvedena v příkazu throw. Jestliže je výjimka znovu vyvolána zadáním výjimky v příkazu throw, seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztracen.|
|[CA2201: Nevyvolávání rezervovaných typů výjimek @ no__t-0|Tím je původní chybě obtížné detekovat a ladit.|
|[CA2202: Neodstraňujte objekty víckrát @ no__t-0|Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání metody System.IDisposable.Dispose nebo ekvivalentní metody pro uvolnění (například metoda Close() u některých typů) stejného objektu.|
|[CA2204: Literály by měly být zadány správně @ no__t-0|Řetězcový literál v těle metody obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA2205: Použít spravované ekvivalenty Win32 API @ no__t-0|Metoda Invoke platformy je definována a k dispozici je metoda .NET s ekvivalentními funkcemi.|
|[CA2207: Inicializovat typ hodnoty statických polí s vložením @ no__t-0|Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte.|
|@NO__T – 0CA2208: Vytváření instancí výjimek argumentu správně @ no__t-0|Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena.|
|[CA2211: Nekonstantní pole by nemělo být viditelné @ no__t-0|Statická pole, která nejsou konstanta nebo jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy.|
|[CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod @ no__t-0|Metoda v typu, který dědí z typu System. EnterpriseServices. ServicedComponent, je označená atributem System. Web. Services. atributu WebMethodAttribute. Protože atribut WebMethodAttribute a metoda ServicedComponent mají konfliktní chování a požadavky na kontext a tok transakcí, bude chování metody v některých případech nesprávné.|
|[CA2213: Pole na jedno použití by mělo být uvolněno @ no__t-0|Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu.|
|[CA2214: Nevolejte přepsatelné metody v konstruktorech @ no__t-0|Když konstruktor volá virtuální metodu, je možné, že konstruktor instance, která volá metodu, není proveden.|
|[CA2215: Metody Dispose by měly volat Dispose třídy Base @ no__t-0|Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose.|
|[CA2216: Typy na jedno použití by měly deklarovat finalizační metodu @ no__t-0.|Typ, který implementuje System. IDisposable a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno v Object. Finalize.|
|[CA2217: Neoznačujte výčty pomocí FlagsAttribute @ no__t-0|Externě viditelný výčet je označen atributem FlagsAttribute a má jednu nebo více hodnot, které nejsou mocninou dvou nebo kombinaci dalších definovaných hodnot výčtu.|
|[CA2218: Přepsat GetHashCode při přepsání rovnosti @ no__t-0|Metoda GetHashCode vrací hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako například tabulku hash. Dva objekty, které jsou stejného typu a jsou stejné, musí vrátit stejnou hodnotu hash.|
|@NO__T – 0CA2219: Nevyvolávání výjimek v klauzulích výjimky @ no__t-0|Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Tím je původní chybě obtížné detekovat a ladit.|
|[CA2220: Finalizační metody by měly volat finalizační metodu třídy Base @ no__t-0|Finalizační metoda musí být šířena přes hierarchii dědičnosti. Chcete-li to zaručit, musí typy zavolat metodu Finalize své základní třídy ve své vlastní metodě Finalize.|
|[CA2221: Finalizační metody by měly být chráněné @ no__t-0|Finalizační metody musí použít modifikátor přístupu family.|
|@NO__T – 0CA2222: Nezmenšení děděné viditelnosti členů @ no__t-0|Neměňte modifikátor přístupu pro zděděné členy. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody.|
|[CA2223: Členy by se měly lišit o více než návratový typ @ no__t-0.|Přestože modul CLR (Common Language Runtime) umožňuje používat návratové typy k rozlišení mezi jinak identickými členy, tato funkce není ve specifikaci CLS, ani není běžnou funkcí v programovacích jazycích rozhraní .NET.|
|[CA2224: Přepište Equals při přetížení operátoru rovnosti @ no__t-0|Veřejný typ implementuje operátor rovnosti, ale nepřepisuje Object. Equals.|
|[CA2225: Přetížení operátoru mají pojmenované alternativy @ no__t-0|Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích, které nepodporují přetížené operátory.|
|@NO__T – 0CA2226: Operátory by měly mít symetrické přetížení @ no__t-0.|Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor.|
|[CA2227: Vlastnosti kolekce by měly být jen pro čtení @ no__t-0|Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy.|
|@NO__T – 0CA2228: Nedodá neuvolníelné formáty prostředků @ no__t-0|Soubory prostředků, které byly vytvořeny pomocí předprodejní verze rozhraní .NET, nemusí být použitelné pro podporované verze rozhraní .NET.|
|[CA2229: Implementovat konstruktory serializace @ no__t-0|Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.|
|[CA2230: Použijte parametry pro proměnné argumenty @ no__t-0|Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání VarArgs místo klíčového slova params.|
|[CA2231: Operátor přetížení se rovná přetížení ValueType. Equals @ no__t-0|Hodnotový typ přepisuje `Object.Equals`, ale neimplementuje operátor rovnosti.|
|[CA2232: Označit model Windows Forms vstupními body pomocí STAThread @ no__t-0|Atribut STAThreadAttribute znamená, že model vláken aplikace COM je jednovláknový apartment (STA). Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně.|
|[CA2233: Operace by neměly přetečení @ no__t-0.|Aritmetické operace by se neměly provádět bez prvotního ověření operandů, aby se zajistilo, že výsledek operace není mimo rozsah možných hodnot datových typů, které se týkají.|
|[CA2234: Předejte objekty System. URI místo řetězců @ no__t-0.|Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“.  Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri.|
|[CA2235: Označte všechna Neserializovatelný pole @ no__t-0|Neserializovatelný typ pole instance je deklarován v serializovatelném typu.|
|[CA2236: Volejte metody základní třídy na typech ISerializable @ no__t-0|Chcete-li napravit porušení tohoto pravidla, zavolejte metodu GetObjectData základního typu nebo konstruktor serializace z odpovídající metody nebo konstruktoru odvozeného typu.|
|[CA2237: Označte typy ISerializable pomocí SerializableAttribute @ no__t-0.|Aby je bylo možné rozpoznat modulem CLR (Common Language Runtime) jako serializovatelný, typy musí být označeny atributem SerializableAttribute i v případě, že typ používá vlastní rutinu serializace prostřednictvím implementace rozhraní ISerializable.|
|[CA2238: Implementujte správně metody serializace @ no__t-0|Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost.|
|[CA2239: Poskytněte metody deserializace pro volitelná pole @ no__t-0|Typ obsahuje pole, které je označeno atributem System. Runtime. Serialization. OptionalFieldAttribute a typ neposkytuje metody zpracování událostí pro deserializaci.|
|[CA2240: Implementace ISerializable správně @ no__t-0|Chcete-li opravit porušení tohoto pravidla, zajistěte, aby byla metoda GetObjectData viditelná a Overridable, a ujistěte se, že všechna pole instance jsou zahrnuta do procesu serializace nebo explicitně označena atributem NonSerializedAttribute.|
|[CA2241: Poskytněte správné argumenty pro metody formátování @ no__t-0|Argument formátu předaný metodě System. String. Format neobsahuje položku formátu, která by odpovídala každému argumentu objektu, nebo naopak.|
|[CA2242: Test pro správně NaN @ no__t-0|Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double).|
|[CA2243: Řetězcové literály atributu by se měly správně analyzovat @ no__t-0|Parametr řetězcového literálu atributu se neanalyzuje správně pro adresu URL, identifikátor GUID nebo verzi.|