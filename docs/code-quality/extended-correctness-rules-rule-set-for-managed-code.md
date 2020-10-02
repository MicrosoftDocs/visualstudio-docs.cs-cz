---
title: Sada pravidel Rozšířená pravidla správnosti pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 00295a8485fa80d2aa6cf1977e014b191b28ba7e
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658604"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Sada pravidel Rozšířená pravidla správnosti pro spravovaný kód

Sada pravidel Rozšířená pravidla správnosti společnosti Microsoft maximalizuje logiku a chyby použití architektury, které jsou hlášeny nástrojem analýza kódu. Další důraz je kladen na konkrétní scénáře, jako je interoperabilita modelu COM a mobilní aplikace. Měli byste zvážit zahrnutí této sady pravidel, pokud se jeden z těchto scénářů vztahuje na váš projekt nebo pokud chcete najít další problémy v projektu.

Sada pravidel Rozšířená pravidla správnosti společnosti Microsoft zahrnuje pravidla, která jsou v sadě pravidel [základní pravidla správnosti](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , která obsahují pravidla uvedená v sadě pravidel [spravovaná doporučená pravidla](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

V následující tabulce jsou popsána všechna pravidla v sadě pravidel Rozšířená pravidla správnosti společnosti Microsoft.

|Pravidlo|Description|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1009](../code-quality/ca1009.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Označte sestavení pomocí AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Metody rozhraní by měly být volatelné podřízenými typy|
|[CA1049](../code-quality/ca1049.md)|Typy, které vlastní nativní prostředky, by měly být uvolnitelné|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Neskrývejte metody základní třídy|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementuje správně IDisposable|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400.md)|Vstupní body volání nespravovaného kódu by měly existovat|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Volání nespravovaných kódů by neměla být viditelná|
|[CA1403](../code-quality/ca1403.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Odeberte prázdné finalizační metody|
|[CA1900](../code-quality/ca1900.md)|Pole typů hodnot by měla být přenosná|
|[CA1901](../code-quality/ca1901.md)|Deklarace volání nespravovaného kódu by měla být přenosná|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Nepoužívejte zámky u objektů se slabou identitou|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Zkontrolujte chyby zabezpečení u dotazů SQL|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
|[CA2108](../code-quality/ca2108.md)|Zkontrolujte deklarativní zabezpečení u typů hodnot|
|[CA2111](../code-quality/ca2111.md)|Ukazatele by neměly být viditelné|
|[CA2112](../code-quality/ca2112.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114.md)|Zabezpečení metod by mělo být nadmnožinou typu|
|[CA2116](../code-quality/ca2116.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy APTCA by měl rozšiřovat pouze základní typy APTCA|
|[CA2122](../code-quality/ca2122.md)|Nezveřejňujte nepřímo metody s požadavky propojení|
|[CA2123](../code-quality/ca2123.md)|Požadavky na propojení přepisů by měly být identické s bází|
|[CA2124](../code-quality/ca2124.md)|Zabalte ohroženou klauzuli finally do vnějšího bloku try|
|[CA2126](../code-quality/ca2126.md)|Požadavky na propojení typů vyžadují požadavky na dědičnost|
|[CA2131](../code-quality/ca2131.md)|Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů|
|[CA2132](../code-quality/ca2132.md)|Výchozí konstruktory musí být alespoň tak kritické, jako výchozí konstruktory základního typu|
|[CA2133](../code-quality/ca2133.md)|Delegáti musí mít vazbu s metodami s konzistentní transparentností|
|[CA2134](../code-quality/ca2134.md)|Metody musí při přepisování základních metod zachovávat konzistentní transparentnost|
|[CA2137](../code-quality/ca2137.md)|Transparentní metody musí obsahovat pouze ověřitelné IL|
|[CA2138](../code-quality/ca2138.md)|Transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|
|[CA2141](../code-quality/ca2141.md)|Transparentní metody nesmí splňovat LinkDemand.|
|[CA2146](../code-quality/ca2146.md)|Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní|
|[CA2147](../code-quality/ca2147.md)|Transparentní metody nemusí používat kontrolní příkazy zabezpečení|
|[CA2149](../code-quality/ca2149.md)|Transparentní metody nesmí provádět volání nativního kódu|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Znovu vyvolejte pro zachování podrobností zásobníku|
|[CA2202](../code-quality/ca2202.md)|Neuvolňujte objekty několikrát|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inicializujte statická pole s typem hodnoty vloženě|
|[CA2212](../code-quality/ca2212.md)|Neoznačujte obsluhované komponenty pomocí WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Uvolnitelná pole by měla být uvolněna|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2220](../code-quality/ca2220.md)|Finalizační metody by měly volat finalizační metodu základní třídy|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementujte serializační konstruktory|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Označte vstupní body modelu Windows Forms pomocí STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236.md)|Volejte metody základní třídy u typů ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementujte správně metody serializace|
|[CA2240](../code-quality/ca2240.md)|Implementujte správně ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Zadejte správné argumenty pro metody formátování|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Testujte správně NaN|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Výčty by měly mít nulovou hodnotu|
|[CA1013](../code-quality/ca1013.md)|Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Nepředávejte literály jako lokalizované parametry|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizujte řetězce na velká písmena|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Neignorujte výsledky metody|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|Volejte správně GC.SuppressFinalize|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Vlastnosti by neměly vracet pole|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testujte prázdné řetězce pomocí délky řetězce|
|[CA1903](../code-quality/ca1903.md)|Používejte jen rozhraní API z cílové architektury|
|[CA2004](../code-quality/ca2004.md)|Odeberte volání GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Použijte SafeHandle k zapouzdření nativních prostředků|
|[CA2102](../code-quality/ca2102.md)|Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách|
|[CA2104](../code-quality/ca2104.md)|Nedeklaruje proměnlivé odkazové typy pouze pro čtení|
|[CA2105](../code-quality/ca2105.md)|Pole s poli by neměla být pouze pro čtení|
|[CA2106](../code-quality/ca2106.md)|Zabezpečte kontrolní příkazy|
|[CA2115](../code-quality/ca2115.md)|Volejte GC.KeepAlive při použití nativních prostředků|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Zapečeťte metody, které vyhovují privátním rozhraním|
|[CA2120](../code-quality/ca2120.md)|Zabezpečte serializační konstruktory|
|[CA2121](../code-quality/ca2121.md)|Statické konstruktory by měly být privátní|
|[CA2130](../code-quality/ca2130.md)|Konstanty kritické pro zabezpečení musí být transparentní|
|[CA2205](../code-quality/ca2205.md)|Použijte spravované ekvivalenty rozhraní Win32 API|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Metody Dispose by měly volat uvolnění základní třídy|
|[CA2221](../code-quality/ca2221.md)|Finalizační metody by měly být chráněné|
|[CA2222](../code-quality/ca2222.md)|Nesnižujte viditelnost zděděného členu|
|[CA2223](../code-quality/ca2223.md)|Členy by se měly lišit více než návratovým typem|
|[CA2224](../code-quality/ca2224.md)|Přepište Equals při přetížení operátoru rovnosti|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operátory by měly mít symetrická přetížení|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Vlastnosti kolekce by měly být pouze pro čtení|
|[CA2239](../code-quality/ca2239.md)|Zadejte metody deserializace pro nepovinná pole|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementujte standardní konstruktory výjimky|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Parametry identifikátoru URI by neměly být řetězce|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Návratové hodnoty identifikátoru URI by neměly být řetězce|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Vlastnosti identifikátoru URI by neměly být řetězce|
|[CA1057](../code-quality/ca1057.md)|Přetížení řetězce identifikátoru URI volají přetížení System.Uri|
|[CA1402](../code-quality/ca1402.md)|Vyhněte se přetížení ve viditelných rozhraních modelu COM|
|[CA1406](../code-quality/ca1406.md)|Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6|
|[CA1407](../code-quality/ca1407.md)|Vyhněte se statickým členům ve viditelných typech modelu COM|
|[CA1408](../code-quality/ca1408.md)|Nepoužívejte typ AutoDual ClassInterface|
|[CA1409](../code-quality/ca1409.md)|Viditelné typy modelu COM by měly být vytvořitelné|
|[CA1411](../code-quality/ca1411.md)|Metody registrace modelu COM by neměly být viditelné|
|[CA1412](../code-quality/ca1412.md)|Označte rozhraní ComSource jako IDispatch|
|[CA1413](../code-quality/ca1413.md)|Vyhněte se neveřejným polím v typech hodnot viditelných modulem COM|
|[CA1414](../code-quality/ca1414.md)|Označte logické argumenty volání nespravovaného kódu pomocí MarshalAs|
|[CA1600](../code-quality/ca1600.md)|Nepoužívejte prioritu nečinného procesu|
|[CA1601](../code-quality/ca1601.md)|Nepoužívejte časovače, které zabraňují změně stavu napájení|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Označte sestavení pomocí NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001.md)|Vyhněte se volání problematických metod|
|[CA2003](../code-quality/ca2003.md)|Nezacházejte s vlákénky jako s vlákny|
|[CA2135](../code-quality/ca2135.md)|Sestavení úrovně 2 by neměla obsahovat LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Členy by neměly mít konfliktní poznámky transparentnosti|
|[CA2139](../code-quality/ca2139.md)|Transparentní metody nemusí používat atribut HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142.md)|Transparentní kód by neměl být chráněn pomocí LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Transparentní metody by neměly používat požadavky zabezpečení|
|[CA2144](../code-quality/ca2144.md)|Transparentní kód by neměl načítat sestavení z bajtových polí|
|[CA2145](../code-quality/ca2145.md)|Transparentní metody by neměly být doplněny o SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Literály by měly být zadány správně|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Nekonstantní pole by neměla být viditelná|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Neoznačujte výčty pomocí FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Přepište GetHashCode při přepsání Equals|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Nevyvolávejte výjimky v klauzulích výjimky|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Přetížení operátoru mají pojmenované alternativy|
|[CA2228](../code-quality/ca2228.md)|Nedodávejte nevydané formáty prostředku|
|[CA2230](../code-quality/ca2230.md)|Použijte parametry pro proměnné argumenty|
|[CA2233](../code-quality/ca2233.md)|Operace by neměly přetéct|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Předejte objekty System.Uri namísto řetězců|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|Řetězcové literály atributů by se měly správně parsovat|
