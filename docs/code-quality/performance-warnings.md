---
title: Upozornění výkonu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13cb3e83b06b3533d1feb1e683fb246f238da732
ms.sourcegitcommit: 6a43ace7b84c401ebd03f65abc17ae1d2a21a130
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2020
ms.locfileid: "89471476"
---
# <a name="performance-warnings"></a>Upozornění výkonu
Upozornění výkonu podporují vysoce výkonné knihovny a aplikace.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1800: Nepřetypujte zbytečně](../code-quality/ca1800.md) | Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. |
| [CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801.md) | Podpis metody obsahuje parametr, který není použit v těle metody. |
| [CA1802: Použijte literály, kde je to vhodné](../code-quality/ca1802.md) | Pole je deklarováno jako static a jen pro čtení (Shared a ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) a je inicializováno s hodnotou, která je v době kompilace Compute. Vzhledem k tomu, že hodnota, která je přiřazena cílovému poli je COMPUTE v době kompilace, změňte deklaraci na pole const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ), aby se hodnota vypočítala v době kompilace místo v době běhu. |
| [CA1804: Odeberte nepoužívané lokální hodnoty](../code-quality/ca1804.md) | Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon. |
| [CA1805: Nepoužívejte inicializaci zbytečně](../code-quality/ca1805.md) | Modul runtime .NET inicializuje všechna pole odkazových typů na jejich výchozí hodnoty před spuštěním konstruktoru. Ve většině případů je explicitní inicializace pole na jeho výchozí hodnotu redundantní, což zvyšuje náklady na údržbu a může snížit výkon (například se zvýšenou velikostí sestavení). |
| [CA1806: Neignorujte výsledky metody](../code-quality/ca1806.md) | Vytvoří se nový objekt, ale nikdy se nepoužívá, nebo metoda, která vytvoří a vrátí nový řetězec, se zavolá a nový řetězec se nikdy nepoužije nebo metoda modelu COM (Component Object Model) nebo volání nespravovaného kódu vrátí hodnotu HRESULT nebo kód chyby, který se nikdy nepoužívá. |
| [CA1809: Vyhněte se nadměrným lokálním hodnotám](../code-quality/ca1809.md) | Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“.  Chcete-li zvýšit pravděpodobnost, že jsou všechny místní proměnné registrován, omezte počet místních proměnných na 64. |
| [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810.md) | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
| [CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811.md) | Soukromý nebo interní člen (na úrovni sestavení) nemá volající v sestavení, není vyvolán modulem CLR (Common Language Runtime) a není vyvolán delegátem. |
| [CA1812: Vyhněte se nevytvořeným instancím interních tříd](../code-quality/ca1812.md) | Instance typu na úrovni sestavení není vytvořena kódem v sestavení. |
| [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813.md) | Rozhraní .NET poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon. |
| [CA1814: Upřednostněte vícenásobná pole před multidimenzionálními](../code-quality/ca1814.md) | Vícenásobné pole je pole, jehož prvky jsou pole. Pole, která tvoří prvky, mohou mít různé velikosti, což může vést k menšímu množství nevyužitého prostoru pro některé sady dat. |
| [CA1815: Přepište rovnosti a operátory rovnosti u typů hodnot](../code-quality/ca1815.md) | Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals. |
| [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816.md) | Metoda, která je implementací metody Dispose, nevolá GC. SuppressFinalize nebo metoda, která není implementací volání Dispose, uvolňuje GC. SuppressFinalize nebo metoda volá GC. SuppressFinalize a projde něco jiného než to (jsem já v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). |
| [CA1819: Vlastnosti by neměly vracet pole](../code-quality/ca1819.md) | Pole, která jsou vrácena vlastnostmi, nejsou chráněna proti zápisu, a to i v případě, že je vlastnost určena pouze pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. |
| [CA1820: Testujte prázdné řetězce pomocí délky řetězce](../code-quality/ca1820.md) | Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals. |
| [CA1821: Odeberte prázdné finalizační metody](../code-quality/ca1821.md) | Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda vyvolává režii bez jakýchkoli výhod. |
| [CA1822: Označte členy jako statické](../code-quality/ca1822.md) | Členy, kteří nemají přístup k datům instance nebo metodám instance volání, mohou být označeny jako statické (sdílené v rámci [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód. |
| [CA1823: Vyhněte se nepoužitým privátním polím](../code-quality/ca1823.md) | Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná. |
| [CA1824: Označte sestavení pomocí NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | Atribut NeutralResourcesLanguage informuje Správce prostředků jazyku, který byl použit k zobrazení prostředků neutrální jazykové verze pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu. |
| [CA1825: Vyhněte se přidělení pole s nulovou délkou.](../code-quality/ca1825.md) | Inicializace pole nulové délky vede k nepotřebnému přidělení paměti. Místo toho použijte staticky přidělenou instanci prázdného pole voláním <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Přidělení paměti se sdílí ve všech voláních této metody. |
| [CA1826: Použijte vlastnost namísto vyčíslitelné metody Linq](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> Metoda LINQ byla použita pro typ, který podporuje ekvivalentní, efektivnější vlastnost. |
| [CA1827: Nepoužívejte Count/LongCount, když se dá použít Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.LongCount%2A> se použila metoda, kde <xref:System.Linq.Enumerable.Any%2A> by byla metoda efektivnější. |
| [CA1828: Nepoužívejte CountAsync/LongCount, když se dá použít AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> nebo <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> se použila metoda, kde <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> by byla metoda efektivnější. |
| [CA1829: Použijte vlastnost Length/Count místo metody Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> Metoda LINQ byla použita pro typ, který podporuje ekvivalentní, efektivnější `Length` nebo `Count` vlastnost. |
| [CA1830: Upřednostňovat pro StringBuilder přetížení metod Append a Insert silného typu](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> a <xref:System.Text.StringBuilder.Insert%2A> Poskytněte přetížení pro více typů za řetězec System. String.  Pokud je to možné, preferovat přetížení silného typu přes použití rozhraní ToString () a přetížení založeného na řetězci. |
| [CA1831: Tam, kde je to možné, používat u řetězců místo indexerů založených na rozsahu metodu AsSpan](../code-quality/ca1831.md) | Při použití rozsahu indexeru na řetězec a implicitně přiřadíte hodnotu ReadOnlySpan &lt; typu char, použije se &gt; namísto toho metoda <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části řetězce. |
| [CA1832: Pro získání části ReadOnlySpan nebo ReadOnlyMemory pole používat místo indexerů založených na rozsahu metodu AsSpan nebo AsMemory](../code-quality/ca1832.md) | Při použití rozsahu indexeru v poli a implicitně přiřadí hodnotu <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> typu nebo, bude <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> použita metoda namísto <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části pole. |
| [CA1833: Pro získání části Span nebo Memory pole používat místo indexerů založených na rozsahu metodu AsSpan nebo AsMemory](../code-quality/ca1833.md) | Při použití rozsahu indexeru v poli a implicitně přiřadí hodnotu <xref:System.Span%601> <xref:System.Memory%601> typu nebo, bude <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> použita metoda namísto <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , která vytvoří kopii požadované části pole. |
| [CA1834: použijte StringBuilder. Append (Char) pro řetězce s jedním znakem.](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> má `Append` přetížení, které přijímá `char` jako svůj argument. Preferovat volání `char` přetížení pro zlepšení výkonu. |
| [CA1835: preferovat přetížení založené na Memory' pro ReadAsync a WriteAsync](../code-quality/ca1835.md) | ' Stream ' má přetížení ' ReadAsync ', které jako první argument přebírá ' paměť &lt; Byte &gt; ' a přetížení ' WriteAsync ', které jako první argument přebírá ' &lt; ReadOnlyMemory byte &gt; '. Preferovat volání přetížení založeného na paměti, což je efektivnější. |
| [CA1836: preferovat více, je- `IsEmpty` `Count` li k dispozici](../code-quality/ca1836.md) | Preferovat `IsEmpty` vlastnost, která je efektivnější než `Count` , `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> nebo <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> k určení, zda objekt obsahuje nebo neobsahuje žádné položky. |
| [CA1837: použijte `Environment.ProcessId` místo `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` je jednodušší a rychlejší než `Process.GetCurrentProcess().Id` . |
| [CA1838: Vyhněte se `StringBuilder` parametrům pro volání nespravovaného volání](../code-quality/ca1838.md) | Zařazování `StringBuilder` vždy vytvoří nativní kopii vyrovnávací paměti a výsledkem je vícenásobné přidělení pro jednu operaci zařazování. |
