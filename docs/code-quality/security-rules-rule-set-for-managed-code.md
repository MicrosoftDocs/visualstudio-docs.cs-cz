---
title: Sada pravidel Pravidla zabezpečení pro spravovaný kód
ms.date: 11/04/2016
description: Přečtěte si o sadě pravidel zabezpečení nastavené pro Visual Studio starší verze analýzy kódu. Podívejte se na popisy pravidel, která se zaměřují na potenciální problémy se zabezpečením.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 32237eb1229e28d1077b2eec8586f52151d69c2d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436950"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Sada pravidel Pravidla zabezpečení pro spravovaný kód

Pomocí sady pravidel zabezpečení společnosti Microsoft pro analýzu kódu starší verze Maximalizujte počet potenciálních problémů zabezpečení, které jsou hlášeny.

|Pravidlo|Popis|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Zkontrolujte chyby zabezpečení u dotazů SQL|
|[CA2102](../code-quality/ca2102.md)|Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách|
|[CA2103](../code-quality/ca2103.md)|Zkontrolujte imperativní zabezpečení|
|[CA2104](../code-quality/ca2104.md)|Nedeklaruje proměnlivé odkazové typy pouze pro čtení|
|[CA2105](../code-quality/ca2105.md)|Pole s poli by neměla být pouze pro čtení|
|[CA2106](../code-quality/ca2106.md)|Zabezpečte kontrolní příkazy|
|[CA2107](../code-quality/ca2107.md)|Zkontrolujte použití čistého odepření a povolení|
|[CA2108](../code-quality/ca2108.md)|Zkontrolujte deklarativní zabezpečení u typů hodnot|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Zkontrolujte viditelné obslužné rutiny událostí|
|[CA2111](../code-quality/ca2111.md)|Ukazatele by neměly být viditelné|
|[CA2112](../code-quality/ca2112.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114.md)|Zabezpečení metod by mělo být nadmnožinou typu|
|[CA2115](../code-quality/ca2115.md)|Volejte GC.KeepAlive při použití nativních prostředků|
|[CA2116](../code-quality/ca2116.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy APTCA by měl rozšiřovat pouze základní typy APTCA|
|[CA2118](../code-quality/ca2118.md)|Zkontrolujte použití SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Zapečeťte metody, které vyhovují privátním rozhraním|
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
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|Nepoužívat nezabezpečený deserializátor BinaryFormatter|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|Nevolat BinaryFormatter.Deserialize dříve, než se nastaví BinaryFormatter.Binder|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|Než zavoláte BinaryFormatter.Deserialize, ujistěte se, že je nastavený BinaryFormatter.Binder|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|Nepoužívat nezabezpečený deserializátor LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|Nepoužívat nezabezpečený deserializátor NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Před deserializací se ujistěte, že je nastavený NetDataContractSerializer.Binder|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|Nepoužívat nezabezpečený deserializátor ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|Nedeserializovat se třídou JavaScriptSerializer pomocí třídy SimpleTypeResolver|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Před deserializaci se ujistěte se, že třída JavaScriptSerializer není inicializována pomocí třídy SimpleTypeResolver|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|Zkontrolujte ohrožení zabezpečení injektáží SQL v kódu|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|Zkontrolujte ohrožení zabezpečení proti XSS v kódu|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Zkontrolujte ohrožení zabezpečení injektáží cesty k souboru v kódu|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|Zkontrolujte ohrožení zabezpečení injektáží protokolu LDAP v kódu|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|Zkontrolujte ohrožení zabezpečení injektáží příkazu procesu v kódu|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|Zkontrolujte ohrožení zabezpečení injektáží XPath v kódu|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|Zkontrolujte ohrožení zabezpečení injektáží XML v kódu|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Zkontrolujte ohrožení zabezpečení injektáží regulárního výrazu v kódu|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|Nepoužívat nezabezpečené režimy šifrování|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|Nepoužívejte pevně zakódovaný certifikát|