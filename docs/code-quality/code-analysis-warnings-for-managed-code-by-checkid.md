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
- CA1068
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6ac6fccb69770c003f21875e5ab3809c2d6415b4
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305877"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Upozornění analýzy kódu pro spravovaný kód podle CheckId

Následující tabulka obsahuje seznam upozornění analýzy kódu pro spravovaný kód podle identifikátoru upozornění CheckId.

| CheckId | Upozornění | Popis |
|---------| - | - |
| CA1000 | [CA1000: Nedeklarujte statické členy v obecných typech @ no__t-0 | Při volání statického členu obecného typu musí být pro tento typ zadán argument typu. Je-li zavolán obecný člen instance, který nepodporuje odvozování, musí být pro tento člen zadán argument typu. V těchto dvou případech je syntaxe zadávání argumentu typu různá a snadno zaměnitelná. |
| CA1001 | [CA1001: Typy, které vlastní pole na jedno použití, by měly být na jedno použití @ no__t-0 | Třída deklaruje a implementuje pole instance typu System.IDisposable, přičemž neimplementuje rozhraní IDisposable. Třída, která deklaruje pole IDisposable nepřímo, vlastní nespravovaný zdroj a měla by rozhraní IDisposable implementovat. |
| CA1002 | @NO__T – 0CA1002: Nezveřejňujte obecné seznamy @ no__t-0 | Třída System.Collections.Generic.List < (ze \<(T >) >) je obecná kolekce navržená pro výkon, nikoli dědičnost. Proto třída List neobsahuje žádné virtuální členy. Místo ní by měly být vystaveny kolekce navržené pro dědičnost. |
| CA1003 | [CA1003: Použijte instance obecných obslužných rutin událostí @ no__t-0 |Typ obsahuje delegát vracející hodnotu void, jehož předpis obsahuje dva parametry (první je objekt a druhý typ přiřaditelný do typu EventArgs), a příslušné sestavení zacíleno na rozhraní Microsoft .NET Framework 2.0. |
| CA1004 | [CA1004: Obecné metody by měly poskytnout parametr typu @ no__t-0 | Argument typu obecné metody je z argumentu typu předávaného metodě odvozen namísto explicitního určení argumentu typu. Má-li být odvozování povoleno, musí předpis parametrů obecné metody zahrnovat parametr stejného typu jako parametr typu metody. V tomto případě nemusí být argument typu zadán. Používáte-li odvození pro všechny parametry typu, je syntaxe volání obecných a neobecných metod instancí identická, což zjednodušuje použití obecných metod. |
| CA1005 | [CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů @ no__t-0 | Čím více parametrů typu obecný typ obsahuje, tím obtížnější je vědět a zapamatovat si, co každý z parametrů typu představuje. To je obvykle zřejmé s jedním parametrem typu, stejně jako v seznamu\<T > a v některých případech se dvěma parametry typu, například u třídy Dictionary\<TKey, TValue >. Pokud však existují více než dva parametry typu, stává se pro většinu uživatelů použití příliš obtížným. |
| CA1006 | @NO__T – 0CA1006: Nevnořovat obecné typy v podpisech členů @ no__t-0 | Vnořený typ argumentu je typ argumentu, který je také obecným typem. Chce-li uživatel zavolat člen, jehož předpis obsahuje vnořený argument typu, musí nejprve vytvořit instanci jednoho obecného typu a předat tento typ konstruktoru druhého obecného typu. Potřebná procedura a syntaxe je složitá a je vhodné se jí vyhnout. |
| CA1007 |[CA1007: Použijte obecné typy, kde je to vhodné @ no__t-0 | Externě viditelná metoda obsahuje referenční parametr typu System.Object. Použitím obecných metod lze metodě předávat všechny typy (s určitými omezeními) bez předchozího přetypování typu na referenční typ parametru. |
| CA1008 | @NO__T – 0CA1008: Výčty by měly mít nulovou hodnotu @ no__t-0. | Výchozí hodnota neinicializovaného výčtu je stejně jako u jiných typů hodnot nula. Atributovaný výčet bez příznaků by měl definovat člen za použití hodnoty nula tak, aby výchozí hodnota byla platnou hodnotou výčtu. Definuje-li výčet, který má aplikován atribut FlagsAttribute, člen s hodnotou nula, měl by jeho název být „None“, aby tak označoval, že ve výčtu nebyly nastaveny žádné hodnoty. |
| CA1009 | [CA1009: Deklarace obslužných rutin událostí správně @ no__t-0 | Metody zpracování událostí přebírají dva parametry. První je typu System.Object a je pojmenován „sender“. Je jím objekt, který vyvolal událost. Druhý parametr je typu System.EventArgs a je pojmenován „e“. Představuje data přidružená k události. Metody zpracování událostí by neměly vracet hodnotu; v programovacím jazyce C# je toto označeno návratovým typem void. |
| CA1010 | [CA1010: Kolekce by měly implementovat obecné rozhraní @ no__t-0 | Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Pak lze tuto kolekci použít k zaplnění typů obecných kolekcí. |
| CA1011 |[CA1011: Zvažte předání základních typů jako parametrů @ no__t-0 | Je-li v deklaraci metody zadán jako parametr základní typ, lze jako příslušný argument k metodě předat kterýkoliv typ odvozený z tohoto základního typu. Pokud není dodatečná funkčnost poskytovaná odvozeným typem parametru vyžadována, umožňuje použití základního typu širší využití metody. |
| CA1012 | [CA1012: Abstraktní typy by neměly mít konstruktory @ no__t-0 | Konstruktory abstraktních typů mohou být volány pouze odvozenými typy. Jelikož veřejné konstruktory vytvářejí instance typu, přičemž nelze vytvořit instance abstraktního typu, je abstraktní typ obsahující veřejný konstruktor nesprávně navržen. |
| CA1013 | [CA1013: Operátor přetížení se rovná přetěžování při přetížení přidat a odečíst @ no__t-0. | Veřejný nebo chráněný typ implementuje operátory sčítání a odčítání, aniž by implementoval operátor rovnosti. |
| CA1014 | [CA1014: Označte sestavení pomocí CLSCompliantAttribute @ no__t-0. | Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh přikazuje, aby všechna sestavení explicitně uvedla dodržování specifikace CLS pomocí <xref:System.CLSCompliantAttribute> . Není-li tento atribut v sestavení přítomen, nedodržuje sestavení specifikaci. |
| CA1016 | [CA1016: Označte sestavení pomocí AssemblyVersionAttribute @ no__t-0. | Rozhraní .NET používá číslo verze k jednoznačné identifikaci sestavení a k vytvoření vazby na typy v silně pojmenovaných sestaveních. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny. |
| CA1017 | [CA1017: Označte sestavení pomocí ComVisibleAttribute @ no__t-0. |Atribut ComVisibleAttribute určuje způsob přístupu klientů COM ke spravovanému kódu. Dobrý návrh přikazuje, aby sestavení explicitně uvedla viditelnost modelu COM. Viditelnost modelu COM může být nastavena pro celé sestavení a poté přepsána pro jednotlivé typy a členy typů. Není-li tento atribut přítomen, je obsah sestavení viditelný klientům COM. |
| CA1018 | [CA1018: Označte atributy pomocí AttributeUsageAttribute @ no__t-0 | Při definování vlastního atributu jej označte použitím atributu AttributeUsageAttribute, čímž je určeno, kde ve zdrojovém kódu může být vlastní atribut použit. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. |
| CA1019 | [CA1019: Definovat přístupové objekty pro argumenty atributu @ no__t-0 | Atributy mohou definovat povinné argumenty, které musí být specifikovány při použití atributu na cíl. Říká se jim také poziční argumenty, jelikož jsou konstruktorům atributů předány jako poziční parametry. Pro každý povinný argument by měl atribut navíc poskytovat odpovídající vlastnost jen pro čtení, aby mohla být hodnota argumentu během spuštění získána. Atributy mohou také definovat volitelné argumenty, které jsou rovněž známy jako pojmenované argumenty. Tyto argumenty jsou podle názvu poskytovány konstruktorům atributů a měly by mít odpovídající vlastnost pro čtení i zápis. |
| CA1020 | [CA1020: Vyhněte se oborům názvů s malým počtem typů @ no__t-0 | Ujistěte se, že všechny obory názvů mají logické uspořádání a že je vložení typů do řídce zaplněných oborů názvů odůvodněné. |
| CA1021 | [CA1021: Vyhněte se parametrům @ no__t-0 | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů, a schopnost práce s metodami vracejícími více návratových typů. Také rozdíl mezi parametry „out“ a „ref“ není běžně chápán. |
| CA1023 | [CA1023: Indexery by neměly být multidimenzionální @ no__t-0 | Indexery (tj. indexované vlastnosti) by měly používat jediný index. Vícerozměrné indexery mohou výrazně snížit použitelnost knihovny. |
| CA1024 | [CA1024: Použijte vlastnosti, kde je to vhodné @ no__t-0. | Veřejná nebo chráněná metoda má název začínající na „Get“, nepřijímá žádné parametry a vrací hodnotu, která není polem. Metoda může být dobrým kandidátem, aby se stala vlastností. |
| CA1025 | [CA1025: Nahraďte opakované argumenty polem param @ no__t-0. | Není-li znám přesný počet argumentů a jsou-li proměnné argumenty stejného typu (nebo je lze předat jako stejný typ), použijte namísto opakovaných argumentů pole parametrů. |
| CA1026 | [CA1026: Výchozí parametry by neměly být použity @ no__t-0 | Ve specifikaci CLS jsou povoleny metody používající výchozí parametry, avšak specifikace CLS umožňuje kompilátorům ignorovat hodnoty přiřazené těmto parametrům. Chcete-li zachovat shodné chování napříč programovacími jazyky, měly by být metody používající výchozí parametry nahrazeny přetíženími metody, která výchozí parametry poskytují. |
| CA1027 |[CA1027: Označte výčty pomocí FlagsAttribute @ no__t-0. | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Mohou-li být pojmenované konstanty smysluplně kombinovány, použijte ve výčtu atribut FlagsAttribute. |
| CA1028 | [CA1028: Úložiště výčtu by mělo být Int32 @ no__t-0 | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Ve výchozím nastavení je pro uložení konstantní hodnoty použit datový typ System.Int32. Přestože lze tento typ změnit, není to ve většině případů zapotřebí ani doporučováno. |
| CA1030 | [CA1030: Použijte události, kde je to vhodné @ no__t-0. |Toto pravidlo zjišťuje metody, které mají názvy obvykle používané pro události. Je-li metoda volána jako odpověď na jednoznačně definovanou změnu stavu, měla by být metoda volána obslužnou rutinou události. Objekty volající tuto metodu by měly místo přímého volání metody vyvolat událost. |
| CA1031 | [CA1031: Nezachycovat obecné typy výjimek @ no__t-0 | Obecné výjimky by neměly být zachycovány. Zachyťte více specifickou výjimku nebo jako poslední příkaz v zachytávacím bloku opětovně vyvolejte obecnou výjimku. |
| CA1032 |[CA1032: Implementujte standardní konstruktory výjimky @ no__t-0 | Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. |
| CA1033 | [CA1033: Metody rozhraní by měly být volatelné podřízenými typy @ no__t-0 | Nezapečetěný externě viditelný typ poskytuje explicitní implementaci metod veřejného rozhraní a neposkytuje alternativní externě viditelnou metodu stejného názvu. |
| CA1034 | [CA1034: Vnořené typy by neměly být viditelné @ no__t-0 | Vnořený typ je typ deklarovaný v rámci jiného typu. Vnořené typy jsou užitečné pro zapouzdření soukromých podrobností implementace v daném typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné. |
| CA1035 | [CA1035: Implementace rozhraní ICollection mají členy silného typu @ no__t-0. | Toto pravidlo vyžaduje, aby implementace rozhraní ICollection poskytovaly členy se silnými typy, aby uživatelé nemuseli při využívání funkčnosti poskytované rozhraním přetypovávat argumenty na typ Object. Toto pravidlo předpokládá, že typ implementuje rozhraní ICollection proto, aby mohl spravovat kolekci instancí typu silnějšího než Object. |
| CA1036 | [CA1036: Přepsat metody na srovnatelných typech @ no__t-0 |Veřejný nebo chráněný typ implementuje rozhraní System.IComparable. Nepřepisuje metodu Object.Equals ani nepřetěžuje operátory rovnosti, nerovnosti, menší než a větší než specifické pro daný jazyk. |
| CA1038 | [CA1038: Enumerátory by měly být silného typu @ no__t-0 | Toto pravidlo vyžaduje, aby implementace rozhraní IEnumerator také poskytovaly verze vlastnosti Current se silnými typy, aby uživatelé nemuseli při použití funkčnosti poskytované tímto rozhraním přetypovávat návratovou hodnotu na silný typ. |
| CA1039 | [CA1039: Seznamy jsou silného typu @ no__t-0. | Toto pravidlo vyžaduje, aby implementace rozhraní IList poskytovaly členy se silnými typy, aby uživatelé nemuseli při využívání funkčnosti poskytované rozhraním přetypovávat argumenty na typ System.Object. |
| CA1040 |[CA1040: Vyhněte se prázdným rozhraním @ no__t-0 | Rozhraní definují členy ujednávající jejich chování nebo užití. Funkčnost popsaná rozhraním může být osvojena libovolným typem bez ohledu na to, kde se typ vyskytuje v hierarchii dědičnosti. Typ implementuje rozhraní tím, že poskytuje implementace jeho členů. Prázdné rozhraní nedefinuje žádné členy, tudíž ani nedefinuje žádná implementovatelná ujednání. |
| CA1041 | [CA1041: Zadejte ObsoleteAttribute zprávu @ no__t-0. | Typ nebo člen je označen atributem System.ObsoleteAttribute, aniž by měl zadánu vlastnost ObsoleteAttribute.Message. Při kompilaci typu nebo členu označeného atributem ObsoleteAttribute je zobrazena vlastnost zprávy tohoto atributu. To uživateli poskytuje informace o zastaralém typu nebo členu. |
| CA1043 | [CA1043: Použít celočíselný nebo řetězcový argument pro indexery @ no__t-0 | Indexery (tj. indexované vlastnosti) by měly jako index používat celočíselné typy nebo typy řetězců. Tyto typy se obvykle používají pro indexování datových struktur a zvyšují použitelnost knihovny. Použití typu Object by mělo být omezeno na ty případy, kdy během návrhu není možné určit konkrétní celočíselný nebo řetězcový typ. |
| CA1044 | [CA1044: Vlastnosti by neměly být pouze pro zápis @ no__t-0. | Ačkoli je přijatelné a často nezbytné použít vlastnost jen pro čtení, směrnice návrhu zakazují použití vlastností jen pro zápis. Důvodem je skutečnost, že umožnit uživateli nastavit hodnotu a poté uživateli zabránit v zobrazení této hodnoty není bezpečné. Taktéž bez přístupu pro čtení není možné zobrazit stav sdílených objektů, což omezuje jejich užitečnost. |
| CA1045 |[CA1045: Nepředávejte typy odkazem @ no__t-0 | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů a schopnost práce s metodami vracejícími více návratových typů. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat, že uživatelé budou hlavní pracovat s parametry `out` nebo `ref`. |
| CA1046 | [CA1046: Nepřetížit operátor rovnosti na odkazových typech @ no__t-0 | U referenčních typů je výchozí implementace operátoru rovnosti téměř vždy správná. Ve výchozím nastavení jsou dva odkazy rovny, pouze pokud ukazují na stejný objekt. |
| CA1047 |[CA1047: Nedeklarujte chráněné členy v zapečetěných typech @ no__t-0 | Typy deklarují chráněné členy, aby k nim odvozené typy mohly přistupovat nebo je přepisovat. Dle definice nelze dědit zapečetěné typy, což znamená, že nelze volat chráněné metody zapečetěných typů. |
| CA1048 | [CA1048: Nedeklarujte virtuální členy v zapečetěných typech @ no__t-0 | Typy deklarují metody jako virtuální, aby odvozující typy mohly přepsat implementaci virtuální metody. Dle definice nelze zdědit zapečetěný typ. Díky tomu postrádá virtuální metoda u zapečetěného typu význam. |
| CA1049 | [CA1049: Typy, které vlastní nativní prostředky by měly být na jedno použití @ no__t-0 | Typy, které přidělují nespravované prostředky, by měly implementovat rozhraní IDisposable a umožnit tak volajícím uvolnit tyto prostředky na požádání a zkrátit životní cyklus objektů, které je využívají. |
| CA1050 | [CA1050: Deklarace typů v oborech názvů @ no__t-0 | Typy jsou deklarovány v oborech názvů, aby bylo zabráněno kolizím názvů a zároveň jako způsob organizace souvisejících typů v hierarchii objektů. |
| CA1051 | [CA1051: Nedeklarujte viditelná pole instance @ no__t-0 | Hlavní použití pole by mělo být jako podrobnost implementace. Pole by měla být soukromá nebo vnitřní a měla by být vystavena s použitím vlastností. |
| CA1052 | [CA1052: Statické typy držitelů by měly být zapečetěné @ no__t-0 | Veřejný nebo chráněný typ obsahuje pouze statické členy a není deklarován s použitím zapečetěného modifikátoru (NotInheritable) (jazyk C#). Typu, u nějž není zamýšleno dědění, by mělo být prostřednictvím označením zapečetěným modifikátorem zabráněno, aby byl použit jako základní typ. |
| CA1053 |[CA1053: Typy statických držitelů by neměly mít konstruktory @ no__t-0. | Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má veřejný nebo chráněný výchozí konstruktor. Konstruktor není nutný, protože volání statických členů nevyžaduje instanci typu. Z důvodu bezpečnosti a zabezpečení by řetězcová přetížení měla volat přetížení identifikátoru URI použitím argumentu řetězce. |
| CA1054 | [CA1054: Parametry identifikátoru URI by neměly být řetězce @ no__t-0. | Pakliže metoda přijímá řetězcovou reprezentaci identifikátoru URI, mělo by být poskytnuto odpovídající přetížení přijímající instanci třídy URI, která tyto služby poskytuje bezpečným a zabezpečeným způsobem. |
| CA1055 | [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce @ no__t-0 | Toto pravidlo předpokládá, že metoda vrací identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1056 | [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce @ no__t-0. | Toto pravidlo předpokládá, že vlastnost reprezentuje identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1057 | [CA1057: Přetížení řetězce identifikátoru URI volají přetížení System. URI @ no__t-0 | Typ deklaruje přetížení metod, které se liší pouze nahrazením řetězcového parametru parametrem System.Uri. Přetížení přijímající řetězcový parametr nevolá přetížení, které přijímá parametr URI. |
| CA1058 | [CA1058: Typy by neměly rozkrývat určité základní typy @ no__t-0. | Externě viditelný typ rozšiřuje určité základní typy. Použijte jednu z alternativ. |
| CA1059 |[CA1059: Členové by neměli zveřejňovat určité konkrétní typy @ no__t-0 | Konkrétní typ je typ, který je zcela implementován, a lze tudíž vytvořit jeho instanci. Chcete-li umožnit široké využití členu, nahraďte konkrétní typ použitím navrhovaného rozhraní. |
| CA1060 | [CA1060: Přesunout volání nespravovaného volání do třídy NativeMethods @ no__t-0 | Metody vyvolání platformy, jako jsou ty, které jsou označeny pomocí atributu System.Runtime.InteropServices.DllImportAttribute, nebo metody, které jsou definovány pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], přístup k nespravovanému kódu. Tyto metody by měly patřit třídě NativeMethods, SafeNativeMethods nebo UnsafeNativeMethods. |
| CA1061 |[CA1061: Neskrývat metody základní třídy @ no__t-0 | Metoda základního typu je skryta identicky pojmenovanou metodou v odvozeném typu, kde je předpis parametrů odvozené metody odlišný od odpovídajících typů v předpisu parametrů základní metody pouze ve slaběji odvozených typech. |
| CA1062 | [CA1062: Ověřit argumenty veřejných metod @ no__t-0 | Všechny argumenty odkazu předané externě viditelným metodám by měly být porovnány s hodnotou NULL. |
| CA1063 | [CA1063: Implementace IDisposable správně @ no__t-0 | Všechny typy IDisposable by měly správně implementovat vzor Dispose. |
| CA1064 | [CA1064: Výjimky by měly být veřejné @ no__t-0 | Interní výjimka je viditelná pouze uvnitř svého vlastního vnitřního rozsahu. Jakmile výjimka přesáhne hranice vnitřního rozsahu, lze pro zachycení výjimky použít pouze základní výjimku. Pokud je vnitřní výjimka zděděna z <xref:System.Exception>, <xref:System.SystemException>, nebo <xref:System.ApplicationException>, externí kód nebude mít dostatečné informace o tom, co dělat, s výjimkou. |
| CA1065 | [CA1065: Nevyvolávání výjimek v neočekávaných umístěních @ no__t-0 | Metoda, u které není předpokládáno vyvolání výjimky, vyvolá výjimku. |
| CA1068 | @NO__T – 0CA1068: Parametry CancellationToken musí být poslední @ no__t-0. | Metoda má parametr CancellationToken, který není posledním parametrem. |
| CA1200 | @NO__T – 0CA1200: Nepoužívejte značky cref s předponou @ no__t-0. | Atribut [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Vyhněte se použití značek `cref` s předponami, protože brání kompilátoru v ověřování odkazů. Zároveň zabrání integrovanému vývojovému prostředí (IDE) sady Visual Studio najít a aktualizovat tyto odkazy na symboly během refaktoringu. |
| CA1300 | [CA1300: Zadejte MessageBoxOptions @ no__t-0 | Chcete-li správně zobrazit okno pro kultury, které používají směr čtení zprava doleva, musí být členy RightAlign a RtlReading výčtu MessageBoxOptions předány metodě Show. |
| CA1301 | [CA1301: Vyhněte se duplicitním akcelerátorům @ no__t-0 | Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Pokud má více ovládacích prvků duplicitní přístupové klíče, není chování přístupového klíče správně definované. |
| CA1302 | [CA1302: Nenekódujte pevně řetězce specifické pro národní prostředí @ no__t-0 | Výčet System.Environment.SpecialFolder obsahuje členy, které odkazují na speciální systémové složky. Umístění těchto složek mohou mít různé hodnoty v různých operačních systémech; uživatel může změnit některé z míst; a místa jsou lokalizována. Metoda Environment.GetFolderPath vrátí lokace, které jsou spojené s výčtem Environment.SpecialFolder, lokalizované a vhodné pro aktuálně spuštěný počítač. |
| CA1303 | [CA1303: Nepředávejte literály jako lokalizované parametry @ no__t-0 | Externě viditelná metoda předává řetězcový literál jako parametr konstruktoru nebo metodě .NET a tento řetězec by měl být Lokalizovatelný. |
| CA1304 | [CA1304: Zadejte CultureInfo @ no__t-0 | Metoda nebo konstruktor volá člen, který má přetížení přijímající parametr System.Globalization.CultureInfo, a tato metoda nebo konstruktor nevolá přetížení přebírající parametr CultureInfo. Pokud objekt CultureInfo nebo System.IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1305 | [CA1305: Zadejte IFormatProvider @ no__t-0 | Metoda nebo konstruktor volá jeden nebo více členů, které mají přetížení přijímající parametr System.IFormatProvider, a tato metoda nebo konstruktor nevolá přetížení, která přebírá parametr IFormatProvider. Pokud objekt System.Globalization.CultureInfo nebo IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1306 | [CA1306: Nastavení národního prostředí pro datové typy @ no__t-0 | Národní prostředí určuje prvky prezentace specifické kultury pro data, například formátování použité pro číselné hodnoty, symboly měny a pořadí řazení. Při vytváření objektu DataSet nebo DataTable byste měli explicitně nastavit národní prostředí. |
| CA1307 | [CA1307: Zadejte StringComparison @ no__t-0 | Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison. |
| CA1308 |[CA1308: Normalizujte řetězce na velká písmena @ no__t-0 | Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků nedokáže po převodu na malá písmena provést zpáteční cestu. |
| CA1309 | [CA1309: Použít ordinální StringComparison @ no__t-0 | Nelingvistická operace porovnání řetězců nemá nastaven parametr StringComparison na hodnotu Ordinal ani na hodnotu OrdinalIgnoreCase. Explicitním nastavením parametru na hodnotu StringComparison.Ordinal nebo StringComparison.OrdinalIgnoreCase dojde ke zrychlení kódu a zvýšení přesnosti a spolehlivosti. |
| CA1400 | [CA1400: Vstupní body volání nespravovaného volání by měly existovat v @ no__t-0 |Veřejná nebo chráněná metoda je označena pomocí atributu System.Runtime.InteropServices.DllImportAttribute. Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně. |
| CA1401 | [CA1401: Volání nespravovaných kódů by neměla být viditelná @ no__t-0 | Veřejná nebo chráněná metoda veřejného typu má nastaven atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tyto metody by neměly být vystaveny. |
| CA1402 |[CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM @ no__t-0 | Když jsou přetížené metody vystaveny klientům modulu COM, zachová svůj název pouze první přetížení metody. Následná přetížení jsou jednoznačně přejmenována přidáním podtržítka (_) a celého čísla odpovídajícího pořadí deklarace tohoto přetížení. |
| CA1403 | [CA1403: Typy automatického rozložení by neměly být viditelné modelu COM @ no__t-0 | Hodnotový typ viditelný modulem COM je označen pomocí atributu System.Runtime.InteropServices.StructLayoutAttribute, nastaveného na hodnotu LayoutKind.Auto. Rozložení těchto typů se může změnit mezi verzemi rozhraní .NET, čímž dojde k přerušení klientů modelu COM, kteří očekávají určité rozložení. |
| CA1404 | [CA1404: Zavolat GetLastError hned po volání nespravovaného volání @ no__t-0 | Je provedeno volání metody Marshal.GetLastWin32Error nebo ekvivalentní [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] Funkce GetLastError a bezprostředně předchozí volání není pro operační systém volání metody. |
| CA1405 | [CA1405: Základní typy viditelného typu modelu COM by měly být viditelné modelu COM @ no__t-0 | Typ viditelný modulem COM je odvozen od typu, který není viditelný modulem COM. |
| CA1406 |[CA1406: Vyhněte se argumentům Int64 pro Visual Basic 6 klientů @ no__t-0 | Klienty modulu COM jazyka Visual Basic 6 nemohou přistupovat k 64bitová celá čísla. |
| CA1407 |[CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM @ no__t-0 | Modul COM nepodporuje statické metody. |
| CA1408 | [CA1408: Nepoužívejte AutoDual ClassInterfaceType @ no__t-0 | Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Pokud ve výchozím nastavení není zadán atribut ClassInterfaceAttribute, použije se pouze rozhraní určené pro odesílání. |
| CA1409 | [CA1409: Viditelné typy modelu COM by měly být vytvořitelné @ no__t-0 |Odkazový typ, který je označen jako viditelný modulům COM, obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů). Typ bez veřejného výchozího konstruktoru není možné vytvořit klienty typu COM. |
| CA1410 | [CA1410: Metody registrace modelu COM by se měly shodovat s @ no__t-0 | Typ deklaruje metodu, která je označena atributem System.Runtime.InteropServices.ComRegisterFunctionAttribute, ale nedeklaruje metodu označenou pomocí atributu System.Runtime.InteropServices.ComUnregisterFunctionAttribute, a naopak. |
| CA1411 | [CA1411: Metody registrace modelu COM by neměly být viditelné @ no__t-0 | Metoda označená pomocí atributu System.Runtime.InteropServices.ComRegisterFunctionAttribute nebo atributu System.Runtime.InteropServices.ComUnregisterFunctionAttribute je externě viditelná. |
| CA1412 | [CA1412: Označte rozhraní ComSource jako IDispatch @ no__t-0. | Typ je označen atributem System.Runtime.InteropServices.ComSourceInterfacesAttribute a alespoň jedno ze zadaných rozhraní není označeno pomocí atributu System.Runtime.InteropServices.InterfaceTypeAttribute nastaveného na hodnotu ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Vyhněte se neveřejným polím v viditelných typech hodnot typu COM @ no__t-0 | Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Zkontrolujte obsah polí, zda neobsahují informace, které by neměly být vystaveny nebo které budou mít nežádoucí účinky na návrh nebo zabezpečení. |
| CA1414 | [CA1414: Označte logické argumenty volání nespravovaného znaménka @ no__t-0. | Datový typ Boolean má v nespravovaném kódu různé reprezentace. |
| CA1415 | [CA1415: Deklarujte správně volání nespravovaného volání @ no__t-0 | Toto pravidlo vyhledá operační systém vyvolat deklarace metody, které se zaměřují [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] parametr struktury funkce, které mají ukazatel na OVERLAPPED a odpovídající spravovaný parametr není ukazatel System.Threading.NativeOverlapped. Struktura. |
| CA1500 | [CA1500: Názvy proměnných by neměly odpovídat názvům polí @ no__t-0 | Metoda instance deklaruje parametr nebo lokální proměnnou, jejichž název odpovídá poli instance deklarovaného typu, což vede k chybám. |
| CA1501 | [CA1501: Vyhněte se nadměrné dědičnosti @ no__t-0 | Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti. Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. |
| CA1502 | [CA1502: Vyhněte se nadměrné složitosti @ no__t-0 | Toto pravidlo měří počet lineárně nezávislých cest skrze metodu, což je určeno počtem a složitostí podmínkových větví. |
| CA1504 | [CA1504: Kontrola zavádějících názvů polí @ no__t-0 | Název pole instance začíná předponou "s_" a název statického pole (Shared v jazyce Visual Basic) začíná předponou "m_". |
| CA1505 | [CA1505: Vyhněte se neudržovatelnému kódu @ no__t-0 | Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti. Nízký index udržovatelnosti označuje, že typ nebo metodu je pravděpodobně obtížné udržovat a je vhodné ji znovu navrhnout. |
| CA1506 |[CA1506: Vyhněte se nadměrnému párování tříd @ no__t-0 | Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje. |
| CA1600 | [CA1600: Nepoužívejte prioritu nečinného procesu @ no__t-0 | Nenastavujte prioritu procesu na Neaktivní. Procesy, které mají nastaveny System.Diagnostics.ProcessPriorityClass.Idle, budou zaměstnávat procesor, pokud by jinak byl nečinný, a tím budou blokovat úsporný režim. |
| CA1601 | [CA1601: Nepoužívejte časovače, které zabraňují změnám stavu napájení @ no__t-0 | Vyšší frekvence periodické aktivity budou udržovat procesor zaneprázdněný a ovlivňovat časovače úspory energie nečinnosti, které vypnou zobrazení a pevné disky. |
| CA1700 | [CA1700: Nejmenujte hodnoty Enum ' rezervované ' ](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. |
| CA1701 | [CA1701: Složená slova řetězce prostředků by se měla použita správně @ no__t-0. | Každé slovo řetězce zdroje je rozděleno na tokeny na základě velikosti písmen. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla. |
| CA1702 | [CA1702: Složená slova by se měla použita správně @ no__t-0. | Název identifikátoru obsahuje více slov a alespoň jedno ze slov se zdá být složené slovo, které není správně formátováno. |
| CA1703 | [CA1703: Řetězce prostředků by měly být zadány správně @ no__t-0 | Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA1704 | [CA1704: Identifikátory by měly být zadány správně @ no__t-0 | Název externě viditelného identifikátoru obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA1707 | [CA1707: Identifikátory by neměly obsahovat podtržítka @ no__t-0. | Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry. |
| CA1708 | [CA1708: Identifikátory by se měly lišit o více než případu @ no__t-0. | Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena. |
| CA1709 | [CA1709: Identifikátory by se měly použita správně @ no__t-0. | Podle konvence používají názvy parametrů zápis typu CamelCase a názvy oborů názvů, typů a členů používají zápis typu PascalCase. |
| CA1710 | [CA1710: Identifikátory by měly mít správnou příponu @ no__t-0 |Podle konvence by měly názvy typů, které rozšiřují některé základní typy nebo určitá rozhraní, nebo typů odvozených z těchto typů mít příponu přidruženou těmto typům nebo rozhraním. |
| CA1711 | [CA1711: Identifikátory by neměly mít nesprávnou příponu @ no__t-0 | Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony. |
| CA1712 | [CA1712: Nepoužívejte předpony hodnot výčtu s názvem typu @ no__t-0 | Názvy členů výčtu nemají předponu názvu typu, protože se očekává, že vývojové nástroje poskytují informace o typu. |
| CA1713 | [CA1713: Události by neměly mít předponu před nebo po @ no__t-0. | Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí. |
| CA1714 | [CA1714: Výčty příznaků by měly mít plurální názvy @ no__t-0. | Veřejný výčet má atribut System.FlagsAttribute a jeho název nekončí písmenem „s“. Typy označené pomocí atributu FlagsAttribute mají názvy, které jsou v množném čísle, protože tento atribut označuje, že lze zadat více než jednu hodnotu. |
| CA1715 | [CA1715: Identifikátory by měly mít správnou předponu @ no__t-0 | Název externě viditelného rozhraní nezačíná velkým písmenem „I“. Název parametru obecného typu u externě viditelného typu nebo metody nezačíná velkým písmenem „T“. |
| CA1716 | [CA1716: Identifikátory by neměly odpovídat klíčovým slovům @ no__t-0. | Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime). |
| CA1717 | [CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle @ no__t-0. | Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu. |
| CA1719 | [CA1719: Názvy parametrů by neměly odpovídat názvům členů @ no__t-0 | Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam členu. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou. |
| CA1720 |[CA1720: Identifikátory by neměly obsahovat názvy typů @ no__t-0. | Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka. |
| CA1721 | [CA1721: Názvy vlastností by neměly odpovídat metodám Get @ no__t-0 |Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce. |
| CA1722 | [CA1722: Identifikátory by neměly mít nesprávnou předponu @ no__t-0. | Podle konvence mají pouze některé programovací prvky názvy začínající určitou předponou. |
| CA1724 | [CA1724: Názvy typů by neměly odpovídat oborům názvů @ no__t-0. | Názvy typů by neměly odpovídat názvům oborů názvů .NET. Porušení tohoto pravidla může snížit použitelnost knihovny. |
| CA1725 | [CA1725: Názvy parametrů by měly odpovídat základní deklaraci @ no__t-0 | Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody. |
| CA1726 | [CA1726: Použijte preferované výrazy @ no__t-0 | Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Název případně obsahuje také výraz „Flag“ nebo „Flags“. |
| CA1800 | [CA1800: Nepoužívejte bezpodmínečně @ no__t-0 | Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. |
| CA1801 | [CA1801: Zkontrolovat nepoužité parametry @ no__t-0 | Podpis metody obsahuje parametr, který není použit v těle metody. |
| CA1802 |[CA1802: Použijte literály, kde je to vhodné @ no__t-0 |Pole je deklarováno jako statické a jen pro čtení (Shared a ReadOnly v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a je inicializováno pomocí hodnoty, kterou lze vypočítat v době kompilace. Protože hodnotu přiřazenou cílovému poli je nelze vypočítat v době kompilace, změňte deklaraci const (Const v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pole tak, aby hodnota byla vypočítána v době kompilace místo v době běhu. |
| CA1804 | [CA1804: Odebrat nepoužívané místní hodnoty @ no__t-0 | Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon. |
| CA1806 | [CA1806: Neignorujte výsledky metody @ no__t-0. | Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije. |
| CA1809 |[CA1809: Vyhnout se nadměrnému počtu lokálních hodnot @ no__t-0 | Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“. Pokud chcete zvýšit pravděpodobnost, že jsou všechny lokální proměnné uloženy v registrech procesoru, omezte počet lokálních proměnných na 64. |
| CA1810 | [CA1810: Inicializovat statická pole typu odkaz na vloženou hodnotu @ no__t-0 | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
| CA1811 | [CA1811: Vyhněte se nevolanému privátnímu kódu @ no__t-0 | Soukromý nebo interní člen (na úrovni sestavení) nemá v sestavení žádné volající, není vyvolán modulem CLR (Common Language Runtime) ani není vyvolán delegátem. |
| CA1812 | [CA1812: Vyhněte se nevytváření instancí vnitřních tříd @ no__t-0 | Instance typu na úrovni sestavení není vytvořena kódem v sestavení. |
| CA1813 | [CA1813: Vyhněte se nezapečetěným atributům @ no__t-0 | Rozhraní .NET poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon. |
| CA1814 | [CA1814: Preferovat vícenásobná pole nad multidimenzionálním @ no__t-0 | Vícenásobné pole je pole, jehož prvky jsou pole. Pole tvořící prvky mohou být různě velká, což vede k menšímu nevyužitému místu u některých sad dat. |
| CA1815 | [CA1815: Přepište Equals a operátor Equals na hodnotových typech @ no__t-0 | Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals. |
| CA1816 | [CA1816: Vyvolejte GC. SuppressFinalize správně @ no__t-0 | Metoda, která je implementací metody Dispose, nevolá uvolňování paměti. SuppressFinalize; nebo uvolňování paměti volá metodu, která není implementací metody Dispose. SuppressFinalize; nebo volání metody GC. SuppressFinalize a předává něco jiného (Me v jazyce Visual Basic). |
| CA1819 | [CA1819: Vlastnosti by neměly vracet pole @ no__t-0 | Pole vrácená vlastnostmi nejsou chráněna proti zápisu, i když je vlastnost jen pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. |
| CA1820 | [CA1820: Testujte prázdné řetězce pomocí délky řetězce @ no__t-0 | Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals. |
| CA1821 | [CA1821: Odebrat prázdné finalizační metody @ no__t-0 | Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda zvyšuje nároky a nemá žádný užitek. |
| CA1822 |[CA1822: Označit členy jako statické @ no__t-0 | Členové, kteří nemají přístup k instanci dat nebo metodám instance volání může být označený jako statické (sdílené v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód. |
| CA1823 | [CA1823: Vyhněte se nepoužitým privátním polím @ no__t-0 | Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná. |
| CA1824 |[CA1824: Označte sestavení pomocí atribut NeutralResourcesLanguageAttribute @ no__t-0. | Atribut NeutralResourcesLanguage informuje správce prostředků jazyka, který byl použit k zobrazení prostředků neutrální jazykové verze pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu. |
| CA1825 |@NO__T – 0CA1825: Vyhněte se přidělení pole s nulovou délkou @ no__t-0 | Inicializace pole nulové délky vede k nepotřebnému přidělení paměti. Místo toho použijte staticky přidělenou instanci prázdného pole voláním <xref:System.Array.Empty%2A?displayProperty=nameWithType>. Přidělení paměti se sdílí ve všech voláních této metody. |
| CA1900 | [CA1900: Pole hodnot typu by měla být Portable @ no__t-0 | Toto pravidlo kontroluje, zda struktury, které jsou deklarovány pomocí explicitního rozložení, budou při zařazení na nespravovaný kód v 64bitových operačních systémech správně zarovnány. |
| CA1901 | [CA1901: Deklarace P/Invoke by měly být přenosné @ no__t-0 | Toto pravidlo vyhodnotí velikost každého parametru a vrácené hodnoty vyvolání P/Invoke a ověří, zda je velikost parametru správná při zařazení na nespravovaný kód na 32bitových a 64bitových operačních systémech. |
| CA1903 | [CA1903: Použít pouze rozhraní API z cílového rozhraní .NET no__t-0 | Člen nebo typ používá člen nebo typ, který byl uveden v aktualizaci Service Pack, která nebyla zahrnuta stejně jako cílové rozhraní projektu. |
| CA2000 | @NO__T – 0CA2000: Uvolnění objektů před ztrátou rozsahu @ no__t-0 | Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah. |
| CA2001 | @NO__T – 0CA2001: Vyhněte se volání problematických metod @ no__t-0 | Člen volá potencionálně nebezpečnou nebo problematickou metodu. |
| CA2002 |@NO__T – 0CA2002: Nepoužívejte zámky na objekty se slabou identitou @ no__t-0 |Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt. |
| CA2003 |@NO__T – 0CA2003: Nevažovat vlákna za vlákna @ no__t-0 | Spravovaným vláknem se zachází jako [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] vlákna. |
| CA2004 | @NO__T – 0CA2004: Odeberte volání GC. Udržení naživu @ no__t-0 | Pokud převádíte na použití SafeHandle, odeberte veškerá volání GC.KeepAlive (object). V tomto případě by třídy neměly volat metodu GC.KeepAlive. To předpokládá, že nemají destruktor, ale spoléhají na SafeHandle, že dokončí popisovač operačního systému za ně. |
| CA2006 | @NO__T – 0CA2006: Použít SafeHandle k zapouzdření nativních prostředků @ no__t-0 | Použití IntPtr ve spravovaném kódu může znamenat možný problém zabezpečení a spolehlivosti. Všechna použití IntPtr musí být přezkoumána za účelem určení, zda je použití SafeHandle (nebo podobné technologie) na tomto místě vyžadováno. |
| CA2007 | @NO__T – 0CA2007: Nečekat přímo na úlohu @ no__t-0 | Asynchronní metoda [čeká](/dotnet/csharp/language-reference/keywords/await) přímo <xref:System.Threading.Tasks.Task>. Když asynchronní metoda čeká přímo <xref:System.Threading.Tasks.Task>, pokračování probíhá ve stejném vláknu, které úlohu vytvořilo. Toto chování může být nákladné v souvislosti s výkonem a může způsobit zablokování ve vlákně uživatelského rozhraní. Zvažte volání <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> k signalizaci záměru pro pokračování. |
| CA2100 | [CA2100: Zkontrolujte dotazy SQL na chyby zabezpečení @ no__t-0 | Metoda nastavuje vlastnost System.Data.IDbCommand.CommandText pomocí řetězce, který je sestaven z řetězcového argumentu k metodě. Toto pravidlo předpokládá, že řetězcový argument obsahuje vstup uživatele. Řetězec příkazu SQL sestavený ze vstupu uživatele je ohrožen útoky prostřednictvím injektáže SQL. |
| CA2101 |[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného řetězce @ no__t-0. | Člen vyvolání platformy povoluje částečně důvěryhodné volající, má řetězcový parametr a explicitně nezařazuje řetězec. To může způsobit potenciální ohrožení zabezpečení. |
| CA2102 | [CA2102: Zachytávání výjimek bez CLSCompliant v obecných obslužných rutinách @ no__t-0 | Člen v sestavení, které není označeno pomocí atributu RuntimeCompatibilityAttribute nebo je označeno atributem RuntimeCompatibility(WrapNonExceptionThrows = false), obsahuje zachytávací blok, který zpracovává typ System.Exception a neobsahuje bezprostředně následující obecný zachytávací blok. |
| CA2103 | [CA2103: Kontrola imperativního zabezpečení @ no__t-0 |Metoda používá imperativní zabezpečení a může vytvářet oprávnění pomocí stavové informace nebo návratové hodnoty, která se může změnit, pokud je žádost aktivní. Používejte deklarativní zabezpečení vždy, když je to možné. |
| CA2104 |[CA2104: Nedeklarujte proměnlivé odkazové typy pouze pro čtení @ no__t-0 | Externě viditelný typ obsahuje externě viditelné pole měnitelného referenčního typu, které je určeno jen pro čtení. Měnitelný typ je typ, jehož instanční data lze upravit. |
| CA2105 | [CA2105: Pole polí by neměly být pouze pro čtení @ no__t-0. |Pokud použijete jen pro čtení (ReadOnly v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modifikátor pro pole, které obsahuje pole, pole nelze změnit tak, aby odkazovaly na jiné pole. Avšak prvky pole, které jsou uloženy v poli určeném jen pro čtení, mohou být změněny. |
| CA2106 | [CA2106: Zabezpečení výrazů @ no__t-0 | Metoda uplatňuje oprávnění a na volajícím nejsou vykonány žádné kontroly zabezpečení. Uplatnění oprávnění zabezpečení bez provedení jakékoliv kontroly zabezpečení může zanechat ve vašem kódu zneužitelné slabé stránky zabezpečení. |
| CA2107 | [CA2107: Zkontrolovat použití Deny a povolit pouze použití @ no__t-0 |Metoda PermitOnly a akce zabezpečení CodeAccessPermission. Deny by měly být používány pouze pomocí těch, kteří mají pokročilé znalosti zabezpečení .NET. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení. |
| CA2108 | [CA2108: Kontrola deklarativního zabezpečení na typech hodnot @ no__t-0 | Veřejný nebo chráněný hodnotový typ je zabezpečen pomocí přístupu k datům nebo požadavků propojení. |
| CA2109 | [CA2109: Kontrola viditelných obslužných rutin událostí @ no__t-0 | Byla zjištěna veřejná nebo chráněná metoda zpracování událostí. Metody zpracování událostí by neměly být vystaveny, pokud to není nezbytně nutné. |
| CA2111 |[CA2111: Ukazatelé by neměli být viditelné @ no__t-0. | Ukazatel není soukromý, interní nebo jen pro čtení. Škodlivý kód může změnit hodnotu ukazatele, což potenciálně umožňuje přístup do libovolného umístění v paměti nebo může způsobit selhání aplikace nebo systému. |
| CA2112 | [CA2112: Zabezpečené typy by neměly vystavovat pole @ no__t-0 | Veřejný nebo chráněný typ obsahuje veřejná pole a je zabezpečen pomocí požadavků propojení. Pokud má kód přístup k instanci typu, která je zabezpečena pomocí požadavku propojení, nemusí kód vyhovět požadavku propojení pro přístup k polím tohoto typu. |
| CA2114 | [CA2114: Zabezpečení metody by mělo být nadmnožinou typu @ no__t-0. | Metoda by neměla mít pro stejnou akci deklarativní zabezpečení jak na úrovni metody, tak na úrovni typu. |
| CA2115 | [CA2115: Vyvolejte GC. Udržení naživu při použití nativních prostředků @ no__t-0 | Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem. |
| CA2116 | [CA2116: Metody APTCA by měly volat pouze metody APTCA @ no__t-0 |Když je pro plně důvěryhodná sestavení uveden atribut APTCA (AllowPartiallyTrustedCallersAttribute) a sestavení spustí kód v jiném sestavení, které neumožňuje volání částečně důvěryhodným volajícím, může se jednat o chybu v zabezpečení. |
| CA2117 | [CA2117: Typy APTCA by měly rozšířily pouze základní typy APTCA @ no__t-0 | Když je pro plně důvěryhodná sestavení uveden atribut APTCA a v sestavení je odvozen z typu, který neumožňuje volání částečně důvěryhodným volajícím, může se jednat o chybu v zabezpečení. |
| CA2118 | [CA2118: Kontrola využití SuppressUnmanagedCodeSecurityAttribute @ no__t-0 |Atribut SuppressUnmanagedCodeSecurityAttribute mění výchozí chování zabezpečení systému pro členy vykonávající nespravovaný kód, který používá zprostředkovatele komunikace s objekty COM nebo vyvolání operačního systému. Tento atribut slouží především ke zvýšení výkonu, ačkoliv nárůst výkonu může být spojen s významnými riziky zabezpečení. |
| CA2119 | [CA2119: Metody zapečetění, které odpovídají privátním rozhraním @ no__t-0 | Odvoditelný veřejný typ poskytuje implementaci přepisovatelné metody vnitřního (Friend v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) rozhraní. Chcete-li opravit porušení tohoto pravidla, zabraňte přepsání metody mimo sestavení. |
| CA2120 | [CA2120: Zabezpečené serializace konstruktory @ no__t-0 | Tento typ má konstruktor, který přebírá objekt System.Runtime.Serialization.SerializationInfo a objekt System.Runtime.Serialization.StreamingContext (podpis serializace konstruktoru). Tento konstruktor není zabezpečen pomocí kontroly zabezpečení, ale jeden nebo více běžných konstruktorů tohoto typu je zabezpečených. |
| CA2121 | [CA2121: Statické konstruktory by měly být privátní @ no__t-0 | Systém volá statický konstruktor před vytvořením první instance typu nebo předtím, než jsou odkazovány jakékoli statické členy. Pokud statický konstruktor není soukromý, může být volán jiným kódem než kódem systému. V závislosti na operacích, které jsou provedeny v konstruktoru, to může způsobit neočekávané chování. |
| CA2122 | [CA2122: Nezveřejňujte nepřímo metody s požadavky propojení @ no__t-0 | Veřejný nebo chráněný člen má požadavky propojení a je volán členem, který neprovádí žádné bezpečnostní kontroly. Požadavek propojení kontroluje pouze oprávnění bezprostředního volajícího. |
| CA2123 | [CA2123: Požadavky na přepsání odkazu by měly být shodné se základem @ no__t-0 | Toto pravidlo přiřazuje metodu své základní metodě, kterou je buď rozhraní, nebo virtuální metoda jiného typu, a poté v obou metodách srovnává požadavky propojení. Je-li toto pravidlo porušeno, může chybný volající obejít požadavek propojení pouhým voláním nezabezpečené metody. |
| CA2124 | [CA2124: Zalamovat nezranitelné klauzule finally ve vnějším try @ no__t-0 | Veřejná nebo chráněná metoda obsahuje blok try/finally. Blok finally nejspíše obnovuje stav zabezpečení a sám není uzavřen v bloku finally. |
| CA2126 | @NO__T – 0CA2126: Požadavky na propojení typů vyžadují dědičnost požadavků @ no__t-0 | Veřejný nezapečetěný typ je chráněn pomocí požadavku propojení a má přepisovatelnou metodu. Tento typ ani tato metoda nejsou chráněny pomocí vyžádané dědičnosti. |
| CA2127 | [CA2136: Členové by neměli mít konfliktní poznámky transparentnosti @ no__t-0 | Ve 100 % transparentním sestavení nemůže nastat kritický kód. Toto pravidlo analyzuje 100 % transparentní sestavení pro jakékoliv anotace SecurityCritical na úrovni typu, pole a metody. |
| CA2128 |[CA2147: Transparentní metody nemůžou používat výrazy zabezpečení @ no__t-0. | Toto pravidlo analyzuje všechny metody a typy v sestavení, který je buď 100 % transparentní, nebo smíšené transparentní/kritické a označí všechny deklarativní nebo imperativní použití výrazu Assert. |
| CA2129 | [CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení @ no__t-0. | Metody označené pomocí atributu SecurityTransparentAttribute volají neveřejné členy, které jsou označeny jako SecurityCritical. Toto pravidlo analyzuje všechny metody a typy v sestavení, které je transparentní/kritické, a označí všechna volání z transparentního kódu do neveřejného kritického kódu, která nejsou označena jako SecurityTreatAsSafe. |
| CA2130 | [CA2130: Konstanty kritické pro zabezpečení by měly být transparentní @ no__t-0 | Pro konstantní hodnoty není vynucována transparentnost, protože kompilátory vkládají konstantní hodnoty do kódu, aby za běhu programu nebylo zapotřebí žádné vyhledávání. Konstantní pole by měla být transparentní z pohledu zabezpečení, aby kontroloři kódu nepředpokládali, že transparentní kód nemůže ke konstantě přistoupit. |
| CA2131 | [CA2131: Typy kritické pro zabezpečení se nemusí účastnit v rovnosti typů @ no__t-0. | Typ se účastní porovnávání typu, přičemž typ samotný nebo jeho člen nebo pole jsou označeny atributem SecurityCriticalAttribute. Toto pravidlo nastává pro všechny kritické typy nebo typy obsahující kritické metody nebo pole, která se účastní porovnávání typu. Když modul CLR zjistí takový typ, nenačítá jej a za běhu vyvolá výjimku TypeLoadException. Obvykle je toto pravidlo vyvoláno pouze v případě, že uživatelé implementují rovnocennost typu ručně namísto prostřednictvím tlbimp a provedení rovnocennosti typu kompilátorem. |
| CA2132 | [CA2132: Výchozí konstruktory musí být alespoň tak kritické jako výchozí konstruktory základního typu @ no__t-0. |Typy a členy, které mají atribut SecurityCriticalAttribute, nelze použít kódem aplikace Silverlight. Typy a členy kritické z hlediska zabezpečení lze použít pouze prostřednictvím důvěryhodného kódu v knihovně tříd rozhraní .NET Framework aplikace Silverlight. Protože veřejné nebo chráněné konstrukce v odvozené třídě musí mít stejnou nebo větší transparentnost než jejich základní třída, nelze třídu v aplikaci odvodit z třídy označené jako SecurityCritical. |
| CA2133 | [CA2133: Delegáti musí být vázáni k metodám s konzistentní transparentností @ no__t-0. | Toto upozornění je vyvoláno na metodě, která vytvoří vazbu delegáta označeného pomocí atributu SecurityCriticalAttribute na metodu, která je transparentní nebo která je označena pomocí atributu SecuritySafeCriticalAttribute. Upozornění je také vyvoláno na metodě, která vytvoří vazbu transparentního delegáta nebo bezpečně kritického delegáta na kritickou metodu. |
| CA2134 | [CA2134: Metody musí při přepisování základních metod zachovávat konzistentní transparentnost. @ no__t-0 |Toto pravidlo je vyvoláno, když metoda označená pomocí atributu SecurityCriticalAttribute přepíše metodu, která je transparentní nebo označená pomocí atributu SecuritySafeCriticalAttribute. Toto pravidlo je vyvoláno také, když transparentní metoda nebo metoda označená pomocí atributu SecuritySafeCriticalAttribute přepíše metodu, která je označená pomocí atributu SecurityCriticalAttribute. Pravidlo je použito při přepisování virtuální metody nebo implementaci rozhraní. |
| CA2135 | [CA2135: Sestavení úrovně 2 by neměla obsahovat LinkDemands @ no__t-0. | Pravidla LinkDemand jsou v sadě pravidel zabezpečení úrovně 2 již zastaralá. Namísto použití pravidel LinkDemand k vynucení zabezpečení v době kompilace JIT označte metody, typy a pole pomocí atributu SecurityCriticalAttribute. |
| CA2136 | [CA2136: Členové by neměli mít konfliktní poznámky transparentnosti @ no__t-0 | Atributy transparentnosti jsou použity z prvků kódu většího rozsahu na prvky menšího rozsahu. Atributy transparentnosti prvků kódu, které mají větší rozsah, mají přednost před atributy transparentnosti prvků kódu, které jsou obsaženy v prvním prvku. Například třída označená atributem SecurityCriticalAttribute nemůže obsahovat metodu, která je označena atributem SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Transparentní metody musí obsahovat jenom ověřitelný IL @ no__t-0. | Metoda obsahuje kód, který nelze ověřit, nebo vrací typ odkazem. Toto pravidlo je vyvoláno při pokusech transparentního kódu zabezpečení spustit jazyk MSIL, který nelze ověřit. Pravidlo však neobsahuje úplný ověřovatel jazyka IL a místo toho k zachycení většiny porušení ověření jazyka MSIL používá heuristiky. |
| CA2138 | [CA2138: Transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity @ no__t-0. | Transparentní metoda zabezpečení volá metodu, která je označena atributem SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Transparentní metody nemůžou používat atribut HandleProcessCorruptingExceptions @ no__t-0. | Toto pravidlo je vyvoláno, je-li jakákoliv metoda transparentní a pokusí se zpracovat výjimku poškozující proces použitím atributu HandleProcessCorruptedStateExceptionsAttribute. Výjimka poškozující proces je klasifikace výjimek dle specifikace CLR verze 4.0, jako například výjimka AccessViolationException. Atribut HandleProcessCorruptedStateExceptionsAttribute lze použít pouze metodami kritickými pro bezpečnost a bude ignorován, je-li použit u transparentních metod. |
| CA2140 | [CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení @ no__t-0. | Prvek kódu označený atributem SecurityCriticalAttribute je kritický pro zabezpečení. Transparentní metoda nemůže použít prvek kritický pro zabezpečení. Pokud se transparentní typ pokusí použít typ kritický pro zabezpečení, je vyvolána výjimka TypeAccessException, MethodAccessException nebo FieldAccessException. |
| CA2141 |[CA2141:Transparentní metody nesmějí vyhovovat LinkDemands](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Transparentní metoda (z hlediska zabezpečení) volá metodu v sestavení, které není označeno atributem APTCA, nebo transparentní metoda (z hlediska zabezpečení) splňuje pravidlo LinkDemand pro typ nebo metodu. |
| CA2142 | [CA2142: Transparentní kód by neměl být chráněn pomocí LinkDemands @ no__t-0. | Toto pravidlo je vyvoláno transparentními metodami, které k přístupu vyžadují pravidla LinkDemand. Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. |
| CA2143 | [CA2143: Transparentní metody by neměly používat požadavky na zabezpečení @ no__t-0 | Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. Kód transparentní z hlediska zabezpečení by měl k učinění rozhodnutí o zabezpečení používat úplné požadavky a bezpečně kritický kód by neměl spoléhat na to, že transparentní kód tyto úplné požadavky provede. |
| CA2144 | [CA2144: Transparentní kód by neměl načítat sestavení z bajtových polí @ no__t-0 | Přezkoumání zabezpečení transparentního kódu není tak úplné jako přezkoumání zabezpečení kritického kódu, protože transparentní kód nemůže provádět akce citlivé na zabezpečení. Sestavení, která jsou načtena z pole bajtů, nemohou být v transparentním kódu zaznamenána a takové pole bajtů může obsahovat kritický nebo důležitější bezpečně kritický kód, který musí být auditován. |
| CA2145 | [CA2145: Transparentní metody by neměly být dekorované s použitím SuppressUnmanagedCodeSecurityAttribute @ no__t-0. | Metody označené atributem SuppressUnmanagedCodeSecurityAttribute mají implicitní LinkDemand umístěn na jakoukoli metodu, která jej volá. Tento LinkDemand vyžaduje, aby byl volající kód kritický z hlediska zabezpečení. Označení metody, která používá SuppressUnmanagedCodeSecurity, atributem SecurityCriticalAttribute zviditelňuje tento požadavek pro volající metody. |
| CA2146 | [CA2146: Typy musí být alespoň tak kritické jako jejich základní typy a rozhraní @ no__t-0. | Toto pravidlo je vyvoláno, když má odvozený typ atribut transparentnosti zabezpečení, který není tak kritický jako jeho základní typ nebo implementované rozhraní. Pouze kritické typy lze odvodit z kritických základních typů nebo mohou implementovat kritická rozhraní a pouze kritické typy nebo bezpečně kritické typy mohou být odvozeny ze základních bezpečně kritických typů nebo mohou implementovat bezpečně kritická rozhraní. |
| CA2147 |[CA2147: Transparentní metody nemůžou používat výrazy zabezpečení @ no__t-0. | U kódu označeného atributem SecurityTransparentAttribute není uděleno dostatečné oprávnění k vyhodnocení. |
| CA2149 | [CA2149: Transparentní metody nesmí volat do nativního kódu @ no__t-0. | Toto pravidlo je vyvoláno na každé transparentní metodě, která přímo volá nativní kód (například prostřednictvím P/Invoke). Porušení tohoto pravidla vede k vyvolání výjimky MethodAccessException v modelu transparentnosti úrovně 2 a k úplnému požadavku na nespravovaný kód v modelu transparentnosti úrovně 1. |
| CA2151 |[CA2151: Pole s kritickými typy by měla být kritická zabezpečení @ no__t-0 | Chcete-li používat typy kritické z hlediska zabezpečení, musí být kód, který odkazuje na typ, buď kritický z hlediska zabezpečení, nebo bezpečně kritický z hlediska zabezpečení. To platí i v případě, že je odkaz nepřímý. Proto je existence transparentního pole kritického z hlediska zabezpečení nebo transparentního pole bezpečně kritického z hlediska zabezpečení zavádějící, jelikož transparentní kód nebude mít k poli přístup. |
| CA2200 | [CA2200: Znovu vyvolat pro zachování podrobností zásobníku @ no__t-0 | Výjimka je znovu vyvolána a je jednoznačně uvedena v příkazu throw. Jestliže je výjimka znovu vyvolána zadáním výjimky v příkazu throw, seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztracen. |
| CA2201 | [CA2201: Nevyvolávání rezervovaných typů výjimek @ no__t-0 | Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2202 | [CA2202: Neodstraňujte objekty víckrát @ no__t-0 |Implementace metody obsahuje cesty kódu, které by mohly způsobit více volání metody System.IDisposable.Dispose nebo ekvivalentní metody pro uvolnění (například metoda Close() u některých typů) stejného objektu. |
| CA2204 | [CA2204: Literály by měly být zadány správně @ no__t-0 | Řetězcový literál v těle metody obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. |
| CA2205 | [CA2205: Použít spravované ekvivalenty Win32 API @ no__t-0 | Je definována metoda vyvolání operačního systému a metoda .NET, která má ekvivalentní funkci, je k dispozici. |
| CA2207 | [CA2207: Inicializovat typ hodnoty statických polí s vložením @ no__t-0 | Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte. |
| CA2208 |@NO__T – 0CA2208: Vytváření instancí výjimek argumentu správně @ no__t-0 | Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena. |
| CA2210 |[CA2210: Sestavení by měly mít platné silné názvy @ no__t-0 | Silný název chrání klienty před neúmyslným načtením narušeného sestavení. Sestavení bez silných názvů by kromě velmi omezených scénářů neměla být nasazována. Pokud sdílíte nebo šíříte sestavení, která nejsou správně podepsána, může být sestavení záměrně poškozeno, modul CLR je nemusí načíst nebo uživatelé mohou být nuceni vypnout na svém počítači ověřování. |
| CA2211 |[CA2211: Nekonstantní pole by nemělo být viditelné @ no__t-0 | Statická pole, která nejsou konstantami ani nejsou jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy. |
| CA2212 | [CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod @ no__t-0 |Metoda typu, který je odvozen z typu System.EnterpriseServices.ServicedComponent, je označena pomocí atributu System.Web.Services.WebMethodAttribute. Protože atribut WebMethodAttribute a metoda ServicedComponent mají konfliktní chování a požadavky na kontext a tok transakcí, bude chování metody v některých případech nesprávné. |
| CA2213 | [CA2213: Pole na jedno použití by mělo být uvolněno @ no__t-0 | Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu. |
| CA2214 | [CA2214: Nevolejte přepsatelné metody v konstruktorech @ no__t-0 | Při volání virtuální metody konstruktorem nemusí být konstruktor instance, která volá tuto metodu, proveden. |
| CA2215 | [CA2215: Metody Dispose by měly volat Dispose třídy Base @ no__t-0 | Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose. |
| CA2216 |[CA2216: Typy na jedno použití by měly deklarovat finalizační metodu @ no__t-0. | Typ, který implementuje rozhraní System.IDisposable a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno metodou Object.Finalize. |
| CA2217 | [CA2217: Neoznačujte výčty pomocí FlagsAttribute @ no__t-0 |Externě viditelný výčet je označen atributem FlagsAttribute a má jednu nebo více hodnot, které nejsou mocninami dvou nebo kombinací jiných definovaných hodnot výčtu. |
| CA2218 |[CA2218: Přepsat GetHashCode při přepsání rovnosti @ no__t-0 | Metoda GetHashCode vrací hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako například tabulku hash. Dva objekty, které jsou stejného typu a jsou stejné, musí vrátit stejnou hodnotu hash. |
| CA2219 | @NO__T – 0CA2219: Nevyvolávání výjimek v klauzulích výjimky @ no__t-0 | Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2220 | [CA2220: Finalizační metody by měly volat finalizační metodu třídy Base @ no__t-0 | Finalizační metoda musí být šířena přes hierarchii dědičnosti. Chcete-li to zaručit, musí typy zavolat metodu Finalize své základní třídy ve své vlastní metodě Finalize. |
| CA2221 |[CA2221: Finalizační metody by měly být chráněné @ no__t-0 | Finalizační metody musí použít modifikátor přístupu family. |
| CA2222 | @NO__T – 0CA2222: Nezmenšení děděné viditelnosti členů @ no__t-0 |Modifikátor přístupu byste neměli měnit u zděděných členů. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody. |
| CA2223 | [CA2223: Členy by se měly lišit o více než návratový typ @ no__t-0. | Přestože modul CLR (Common Language Runtime) umožňuje používat návratové typy k rozlišení mezi jinak identickými členy, tato funkce není ve specifikaci CLS, ani není běžnou funkcí v programovacích jazycích rozhraní .NET. |
| CA2224 | [CA2224: Přepište Equals při přetížení operátoru rovnosti @ no__t-0 | Veřejný typ implementuje operátor rovnosti, ale nepřepisuje metodu Object.Equals. |
| CA2225 | [CA2225: Přetížení operátoru mají pojmenované alternativy @ no__t-0 |Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích nepodporujících přetížené operátory. |
| CA2226 | @NO__T – 0CA2226: Operátory by měly mít symetrické přetížení @ no__t-0. | Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor. |
| CA2227 |[CA2227: Vlastnosti kolekce by měly být jen pro čtení @ no__t-0 |Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy. |
| CA2228 | @NO__T – 0CA2228: Nedodá neuvolníelné formáty prostředků @ no__t-0 | Soubory prostředků, které byly vytvořeny pomocí předprodejní verze rozhraní .NET, nemusí být použitelné pro podporované verze rozhraní .NET. |
| CA2229 | [CA2229: Implementovat konstruktory serializace @ no__t-0 | Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. |
| CA2230 | [CA2230: Použijte parametry pro proměnné argumenty @ no__t-0 | Veřejný nebo chráněný typ obsahuje veřejnou nebo chráněnou metodu, která používá konvenci volání VarArgs místo klíčového slova params. |
| CA2231 | [CA2231: Operátor přetížení se rovná přetížení ValueType. Equals @ no__t-0 | Hodnotový typ přepisuje metodu Object.Equals, ale neimplementuje operátor rovnosti. |
| CA2232 | [CA2232: Označit model Windows Forms vstupními body pomocí STAThread @ no__t-0 | Atribut STAThreadAttribute znamená, že model vláken aplikace COM je jednovláknový apartment (STA). Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně. |
| CA2233 |[CA2233: Operace by neměly přetečení @ no__t-0. | Aritmetické operace byste neměli provádět bez ověření operandů. Tím zajistíte, že výsledek operace není mimo rozsah možných hodnot použitých datových typů. |
| CA2234 | [CA2234: Předejte objekty System. URI místo řetězců @ no__t-0. | Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“. Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri. |
| CA2235 | [CA2235: Označte všechna Neserializovatelný pole @ no__t-0 | Neserializovatelný typ pole instance je deklarován v serializovatelném typu. |
| CA2236 | [CA2236: Volejte metody základní třídy na typech ISerializable @ no__t-0 | Chcete-li napravit porušení tohoto pravidla, zavolejte metodu GetObjectData základního typu nebo konstruktor serializace z odpovídající metody nebo konstruktoru odvozeného typu. |
| CA2237 | [CA2237: Označte typy ISerializable pomocí SerializableAttribute @ no__t-0. | Aby byl typ rozpoznán modulem CLR (Common Language Runtime) jako serializovatelný, musí být označen pomocí atributu SerializableAttribute, i když typ používá vlastní rutinu serializace prostřednictvím implementace rozhraní ISerializable. |
| CA2238 |[CA2238: Implementujte správně metody serializace @ no__t-0 | Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost. |
| CA2239 | [CA2239: Poskytněte metody deserializace pro volitelná pole @ no__t-0 | Typ má pole označené atributem System.Runtime.Serialization.OptionalFieldAttribute a neposkytuje metody zpracování událostí deserializace. |
| CA2240 | [CA2240: Implementace ISerializable správně @ no__t-0 | Chcete-li opravit porušení tohoto pravidla, nastavte metodu GetObjectData jako viditelnou a přepisovatelnou a ujistěte se, že všechna pole instancí jsou součástí procesu serializace nebo výslovně označena pomocí atributu NonSerializedAttribute. |
| CA2241 | [CA2241: Poskytněte správné argumenty pro metody formátování @ no__t-0 | Formátovací argument, který je předán metodě System.String.Format, neobsahuje formátovací položku, která odpovídá každému argumentu objektu nebo naopak. |
| CA2242 |[CA2242: Test pro správně NaN @ no__t-0 | Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double). |
| CA2243 |[CA2243: Řetězcové literály atributu by se měly správně analyzovat @ no__t-0 | Parametr řetězcového literálu atributu nesprávně analyzuje adresu URL, identifikátor GUID nebo verzi. |
| CA5122 | [CA5122: Deklarace volání nespravovaného kódu nesmí být kritické pro zabezpečení](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Metody jsou při provádění operace citlivé na zabezpečení označeny jako SecuritySafeCritical, ale lze je také bezpečně použít transparentním kódem. Transparentní kód nesmí nikdy přímo volat nativní kód prostřednictvím P/Invoke. Proto označení P/Invoke jako bezpečně kritické z hlediska zabezpečení neumožní transparentnímu kódu vyvolat je a je zavádějící pro analýzu zabezpečení. |
