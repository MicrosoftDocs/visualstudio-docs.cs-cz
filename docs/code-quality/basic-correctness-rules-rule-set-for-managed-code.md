---
title: Sada pravidel Základní pravidla správnosti pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8f48b2d60feb9743529de8ed80b80365ffb815d1
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534599"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Sada pravidel Základní pravidla správnosti pro spravovaný kód

Sada pravidel základní pravidla správnosti se zaměřuje na logické chyby a běžné chyby v používání rozhraní API architektury. Základní pravidla správnosti zahrnují pravidla uvedená v sadě pravidel [spravovaná doporučená pravidla](managed-recommended-rules-rule-set-for-managed-code.md) .

V následující tabulce jsou popsána všechna pravidla v sadě pravidel základní pravidla správnosti společnosti Microsoft.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1009](../code-quality/ca1009.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1016](../code-quality/ca1016.md)|Označte sestavení pomocí AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|Metody rozhraní by měly být volatelné podřízenými typy|
|[CA1049](../code-quality/ca1049.md)|Typy, které vlastní nativní prostředky, by měly být uvolnitelné|
|[CA1060](../code-quality/ca1060.md)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Neskrývejte metody základní třídy|
|[CA1063](../code-quality/ca1063.md)|Implementuje správně IDisposable|
|[CA1065](../code-quality/ca1065.md)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400.md)|Vstupní body volání nespravovaného kódu by měly existovat|
|[CA1401](../code-quality/ca1401.md)|Volání nespravovaných kódů by neměla být viditelná|
|[CA1403](../code-quality/ca1403.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1821](../code-quality/ca1821.md)|Odeberte prázdné finalizační metody|
|[CA1900](../code-quality/ca1900.md)|Pole typů hodnot by měla být přenosná|
|[CA1901](../code-quality/ca1901.md)|Deklarace volání nespravovaného kódu by měla být přenosná|
|[CA2002](../code-quality/ca2002.md)|Nepoužívejte zámky u objektů se slabou identitou|
|[CA2100](../code-quality/ca2100.md)|Zkontrolujte chyby zabezpečení u dotazů SQL|
|[CA2101](../code-quality/ca2101.md)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
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
|[CA2200](../code-quality/ca2200.md)|Znovu vyvolejte pro zachování podrobností zásobníku|
|[CA2202](../code-quality/ca2202.md)|Neuvolňujte objekty několikrát|
|[CA2207](../code-quality/ca2207.md)|Inicializujte statická pole s typem hodnoty vloženě|
|[CA2212](../code-quality/ca2212.md)|Neoznačujte obsluhované komponenty pomocí WebMethod|
|[CA2213](../code-quality/ca2213.md)|Uvolnitelná pole by měla být uvolněna|
|[CA2214](../code-quality/ca2214.md)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](../code-quality/ca2216.md)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2220](../code-quality/ca2220.md)|Finalizační metody by měly volat finalizační metodu základní třídy|
|[CA2229](../code-quality/ca2229.md)|Implementujte serializační konstruktory|
|[CA2231](../code-quality/ca2231.md)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Označte vstupní body modelu Windows Forms pomocí STAThread|
|[CA2235](../code-quality/ca2235.md)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236.md)|Volejte metody základní třídy u typů ISerializable|
|[CA2237](../code-quality/ca2237.md)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementujte správně metody serializace|
|[CA2240](../code-quality/ca2240.md)|Implementujte správně ISerializable|
|[CA2241](../code-quality/ca2241.md)|Zadejte správné argumenty pro metody formátování|
|[CA2242](../code-quality/ca2242.md)|Testujte správně NaN|
|[CA1008](../code-quality/ca1008.md)|Výčty by měly mít nulovou hodnotu|
|[CA1013](../code-quality/ca1013.md)|Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání|
|[CA1303](../code-quality/ca1303.md)|Nepředávejte literály jako lokalizované parametry|
|[CA1308](../code-quality/ca1308.md)|Normalizujte řetězce na velká písmena|
|[CA1806](../code-quality/ca1806.md)|Neignorujte výsledky metody|
|[CA1816](../code-quality/ca1816.md)|Volejte správně GC.SuppressFinalize|
|[CA1819](../code-quality/ca1819.md)|Vlastnosti by neměly vracet pole|
|[CA1820](../code-quality/ca1820.md)|Testujte prázdné řetězce pomocí délky řetězce|
|[CA1903](../code-quality/ca1903.md)|Používejte jen rozhraní API z cílové architektury|
|[CA2004](../code-quality/ca2004.md)|Odeberte volání GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Použijte SafeHandle k zapouzdření nativních prostředků|
|[CA2102](../code-quality/ca2102.md)|Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách|
|[CA2104](../code-quality/ca2104.md)|Nedeklaruje proměnlivé odkazové typy pouze pro čtení|
|[CA2105](../code-quality/ca2105.md)|Pole s poli by neměla být pouze pro čtení|
|[CA2106](../code-quality/ca2106.md)|Zabezpečte kontrolní příkazy|
|[CA2115](../code-quality/ca2115.md)|Volejte GC.KeepAlive při použití nativních prostředků|
|[CA2119](../code-quality/ca2119.md)|Zapečeťte metody, které vyhovují privátním rozhraním|
|[CA2120](../code-quality/ca2120.md)|Zabezpečte serializační konstruktory|
|[CA2121](../code-quality/ca2121.md)|Statické konstruktory by měly být privátní|
|[CA2130](../code-quality/ca2130.md)|Konstanty kritické pro zabezpečení musí být transparentní|
|[CA2205](../code-quality/ca2205.md)|Použijte spravované ekvivalenty rozhraní Win32 API|
|[CA2215](../code-quality/ca2215.md)|Metody Dispose by měly volat uvolnění základní třídy|
|[CA2221](../code-quality/ca2221.md)|Finalizační metody by měly být chráněné|
|[CA2222](../code-quality/ca2222.md)|Nesnižujte viditelnost zděděného členu|
|[CA2223](../code-quality/ca2223.md)|Členy by se měly lišit více než návratovým typem|
|[CA2224](../code-quality/ca2224.md)|Přepište Equals při přetížení operátoru rovnosti|
|[CA2226](../code-quality/ca2226.md)|Operátory by měly mít symetrická přetížení|
|[CA2227](../code-quality/ca2227.md)|Vlastnosti kolekce by měly být pouze pro čtení|
|[CA2239](../code-quality/ca2239.md)|Zadejte metody deserializace pro nepovinná pole|
