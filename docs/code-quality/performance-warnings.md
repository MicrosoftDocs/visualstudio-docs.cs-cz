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
ms.openlocfilehash: 42f188901db72378acfd1dee8e22c9a2261b8eb9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587248"
---
# <a name="performance-warnings"></a>Upozornění výkonu
Upozornění výkonu podporují vysoce výkonné knihovny a aplikace.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1800: Nepřetypujte zbytečně](../code-quality/ca1800.md) | Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. |
| [CA1801: Revize nepoužitých parametrů](../code-quality/ca1801.md) | Podpis metody obsahuje parametr, který není použit v těle metody. |
| [CA1802: Použijte literály, kde je to vhodné](../code-quality/ca1802.md) | Pole je deklarováno jako static a jen pro čtení (Shared a ReadOnly v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a je inicializováno s hodnotou, která je COMPUTE v době kompilace. Protože hodnotu přiřazenou cílovému poli je nelze vypočítat v době kompilace, změňte deklaraci const (Const v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pole tak, aby hodnota byla vypočítána v době kompilace místo v době běhu. |
| [CA1804: Odeberte nepoužívané místní hodnoty](../code-quality/ca1804.md) | Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon. |
| [CA1806: Neignorujte výsledky metody](../code-quality/ca1806.md) | Vytvoří se nový objekt, ale nikdy se nepoužívá, nebo metoda, která vytvoří a vrátí nový řetězec, se zavolá a nový řetězec se nikdy nepoužije nebo metoda modelu COM (Component Object Model) nebo volání nespravovaného kódu vrátí hodnotu HRESULT nebo kód chyby, který se nikdy nepoužívá. |
| [CA1809: Vyhněte se nadměrným místním hodnotám](../code-quality/ca1809.md) | Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“.  Pokud chcete zvýšit pravděpodobnost, že jsou všechny lokální proměnné uloženy v registrech procesoru, omezte počet lokálních proměnných na 64. |
| [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810.md) | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
| [CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811.md) | Soukromý nebo interní člen (na úrovni sestavení) nemá volající v sestavení, není vyvolán modulem CLR (Common Language Runtime) a není vyvolán delegátem. |
| [CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd](../code-quality/ca1812.md) | Instance typu na úrovni sestavení není vytvořena kódem v sestavení. |
| [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813.md) | Rozhraní .NET poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon. |
| [CA1814: Preferujte vícenásobná pole více než multidimenzionální](../code-quality/ca1814.md) | Vícenásobné pole je pole, jehož prvky jsou pole. Pole, která tvoří prvky, mohou mít různé velikosti, což může vést k menšímu množství nevyužitého prostoru pro některé sady dat. |
| [CA1815: Přepište rovná se a operátor rovnosti na hodnotových typech](../code-quality/ca1815.md) | Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals. |
| [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816.md) | Metoda, která je implementací metody Dispose, nevolá GC. SuppressFinalize nebo metoda, která není implementací volání Dispose, uvolňuje GC. SuppressFinalize nebo metoda volá GC. SuppressFinalize a projde něco jiného než to (já v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Vlastnosti by neměly vracet pole](../code-quality/ca1819.md) | Pole, která jsou vrácena vlastnostmi, nejsou chráněna proti zápisu, a to i v případě, že je vlastnost určena pouze pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. |
| [CA1820: Testujte prázdné řetězce pomocí délky řetězce](../code-quality/ca1820.md) | Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals. |
| [CA1821: Odstraňte prázdné finalizační metody](../code-quality/ca1821.md) | Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda vyvolává režii bez jakýchkoli výhod. |
| [CA1822: Označte členy jako statické](../code-quality/ca1822.md) | Členové, kteří nemají přístup k instanci dat nebo metodám instance volání může být označený jako statické (sdílené v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód. |
| [CA1823: Vyhněte se nepoužitým privátním polím](../code-quality/ca1823.md) | Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná. |
| [CA1824: Označte sestavení pomocí atributu NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | Atribut NeutralResourcesLanguage informuje správce prostředků o jazyku použitém pro vykreslení neutrální jazykové verze prostředků pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu. |
| [CA1825: Vyhněte se přidělením pole s nulovou délkou.](../code-quality/ca1825.md) | Inicializace pole nulové délky vede k nepotřebnému přidělení paměti. Místo toho použijte staticky přidělenou instanci prázdného pole voláním <xref:System.Array.Empty%2A?displayProperty=nameWithType>. Přidělení paměti se sdílí ve všech voláních této metody. |
