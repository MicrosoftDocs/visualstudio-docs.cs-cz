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
ms.openlocfilehash: cf30e3294c1a96e64efd47ffd14f03328ebec62c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75573181"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód

Můžete použít pravidlo pravidla obecných zásad návrhu Microsoft Basic, abyste se mohli soustředit na snazší pochopení a používání kódu. Tuto sadu pravidel byste měli zahrnout, pokud projekt obsahuje kód knihovny nebo pokud chcete vyhovět osvědčeným postupům pro kód, který se snadno udržuje.

Základní pravidla obecných zásad návrhu zahrnují všechna pravidla uvedená v sadě pravidel [spravovaná doporučená pravidla](managed-recommended-rules-rule-set-for-managed-code.md) .

V následující tabulce jsou popsána všechna pravidla v sadě pravidel základní pravidla návrhu Microsoft Basic.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1000](../code-quality/ca1000.md)|Nedeklarujte statické členy v obecných typech|
|[CA1001](../code-quality/ca1001.md)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1002](../code-quality/ca1002.md)|Nezveřejňujte obecné seznamy|
|[CA1003](../code-quality/ca1003.md)|Použijte instance obecných obslužných rutin události|
|[CA1004](../code-quality/ca1004.md)|Obecné metody by měly poskytnout parametr typu|
|[CA1005](../code-quality/ca1005.md)|Vyhněte se nadbytečným parametrům u obecných typů|
|[CA1006](../code-quality/ca1006.md)|Nevnořujte obecné typy do signatur členu|
|[CA1007](../code-quality/ca1007.md)|Použijte obecné typy, kde je to vhodné|
|[CA1008](../code-quality/ca1008.md)|Výčty by měly mít nulovou hodnotu|
|[CA1009](../code-quality/ca1009.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1010](../code-quality/ca1010.md)|Kolekce musí implementovat obecné rozhraní|
|[CA1011](../code-quality/ca1011.md)|Zvažte předání základních typů jako parametrů|
|[CA1012](../code-quality/ca1012.md)|Abstraktní typy by neměly mít konstruktory|
|[CA1013](../code-quality/ca1013.md)|Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání|
|[CA1014](../code-quality/ca1014.md)|Označte sestavení pomocí CLSCompliantAttribute|
|[CA1016](../code-quality/ca1016.md)|Označte sestavení pomocí AssemblyVersionAttribute|
|[CA1017](../code-quality/ca1017.md)|Označte sestavení pomocí ComVisibleAttribute|
|[CA1018](../code-quality/ca1018.md)|Označte atributy pomocí AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019.md)|Definujte přístupové objekty pro argumenty atributů|
|[CA1023](../code-quality/ca1023.md)|Indexery by neměly být multidimenzionální|
|[CA1024](../code-quality/ca1024.md)|Použijte vlastnosti, kde je to vhodné|
|[CA1025](../code-quality/ca1025.md)|Nahraďte opakované argumenty polem parametrů|
|[CA1026](../code-quality/ca1026.md)|Neměly by být použity výchozí parametry|
|[CA1027](../code-quality/ca1027.md)|Označte výčty pomocí FlagsAttribute|
|[CA1028](../code-quality/ca1028.md)|Úložiště výčtu by mělo být Int32|
|[CA1030](../code-quality/ca1030.md)|Použijte události, kde je to vhodné|
|[CA1031](../code-quality/ca1031.md)|Nezachycujte výjimky obecného typu|
|[CA1032](../code-quality/ca1032.md)|Implementujte standardní konstruktory výjimky|
|[CA1033](../code-quality/ca1033.md)|Metody rozhraní by měly být volatelné podřízenými typy|
|[CA1034](../code-quality/ca1034.md)|Vnořené typy by neměly být viditelné|
|[CA1035](../code-quality/ca1035.md)|Implementace ICollection mají členy silného typu|
|[CA1036](../code-quality/ca1036.md)|Přepište metody u srovnatelných typů|
|[CA1038](../code-quality/ca1038.md)|Enumerátory by měly být silného typu|
|[CA1039](../code-quality/ca1039.md)|Seznamy jsou silného typu|
|[CA1041](../code-quality/ca1041.md)|Poskytněte zprávu ObsoleteAttribute|
|[CA1043](../code-quality/ca1043.md)|Použijte celočíselný nebo řetězcový argument pro indexery|
|[CA1044](../code-quality/ca1044.md)|Vlastnosti by neměly být pouze pro zápis|
|[CA1046](../code-quality/ca1046.md)|Nepřetěžujte operátory rovnosti u odkazových typů|
|[CA1047](../code-quality/ca1047.md)|Nedeklarujte chráněné členy v zapečetěných typech|
|[CA1048](../code-quality/ca1048.md)|Nedeklarujte virtuální členy v zapečetěných typech|
|[CA1049](../code-quality/ca1049.md)|Typy, které vlastní nativní prostředky, by měly být uvolnitelné|
|[CA1050](../code-quality/ca1050.md)|Deklarujte typy v oborech názvů|
|[CA1051](../code-quality/ca1051.md)|Nedeklarujte viditelná pole instance|
|[CA1052](../code-quality/ca1052.md)|Statické typy vlastníků by měly být zapečetěné|
|[CA1053](../code-quality/ca1053.md)|Statické typy vlastníků by neměly mít konstruktory|
|[CA1054](../code-quality/ca1054.md)|Parametry identifikátoru URI by neměly být řetězce|
|[CA1055](../code-quality/ca1055.md)|Návratové hodnoty identifikátoru URI by neměly být řetězce|
|[CA1056](../code-quality/ca1056.md)|Vlastnosti identifikátoru URI by neměly být řetězce|
|[CA1057](../code-quality/ca1057.md)|Přetížení řetězce identifikátoru URI volají přetížení System.Uri|
|[CA1058](../code-quality/ca1058.md)|Typy by neměly rozšiřovat určité základní typy|
|[CA1059](../code-quality/ca1059.md)|Členy by neměly zveřejňovat určité konkrétní typy|
|[CA1060](../code-quality/ca1060.md)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Neskrývejte metody základní třídy|
|[CA1063](../code-quality/ca1063.md)|Implementuje správně IDisposable|
|[CA1064](../code-quality/ca1064.md)|Výjimky by měly být veřejné|
|[CA1065](../code-quality/ca1065.md)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400.md)|Vstupní body volání nespravovaného kódu by měly existovat|
|[CA1401](../code-quality/ca1401.md)|Volání nespravovaných kódů by neměla být viditelná|
|[CA1403](../code-quality/ca1403.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1500](../code-quality/ca1500.md)|Názvy proměnných by neměly odpovídat názvům polí|
|[CA1502](../code-quality/ca1502.md)|Vyhněte se nadměrné složitosti|
|[CA1708](../code-quality/ca1708.md)|Identifikátory by se měly lišit více než použitím malých a velkých písmen|
|[CA1716](../code-quality/ca1716.md)|Identifikátory by se neměly shodovat s klíčovými slovy|
|[CA1801](../code-quality/ca1801.md)|Zkontrolujte nepoužité parametry|
|[CA1804](../code-quality/ca1804.md)|Odeberte nepoužívané lokální hodnoty|
|[CA1809](../code-quality/ca1809.md)|Vyhněte se nadměrným lokálním hodnotám|
|[CA1810](../code-quality/ca1810.md)|Inicializujte odkazový typ statického pole vloženě|
|[CA1811](../code-quality/ca1811.md)|Vyhněte se nevolanému privátnímu kódu|
|[CA1812](../code-quality/ca1812.md)|Vyhněte se nevytvořeným instancím interních tříd|
|[CA1813](../code-quality/ca1813.md)|Vyhněte se nezapečetěným atributům|
|[CA1814](../code-quality/ca1814.md)|Upřednostněte vícenásobná pole před multidimenzionálními|
|[CA1815](../code-quality/ca1815.md)|Přepište rovnosti a operátory rovnosti u typů hodnot|
|[CA1819](../code-quality/ca1819.md)|Vlastnosti by neměly vracet pole|
|[CA1820](../code-quality/ca1820.md)|Testujte prázdné řetězce pomocí délky řetězce|
|[CA1821](../code-quality/ca1821.md)|Odeberte prázdné finalizační metody|
|[CA1822](../code-quality/ca1822.md)|Označte členy jako statické|
|[CA1823](../code-quality/ca1823.md)|Vyhněte se nepoužitým privátním polím|
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
|[CA2201](../code-quality/ca2201.md)|Nevyvolávejte vyhrazené typy výjimek|
|[CA2202](../code-quality/ca2202.md)|Neuvolňujte objekty několikrát|
|[CA2205](../code-quality/ca2205.md)|Použijte spravované ekvivalenty rozhraní Win32 API|
|[CA2207](../code-quality/ca2207.md)|Inicializujte statická pole s typem hodnoty vloženě|
|[CA2208](../code-quality/ca2208.md)|Vytvořte správně instance výjimky argumentu|
|[CA2211](../code-quality/ca2211.md)|Nekonstantní pole by neměla být viditelná|
|[CA2212](../code-quality/ca2212.md)|Neoznačujte obsluhované komponenty pomocí WebMethod|
|[CA2213](../code-quality/ca2213.md)|Uvolnitelná pole by měla být uvolněna|
|[CA2214](../code-quality/ca2214.md)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](../code-quality/ca2216.md)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2217](../code-quality/ca2217.md)|Neoznačujte výčty pomocí FlagsAttribute|
|[CA2219](../code-quality/ca2219.md)|Nevyvolávejte výjimky v klauzulích výjimky|
|[CA2220](../code-quality/ca2220.md)|Finalizační metody by měly volat finalizační metodu základní třídy|
|[CA2221](../code-quality/ca2221.md)|Finalizační metody by měly být chráněné|
|[CA2222](../code-quality/ca2222.md)|Nesnižujte viditelnost zděděného členu|
|[CA2223](../code-quality/ca2223.md)|Členy by se měly lišit více než návratovým typem|
|[CA2224](../code-quality/ca2224.md)|Přepište Equals při přetížení operátoru rovnosti|
|[CA2225](../code-quality/ca2225.md)|Přetížení operátoru mají pojmenované alternativy|
|[CA2226](../code-quality/ca2226.md)|Operátory by měly mít symetrická přetížení|
|[CA2227](../code-quality/ca2227.md)|Vlastnosti kolekce by měly být pouze pro čtení|
|[CA2229](../code-quality/ca2229.md)|Implementujte serializační konstruktory|
|[CA2230](../code-quality/ca2230.md)|Použijte parametry pro proměnné argumenty|
|[CA2231](../code-quality/ca2231.md)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Označte vstupní body modelu Windows Forms pomocí STAThread|
|[CA2234](../code-quality/ca2234.md)|Předejte objekty System.Uri namísto řetězců|
|[CA2235](../code-quality/ca2235.md)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236.md)|Volejte metody základní třídy u typů ISerializable|
|[CA2237](../code-quality/ca2237.md)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementujte správně metody serializace|
|[CA2239](../code-quality/ca2239.md)|Zadejte metody deserializace pro nepovinná pole|
|[CA2240](../code-quality/ca2240.md)|Implementujte správně ISerializable|
|[CA2241](../code-quality/ca2241.md)|Zadejte správné argumenty pro metody formátování|
|[CA2242](../code-quality/ca2242.md)|Testujte správně NaN|
