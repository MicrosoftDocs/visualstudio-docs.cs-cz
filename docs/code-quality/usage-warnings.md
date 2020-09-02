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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66d78988ef70e4f991dd02cb16a164cbf48e55f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176075"
---
# <a name="usage-warnings"></a>Upozornění využití

Upozornění použití podporují správné použití .NET.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801.md)|Podpis metody obsahuje parametr, který není použit v těle metody.|
|[CA1806: Neignorujte výsledky metody](../code-quality/ca1806.md)|Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije.|
|[CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816.md)|Metoda, která je implementací metody Dispose, nevolá GC. SuppressFinalize nebo metoda, která není implementací volání Dispose, volá GC. SuppressFinalize nebo metoda volá GC. SuppressFinalize a projde něco jiného než to (já v Visual Basic).|
|[CA2200: Znovu vyvolejte pro zachování podrobností zásobníku](../code-quality/ca2200.md)|Výjimka je znovu vyvolána a je jednoznačně uvedena v příkazu throw. Jestliže je výjimka znovu vyvolána zadáním výjimky v příkazu throw, seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztracen.|
|[CA2201: Nevyvolávejte vyhrazené typy výjimek](../code-quality/ca2201.md)|Tím je původní chybě obtížné detekovat a ladit.|
|[CA2202: Neuvolňujte objekty několikrát](../code-quality/ca2202.md)|Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání metody System.IDisposable.Dispose nebo ekvivalentní metody pro uvolnění (například metoda Close() u některých typů) stejného objektu.|
|[CA2204: Literály by měly být zadány správně](../code-quality/ca2204.md)|Řetězcový literál v těle metody obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA2205: Použijte spravované ekvivalenty rozhraní Win32 API](../code-quality/ca2205.md)|Metoda Invoke platformy je definována a k dispozici je metoda .NET s ekvivalentními funkcemi.|
|[CA2207: Inicializujte statická pole s typem hodnoty vloženě](../code-quality/ca2207.md)|Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte.|
|[CA2208: Vytvořte správně instance výjimky argumentu](../code-quality/ca2208.md)|Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena.|
|[CA2211: Nekonstantní pole by neměla být viditelná](../code-quality/ca2211.md)|Statická pole, která nejsou konstanta nebo jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy.|
|[CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod](../code-quality/ca2212.md)|Metoda v typu, který dědí z typu System. EnterpriseServices. ServicedComponent, je označená atributem System. Web. Services. atributu WebMethodAttribute. Protože atribut WebMethodAttribute a metoda ServicedComponent mají konfliktní chování a požadavky na kontext a tok transakcí, bude chování metody v některých případech nesprávné.|
|[CA2213: Uvolnitelná pole by měla být uvolněna](../code-quality/ca2213.md)|Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu.|
|[CA2214: Nevolejte přepisovatelné metody v konstruktorech](../code-quality/ca2214.md)|Když konstruktor volá virtuální metodu, je možné, že konstruktor instance, která volá metodu, není proveden.|
|[CA2215: Metody Dispose by měly volat uvolnění základní třídy](../code-quality/ca2215.md)|Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose.|
|[CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216.md)|Typ, který implementuje System. IDisposable a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno v Object. Finalize.|
|[CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217.md)|Externě viditelný výčet je označen atributem FlagsAttribute a má jednu nebo více hodnot, které nejsou mocninou dvou nebo kombinaci dalších definovaných hodnot výčtu.|
|[CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218.md)|Metoda GetHashCode vrací hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako například tabulku hash. Dva objekty, které jsou stejného typu a jsou stejné, musí vrátit stejnou hodnotu hash.|
|[CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219.md)|Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Tím je původní chybě obtížné detekovat a ladit.|
|[CA2220: Finalizační metody by měly volat finalizační metodu základní třídy](../code-quality/ca2220.md)|Finalizační metoda musí být šířena přes hierarchii dědičnosti. Chcete-li to zaručit, musí typy zavolat metodu Finalize své základní třídy ve své vlastní metodě Finalize.|
|[CA2221: Finalizační metody by měly být chráněné](../code-quality/ca2221.md)|Finalizační metody musí použít modifikátor přístupu family.|
|[CA2222: Nesnižujte viditelnost zděděného členu](../code-quality/ca2222.md)|Neměňte modifikátor přístupu pro zděděné členy. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody.|
|[CA2223: Členy by se měly lišit více než návratovým typem](../code-quality/ca2223.md)|Přestože modul CLR (Common Language Runtime) umožňuje používat návratové typy k rozlišení mezi jinak identickými členy, tato funkce není ve specifikaci CLS, ani není běžnou funkcí v programovacích jazycích rozhraní .NET.|
|[CA2224: Přepište Equals při přetížení operátoru rovnosti](../code-quality/ca2224.md)|Veřejný typ implementuje operátor rovnosti, ale nepřepisuje Object. Equals.|
|[CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225.md)|Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích, které nepodporují přetížené operátory.|
|[CA2226: Operátory by měly mít symetrická přetížení](../code-quality/ca2226.md)|Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor.|
|[CA2227: Vlastnosti kolekce by měly být pouze pro čtení](../code-quality/ca2227.md)|Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy.|
|[CA2228: Nedodávejte nevydané formáty prostředku](../code-quality/ca2228.md)|Soubory prostředků, které byly vytvořeny pomocí předprodejní verze rozhraní .NET, nemusí být použitelné pro podporované verze rozhraní .NET.|
|[CA2229: Implementujte serializační konstruktory](../code-quality/ca2229.md)|Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.|
|[CA2230: Použijte parametry pro proměnné argumenty](../code-quality/ca2230.md)|Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání VarArgs místo klíčového slova params.|
|[CA2231: Přetižte operátor rovnosti při přetížení ValueType.Equals](../code-quality/ca2231.md)|Hodnotový typ přepisuje, `Object.Equals` ale neimplementuje operátor rovnosti.|
|[CA2232: Označte vstupní body modelu Windows Forms pomocí STAThread](../code-quality/ca2232.md)|Atribut STAThreadAttribute znamená, že model vláken aplikace COM je jednovláknový apartment (STA). Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně.|
|[CA2233: Operace by neměly přetéct](../code-quality/ca2233.md)|Aritmetické operace by se neměly provádět bez prvotního ověření operandů, aby se zajistilo, že výsledek operace není mimo rozsah možných hodnot datových typů, které se týkají.|
|[CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234.md)|Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“.  Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri.|
|[CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235.md)|Neserializovatelný typ pole instance je deklarován v serializovatelném typu.|
|[CA2236: Volejte metody základní třídy u typů ISerializable](../code-quality/ca2236.md)|Chcete-li napravit porušení tohoto pravidla, zavolejte metodu GetObjectData základního typu nebo konstruktor serializace z odpovídající metody nebo konstruktoru odvozeného typu.|
|[CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237.md)|Aby je bylo možné rozpoznat modulem CLR (Common Language Runtime) jako serializovatelný, typy musí být označeny atributem SerializableAttribute i v případě, že typ používá vlastní rutinu serializace prostřednictvím implementace rozhraní ISerializable.|
|[CA2238: Implementujte správně metody serializace](../code-quality/ca2238.md)|Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost.|
|[CA2239: Zadejte metody deserializace pro nepovinná pole](../code-quality/ca2239.md)|Typ obsahuje pole, které je označeno atributem System. Runtime. Serialization. OptionalFieldAttribute a typ neposkytuje metody zpracování událostí pro deserializaci.|
|[CA2240: Implementujte správně ISerializable](../code-quality/ca2240.md)|Chcete-li opravit porušení tohoto pravidla, zajistěte, aby byla metoda GetObjectData viditelná a Overridable, a ujistěte se, že všechna pole instance jsou zahrnuta do procesu serializace nebo explicitně označena atributem NonSerializedAttribute.|
|[CA2241: Zadejte správné argumenty pro metody formátování](../code-quality/ca2241.md)|Argument formátu předaný metodě System. String. Format neobsahuje položku formátu, která by odpovídala každému argumentu objektu, nebo naopak.|
|[CA2242: Testujte správně NaN](../code-quality/ca2242.md)|Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double).|
|[CA2243: Řetězcové literály atributů by se měly správně parsovat](../code-quality/ca2243.md)|Parametr řetězcového literálu atributu se neanalyzuje správně pro adresu URL, identifikátor GUID nebo verzi.|
|[CA2244: Neduplikujte inicializace indexovaných elementů.](../code-quality/ca2244.md)|Inicializátor objektu má více než jeden inicializátor indexovaného elementu se stejným indexem konstanty. Všechny kromě posledního inicializátoru jsou redundantní.|
|[CA2245: Nepřiřazujte vlastnost k ní samotné.](../code-quality/ca2245.md)|Vlastnost byla omylem přiřazena sama sobě.|
|[CA2246: Nepřiřazujte symbol a jeho člena v témže příkazu.](../code-quality/ca2246.md)|Přiřazení symbolu a jeho členu, tedy pole nebo vlastnost, ve stejném příkazu není doporučeno. Není jasné, jestli má členský přístup za cíl použít starou hodnotu symbolu před přiřazením nebo novou hodnotou z přiřazení v tomto prohlášení.|
|[CA2247: Argument předaný konstruktoru TaskCompletionSource by měl být výčet TaskCreationOptions, nikoli výčet TaskContinuationOptions](../code-quality/ca2246.md)|TaskCompletionSource má konstruktory, které přijímají parametr TaskCreationOptions, které ovládají podkladovou úlohu a konstruktory, které přijímají stav objektu, který je uložen v úloze.  Náhodné předání typ TaskContinuationOptions namísto parametr TaskCreationOptions způsobí, že volání zpracuje možnosti jako stav.|
|[CA2248: Zadejte správný argument enum pro Enum. HasFlag.](../code-quality/ca2248.md)|Typ výčtu předaný jako argument pro `HasFlag` volání metody se liší od volajícího typu výčtu.|
|[CA2249: Zvážit možnost místo string.IndexOf použít string.Contains](../code-quality/ca2249.md)|Volání na `string.IndexOf` místo, kde je použit výsledek pro kontrolu přítomnosti nebo absence podřetězce může být nahrazena `string.Contains` .|
