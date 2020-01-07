---
title: Sada pravidel Pravidla zabezpečení pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: babfc00dfadc6b26f8338faf37b5b4a1f7c1d8e5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587222"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla zabezpečení pro spravovaný kód

Pomocí sady pravidel zabezpečení společnosti Microsoft pro analýzu kódu starší verze Maximalizujte počet potenciálních problémů zabezpečení, které jsou hlášeny.

|Pravidlo|Popis|
|----------|-----------------|
|[CA2100](../code-quality/ca2100.md)|Zkontrolujte chyby zabezpečení u dotazů SQL|
|[CA2102](../code-quality/ca2102.md)|Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách|
|[CA2103](../code-quality/ca2103.md)|Zkontrolujte imperativní zabezpečení|
|[CA2104](../code-quality/ca2104.md)|Nedeklaruje proměnlivé odkazové typy pouze pro čtení|
|[CA2105](../code-quality/ca2105.md)|Pole s poli by neměla být pouze pro čtení|
|[CA2106](../code-quality/ca2106.md)|Zabezpečte kontrolní příkazy|
|[CA2107](../code-quality/ca2107.md)|Zkontrolujte použití čistého odepření a povolení|
|[CA2108](../code-quality/ca2108.md)|Zkontrolujte deklarativní zabezpečení u typů hodnot|
|[CA2109](../code-quality/ca2109.md)|Zkontrolujte viditelné obslužné rutiny událostí|
|[CA2111](../code-quality/ca2111.md)|Ukazatele by neměly být viditelné|
|[CA2112](../code-quality/ca2112.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114.md)|Zabezpečení metod by mělo být nadmnožinou typu|
|[CA2115](../code-quality/ca2115.md)|Volejte GC.KeepAlive při použití nativních prostředků|
|[CA2116](../code-quality/ca2116.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy APTCA by měl rozšiřovat pouze základní typy APTCA|
|[CA2118](../code-quality/ca2118.md)|Zkontrolujte použití SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119.md)|Zapečeťte metody, které vyhovují privátním rozhraním|
|[CA2120](../code-quality/ca2120.md)|Zabezpečte serializační konstruktory|
|[CA2121](../code-quality/ca2121.md)|Statické konstruktory by měly být privátní|
|[CA2122](../code-quality/ca2122.md)|Nezveřejňujte nepřímo metody s požadavky propojení|
|[CA2123](../code-quality/ca2123.md)|Požadavky na propojení přepisů by měly být identické s bází|
|[CA2124](../code-quality/ca2124.md)|Zabalte ohroženou klauzuli finally do vnějšího bloku try|
|[CA2126](../code-quality/ca2126.md)|Požadavky na propojení typů vyžadují požadavky na dědičnost|
|[CA2130](../code-quality/ca2130.md)|Konstanty kritické pro zabezpečení musí být transparentní|
|[CA2131](../code-quality/ca2131.md)|Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů|
|[CA2132](../code-quality/ca2132.md)|Výchozí konstruktory musí být alespoň tak kritické, jako výchozí konstruktory základního typu|
|[CA2133](../code-quality/ca2133.md)|Delegáti musí mít vazbu s metodami s konzistentní transparentností|
|[CA2134](../code-quality/ca2134.md)|Metody musí při přepisování základních metod zachovávat konzistentní transparentnost|
|[CA2135](../code-quality/ca2135.md)|Sestavení úrovně 2 by neměla obsahovat LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Členy by neměly mít konfliktní poznámky transparentnosti|
|[CA2137](../code-quality/ca2137.md)|Transparentní metody musí obsahovat pouze ověřitelné IL|
|[CA2138](../code-quality/ca2138.md)|Transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|Transparentní metody nemusí používat atribut HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|
|[CA2141](../code-quality/ca2141.md)|Transparentní metody nesmí splňovat LinkDemand.|
|[CA2142](../code-quality/ca2142.md)|Transparentní kód by neměl být chráněn pomocí LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Transparentní metody by neměly používat požadavky zabezpečení|
|[CA2144](../code-quality/ca2144.md)|Transparentní kód by neměl načítat sestavení z bajtových polí|
|[CA2145](../code-quality/ca2145.md)|Transparentní metody by neměly být doplněny o SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní|
|[CA2147](../code-quality/ca2147.md)|Transparentní metody nemusí používat kontrolní příkazy zabezpečení|
|[CA2149](../code-quality/ca2149.md)|Transparentní metody nesmí provádět volání nativního kódu|
|[CA2210](../code-quality/ca2210.md)|Sestavení by měla mít platné silné názvy|
|[CA2300](ca2300.md)|Nepoužívat nezabezpečený deserializátor BinaryFormatter|
|[CA2301](ca2301.md)|Nevolat BinaryFormatter.Deserialize dříve, než se nastaví BinaryFormatter.Binder|
|[CA2302](ca2302.md)|Než zavoláte BinaryFormatter.Deserialize, ujistěte se, že je nastavený BinaryFormatter.Binder|
|[CA2305](ca2305.md)|Nepoužívat nezabezpečený deserializátor LosFormatter|
|[CA2310](ca2310.md)|Nepoužívat nezabezpečený deserializátor NetDataContractSerializer|
|[CA2311](ca2311.md)|Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder|
|[CA2312](ca2312.md)|Před deserializací se ujistěte, že je nastavený NetDataContractSerializer.Binder|
|[CA2315](ca2315.md)|Nepoužívat nezabezpečený deserializátor ObjectStateFormatter|
|[CA2321](ca2321.md)|Nedeserializovat se třídou JavaScriptSerializer pomocí třídy SimpleTypeResolver|
|[CA2322](ca2322.md)|Před deserializaci se ujistěte se, že třída JavaScriptSerializer není inicializována pomocí třídy SimpleTypeResolver|
|[CA3001](../code-quality/ca3001.md)|Zkontrolujte ohrožení zabezpečení injektáží SQL v kódu|
|[CA3002](../code-quality/ca3002.md)|Zkontrolujte ohrožení zabezpečení proti XSS v kódu|
|[CA3003](../code-quality/ca3003.md)|Zkontrolujte ohrožení zabezpečení injektáží cesty k souboru v kódu|
|[CA3004](../code-quality/ca3004.md)|Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu|
|[CA3005](../code-quality/ca3005.md)|Zkontrolujte ohrožení zabezpečení injektáží protokolu LDAP v kódu|
|[CA3006](../code-quality/ca3006.md)|Zkontrolujte ohrožení zabezpečení injektáží příkazu procesu v kódu|
|[CA3007](../code-quality/ca3007.md)|Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu|
|[CA3008](../code-quality/ca3008.md)|Zkontrolujte ohrožení zabezpečení injektáží XPath v kódu|
|[CA3009](../code-quality/ca3009.md)|Zkontrolujte ohrožení zabezpečení injektáží XML v kódu|
|[CA3010](../code-quality/ca3010.md)|Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu|
|[CA3011](../code-quality/ca3011.md)|Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu|
|[CA3012](../code-quality/ca3012.md)|Zkontrolujte ohrožení zabezpečení injektáží regulárního výrazu v kódu|
|[CA5403](../code-quality/ca5403.md)|Nepoužívejte pevně zakódovaný certifikát|
