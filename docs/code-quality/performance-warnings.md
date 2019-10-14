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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305655"
---
# <a name="performance-warnings"></a>Upozornění výkonu
Upozornění výkonu podporují vysoce výkonné knihovny a aplikace.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1800: Nepoužívejte bezpodmínečně @ no__t-0 | Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. |
| [CA1801: Zkontrolovat nepoužité parametry @ no__t-0 | Podpis metody obsahuje parametr, který není použit v těle metody. |
| [CA1802: Použijte literály, kde je to vhodné @ no__t-0 | Pole je deklarováno jako static a jen pro čtení (Shared a ReadOnly v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a je inicializováno s hodnotou, která je COMPUTE v době kompilace. Protože hodnotu přiřazenou cílovému poli je nelze vypočítat v době kompilace, změňte deklaraci const (Const v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pole tak, aby hodnota byla vypočítána v době kompilace místo v době běhu. |
| [CA1804: Odebrat nepoužívané místní hodnoty @ no__t-0 | Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon. |
| [CA1806: Neignorujte výsledky metody @ no__t-0. | Vytvoří se nový objekt, ale nikdy se nepoužívá, nebo metoda, která vytvoří a vrátí nový řetězec, se zavolá a nový řetězec se nikdy nepoužije nebo metoda modelu COM (Component Object Model) nebo volání nespravovaného kódu vrátí hodnotu HRESULT nebo kód chyby, který se nikdy nepoužívá. |
| [CA1809: Vyhnout se nadměrnému počtu lokálních hodnot @ no__t-0 | Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“.  Pokud chcete zvýšit pravděpodobnost, že jsou všechny lokální proměnné uloženy v registrech procesoru, omezte počet lokálních proměnných na 64. |
| [CA1810: Inicializovat statická pole typu odkaz na vloženou hodnotu @ no__t-0 | Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon. |
| [CA1811: Vyhněte se nevolanému privátnímu kódu @ no__t-0 | Soukromý nebo interní člen (na úrovni sestavení) nemá volající v sestavení, není vyvolán modulem CLR (Common Language Runtime) a není vyvolán delegátem. |
| [CA1812: Vyhněte se nevytváření instancí vnitřních tříd @ no__t-0 | Instance typu na úrovni sestavení není vytvořena kódem v sestavení. |
| [CA1813: Vyhněte se nezapečetěným atributům @ no__t-0 | Rozhraní .NET poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon. |
| [CA1814: Preferovat vícenásobná pole nad multidimenzionálním @ no__t-0 | Vícenásobné pole je pole, jehož prvky jsou pole. Pole, která tvoří prvky, mohou mít různé velikosti, což může vést k menšímu množství nevyužitého prostoru pro některé sady dat. |
| [CA1815: Přepište Equals a operátor Equals na hodnotových typech @ no__t-0 | Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals. |
| [CA1816: Vyvolejte GC. SuppressFinalize správně @ no__t-0 | Metoda, která je implementací metody Dispose, nevolá GC. SuppressFinalize nebo metoda, která není implementací volání Dispose, uvolňuje GC. SuppressFinalize nebo metoda volá GC. SuppressFinalize a projde něco jiného než to (já v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Vlastnosti by neměly vracet pole @ no__t-0 | Pole, která jsou vrácena vlastnostmi, nejsou chráněna proti zápisu, a to i v případě, že je vlastnost určena pouze pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. |
| [CA1820: Testujte prázdné řetězce pomocí délky řetězce @ no__t-0 | Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals. |
| [CA1821: Odebrat prázdné finalizační metody @ no__t-0 | Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda vyvolává režii bez jakýchkoli výhod. |
| [CA1822: Označit členy jako statické @ no__t-0 | Členové, kteří nemají přístup k instanci dat nebo metodám instance volání může být označený jako statické (sdílené v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód. |
| [CA1823: Vyhněte se nepoužitým privátním polím @ no__t-0 | Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná. |
| [CA1824: Označte sestavení pomocí atribut NeutralResourcesLanguageAttribute @ no__t-0. | Atribut NeutralResourcesLanguage informuje správce prostředků o jazyku použitém pro vykreslení neutrální jazykové verze prostředků pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu. |
| @NO__T – 0CA1825: Vyhněte se přidělení pole s nulovou délkou @ no__t-0 | Inicializace pole nulové délky vede k nepotřebnému přidělení paměti. Místo toho použijte staticky přidělenou instanci prázdného pole voláním <xref:System.Array.Empty%2A?displayProperty=nameWithType>. Přidělení paměti se sdílí ve všech voláních této metody. |
