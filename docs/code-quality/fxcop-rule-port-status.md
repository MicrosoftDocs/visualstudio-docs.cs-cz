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
ms.openlocfilehash: 945b26158da4c4c7788570db0c565ebbcfc2b460
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658578"
---
# <a name="fxcop-rule-port-status"></a>Stav portu pravidla FxCop

Pokud jste dříve používali analýzu statického kódu v aplikaci Visual Studio, můžete si všimnout, že tato pravidla jsou k dispozici v aktuální implementaci jako [analyzátory FxCop](install-fxcop-analyzers.md). Tato stránka obsahuje seznam pravidel, která byla předaná. Podívejte se na nepřipojená [pravidla](fxcop-unported-rules.md) pro ty, které se nedostaly do portu a zda existují plány pro jejich přenos.

## <a name="ported-rules"></a>Přenesená pravidla

[Stránka pro automaticky generovanou dokumentaci](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) v úložišti Roslyn-Analyzer obsahuje nejaktuálnější seznam pravidel, která byla předaná do analyzátorů FxCop. Tato stránka obsahuje také další informace, například zda je pravidlo povoleno ve výchozím nastavení a zda má přidruženou *opravu kódu*. ([Opravy kódu](../ide/quick-actions.md) jsou dostupné opravy jedním kliknutím v nabídce ikony žárovky v aplikaci Visual Studio.)

Od data na této stránce seznam pravidel FxCop, která byla předaná do [analyzátorů FxCop](install-fxcop-analyzers.md) , zahrnují:

ID pravidla | Nadpis
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Nedeklarujte statické členy v obecných typech
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Nezveřejňujte obecné seznamy
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Použijte instance obecných obslužných rutin události
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Vyhněte se nadbytečným parametrům u obecných typů
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Výčty by měly mít nulovou hodnotu
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Kolekce musí implementovat obecné rozhraní
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Abstraktní typy by neměly mít konstruktory
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Označte sestavení pomocí CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Označit sestavení verzí sestavení
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Označte sestavení pomocí ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Označte atributy pomocí AttributeUsageAttribute
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Definujte přístupové objekty pro argumenty atributů
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Vyhněte se výstupním parametrům
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Použijte vlastnosti, kde je to vhodné
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Označte výčty pomocí FlagsAttribute
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Úložiště výčtu by měl být Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Použijte události, kde je to vhodné
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Nezachycujte výjimky obecného typu
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Implementujte standardní konstruktory výjimky
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Metody rozhraní by měly být volatelné podřízenými typy
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Vnořené typy by neměly být viditelné
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Přepište metody u srovnatelných typů
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Vyhněte se prázdným rozhraním
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Poskytněte zprávu ObsoleteAttribute
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Použít celočíselný nebo řetězcový argument pro indexery
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Vlastnosti by neměly být pouze pro zápis
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Nepředávejte typy odkazem
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Nepřetěžujte operátory rovnosti u odkazových typů
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Nedeklarujte chráněné členy v zapečetěných typech
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Deklarujte typy v oborech názvů
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Nedeklarujte viditelná pole instance
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Statické typy držitelů by měly být statické nebo NotInheritable.
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Typy statických držitelů by neměly mít konstruktory (CA1053 je součást [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) pro analyzátory FxCop).
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Parametry identifikátoru URI by neměly být řetězce
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Návratové hodnoty identifikátoru URI by neměly být řetězce
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Vlastnosti identifikátoru URI by neměly být řetězce
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Typy by neměly rozšiřovat určité základní typy
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Přesunout PInvoke do nativní třídy metod
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Neskrývejte metody základní třídy
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Ověřte argumenty veřejných metod
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Implementovat správně IDisposable
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Výjimky by měly být veřejné
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Nevyvolávejte výjimky v neočekávaných umístěních
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | Typ {0} by měl implementovat IEquatable \<T> , protože přepisuje rovnost
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Přepsat Object. Equals (Object) při implementaci IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Nepředávejte literály jako lokalizované parametry
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Určete CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Určete IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Zadejte StringComparison pro přehlednost.
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Normalizujte řetězce na velká písmena
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Použít ordinální porovnávání řetězců
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | Volání nespravovaných kódů by neměla být viditelná
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Vyhněte se nadměrné dědičnosti
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Vyhněte se nadměrné složitosti
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Vyhněte se neudržovatelnému kódu
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Vyhněte se nadměrnému párování tříd
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Nepojmenovávejte výčty hodnot 'Reserved'
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Identifikátory by neměly obsahovat podtržítka
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Identifikátory by se měly lišit více než použitím malých a velkých písmen
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Identifikátory by měly mít správnou příponu
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Identifikátory by neměly mít nesprávnou příponu
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Nezačínejte hodnoty výčtu názvem typu
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Události by neměly mít předponu před nebo po
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Výčty příznaků by neměly mít názvy v množném čísle
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Identifikátory by měly mít správnou předponu
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Identifikátory by se neměly shodovat s klíčovými slovy
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Pouze výčty FlagsAttribute by měly mít názvy v množném čísle
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | Identifikátor obsahuje název typu.
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Názvy vlastností by se neměly shodovat s metodami Get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Názvy typů by neměly odpovídat oborům názvů
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Názvy parametrů by měly odpovídat základní deklaraci
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Zkontrolujte nepoužité parametry
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Použijte literály, kde je to vhodné
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Neinicializovat zbytečně
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Neignorujte výsledky metody
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Inicializujte odkazový typ statického pole vloženě
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Vyhněte se nevytvořeným instancím interních tříd
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Vyhněte se nezapečetěným atributům
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Upřednostněte vícenásobná pole před multidimenzionálními
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Přepište rovnosti a operátory rovnosti u typů hodnot
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Metody Dispose by měly volat SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Vlastnosti by neměly vracet pole
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Testujte prázdné řetězce pomocí délky řetězce
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Odebrat prázdné finalizační metody
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Označte členy jako statické
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Vyhněte se nepoužitým privátním polím
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Označte sestavení pomocí NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Vyhněte se přidělení pole s nulovou délkou.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Uvolňujte objekty před ztrátou oboru
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Nepoužívejte zámky u objektů se slabou identitou
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Zkontrolujte chyby zabezpečení u dotazů SQL
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Určete zařazování pro argumenty řetězce volání nespravovaného kódu
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Zkontrolujte viditelné obslužné rutiny událostí
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Zapečeťte metody, které vyhovují privátním rozhraním
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Nezachytit poškozené výjimky stavu
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Znovu vyvolejte pro zachování podrobností zásobníku.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Nevyvolávejte vyhrazené typy výjimek
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Inicializujte statická pole s typem hodnoty vloženě
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Vytvořte správně instance výjimky argumentu
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Nekonstantní pole by neměla být viditelná
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Uvolnitelná pole by měla být uvolněna
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Nevolejte přepisovatelné metody v konstruktorech
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Metody Dispose by měly volat uvolnění základní třídy
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Uvolnitelné typy by měly deklarovat finalizační metodu
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Neoznačujte výčty pomocí FlagsAttribute
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Nevyvolávání výjimek v klauzulích finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Přetížení operátoru mají pojmenované alternativy
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Operátory by měly mít symetrická přetížení
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Vlastnosti kolekce by měly být pouze pro čtení
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Implementujte serializační konstruktory
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Operátor přetížení se rovná překrytí typu hodnoty Equals.
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Předání objektů identifikátoru URI systému místo řetězců
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Označte všechna neserializovatelná pole
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Označte typy ISerializable s serializovatelným
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Zadejte správné argumenty pro metody formátování
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Testujte správně NaN
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Řetězcové literály atributů by se měly správně parsovat
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Nepoužívat nezabezpečený deserializátor BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | Nevolat BinaryFormatter.Deserialize dříve, než se nastaví BinaryFormatter.Binder
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Než zavoláte BinaryFormatter.Deserialize, ujistěte se, že je nastavený BinaryFormatter.Binder
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Nepoužívat nezabezpečený deserializátor LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Nepoužívat nezabezpečený deserializátor NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Před deserializací se ujistěte, že je nastavený NetDataContractSerializer.Binder
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Nepoužívat nezabezpečený deserializátor ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Nedeserializovat se třídou JavaScriptSerializer pomocí třídy SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Před deserializaci se ujistěte se, že třída JavaScriptSerializer není inicializována pomocí třídy SimpleTypeResolver
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Zkontrolujte ohrožení zabezpečení injektáží SQL v kódu
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Zkontrolujte ohrožení zabezpečení proti XSS v kódu
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Zkontrolujte ohrožení zabezpečení injektáží cesty k souboru v kódu
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Zkontrolujte ohrožení zabezpečení injektáží protokolu LDAP v kódu
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Zkontrolujte ohrožení zabezpečení injektáží příkazu procesu v kódu
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Zkontrolujte ohrožení zabezpečení injektáží XPath v kódu
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Zkontrolujte ohrožení zabezpečení injektáží XML v kódu
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Zkontrolujte ohrožení zabezpečení injektáží regulárního výrazu v kódu
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Nepřidávat schéma podle adresy URL
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Nezabezpečené zpracování DTD v XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Nezabezpečené zpracování skriptu XSLT
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Nezabezpečené zpracování v návrzích rozhraní API, XmlDocument a XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Označit obslužné rutiny operací s tokenem ověření antipadělání
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Nepoužívejte slabé kryptografické algoritmy
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Nepoužívejte nefunkční kryptografické algoritmy.
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Nepoužívat nezabezpečené režimy šifrování
CA5359 | Nezakázat ověřování certifikátu
CA5360 | Nevolat nebezpečné metody v deserializaci
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Nepovolujte používání SChannel silného šifrování.
CA5362 | Neodkazovat na sebe jako na serializovatelných třídách
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Nezakázat ověřování žádostí
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Nepoužívat zastaralé protokoly zabezpečení
CA5365 | Nezakázat kontrolu hlaviček protokolu HTTP
CA5366 | Použití XmlReader pro čtení XML pro datovou sadu
CA5367 | Neserializovat typy s poli ukazatelů
CA5368 | Nastavit ViewStateUserKey pro třídy odvozené ze stránky
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Použít XmlReader pro deserializaci
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Použití XmlReader k ověření čtecího zařízení
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Použít XmlReader pro čtení schématu
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Použití XmlReader pro XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Nepoužívat zastaralou funkci odvození klíče
CA5374 | Nepoužívat XslTransform
CA5375 | Nepoužívat sdílený přístupový podpis účtu
CA5376 | Použití SharedAccessProtocol HttpsOnly
CA5377 | Použít zásady přístupu na úrovni kontejneru
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Nezakazujte ServicePointManagerSecurityProtocols
CA5379 | Nepoužívejte slabý algoritmus funkce odvození klíče.
CA9999 | Neshoda verze analyzátoru

## <a name="see-also"></a>Viz také

- [Pravidla Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
