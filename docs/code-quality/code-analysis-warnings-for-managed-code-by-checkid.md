---
title: Upozornění Analýzy kódu pro spravovaný kód podle CheckId
ms.date: 04/18/2019
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
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
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
- CA1507
- CA1508
- CA1509
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
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1835
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
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
- CA2245
- CA2246
- CA2247
- CA5122
- CA5374
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d9c4834604d4f77d53dc0ff7bb725eae3312779
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382676"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Upozornění analýzy kódu pro spravovaný kód podle CheckId

Následující tabulka obsahuje seznam upozornění analýzy kódu pro spravovaný kód podle identifikátoru upozornění CheckId.

| CheckId | Upozornění | Popis |
|---------| - | - |
| CA1000 | [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000.md) | Při volání statického členu obecného typu musí být pro tento typ zadán argument typu. Je-li zavolán obecný člen instance, který nepodporuje odvozování, musí být pro tento člen zadán argument typu. V těchto dvou případech je syntaxe zadávání argumentu typu různá a snadno zaměnitelná. |
| CA1001 | [CA1001: Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné](../code-quality/ca1001.md) | Třída deklaruje a implementuje pole instance typu System.IDisposable, přičemž neimplementuje rozhraní IDisposable. Třída, která deklaruje pole IDisposable nepřímo, vlastní nespravovaný zdroj a měla by rozhraní IDisposable implementovat. |
| CA1002 | [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002.md) | System. Collections. Generic. list< (of \<(T> ) >) je obecná kolekce, která je navržena pro výkon, nikoli dědičnost. Proto třída List neobsahuje žádné virtuální členy. Místo ní by měly být vystaveny kolekce navržené pro dědičnost. |
| CA1003 | [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003.md) |Typ obsahuje delegát, který vrací typ void, jehož signatura obsahuje dva parametry (první objekt a druhý typ, který lze přiřadit k EventArgs), a nadřazené sestavení cílí na Microsoft .NET Framework 2,0. |
| CA1004 | [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004.md) | Argument typu obecné metody je z argumentu typu předávaného metodě odvozen namísto explicitního určení argumentu typu. Má-li být odvozování povoleno, musí předpis parametrů obecné metody zahrnovat parametr stejného typu jako parametr typu metody. V tomto případě nemusí být argument typu zadán. Používáte-li odvození pro všechny parametry typu, je syntaxe volání obecných a neobecných metod instancí identická, což zjednodušuje použití obecných metod. |
| CA1005 | [CA1005: Vyhněte se nadbytečným parametrům u obecných typů](../code-quality/ca1005.md) | Čím více parametrů typu obecný typ obsahuje, tím obtížnější je vědět a zapamatovat si, co každý z parametrů typu představuje. Je obvykle zřejmé s jedním parametrem typu, jako v seznamu \<T> , a v některých případech, které mají dva parametry typu, jako ve slovníku \<TKey, TValue> . Pokud však existují více než dva parametry typu, stává se pro většinu uživatelů použití příliš obtížným. |
| CA1006 | [CA1006: Nevnořujte obecné typy do signatur členu](../code-quality/ca1006.md) | Vnořený typ argumentu je typ argumentu, který je také obecným typem. Chce-li uživatel zavolat člen, jehož předpis obsahuje vnořený argument typu, musí nejprve vytvořit instanci jednoho obecného typu a předat tento typ konstruktoru druhého obecného typu. Potřebná procedura a syntaxe je složitá a je vhodné se jí vyhnout. |
| CA1007 |[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007.md) | Externě viditelná metoda obsahuje referenční parametr typu System.Object. Použitím obecných metod lze metodě předávat všechny typy (s určitými omezeními) bez předchozího přetypování typu na referenční typ parametru. |
| CA1008 | [CA1008: Výčty by měly mít nulovou hodnotu](../code-quality/ca1008.md) | Výchozí hodnota neinicializovaného výčtu je stejně jako u jiných typů hodnot nula. Atributovaný výčet bez příznaků by měl definovat člen za použití hodnoty nula tak, aby výchozí hodnota byla platnou hodnotou výčtu. Definuje-li výčet, který má aplikován atribut FlagsAttribute, člen s hodnotou nula, měl by jeho název být „None“, aby tak označoval, že ve výčtu nebyly nastaveny žádné hodnoty. |
| CA1009 | [CA1009: Deklarujte správně obslužné rutiny událostí](../code-quality/ca1009.md) | Metody zpracování událostí přebírají dva parametry. První je typu System.Object a je pojmenován „sender“. Je jím objekt, který vyvolal událost. Druhý parametr je typu System.EventArgs a je pojmenován „e“. Představuje data přidružená k události. Metody zpracování událostí by neměly vracet hodnotu; v programovacím jazyce C# je toto označeno návratovým typem void. |
| CA1010 | [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010.md) | Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Pak lze tuto kolekci použít k zaplnění typů obecných kolekcí. |
| CA1011 |[CA1011: Zvažte předání základních typů jako parametrů](../code-quality/ca1011.md) | Je-li v deklaraci metody zadán jako parametr základní typ, lze jako příslušný argument k metodě předat kterýkoliv typ odvozený z tohoto základního typu. Pokud není dodatečná funkčnost poskytovaná odvozeným typem parametru vyžadována, umožňuje použití základního typu širší využití metody. |
| CA1012 | [CA1012: Abstraktní typy by neměly mít konstruktory](../code-quality/ca1012.md) | Konstruktory abstraktních typů mohou být volány pouze odvozenými typy. Jelikož veřejné konstruktory vytvářejí instance typu, přičemž nelze vytvořit instance abstraktního typu, je abstraktní typ obsahující veřejný konstruktor nesprávně navržen. |
| CA1013 | [CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání](../code-quality/ca1013.md) | Veřejný nebo chráněný typ implementuje operátory sčítání a odčítání, aniž by implementoval operátor rovnosti. |
| CA1014 | [CA1014: Označte sestavení pomocí CLSCompliantAttribute](../code-quality/ca1014.md) | Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh určuje, že všechna sestavení explicitně označují dodržování předpisů CLS pomocí <xref:System.CLSCompliantAttribute> . Není-li tento atribut v sestavení přítomen, nedodržuje sestavení specifikaci. |
| CA1016 | [CA1016: Označte sestavení pomocí AssemblyVersionAttribute](../code-quality/ca1016.md) | Rozhraní .NET používá číslo verze k jednoznačné identifikaci sestavení a k vytvoření vazby na typy v silně pojmenovaných sestaveních. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny. |
| CA1017 | [CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017.md) |Atribut ComVisibleAttribute určuje způsob přístupu klientů COM ke spravovanému kódu. Dobrý návrh přikazuje, aby sestavení explicitně uvedla viditelnost modelu COM. Viditelnost modelu COM může být nastavena pro celé sestavení a poté přepsána pro jednotlivé typy a členy typů. Není-li tento atribut přítomen, je obsah sestavení viditelný klientům COM. |
| CA1018 | [CA1018: Označte atributy pomocí AttributeUsageAttribute](../code-quality/ca1018.md) | Při definování vlastního atributu jej označte použitím atributu AttributeUsageAttribute, čímž je určeno, kde ve zdrojovém kódu může být vlastní atribut použit. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. |
| CA1019 | [CA1019: Definujte přístupové objekty pro argumenty atributů](../code-quality/ca1019.md) | Atributy mohou definovat povinné argumenty, které musí být specifikovány při použití atributu na cíl. Říká se jim také poziční argumenty, jelikož jsou konstruktorům atributů předány jako poziční parametry. Pro každý povinný argument by měl atribut navíc poskytovat odpovídající vlastnost jen pro čtení, aby mohla být hodnota argumentu během spuštění získána. Atributy mohou také definovat volitelné argumenty, které jsou rovněž známy jako pojmenované argumenty. Tyto argumenty jsou podle názvu poskytovány konstruktorům atributů a měly by mít odpovídající vlastnost pro čtení i zápis. |
| CA1020 | [CA1020: Vyhněte se oborům názvu s malým množstvím typů](../code-quality/ca1020.md) | Ujistěte se, že všechny obory názvů mají logické uspořádání a že je vložení typů do řídce zaplněných oborů názvů odůvodněné. |
| CA1021 | [CA1021: Vyhněte se výstupním parametrům](../code-quality/ca1021.md) | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů, a schopnost práce s metodami vracejícími více návratových typů. Také rozdíl mezi parametry „out“ a „ref“ není běžně chápán. |
| CA1023 | [CA1023: Indexery by neměly být multidimenzionální](../code-quality/ca1023.md) | Indexery (tj. indexované vlastnosti) by měly používat jediný index. Vícerozměrné indexery mohou výrazně snížit použitelnost knihovny. |
| CA1024 | [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024.md) | Veřejná nebo chráněná metoda má název začínající na „Get“, nepřijímá žádné parametry a vrací hodnotu, která není polem. Metoda může být dobrým kandidátem, aby se stala vlastností. |
| CA1025 | [CA1025: Nahraďte opakované argumenty polem parametrů](../code-quality/ca1025.md) | Není-li znám přesný počet argumentů a jsou-li proměnné argumenty stejného typu (nebo je lze předat jako stejný typ), použijte namísto opakovaných argumentů pole parametrů. |
| CA1026 | [CA1026: Neměly by být použity výchozí parametry](../code-quality/ca1026.md) | Ve specifikaci CLS jsou povoleny metody používající výchozí parametry, avšak specifikace CLS umožňuje kompilátorům ignorovat hodnoty přiřazené těmto parametrům. Chcete-li zachovat shodné chování napříč programovacími jazyky, měly by být metody používající výchozí parametry nahrazeny přetíženími metody, která výchozí parametry poskytují. |
| CA1027 |[CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027.md) | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Mohou-li být pojmenované konstanty smysluplně kombinovány, použijte ve výčtu atribut FlagsAttribute. |
| CA1028 | [CA1028: Úložiště výčtu by mělo být Int32](../code-quality/ca1028.md) | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Ve výchozím nastavení je pro uložení konstantní hodnoty použit datový typ System.Int32. Přestože lze tento typ změnit, není to ve většině případů zapotřebí ani doporučováno. |
| CA1030 | [CA1030: Použijte události, kde je to vhodné](../code-quality/ca1030.md) |Toto pravidlo zjišťuje metody, které mají názvy obvykle používané pro události. Je-li metoda volána jako odpověď na jednoznačně definovanou změnu stavu, měla by být metoda volána obslužnou rutinou události. Objekty volající tuto metodu by měly místo přímého volání metody vyvolat událost. |
| CA1031 | [CA1031: Nezachycujte výjimky obecného typu](../code-quality/ca1031.md) | Obecné výjimky by neměly být zachycovány. Zachyťte více specifickou výjimku nebo jako poslední příkaz v zachytávacím bloku opětovně vyvolejte obecnou výjimku. |
| CA1032 |[CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032.md) | Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. |
| CA1033 | [CA1033: Metody rozhraní by měly být volatelné podřízenými typy](../code-quality/ca1033.md) | Nezapečetěný externě viditelný typ poskytuje explicitní implementaci metod veřejného rozhraní a neposkytuje alternativní externě viditelnou metodu stejného názvu. |
| CA1034 | [CA1034: Vnořené typy by neměly být viditelné](../code-quality/ca1034.md) | Vnořený typ je typ deklarovaný v rámci jiného typu. Vnořené typy jsou užitečné pro zapouzdření soukromých podrobností implementace v daném typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné. |
| CA1035 | [CA1035: Implementace ICollection mají členy silného typu](../code-quality/ca1035.md) | Toto pravidlo vyžaduje, aby implementace rozhraní ICollection poskytovaly členy se silnými typy, aby uživatelé nemuseli při využívání funkčnosti poskytované rozhraním přetypovávat argumenty na typ Object. Toto pravidlo předpokládá, že typ implementuje rozhraní ICollection proto, aby mohl spravovat kolekci instancí typu silnějšího než Object. |
| CA1036 | [CA1036: Přepište metody u srovnatelných typů](../code-quality/ca1036.md) |Veřejný nebo chráněný typ implementuje rozhraní System.IComparable. Nepřepisuje metodu Object.Equals ani nepřetěžuje operátory rovnosti, nerovnosti, menší než a větší než specifické pro daný jazyk. |
| CA1038 | [CA1038: Enumerátory by měly být silného typu](../code-quality/ca1038.md) | Toto pravidlo vyžaduje, aby implementace rozhraní IEnumerator také poskytovaly verze vlastnosti Current se silnými typy, aby uživatelé nemuseli při použití funkčnosti poskytované tímto rozhraním přetypovávat návratovou hodnotu na silný typ. |
| CA1039 | [CA1039: Seznamy jsou silného typu](../code-quality/ca1039.md) | Toto pravidlo vyžaduje, aby implementace rozhraní IList poskytovaly členy se silnými typy, aby uživatelé nemuseli při využívání funkčnosti poskytované rozhraním přetypovávat argumenty na typ System.Object. |
| CA1040 |[CA1040: Vyhněte se prázdným rozhraním](../code-quality/ca1040.md) | Rozhraní definují členy ujednávající jejich chování nebo užití. Funkčnost popsaná rozhraním může být osvojena libovolným typem bez ohledu na to, kde se typ vyskytuje v hierarchii dědičnosti. Typ implementuje rozhraní tím, že poskytuje implementace jeho členů. Prázdné rozhraní nedefinuje žádné členy, tudíž ani nedefinuje žádná implementovatelná ujednání. |
| CA1041 | [CA1041: Poskytněte zprávu ObsoleteAttribute](../code-quality/ca1041.md) | Typ nebo člen je označen atributem System.ObsoleteAttribute, aniž by měl zadánu vlastnost ObsoleteAttribute.Message. Při kompilaci typu nebo členu označeného atributem ObsoleteAttribute je zobrazena vlastnost zprávy tohoto atributu. To uživateli poskytuje informace o zastaralém typu nebo členu. |
| CA1043 | [CA1043: Použijte celočíselný nebo řetězcový argument pro indexery](../code-quality/ca1043.md) | Indexery (tj. indexované vlastnosti) by měly jako index používat celočíselné typy nebo typy řetězců. Tyto typy se obvykle používají pro indexování datových struktur a zvyšují použitelnost knihovny. Použití typu Object by mělo být omezeno na ty případy, kdy během návrhu není možné určit konkrétní celočíselný nebo řetězcový typ. |
| CA1044 | [CA1044: Vlastnosti by neměly být pouze pro zápis](../code-quality/ca1044.md) | Ačkoli je přijatelné a často nezbytné použít vlastnost jen pro čtení, směrnice návrhu zakazují použití vlastností jen pro zápis. Důvodem je skutečnost, že umožnit uživateli nastavit hodnotu a poté uživateli zabránit v zobrazení této hodnoty není bezpečné. Taktéž bez přístupu pro čtení není možné zobrazit stav sdílených objektů, což omezuje jejich užitečnost. |
| CA1045 |[CA1045: Nepředávejte typy odkazem](../code-quality/ca1045.md) | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů a schopnost práce s metodami vracejícími více návratových typů. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat, že uživatelé budou hlavní pracovat s `out` `ref` parametry nebo. |
| CA1046 | [CA1046: Nepřetěžujte operátory rovnosti u odkazových typů](../code-quality/ca1046.md) | U referenčních typů je výchozí implementace operátoru rovnosti téměř vždy správná. Ve výchozím nastavení jsou dva odkazy rovny, pouze pokud ukazují na stejný objekt. |
| CA1047 |[CA1047: Nedeklarujte chráněné členy v zapečetěných typech](../code-quality/ca1047.md) | Typy deklarují chráněné členy, aby k nim odvozené typy mohly přistupovat nebo je přepisovat. Dle definice nelze dědit zapečetěné typy, což znamená, že nelze volat chráněné metody zapečetěných typů. |
| CA1048 | [CA1048: Nedeklarujte virtuální členy v zapečetěných typech](../code-quality/ca1048.md) | Typy deklarují metody jako virtuální, aby odvozující typy mohly přepsat implementaci virtuální metody. Dle definice nelze zdědit zapečetěný typ. Díky tomu postrádá virtuální metoda u zapečetěného typu význam. |
| CA1049 | [CA1049: Typy, které vlastní nativní prostředky, by měly být uvolnitelné](../code-quality/ca1049.md) | Typy, které přidělují nespravované prostředky, by měly implementovat rozhraní IDisposable a umožnit tak volajícím uvolnit tyto prostředky na požádání a zkrátit životní cyklus objektů, které je využívají. |
| CA1050 | [CA1050: Deklarujte typy v oborech názvů](../code-quality/ca1050.md) | Typy jsou deklarovány v oborech názvů, aby bylo zabráněno kolizím názvů a zároveň jako způsob organizace souvisejících typů v hierarchii objektů. |
| CA1051 | [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051.md) | Hlavní použití pole by mělo být jako podrobnost implementace. Pole by měla být soukromá nebo vnitřní a měla by být vystavena s použitím vlastností. |
| CA1052 | [CA1052: Statické typy vlastníků by měly být zapečetěné](../code-quality/ca1052.md) | Veřejný nebo chráněný typ obsahuje pouze statické členy a není deklarován s použitím zapečetěného modifikátoru (NotInheritable) (jazyk C#). Typu, u nějž není zamýšleno dědění, by mělo být prostřednictvím označením zapečetěným modifikátorem zabráněno, aby byl použit jako základní typ. |
| CA1053 |[CA1053: Statické typy vlastníků by neměly mít konstruktory](../code-quality/ca1053.md) | Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má veřejný nebo chráněný výchozí konstruktor. Konstruktor není nutný, protože volání statických členů nevyžaduje instanci typu. Z důvodu bezpečnosti a zabezpečení by řetězcová přetížení měla volat přetížení identifikátoru URI použitím argumentu řetězce. |
| CA1054 | [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054.md) | Pakliže metoda přijímá řetězcovou reprezentaci identifikátoru URI, mělo by být poskytnuto odpovídající přetížení přijímající instanci třídy URI, která tyto služby poskytuje bezpečným a zabezpečeným způsobem. |
| CA1055 | [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055.md) | Toto pravidlo předpokládá, že metoda vrací identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1056 | [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056.md) | Toto pravidlo předpokládá, že vlastnost reprezentuje identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1057 | [CA1057: Přetížení řetězce identifikátoru URI volají přetížení System.Uri](../code-quality/ca1057.md) | Typ deklaruje přetížení metod, které se liší pouze nahrazením řetězcového parametru parametrem System.Uri. Přetížení přijímající řetězcový parametr nevolá přetížení, které přijímá parametr URI. |
| CA1058 | [CA1058: Typy by neměly rozšiřovat určité základní typy](../code-quality/ca1058.md) | Externě viditelný typ rozšiřuje určité základní typy. Použijte jednu z alternativ. |
| CA1059 |[CA1059: Členy by neměly zveřejňovat určité konkrétní typy](../code-quality/ca1059.md) | Konkrétní typ je typ, který je zcela implementován, a lze tudíž vytvořit jeho instanci. Chcete-li umožnit široké využití členu, nahraďte konkrétní typ použitím navrhovaného rozhraní. |
| CA1060 | [CA1060: přesunout volání nespravovaného volání do třídy NativeMethods](../code-quality/ca1060.md) | Metody vyvolání platformy, například ty, které jsou označeny pomocí atributu System.Runtime.InteropServices.DllImportAttribute, nebo metody, které jsou definovány pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , přistupuje k nespravovanému kódu. Tyto metody by měly patřit třídě NativeMethods, SafeNativeMethods nebo UnsafeNativeMethods. |
| CA1061 |[CA1061: Neskrývejte metody základní třídy](../code-quality/ca1061.md) | Metoda základního typu je skryta identicky pojmenovanou metodou v odvozeném typu, kde je předpis parametrů odvozené metody odlišný od odpovídajících typů v předpisu parametrů základní metody pouze ve slaběji odvozených typech. |
| CA1062 | [CA1062: Ověřte argumenty veřejných metod](../code-quality/ca1062.md) | Všechny argumenty odkazu předané externě viditelným metodám by měly být porovnány s hodnotou NULL. |
| CA1063 | [CA1063: Implementuje správně IDisposable](../code-quality/ca1063.md) | Všechny typy IDisposable by měly správně implementovat vzor Dispose. |
| CA1064 | [CA1064: Výjimky by měly být veřejné](../code-quality/ca1064.md) | Interní výjimka je viditelná pouze uvnitř svého vlastního vnitřního rozsahu. Jakmile výjimka přesáhne hranice vnitřního rozsahu, lze pro zachycení výjimky použít pouze základní výjimku. Pokud je interní výjimka zděděna z <xref:System.Exception> , <xref:System.SystemException> , nebo <xref:System.ApplicationException> , externí kód nebude mít dostatečné informace k tomu, abyste věděli, co dělat s výjimkou. |
| CA1065 | [CA1065: Nevyvolávejte výjimky v neočekávaných umístěních](../code-quality/ca1065.md) | Metoda, u které není předpokládáno vyvolání výjimky, vyvolá výjimku. |
| CA1066 | [CA1066: Při přepisu Equals implementujte IEquatable.](../code-quality/ca1066.md) | Hodnotový typ přepisuje <xref:System.Object.Equals%2A> metodu, ale neimplementuje <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: Při implementaci IEquatable přepište Equals.](../code-quality/ca1067.md) | Typ implementuje <xref:System.IEquatable%601> , ale nepřepisuje <xref:System.Object.Equals%2A> metodu. |
| CA1068 | [CA1068: Parametry CancellationToken musí být poslední.](../code-quality/ca1068.md) | Metoda má parametr CancellationToken, který není posledním parametrem. |
| CA1069 | [CA1069: Výčty by neměly mít duplicitní hodnoty.](../code-quality/ca1069.md) | Výčet má více členů, kteří mají explicitně přiřazenou stejnou konstantní hodnotu. |
| CA1070 | [CA1070: Nedeklarujte pole událostí jako virtuální.](../code-quality/ca1070.md) | [Událost podobná poli](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) byla deklarována jako Virtual. |
| CA1200 | [CA1200: Nepoužívejte značky cref s předponou](../code-quality/ca1200.md) | Atribut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Vyhněte se použití `cref` značek s předponami, protože brání kompilátoru v ověřování odkazů. Zároveň zabrání integrovanému vývojovému prostředí (IDE) sady Visual Studio najít a aktualizovat tyto odkazy na symboly během refaktoringu. |
| CA1300 | [CA1300: Určete MessageBoxOptions](../code-quality/ca1300.md) | Chcete-li správně zobrazit okno pro kultury, které používají směr čtení zprava doleva, musí být členy RightAlign a RtlReading výčtu MessageBoxOptions předány metodě Show. |
| CA1301 | [CA1301: Vyhněte se duplicitním akcelerátorům](../code-quality/ca1301.md) | Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Pokud má více ovládacích prvků duplicitní přístupové klíče, není chování přístupového klíče správně definované. |
| CA1302 | [CA1302: Nekódujte pevně řetězce závislé na národním prostředí](../code-quality/ca1302.md) | Výčet System.Environment.SpecialFolder obsahuje členy, které odkazují na speciální systémové složky. Umístění těchto složek mohou mít různé hodnoty v různých operačních systémech; uživatel může změnit některé z míst; a místa jsou lokalizována. Metoda Environment.GetFolderPath vrátí lokace, které jsou spojené s výčtem Environment.SpecialFolder, lokalizované a vhodné pro aktuálně spuštěný počítač. |
| CA1303 | [CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303.md) | Externě viditelná metoda předává řetězcový literál jako parametr konstruktoru nebo metodě .NET a tento řetězec by měl být Lokalizovatelný. |
| CA1304 | [CA1304: Určete CultureInfo](../code-quality/ca1304.md) | Metoda nebo konstruktor volá člen, který má přetížení přijímající parametr System.Globalization.CultureInfo, a tato metoda nebo konstruktor nevolá přetížení přebírající parametr CultureInfo. Pokud objekt CultureInfo nebo System.IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1305 | [CA1305: Určete IFormatProvider](../code-quality/ca1305.md) | Metoda nebo konstruktor volá jeden nebo více členů, které mají přetížení přijímající parametr System.IFormatProvider, a tato metoda nebo konstruktor nevolá přetížení, která přebírá parametr IFormatProvider. Pokud objekt System.Globalization.CultureInfo nebo IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1306 | [CA1306: Nastavte národního prostředí pro datové typy](../code-quality/ca1306.md) | Národní prostředí určuje prvky prezentace specifické kultury pro data, například formátování použité pro číselné hodnoty, symboly měny a pořadí řazení. Při vytváření objektu DataSet nebo DataTable byste měli explicitně nastavit národní prostředí. |
| CA1307 | [CA1307: Určete StringComparison](../code-quality/ca1307.md) | Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison. |
| CA1308 |[CA1308: Normalizujte řetězce na velká písmena](../code-quality/ca1308.md) | Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků nedokáže po převodu na malá písmena provést zpáteční cestu. |
| CA1309 | [CA1309: Použijte řadový StringComparison](../code-quality/ca1309.md) | Nelingvistická operace porovnání řetězců nemá nastaven parametr StringComparison na hodnotu Ordinal ani na hodnotu OrdinalIgnoreCase. Explicitním nastavením parametru na hodnotu StringComparison.Ordinal nebo StringComparison.OrdinalIgnoreCase dojde ke zrychlení kódu a zvýšení přesnosti a spolehlivosti. |
| CA1400 | [CA1400: vstupní body volání nespravovaného volání by měly existovat](../code-quality/ca1400.md) |Veřejná nebo chráněná metoda je označena pomocí atributu System.Runtime.InteropServices.DllImportAttribute. Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně. |
| CA1401 | [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401.md) | Veřejná nebo chráněná metoda ve veřejném typu má atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Tyto metody by neměly být vystaveny. |
| CA1402 |[CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM](../code-quality/ca1402.md) | Když jsou přetížené metody vystaveny klientům modulu COM, zachová svůj název pouze první přetížení metody. Následná přetížení jsou jednoznačně přejmenována přidáním podtržítka (_) a celého čísla odpovídajícího pořadí deklarace tohoto přetížení. |
| CA1403 | [CA1403: Typy automatického rozložení by neměly být viditelné modelu COM](../code-quality/ca1403.md) | Typ hodnoty viditelný v modelu COM je označen pomocí atributu System. Runtime. InteropServices. StructLayoutAttribute nastaveného na hodnotu LayoutKind. auto. Rozložení těchto typů se může změnit mezi verzemi rozhraní .NET, čímž dojde k přerušení klientů modelu COM, kteří očekávají určité rozložení. |
| CA1404 | [CA1404: volejte GetLastError hned po volání nespravovaného volání](../code-quality/ca1404.md) | Bylo provedeno volání metody Marshal. GetLastWin32Error nebo ekvivalentní [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] Funkce GetLastError a bezprostředně předchozí volání není metodou vyvolání operačního systému. |
| CA1405 | [CA1405: Základní typy viditelného typu modelu COM by měly být viditelné modelu COM](../code-quality/ca1405.md) | Typ viditelný modulem COM je odvozen od typu, který není viditelný modulem COM. |
| CA1406 |[CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6](../code-quality/ca1406.md) | Klienti modelu COM Visual Basic 6 nemají přístup k 64 celých čísel. |
| CA1407 |[CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407.md) | Modul COM nepodporuje statické metody. |
| CA1408 | [CA1408: Nepoužívejte typ AutoDual ClassInterface](../code-quality/ca1408.md) | Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Pokud ve výchozím nastavení není zadán atribut ClassInterfaceAttribute, použije se pouze rozhraní určené pro odesílání. |
| CA1409 | [CA1409: Viditelné typy modelu COM by měly být vytvořitelné](../code-quality/ca1409.md) |Odkazový typ, který je označen jako viditelný modulům COM, obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů). Typ bez veřejného výchozího konstruktoru není možné vytvořit klienty typu COM. |
| CA1410 | [CA1410: Metody registrace modelu COM by si měly odpovídat](../code-quality/ca1410.md) | Typ deklaruje metodu, která je označena atributem System.Runtime.InteropServices.ComRegisterFunctionAttribute, ale nedeklaruje metodu označenou pomocí atributu System.Runtime.InteropServices.ComUnregisterFunctionAttribute, a naopak. |
| CA1411 | [CA1411: Metody registrace modelu COM by neměly být viditelné](../code-quality/ca1411.md) | Metoda označená pomocí atributu System.Runtime.InteropServices.ComRegisterFunctionAttribute nebo atributu System.Runtime.InteropServices.ComUnregisterFunctionAttribute je externě viditelná. |
| CA1412 | [CA1412: Označte rozhraní ComSource jako IDispatch](../code-quality/ca1412.md) | Typ je označen atributem System.Runtime.InteropServices.ComSourceInterfacesAttribute a alespoň jedno ze zadaných rozhraní není označeno pomocí atributu System.Runtime.InteropServices.InterfaceTypeAttribute nastaveného na hodnotu ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Vyhněte se neveřejným polím v typech hodnot viditelných modulem COM](../code-quality/ca1413.md) | Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Zkontrolujte obsah polí, zda neobsahují informace, které by neměly být vystaveny nebo které budou mít nežádoucí účinky na návrh nebo zabezpečení. |
| CA1414 | [CA1414: označte logické argumenty P/Invoke s MarshalAs](../code-quality/ca1414.md) | Datový typ Boolean má v nespravovaném kódu různé reprezentace. |
| CA1415 | [CA1415: deklarujte správně volání nespravovaných kódů](../code-quality/ca1415.md) | Toto pravidlo vyhledá deklarace metod s operačním systémem, které cílí [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] na funkce, které mají ukazatel na PŘEkrývající se parametr struktury a odpovídající spravovaný parametr není ukazatel na strukturu System. Threading. NativeOverlapped. |
| CA1500 | [CA1500: Názvy proměnných by neměly odpovídat názvům polí](../code-quality/ca1500.md) | Metoda instance deklaruje parametr nebo lokální proměnnou, jejichž název odpovídá poli instance deklarovaného typu, což vede k chybám. |
| CA1501 | [CA1501: Vyhněte se nadměrné dědičnosti](../code-quality/ca1501.md) | Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti. Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. |
| CA1502 | [CA1502: Vyhněte se nadměrné složitosti](../code-quality/ca1502.md) | Toto pravidlo měří počet lineárně nezávislých cest skrze metodu, což je určeno počtem a složitostí podmínkových větví. |
| CA1504 | [CA1504: Zkontrolujte zavádějící názvy polí](../code-quality/ca1504.md) | Název pole instance začíná řetězcem "s_", nebo název statického (sdíleného v Visual Basic) pole začíná řetězcem "m_". |
| CA1505 | [CA1505: Vyhněte se neudržovatelnému kódu](../code-quality/ca1505.md) | Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti. Nízký index udržovatelnosti označuje, že typ nebo metodu je pravděpodobně obtížné udržovat a je vhodné ji znovu navrhnout. |
| CA1506 | [CA1506: Vyhněte se nadměrnému párování tříd](../code-quality/ca1506.md) | Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje. |
| CA1507 | [CA1507: Místo řetězce použijte výraz nameof.](../code-quality/ca1507.md) | Řetězcový literál se používá jako argument, ve kterém `nameof` by se mohl použít výraz. |
| CA1508 | [CA1508: Vyhněte se mrtvému podmíněnému kódu](../code-quality/ca1508.md) | Metoda má podmíněný kód, který se vždy vyhodnocuje `true` za `false` běhu nebo za běhu. To vede k nedoručenému kódu ve `false` větvi podmínky. |
| CA1509 | [CA1509: Neplatná položka v souboru konfigurace metrik kódu](../code-quality/ca1509.md) | Pravidla metrik kódu, například [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) a [CA1506](ca1506.md), dodaly konfigurační soubor s názvem `CodeMetricsConfig.txt` , který má neplatnou položku. |
| CA1600 | [CA1600: Nepoužívejte prioritu nečinného procesu](../code-quality/ca1600.md) | Nenastavujte prioritu procesu na Neaktivní. Procesy, které mají nastaveny System.Diagnostics.ProcessPriorityClass.Idle, budou zaměstnávat procesor, pokud by jinak byl nečinný, a tím budou blokovat úsporný režim. |
| CA1601 | [CA1601: Nepoužívejte časovače, které zabraňují změně stavu napájení](../code-quality/ca1601.md) | Vyšší frekvence periodické aktivity budou udržovat procesor zaneprázdněný a ovlivňovat časovače úspory energie nečinnosti, které vypnou zobrazení a pevné disky. |
| CA1700 | [CA1700: Nepojmenovávejte výčty hodnot 'Reserved'](../code-quality/ca1700.md) | Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. |
| CA1701 | [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701.md) | Každé slovo řetězce zdroje je rozděleno na tokeny na základě velikosti písmen. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla. |
| CA1702 | [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702.md) | Název identifikátoru obsahuje více slov a alespoň jedno ze slov se zdá být složené slovo, které není správně formátováno. |
| CA1703 | [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703.md) | Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA1704 | [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704.md) | Název externě viditelného identifikátoru obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA1707 | [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707.md) | Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry. |
| CA1708 | [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708.md) | Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena. |
| CA1709 | [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709.md) | Podle konvence používají názvy parametrů zápis typu CamelCase a názvy oborů názvů, typů a členů používají zápis typu PascalCase. |
| CA1710 | [CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710.md) |Podle konvence by měly názvy typů, které rozšiřují některé základní typy nebo určitá rozhraní, nebo typů odvozených z těchto typů mít příponu přidruženou těmto typům nebo rozhraním. |
| CA1711 | [CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711.md) | Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony. |
| CA1712 | [CA1712: Nezačínejte hodnoty výčtu názvem typu](../code-quality/ca1712.md) | Názvy členů výčtu nemají předponu názvu typu, protože se očekává, že vývojové nástroje poskytují informace o typu. |
| CA1713 | [CA1713: Události by neměly mít předponu před nebo po](../code-quality/ca1713.md) | Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí. |
| CA1714 | [CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714.md) | Veřejný výčet má atribut System.FlagsAttribute a jeho název nekončí písmenem „s“. Typy označené pomocí atributu FlagsAttribute mají názvy, které jsou v množném čísle, protože tento atribut označuje, že lze zadat více než jednu hodnotu. |
| CA1715 | [CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715.md) | Název externě viditelného rozhraní nezačíná velkým písmenem „I“. Název parametru obecného typu u externě viditelného typu nebo metody nezačíná velkým písmenem „T“. |
| CA1716 | [CA1716: Identifikátory by se neměly shodovat s klíčovými slovy](../code-quality/ca1716.md) | Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime). |
| CA1717 | [CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle](../code-quality/ca1717.md) | Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu. |
| CA1719 | [CA1719: Názvy parametrů by se neměly shodovat s názvy členů](../code-quality/ca1719.md) | Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam členu. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou. |
| CA1720 |[CA1720: Identifikátory by neměly obsahovat názvy typů](../code-quality/ca1720.md) | Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka. |
| CA1721 | [CA1721: Názvy vlastností by se neměly shodovat s metodami Get](../code-quality/ca1721.md) |Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce. |
| CA1722 | [CA1722: Identifikátory by neměly mít nesprávnou předponu](../code-quality/ca1722.md) | Podle konvence mají pouze některé programovací prvky názvy začínající určitou předponou. |
| CA1724 | [CA1724: Názvy typů by se neměly shodovat s obory názvů](../code-quality/ca1724.md) | Názvy typů by neměly odpovídat názvům oborů názvů .NET. Porušení tohoto pravidla může snížit použitelnost knihovny. |
| CA1725 | [CA1725: Názvy parametrů by měly odpovídat základní deklaraci](../code-quality/ca1725.md) | Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody. |
| CA1726 | [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726.md) | Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Název případně obsahuje také výraz „Flag“ nebo „Flags“. |
| CA1800 | [CA1800: Nepřetypujte zbytečně](../code-quality/ca1800.md) | Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. |
| CA1801 | [CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801.md) | Podpis metody obsahuje parametr, který není použit v těle metody. |
| CA1802 |[CA1802: Použijte literály, kde je to vhodné](../code-quality/ca1802.md) |Pole je deklarováno jako static a jen pro čtení (Shared a ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) a je inicializováno pomocí hodnoty, která je v době kompilace Compute. Vzhledem k tomu, že hodnota, která je přiřazena cílovému poli je COMPUTE v době kompilace, změňte deklaraci na pole const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ), aby se hodnota vypočítala v době kompilace místo v době běhu. |
| CA1804 | [CA1804: Odeberte nepoužívané lokální hodnoty](../code-quality/ca1804.md) | Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon. |
| CA1806 | [CA1806: Neignorujte výsledky metody](../code-quality/ca1806.md) | Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije. |
| CA1809 |[CA1809: Vyhněte se nadměrným lokálním hodnotám](../code-quality/ca1809.md) | Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“. Chcete-li zvýšit pravděpodobnost, že jsou všechny místní proměnné registrován, omezte počet místních proměnných na 64. |
| CA1810 | [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810.md) | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
| CA1811 | [CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811.md) | Soukromý nebo interní člen (na úrovni sestavení) nemá v sestavení žádné volající, není vyvolán modulem CLR (Common Language Runtime) ani není vyvolán delegátem. |
| CA1812 | [CA1812: Vyhněte se nevytvořeným instancím interních tříd](../code-quality/ca1812.md) | Instance typu na úrovni sestavení není vytvořena kódem v sestavení. |
| CA1813 | [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813.md) | Rozhraní .NET poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon. |
| CA1814 | [CA1814: Upřednostněte vícenásobná pole před multidimenzionálními](../code-quality/ca1814.md) | Vícenásobné pole je pole, jehož prvky jsou pole. Pole tvořící prvky mohou být různě velká, což vede k menšímu nevyužitému místu u některých sad dat. |
| CA1815 | [CA1815: Přepište rovnosti a operátory rovnosti u typů hodnot](../code-quality/ca1815.md) | Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals. |
| CA1816 | [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816.md) | Metoda, která je implementací metody Dispose, nevolá GC. SuppressFinalize nebo metoda, která není implementací volání Dispose, volá GC. SuppressFinalize nebo metoda volá GC. SuppressFinalize a projde něco jiného než to (já v Visual Basic). |
| CA1819 | [CA1819: Vlastnosti by neměly vracet pole](../code-quality/ca1819.md) | Pole vrácená vlastnostmi nejsou chráněna proti zápisu, i když je vlastnost jen pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. |
| CA1820 | [CA1820: Testujte prázdné řetězce pomocí délky řetězce](../code-quality/ca1820.md) | Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals. |
| CA1821 | [CA1821: Odeberte prázdné finalizační metody](../code-quality/ca1821.md) | Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda zvyšuje nároky a nemá žádný užitek. |
| CA1822 |[CA1822: Označte členy jako statické](../code-quality/ca1822.md) | Členy, kteří nemají přístup k datům instance nebo metodám instance volání, mohou být označeny jako statické (sdílené v rámci [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód. |
| CA1823 | [CA1823: Vyhněte se nepoužitým privátním polím](../code-quality/ca1823.md) | Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná. |
| CA1824 |[CA1824: Označte sestavení pomocí NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | Atribut NeutralResourcesLanguage informuje správce prostředků jazyka, který byl použit k zobrazení prostředků neutrální jazykové verze pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu. |
| CA1825 |[CA1825: Vyhněte se přidělení pole s nulovou délkou.](../code-quality/ca1825.md) | Inicializace pole nulové délky vede k nepotřebnému přidělení paměti. Místo toho použijte staticky přidělenou instanci prázdného pole voláním <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Přidělení paměti se sdílí ve všech voláních této metody. |
| CA1826 |[CA1826: Použijte vlastnost namísto vyčíslitelné metody Linq](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>Metoda LINQ byla použita pro typ, který podporuje ekvivalentní, efektivnější vlastnost. |
| CA1827 |[CA1827: Nepoužívejte Count/LongCount, když se dá použít Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A>nebo <xref:System.Linq.Enumerable.LongCount%2A> se použila metoda, kde <xref:System.Linq.Enumerable.Any%2A> by byla metoda efektivnější. |
| CA1828 |[CA1828: Nepoužívejte CountAsync/LongCount, když se dá použít AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A>nebo <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> se použila metoda, kde <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> by byla metoda efektivnější. |
| CA1829 |[CA1829: Použijte vlastnost Length/Count místo metody Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>Metoda LINQ byla použita pro typ, který podporuje ekvivalentní, efektivnější `Length` nebo `Count` vlastnost. |
| CA1830 |[CA1830: preferovat silné typy připojení a vkládání metod v typu StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A>a <xref:System.Text.StringBuilder.Insert%2A> Poskytněte přetížení pro více typů mimo <xref:System.String> .  Pokud je to možné, preferovat přetížení silného typu přes použití rozhraní ToString () a přetížení založeného na řetězci. |
| CA1831 |[CA1831: Tam, kde je to možné, používat u řetězců místo indexerů založených na rozsahu metodu AsSpan](../code-quality/ca1831.md) | Při použití rozsahu indexeru na řetězec a implicitně přiřadí hodnotu ReadOnlySpan &lt; &gt; typu char, metoda <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> bude použita místo <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části řetězce. |
| CA1832 |[CA1832: Pro získání části ReadOnlySpan nebo ReadOnlyMemory pole používat místo indexerů založených na rozsahu metodu AsSpan nebo AsMemory](../code-quality/ca1832.md) | Při použití rozsahu indexeru v poli a implicitně přiřadí hodnotu <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> typu nebo, bude <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> použita metoda namísto <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části pole. |
| CA1833 |[CA1833: Pro získání části Span nebo Memory pole používat místo indexerů založených na rozsahu metodu AsSpan nebo AsMemory](../code-quality/ca1833.md) | Při použití rozsahu indexeru v poli a implicitně přiřadí hodnotu <xref:System.Span%601> <xref:System.Memory%601> typu nebo, bude <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> použita metoda namísto <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části pole. |
| CA1835 |[CA1835: preferovat přetížení založené na Memory' pro ReadAsync a WriteAsync](../code-quality/ca1835.md) | ' Stream ' má přetížení ' ReadAsync ', které jako první argument přebírá ' paměť &lt; Byte &gt; ' a přetížení ' WriteAsync ', které jako první argument přebírá ' &lt; ReadOnlyMemory byte &gt; '. Preferovat volání přetížení založeného na paměti, což je efektivnější. |
| CA1900 | [CA1900: Pole typů hodnot by měla být přenosná](../code-quality/ca1900.md) | Toto pravidlo kontroluje, zda struktury, které jsou deklarovány pomocí explicitního rozložení, budou při zařazení na nespravovaný kód v 64bitových operačních systémech správně zarovnány. |
| CA1901 | [CA1901: deklarace P/Invoke by měly být přenosné](../code-quality/ca1901.md) | Toto pravidlo vyhodnotí velikost každého parametru a vrácené hodnoty vyvolání P/Invoke a ověří, zda je velikost parametru správná při zařazení na nespravovaný kód na 32bitových a 64bitových operačních systémech. |
| CA1903 | [CA1903: Používejte jen rozhraní API z cílové architektury](../code-quality/ca1903.md) | Člen nebo typ používá člen nebo typ, který byl uveden v aktualizaci Service Pack, která nebyla zahrnuta stejně jako cílové rozhraní projektu. |
| CA2000 | [CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000.md) | Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah. |
| CA2001 | [CA2001: Vyhněte se volání problematických metod](../code-quality/ca2001.md) | Člen volá potencionálně nebezpečnou nebo problematickou metodu. |
| CA2002 |[CA2002: Nepoužívejte zámky u objektů se slabou identitou](../code-quality/ca2002.md) |Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt. |
| CA2003 |[CA2003: Nezacházejte s vlákénky jako s vlákny](../code-quality/ca2003.md) | Spravované vlákno se považuje za [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] vlákno. |
| CA2004 | [CA2004: Odeberte volání GC.KeepAlive](../code-quality/ca2004.md) | Pokud převádíte na použití SafeHandle, odeberte veškerá volání GC.KeepAlive (object). V tomto případě by třídy neměly volat metodu GC.KeepAlive. To předpokládá, že nemají destruktor, ale spoléhají na SafeHandle, že dokončí popisovač operačního systému za ně. |
| CA2006 | [CA2006: Použijte SafeHandle k zapouzdření nativních prostředků](../code-quality/ca2006.md) | Použití IntPtr ve spravovaném kódu může znamenat možný problém zabezpečení a spolehlivosti. Všechna použití IntPtr musí být přezkoumána za účelem určení, zda je použití SafeHandle (nebo podobné technologie) na tomto místě vyžadováno. |
| CA2007 | [CA2007: Nečekejte přímo na úlohu](ca2007.md) | Asynchronní metoda [čeká](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> přímo. Když asynchronní metoda čeká <xref:System.Threading.Tasks.Task> přímo, pokračování probíhá ve stejném vláknu, které úlohu vytvořilo. Toto chování může být nákladné v souvislosti s výkonem a může způsobit zablokování ve vlákně uživatelského rozhraní. Zvažte volání <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> , abyste vyvolali svůj záměr na pokračování. |
| CA2009 | [CA2009: Nevolejte ToImmutableCollection pro hodnotu ImmutableCollection](ca2009.md) | `ToImmutable`Metoda byla nutně volána pro neproměnlivou kolekci z <xref:System.Collections.Immutable> oboru názvů. |
| CA2011 | [CA2011: Nepřiřazujte vlastnost v rámci její metody setter](ca2011.md) | Vlastnost byla omylem přiřazena hodnota v rámci vlastního [přístupového objektu set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| CA2012 | [CA2012: Správně použít hodnoty ValueTask](ca2012.md) | ValueTasks vrácené z vyvolání členů mají být přímo očekávány.  Pokusí se využít ValueTask vícekrát nebo získat přímý přístup k jednomu výsledku před tím, než je známý k dokončení, může způsobit výjimku nebo poškození.  Ignorování takového ValueTask je pravděpodobně indikace funkční chyby a může snížit výkon. |
| CA2013 | [CA2013: Nepoužívejte ReferenceEquals s typy hodnot](ca2013.md) | Při porovnávání hodnot pomocí <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , jsou-li objA a objB typy hodnot, jsou zabaleny před předáním do <xref:System.Object.ReferenceEquals%2A> metody. To znamená, že i když obě objA a objB reprezentují stejnou instanci typu hodnoty, <xref:System.Object.ReferenceEquals%2A> metoda ale přesto vrátí hodnotu false. |
| CA2014 | [CA2014: Nepoužívejte stackalloc ve smyčce.](ca2014.md) | Prostor zásobníku přidělený stackalloc je vydaný jenom na konci vyvolání aktuální metody.  Použití ve smyčce může mít za následek neohraničený nárůst zásobníku a případné podmínky přetečení zásobníku. |
| CA2015 | [CA2015: nedefinujte finalizační metody pro typy odvozené z MemoryManager &lt; T&gt;](ca2015.md) | Přidání finalizační metody do typu odvozeného z <xref:System.Buffers.MemoryManager%601> může umožnit uvolnění paměti, pokud je stále používána <xref:System.Span%601> . |
| CA2100 | [CA2100: Zkontrolujte chyby zabezpečení u dotazů SQL](../code-quality/ca2100.md) | Metoda nastavuje vlastnost System.Data.IDbCommand.CommandText pomocí řetězce, který je sestaven z řetězcového argumentu k metodě. Toto pravidlo předpokládá, že řetězcový argument obsahuje vstup uživatele. Řetězec příkazu SQL sestavený ze vstupu uživatele je ohrožen útoky prostřednictvím injektáže SQL. |
| CA2101 |[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného voláním](../code-quality/ca2101.md) | Člen vyvolání platformy povoluje částečně důvěryhodné volající, má řetězcový parametr a explicitně nezařazuje řetězec. To může způsobit potenciální ohrožení zabezpečení. |
| CA2102 | [CA2102: Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách](../code-quality/ca2102.md) | Člen v sestavení, které není označeno pomocí atributu RuntimeCompatibilityAttribute nebo je označeno atributem RuntimeCompatibility(WrapNonExceptionThrows = false), obsahuje zachytávací blok, který zpracovává typ System.Exception a neobsahuje bezprostředně následující obecný zachytávací blok. |
| CA2103 | [CA2103: Zkontrolujte imperativní zabezpečení](../code-quality/ca2103.md) |Metoda používá imperativní zabezpečení a může vytvářet oprávnění pomocí stavové informace nebo návratové hodnoty, která se může změnit, pokud je žádost aktivní. Používejte deklarativní zabezpečení vždy, když je to možné. |
| CA2104 |[CA2104: Nedeklaruje proměnlivé odkazové typy pouze pro čtení](../code-quality/ca2104.md) | Externě viditelný typ obsahuje externě viditelné pole měnitelného referenčního typu, které je určeno jen pro čtení. Měnitelný typ je typ, jehož instanční data lze upravit. |
| CA2105 | [CA2105: Pole s poli by neměla být pouze pro čtení](../code-quality/ca2105.md) |Když použijete modifikátor jen pro čtení (jen pro čtení v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) na pole, které obsahuje pole, nelze změnit pole tak, aby odkazovalo na jiné pole. Avšak prvky pole, které jsou uloženy v poli určeném jen pro čtení, mohou být změněny. |
| CA2106 | [CA2106: Zabezpečte kontrolní příkazy](../code-quality/ca2106.md) | Metoda uplatňuje oprávnění a na volajícím nejsou vykonány žádné kontroly zabezpečení. Uplatnění oprávnění zabezpečení bez provedení jakékoliv kontroly zabezpečení může zanechat ve vašem kódu zneužitelné slabé stránky zabezpečení. |
| CA2107 | [CA2107: Zkontrolujte použití čistého odepření a povolení](../code-quality/ca2107.md) |Metoda PermitOnly a akce zabezpečení CodeAccessPermission. Deny by měly být používány pouze pomocí těch, kteří mají pokročilé znalosti zabezpečení .NET. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení. |
| CA2108 | [CA2108: Zkontrolujte deklarativní zabezpečení u typů hodnot](../code-quality/ca2108.md) | Veřejný nebo chráněný hodnotový typ je zabezpečen pomocí přístupu k datům nebo požadavků propojení. |
| CA2109 | [CA2109: Zkontrolujte viditelné obslužné rutiny událostí](../code-quality/ca2109.md) | Byla zjištěna veřejná nebo chráněná metoda zpracování událostí. Metody zpracování událostí by neměly být vystaveny, pokud to není nezbytně nutné. |
| CA2111 |[CA2111: Ukazatele by neměly být viditelné](../code-quality/ca2111.md) | Ukazatel není soukromý, interní nebo jen pro čtení. Škodlivý kód může změnit hodnotu ukazatele, což potenciálně umožňuje přístup do libovolného umístění v paměti nebo může způsobit selhání aplikace nebo systému. |
| CA2112 | [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112.md) | Veřejný nebo chráněný typ obsahuje veřejná pole a je zabezpečen pomocí požadavků propojení. Pokud má kód přístup k instanci typu, která je zabezpečena pomocí požadavku propojení, nemusí kód vyhovět požadavku propojení pro přístup k polím tohoto typu. |
| CA2114 | [CA2114: Zabezpečení metod by mělo být nadmnožinou typu](../code-quality/ca2114.md) | Metoda by neměla mít pro stejnou akci deklarativní zabezpečení jak na úrovni metody, tak na úrovni typu. |
| CA2115 | [CA2115: Volejte GC.KeepAlive při použití nativních prostředků](../code-quality/ca2115.md) | Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem. |
| CA2116 | [CA2116: Metody APTCA by měly volat pouze metody APTCA](../code-quality/ca2116.md) |Když je pro plně důvěryhodná sestavení uveden atribut APTCA (AllowPartiallyTrustedCallersAttribute) a sestavení spustí kód v jiném sestavení, které neumožňuje volání částečně důvěryhodným volajícím, může se jednat o chybu v zabezpečení. |
| CA2117 | [CA2117: Typy APTCA by měl rozšiřovat pouze základní typy APTCA](../code-quality/ca2117.md) | Když je pro plně důvěryhodná sestavení uveden atribut APTCA a v sestavení je odvozen z typu, který neumožňuje volání částečně důvěryhodným volajícím, může se jednat o chybu v zabezpečení. |
| CA2118 | [CA2118: Zkontrolujte použití SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118.md) |Atribut SuppressUnmanagedCodeSecurityAttribute mění výchozí chování zabezpečení systému pro členy vykonávající nespravovaný kód, který používá zprostředkovatele komunikace s objekty COM nebo vyvolání operačního systému. Tento atribut slouží především ke zvýšení výkonu, ačkoliv nárůst výkonu může být spojen s významnými riziky zabezpečení. |
| CA2119 | [CA2119: Zapečeťte metody, které vyhovují privátním rozhraním](../code-quality/ca2119.md) | Dědičný veřejný typ poskytuje implementaci přepsatelné metody interního (Friend v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) rozhraní. Chcete-li opravit porušení tohoto pravidla, zabraňte přepsání metody mimo sestavení. |
| CA2120 | [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120.md) | Tento typ má konstruktor, který přebírá objekt System.Runtime.Serialization.SerializationInfo a objekt System.Runtime.Serialization.StreamingContext (podpis serializace konstruktoru). Tento konstruktor není zabezpečen pomocí kontroly zabezpečení, ale jeden nebo více běžných konstruktorů tohoto typu je zabezpečených. |
| CA2121 | [CA2121: Statické konstruktory by měly být privátní](../code-quality/ca2121.md) | Systém volá statický konstruktor před vytvořením první instance typu nebo předtím, než jsou odkazovány jakékoli statické členy. Pokud statický konstruktor není soukromý, může být volán jiným kódem než kódem systému. V závislosti na operacích, které jsou provedeny v konstruktoru, to může způsobit neočekávané chování. |
| CA2122 | [CA2122: Nezveřejňujte nepřímo metody s požadavky propojení](../code-quality/ca2122.md) | Veřejný nebo chráněný člen má požadavky propojení a je volán členem, který neprovádí žádné bezpečnostní kontroly. Požadavek propojení kontroluje pouze oprávnění bezprostředního volajícího. |
| CA2123 | [CA2123: Požadavky na propojení přepisů by měly být identické s bází](../code-quality/ca2123.md) | Toto pravidlo přiřazuje metodu své základní metodě, kterou je buď rozhraní, nebo virtuální metoda jiného typu, a poté v obou metodách srovnává požadavky propojení. Je-li toto pravidlo porušeno, může chybný volající obejít požadavek propojení pouhým voláním nezabezpečené metody. |
| CA2124 | [CA2124: Zabalte ohroženou klauzuli finally do vnějšího bloku try](../code-quality/ca2124.md) | Veřejná nebo chráněná metoda obsahuje blok try/finally. Blok finally nejspíše obnovuje stav zabezpečení a sám není uzavřen v bloku finally. |
| CA2126 | [CA2126: Požadavky na propojení typů vyžadují požadavky na dědičnost](../code-quality/ca2126.md) | Veřejný nezapečetěný typ je chráněn pomocí požadavku propojení a má přepisovatelnou metodu. Tento typ ani tato metoda nejsou chráněny pomocí vyžádané dědičnosti. |
| CA2130 | [CA2130: Konstanty kritické pro zabezpečení musí být transparentní](../code-quality/ca2130.md) | Pro konstantní hodnoty není vynucována transparentnost, protože kompilátory vkládají konstantní hodnoty do kódu, aby za běhu programu nebylo zapotřebí žádné vyhledávání. Konstantní pole by měla být transparentní z pohledu zabezpečení, aby kontroloři kódu nepředpokládali, že transparentní kód nemůže ke konstantě přistoupit. |
| CA2131 | [CA2131: Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů](../code-quality/ca2131.md) | Typ se účastní porovnávání typu, přičemž typ samotný nebo jeho člen nebo pole jsou označeny atributem SecurityCriticalAttribute. Toto pravidlo nastává pro všechny kritické typy nebo typy obsahující kritické metody nebo pole, která se účastní porovnávání typu. Když modul CLR zjistí takový typ, nenačítá jej a za běhu vyvolá výjimku TypeLoadException. Obvykle je toto pravidlo vyvoláno pouze v případě, že uživatelé implementují rovnocennost typu ručně namísto prostřednictvím tlbimp a provedení rovnocennosti typu kompilátorem. |
| CA2132 | [CA2132: Výchozí konstruktory musí být alespoň tak kritické, jako výchozí konstruktory základního typu](../code-quality/ca2132.md) |Typy a členy, které mají atribut SecurityCriticalAttribute, nelze použít kódem aplikace Silverlight. Typy a členy kritické z hlediska zabezpečení lze použít pouze prostřednictvím důvěryhodného kódu v knihovně tříd rozhraní .NET Framework aplikace Silverlight. Protože veřejné nebo chráněné konstrukce v odvozené třídě musí mít stejnou nebo větší transparentnost než jejich základní třída, nelze třídu v aplikaci odvodit z třídy označené jako SecurityCritical. |
| CA2133 | [CA2133: Delegáti musí mít vazbu s metodami s konzistentní transparentností](../code-quality/ca2133.md) | Toto upozornění je vyvoláno na metodě, která vytvoří vazbu delegáta označeného pomocí atributu SecurityCriticalAttribute na metodu, která je transparentní nebo která je označena pomocí atributu SecuritySafeCriticalAttribute. Upozornění je také vyvoláno na metodě, která vytvoří vazbu transparentního delegáta nebo bezpečně kritického delegáta na kritickou metodu. |
| CA2134 | [CA2134: Metody musí při přepisování základních metod zachovávat konzistentní transparentnost](../code-quality/ca2134.md) |Toto pravidlo je vyvoláno, když metoda označená pomocí atributu SecurityCriticalAttribute přepíše metodu, která je transparentní nebo označená pomocí atributu SecuritySafeCriticalAttribute. Toto pravidlo je vyvoláno také, když transparentní metoda nebo metoda označená pomocí atributu SecuritySafeCriticalAttribute přepíše metodu, která je označená pomocí atributu SecurityCriticalAttribute. Pravidlo je použito při přepisování virtuální metody nebo implementaci rozhraní. |
| CA2135 | [CA2135: Sestavení úrovně 2 by neměla obsahovat LinkDemands](../code-quality/ca2135.md) | Pravidla LinkDemand jsou v sadě pravidel zabezpečení úrovně 2 již zastaralá. Namísto použití pravidel LinkDemand k vynucení zabezpečení v době kompilace JIT označte metody, typy a pole pomocí atributu SecurityCriticalAttribute. |
| CA2127 | [CA2136: Členy by neměly mít konfliktní poznámky transparentnosti](../code-quality/ca2136.md) | V transparentním sestavení 100% se nemůže vyskytovat kritický kód. Toto pravidlo analyzuje 100% transparentní sestavení pro jakékoliv poznámky SecurityCritical na úrovni typu, pole a metody. |
| CA2136 | [CA2136: Členy by neměly mít konfliktní poznámky transparentnosti](../code-quality/ca2136.md) | Atributy transparentnosti jsou použity z prvků kódu většího rozsahu na prvky menšího rozsahu. Atributy transparentnosti prvků kódu, které mají větší rozsah, mají přednost před atributy transparentnosti prvků kódu, které jsou obsaženy v prvním prvku. Například třída označená atributem SecurityCriticalAttribute nemůže obsahovat metodu, která je označena atributem SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Transparentní metody musí obsahovat pouze ověřitelné IL](../code-quality/ca2137.md) | Metoda obsahuje kód, který nelze ověřit, nebo vrací typ odkazem. Toto pravidlo je vyvoláno při pokusech transparentního kódu zabezpečení spustit jazyk MSIL, který nelze ověřit. Pravidlo však neobsahuje úplný ověřovatel jazyka IL a místo toho k zachycení většiny porušení ověření jazyka MSIL používá heuristiky. |
| CA2138 | [CA2138: Transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity](../code-quality/ca2138.md) | Transparentní metoda zabezpečení volá metodu, která je označena atributem SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Transparentní metody nemusí používat atribut HandleProcessCorruptingExceptions](../code-quality/ca2139.md) | Toto pravidlo je vyvoláno, je-li jakákoliv metoda transparentní a pokusí se zpracovat výjimku poškozující proces použitím atributu HandleProcessCorruptedStateExceptionsAttribute. Výjimka poškozující proces je klasifikace výjimek dle specifikace CLR verze 4.0, jako například výjimka AccessViolationException. Atribut HandleProcessCorruptedStateExceptionsAttribute lze použít pouze metodami kritickými pro bezpečnost a bude ignorován, je-li použit u transparentních metod. |
| CA2129 | [CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení](../code-quality/ca2140.md) | Metody označené pomocí atributu SecurityTransparentAttribute volají neveřejné členy, které jsou označeny jako SecurityCritical. Toto pravidlo analyzuje všechny metody a typy v sestavení, které je transparentní/kritické, a označí všechna volání z transparentního kódu do neveřejného kritického kódu, která nejsou označena jako SecurityTreatAsSafe. |
| CA2140 | [CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení](../code-quality/ca2140.md) | Prvek kódu označený atributem SecurityCriticalAttribute je kritický pro zabezpečení. Transparentní metoda nemůže použít prvek kritický pro zabezpečení. Pokud se transparentní typ pokusí použít typ kritický pro zabezpečení, je vyvolána výjimka TypeAccessException, MethodAccessException nebo FieldAccessException. |
| CA2141 |[CA2141:Transparentní metody nesmějí vyhovovat LinkDemands](../code-quality/ca2141.md) | Transparentní metoda (z hlediska zabezpečení) volá metodu v sestavení, které není označeno atributem APTCA, nebo transparentní metoda (z hlediska zabezpečení) splňuje pravidlo LinkDemand pro typ nebo metodu. |
| CA2142 | [CA2142: Transparentní kód by neměl být chráněn pomocí LinkDemands](../code-quality/ca2142.md) | Toto pravidlo je vyvoláno transparentními metodami, které k přístupu vyžadují pravidla LinkDemand. Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. |
| CA2143 | [CA2143: Transparentní metody by neměly používat požadavky zabezpečení](../code-quality/ca2143.md) | Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. Kód transparentní z hlediska zabezpečení by měl k učinění rozhodnutí o zabezpečení používat úplné požadavky a bezpečně kritický kód by neměl spoléhat na to, že transparentní kód tyto úplné požadavky provede. |
| CA2144 | [CA2144: Transparentní kód by neměl načítat sestavení z bajtových polí](../code-quality/ca2144.md) | Přezkoumání zabezpečení transparentního kódu není tak úplné jako přezkoumání zabezpečení kritického kódu, protože transparentní kód nemůže provádět akce citlivé na zabezpečení. Sestavení, která jsou načtena z pole bajtů, nemohou být v transparentním kódu zaznamenána a takové pole bajtů může obsahovat kritický nebo důležitější bezpečně kritický kód, který musí být auditován. |
| CA2145 | [CA2145: Transparentní metody by neměly být doplněny o SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145.md) | Metody označené atributem SuppressUnmanagedCodeSecurityAttribute mají implicitní LinkDemand umístěn na jakoukoli metodu, která jej volá. Tento LinkDemand vyžaduje, aby byl volající kód kritický z hlediska zabezpečení. Označení metody, která používá SuppressUnmanagedCodeSecurity, atributem SecurityCriticalAttribute zviditelňuje tento požadavek pro volající metody. |
| CA2146 | [CA2146: Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní](../code-quality/ca2146.md) | Toto pravidlo je vyvoláno, když má odvozený typ atribut transparentnosti zabezpečení, který není tak kritický jako jeho základní typ nebo implementované rozhraní. Pouze kritické typy lze odvodit z kritických základních typů nebo mohou implementovat kritická rozhraní a pouze kritické typy nebo bezpečně kritické typy mohou být odvozeny ze základních bezpečně kritických typů nebo mohou implementovat bezpečně kritická rozhraní. |
| CA2128 |[CA2147: Transparentní metody nemusí používat kontrolní příkazy zabezpečení](../code-quality/ca2147.md) | Toto pravidlo analyzuje všechny metody a typy v sestavení, které je buď 100%-transparentní, nebo smíšené transparentní/kritické, a označí jakékoli deklarativní nebo imperativní použití výrazu Assert. |
| CA2147 |[CA2147: Transparentní metody nemusí používat kontrolní příkazy zabezpečení](../code-quality/ca2147.md) | U kódu označeného atributem SecurityTransparentAttribute není uděleno dostatečné oprávnění k vyhodnocení. |
| CA2149 | [CA2149: Transparentní metody nesmí provádět volání nativního kódu](../code-quality/ca2149.md) | Toto pravidlo je vyvoláno na každé transparentní metodě, která přímo volá nativní kód (například prostřednictvím P/Invoke). Porušení tohoto pravidla vede k vyvolání výjimky MethodAccessException v modelu transparentnosti úrovně 2 a k úplnému požadavku na nespravovaný kód v modelu transparentnosti úrovně 1. |
| CA2151 |[CA2151: Pole s kritickými typy by měla být kritická pro zabezpečení](../code-quality/ca2151.md) | Chcete-li používat typy kritické z hlediska zabezpečení, musí být kód, který odkazuje na typ, buď kritický z hlediska zabezpečení, nebo bezpečně kritický z hlediska zabezpečení. To platí i v případě, že je odkaz nepřímý. Proto je existence transparentního pole kritického z hlediska zabezpečení nebo transparentního pole bezpečně kritického z hlediska zabezpečení zavádějící, jelikož transparentní kód nebude mít k poli přístup. |
| CA2200 | [CA2200: Znovu vyvolejte pro zachování podrobností zásobníku](../code-quality/ca2200.md) | Výjimka je znovu vyvolána a je jednoznačně uvedena v příkazu throw. Jestliže je výjimka znovu vyvolána zadáním výjimky v příkazu throw, seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztracen. |
| CA2201 | [CA2201: Nevyvolávejte vyhrazené typy výjimek](../code-quality/ca2201.md) | Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2202 | [CA2202: Neuvolňujte objekty několikrát](../code-quality/ca2202.md) |Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání metody System.IDisposable.Dispose nebo ekvivalentní metody pro uvolnění (například metoda Close() u některých typů) stejného objektu. |
| CA2204 | [CA2204: Literály by měly být zadány správně](../code-quality/ca2204.md) | Řetězcový literál v těle metody obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA2205 | [CA2205: Použijte spravované ekvivalenty rozhraní Win32 API](../code-quality/ca2205.md) | Je definována metoda vyvolání operačního systému a metoda .NET, která má ekvivalentní funkci, je k dispozici. |
| CA2207 | [CA2207: Inicializujte statická pole s typem hodnoty vloženě](../code-quality/ca2207.md) | Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte. |
| CA2208 |[CA2208: Vytvořte správně instance výjimky argumentu](../code-quality/ca2208.md) | Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena. |
| CA2210 |[CA2210: Sestavení by měla mít platné silné názvy](../code-quality/ca2210.md) | Silný název chrání klienty před neúmyslným načtením narušeného sestavení. Sestavení bez silných názvů by kromě velmi omezených scénářů neměla být nasazována. Pokud sdílíte nebo šíříte sestavení, která nejsou správně podepsána, může být sestavení záměrně poškozeno, modul CLR je nemusí načíst nebo uživatelé mohou být nuceni vypnout na svém počítači ověřování. |
| CA2211 |[CA2211: Nekonstantní pole by neměla být viditelná](../code-quality/ca2211.md) | Statická pole, která nejsou konstantami ani nejsou jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy. |
| CA2212 | [CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod](../code-quality/ca2212.md) |Metoda typu, který je odvozen z typu System.EnterpriseServices.ServicedComponent, je označena pomocí atributu System.Web.Services.WebMethodAttribute. Protože atribut WebMethodAttribute a metoda ServicedComponent mají konfliktní chování a požadavky na kontext a tok transakcí, bude chování metody v některých případech nesprávné. |
| CA2213 | [CA2213: Uvolnitelná pole by měla být uvolněna](../code-quality/ca2213.md) | Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu. |
| CA2214 | [CA2214: Nevolejte přepisovatelné metody v konstruktorech](../code-quality/ca2214.md) | Při volání virtuální metody konstruktorem nemusí být konstruktor instance, která volá tuto metodu, proveden. |
| CA2215 | [CA2215: Metody Dispose by měly volat uvolnění základní třídy](../code-quality/ca2215.md) | Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose. |
| CA2216 |[CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216.md) | Typ, který implementuje rozhraní System.IDisposable a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno metodou Object.Finalize. |
| CA2217 | [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217.md) |Externě viditelný výčet je označen atributem FlagsAttribute a má jednu nebo více hodnot, které nejsou mocninami dvou nebo kombinací jiných definovaných hodnot výčtu. |
| CA2218 |[CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218.md) | Metoda GetHashCode vrací hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako například tabulku hash. Dva objekty, které jsou stejného typu a jsou stejné, musí vrátit stejnou hodnotu hash. |
| CA2219 | [CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219.md) | Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2220 | [CA2220: Finalizační metody by měly volat finalizační metodu základní třídy](../code-quality/ca2220.md) | Finalizační metoda musí být šířena přes hierarchii dědičnosti. Chcete-li to zaručit, musí typy zavolat metodu Finalize své základní třídy ve své vlastní metodě Finalize. |
| CA2221 |[CA2221: Finalizační metody by měly být chráněné](../code-quality/ca2221.md) | Finalizační metody musí použít modifikátor přístupu family. |
| CA2222 | [CA2222: Nesnižujte viditelnost zděděného členu](../code-quality/ca2222.md) |Modifikátor přístupu byste neměli měnit u zděděných členů. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody. |
| CA2223 | [CA2223: Členy by se měly lišit více než návratovým typem](../code-quality/ca2223.md) | Přestože modul CLR (Common Language Runtime) umožňuje používat návratové typy k rozlišení mezi jinak identickými členy, tato funkce není ve specifikaci CLS, ani není běžnou funkcí v programovacích jazycích rozhraní .NET. |
| CA2224 | [CA2224: Přepište Equals při přetížení operátoru rovnosti](../code-quality/ca2224.md) | Veřejný typ implementuje operátor rovnosti, ale nepřepisuje metodu Object.Equals. |
| CA2225 | [CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225.md) |Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích nepodporujících přetížené operátory. |
| CA2226 | [CA2226: Operátory by měly mít symetrická přetížení](../code-quality/ca2226.md) | Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor. |
| CA2227 |[CA2227: Vlastnosti kolekce by měly být pouze pro čtení](../code-quality/ca2227.md) |Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy. |
| CA2228 | [CA2228: Nedodávejte nevydané formáty prostředku](../code-quality/ca2228.md) | Soubory prostředků, které byly vytvořeny pomocí předprodejní verze rozhraní .NET, nemusí být použitelné pro podporované verze rozhraní .NET. |
| CA2229 | [CA2229: Implementujte serializační konstruktory](../code-quality/ca2229.md) | Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. |
| CA2230 | [CA2230: Použijte parametry pro proměnné argumenty](../code-quality/ca2230.md) | Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání VarArgs místo klíčového slova params. |
| CA2231 | [CA2231: Přetižte operátor rovnosti při přetížení ValueType.Equals](../code-quality/ca2231.md) | Hodnotový typ přepisuje metodu Object.Equals, ale neimplementuje operátor rovnosti. |
| CA2232 | [CA2232: Označte vstupní body modelu Windows Forms pomocí STAThread](../code-quality/ca2232.md) | Atribut STAThreadAttribute znamená, že model vláken aplikace COM je jednovláknový apartment (STA). Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně. |
| CA2233 |[CA2233: Operace by neměly přetéct](../code-quality/ca2233.md) | Aritmetické operace byste neměli provádět bez ověření operandů. Tím zajistíte, že výsledek operace není mimo rozsah možných hodnot použitých datových typů. |
| CA2234 | [CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234.md) | Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“. Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri. |
| CA2235 | [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235.md) | Neserializovatelný typ pole instance je deklarován v serializovatelném typu. |
| CA2236 | [CA2236: Volejte metody základní třídy u typů ISerializable](../code-quality/ca2236.md) | Chcete-li napravit porušení tohoto pravidla, zavolejte metodu GetObjectData základního typu nebo konstruktor serializace z odpovídající metody nebo konstruktoru odvozeného typu. |
| CA2237 | [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237.md) | Aby byl typ rozpoznán modulem CLR (Common Language Runtime) jako serializovatelný, musí být označen pomocí atributu SerializableAttribute, i když typ používá vlastní rutinu serializace prostřednictvím implementace rozhraní ISerializable. |
| CA2238 |[CA2238: Implementujte správně metody serializace](../code-quality/ca2238.md) | Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost. |
| CA2239 | [CA2239: Zadejte metody deserializace pro nepovinná pole](../code-quality/ca2239.md) | Typ má pole označené atributem System.Runtime.Serialization.OptionalFieldAttribute a neposkytuje metody zpracování událostí deserializace. |
| CA2240 | [CA2240: Implementujte správně ISerializable](../code-quality/ca2240.md) | Chcete-li opravit porušení tohoto pravidla, nastavte metodu GetObjectData jako viditelnou a přepisovatelnou a ujistěte se, že všechna pole instancí jsou součástí procesu serializace nebo výslovně označena pomocí atributu NonSerializedAttribute. |
| CA2241 | [CA2241: Zadejte správné argumenty pro metody formátování](../code-quality/ca2241.md) | Formátovací argument, který je předán metodě System.String.Format, neobsahuje formátovací položku, která odpovídá každému argumentu objektu nebo naopak. |
| CA2242 |[CA2242: Testujte správně NaN](../code-quality/ca2242.md) | Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double). |
| CA2243 |[CA2243: Řetězcové literály atributů by se měly správně parsovat](../code-quality/ca2243.md) | Parametr řetězcového literálu atributu nesprávně analyzuje adresu URL, identifikátor GUID nebo verzi. |
| CA2244 | [CA2244: Neduplikujte inicializace indexovaných elementů.](../code-quality/ca2244.md) | Inicializátor objektu má více než jeden inicializátor indexovaného elementu se stejným indexem konstanty. Všechny kromě posledního inicializátoru jsou redundantní. |
| CA2245 | [CA2245: Nepřiřazujte vlastnost k ní samotné.](../code-quality/ca2245.md) | Vlastnost byla omylem přiřazena sama sobě. |
| CA2246 | [CA2246: Nepřiřazujte symbol a jeho člena v témže příkazu.](../code-quality/ca2246.md) | Přiřazení symbolu a jeho členu, tedy pole nebo vlastnost, ve stejném příkazu není doporučeno. Není jasné, jestli má členský přístup za cíl použít starou hodnotu symbolu před přiřazením nebo novou hodnotou z přiřazení v tomto prohlášení. |
| CA2247 | [CA2247: argument předaný konstruktoru TaskCompletionSource by měl být parametr TaskCreationOptions enum namísto typ TaskContinuationOptions Enum.](../code-quality/ca2247.md) | TaskCompletionSource má konstruktory, které přijímají parametr TaskCreationOptions, které ovládají podkladovou úlohu a konstruktory, které přijímají stav objektu, který je uložen v úloze.  Náhodné předání typ TaskContinuationOptions namísto parametr TaskCreationOptions způsobí, že volání zpracuje možnosti jako stav. |
| CA5122 | [Deklarace CA5122 P/Invoke by neměly být bezpečné kritické](../code-quality/ca5122.md) | Metody jsou při provádění operace citlivé na zabezpečení označeny jako SecuritySafeCritical, ale lze je také bezpečně použít transparentním kódem. Transparentní kód nesmí nikdy přímo volat nativní kód prostřednictvím P/Invoke. Proto označení P/Invoke jako bezpečně kritické z hlediska zabezpečení neumožní transparentnímu kódu vyvolat je a je zavádějící pro analýzu zabezpečení. |
| CA5359 | [CA5359 Nezakázat ověřování certifikátu](../code-quality/ca5359.md) | Certifikát může pomáhat ověřit identitu serveru. Klienti by měli ověřit certifikát serveru, aby se zajistilo, že se požadavky odesílají na určený server. Pokud se ServerCertificateValidationCallback vždycky vrátí `true` , certifikát se předá ověření. |
| CA5360 | [CA5360 nevolá nebezpečné metody v deserializaci.](../code-quality/ca5360.md) | Nezabezpečená deserializace je ohrožení zabezpečení, ke kterému dochází, pokud se nedůvěryhodná data používají k zneužití logiky aplikace, což způsobuje útok DoS (Denial of Service), nebo dokonce spouštějí libovolný kód, který je deserializován. Je často možné, že uživatelé se zlými úmysly můžou tyto funkce deserializace zneužít, když aplikace deserializace nedůvěryhodných dat, která jsou pod jejich ovládacími prvky. Konkrétně volejte nebezpečné metody v procesu deserializace. Nezabezpečené útoky na deserializaci by mohly útočníkovi umožnit provést útoky, jako jsou útoky DoS, obcházení ověřování a vzdálené spuštění kódu. |
| CA5362 | [CA5362 potenciální cyklus odkazů v deserializovaném grafu objektů](../code-quality/ca5362.md) | Pokud dojde k deserializaci nedůvěryhodných dat, pak jakékoli zpracování deserializovaného objektu graf musí zpracovávat cykly odkazů, aniž by se museli přecházet do nekonečné smyčky. To zahrnuje kód, který je součástí zpětného volání deserializace, a kódu, který zpracovává graf objektu po deserializaci dokončeno. V opačném případě by útočník mohl provést útok DOS se škodlivými daty obsahujícími cyklický odkaz. |
| CA5365 | [CA5365 Nezakázat kontrolu hlaviček protokolu HTTP](../code-quality/ca5365.md) | Kontrola hlaviček protokolu HTTP umožňuje kódování návratových znaků a znaků nového řádku, \r a \n, které se nacházejí v hlavičkách odpovědí. Toto kódování může pomáhat zabránit útokům prostřednictvím injektáže, které využívají aplikaci, která vrací nedůvěryhodná data obsažená v hlavičce. |
| CA5366 | [CA5366 použít XmlReader pro čtení XML pro datovou sadu](../code-quality/ca5366.md) | Použití <xref:System.Data.DataSet> metody ke čtení XML s nedůvěryhodnými daty může načítat nebezpečné externí odkazy, které by měly být omezeny pomocí <xref:System.Xml.XmlReader> zabezpečeného překladače nebo se zakázaným zpracováním DTD. |
| CA5367 | [CA5367 neserializovat typy s poli ukazatelů](../code-quality/ca5367.md) | Toto pravidlo kontroluje, zda existuje serializovatelný třída s polem nebo vlastností s ukazatelem. Členy, které nemohou být serializovány, mohou být ukazatel, jako jsou například statické členy nebo pole s označením <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 sada ViewStateUserKey pro třídy odvozené ze stránky](../code-quality/ca5368.md) | Nastavení <xref:System.Web.UI.Page.ViewStateUserKey> vlastnosti vám může pomáhat zabránit útokům na aplikaci tím, že vám umožní přiřadit identifikátor k proměnné stavu zobrazení pro jednotlivé uživatele, aby útočníci nemohli použít tuto proměnnou k vygenerování útoku. V opačném případě dojde k ohrožení zabezpečení pro padělání požadavků mezi weby. |
| CA5374 | [CA5374 nepoužívá XslTransform](../code-quality/ca5374.md) | Toto pravidlo zkontroluje, zda <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> je v kódu vytvořena instance. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>je teď zastaralá a neměla by se používat. |
| CA5375 | [CA5375 nepoužívat sdílený přístupový podpis účtu](../code-quality/ca5375.md) | Podpis SAS účtu může delegovat přístup k operacím čtení, zápisu a odstraňování na kontejnerech objektů blob, tabulkách, frontách a sdíleným složkám, které nejsou u SAS služby povoleny. Nepodporuje ale zásady na úrovni kontejneru a má méně flexibilitu a kontrolu nad oprávněními, která jsou udělena. Jakmile je uživatelé se zlými úmysly obdrží, váš účet úložiště bude snadno ohrožen. |
| CA5376 | [CA5376 použít SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS je citlivá data, která se nedají přenést do prostého textu v HTTP. |
| CA5377 | [CA5377 použít zásady přístupu na úrovni kontejneru](../code-quality/ca5377.md) | Zásady přístupu na úrovni kontejneru můžete kdykoli upravit nebo odvolat. Poskytuje větší flexibilitu a kontrolu nad oprávněními, která jsou udělena. |
| CA5379 | [CA5379 nepoužívá slabší algoritmus funkce odvození klíče.](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>Třída standardně používá <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algoritmus. Je nutné zadat algoritmus hash pro použití v některých přetíženích konstruktoru s <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> nebo vyšším. Poznámka: <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> vlastnost má pouze `get` přistupující objekt a nemá `overriden` modifikátor. |
| CA5382 | [CA5382 použít zabezpečené soubory cookie v ASP.NET Core](../code-quality/ca5382.md) | Aplikace dostupné přes HTTPS musí používat zabezpečené soubory cookie, které označují prohlížeči, že by se měl soubor cookie přenést jenom pomocí SSL (Secure Sockets Layer) (SSL). |
| CA5383 | [CA5383 zajistěte, aby v ASP.NET Core používali zabezpečené soubory cookie](../code-quality/ca5383.md) | Aplikace dostupné přes HTTPS musí používat zabezpečené soubory cookie, které označují prohlížeči, že by se měl soubor cookie přenést jenom pomocí SSL (Secure Sockets Layer) (SSL). |
| CA5384 | [CA5384 nepoužívat algoritmus DSA (Digital Signature Algorithm)](../code-quality/ca5384.md) | DSA je slabý asymetrický šifrovací algoritmus. |
| CA5385 | [CA5385 použít algoritmus Rivest – Shamir – Adleman (RSA) s dostatkem velikosti klíče](../code-quality/ca5385.md) | Klíč RSA menší než 2048 bitů je zranitelnější vůči útokům hrubou silou. |
| CA5387 | [CA5387 nepoužívá slabé funkce odvození klíče s nedostatečným počtem iterací.](../code-quality/ca5387.md) | Toto pravidlo kontroluje, zda byl kryptografický klíč generován pomocí <xref:System.Security.Cryptography.Rfc2898DeriveBytes> počtu iterací menšího než 100 000. Vyšší počet iterací může přispět ke zmírnění útoků pomocí slovníků, které se pokoušejí odhadnout vygenerovaný kryptografický klíč. |
| CA5388 | [CA5388 zajistit dostatečný počet iterací při použití slabé funkce odvození klíče](../code-quality/ca5388.md) | Toto pravidlo kontroluje, zda byl kryptografický klíč generován pomocí <xref:System.Security.Cryptography.Rfc2898DeriveBytes> počtu iterací, který může být menší než 100 000. Vyšší počet iterací může přispět ke zmírnění útoků pomocí slovníků, které se pokoušejí odhadnout vygenerovaný kryptografický klíč. |
| CA5390 | [CA5390 šifrovací klíč na pevný kód](../code-quality/ca5390.md) | Aby byl symetrický algoritmus úspěšný, tajný klíč musí být známý pouze pro odesílatele a příjemce. Když je klíč pevně kódovaný, je snadno zjištěn. Dokonce i u kompilovaných binárních souborů je můžete snadno extrahovat i uživatelům se zlými úmysly. Po ohrožení bezpečnosti privátního klíče může být zašifrovaný text přímo dešifrován a již není chráněn. |
| CA5391 | [CA5391 používat tokeny proti padělání v ASP.NET Core řadičích MVC](../code-quality/ca5391.md) | Zpracování `POST` požadavku, `PUT` , `PATCH` nebo `DELETE` bez ověření tokenu antipadělání může být zranitelné vůči útokům proti falšování požadavků mezi weby. Útok proti padělání žádostí mezi servery může odesílat škodlivé požadavky od ověřeného uživatele do vašeho kontroleru ASP.NET Core MVC. |
| CA5392 | [CA5392 použít atribut DefaultDllImportSearchPaths pro volání nespravovaného volání](../code-quality/ca5392.md) | Ve výchozím nastavení funkce volání nespravovaného <xref:System.Runtime.InteropServices.DllImportAttribute> testu využívají v testu počet adresářů, včetně aktuálního pracovního adresáře, který má knihovna načíst. Může se jednat o problémy zabezpečení pro určité aplikace, což vede ke zneužití knihovny DLL. |
| CA5393 | [CA5393 nepoužívá nebezpečnou DllImportSearchPath hodnotu](../code-quality/ca5393.md) | V adresářích pro hledání výchozích knihoven DLL a v adresářích sestavení může být škodlivá knihovna DLL. Nebo, v závislosti na tom, kde je aplikace spuštěná, může být v adresáři aplikace škodlivá knihovna DLL. |
| CA5394 | [CA5394 nepoužívat nezabezpečenou náhodnost](../code-quality/ca5394.md) | Použití kryptograficky slabé generátory náhodných čísel může útočníkovi umožnit předpovědět, jaká hodnota citlivá na zabezpečení bude vygenerována. |
| CA5395 | [CA5395 neúspěšných hodnotu httpVerb atributů pro metody akce](../code-quality/ca5395.md) | Všechny metody akcí, které vytvoří, upraví, odstraní nebo jinak upravují data, musí být chráněny pomocí atributu ochrany proti padělání žádostí mezi lokalitami. Operace GET by měla být bezpečná operace, která nemá žádné vedlejší účinky a neupravuje vaše trvalá data. |
| CA5396 | [CA5396 nastavit HttpOnly na true pro HttpCookie](../code-quality/ca5396.md) | V rámci hloubkové míry ochrany zajistěte, aby se soubory cookie protokolu HTTP citlivé na zabezpečení označily jako HttpOnly. To znamená, že by webový prohlížeč měl zakázat skriptům přístup k souborům cookie. Vložené škodlivé skripty představují společný způsob, jak ukrást soubory cookie. |
| CA5399 | [CA5399 jednoznačně zakázat kontrolu seznamu odvolaných certifikátů HttpClient](../code-quality/ca5399.md) | Odvolaný certifikát už není důvěryhodný. Může je použít útočníky, kteří předávají některá škodlivá data nebo ukrást citlivá data v komunikaci přes protokol HTTPS. |
| CA5400 | [CA5400 zajistěte, aby kontrola seznamu odvolaných certifikátů HttpClient není zakázaná](../code-quality/ca5400.md) | Odvolaný certifikát už není důvěryhodný. Může je použít útočníky, kteří předávají některá škodlivá data nebo ukrást citlivá data v komunikaci přes protokol HTTPS. |
| CA5401 | [CA5401 nepoužívá CreateEncryptor s jiným než výchozím IV](../code-quality/ca5401.md) | Symetrické šifrování by mělo vždy používat neopakovaný inicializační vektor, aby se zabránilo útokům na slovník. |
| CA5402 | [CA5402 použít CreateEncryptor s výchozí IV](../code-quality/ca5402.md) | Symetrické šifrování by mělo vždy používat neopakovaný inicializační vektor, aby se zabránilo útokům na slovník. |
