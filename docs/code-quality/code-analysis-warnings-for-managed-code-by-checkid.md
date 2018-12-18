---
title: Upozornění Analýzy kódu pro spravovaný kód podle CheckId
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 87fc6bdda65bf06b344a0971fb255555914e3102
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053033"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Upozornění analýzy kódu pro spravovaný kód podle CheckId

Následující tabulka obsahuje seznam upozornění analýzy kódu pro spravovaný kód podle identifikátoru upozornění CheckId.

| CheckId | Upozornění | Popis |
|---------| - | - |
| CA1000 | [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md) | Při volání statického členu obecného typu musí být pro tento typ zadán argument typu. Je-li zavolán obecný člen instance, který nepodporuje odvozování, musí být pro tento člen zadán argument typu. V těchto dvou případech je syntaxe zadávání argumentu typu různá a snadno zaměnitelná. |
| CA1001 | [CA1001: Typy vlastních uvolnitelných polí, které by měly být uvolnitelné](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Třída deklaruje a implementuje pole instance typu System.IDisposable, přičemž neimplementuje rozhraní IDisposable. Třída, která deklaruje pole IDisposable nepřímo, vlastní nespravovaný zdroj a měla by rozhraní IDisposable implementovat. |
| CA1002 | [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md) | Třída System.Collections.Generic.List < (ze \<(T >) >) je obecná kolekce navržená pro výkon, nikoli dědičnost. Proto třída List neobsahuje žádné virtuální členy. Místo ní by měly být vystaveny kolekce navržené pro dědičnost. |
| CA1003 | [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md) |Typ obsahuje delegát vracející hodnotu void, jehož předpis obsahuje dva parametry (první je objekt a druhý typ přiřaditelný do typu EventArgs), a příslušné sestavení zacíleno na rozhraní Microsoft .NET Framework 2.0. |
| CA1004 | [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md) | Argument typu obecné metody je z argumentu typu předávaného metodě odvozen namísto explicitního určení argumentu typu. Má-li být odvozování povoleno, musí předpis parametrů obecné metody zahrnovat parametr stejného typu jako parametr typu metody. V tomto případě nemusí být argument typu zadán. Používáte-li odvození pro všechny parametry typu, je syntaxe volání obecných a neobecných metod instancí identická, což zjednodušuje použití obecných metod. |
| CA1005 | [CA1005: Vyhněte se nadbytečným parametrům na obecných typech](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md) | Čím více parametrů typu obecný typ obsahuje, tím obtížnější je vědět a zapamatovat si, co každý z parametrů typu představuje. To je obvykle zřejmé s jedním parametrem typu, stejně jako v seznamu\<T > a v některých případech se dvěma parametry typu, například u třídy Dictionary\<TKey, TValue >. Pokud však existují více než dva parametry typu, stává se pro většinu uživatelů použití příliš obtížným. |
| CA1006 | [CA1006: Nevnořujte obecné typy v signaturách členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md) | Vnořený typ argumentu je typ argumentu, který je také obecným typem. Chce-li uživatel zavolat člen, jehož předpis obsahuje vnořený argument typu, musí nejprve vytvořit instanci jednoho obecného typu a předat tento typ konstruktoru druhého obecného typu. Potřebná procedura a syntaxe je složitá a je vhodné se jí vyhnout. |
| CA1007 |[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md) | Externě viditelná metoda obsahuje referenční parametr typu System.Object. Použitím obecných metod lze metodě předávat všechny typy (s určitými omezeními) bez předchozího přetypování typu na referenční typ parametru. |
| CA1008 | [CA1008: Výčty by měly mít nulovou hodnotu](../code-quality/ca1008-enums-should-have-zero-value.md) | Výchozí hodnota neinicializovaného výčtu je stejně jako u jiných typů hodnot nula. Atributovaný výčet bez příznaků by měl definovat člen za použití hodnoty nula tak, aby výchozí hodnota byla platnou hodnotou výčtu. Definuje-li výčet, který má aplikován atribut FlagsAttribute, člen s hodnotou nula, měl by jeho název být „None“, aby tak označoval, že ve výčtu nebyly nastaveny žádné hodnoty. |
| CA1009 | [CA1009: Deklarujte správně obslužné rutiny událostí](../code-quality/ca1009-declare-event-handlers-correctly.md) | Metody zpracování událostí přebírají dva parametry. První je typu System.Object a je pojmenován „sender“. Je jím objekt, který vyvolal událost. Druhý parametr je typu System.EventArgs a je pojmenován „e“. Představuje data přidružená k události. Metody zpracování událostí by neměly vracet hodnotu; v programovacím jazyce C# je toto označeno návratovým typem void. |
| CA1010 | [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md) | Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Pak lze tuto kolekci použít k zaplnění typů obecných kolekcí. |
| CA1011 |[CA1011: Zvažte předání základních typů jako parametrů](../code-quality/ca1011-consider-passing-base-types-as-parameters.md) | Je-li v deklaraci metody zadán jako parametr základní typ, lze jako příslušný argument k metodě předat kterýkoliv typ odvozený z tohoto základního typu. Pokud není dodatečná funkčnost poskytovaná odvozeným typem parametru vyžadována, umožňuje použití základního typu širší využití metody. |
| CA1012 | [CA1012: Abstraktní typy by neměly mít konstruktory](../code-quality/ca1012-abstract-types-should-not-have-constructors.md) | Konstruktory abstraktních typů mohou být volány pouze odvozenými typy. Jelikož veřejné konstruktory vytvářejí instance typu, přičemž nelze vytvořit instance abstraktního typu, je abstraktní typ obsahující veřejný konstruktor nesprávně navržen. |
| CA1013 | [CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md) | Veřejný nebo chráněný typ implementuje operátory sčítání a odčítání, aniž by implementoval operátor rovnosti. |
| CA1014 | [CA1014: Označte sestavení pomocí atributu CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md) | Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh přikazuje, aby všechna sestavení explicitně uvedla dodržování specifikace CLS pomocí <xref:System.CLSCompliantAttribute> . Není-li tento atribut v sestavení přítomen, nedodržuje sestavení specifikaci. |
| CA1016 | [CA1016: Označte sestavení pomocí atributu AssemblyVersionAttribute](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md) | Rozhraní .NET Framework používá číslo verze k jednoznačné identifikaci sestavení a pro svázání s typy v sestaveních se silným názvem. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny. |
| CA1017 | [CA1017: Označte sestavení pomocí atributu ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md) |Atribut ComVisibleAttribute určuje způsob přístupu klientů COM ke spravovanému kódu. Dobrý návrh přikazuje, aby sestavení explicitně uvedla viditelnost modelu COM. Viditelnost modelu COM může být nastavena pro celé sestavení a poté přepsána pro jednotlivé typy a členy typů. Není-li tento atribut přítomen, je obsah sestavení viditelný klientům COM. |
| CA1018 | [CA1018: Označte atributy pomocí AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md) | Při definování vlastního atributu jej označte použitím atributu AttributeUsageAttribute, čímž je určeno, kde ve zdrojovém kódu může být vlastní atribut použit. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. |
| CA1019 | [CA1019: Definujte přístupové objekty pro argumenty atributu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) | Atributy mohou definovat povinné argumenty, které musí být specifikovány při použití atributu na cíl. Říká se jim také poziční argumenty, jelikož jsou konstruktorům atributů předány jako poziční parametry. Pro každý povinný argument by měl atribut navíc poskytovat odpovídající vlastnost jen pro čtení, aby mohla být hodnota argumentu během spuštění získána. Atributy mohou také definovat volitelné argumenty, které jsou rovněž známy jako pojmenované argumenty. Tyto argumenty jsou podle názvu poskytovány konstruktorům atributů a měly by mít odpovídající vlastnost pro čtení i zápis. |
| CA1020 | [CA1020: Vyvarujte se oborům názvu s malým množstvím typů](../code-quality/ca1020-avoid-namespaces-with-few-types.md) | Ujistěte se, že všechny obory názvů mají logické uspořádání a že je vložení typů do řídce zaplněných oborů názvů odůvodněné. |
| CA1021 | [CA1021: Vyhněte se výstupním parametrům](../code-quality/ca1021-avoid-out-parameters.md) | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů, a schopnost práce s metodami vracejícími více návratových typů. Také rozdíl mezi parametry „out“ a „ref“ není běžně chápán. |
| CA1023 | [CA1023: Indexery by neměly být multidimenzionální](../code-quality/ca1023-indexers-should-not-be-multidimensional.md) | Indexery (tj. indexované vlastnosti) by měly používat jediný index. Vícerozměrné indexery mohou výrazně snížit použitelnost knihovny. |
| CA1024 | [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024-use-properties-where-appropriate.md) | Veřejná nebo chráněná metoda má název začínající na „Get“, nepřijímá žádné parametry a vrací hodnotu, která není polem. Metoda může být dobrým kandidátem, aby se stala vlastností. |
| CA1025 | [CA1025: Nahraďte opakované argumenty polem parametrů](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md) | Není-li znám přesný počet argumentů a jsou-li proměnné argumenty stejného typu (nebo je lze předat jako stejný typ), použijte namísto opakovaných argumentů pole parametrů. |
| CA1026 | [CA1026: Neměly by být použity výchozí parametry](../code-quality/ca1026-default-parameters-should-not-be-used.md) | Ve specifikaci CLS jsou povoleny metody používající výchozí parametry, avšak specifikace CLS umožňuje kompilátorům ignorovat hodnoty přiřazené těmto parametrům. Chcete-li zachovat shodné chování napříč programovacími jazyky, měly by být metody používající výchozí parametry nahrazeny přetíženími metody, která výchozí parametry poskytují. |
| CA1027 |[CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md) | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Mohou-li být pojmenované konstanty smysluplně kombinovány, použijte ve výčtu atribut FlagsAttribute. |
| CA1028 | [CA1028: Úložiště výčtu by měl být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md) | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Ve výchozím nastavení je pro uložení konstantní hodnoty použit datový typ System.Int32. Přestože lze tento typ změnit, není to ve většině případů zapotřebí ani doporučováno. |
| CA1030 | [CA1030: Použijte události, kde je to vhodné](../code-quality/ca1030-use-events-where-appropriate.md) |Toto pravidlo zjišťuje metody, které mají názvy obvykle používané pro události. Je-li metoda volána jako odpověď na jednoznačně definovanou změnu stavu, měla by být metoda volána obslužnou rutinou události. Objekty volající tuto metodu by měly místo přímého volání metody vyvolat událost. |
| CA1031 | [CA1031: Nezachycujte výjimky obecného typu](../code-quality/ca1031-do-not-catch-general-exception-types.md) | Obecné výjimky by neměly být zachycovány. Zachyťte více specifickou výjimku nebo jako poslední příkaz v zachytávacím bloku opětovně vyvolejte obecnou výjimku. |
| CA1032 |[CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md) | Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. |
| CA1033 | [CA1033: Metody rozhraní by měly být volatelné podřízenými typy](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md) | Nezapečetěný externě viditelný typ poskytuje explicitní implementaci metod veřejného rozhraní a neposkytuje alternativní externě viditelnou metodu stejného názvu. |
| CA1034 | [CA1034: Vnořené typy by neměly být viditelné](../code-quality/ca1034-nested-types-should-not-be-visible.md) | Vnořený typ je typ deklarovaný v rámci jiného typu. Vnořené typy jsou užitečné pro zapouzdření soukromých podrobností implementace v daném typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné. |
| CA1035 | [CA1035: Implementace ICollection mají členy silného typu](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md) | Toto pravidlo vyžaduje, aby implementace rozhraní ICollection poskytovaly členy se silnými typy, aby uživatelé nemuseli při využívání funkčnosti poskytované rozhraním přetypovávat argumenty na typ Object. Toto pravidlo předpokládá, že typ implementuje rozhraní ICollection proto, aby mohl spravovat kolekci instancí typu silnějšího než Object. |
| CA1036 | [CA1036: Přepište metody srovnatelných typů](../code-quality/ca1036-override-methods-on-comparable-types.md) |Veřejný nebo chráněný typ implementuje rozhraní System.IComparable. Nepřepisuje metodu Object.Equals ani nepřetěžuje operátory rovnosti, nerovnosti, menší než a větší než specifické pro daný jazyk. |
| CA1038 | [CA1038: Enumerátory by měly být silného typu](../code-quality/ca1038-enumerators-should-be-strongly-typed.md) | Toto pravidlo vyžaduje, aby implementace rozhraní IEnumerator také poskytovaly verze vlastnosti Current se silnými typy, aby uživatelé nemuseli při použití funkčnosti poskytované tímto rozhraním přetypovávat návratovou hodnotu na silný typ. |
| CA1039 | [CA1039: Seznamy jsou silného typu](../code-quality/ca1039-lists-are-strongly-typed.md) | Toto pravidlo vyžaduje, aby implementace rozhraní IList poskytovaly členy se silnými typy, aby uživatelé nemuseli při využívání funkčnosti poskytované rozhraním přetypovávat argumenty na typ System.Object. |
| CA1040 |[CA1040: Vyhněte se prázdným rozhraním](../code-quality/ca1040-avoid-empty-interfaces.md) | Rozhraní definují členy ujednávající jejich chování nebo užití. Funkčnost popsaná rozhraním může být osvojena libovolným typem bez ohledu na to, kde se typ vyskytuje v hierarchii dědičnosti. Typ implementuje rozhraní tím, že poskytuje implementace jeho členů. Prázdné rozhraní nedefinuje žádné členy, tudíž ani nedefinuje žádná implementovatelná ujednání. |
| CA1041 | [CA1041: Poskytněte zprávu ObsoleteAttribute](../code-quality/ca1041-provide-obsoleteattribute-message.md) | Typ nebo člen je označen atributem System.ObsoleteAttribute, aniž by měl zadánu vlastnost ObsoleteAttribute.Message. Při kompilaci typu nebo členu označeného atributem ObsoleteAttribute je zobrazena vlastnost zprávy tohoto atributu. To uživateli poskytuje informace o zastaralém typu nebo členu. |
| CA1043 | [CA1043: Použijte celočíselný nebo řetězcový argument pro indexery](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md) | Indexery (tj. indexované vlastnosti) by měly jako index používat celočíselné typy nebo typy řetězců. Tyto typy se obvykle používají pro indexování datových struktur a zvyšují použitelnost knihovny. Použití typu Object by mělo být omezeno na ty případy, kdy během návrhu není možné určit konkrétní celočíselný nebo řetězcový typ. |
| CA1044 | [CA1044: Vlastnosti by neměly být pouze pro zápis](../code-quality/ca1044-properties-should-not-be-write-only.md) | Ačkoli je přijatelné a často nezbytné použít vlastnost jen pro čtení, směrnice návrhu zakazují použití vlastností jen pro zápis. Důvodem je skutečnost, že umožnit uživateli nastavit hodnotu a poté uživateli zabránit v zobrazení této hodnoty není bezpečné. Taktéž bez přístupu pro čtení není možné zobrazit stav sdílených objektů, což omezuje jejich užitečnost. |
| CA1045 |[CA1045: Nepředávejte typy odkazem](../code-quality/ca1045-do-not-pass-types-by-reference.md) | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů a schopnost práce s metodami vracejícími více návratových typů. Návrháři knihoven, kteří navrhují knihovny pro širokou veřejnost, by neměli očekávat schopnost uživatelů pracovat s parametry „out“ nebo „ref“. |
| CA1046 | [CA1046: Nepřetěžujte operátory rovnosti na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md) | U referenčních typů je výchozí implementace operátoru rovnosti téměř vždy správná. Ve výchozím nastavení jsou dva odkazy rovny, pouze pokud ukazují na stejný objekt. |
| CA1047 |[CA1047: Nedeklarujte chráněné členy v zapečetěných typech](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md) | Typy deklarují chráněné členy, aby k nim odvozené typy mohly přistupovat nebo je přepisovat. Dle definice nelze dědit zapečetěné typy, což znamená, že nelze volat chráněné metody zapečetěných typů. |
| CA1048 | [CA1048: Nedeklarujte virtuální členy v zapečetěných typech](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md) | Typy deklarují metody jako virtuální, aby odvozující typy mohly přepsat implementaci virtuální metody. Dle definice nelze zdědit zapečetěný typ. Díky tomu postrádá virtuální metoda u zapečetěného typu význam. |
| CA1049 | [CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md) | Typy, které přidělují nespravované prostředky, by měly implementovat rozhraní IDisposable a umožnit tak volajícím uvolnit tyto prostředky na požádání a zkrátit životní cyklus objektů, které je využívají. |
| CA1050 | [CA1050: Deklarujte typy v oborech názvů](../code-quality/ca1050-declare-types-in-namespaces.md) | Typy jsou deklarovány v oborech názvů, aby bylo zabráněno kolizím názvů a zároveň jako způsob organizace souvisejících typů v hierarchii objektů. |
| CA1051 | [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) | Hlavní použití pole by mělo být jako podrobnost implementace. Pole by měla být soukromá nebo vnitřní a měla by být vystavena s použitím vlastností. |
| CA1052 | [CA1052: Statický vlastník typů by měl být zapečetěný](../code-quality/ca1052-static-holder-types-should-be-sealed.md) | Veřejný nebo chráněný typ obsahuje pouze statické členy a není deklarován s použitím zapečetěného modifikátoru (NotInheritable) (jazyk C#). Typu, u nějž není zamýšleno dědění, by mělo být prostřednictvím označením zapečetěným modifikátorem zabráněno, aby byl použit jako základní typ. |
| CA1053 |[CA1053: Statický vlastník typů by neměl mít konstruktory](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md) | Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má veřejný nebo chráněný výchozí konstruktor. Konstruktor není nutný, protože volání statických členů nevyžaduje instanci typu. Z důvodu bezpečnosti a zabezpečení by řetězcová přetížení měla volat přetížení identifikátoru URI použitím argumentu řetězce. |
| CA1054 | [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md) | Pakliže metoda přijímá řetězcovou reprezentaci identifikátoru URI, mělo by být poskytnuto odpovídající přetížení přijímající instanci třídy URI, která tyto služby poskytuje bezpečným a zabezpečeným způsobem. |
| CA1055 | [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md) | Toto pravidlo předpokládá, že metoda vrací identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1056 | [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md) | Toto pravidlo předpokládá, že vlastnost reprezentuje identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1057 | [CA1057: Řetězcové přetížení identifikátoru URI volá přetížení System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md) | Typ deklaruje přetížení metod, které se liší pouze nahrazením řetězcového parametru parametrem System.Uri. Přetížení přijímající řetězcový parametr nevolá přetížení, které přijímá parametr URI. |
| CA1058 | [CA1058: Typy by neměly rozšířit určité základní typy](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | Externě viditelný typ rozšiřuje určité základní typy. Použijte jednu z alternativ. |
| CA1059 |[CA1059: Členové by neměli zveřejňovat určité konkrétní typy](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md) | Konkrétní typ je typ, který je zcela implementován, a lze tudíž vytvořit jeho instanci. Chcete-li umožnit široké využití členu, nahraďte konkrétní typ použitím navrhovaného rozhraní. |
| CA1060 | [CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md) | Metody vyvolání platformy, jako jsou ty, které jsou označeny pomocí atributu System.Runtime.InteropServices.DllImportAttribute, nebo metody, které jsou definovány pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], přístup k nespravovanému kódu. Tyto metody by měly patřit třídě NativeMethods, SafeNativeMethods nebo UnsafeNativeMethods. |
| CA1061 |[CA1061: Neskrývejte metody třídy base](../code-quality/ca1061-do-not-hide-base-class-methods.md) | Metoda základního typu je skryta identicky pojmenovanou metodou v odvozeném typu, kde je předpis parametrů odvozené metody odlišný od odpovídajících typů v předpisu parametrů základní metody pouze ve slaběji odvozených typech. |
| CA1062 | [CA1062: Ověřte argumenty veřejných metod](../code-quality/ca1062-validate-arguments-of-public-methods.md) | Všechny argumenty odkazu předané externě viditelným metodám by měly být porovnány s hodnotou NULL. |
| CA1063 | [CA1063: Implementuje správně IDisposable](../code-quality/ca1063-implement-idisposable-correctly.md) | Všechny typy IDisposable by měly správně implementovat vzor Dispose. |
| CA1064 | [CA1064: Výjimky by měly být veřejné](../code-quality/ca1064-exceptions-should-be-public.md) | Interní výjimka je viditelná pouze uvnitř svého vlastního vnitřního rozsahu. Jakmile výjimka přesáhne hranice vnitřního rozsahu, lze pro zachycení výjimky použít pouze základní výjimku. Pokud je vnitřní výjimka zděděna z <xref:System.Exception>, <xref:System.SystemException>, nebo <xref:System.ApplicationException>, externí kód nebude mít dostatečné informace o tom, co dělat, s výjimkou. |
| CA1065 | [CA1065: Nevyvolávejte výjimky v neočekávaných umístěních](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Metoda, u které není předpokládáno vyvolání výjimky, vyvolá výjimku. |
| CA1300 | [CA1300: Zadejte možnosti MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md) | Chcete-li správně zobrazit okno pro kultury, které používají směr čtení zprava doleva, musí být členy RightAlign a RtlReading výčtu MessageBoxOptions předány metodě Show. |
| CA1301 | [CA1301: Vyhněte se duplicitním akcelerátorům](../code-quality/ca1301-avoid-duplicate-accelerators.md) | Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Když má více ovládacích prvků duplicitní přístupové klávesy, není chování přístupové klávesy dobře definováno. |
| CA1302 | [CA1302: Nekódujte pevně řetězce závislé na národním prostředí](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md) | Výčet System.Environment.SpecialFolder obsahuje členy, které odkazují na speciální systémové složky. Umístění těchto složek mohou mít různé hodnoty v různých operačních systémech; uživatel může změnit některé z míst; a místa jsou lokalizována. Metoda Environment.GetFolderPath vrátí lokace, které jsou spojené s výčtem Environment.SpecialFolder, lokalizované a vhodné pro aktuálně spuštěný počítač. |
| CA1303 | [CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md) | Externě viditelná metoda předává řetězcový literál jako parametr do konstruktoru nebo metody v knihovně tříd rozhraní .NET Framework a tento řetězec by měl být lokalizovatelný. |
| CA1304 | [CA1304: Zadejte možnosti CultureInfo](../code-quality/ca1304-specify-cultureinfo.md) | Metoda nebo konstruktor volá člen, který má přetížení přijímající parametr System.Globalization.CultureInfo, a tato metoda nebo konstruktor nevolá přetížení přebírající parametr CultureInfo. Pokud objekt CultureInfo nebo System.IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1305 | [CA1305: Zadejte možnosti IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md) | Metoda nebo konstruktor volá jeden nebo více členů, které mají přetížení přijímající parametr System.IFormatProvider, a tato metoda nebo konstruktor nevolá přetížení, která přebírá parametr IFormatProvider. Pokud objekt System.Globalization.CultureInfo nebo IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1306 | [CA1306: Nastavte národního prostředí pro datové typy](../code-quality/ca1306-set-locale-for-data-types.md) | Národní prostředí určuje prvky prezentace specifické kultury pro data, například formátování použité pro číselné hodnoty, symboly měny a pořadí řazení. Při vytváření objektu DataSet nebo DataTable byste měli explicitně nastavit národní prostředí. |
| CA1307 | [CA1307: Zadejte možnosti StringComparison](../code-quality/ca1307-specify-stringcomparison.md) | Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison. |
| CA1308 |[CA1308: Normalizujte řetězce na velká písmena](../code-quality/ca1308-normalize-strings-to-uppercase.md) | Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků nedokáže po převodu na malá písmena provést zpáteční cestu. |
| CA1309 | [CA1309: Použijte řadový StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md) | Nelingvistická operace porovnání řetězců nemá nastaven parametr StringComparison na hodnotu Ordinal ani na hodnotu OrdinalIgnoreCase. Explicitním nastavením parametru na hodnotu StringComparison.Ordinal nebo StringComparison.OrdinalIgnoreCase dojde ke zrychlení kódu a zvýšení přesnosti a spolehlivosti. |
| CA1400 | [CA1400: Vstupní body volání nespravovaného kódu by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) |Veřejná nebo chráněná metoda je označena pomocí atributu System.Runtime.InteropServices.DllImportAttribute. Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně. |
| CA1401 | [CA1401: Volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | Veřejná nebo chráněná metoda veřejného typu má nastaven atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tyto metody by neměly být vystaveny. |
| CA1402 |[CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | Když jsou přetížené metody vystaveny klientům modulu COM, zachová svůj název pouze první přetížení metody. Následná přetížení jsou jednoznačně přejmenována přidáním podtržítka (_) a celého čísla odpovídajícího pořadí deklarace tohoto přetížení. |
| CA1403 | [CA1403: Typy automatického rozložení by neměly být viditelné modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | Hodnotový typ viditelný modulem COM je označen pomocí atributu System.Runtime.InteropServices.StructLayoutAttribute, nastaveného na hodnotu LayoutKind.Auto. Mezi verzemi rozhraní .NET Framework, což naruší klienty modulu COM, které očekávají specifické rozložení můžete změnit rozložení těchto typů. |
| CA1404 | [CA1404: Volejte GetLastError ihned po volání nespravovaného kódu](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Je provedeno volání metody Marshal.GetLastWin32Error nebo ekvivalentní [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] Funkce GetLastError a bezprostředně předchozí volání není pro operační systém volání metody. |
| CA1405 | [CA1405: Základní typy viditelného typu modelu COM by měly být viditelné modelu COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | Typ viditelný modulem COM je odvozen od typu, který není viditelný modulem COM. |
| CA1406 |[CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Klienty modulu COM jazyka Visual Basic 6 nemohou přistupovat k 64bitová celá čísla. |
| CA1407 |[CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | Modul COM nepodporuje statické metody. |
| CA1408 | [CA1408: Nepoužívejte AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Pokud ve výchozím nastavení není zadán atribut ClassInterfaceAttribute, použije se pouze rozhraní určené pro odesílání. |
| CA1409 | [CA1409: Viditelné typy modelu COM by měly být vytvořitelné](../code-quality/ca1409-com-visible-types-should-be-creatable.md) |Odkazový typ, který je označen jako viditelný modulům COM, obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů). Typ bez veřejného výchozího konstruktoru není možné vytvořit klienty typu COM. |
| CA1410 | [CA1410: Metody registrace modelu COM by si měly odpovídat](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | Typ deklaruje metodu, která je označena atributem System.Runtime.InteropServices.ComRegisterFunctionAttribute, ale nedeklaruje metodu označenou pomocí atributu System.Runtime.InteropServices.ComUnregisterFunctionAttribute, a naopak. |
| CA1411 | [CA1411: Metody registrace modelu COM by neměly být viditelné](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | Metoda označená pomocí atributu System.Runtime.InteropServices.ComRegisterFunctionAttribute nebo atributu System.Runtime.InteropServices.ComUnregisterFunctionAttribute je externě viditelná. |
| CA1412 | [CA1412: Označte rozhraní ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | Typ je označen atributem System.Runtime.InteropServices.ComSourceInterfacesAttribute a alespoň jedno ze zadaných rozhraní není označeno pomocí atributu System.Runtime.InteropServices.InterfaceTypeAttribute nastaveného na hodnotu ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Zkontrolujte obsah polí, zda neobsahují informace, které by neměly být vystaveny nebo které budou mít nežádoucí účinky na návrh nebo zabezpečení. |
| CA1414 | [CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Datový typ Boolean má v nespravovaném kódu různé reprezentace. |
| CA1415 | [CA1415: Deklarujte správně volání nespravovaných kódů](../code-quality/ca1415-declare-p-invokes-correctly.md) | Toto pravidlo vyhledá operační systém vyvolat deklarace metody, které se zaměřují [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] parametr struktury funkce, které mají ukazatel na OVERLAPPED a odpovídající spravovaný parametr není ukazatel System.Threading.NativeOverlapped. Struktura. |
| CA1500 | [CA1500: Názvy proměnných by neměly odpovídat názvům polí](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Metoda instance deklaruje parametr nebo lokální proměnnou, jejichž název odpovídá poli instance deklarovaného typu, což vede k chybám. |
| CA1501 | [CA1501: Vyhněte se nadměrné dědičnosti](../code-quality/ca1501-avoid-excessive-inheritance.md) | Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti. Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. |
| CA1502 | [CA1502: Vyhněte se nadměrné složitosti](../code-quality/ca1502-avoid-excessive-complexity.md) | Toto pravidlo měří počet lineárně nezávislých cest skrze metodu, což je určeno počtem a složitostí podmínkových větví. |
| CA1504 | [CA1504: Revize zavádějících názvů polí](../code-quality/ca1504-review-misleading-field-names.md) | Název pole instance začíná předponou "s_" a název statického pole (Shared v jazyce Visual Basic) začíná předponou "m_". |
| CA1505 | [CA1505: Vyhněte se neudržovatelnému kódu](../code-quality/ca1505-avoid-unmaintainable-code.md) | Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti. Nízký index udržovatelnosti označuje, že typ nebo metodu je pravděpodobně obtížné udržovat a je vhodné ji znovu navrhnout. |
| CA1506 |[CA1506: Vyhněte se nadměrnému párování tříd](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje. |
| CA1600 | [CA1600: Nepoužívejte prioritu nečinného procesu](../code-quality/ca1600-do-not-use-idle-process-priority.md) | Nenastavujte prioritu procesu na Neaktivní. Procesy, které mají nastaveny System.Diagnostics.ProcessPriorityClass.Idle, budou zaměstnávat procesor, pokud by jinak byl nečinný, a tím budou blokovat úsporný režim. |
| CA1601 | [CA1601: Nepoužívejte časovače, které zabraňují změně stavu napájení](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | Vyšší frekvence periodické aktivity budou udržovat procesor zaneprázdněný a ovlivňovat časovače úspory energie nečinnosti, které vypnou zobrazení a pevné disky. |
| CA1700 | [CA1700: Nepojmenovávejte výčty hodnot Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. |
| CA1701 | [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md) | Každé slovo řetězce zdroje je rozděleno na tokeny na základě velikosti písmen. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla. |
| CA1702 | [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md) | Název identifikátoru obsahuje více slov a alespoň jedno ze slov se zdá být složené slovo, které není správně formátováno. |
| CA1703 | [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md) | Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA1704 | [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md) | Název externě viditelného identifikátoru obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA1707 | [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md) | Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry. |
| CA1708 | [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md) | Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena. |
| CA1709 | [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md) | Podle konvence používají názvy parametrů zápis typu CamelCase a názvy oborů názvů, typů a členů používají zápis typu PascalCase. |
| CA1710 | [CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md) |Podle konvence by měly názvy typů, které rozšiřují některé základní typy nebo určitá rozhraní, nebo typů odvozených z těchto typů mít příponu přidruženou těmto typům nebo rozhraním. |
| CA1711 | [CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md) | Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony. |
| CA1712 | [CA1712: Nezačínejte hodnoty výčtu s názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md) | Názvy členů výčtu nemají předponu názvu typu, protože se očekává, že vývojové nástroje poskytují informace o typu. |
| CA1713 | [CA1713: Události by neměly mít předponu před nebo po](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md) | Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí. |
| CA1714 | [CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714-flags-enums-should-have-plural-names.md) | Veřejný výčet má atribut System.FlagsAttribute a jeho název nekončí písmenem „s“. Typy označené pomocí atributu FlagsAttribute mají názvy, které jsou v množném čísle, protože tento atribut označuje, že lze zadat více než jednu hodnotu. |
| CA1715 | [CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715-identifiers-should-have-correct-prefix.md) | Název externě viditelného rozhraní nezačíná velkým písmenem „I“. Název parametru obecného typu u externě viditelného typu nebo metody nezačíná velkým písmenem „T“. |
| CA1716 | [CA1716: Identifikátory by neměly odpovídat klíčovým slovům](../code-quality/ca1716-identifiers-should-not-match-keywords.md) | Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime). |
| CA1717 | [CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu. |
| CA1719 | [CA1719: Názvy parametrů by neměly odpovídat názvům členů](../code-quality/ca1719-parameter-names-should-not-match-member-names.md) | Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam členu. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou. |
| CA1720 |[CA1720: Identifikátory by neměly obsahovat názvy typů](../code-quality/ca1720-identifiers-should-not-contain-type-names.md) | Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka. |
| CA1721 | [CA1721: Názvy vlastností by neměly odpovídat metodám Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md) |Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce. |
| CA1722 | [CA1722: Identifikátory by neměly mít nesprávnou předponu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md) | Podle konvence mají pouze některé programovací prvky názvy začínající určitou předponou. |
| CA1724 | [CA1724: Názvy typů by neměly odpovídat oborům názvů](../code-quality/ca1724-type-names-should-not-match-namespaces.md) | Názvy typů by neměly odpovídat názvům obory názvů, které jsou definovány v knihovně tříd rozhraní .NET Framework. Porušení tohoto pravidla může snížit použitelnost knihovny. |
| CA1725 | [CA1725: Názvy parametrů by měly odpovídat základní deklaraci](../code-quality/ca1725-parameter-names-should-match-base-declaration.md) | Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody. |
| CA1726 | [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md) | Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Název případně obsahuje také výraz „Flag“ nebo „Flags“. |
| CA1800 | [CA1800: Nepřetypujte zbytečně](../code-quality/ca1800-do-not-cast-unnecessarily.md) | Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. |
| CA1801 | [CA1801: Revize nepoužitých parametrů](../code-quality/ca1801-review-unused-parameters.md) | Podpis metody obsahuje parametr, který není použit v těle metody. |
| CA1802 |[CA1802: Použijte literály, kde je to vhodné](../code-quality/ca1802-use-literals-where-appropriate.md) |Pole je deklarováno jako statické a jen pro čtení (Shared a ReadOnly v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a je inicializováno pomocí hodnoty, kterou lze vypočítat v době kompilace. Protože hodnotu přiřazenou cílovému poli je nelze vypočítat v době kompilace, změňte deklaraci const (Const v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pole tak, aby hodnota byla vypočítána v době kompilace místo v době běhu. |
| CA1804 | [CA1804: Odeberte nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md) | Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon. |
| CA1806 | [CA1806: Neignorujte výsledky metody](../code-quality/ca1806-do-not-ignore-method-results.md) | Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije. |
| CA1809 |[CA1809: Vyhněte se nadměrným místním hodnotám](../code-quality/ca1809-avoid-excessive-locals.md) | Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“. Pokud chcete zvýšit pravděpodobnost, že jsou všechny lokální proměnné uloženy v registrech procesoru, omezte počet lokálních proměnných na 64. |
| CA1810 | [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
| CA1811 | [CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md) | Soukromý nebo interní člen (na úrovni sestavení) nemá v sestavení žádné volající, není vyvolán modulem CLR (Common Language Runtime) ani není vyvolán delegátem. |
| CA1812 | [CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | Instance typu na úrovni sestavení není vytvořena kódem v sestavení. |
| CA1813 | [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813-avoid-unsealed-attributes.md) | Knihovna tříd rozhraní .NET Framework poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon. |
| CA1814 | [CA1814: Preferujte vícenásobná pole více než multidimenzionální](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | Vícenásobné pole je pole, jehož prvky jsou pole. Pole tvořící prvky mohou být různě velká, což vede k menšímu nevyužitému místu u některých sad dat. |
| CA1815 | [CA1815: Přepište rovná se a operátor rovnosti na hodnotových typech](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals. |
| CA1816 | [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | Metoda, která je implementací metody Dispose, nevolá uvolňování paměti. SuppressFinalize; nebo uvolňování paměti volá metodu, která není implementací metody Dispose. SuppressFinalize; nebo volání metody GC. SuppressFinalize a předává něco jiného (Me v jazyce Visual Basic). |
| CA1819 | [CA1819: Vlastnosti by neměly vracet pole](../code-quality/ca1819-properties-should-not-return-arrays.md) | Pole vrácená vlastnostmi nejsou chráněna proti zápisu, i když je vlastnost jen pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. |
| CA1820 | [CA1820: Testujte prázdné řetězce pomocí délky řetězce](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals. |
| CA1821 | [CA1821: Odstraňte prázdné finalizační metody](../code-quality/ca1821-remove-empty-finalizers.md) | Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda zvyšuje nároky a nemá žádný užitek. |
| CA1822 |[CA1822: Označte členy jako statické](../code-quality/ca1822-mark-members-as-static.md) | Členové, kteří nemají přístup k instanci dat nebo metodám instance volání může být označený jako statické (sdílené v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód. |
| CA1823 | [CA1823: Vyhněte se nepoužitým privátním polím](../code-quality/ca1823-avoid-unused-private-fields.md) | Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná. |
| CA1824 |[CA1824: Označte sestavení pomocí atributu NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Atribut NeutralResourcesLanguage informuje správce prostředků o jazyku použitém pro vykreslení neutrální jazykové verze prostředků pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu. |
| CA1900 | [CA1900: Pole hodnot by měla být přenosná](../code-quality/ca1900-value-type-fields-should-be-portable.md) | Toto pravidlo kontroluje, zda struktury, které jsou deklarovány pomocí explicitního rozložení, budou při zařazení na nespravovaný kód v 64bitových operačních systémech správně zarovnány. |
| CA1901 | [CA1901: Deklarace volání nespravovaného kódu by měly být přenosné](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md) | Toto pravidlo vyhodnotí velikost každého parametru a vrácené hodnoty vyvolání P/Invoke a ověří, zda je velikost parametru správná při zařazení na nespravovaný kód na 32bitových a 64bitových operačních systémech. |
| CA1903 | [CA1903: Použijte pouze API z cílového rozhraní .NET Framework](../code-quality/ca1903-use-only-api-from-targeted-framework.md) | Člen nebo typ používá člen nebo typ, který byl uveden v aktualizaci Service Pack, která nebyla zahrnuta stejně jako cílové rozhraní projektu. |
| CA2000 | [CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000-dispose-objects-before-losing-scope.md) | Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah. |
| CA2001 | [CA2001: Vyhněte se volání problematických metod](../code-quality/ca2001-avoid-calling-problematic-methods.md) | Člen volá potencionálně nebezpečnou nebo problematickou metodu. |
| CA2002 |[CA2002: Nepoužívejte zámky na objekty se slabou identitou](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md) |Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt. |
| CA2003 |[CA2003: Rozlišujte vlákénka od vláken](../code-quality/ca2003-do-not-treat-fibers-as-threads.md) | Spravovaným vláknem se zachází jako [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] vlákna. |
| CA2004 | [CA2004: Odeberte volání GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md) | Pokud převádíte na použití SafeHandle, odeberte veškerá volání GC.KeepAlive (object). V tomto případě by třídy neměly volat metodu GC.KeepAlive. To předpokládá, že nemají destruktor, ale spoléhají na SafeHandle, že dokončí popisovač operačního systému za ně. |
| CA2006 | [CA2006: Použijte SafeHandle pro zapouzdření nativních prostředků](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md) | Použití IntPtr ve spravovaném kódu může znamenat možný problém zabezpečení a spolehlivosti. Všechna použití IntPtr musí být přezkoumána za účelem určení, zda je použití SafeHandle (nebo podobné technologie) na tomto místě vyžadováno. |
| CA2100 | [CA2100: Revize dotazů SQL pro chyby zabezpečení](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md) | Metoda nastavuje vlastnost System.Data.IDbCommand.CommandText pomocí řetězce, který je sestaven z řetězcového argumentu k metodě. Toto pravidlo předpokládá, že řetězcový argument obsahuje vstup uživatele. Řetězec příkazu SQL sestavený ze vstupu uživatele je ohrožen útoky prostřednictvím injektáže SQL. |
| CA2101 |[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Člen vyvolání platformy povoluje částečně důvěryhodné volající, má řetězcový parametr a explicitně nezařazuje řetězec. To může způsobit potenciální ohrožení zabezpečení. |
| CA2102 | [CA2102: Zachycujte výjimky bez CLSCompliant v obecné obslužné rutině](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md) | Člen v sestavení, které není označeno pomocí atributu RuntimeCompatibilityAttribute nebo je označeno atributem RuntimeCompatibility(WrapNonExceptionThrows = false), obsahuje zachytávací blok, který zpracovává typ System.Exception a neobsahuje bezprostředně následující obecný zachytávací blok. |
| CA2103 | [CA2103: Revize naléhavého zabezpečení](../code-quality/ca2103-review-imperative-security.md) |Metoda používá imperativní zabezpečení a může vytvářet oprávnění pomocí stavové informace nebo návratové hodnoty, která se může změnit, pokud je žádost aktivní. Používejte deklarativní zabezpečení vždy, když je to možné. |
| CA2104 |[CA2104: Nedeklaruje proměnlivé odkazové typy pouze pro čtení](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md) | Externě viditelný typ obsahuje externě viditelné pole měnitelného referenčního typu, které je určeno jen pro čtení. Měnitelný typ je typ, jehož instanční data lze upravit. |
| CA2105 | [CA2105: Pole polí by neměly být pouze pro čtení](../code-quality/ca2105-array-fields-should-not-be-read-only.md) |Pokud použijete jen pro čtení (ReadOnly v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modifikátor pro pole, které obsahuje pole, pole nelze změnit tak, aby odkazovaly na jiné pole. Avšak prvky pole, které jsou uloženy v poli určeném jen pro čtení, mohou být změněny. |
| CA2106 | [CA2106: Zabezpečte nepodmíněné výrazy](../code-quality/ca2106-secure-asserts.md) | Metoda uplatňuje oprávnění a na volajícím nejsou vykonány žádné kontroly zabezpečení. Uplatnění oprávnění zabezpečení bez provedení jakékoliv kontroly zabezpečení může zanechat ve vašem kódu zneužitelné slabé stránky zabezpečení. |
| CA2107 | [CA2107: Revize použití operací odepřít a povolit pouze](../code-quality/ca2107-review-deny-and-permit-only-usage.md) |Metoda PermitOnly a akce zabezpečení CodeAccessPermission.Deny by měly být používány pouze těmi, kdo mají pokročilé znalosti o zabezpečení rozhraní .NET Framework. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení. |
| CA2108 | [CA2108: Revize deklarativních zabezpečení na hodnotách](../code-quality/ca2108-review-declarative-security-on-value-types.md) | Veřejný nebo chráněný hodnotový typ je zabezpečen pomocí přístupu k datům nebo požadavků propojení. |
| CA2109 | [CA2109: Revize viditelných obslužných rutin událostí](../code-quality/ca2109-review-visible-event-handlers.md) | Byla zjištěna veřejná nebo chráněná metoda zpracování událostí. Metody zpracování událostí by neměly být vystaveny, pokud to není nezbytně nutné. |
| CA2111 |[CA2111: Ukazatele by neměly být viditelné](../code-quality/ca2111-pointers-should-not-be-visible.md) | Ukazatel není soukromý, interní nebo jen pro čtení. Škodlivý kód může změnit hodnotu ukazatele, což potenciálně umožňuje přístup do libovolného umístění v paměti nebo může způsobit selhání aplikace nebo systému. |
| CA2112 | [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md) | Veřejný nebo chráněný typ obsahuje veřejná pole a je zabezpečen pomocí požadavků propojení. Pokud má kód přístup k instanci typu, která je zabezpečena pomocí požadavku propojení, nemusí kód vyhovět požadavku propojení pro přístup k polím tohoto typu. |
| CA2114 | [CA2114: Zabezpečení metody by mělo být nadmnožinou typu](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md) | Metoda by neměla mít pro stejnou akci deklarativní zabezpečení jak na úrovni metody, tak na úrovni typu. |
| CA2115 | [CA2115: Volejte GC.KeepAlive při použití nativních zdrojů](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md) | Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem. |
| CA2116 | [CA2116: Metody APTCA by měly volat pouze metody APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md) |Když je pro plně důvěryhodná sestavení uveden atribut APTCA (AllowPartiallyTrustedCallersAttribute) a sestavení spustí kód v jiném sestavení, které neumožňuje volání částečně důvěryhodným volajícím, může se jednat o chybu v zabezpečení. |
| CA2117 | [CA2117: Typy APTCA by měly rozšířit pouze základní typy APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md) | Když je pro plně důvěryhodná sestavení uveden atribut APTCA a v sestavení je odvozen z typu, který neumožňuje volání částečně důvěryhodným volajícím, může se jednat o chybu v zabezpečení. |
| CA2118 | [CA2118: Revize použití SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) |Atribut SuppressUnmanagedCodeSecurityAttribute mění výchozí chování zabezpečení systému pro členy vykonávající nespravovaný kód, který používá zprostředkovatele komunikace s objekty COM nebo vyvolání operačního systému. Tento atribut slouží především ke zvýšení výkonu, ačkoliv nárůst výkonu může být spojen s významnými riziky zabezpečení. |
| CA2119 | [CA2119: Zapečeťte metody, které vyhovují privátním rozhraním](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md) | Odvoditelný veřejný typ poskytuje implementaci přepisovatelné metody vnitřního (Friend v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) rozhraní. Chcete-li opravit porušení tohoto pravidla, zabraňte přepsání metody mimo sestavení. |
| CA2120 | [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120-secure-serialization-constructors.md) | Tento typ má konstruktor, který přebírá objekt System.Runtime.Serialization.SerializationInfo a objekt System.Runtime.Serialization.StreamingContext (podpis serializace konstruktoru). Tento konstruktor není zabezpečen pomocí kontroly zabezpečení, ale jeden nebo více běžných konstruktorů tohoto typu je zabezpečených. |
| CA2121 | [CA2121: Statické konstruktory by měly být privátní](../code-quality/ca2121-static-constructors-should-be-private.md) | Systém volá statický konstruktor před vytvořením první instance typu nebo předtím, než jsou odkazovány jakékoli statické členy. Pokud statický konstruktor není soukromý, může být volán jiným kódem než kódem systému. V závislosti na operacích, které jsou provedeny v konstruktoru, to může způsobit neočekávané chování. |
| CA2122 | [CA2122: Nezveřejňujte nepřímo metody s požadavky propojení](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md) | Veřejný nebo chráněný člen má požadavky propojení a je volán členem, který neprovádí žádné bezpečnostní kontroly. Požadavek propojení kontroluje pouze oprávnění bezprostředního volajícího. |
| CA2123 | [CA2123: Požadavky na přepsání odkazu musejí být identické s bází](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md) | Toto pravidlo přiřazuje metodu své základní metodě, kterou je buď rozhraní, nebo virtuální metoda jiného typu, a poté v obou metodách srovnává požadavky propojení. Je-li toto pravidlo porušeno, může chybný volající obejít požadavek propojení pouhým voláním nezabezpečené metody. |
| CA2124 | [CA2124: Zabalte ohroženou klauzuli finally do vnějšího bloku try](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md) | Veřejná nebo chráněná metoda obsahuje blok try/finally. Blok finally nejspíše obnovuje stav zabezpečení a sám není uzavřen v bloku finally. |
| CA2126 | [CA2126: Požadavky propojení typů vyžadují dědičnost požadavků](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md) | Veřejný nezapečetěný typ je chráněn pomocí požadavku propojení a má přepisovatelnou metodu. Tento typ ani tato metoda nejsou chráněny pomocí vyžádané dědičnosti. |
| CA2127 | [CA2136: Členy nesmějí mít konfliktní poznámky transparentnosti](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | Ve 100 % transparentním sestavení nemůže nastat kritický kód. Toto pravidlo analyzuje 100 % transparentní sestavení pro jakékoliv anotace SecurityCritical na úrovni typu, pole a metody. |
| CA2128 |[CA2147: Transparentní metody nemusejí podporovat použití nepodmíněných výrazů zabezpečení](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | Toto pravidlo analyzuje všechny metody a typy v sestavení, který je buď 100 % transparentní, nebo smíšené transparentní/kritické a označí všechny deklarativní nebo imperativní použití výrazu Assert. |
| CA2129 | [CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | Metody označené pomocí atributu SecurityTransparentAttribute volají neveřejné členy, které jsou označeny jako SecurityCritical. Toto pravidlo analyzuje všechny metody a typy v sestavení, které je transparentní/kritické, a označí všechna volání z transparentního kódu do neveřejného kritického kódu, která nejsou označena jako SecurityTreatAsSafe. |
| CA2130 | [CA2130: Konstanty kritické pro zabezpečení musejí být transparentní](../code-quality/ca2130-security-critical-constants-should-be-transparent.md) | Pro konstantní hodnoty není vynucována transparentnost, protože kompilátory vkládají konstantní hodnoty do kódu, aby za běhu programu nebylo zapotřebí žádné vyhledávání. Konstantní pole by měla být transparentní z pohledu zabezpečení, aby kontroloři kódu nepředpokládali, že transparentní kód nemůže ke konstantě přistoupit. |
| CA2131 | [CA2131: Typy kritické pro zabezpečení nemusejí podporovat účast na ekvivalenci typů](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md) | Typ se účastní porovnávání typu, přičemž typ samotný nebo jeho člen nebo pole jsou označeny atributem SecurityCriticalAttribute. Toto pravidlo nastává pro všechny kritické typy nebo typy obsahující kritické metody nebo pole, která se účastní porovnávání typu. Když modul CLR zjistí takový typ, nenačítá jej a za běhu vyvolá výjimku TypeLoadException. Obvykle je toto pravidlo vyvoláno pouze v případě, že uživatelé implementují rovnocennost typu ručně namísto prostřednictvím tlbimp a provedení rovnocennosti typu kompilátorem. |
| CA2132 | [CA2132: Výchozí konstruktory nesmějí být méně kritické než výchozí konstruktory základního typu](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md) |Typy a členy, které mají atribut SecurityCriticalAttribute, nelze použít kódem aplikace Silverlight. Typy a členy kritické z hlediska zabezpečení lze použít pouze prostřednictvím důvěryhodného kódu v knihovně tříd rozhraní .NET Framework aplikace Silverlight. Protože veřejné nebo chráněné konstrukce v odvozené třídě musí mít stejnou nebo větší transparentnost než jejich základní třída, nelze třídu v aplikaci odvodit z třídy označené jako SecurityCritical. |
| CA2133 | [CA2133: Delegáti musejí být připojeni k metodám s konzistentní transparentností](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md) | Toto upozornění je vyvoláno na metodě, která vytvoří vazbu delegáta označeného pomocí atributu SecurityCriticalAttribute na metodu, která je transparentní nebo která je označena pomocí atributu SecuritySafeCriticalAttribute. Upozornění je také vyvoláno na metodě, která vytvoří vazbu transparentního delegáta nebo bezpečně kritického delegáta na kritickou metodu. |
| CA2134 | [CA2134: Metody musejí při přepisování základních metod zachovávat konzistentní transparentnost](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md) |Toto pravidlo je vyvoláno, když metoda označená pomocí atributu SecurityCriticalAttribute přepíše metodu, která je transparentní nebo označená pomocí atributu SecuritySafeCriticalAttribute. Toto pravidlo je vyvoláno také, když transparentní metoda nebo metoda označená pomocí atributu SecuritySafeCriticalAttribute přepíše metodu, která je označená pomocí atributu SecurityCriticalAttribute. Pravidlo je použito při přepisování virtuální metody nebo implementaci rozhraní. |
| CA2135 | [CA2135: Sestavení úrovně 2 nesmějí obsahovat LinkDemands](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md) | Pravidla LinkDemand jsou v sadě pravidel zabezpečení úrovně 2 již zastaralá. Namísto použití pravidel LinkDemand k vynucení zabezpečení v době kompilace JIT označte metody, typy a pole pomocí atributu SecurityCriticalAttribute. |
| CA2136 | [CA2136: Členy nesmějí mít konfliktní poznámky transparentnosti](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | Atributy transparentnosti jsou použity z prvků kódu většího rozsahu na prvky menšího rozsahu. Atributy transparentnosti prvků kódu, které mají větší rozsah, mají přednost před atributy transparentnosti prvků kódu, které jsou obsaženy v prvním prvku. Například třída označená atributem SecurityCriticalAttribute nemůže obsahovat metodu, která je označena atributem SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Transparentní metody musejí obsahovat pouze ověřitelné IL](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md) | Metoda obsahuje kód, který nelze ověřit, nebo vrací typ odkazem. Toto pravidlo je vyvoláno při pokusech transparentního kódu zabezpečení spustit jazyk MSIL, který nelze ověřit. Pravidlo však neobsahuje úplný ověřovatel jazyka IL a místo toho k zachycení většiny porušení ověření jazyka MSIL používá heuristiky. |
| CA2138 | [CA2138: Transparentní metody nesmějí volat metody s atributem SuppressUnmanagedCodeSecurity](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md) | Transparentní metoda zabezpečení volá metodu, která je označena atributem SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Transparentní metody nemusejí podporovat použití atributu HandleProcessCorruptingExceptions](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md) | Toto pravidlo je vyvoláno, je-li jakákoliv metoda transparentní a pokusí se zpracovat výjimku poškozující proces použitím atributu HandleProcessCorruptedStateExceptionsAttribute. Výjimka poškozující proces je klasifikace výjimek dle specifikace CLR verze 4.0, jako například výjimka AccessViolationException. Atribut HandleProcessCorruptedStateExceptionsAttribute lze použít pouze metodami kritickými pro bezpečnost a bude ignorován, je-li použit u transparentních metod. |
| CA2140 | [CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | Prvek kódu označený atributem SecurityCriticalAttribute je kritický pro zabezpečení. Transparentní metoda nemůže použít prvek kritický pro zabezpečení. Pokud se transparentní typ pokusí použít typ kritický pro zabezpečení, je vyvolána výjimka TypeAccessException, MethodAccessException nebo FieldAccessException. |
| CA2141 |[CA2141:Transparentní metody nesmějí vyhovovat LinkDemands](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Transparentní metoda (z hlediska zabezpečení) volá metodu v sestavení, které není označeno atributem APTCA, nebo transparentní metoda (z hlediska zabezpečení) splňuje pravidlo LinkDemand pro typ nebo metodu. |
| CA2142 | [CA2142: Transparentní kód nemůže být chráněn pomocí LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md) | Toto pravidlo je vyvoláno transparentními metodami, které k přístupu vyžadují pravidla LinkDemand. Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. |
| CA2143 | [CA2143: Transparentní metody nemohou používat požadavky zabezpečení](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md) | Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. Kód transparentní z hlediska zabezpečení by měl k učinění rozhodnutí o zabezpečení používat úplné požadavky a bezpečně kritický kód by neměl spoléhat na to, že transparentní kód tyto úplné požadavky provede. |
| CA2144 | [CA2144: Transparentní kód nesmí načítat sestavení z bajtových polí](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md) | Přezkoumání zabezpečení transparentního kódu není tak úplné jako přezkoumání zabezpečení kritického kódu, protože transparentní kód nemůže provádět akce citlivé na zabezpečení. Sestavení, která jsou načtena z pole bajtů, nemohou být v transparentním kódu zaznamenána a takové pole bajtů může obsahovat kritický nebo důležitější bezpečně kritický kód, který musí být auditován. |
| CA2145 | [CA2145: Transparentní metody nesmějí být doplněny pomocí SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md) | Metody označené atributem SuppressUnmanagedCodeSecurityAttribute mají implicitní LinkDemand umístěn na jakoukoli metodu, která jej volá. Tento LinkDemand vyžaduje, aby byl volající kód kritický z hlediska zabezpečení. Označení metody, která používá SuppressUnmanagedCodeSecurity, atributem SecurityCriticalAttribute zviditelňuje tento požadavek pro volající metody. |
| CA2146 | [CA2146: Typy nesmějí být kritické méně než jejich základní typy a rozhraní](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md) | Toto pravidlo je vyvoláno, když má odvozený typ atribut transparentnosti zabezpečení, který není tak kritický jako jeho základní typ nebo implementované rozhraní. Pouze kritické typy lze odvodit z kritických základních typů nebo mohou implementovat kritická rozhraní a pouze kritické typy nebo bezpečně kritické typy mohou být odvozeny ze základních bezpečně kritických typů nebo mohou implementovat bezpečně kritická rozhraní. |
| CA2147 |[CA2147: Transparentní metody nemusejí podporovat použití nepodmíněných výrazů zabezpečení](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | U kódu označeného atributem SecurityTransparentAttribute není uděleno dostatečné oprávnění k vyhodnocení. |
| CA2149 | [CA2149: Transparentní metody nesmějí provádět volání do nativního kódu](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md) | Toto pravidlo je vyvoláno na každé transparentní metodě, která přímo volá nativní kód (například prostřednictvím P/Invoke). Porušení tohoto pravidla vede k vyvolání výjimky MethodAccessException v modelu transparentnosti úrovně 2 a k úplnému požadavku na nespravovaný kód v modelu transparentnosti úrovně 1. |
| CA2151 |[CA2151: Pole s kritickými typy by měla být kritická pro zabezpečení](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md) | Chcete-li používat typy kritické z hlediska zabezpečení, musí být kód, který odkazuje na typ, buď kritický z hlediska zabezpečení, nebo bezpečně kritický z hlediska zabezpečení. To platí i v případě, že je odkaz nepřímý. Proto je existence transparentního pole kritického z hlediska zabezpečení nebo transparentního pole bezpečně kritického z hlediska zabezpečení zavádějící, jelikož transparentní kód nebude mít k poli přístup. |
| CA2200 | [CA2200: Znovu vyvolejte pro zachování podrobností zásobníku](../code-quality/ca2200-rethrow-to-preserve-stack-details.md) | Výjimka je znovu vyvolána a je jednoznačně uvedena v příkazu throw. Jestliže je výjimka znovu vyvolána zadáním výjimky v příkazu throw, seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztracen. |
| CA2201 | [CA2201: Nevyvolávejte vyhrazené typy výjimek](../code-quality/ca2201-do-not-raise-reserved-exception-types.md) | Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2202 | [CA2202: Neuvolňujte objekty několikrát](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md) |Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání metody System.IDisposable.Dispose nebo ekvivalentní metody pro uvolnění (například metoda Close() u některých typů) stejného objektu. |
| CA2204 | [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md) | Řetězcový literál v těle metody obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA2205 | [CA2205: Použijte spravované ekvivalenty rozhraní Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md) | Vyvolání operačního systému je definována metoda a metodu, která obsahuje ekvivalentní funkce, které se nachází v knihovně tříd rozhraní .NET Framework. |
| CA2207 | [CA2207: Inicializujte vloženou hodnotu statických polí](../code-quality/ca2207-initialize-value-type-static-fields-inline.md) | Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte. |
| CA2208 |[CA2208: Vytvořte správně instance výjimky argumentu](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md) | Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena. |
| CA2210 |[CA2210: Sestavení by měly mít platné silné názvy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md) | Silný název chrání klienty před neúmyslným načtením narušeného sestavení. Sestavení bez silných názvů by kromě velmi omezených scénářů neměla být nasazována. Pokud sdílíte nebo šíříte sestavení, která nejsou správně podepsána, může být sestavení záměrně poškozeno, modul CLR je nemusí načíst nebo uživatelé mohou být nuceni vypnout na svém počítači ověřování. |
| CA2211 |[CA2211: Nekonstantní pole by nemělo být viditelné](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md) | Statická pole, která nejsou konstantami ani nejsou jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy. |
| CA2212 | [CA2212: Neoznačujte obsluhované součásti pomocí WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md) |Metoda typu, který je odvozen z typu System.EnterpriseServices.ServicedComponent, je označena pomocí atributu System.Web.Services.WebMethodAttribute. Protože atribut WebMethodAttribute a metoda ServicedComponent mají konfliktní chování a požadavky na kontext a tok transakcí, bude chování metody v některých případech nesprávné. |
| CA2213 | [CA2213: Uvolnitelné pole by mělo být uvolněno](../code-quality/ca2213-disposable-fields-should-be-disposed.md) | Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu. |
| CA2214 | [CA2214: Nevolejte přepisovatelné metody v konstruktorech](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md) | Při volání virtuální metody konstruktorem nemusí být konstruktor instance, která volá tuto metodu, proveden. |
| CA2215 | [CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md) | Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose. |
| CA2216 |[CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md) | Typ, který implementuje rozhraní System.IDisposable a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno metodou Object.Finalize. |
| CA2217 | [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md) |Externě viditelný výčet je označen atributem FlagsAttribute a má jednu nebo více hodnot, které nejsou mocninami dvou nebo kombinací jiných definovaných hodnot výčtu. |
| CA2218 |[CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md) | Metoda GetHashCode vrací hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako například tabulku hash. Dva objekty, které jsou stejného typu a jsou stejné, musí vrátit stejnou hodnotu hash. |
| CA2219 | [CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md) | Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2220 | [CA2220: Finalizační metody by měly volat finalizační metodu třídy Base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md) | Finalizační metoda musí být šířena přes hierarchii dědičnosti. Chcete-li to zaručit, musí typy zavolat metodu Finalize své základní třídy ve své vlastní metodě Finalize. |
| CA2221 |[CA2221: Finalizační metody by měly být chráněné](../code-quality/ca2221-finalizers-should-be-protected.md) | Finalizační metody musí použít modifikátor přístupu family. |
| CA2222 | [CA2222: Nesnižujte viditelnost zděděného členu](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md) |Modifikátor přístupu byste neměli měnit u zděděných členů. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody. |
| CA2223 | [CA2223: Členy by se měly lišit o více než návratový typ](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md) | Přestože modul CLR (Common Language Runtime) umožňuje používat návratové typy k rozlišení mezi jinak identickými členy, tato funkce není ve specifikaci CLS, ani není běžnou funkcí v programovacích jazycích rozhraní .NET. |
| CA2224 | [CA2224: Přepište Equals při přetížení operátoru rovnosti](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md) | Veřejný typ implementuje operátor rovnosti, ale nepřepisuje metodu Object.Equals. |
| CA2225 | [CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225-operator-overloads-have-named-alternates.md) |Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích nepodporujících přetížené operátory. |
| CA2226 | [CA2226: Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md) | Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor. |
| CA2227 |[CA2227: Vlastnosti kolekce by měly být pouze pro čtení](../code-quality/ca2227-collection-properties-should-be-read-only.md) |Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy. |
| CA2228 | [CA2228: Nedodávejte nevydané formáty prostředku](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md) | Soubory prostředků, které byly vytvořeny pomocí předprodejní verze rozhraní .NET Framework nemusí být použitelné podporovanými verzemi rozhraní .NET Framework. |
| CA2229 | [CA2229: Implementovat serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md) | Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. |
| CA2230 | [CA2230: Použijte parametry pro proměnné argumenty](../code-quality/ca2230-use-params-for-variable-arguments.md) | Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání VarArgs místo klíčového slova params. |
| CA2231 | [CA2231: Přetižte operátor equals při přepsání ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Hodnotový typ přepisuje metodu Object.Equals, ale neimplementuje operátor rovnosti. |
| CA2232 | [CA2232: Označte vstupní bod modelu Windows Forms pomocí STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md) | Atribut STAThreadAttribute znamená, že model vláken aplikace COM je jednovláknový apartment (STA). Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně. |
| CA2233 |[CA2233: Operace by neměly přetéct](../code-quality/ca2233-operations-should-not-overflow.md) | Aritmetické operace byste neměli provádět bez ověření operandů. Tím zajistíte, že výsledek operace není mimo rozsah možných hodnot použitých datových typů. |
| CA2234 | [CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md) | Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“. Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri. |
| CA2235 | [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md) | Neserializovatelný typ pole instance je deklarován v serializovatelném typu. |
| CA2236 | [CA2236: Volejte metody třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) | Chcete-li napravit porušení tohoto pravidla, zavolejte metodu GetObjectData základního typu nebo konstruktor serializace z odpovídající metody nebo konstruktoru odvozeného typu. |
| CA2237 | [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) | Aby byl typ rozpoznán modulem CLR (Common Language Runtime) jako serializovatelný, musí být označen pomocí atributu SerializableAttribute, i když typ používá vlastní rutinu serializace prostřednictvím implementace rozhraní ISerializable. |
| CA2238 |[CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md) | Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost. |
| CA2239 | [CA2239: Poskytujte metody deserializace pro nepovinné pole](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) | Typ má pole označené atributem System.Runtime.Serialization.OptionalFieldAttribute a neposkytuje metody zpracování událostí deserializace. |
| CA2240 | [CA2240: Implementujte správně ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md) | Chcete-li opravit porušení tohoto pravidla, nastavte metodu GetObjectData jako viditelnou a přepisovatelnou a ujistěte se, že všechna pole instancí jsou součástí procesu serializace nebo výslovně označena pomocí atributu NonSerializedAttribute. |
| CA2241 | [CA2241: Poskytněte správné argumenty metodě formátování](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md) | Formátovací argument, který je předán metodě System.String.Format, neobsahuje formátovací položku, která odpovídá každému argumentu objektu nebo naopak. |
| CA2242 |[CA2242: Testujte správně NaN](../code-quality/ca2242-test-for-nan-correctly.md) | Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double). |
| CA2243 |[CA2243: Literály řetězce atributu by se měly správně analyzovat](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md) | Parametr řetězcového literálu atributu nesprávně analyzuje adresu URL, identifikátor GUID nebo verzi. |
| CA5122 | [CA5122: Deklarace volání nespravovaného kódu nesmí být kritické pro zabezpečení](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Metody jsou při provádění operace citlivé na zabezpečení označeny jako SecuritySafeCritical, ale lze je také bezpečně použít transparentním kódem. Transparentní kód nesmí nikdy přímo volat nativní kód prostřednictvím P/Invoke. Proto označení P/Invoke jako bezpečně kritické z hlediska zabezpečení neumožní transparentnímu kódu vyvolat je a je zavádějící pro analýzu zabezpečení. |