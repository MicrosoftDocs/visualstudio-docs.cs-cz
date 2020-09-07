---
title: Stav portu pravidla FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508363"
---
# <a name="fxcop-rule-port-status"></a>Stav portu pravidla FxCop

Pokud jste dříve používali analýzu statického kódu v aplikaci Visual Studio, můžete si všimnout, že tato pravidla jsou k dispozici v aktuální implementaci jako [analyzátory FxCop](install-fxcop-analyzers.md). Tato stránka obsahuje seznam pravidel, která byla předaná. Podívejte se na nepřipojená [pravidla](fxcop-unported-rules.md) pro ty, které se nedostaly do portu a zda existují plány pro jejich přenos.

## <a name="ported-rules"></a>Přenesená pravidla

[Stránka pro automaticky generovanou dokumentaci](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) v úložišti Roslyn-Analyzer obsahuje nejaktuálnější seznam pravidel, která byla předaná do analyzátorů FxCop. Tato stránka obsahuje také další informace, například zda je pravidlo povoleno ve výchozím nastavení a zda má přidruženou *opravu kódu*. ([Opravy kódu](../ide/quick-actions.md) jsou dostupné opravy jedním kliknutím v nabídce ikony žárovky v aplikaci Visual Studio.)

Od data na této stránce seznam pravidel FxCop, která byla předaná do [analyzátorů FxCop](install-fxcop-analyzers.md) , zahrnují:

ID pravidla | Nadpis
--------|---------
[CA1000](ca1000.md) | Nedeklarujte statické členy v obecných typech
[CA1001](ca1001.md) | Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné
[CA1002](ca1002.md) | Nezveřejňujte obecné seznamy
[CA1003](ca1003.md) | Použijte instance obecných obslužných rutin události
[CA1005](ca1005.md) | Vyhněte se nadbytečným parametrům u obecných typů
[CA1008](ca1008.md) | Výčty by měly mít nulovou hodnotu
[CA1010](ca1010.md) | Kolekce musí implementovat obecné rozhraní
[CA1012](ca1012.md) | Abstraktní typy by neměly mít konstruktory
[CA1014](ca1014.md) | Označte sestavení pomocí CLSCompliant
[CA1016](ca1016.md) | Označit sestavení verzí sestavení
[CA1017](ca1017.md) | Označte sestavení pomocí ComVisible
[CA1018](ca1018.md) | Označte atributy pomocí AttributeUsageAttribute
[CA1019](ca1019.md) | Definujte přístupové objekty pro argumenty atributů
[CA1021](ca1021.md) | Vyhněte se výstupním parametrům
[CA1024](ca1024.md) | Použijte vlastnosti, kde je to vhodné
[CA1027](ca1027.md) | Označte výčty pomocí FlagsAttribute
[CA1028](ca1028.md) | Úložiště výčtu by měl být Int32
[CA1030](ca1030.md) | Použijte události, kde je to vhodné
[CA1031](ca1031.md) | Nezachycujte výjimky obecného typu
[CA1032](ca1032.md) | Implementujte standardní konstruktory výjimky
[CA1033](ca1033.md) | Metody rozhraní by měly být volatelné podřízenými typy
[CA1034](ca1034.md) | Vnořené typy by neměly být viditelné
[CA1036](ca1036.md) | Přepište metody u srovnatelných typů
[CA1040](ca1040.md) | Vyhněte se prázdným rozhraním
[CA1041](ca1041.md) | Poskytněte zprávu ObsoleteAttribute
[CA1043](ca1043.md) | Použít celočíselný nebo řetězcový argument pro indexery
[CA1044](ca1044.md) | Vlastnosti by neměly být pouze pro zápis
[CA1045](ca1045.md) | Nepředávejte typy odkazem
[CA1046](ca1046.md) | Nepřetěžujte operátory rovnosti u odkazových typů
[CA1047](ca1047.md) | Nedeklarujte chráněné členy v zapečetěných typech
[CA1050](ca1050.md) | Deklarujte typy v oborech názvů
[CA1051](ca1051.md) | Nedeklarujte viditelná pole instance
[CA1052](ca1052.md) | Statické typy držitelů by měly být statické nebo NotInheritable.
[CA1053](ca1053.md) | Typy statických držitelů by neměly mít konstruktory (CA1053 je součást [CA1052](ca1052.md) pro analyzátory FxCop).
[CA1054](ca1054.md) | Parametry identifikátoru URI by neměly být řetězce
[CA1055](ca1055.md) | Návratové hodnoty identifikátoru URI by neměly být řetězce
[CA1056](ca1056.md) | Vlastnosti identifikátoru URI by neměly být řetězce
[CA1058](ca1058.md) | Typy by neměly rozšiřovat určité základní typy
[CA1060](ca1060.md) | Přesunout PInvoke do nativní třídy metod
[CA1061](ca1061.md) | Neskrývejte metody základní třídy
[CA1062](ca1062.md) | Ověřte argumenty veřejných metod
[CA1063](ca1063.md) | Implementovat správně IDisposable
[CA1064](ca1064.md) | Výjimky by měly být veřejné
[CA1065](ca1065.md) | Nevyvolávejte výjimky v neočekávaných umístěních
[CA1066](ca1066.md) | Typ {0} by měl implementovat IEquatable \<T> , protože přepisuje rovnost
[CA1067](ca1067.md) | Přepsat Object. Equals (Object) při implementaci IEquatable\<T>
[CA1303](ca1303.md) | Nepředávejte literály jako lokalizované parametry
[CA1304](ca1304.md) | Určete CultureInfo
[CA1305](ca1305.md) | Určete IFormatProvider
[CA1307](ca1307.md) | Zadejte StringComparison pro přehlednost.
[CA1308](ca1308.md) | Normalizujte řetězce na velká písmena
[CA1309](ca1309.md) | Použít ordinální porovnávání řetězců
[CA1401](ca1401.md) | Volání nespravovaných kódů by neměla být viditelná
[CA1501](ca1501.md) | Vyhněte se nadměrné dědičnosti
[CA1502](ca1502.md) | Vyhněte se nadměrné složitosti
[CA1505](ca1505.md) | Vyhněte se neudržovatelnému kódu
[CA1506](ca1506.md) | Vyhněte se nadměrnému párování tříd
[CA1700](ca1700.md) | Nepojmenovávejte výčty hodnot 'Reserved'
[CA1707](ca1707.md) | Identifikátory by neměly obsahovat podtržítka
[CA1708](ca1708.md) | Identifikátory by se měly lišit více než použitím malých a velkých písmen
[CA1710](ca1710.md) | Identifikátory by měly mít správnou příponu
[CA1711](ca1711.md) | Identifikátory by neměly mít nesprávnou příponu
[CA1712](ca1712.md) | Nezačínejte hodnoty výčtu názvem typu
[CA1713](ca1713.md) | Události by neměly mít předponu před nebo po
[CA1714](ca1714.md) | Výčty příznaků by neměly mít názvy v množném čísle
[CA1715](ca1715.md) | Identifikátory by měly mít správnou předponu
[CA1716](ca1716.md) | Identifikátory by se neměly shodovat s klíčovými slovy
[CA1717](ca1717.md) | Pouze výčty FlagsAttribute by měly mít názvy v množném čísle
[CA1720](ca1720.md) | Identifikátor obsahuje název typu.
[CA1721](ca1721.md) | Názvy vlastností by se neměly shodovat s metodami Get
[CA1724](ca1724.md) | Názvy typů by neměly odpovídat oborům názvů
[CA1725](ca1725.md) | Názvy parametrů by měly odpovídat základní deklaraci
[CA1801](ca1801.md) | Zkontrolujte nepoužité parametry
[CA1802](ca1802.md) | Použijte literály, kde je to vhodné
[CA1805](ca1805.md) | Neinicializovat zbytečně
[CA1806](ca1806.md) | Neignorujte výsledky metody
[CA1810](ca1810.md) | Inicializujte odkazový typ statického pole vloženě
[CA1812](ca1812.md) | Vyhněte se nevytvořeným instancím interních tříd
[CA1813](ca1813.md) | Vyhněte se nezapečetěným atributům
[CA1814](ca1814.md) | Upřednostněte vícenásobná pole před multidimenzionálními
[CA1815](ca1815.md) | Přepište rovnosti a operátory rovnosti u typů hodnot
[CA1816](ca1816.md) | Metody Dispose by měly volat SuppressFinalize
[CA1819](ca1819.md) | Vlastnosti by neměly vracet pole
[CA1820](ca1820.md) | Testujte prázdné řetězce pomocí délky řetězce
[CA1821](ca1821.md) | Odebrat prázdné finalizační metody
[CA1822](ca1822.md) | Označte členy jako statické
[CA1823](ca1823.md) | Vyhněte se nepoužitým privátním polím
[CA1824](ca1824.md) | Označte sestavení pomocí NeutralResourcesLanguageAttribute
[CA1825](ca1825.md) | Vyhněte se přidělení pole s nulovou délkou.
[CA2000](ca2000.md) | Uvolňujte objekty před ztrátou oboru
[CA2002](ca2002.md) | Nepoužívejte zámky u objektů se slabou identitou
[CA2100](ca2100.md) | Zkontrolujte chyby zabezpečení u dotazů SQL
[CA2101](ca2101.md) | Určete zařazování pro argumenty řetězce volání nespravovaného kódu
[CA2109](ca2109.md) | Zkontrolujte viditelné obslužné rutiny událostí
[CA2119](ca2119.md) | Zapečeťte metody, které vyhovují privátním rozhraním
[CA2153](ca2153.md) | Nezachytit poškozené výjimky stavu
[CA2200](ca2200.md) | Znovu vyvolejte pro zachování podrobností zásobníku.
[CA2201](ca2201.md) | Nevyvolávejte vyhrazené typy výjimek
[CA2207](ca2207.md) | Inicializujte statická pole s typem hodnoty vloženě
[CA2208](ca2208.md) | Vytvořte správně instance výjimky argumentu
[CA2211](ca2211.md) | Nekonstantní pole by neměla být viditelná
[CA2213](ca2213.md) | Uvolnitelná pole by měla být uvolněna
[CA2214](ca2214.md) | Nevolejte přepisovatelné metody v konstruktorech
[CA2215](ca2215.md) | Metody Dispose by měly volat uvolnění základní třídy
[CA2216](ca2216.md) | Uvolnitelné typy by měly deklarovat finalizační metodu
[CA2217](ca2217.md) | Neoznačujte výčty pomocí FlagsAttribute
[CA2219](ca2219.md) | Nevyvolávání výjimek v klauzulích finally
[CA2225](ca2225.md) | Přetížení operátoru mají pojmenované alternativy
[CA2226](ca2226.md) | Operátory by měly mít symetrická přetížení
[CA2227](ca2227.md) | Vlastnosti kolekce by měly být pouze pro čtení
[CA2229](ca2229.md) | Implementujte serializační konstruktory
[CA2231](ca2231.md) | Operátor přetížení se rovná překrytí typu hodnoty Equals.
[CA2234](ca2234.md) | Předání objektů identifikátoru URI systému místo řetězců
[CA2235](ca2235.md) | Označte všechna neserializovatelná pole
[CA2237](ca2237.md) | Označte typy ISerializable s serializovatelným
[CA2241](ca2241.md) | Zadejte správné argumenty pro metody formátování
[CA2242](ca2242.md) | Testujte správně NaN
[CA2243](ca2243.md) | Řetězcové literály atributů by se měly správně parsovat
[CA2300](ca2300.md) | Nepoužívat nezabezpečený deserializátor BinaryFormatter
[CA2301](ca2301.md) | Nevolat BinaryFormatter.Deserialize dříve, než se nastaví BinaryFormatter.Binder
[CA2302](ca2302.md) | Než zavoláte BinaryFormatter.Deserialize, ujistěte se, že je nastavený BinaryFormatter.Binder
[CA2305](ca2305.md) | Nepoužívat nezabezpečený deserializátor LosFormatter
[CA2310](ca2310.md) | Nepoužívat nezabezpečený deserializátor NetDataContractSerializer
[CA2311](ca2311.md) | Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Před deserializací se ujistěte, že je nastavený NetDataContractSerializer.Binder
[CA2315](ca2315.md) | Nepoužívat nezabezpečený deserializátor ObjectStateFormatter
[CA2321](ca2321.md) | Nedeserializovat se třídou JavaScriptSerializer pomocí třídy SimpleTypeResolver
[CA2322](ca2322.md) | Před deserializaci se ujistěte se, že třída JavaScriptSerializer není inicializována pomocí třídy SimpleTypeResolver
[CA3001](ca3001.md) | Zkontrolujte ohrožení zabezpečení injektáží SQL v kódu
[CA3002](ca3002.md) | Zkontrolujte ohrožení zabezpečení proti XSS v kódu
[CA3003](ca3003.md) | Zkontrolujte ohrožení zabezpečení injektáží cesty k souboru v kódu
[CA3004](ca3004.md) | Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu
[CA3005](ca3005.md) | Zkontrolujte ohrožení zabezpečení injektáží protokolu LDAP v kódu
[CA3006](ca3006.md) | Zkontrolujte ohrožení zabezpečení injektáží příkazu procesu v kódu
[CA3007](ca3007.md) | Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu
[CA3008](ca3008.md) | Zkontrolujte ohrožení zabezpečení injektáží XPath v kódu
[CA3009](ca3009.md) | Zkontrolujte ohrožení zabezpečení injektáží XML v kódu
[CA3010](ca3010.md) | Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu
[CA3011](ca3011.md) | Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu
[CA3012](ca3012.md) | Zkontrolujte ohrožení zabezpečení injektáží regulárního výrazu v kódu
[CA3061](ca3061.md) | Nepřidávat schéma podle adresy URL
[CA3075](ca3075.md) | Nezabezpečené zpracování DTD v XML
[CA3076](ca3076.md) | Nezabezpečené zpracování skriptu XSLT
[CA3077](ca3077.md) | Nezabezpečené zpracování v návrzích rozhraní API, XmlDocument a XmlTextReader
[CA3147](ca3147.md) | Označit obslužné rutiny operací s tokenem ověření antipadělání
[CA5350](ca5350.md) | Nepoužívejte slabé kryptografické algoritmy
[CA5351](ca5351.md) | Nepoužívejte nefunkční kryptografické algoritmy.
[CA5358](ca5358.md) | Nepoužívat nezabezpečené režimy šifrování
CA5359 | Nezakázat ověřování certifikátu
CA5360 | Nevolat nebezpečné metody v deserializaci
[CA5361](ca5361.md) | Nepovolujte používání SChannel silného šifrování.
CA5362 | Neodkazovat na sebe jako na serializovatelných třídách
[CA5363](ca5363.md) | Nezakázat ověřování žádostí
[CA5364](ca5364.md) | Nepoužívat zastaralé protokoly zabezpečení
CA5365 | Nezakázat kontrolu hlaviček protokolu HTTP
CA5366 | Použití XmlReader pro čtení XML pro datovou sadu
CA5367 | Neserializovat typy s poli ukazatelů
CA5368 | Nastavit ViewStateUserKey pro třídy odvozené ze stránky
[CA5369](ca5369.md) | Použít XmlReader pro deserializaci
[CA5370](ca5370.md) | Použití XmlReader k ověření čtecího zařízení
[CA5371](ca5371.md) | Použít XmlReader pro čtení schématu
[CA5372](ca5372.md) | Použití XmlReader pro XPathDocument
[CA5373](ca5373.md) | Nepoužívat zastaralou funkci odvození klíče
CA5374 | Nepoužívat XslTransform
CA5375 | Nepoužívat sdílený přístupový podpis účtu
CA5376 | Použití SharedAccessProtocol HttpsOnly
CA5377 | Použít zásady přístupu na úrovni kontejneru
[CA5378](ca5378.md) | Nezakazujte ServicePointManagerSecurityProtocols
CA5379 | Nepoužívejte slabý algoritmus funkce odvození klíče.
CA9999 | Neshoda verze analyzátoru

## <a name="see-also"></a>Viz také

- [Pravidla Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
