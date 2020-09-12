---
title: Přehled pravidel pro kvalitu kódu
ms.date: 09/01/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
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
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
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
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a298ab142ae6a44c1fb24b2cb1b752f6beb4a68e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037234"
---
# <a name="code-quality-analysis-rules-by-rule-id"></a>Pravidla analýzy kvality kódu podle ID pravidla

V následující tabulce jsou uvedena pravidla analýzy kvality kódu podle identifikátoru pravidla.

| CheckId | Upozornění | Popis |
|---------| - | - |
| CA1000 | [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000.md) | Při volání statického členu obecného typu musí být pro tento typ zadán argument typu. Je-li zavolán obecný člen instance, který nepodporuje odvozování, musí být pro tento člen zadán argument typu. V těchto dvou případech je syntaxe zadávání argumentu typu různá a snadno zaměnitelná. |
| CA1001 | [CA1001: Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné](../code-quality/ca1001.md) | Třída deklaruje a implementuje pole instance typu System.IDisposable, přičemž neimplementuje rozhraní IDisposable. Třída, která deklaruje pole IDisposable nepřímo, vlastní nespravovaný zdroj a měla by rozhraní IDisposable implementovat. |
| CA1002 | [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002.md) | System. Collections. Generic. list< (of \<(T> ) >) je obecná kolekce, která je navržena pro výkon, nikoli dědičnost. Proto třída List neobsahuje žádné virtuální členy. Místo ní by měly být vystaveny kolekce navržené pro dědičnost. |
| CA1003 | [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003.md) |Typ obsahuje delegát, který vrací typ void, jehož signatura obsahuje dva parametry (první objekt a druhý typ, který lze přiřadit k EventArgs), a nadřazené sestavení cílí na Microsoft .NET Framework 2,0. |
| CA1005 | [CA1005: Vyhněte se nadbytečným parametrům u obecných typů](../code-quality/ca1005.md) | Čím více parametrů typu obecný typ obsahuje, tím obtížnější je vědět a zapamatovat si, co každý z parametrů typu představuje. Je obvykle zřejmé s jedním parametrem typu, jako v seznamu \<T> , a v některých případech, které mají dva parametry typu, jako ve slovníku \<TKey, TValue> . Pokud však existují více než dva parametry typu, stává se pro většinu uživatelů použití příliš obtížným. |
| CA1008 | [CA1008: Výčty by měly mít nulovou hodnotu](../code-quality/ca1008.md) | Výchozí hodnota neinicializovaného výčtu je stejně jako u jiných typů hodnot nula. Atributovaný výčet bez příznaků by měl definovat člen za použití hodnoty nula tak, aby výchozí hodnota byla platnou hodnotou výčtu. Definuje-li výčet, který má aplikován atribut FlagsAttribute, člen s hodnotou nula, měl by jeho název být „None“, aby tak označoval, že ve výčtu nebyly nastaveny žádné hodnoty. |
| CA1010 | [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010.md) | Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Pak lze tuto kolekci použít k zaplnění typů obecných kolekcí. |
| CA1012 | [CA1012: Abstraktní typy by neměly mít konstruktory](../code-quality/ca1012.md) | Konstruktory abstraktních typů mohou být volány pouze odvozenými typy. Jelikož veřejné konstruktory vytvářejí instance typu, přičemž nelze vytvořit instance abstraktního typu, je abstraktní typ obsahující veřejný konstruktor nesprávně navržen. |
| CA1014 | [CA1014: Označte sestavení pomocí CLSCompliantAttribute](../code-quality/ca1014.md) | Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh určuje, že všechna sestavení explicitně označují dodržování předpisů CLS pomocí <xref:System.CLSCompliantAttribute> . Není-li tento atribut v sestavení přítomen, nedodržuje sestavení specifikaci. |
| CA1016 | [CA1016: Označte sestavení pomocí AssemblyVersionAttribute](../code-quality/ca1016.md) | Rozhraní .NET používá číslo verze k jednoznačné identifikaci sestavení a k vytvoření vazby na typy v silně pojmenovaných sestaveních. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny. |
| CA1017 | [CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017.md) |Atribut ComVisibleAttribute určuje způsob přístupu klientů COM ke spravovanému kódu. Dobrý návrh přikazuje, aby sestavení explicitně uvedla viditelnost modelu COM. Viditelnost modelu COM může být nastavena pro celé sestavení a poté přepsána pro jednotlivé typy a členy typů. Není-li tento atribut přítomen, je obsah sestavení viditelný klientům COM. |
| CA1018 | [CA1018: Označte atributy pomocí AttributeUsageAttribute](../code-quality/ca1018.md) | Při definování vlastního atributu jej označte použitím atributu AttributeUsageAttribute, čímž je určeno, kde ve zdrojovém kódu může být vlastní atribut použit. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. |
| CA1019 | [CA1019: Definujte přístupové objekty pro argumenty atributů](../code-quality/ca1019.md) | Atributy mohou definovat povinné argumenty, které musí být specifikovány při použití atributu na cíl. Říká se jim také poziční argumenty, jelikož jsou konstruktorům atributů předány jako poziční parametry. Pro každý povinný argument by měl atribut navíc poskytovat odpovídající vlastnost jen pro čtení, aby mohla být hodnota argumentu během spuštění získána. Atributy mohou také definovat volitelné argumenty, které jsou rovněž známy jako pojmenované argumenty. Tyto argumenty jsou podle názvu poskytovány konstruktorům atributů a měly by mít odpovídající vlastnost pro čtení i zápis. |
| CA1021 | [CA1021: Vyhněte se výstupním parametrům](../code-quality/ca1021.md) | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů, a schopnost práce s metodami vracejícími více návratových typů. Také rozdíl mezi parametry „out“ a „ref“ není běžně chápán. |
| CA1024 | [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024.md) | Veřejná nebo chráněná metoda má název začínající na „Get“, nepřijímá žádné parametry a vrací hodnotu, která není polem. Metoda může být dobrým kandidátem, aby se stala vlastností. |
| CA1027 |[CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027.md) | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Mohou-li být pojmenované konstanty smysluplně kombinovány, použijte ve výčtu atribut FlagsAttribute. |
| CA1028 | [CA1028: Úložiště výčtu by mělo být Int32](../code-quality/ca1028.md) | Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Ve výchozím nastavení je pro uložení konstantní hodnoty použit datový typ System.Int32. Přestože lze tento typ změnit, není to ve většině případů zapotřebí ani doporučováno. |
| CA1030 | [CA1030: Použijte události, kde je to vhodné](../code-quality/ca1030.md) |Toto pravidlo zjišťuje metody, které mají názvy obvykle používané pro události. Je-li metoda volána jako odpověď na jednoznačně definovanou změnu stavu, měla by být metoda volána obslužnou rutinou události. Objekty volající tuto metodu by měly místo přímého volání metody vyvolat událost. |
| CA1031 | [CA1031: Nezachycujte výjimky obecného typu](../code-quality/ca1031.md) | Obecné výjimky by neměly být zachycovány. Zachyťte více specifickou výjimku nebo jako poslední příkaz v zachytávacím bloku opětovně vyvolejte obecnou výjimku. |
| CA1032 |[CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032.md) | Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. |
| CA1033 | [CA1033: Metody rozhraní by měly být volatelné podřízenými typy](../code-quality/ca1033.md) | Nezapečetěný externě viditelný typ poskytuje explicitní implementaci metod veřejného rozhraní a neposkytuje alternativní externě viditelnou metodu stejného názvu. |
| CA1034 | [CA1034: Vnořené typy by neměly být viditelné](../code-quality/ca1034.md) | Vnořený typ je typ deklarovaný v rámci jiného typu. Vnořené typy jsou užitečné pro zapouzdření soukromých podrobností implementace v daném typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné. |
| CA1036 | [CA1036: Přepište metody u srovnatelných typů](../code-quality/ca1036.md) |Veřejný nebo chráněný typ implementuje rozhraní System.IComparable. Nepřepisuje metodu Object.Equals ani nepřetěžuje operátory rovnosti, nerovnosti, menší než a větší než specifické pro daný jazyk. |
| CA1040 |[CA1040: Vyhněte se prázdným rozhraním](../code-quality/ca1040.md) | Rozhraní definují členy ujednávající jejich chování nebo užití. Funkčnost popsaná rozhraním může být osvojena libovolným typem bez ohledu na to, kde se typ vyskytuje v hierarchii dědičnosti. Typ implementuje rozhraní tím, že poskytuje implementace jeho členů. Prázdné rozhraní nedefinuje žádné členy, tudíž ani nedefinuje žádná implementovatelná ujednání. |
| CA1041 | [CA1041: Poskytněte zprávu ObsoleteAttribute](../code-quality/ca1041.md) | Typ nebo člen je označen atributem System.ObsoleteAttribute, aniž by měl zadánu vlastnost ObsoleteAttribute.Message. Při kompilaci typu nebo členu označeného atributem ObsoleteAttribute je zobrazena vlastnost zprávy tohoto atributu. To uživateli poskytuje informace o zastaralém typu nebo členu. |
| CA1043 | [CA1043: Použijte celočíselný nebo řetězcový argument pro indexery](../code-quality/ca1043.md) | Indexery (tj. indexované vlastnosti) by měly jako index používat celočíselné typy nebo typy řetězců. Tyto typy se obvykle používají pro indexování datových struktur a zvyšují použitelnost knihovny. Použití typu Object by mělo být omezeno na ty případy, kdy během návrhu není možné určit konkrétní celočíselný nebo řetězcový typ. |
| CA1044 | [CA1044: Vlastnosti by neměly být pouze pro zápis](../code-quality/ca1044.md) | Ačkoli je přijatelné a často nezbytné použít vlastnost jen pro čtení, směrnice návrhu zakazují použití vlastností jen pro zápis. Důvodem je skutečnost, že umožnit uživateli nastavit hodnotu a poté uživateli zabránit v zobrazení této hodnoty není bezpečné. Taktéž bez přístupu pro čtení není možné zobrazit stav sdílených objektů, což omezuje jejich užitečnost. |
| CA1045 |[CA1045: Nepředávejte typy odkazem](../code-quality/ca1045.md) | Předávání typů odkazem (za použití klíčových slov „out“ nebo „ref“) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů a schopnost práce s metodami vracejícími více návratových typů. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat, že uživatelé budou hlavní pracovat s `out` `ref` parametry nebo. |
| CA1046 | [CA1046: Nepřetěžujte operátory rovnosti u odkazových typů](../code-quality/ca1046.md) | U referenčních typů je výchozí implementace operátoru rovnosti téměř vždy správná. Ve výchozím nastavení jsou dva odkazy rovny, pouze pokud ukazují na stejný objekt. |
| CA1047 |[CA1047: Nedeklarujte chráněné členy v zapečetěných typech](../code-quality/ca1047.md) | Typy deklarují chráněné členy, aby k nim odvozené typy mohly přistupovat nebo je přepisovat. Dle definice nelze dědit zapečetěné typy, což znamená, že nelze volat chráněné metody zapečetěných typů. |
| CA1050 | [CA1050: Deklarujte typy v oborech názvů](../code-quality/ca1050.md) | Typy jsou deklarovány v oborech názvů, aby bylo zabráněno kolizím názvů a zároveň jako způsob organizace souvisejících typů v hierarchii objektů. |
| CA1051 | [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051.md) | Hlavní použití pole by mělo být jako podrobnost implementace. Pole by měla být soukromá nebo vnitřní a měla by být vystavena s použitím vlastností. |
| CA1052 | [CA1052: Statické typy vlastníků by měly být zapečetěné](../code-quality/ca1052.md) | Veřejný nebo chráněný typ obsahuje pouze statické členy a není deklarován s použitím zapečetěného modifikátoru (NotInheritable) (jazyk C#). Typu, u nějž není zamýšleno dědění, by mělo být prostřednictvím označením zapečetěným modifikátorem zabráněno, aby byl použit jako základní typ. |
| CA1053 |[CA1053: Statické typy vlastníků by neměly mít konstruktory](../code-quality/ca1053.md) | Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má veřejný nebo chráněný výchozí konstruktor. Konstruktor není nutný, protože volání statických členů nevyžaduje instanci typu. Z důvodu bezpečnosti a zabezpečení by řetězcová přetížení měla volat přetížení identifikátoru URI použitím argumentu řetězce. |
| CA1054 | [CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054.md) | Pakliže metoda přijímá řetězcovou reprezentaci identifikátoru URI, mělo by být poskytnuto odpovídající přetížení přijímající instanci třídy URI, která tyto služby poskytuje bezpečným a zabezpečeným způsobem. |
| CA1055 | [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055.md) | Toto pravidlo předpokládá, že metoda vrací identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1056 | [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056.md) | Toto pravidlo předpokládá, že vlastnost reprezentuje identifikátor URI. Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Třída System.Uri poskytuje tyto služby bezpečným a zabezpečeným způsobem. |
| CA1058 | [CA1058: Typy by neměly rozšiřovat určité základní typy](../code-quality/ca1058.md) | Externě viditelný typ rozšiřuje určité základní typy. Použijte jednu z alternativ. |
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
| CA1303 | [CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303.md) | Externě viditelná metoda předává řetězcový literál jako parametr konstruktoru nebo metodě .NET a tento řetězec by měl být Lokalizovatelný. |
| CA1304 | [CA1304: Určete CultureInfo](../code-quality/ca1304.md) | Metoda nebo konstruktor volá člen, který má přetížení přijímající parametr System.Globalization.CultureInfo, a tato metoda nebo konstruktor nevolá přetížení přebírající parametr CultureInfo. Pokud objekt CultureInfo nebo System.IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1305 | [CA1305: Určete IFormatProvider](../code-quality/ca1305.md) | Metoda nebo konstruktor volá jeden nebo více členů, které mají přetížení přijímající parametr System.IFormatProvider, a tato metoda nebo konstruktor nevolá přetížení, která přebírá parametr IFormatProvider. Pokud objekt System.Globalization.CultureInfo nebo IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt. |
| CA1307 | [CA1307: Zadejte StringComparison, aby nebyly pochyby](../code-quality/ca1307.md) | Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison. |
| CA1308 |[CA1308: Normalizujte řetězce na velká písmena](../code-quality/ca1308.md) | Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků nedokáže po převodu na malá písmena provést zpáteční cestu. |
| CA1309 | [CA1309: Použijte řadový StringComparison](../code-quality/ca1309.md) | Nelingvistická operace porovnání řetězců nemá nastaven parametr StringComparison na hodnotu Ordinal ani na hodnotu OrdinalIgnoreCase. Explicitním nastavením parametru na hodnotu StringComparison.Ordinal nebo StringComparison.OrdinalIgnoreCase dojde ke zrychlení kódu a zvýšení přesnosti a spolehlivosti. |
| CA1310 | [CA1310: Zadejte StringComparison pro správnost](../code-quality/ca1310.md) | Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison a ve výchozím nastavení používá porovnávání řetězců specifické pro jazykovou verzi. |
| CA1401 | [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401.md) | Veřejná nebo chráněná metoda ve veřejném typu má atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Tyto metody by neměly být vystaveny. |
| CA1417 | [CA1417: Nepoužívejte pro `OutAttribute` řetězcové parametry pro volání nespravovaného volání.](../code-quality/ca1417.md) | Řetězcové parametry předávané hodnotou s `OutAttribute` může destabilizovat modul runtime, pokud je řetězec interně řetězec. |
| CA1501 | [CA1501: Vyhněte se nadměrné dědičnosti](../code-quality/ca1501.md) | Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti. Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. |
| CA1502 | [CA1502: Vyhněte se nadměrné složitosti](../code-quality/ca1502.md) | Toto pravidlo měří počet lineárně nezávislých cest skrze metodu, což je určeno počtem a složitostí podmínkových větví. |
| CA1505 | [CA1505: Vyhněte se neudržovatelnému kódu](../code-quality/ca1505.md) | Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti. Nízký index udržovatelnosti označuje, že typ nebo metodu je pravděpodobně obtížné udržovat a je vhodné ji znovu navrhnout. |
| CA1506 | [CA1506: Vyhněte se nadměrnému párování tříd](../code-quality/ca1506.md) | Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje. |
| CA1507 | [CA1507: Místo řetězce použijte výraz nameof.](../code-quality/ca1507.md) | Řetězcový literál se používá jako argument, ve kterém `nameof` by se mohl použít výraz. |
| CA1508 | [CA1508: Vyhněte se mrtvému podmíněnému kódu](../code-quality/ca1508.md) | Metoda má podmíněný kód, který se vždy vyhodnocuje `true` za `false` běhu nebo za běhu. To vede k nedoručenému kódu ve `false` větvi podmínky. |
| CA1509 | [CA1509: Neplatná položka v souboru konfigurace metrik kódu](../code-quality/ca1509.md) | Pravidla metrik kódu, například [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) a [CA1506](ca1506.md), dodaly konfigurační soubor s názvem `CodeMetricsConfig.txt` , který má neplatnou položku. |
| CA1700 | [CA1700: Nepojmenovávejte výčty hodnot 'Reserved'](../code-quality/ca1700.md) | Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. |
| CA1707 | [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707.md) | Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry. |
| CA1708 | [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708.md) | Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena. |
| CA1710 | [CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710.md) |Podle konvence by měly názvy typů, které rozšiřují některé základní typy nebo určitá rozhraní, nebo typů odvozených z těchto typů mít příponu přidruženou těmto typům nebo rozhraním. |
| CA1711 | [CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711.md) | Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony. |
| CA1712 | [CA1712: Nezačínejte hodnoty výčtu názvem typu](../code-quality/ca1712.md) | Názvy členů výčtu nemají předponu názvu typu, protože se očekává, že vývojové nástroje poskytují informace o typu. |
| CA1713 | [CA1713: Události by neměly mít předponu před nebo po](../code-quality/ca1713.md) | Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí. |
| CA1714 | [CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714.md) | Veřejný výčet má atribut System.FlagsAttribute a jeho název nekončí písmenem „s“. Typy označené pomocí atributu FlagsAttribute mají názvy, které jsou v množném čísle, protože tento atribut označuje, že lze zadat více než jednu hodnotu. |
| CA1715 | [CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715.md) | Název externě viditelného rozhraní nezačíná velkým písmenem „I“. Název parametru obecného typu u externě viditelného typu nebo metody nezačíná velkým písmenem „T“. |
| CA1716 | [CA1716: Identifikátory by se neměly shodovat s klíčovými slovy](../code-quality/ca1716.md) | Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime). |
| CA1717 | [CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle](../code-quality/ca1717.md) | Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu. |
| CA1720 |[CA1720: Identifikátory by neměly obsahovat názvy typů](../code-quality/ca1720.md) | Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka. |
| CA1721 | [CA1721: Názvy vlastností by se neměly shodovat s metodami Get](../code-quality/ca1721.md) |Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce. |
| CA1724 | [CA1724: Názvy typů by se neměly shodovat s obory názvů](../code-quality/ca1724.md) | Názvy typů by neměly odpovídat názvům oborů názvů .NET. Porušení tohoto pravidla může snížit použitelnost knihovny. |
| CA1725 | [CA1725: Názvy parametrů by měly odpovídat základní deklaraci](../code-quality/ca1725.md) | Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody. |
| CA1801 | [CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801.md) | Podpis metody obsahuje parametr, který není použit v těle metody. |
| CA1802 |[CA1802: Použijte literály, kde je to vhodné](../code-quality/ca1802.md) |Pole je deklarováno jako static a jen pro čtení (Shared a ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) a je inicializováno pomocí hodnoty, která je v době kompilace Compute. Vzhledem k tomu, že hodnota, která je přiřazena cílovému poli je COMPUTE v době kompilace, změňte deklaraci na pole const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ), aby se hodnota vypočítala v době kompilace místo v době běhu. |
| CA1805 | [CA1805: Nepoužívejte inicializaci zbytečně](../code-quality/ca1805.md) | Modul runtime .NET inicializuje všechna pole odkazových typů na jejich výchozí hodnoty před spuštěním konstruktoru. Ve většině případů je explicitní inicializace pole na jeho výchozí hodnotu redundantní, což zvyšuje náklady na údržbu a může snížit výkon (například se zvýšenou velikostí sestavení). |
| CA1806 | [CA1806: Neignorujte výsledky metody](../code-quality/ca1806.md) | Nový objekt je vytvořen, ale nikdy se nepoužije, nebo je zavolána metoda, která vytvoří a vrátí nový řetězec a ten se nikdy nepoužije, nebo metoda modulu COM nebo P/Invoke vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužije. |
| CA1810 | [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810.md) | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
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
| CA1826 |[CA1826: Použijte vlastnost namísto vyčíslitelné metody Linq](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> Metoda LINQ byla použita pro typ, který podporuje ekvivalentní, efektivnější vlastnost. |
| CA1827 |[CA1827: Nepoužívejte Count/LongCount, když se dá použít Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.LongCount%2A> se použila metoda, kde <xref:System.Linq.Enumerable.Any%2A> by byla metoda efektivnější. |
| CA1828 |[CA1828: Nepoužívejte CountAsync/LongCount, když se dá použít AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> nebo <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> se použila metoda, kde <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> by byla metoda efektivnější. |
| CA1829 |[CA1829: Použijte vlastnost Length/Count místo metody Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> Metoda LINQ byla použita pro typ, který podporuje ekvivalentní, efektivnější `Length` nebo `Count` vlastnost. |
| CA1830 |[CA1830: Upřednostňovat pro StringBuilder přetížení metod Append a Insert silného typu](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> a <xref:System.Text.StringBuilder.Insert%2A> Poskytněte přetížení pro více typů mimo <xref:System.String> .  Pokud je to možné, preferovat přetížení silného typu přes použití rozhraní ToString () a přetížení založeného na řetězci. |
| CA1831 |[CA1831: Tam, kde je to možné, používat u řetězců místo indexerů založených na rozsahu metodu AsSpan](../code-quality/ca1831.md) | Při použití rozsahu indexeru na řetězec a implicitně přiřadí hodnotu ReadOnlySpan &lt; &gt; typu char, metoda <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> bude použita místo <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části řetězce. |
| CA1832 |[CA1832: Pro získání části ReadOnlySpan nebo ReadOnlyMemory pole používat místo indexerů založených na rozsahu metodu AsSpan nebo AsMemory](../code-quality/ca1832.md) | Při použití rozsahu indexeru v poli a implicitně přiřadí hodnotu <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> typu nebo, bude <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> použita metoda namísto <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části pole. |
| CA1833 |[CA1833: Pro získání části Span nebo Memory pole používat místo indexerů založených na rozsahu metodu AsSpan nebo AsMemory](../code-quality/ca1833.md) | Při použití rozsahu indexeru v poli a implicitně přiřadí hodnotu <xref:System.Span%601> <xref:System.Memory%601> typu nebo, bude <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> použita metoda namísto <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části pole. |
| CA1834 |[CA1834: Pro jednoznakové řetězce používat metodu StringBuilder.Append(char)](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> má `Append` přetížení, které přijímá `char` jako svůj argument. Preferovat volání `char` přetížení z důvodů výkonu. |
| CA1835 |[CA1835: preferovat přetížení založené na Memory' pro ReadAsync a WriteAsync](../code-quality/ca1835.md) | ' Stream ' má přetížení ' ReadAsync ', které jako první argument přebírá ' paměť &lt; Byte &gt; ' a přetížení ' WriteAsync ', které jako první argument přebírá ' &lt; ReadOnlyMemory byte &gt; '. Preferovat volání přetížení založeného na paměti, což je efektivnější. |
| CA1836 |[CA1836: preferovat více, je- `IsEmpty` `Count` li k dispozici](../code-quality/ca1836.md) | Preferovat `IsEmpty` vlastnost, která je efektivnější než `Count` , `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> nebo <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> k určení, zda objekt obsahuje nebo neobsahuje žádné položky. |
| CA1837 | [CA1837: použijte `Environment.ProcessId` místo `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` je jednodušší a rychlejší než `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: Vyhněte se `StringBuilder` parametrům pro volání nespravovaného volání](../code-quality/ca1838.md) | Zařazování ' StringBuilder ' vždy vytvoří nativní kopii vyrovnávací paměti, což vede k vícenásobnému přidělení pro jednu operaci zařazování. |
| CA2000 | [CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000.md) | Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah. |
| CA2002 |[CA2002: Nepoužívejte zámky u objektů se slabou identitou](../code-quality/ca2002.md) |Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt. |
| CA2007 | [CA2007: Nečekejte přímo na úlohu](ca2007.md) | Asynchronní metoda [čeká](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> přímo. Když asynchronní metoda čeká <xref:System.Threading.Tasks.Task> přímo, pokračování probíhá ve stejném vláknu, které úlohu vytvořilo. Toto chování může být nákladné v souvislosti s výkonem a může způsobit zablokování ve vlákně uživatelského rozhraní. Zvažte volání <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> , abyste vyvolali svůj záměr na pokračování. |
| CA2008 | [CA2008: Nevytvářejte úlohy bez předání Plánovače úloh](ca2008.md) | Operace vytvoření nebo pokračování úlohy používá přetížení metody, které neurčuje <xref:System.Threading.Tasks.TaskScheduler> parametr. |
| CA2009 | [CA2009: Nevolejte ToImmutableCollection pro hodnotu ImmutableCollection](ca2009.md) | `ToImmutable` Metoda byla nutně volána pro neproměnlivou kolekci z <xref:System.Collections.Immutable> oboru názvů. |
| CA2011 | [CA2011: Nepřiřazujte vlastnost v rámci její metody setter](ca2011.md) | Vlastnost byla omylem přiřazena hodnota v rámci vlastního [přístupového objektu set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| CA2012 | [CA2012: Správně použít hodnoty ValueTask](ca2012.md) | ValueTasks vrácené z vyvolání členů mají být přímo očekávány.  Pokusí se využít ValueTask vícekrát nebo získat přímý přístup k jednomu výsledku před tím, než je známý k dokončení, může způsobit výjimku nebo poškození.  Ignorování takového ValueTask je pravděpodobně indikace funkční chyby a může snížit výkon. |
| CA2013 | [CA2013: Nepoužívejte ReferenceEquals s typy hodnot](ca2013.md) | Při porovnávání hodnot pomocí <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , jsou-li objA a objB typy hodnot, jsou zabaleny před předáním do <xref:System.Object.ReferenceEquals%2A> metody. To znamená, že i když obě objA a objB reprezentují stejnou instanci typu hodnoty, <xref:System.Object.ReferenceEquals%2A> metoda ale přesto vrátí hodnotu false. |
| CA2014 | [CA2014: Nepoužívejte stackalloc ve smyčce.](ca2014.md) | Prostor zásobníku přidělený stackalloc je vydaný jenom na konci vyvolání aktuální metody.  Použití ve smyčce může mít za následek neohraničený nárůst zásobníku a případné podmínky přetečení zásobníku. |
| CA2015 | [CA2015: nedefinujte finalizační metody pro typy odvozené z MemoryManager &lt; T&gt;](ca2015.md) | Přidání finalizační metody do typu odvozeného z <xref:System.Buffers.MemoryManager%601> může umožnit uvolnění paměti, pokud je stále používána <xref:System.Span%601> . |
| CA2016 | [CA2016: Přeposlat parametr CancellationToken metodám, které ho přijmou](ca2016.md) | Předejte `CancellationToken` parametr do metod, které jednu z nich přebírají, aby se zajistilo, že oznámení o zrušení operace budou správně šířena, nebo jestli se má explicitně předat označení, že se `CancellationToken.None` token nešíří. |
| CA2100 | [CA2100: Zkontrolujte chyby zabezpečení u dotazů SQL](../code-quality/ca2100.md) | Metoda nastavuje vlastnost System.Data.IDbCommand.CommandText pomocí řetězce, který je sestaven z řetězcového argumentu k metodě. Toto pravidlo předpokládá, že řetězcový argument obsahuje vstup uživatele. Řetězec příkazu SQL sestavený ze vstupu uživatele je ohrožen útoky prostřednictvím injektáže SQL. |
| CA2101 |[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného voláním](../code-quality/ca2101.md) | Člen vyvolání platformy povoluje částečně důvěryhodné volající, má řetězcový parametr a explicitně nezařazuje řetězec. To může způsobit potenciální ohrožení zabezpečení. |
| CA2109 | [CA2109: Zkontrolujte viditelné obslužné rutiny událostí](../code-quality/ca2109.md) | Byla zjištěna veřejná nebo chráněná metoda zpracování událostí. Metody zpracování událostí by neměly být vystaveny, pokud to není nezbytně nutné. |
| CA2119 | [CA2119: Zapečeťte metody, které vyhovují privátním rozhraním](../code-quality/ca2119.md) | Dědičný veřejný typ poskytuje implementaci přepsatelné metody interního (Friend v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) rozhraní. Chcete-li opravit porušení tohoto pravidla, zabraňte přepsání metody mimo sestavení. |
| CA2153 |[CA2153: Vyhněte se zpracování výjimek poškozených stavů](../code-quality/ca2153.md) | Poškozené výjimky stavu (rozšíření) označují, že v procesu existuje poškození paměti. Pokud by útočník mohl zneužít do poškozené oblasti paměti, může to místo toho zachytit, než umožní selhání procesu způsobit chyby zabezpečení. |
| CA2200 | [CA2200: Znovu vyvolejte pro zachování podrobností zásobníku](../code-quality/ca2200.md) | Výjimka je znovu vyvolána a je jednoznačně uvedena v příkazu throw. Jestliže je výjimka znovu vyvolána zadáním výjimky v příkazu throw, seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztracen. |
| CA2201 | [CA2201: Nevyvolávejte vyhrazené typy výjimek](../code-quality/ca2201.md) | Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2207 | [CA2207: Inicializujte statická pole s typem hodnoty vloženě](../code-quality/ca2207.md) | Hodnotový typ deklaruje explicitní statický konstruktor. Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte. |
| CA2208 |[CA2208: Vytvořte správně instance výjimky argumentu](../code-quality/ca2208.md) | Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je typu ArgumentException nebo je z něj odvozena, nebo je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, která je typu ArgumentException nebo je z něj odvozena. |
| CA2211 |[CA2211: Nekonstantní pole by neměla být viditelná](../code-quality/ca2211.md) | Statická pole, která nejsou konstantami ani nejsou jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy. |
| CA2213 | [CA2213: Uvolnitelná pole by měla být uvolněna](../code-quality/ca2213.md) | Typ implementující rozhraní System.IDisposable deklaruje typy polí, které také implementují rozhraní IDisposable. Metoda pole Dispose není volána pomocí metody Dispose deklarujícího typu. |
| CA2214 | [CA2214: Nevolejte přepisovatelné metody v konstruktorech](../code-quality/ca2214.md) | Při volání virtuální metody konstruktorem nemusí být konstruktor instance, která volá tuto metodu, proveden. |
| CA2215 | [CA2215: Metody Dispose by měly volat uvolnění základní třídy](../code-quality/ca2215.md) | Pokud typ dědí z uvolnitelného typu, musí volat metodu Dispose ze základního typu v rámci své vlastní metody Dispose. |
| CA2216 |[CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216.md) | Typ, který implementuje rozhraní System.IDisposable a obsahuje pole, která navrhují použití nespravovaných prostředků, neimplementuje finalizační metodu, jak je popsáno metodou Object.Finalize. |
| CA2217 | [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217.md) |Externě viditelný výčet je označen atributem FlagsAttribute a má jednu nebo více hodnot, které nejsou mocninami dvou nebo kombinací jiných definovaných hodnot výčtu. |
| CA2219 | [CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219.md) | Když je výjimka vyvolána v klauzuli finally nebo fault, je případná aktivní výjimka překryta novou výjimkou. Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí. Díky tomu je obtížné rozpoznat a ladit původní chybu. |
| CA2225 | [CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225.md) |Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích nepodporujících přetížené operátory. |
| CA2226 | [CA2226: Operátory by měly mít symetrická přetížení](../code-quality/ca2226.md) | Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor. |
| CA2227 |[CA2227: Vlastnosti kolekce by měly být pouze pro čtení](../code-quality/ca2227.md) |Zapisovatelná vlastnost kolekce umožňuje uživateli nahradit kolekci jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy. |
| CA2229 | [CA2229: Implementujte serializační konstruktory](../code-quality/ca2229.md) | Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. |
| CA2231 | [CA2231: Přetižte operátor rovnosti při přetížení ValueType.Equals](../code-quality/ca2231.md) | Hodnotový typ přepisuje metodu Object.Equals, ale neimplementuje operátor rovnosti. |
| CA2234 | [CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234.md) | Je provedeno volání metody, která má řetězcový parametr, jehož název obsahuje „uri“, „URI“, „urn“, „URN“, „url“ nebo „URL“. Typ deklarující metodu obsahuje odpovídající přetížení metody, která má parametr typu System.Uri. |
| CA2235 | [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235.md) | Neserializovatelný typ pole instance je deklarován v serializovatelném typu. |
| CA2237 | [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237.md) | Aby byl typ rozpoznán modulem CLR (Common Language Runtime) jako serializovatelný, musí být označen pomocí atributu SerializableAttribute, i když typ používá vlastní rutinu serializace prostřednictvím implementace rozhraní ISerializable. |
| CA2241 | [CA2241: Zadejte správné argumenty pro metody formátování](../code-quality/ca2241.md) | Formátovací argument, který je předán metodě System.String.Format, neobsahuje formátovací položku, která odpovídá každému argumentu objektu nebo naopak. |
| CA2242 |[CA2242: Testujte správně NaN](../code-quality/ca2242.md) | Tento výraz testuje hodnotu proti metodě Single.Nan nebo Double.Nan. Chcete-li tuto hodnotu otestovat, použijte metodu Single.IsNan(Single) nebo Double.IsNan(Double). |
| CA2243 |[CA2243: Řetězcové literály atributů by se měly správně parsovat](../code-quality/ca2243.md) | Parametr řetězcového literálu atributu nesprávně analyzuje adresu URL, identifikátor GUID nebo verzi. |
| CA2244 | [CA2244: Neduplikujte inicializace indexovaných elementů.](../code-quality/ca2244.md) | Inicializátor objektu má více než jeden inicializátor indexovaného elementu se stejným indexem konstanty. Všechny kromě posledního inicializátoru jsou redundantní. |
| CA2245 | [CA2245: Nepřiřazujte vlastnost k ní samotné.](../code-quality/ca2245.md) | Vlastnost byla omylem přiřazena sama sobě. |
| CA2246 | [CA2246: Nepřiřazujte symbol a jeho člena v témže příkazu.](../code-quality/ca2246.md) | Přiřazení symbolu a jeho členu, tedy pole nebo vlastnost, ve stejném příkazu není doporučeno. Není jasné, jestli má členský přístup za cíl použít starou hodnotu symbolu před přiřazením nebo novou hodnotou z přiřazení v tomto prohlášení. |
| CA2247 | [CA2247: argument předaný konstruktoru TaskCompletionSource by měl být parametr TaskCreationOptions enum namísto typ TaskContinuationOptions Enum.](../code-quality/ca2247.md) | TaskCompletionSource má konstruktory, které přijímají parametr TaskCreationOptions, které ovládají podkladovou úlohu a konstruktory, které přijímají stav objektu, který je uložen v úloze.  Náhodné předání typ TaskContinuationOptions namísto parametr TaskCreationOptions způsobí, že volání zpracuje možnosti jako stav. |
| CA2248 | [CA2248: Poskytněte prosím do Enum.HasFlag správný argument enum](../code-quality/ca2248.md) | Typ výčtu předaný jako argument pro `HasFlag` volání metody se liší od volajícího typu výčtu. |
| CA2249 | [CA2249: Zvážit možnost místo string.IndexOf použít string.Contains](../code-quality/ca2249.md) | Volání na `string.IndexOf` místo, kde je použit výsledek pro kontrolu přítomnosti nebo absence podřetězce, může být nahrazena `string.Contains` . |
| CA2300 | [CA2300: Nepoužívat nezabezpečený deserializátor BinaryFormatter](../code-quality/ca2300.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2301 | [CA2301: Nevolat BinaryFormatter.Deserialize dříve, než se nastaví BinaryFormatter.Binder](../code-quality/ca2301.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2302 | [CA2302: Než zavoláte BinaryFormatter.Deserialize, ujistěte se, že je nastavený BinaryFormatter.Binder](../code-quality/ca2302.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2305 | [CA2305: Nepoužívat nezabezpečený deserializátor LosFormatter](../code-quality/ca2305.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2310 | [CA2310: Nepoužívat nezabezpečený deserializátor NetDataContractSerializer](../code-quality/ca2310.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2311 | [CA2311: Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder](../code-quality/ca2311.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2312 | [CA2312: Před deserializací se ujistěte, že je nastavený NetDataContractSerializer.Binder](../code-quality/ca2312.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2315 | [CA2315: Nepoužívat nezabezpečený deserializátor ObjectStateFormatter](../code-quality/ca2315.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2321 | [CA2321: Nedeserializovat se třídou JavaScriptSerializer pomocí třídy SimpleTypeResolver](../code-quality/ca2321.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2322 | [CA2322: Před deserializaci se ujistěte se, že třída JavaScriptSerializer není inicializována pomocí třídy SimpleTypeResolver](../code-quality/ca2322.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2326 | [CA2326: Nepoužívejte jiné hodnoty TypeNameHandling než None](../code-quality/ca2326.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2327 | [CA2327: Nepoužívejte nezabezpečená nastavení JsonSerializerSettings](../code-quality/ca2327.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2328 | [CA2328: Ujistěte se, že nastavení JsonSerializerSettings jsou zabezpečená](../code-quality/ca2328.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2329 | [CA2329: Nepoužívejte s JsonSerializer deserializaci pomocí nezabezpečené konfigurace](../code-quality/ca2329.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2330 | [CA2330: Ujistěte se, že JsonSerializer má při deserializaci zabezpečenou konfiguraci](../code-quality/ca2330.md) | Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. |
| CA2350 | [CA2350: Ujistěte se, že vstup pro DataTable.ReadXml() je důvěryhodný](ca2350.md) | Při deserializaci a <xref:System.Data.DataTable> s nedůvěryhodným vstupem může útočník vytvořit útok se zlými úmysly, aby provedl útok na dostupnost služby. Může dojít k neznámému ohrožení vzdáleného spuštění kódu. |
| CA2351 | [CA2351: Ujistěte se, že vstup pro DataSet.ReadXml() je důvěryhodný](ca2351.md) | Při deserializaci a <xref:System.Data.DataSet> s nedůvěryhodným vstupem může útočník vytvořit útok se zlými úmysly, aby provedl útok na dostupnost služby. Může dojít k neznámému ohrožení vzdáleného spuštění kódu. |
| CA2352 | [CA2352: Nezabezpečená datová sada nebo datová tabulka serializovatelného typu může být zranitelná vůči útokům vzdáleného spuštění kódu](ca2352.md) | Třída nebo struktura označená <xref:System.SerializableAttribute> obsahující <xref:System.Data.DataSet> <xref:System.Data.DataTable> pole nebo vlastnost nebo a nemá <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: Nezabezpečená datová sada nebo datová tabulka serializovatelného typu](ca2353.md) | Třída nebo struktura označená atributem serializace XML nebo atributem kontraktu dat obsahuje <xref:System.Data.DataSet> <xref:System.Data.DataTable> pole nebo vlastnost. |
| CA2354 | [CA2354: Nezabezpečená datová sada nebo datová tabulka v grafu deserializovaných objektů může být zranitelná vůči útoku vzdáleného spuštění kódu](ca2354.md) | Deserializace pomocí <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> serializovaného objektu a grafu objektů přetypování typu může obsahovat <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: Nezabezpečená datová sada nebo datová tabulka v grafu deserializovaných objektů](ca2355.md) | Deserializace v případě, že graf objektu přetypování nebo zadaného typu může obsahovat <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: nezabezpečená datová sada nebo DataTable ve webovém deserializovaném objektu grafu](ca2356.md) | Metoda s <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> parametrem nebo má parametr, který může odkazovat na <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: Zajistěte, aby se automaticky vygenerovaná třída obsahující DataSet.ReadXml() nepoužívala s nedůvěryhodnými daty.](ca2361.md) | Při deserializaci a <xref:System.Data.DataSet> s nedůvěryhodným vstupem může útočník vytvořit útok se zlými úmysly, aby provedl útok na dostupnost služby. Může dojít k neznámému ohrožení vzdáleného spuštění kódu. |
| CA2362 | [CA2362: Nezabezpečená datová sada nebo datová tabulka v automaticky vygenerovaném serializovatelném typu může být zranitelná vůči útokům vzdáleného spuštění kódu.](ca2362.md) | Při deserializaci nedůvěryhodného vstupu pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a deserializovaný graf objektu obsahuje <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> může útočník vytvořit škodlivý datový prvek, který provede útok na vzdálené spuštění kódu. |
| CA3001 | [CA3001: Zkontrolujte ohrožení zabezpečení injektáží SQL v kódu](../code-quality/ca3001.md) | Při práci s nedůvěryhodnými vstupy a příkazy SQL Zajistěte útokům prostřednictvím injektáže SQL. Útok na injektáže SQL může spouštět škodlivé příkazy SQL a ohrozit tak zabezpečení a integritu vaší aplikace. |
| CA3002 | [CA3002: Zkontrolujte ohrožení zabezpečení proti XSS v kódu](../code-quality/ca3002.md) | Při práci s nedůvěryhodným vstupem z webových požadavků zajistěte útoky skriptování XSS (mezi weby). Útok XSS vloží nedůvěryhodný vstup do nezpracovaného výstupu HTML a umožní útočníkovi spustit škodlivé skripty nebo škodlivým způsobem upravovat obsah na webové stránce. |
| CA3003 | [CA3003: Zkontrolujte ohrožení zabezpečení injektáží cesty k souboru v kódu](../code-quality/ca3003.md) | Při práci s nedůvěryhodným vstupem z webových požadavků nezapomeňte při zadávání cest k souborům použít vstup, který je řízený uživatelem. |
| CA3004 | [CA3004: Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu](../code-quality/ca3004.md) | Vydávání informací o výjimce poskytne útočníkům přehled o vnitřních verzích vaší aplikace, které můžou útočníkům pomoci najít další ohrožení zabezpečení pro zneužití. |
| CA3006 | [CA3006: Zkontrolujte ohrožení zabezpečení injektáží příkazu procesu v kódu](../code-quality/ca3006.md) | Při práci s nedůvěryhodným vstupem se zaměříte na útoky vkládání příkazů. Útok injektáže příkazu může spustit škodlivé příkazy v podkladovém operačním systému a ohrozit tak zabezpečení a integritu serveru. |
| CA3007 | [CA3007: Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu](../code-quality/ca3007.md) | Při práci s nedůvěryhodným vstupem nezapomeňte na otevřené chyby zabezpečení přesměrování. Útočník může zneužít otevřenou chybu zabezpečení přesměrování pro použití vašeho webu k poskytnutí vzhledu legitimní adresy URL, ale přesměruje nepodezřelého návštěvníka na podvodný nebo jinou škodlivou webovou stránku. |
| CA3008 | [CA3008: Zkontrolujte ohrožení zabezpečení injektáží XPath v kódu](../code-quality/ca3008.md) | Při práci s nedůvěryhodným vstupem si vědomete útoků prostřednictvím injektáže XPath. Vytváření dotazů XPath pomocí nedůvěryhodného vstupu může útočníkovi umožnit škodlivým způsobem manipulovat s dotazem, aby vrátil nezamýšlený výsledek a případně vyzradit obsah dotazovaného XML. |
| CA3009 | [CA3009: Zkontrolujte ohrožení zabezpečení injektáží XML v kódu](../code-quality/ca3009.md) | Při práci s nedůvěryhodným vstupem nezapomeňte na útoky prostřednictvím injektáže XML. |
| CA3010 | [CA3010: Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu](../code-quality/ca3010.md) | Při práci s nedůvěryhodným vstupem si vědomete útoků prostřednictvím injektáže XAML. XAML je jazyk značek, který přímo představuje instanci objektu a provádění. To znamená, že prvky vytvořené v jazyce XAML mohou pracovat se systémovými prostředky (například síťový přístup a vstupně-výstupní operace systému souborů). |
| CA3011 | [CA3011: Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu](../code-quality/ca3011.md) | Při práci s nedůvěryhodným vstupem nezapomeňte načíst nedůvěryhodný kód. Pokud vaše webová aplikace načte nedůvěryhodný kód, útočník může být schopen vložit do procesu škodlivé knihovny DLL a spustit škodlivý kód. |
| CA3012 | [CA3012: Zkontrolujte ohrožení zabezpečení injektáží regulárního výrazu v kódu](../code-quality/ca3012.md) | Při práci s nedůvěryhodným vstupem nezapomeňte na útoky pomocí injektáže regulárního výrazu. Útočník může použít injektáže regulárního výrazu pro zlomyslnou úpravu regulárního výrazu, aby regulární výraz odpovídal nezamýšleným výsledkům, nebo aby regulární výraz využil nadměrného využití procesoru, což způsobuje útok na útok DOS. |
| CA3061 | [CA3061: Nepřidávat schéma podle adresy URL](../code-quality/ca3061.md) | Nepoužívejte nezabezpečené přetížení metody Add, protože by mohlo dojít k nebezpečným externím odkazům. |
| CA3075 | [CA3075: Zpracování nezabezpečené specifikace DTD](../code-quality/ca3075.md) | Pokud používáte nezabezpečené instance DTDProcessing nebo odkazujete na zdroje externích entit, může analyzátor přijmout nedůvěryhodné vstupní a únik citlivých informací útočníkům. |
| CA3076 | [CA3076: Spuštění nezabezpečeného skriptu XSLT](../code-quality/ca3076.md) | Pokud v aplikacích .NET nezabezpečeně vykonáte Extensible Stylesheet Language Transformers (XSLT), může procesor vyřešit nedůvěryhodné odkazy identifikátorů URI, které by mohly zveřejnit citlivé informace pro útočníky, což vede k odepření útoků služby a mezi weby. |
| CA3077 | [CA3077: Nezabezpečené zpracování v návrhu rozhraní API, dokumentu XML a čtečce textu XML](../code-quality/ca3077.md) | Při navrhování rozhraní API odvozeného z XMLDocument a XMLTextReader nezapomeňte na DtdProcessing. Použití nezabezpečených instancí DTDProcessing při odkazování na zdroje externích entit nebo jejich překládání na nezabezpečené hodnoty v XML může vést k odhalení informací. |
| CA3147 | [CA3147: Označte obslužné rutiny příkazů pomocí ValidateAntiForgeryToken](../code-quality/ca3147.md) | Při navrhování kontroleru ASP.NET MVC si zajistěte útoky proti falšování požadavků mezi lokalitami. Útok proti padělání žádostí mezi servery může odesílat škodlivé požadavky od ověřeného uživatele do kontroleru ASP.NET MVC. |
| CA5350 | [CA5350: Nepoužívejte slabé kryptografické algoritmy](../code-quality/ca5350.md) | Slabé šifrovací algoritmy a funkce hash jsou dnes používány z mnoha důvodů, ale neměly by se používat k zajištění důvěrnosti nebo integrity dat, která chrání. Toto pravidlo se aktivuje, když v kódu nalezne algoritmy TripleDES, SHA1 nebo RIPEMD160.|
| CA5351 | [CA5351: Nepoužívejte poškozené kryptografické algoritmy](../code-quality/ca5351.md) | Nefunkční kryptografické algoritmy nejsou považovány za zabezpečené a jejich použití by se mělo důrazně nedoporučuje. Toto pravidlo se aktivuje, když nalezne algoritmus hash MD5 nebo šifrovací algoritmy DES nebo RC2 v kódu. |
| CA5358 | [CA5358: Nepoužívat nezabezpečené režimy šifrování](../code-quality/ca5358.md) | Nepoužívat nezabezpečené režimy šifrování |
| CA5359 | [CA5359 Nezakázat ověřování certifikátu](../code-quality/ca5359.md) | Certifikát může pomáhat ověřit identitu serveru. Klienti by měli ověřit certifikát serveru, aby se zajistilo, že se požadavky odesílají na určený server. Pokud se ServerCertificateValidationCallback vždycky vrátí `true` , certifikát se předá ověření. |
| CA5360 | [CA5360 nevolá nebezpečné metody v deserializaci.](../code-quality/ca5360.md) | Nezabezpečená deserializace je ohrožení zabezpečení, ke kterému dochází, pokud se nedůvěryhodná data používají k zneužití logiky aplikace, což způsobuje útok DoS (Denial of Service), nebo dokonce spouštějí libovolný kód, který je deserializován. Je často možné, že uživatelé se zlými úmysly můžou tyto funkce deserializace zneužít, když aplikace deserializace nedůvěryhodných dat, která jsou pod jejich ovládacími prvky. Konkrétně volejte nebezpečné metody v procesu deserializace. Nezabezpečené útoky na deserializaci by mohly útočníkovi umožnit provést útoky, jako jsou útoky DoS, obcházení ověřování a vzdálené spuštění kódu. |
| CA5361 | [CA5361: nepovolujte použití Schannel silného šifrování.](../code-quality/ca5361.md) | Nastavení `Switch.System.Net.DontEnableSchUseStrongCrypto` pro `true` oslabení kryptografie používané v odchozích připojeních TLS (Transport Layer Security). Slabší kryptografie může ohrozit důvěrnost komunikace mezi vaší aplikací a serverem, což usnadňuje útočníkům eavesdrop citlivá data. |
| CA5362 | [CA5362 potenciální cyklus odkazů v deserializovaném grafu objektů](../code-quality/ca5362.md) | Pokud dojde k deserializaci nedůvěryhodných dat, pak jakékoli zpracování deserializovaného objektu graf musí zpracovávat cykly odkazů, aniž by se museli přecházet do nekonečné smyčky. To zahrnuje kód, který je součástí zpětného volání deserializace, a kódu, který zpracovává graf objektu po deserializaci dokončeno. V opačném případě by útočník mohl provést útok DOS se škodlivými daty obsahujícími cyklický odkaz. |
| CA5363 | [CA5363: Nezakazovat ověřování požadavků](../code-quality/ca5363.md) | Ověření žádosti je funkce v ASP.NET, která prověřuje požadavky HTTP a určuje, jestli obsahují potenciálně nebezpečný obsah, který může vést k útokům prostřednictvím injektáže, včetně skriptování mezi weby. |
| CA5364 | [CA5364: Nepoužívejte zastaralé protokoly zabezpečení](../code-quality/ca5364.md) | Protokol TLS (Transport Layer Security) zabezpečuje komunikaci mezi počítači, nejčastěji s protokolem HTTPS (Hypertext Transfer Protocol Secure). Starší verze protokolu TLS jsou méně bezpečné než TLS 1,2 a TLS 1,3 a je pravděpodobnější, že dojde k novým chybám zabezpečení. Nepoužívejte starší verze protokolu pro minimalizaci rizik. |
| CA5365 | [CA5365 Nezakázat kontrolu hlaviček protokolu HTTP](../code-quality/ca5365.md) | Kontrola hlaviček protokolu HTTP umožňuje kódování návratových znaků a znaků nového řádku, \r a \n, které se nacházejí v hlavičkách odpovědí. Toto kódování může pomáhat zabránit útokům prostřednictvím injektáže, které využívají aplikaci, která vrací nedůvěryhodná data obsažená v hlavičce. |
| CA5366 | [CA5366 použít XmlReader pro čtení XML pro datovou sadu](../code-quality/ca5366.md) | Použití <xref:System.Data.DataSet> metody ke čtení XML s nedůvěryhodnými daty může načítat nebezpečné externí odkazy, které by měly být omezeny pomocí <xref:System.Xml.XmlReader> zabezpečeného překladače nebo se zakázaným zpracováním DTD. |
| CA5367 | [CA5367 neserializovat typy s poli ukazatelů](../code-quality/ca5367.md) | Toto pravidlo kontroluje, zda existuje serializovatelný třída s polem nebo vlastností s ukazatelem. Členy, které nemohou být serializovány, mohou být ukazatel, jako jsou například statické členy nebo pole s označením <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 sada ViewStateUserKey pro třídy odvozené ze stránky](../code-quality/ca5368.md) | Nastavení <xref:System.Web.UI.Page.ViewStateUserKey> vlastnosti vám může pomáhat zabránit útokům na aplikaci tím, že vám umožní přiřadit identifikátor k proměnné stavu zobrazení pro jednotlivé uživatele, aby útočníci nemohli použít tuto proměnnou k vygenerování útoku. V opačném případě dojde k ohrožení zabezpečení pro padělání požadavků mezi weby. |
| CA5369 | [CA5369: Použít XmlReader pro Deserialize](../code-quality/ca5369.md) | Zpracování nedůvěryhodných schémat DTD a XML může povolit načítání nebezpečných externích odkazů, které by měly být omezeny pomocí objektu XmlReader s zabezpečeným překladačem nebo se zakázaným zpracováním vloženého schématu DTD a XML. |
| CA5370 | [CA5370: Použít XmlReader pro ověřování čtečky](../code-quality/ca5370.md) | Zpracování nedůvěryhodných schémat DTD a XML může povolit načítání nebezpečných externích odkazů. Toto nebezpečné načítání může být omezeno pomocí objektu XmlReader s zabezpečeným překladačem nebo zpracováním vloženého schématu DTD a XML. |
| CA5371 | [CA5371: Použít XmlReader pro čtení schématu](../code-quality/ca5371.md) | Zpracování nedůvěryhodných schémat DTD a XML může povolit načítání nebezpečných externích odkazů. Použití objektu XmlReader s zabezpečeným překladačem nebo zpracováním vloženého schématu DTD a XML je zakázané. |
| CA5372 | [CA5372: Použít XmlReader pro XPathDocument](../code-quality/ca5372.md) | Zpracování XML z nedůvěryhodných dat může načítat nebezpečné externí odkazy, které mohou být omezeny pomocí objektu XmlReader s zabezpečeným překladačem nebo zakázaným zpracováním DTD. |
| CA5373 | [CA5373: Nepoužívat zastaralou funkci odvození klíče](../code-quality/ca5373.md) | Toto pravidlo detekuje vyvolání slabé metody odvození klíče <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> a `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> používal se slabší PBKDF1 algoritmu. |
| CA5374 | [CA5374 nepoužívá XslTransform](../code-quality/ca5374.md) | Toto pravidlo zkontroluje, zda <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> je v kódu vytvořena instance. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> je teď zastaralá a neměla by se používat. |
| CA5375 | [CA5375 nepoužívat sdílený přístupový podpis účtu](../code-quality/ca5375.md) | Podpis SAS účtu může delegovat přístup k operacím čtení, zápisu a odstraňování na kontejnerech objektů blob, tabulkách, frontách a sdíleným složkám, které nejsou u SAS služby povoleny. Nepodporuje ale zásady na úrovni kontejneru a má méně flexibilitu a kontrolu nad oprávněními, která jsou udělena. Jakmile je uživatelé se zlými úmysly obdrží, váš účet úložiště bude snadno ohrožen. |
| CA5376 | [CA5376 použít SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS je citlivá data, která se nedají přenést do prostého textu v HTTP. |
| CA5377 | [CA5377 použít zásady přístupu na úrovni kontejneru](../code-quality/ca5377.md) | Zásady přístupu na úrovni kontejneru můžete kdykoli upravit nebo odvolat. Poskytuje větší flexibilitu a kontrolu nad oprávněními, která jsou udělena. |
| CA5378 | [CA5378: Nezakazujte ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | Nastavení `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` pro `true` omezení připojení TLS (Transport Layer Security) technologie Windows Communication Framework (TLS) k použití protokolu TLS 1,0. Tato verze TLS bude zastaralá. |
| CA5379 | [CA5379 nepoužívá slabší algoritmus funkce odvození klíče.](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>Třída standardně používá <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algoritmus. Je nutné zadat algoritmus hash pro použití v některých přetíženích konstruktoru s <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> nebo vyšším. Poznámka: <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> vlastnost má pouze `get` přistupující objekt a nemá `overriden` modifikátor. |
| CA5380 | [CA5380: Nepřidávat certifikáty do kořenového úložiště](../code-quality/ca5380.md) | Toto pravidlo detekuje kód, který přidá certifikát do úložiště certifikátů důvěryhodných kořenových certifikačních autorit. Ve výchozím nastavení je úložiště certifikátů důvěryhodných kořenových certifikačních autorit nakonfigurováno se sadou veřejných certifikačních autorit, které splnily požadavky programu Microsoft Root Certificate Program. |
| CA5381 | [CA5381: Zajistit, aby se certifikáty nepřidávaly do kořenového úložiště](../code-quality/ca5381.md) | Toto pravidlo detekuje kód, který potenciálně přidá certifikát do úložiště certifikátů důvěryhodných kořenových certifikačních autorit. Ve výchozím nastavení je úložiště certifikátů důvěryhodných kořenových certifikačních autorit nakonfigurováno se sadou veřejných certifikačních autorit (CA), které splnily požadavky programu Microsoft Root Certificate Program. |
| CA5382 | [CA5382 použít zabezpečené soubory cookie v ASP.NET Core](../code-quality/ca5382.md) | Aplikace dostupné přes HTTPS musí používat zabezpečené soubory cookie, které označují prohlížeči, že by se měl soubor cookie přenést jenom pomocí SSL (Secure Sockets Layer) (SSL). |
| CA5383 | [CA5383 zajistěte, aby v ASP.NET Core používali zabezpečené soubory cookie](../code-quality/ca5383.md) | Aplikace dostupné přes HTTPS musí používat zabezpečené soubory cookie, které označují prohlížeči, že by se měl soubor cookie přenést jenom pomocí SSL (Secure Sockets Layer) (SSL). |
| CA5384 | [CA5384 nepoužívat algoritmus DSA (Digital Signature Algorithm)](../code-quality/ca5384.md) | DSA je slabý asymetrický šifrovací algoritmus. |
| CA5385 | [CA5385 použít algoritmus Rivest – Shamir – Adleman (RSA) s dostatkem velikosti klíče](../code-quality/ca5385.md) | Klíč RSA menší než 2048 bitů je zranitelnější vůči útokům hrubou silou. |
| CA5386 | [CA5386: Vyhněte se pevnému zakódování hodnoty SecurityProtocolType](../code-quality/ca5386.md) | Protokol TLS (Transport Layer Security) zabezpečuje komunikaci mezi počítači, nejčastěji s protokolem HTTPS (Hypertext Transfer Protocol Secure). Verze protokolu TLS 1,0 a TLS 1,1 jsou zastaralé, zatímco protokol TLS 1,2 a TLS 1,3 jsou aktuální. V budoucnu může být TLS 1,2 a TLS 1,3 zastaralá. Aby se zajistilo, že vaše aplikace zůstane v bezpečí, vyhněte se zakódujeme verze protokolu a cílit aspoň na 4.7.1 .NET Framework v. |
| CA5387 | [CA5387 nepoužívá slabé funkce odvození klíče s nedostatečným počtem iterací.](../code-quality/ca5387.md) | Toto pravidlo kontroluje, zda byl kryptografický klíč generován pomocí <xref:System.Security.Cryptography.Rfc2898DeriveBytes> počtu iterací menšího než 100 000. Vyšší počet iterací může přispět ke zmírnění útoků pomocí slovníků, které se pokoušejí odhadnout vygenerovaný kryptografický klíč. |
| CA5388 | [CA5388 zajistit dostatečný počet iterací při použití slabé funkce odvození klíče](../code-quality/ca5388.md) | Toto pravidlo kontroluje, zda byl kryptografický klíč generován pomocí <xref:System.Security.Cryptography.Rfc2898DeriveBytes> počtu iterací, který může být menší než 100 000. Vyšší počet iterací může přispět ke zmírnění útoků pomocí slovníků, které se pokoušejí odhadnout vygenerovaný kryptografický klíč. |
| CA5389 | [CA5389: Nepřidávat cestu položky archivace k cílové cestě systému souborů](../code-quality/ca5389.md) | Cesta k souboru může být relativní a může vést k přístupu k systému souborů mimo očekávanou cílovou cestu systému souborů, což vede ke škodlivým změnám konfigurace a ke vzdálenému spuštění kódu prostřednictvím techniky stanovení a čekání. |
| CA5390 | [CA5390 šifrovací klíč na pevný kód](../code-quality/ca5390.md) | Aby byl symetrický algoritmus úspěšný, tajný klíč musí být známý pouze pro odesílatele a příjemce. Když je klíč pevně kódovaný, je snadno zjištěn. Dokonce i u kompilovaných binárních souborů je můžete snadno extrahovat i uživatelům se zlými úmysly. Po ohrožení bezpečnosti privátního klíče může být zašifrovaný text přímo dešifrován a již není chráněn. |
| CA5391 | [CA5391 používat tokeny proti padělání v ASP.NET Core řadičích MVC](../code-quality/ca5391.md) | Zpracování `POST` požadavku, `PUT` , `PATCH` nebo `DELETE` bez ověření tokenu antipadělání může být zranitelné vůči útokům proti falšování požadavků mezi weby. Útok proti padělání žádostí mezi servery může odesílat škodlivé požadavky od ověřeného uživatele do vašeho kontroleru ASP.NET Core MVC. |
| CA5392 | [CA5392 použít atribut DefaultDllImportSearchPaths pro volání nespravovaného volání](../code-quality/ca5392.md) | Ve výchozím nastavení funkce volání nespravovaného <xref:System.Runtime.InteropServices.DllImportAttribute> testu využívají v testu počet adresářů, včetně aktuálního pracovního adresáře, který má knihovna načíst. Může se jednat o problémy zabezpečení pro určité aplikace, což vede ke zneužití knihovny DLL. |
| CA5393 | [CA5393 nepoužívá nebezpečnou DllImportSearchPath hodnotu](../code-quality/ca5393.md) | V adresářích pro hledání výchozích knihoven DLL a v adresářích sestavení může být škodlivá knihovna DLL. Nebo, v závislosti na tom, kde je aplikace spuštěná, může být v adresáři aplikace škodlivá knihovna DLL. |
| CA5394 | [CA5394 nepoužívat nezabezpečenou náhodnost](../code-quality/ca5394.md) | Použití kryptograficky slabé generátory náhodných čísel může útočníkovi umožnit předpovědět, jaká hodnota citlivá na zabezpečení bude vygenerována. |
| CA5395 | [CA5395 neúspěšných hodnotu httpVerb atributů pro metody akce](../code-quality/ca5395.md) | Všechny metody akcí, které vytvoří, upraví, odstraní nebo jinak upravují data, musí být chráněny pomocí atributu ochrany proti padělání žádostí mezi lokalitami. Operace GET by měla být bezpečná operace, která nemá žádné vedlejší účinky a neupravuje vaše trvalá data. |
| CA5396 | [CA5396 nastavit HttpOnly na true pro HttpCookie](../code-quality/ca5396.md) | V rámci hloubkové míry ochrany zajistěte, aby se soubory cookie protokolu HTTP citlivé na zabezpečení označily jako HttpOnly. To znamená, že by webový prohlížeč měl zakázat skriptům přístup k souborům cookie. Vložené škodlivé skripty představují společný způsob, jak ukrást soubory cookie. |
| CA5397 | [CA5397: Nepoužívejte zastaralé hodnoty SslProtocols](../code-quality/ca5397.md) | Protokol TLS (Transport Layer Security) zabezpečuje komunikaci mezi počítači, nejčastěji s protokolem HTTPS (Hypertext Transfer Protocol Secure). Starší verze protokolu TLS jsou méně bezpečné než TLS 1,2 a TLS 1,3 a je pravděpodobnější, že dojde k novým chybám zabezpečení. Nepoužívejte starší verze protokolu pro minimalizaci rizik. |
| CA5398 | [CA5398: Vyhněte se pevně zakódovaným hodnotám SslProtocols](../code-quality/ca5398.md) | Protokol TLS (Transport Layer Security) zabezpečuje komunikaci mezi počítači, nejčastěji s protokolem HTTPS (Hypertext Transfer Protocol Secure). Verze protokolu TLS 1,0 a TLS 1,1 jsou zastaralé, zatímco protokol TLS 1,2 a TLS 1,3 jsou aktuální. V budoucnu může být TLS 1,2 a TLS 1,3 zastaralá. Abyste měli jistotu, že vaše aplikace zůstane v bezpečí, vyhněte se zakódujeme verze protokolu. |
| CA5399 | [CA5399 jednoznačně zakázat kontrolu seznamu odvolaných certifikátů HttpClient](../code-quality/ca5399.md) | Odvolaný certifikát už není důvěryhodný. Může je použít útočníky, kteří předávají některá škodlivá data nebo ukrást citlivá data v komunikaci přes protokol HTTPS. |
| CA5400 | [CA5400 zajistěte, aby kontrola seznamu odvolaných certifikátů HttpClient není zakázaná](../code-quality/ca5400.md) | Odvolaný certifikát už není důvěryhodný. Může je použít útočníky, kteří předávají některá škodlivá data nebo ukrást citlivá data v komunikaci přes protokol HTTPS. |
| CA5401 | [CA5401 nepoužívá CreateEncryptor s jiným než výchozím IV](../code-quality/ca5401.md) | Symetrické šifrování by mělo vždy používat neopakovaný inicializační vektor, aby se zabránilo útokům na slovník. |
| CA5402 | [CA5402 použít CreateEncryptor s výchozí IV](../code-quality/ca5402.md) | Symetrické šifrování by mělo vždy používat neopakovaný inicializační vektor, aby se zabránilo útokům na slovník. |
| CA5403 | [CA5403: Nepoužívejte pevně zakódovaný certifikát](../code-quality/ca5403.md) | `data`Parametr nebo `rawData` <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktoru nebo jsou pevně zakódované. |
| IL3000 | [IL3000 vyhnout se přístupu k cestě k souboru sestavení při publikování jako jeden soubor](../code-quality/il3000.md) | Nepoužívejte přístup k cestě k souboru sestavení při publikování jako jeden soubor. |
| IL3001 | [IL3001 vyhnout se přístupu k cestě k souboru sestavení při publikování jako jeden soubor](../code-quality/il3001.md) | Nepoužívat cestu k souboru sestavení při publikování jako jeden soubor |
