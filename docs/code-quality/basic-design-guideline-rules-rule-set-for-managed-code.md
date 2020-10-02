---
title: Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2bf7542d94b16042df27ec8b780cc93c9061d6e8
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659124"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód

Můžete použít pravidlo pravidla obecných zásad návrhu Microsoft Basic, abyste se mohli soustředit na snazší pochopení a používání kódu. Tuto sadu pravidel byste měli zahrnout, pokud projekt obsahuje kód knihovny nebo pokud chcete vyhovět osvědčeným postupům pro kód, který se snadno udržuje.

Základní pravidla obecných zásad návrhu zahrnují všechna pravidla uvedená v sadě pravidel [spravovaná doporučená pravidla](managed-recommended-rules-rule-set-for-managed-code.md) .

V následující tabulce jsou popsána všechna pravidla v sadě pravidel základní pravidla návrhu Microsoft Basic.

|Pravidlo|Description|
|----------|-----------------|
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Nedeklarujte statické členy v obecných typech|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Nezveřejňujte obecné seznamy|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Použijte instance obecných obslužných rutin události|
|[CA1004](../code-quality/ca1004.md)|Obecné metody by měly poskytnout parametr typu|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Vyhněte se nadbytečným parametrům u obecných typů|
|[CA1006](../code-quality/ca1006.md)|Nevnořujte obecné typy do signatur členu|
|[CA1007](../code-quality/ca1007.md)|Použijte obecné typy, kde je to vhodné|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Výčty by měly mít nulovou hodnotu|
|[CA1009](../code-quality/ca1009.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Kolekce musí implementovat obecné rozhraní|
|[CA1011](../code-quality/ca1011.md)|Zvažte předání základních typů jako parametrů|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Abstraktní typy by neměly mít konstruktory|
|[CA1013](../code-quality/ca1013.md)|Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Označte sestavení pomocí CLSCompliantAttribute|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Označte sestavení pomocí AssemblyVersionAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Označte sestavení pomocí ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Označte atributy pomocí AttributeUsageAttribute|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Definujte přístupové objekty pro argumenty atributů|
|[CA1023](../code-quality/ca1023.md)|Indexery by neměly být multidimenzionální|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Použijte vlastnosti, kde je to vhodné|
|[CA1025](../code-quality/ca1025.md)|Nahraďte opakované argumenty polem parametrů|
|[CA1026](../code-quality/ca1026.md)|Neměly by být použity výchozí parametry|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Označte výčty pomocí FlagsAttribute|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Úložiště výčtu by mělo být Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Použijte události, kde je to vhodné|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Nezachycujte výjimky obecného typu|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementujte standardní konstruktory výjimky|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Metody rozhraní by měly být volatelné podřízenými typy|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Vnořené typy by neměly být viditelné|
|[CA1035](../code-quality/ca1035.md)|Implementace ICollection mají členy silného typu|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Přepište metody u srovnatelných typů|
|[CA1038](../code-quality/ca1038.md)|Enumerátory by měly být silného typu|
|[CA1039](../code-quality/ca1039.md)|Seznamy jsou silného typu|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Poskytněte zprávu ObsoleteAttribute|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Použijte celočíselný nebo řetězcový argument pro indexery|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Vlastnosti by neměly být pouze pro zápis|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Nepřetěžujte operátory rovnosti u odkazových typů|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Nedeklarujte chráněné členy v zapečetěných typech|
|[CA1048](../code-quality/ca1048.md)|Nedeklarujte virtuální členy v zapečetěných typech|
|[CA1049](../code-quality/ca1049.md)|Typy, které vlastní nativní prostředky, by měly být uvolnitelné|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Deklarujte typy v oborech názvů|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Nedeklarujte viditelná pole instance|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Statické typy vlastníků by měly být zapečetěné|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Statické typy vlastníků by neměly mít konstruktory|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Parametry identifikátoru URI by neměly být řetězce|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Návratové hodnoty identifikátoru URI by neměly být řetězce|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Vlastnosti identifikátoru URI by neměly být řetězce|
|[CA1057](../code-quality/ca1057.md)|Přetížení řetězce identifikátoru URI volají přetížení System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Typy by neměly rozšiřovat určité základní typy|
|[CA1059](../code-quality/ca1059.md)|Členy by neměly zveřejňovat určité konkrétní typy|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Neskrývejte metody základní třídy|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementuje správně IDisposable|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Výjimky by měly být veřejné|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400.md)|Vstupní body volání nespravovaného kódu by měly existovat|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Volání nespravovaných kódů by neměla být viditelná|
|[CA1403](../code-quality/ca1403.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1500](../code-quality/ca1500.md)|Názvy proměnných by neměly odpovídat názvům polí|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Vyhněte se nadměrné složitosti|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Identifikátory by se měly lišit více než použitím malých a velkých písmen|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Identifikátory by se neměly shodovat s klíčovými slovy|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Zkontrolujte nepoužité parametry|
|[CA1804](../code-quality/ca1804.md)|Odeberte nepoužívané lokální hodnoty|
|[CA1809](../code-quality/ca1809.md)|Vyhněte se nadměrným lokálním hodnotám|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Inicializujte odkazový typ statického pole vloženě|
|[CA1811](../code-quality/ca1811.md)|Vyhněte se nevolanému privátnímu kódu|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Vyhněte se nevytvořeným instancím interních tříd|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Vyhněte se nezapečetěným atributům|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Upřednostněte vícenásobná pole před multidimenzionálními|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Přepište rovnosti a operátory rovnosti u typů hodnot|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Vlastnosti by neměly vracet pole|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testujte prázdné řetězce pomocí délky řetězce|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Odeberte prázdné finalizační metody|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Označte členy jako statické|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Vyhněte se nepoužitým privátním polím|
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
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Nevyvolávejte vyhrazené typy výjimek|
|[CA2202](../code-quality/ca2202.md)|Neuvolňujte objekty několikrát|
|[CA2205](../code-quality/ca2205.md)|Použijte spravované ekvivalenty rozhraní Win32 API|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inicializujte statická pole s typem hodnoty vloženě|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Vytvořte správně instance výjimky argumentu|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Nekonstantní pole by neměla být viditelná|
|[CA2212](../code-quality/ca2212.md)|Neoznačujte obsluhované komponenty pomocí WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Uvolnitelná pole by měla být uvolněna|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Neoznačujte výčty pomocí FlagsAttribute|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Nevyvolávejte výjimky v klauzulích výjimky|
|[CA2220](../code-quality/ca2220.md)|Finalizační metody by měly volat finalizační metodu základní třídy|
|[CA2221](../code-quality/ca2221.md)|Finalizační metody by měly být chráněné|
|[CA2222](../code-quality/ca2222.md)|Nesnižujte viditelnost zděděného členu|
|[CA2223](../code-quality/ca2223.md)|Členy by se měly lišit více než návratovým typem|
|[CA2224](../code-quality/ca2224.md)|Přepište Equals při přetížení operátoru rovnosti|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Přetížení operátoru mají pojmenované alternativy|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operátory by měly mít symetrická přetížení|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Vlastnosti kolekce by měly být pouze pro čtení|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementujte serializační konstruktory|
|[CA2230](../code-quality/ca2230.md)|Použijte parametry pro proměnné argumenty|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Označte vstupní body modelu Windows Forms pomocí STAThread|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Předejte objekty System.Uri namísto řetězců|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236.md)|Volejte metody základní třídy u typů ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementujte správně metody serializace|
|[CA2239](../code-quality/ca2239.md)|Zadejte metody deserializace pro nepovinná pole|
|[CA2240](../code-quality/ca2240.md)|Implementujte správně ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Zadejte správné argumenty pro metody formátování|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Testujte správně NaN|
