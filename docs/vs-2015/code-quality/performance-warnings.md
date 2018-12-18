---
title: Upozornění výkonu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a586da52a62dbc12abef442fbc379da2fcc14d1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298048"
---
# <a name="performance-warnings"></a>Upozornění výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění výkonu podporu vysoce výkonných knihoven a aplikací.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Pravidlo|Popis|  
|----------|-----------------|  
|[CA1800: Nepřetypujte zbytečně](../code-quality/ca1800-do-not-cast-unnecessarily.md)|Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace.|  
|[CA1801: Revize nepoužitých parametrů](../code-quality/ca1801-review-unused-parameters.md)|Podpis metody obsahuje parametr, který není použit v těle metody.|  
|[CA1802: Použijte literály, kde je to vhodné](../code-quality/ca1802-use-literals-where-appropriate.md)|Pole je deklarováno jako statické a jen pro čtení (Shared a ReadOnly v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) a je inicializován s hodnotou, kterou lze vypočítat v době kompilace. Protože hodnotu přiřazenou cílovému poli je nelze vypočítat v době kompilace, změňte deklaraci const (Const v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) pole tak, aby hodnota byla vypočítána v době kompilace místo v době běhu.|  
|[CA1804: Odeberte nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)|Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon.|  
|[CA1806: Neignorujte výsledky metody](../code-quality/ca1806-do-not-ignore-method-results.md)|Nový objekt je vytvořen, ale nikdy nepoužívali, nebo volat metodu, která vytvoří a vrátí nový řetězec a nový řetězec se nikdy nepoužívá, nebo metodu modelu COM (Component Object) nebo P/Invoke vrací HRESULT nebo kód chyby, který se nikdy nepoužívá.|  
|[CA1809: Vyhněte se nadměrným místním hodnotám](../code-quality/ca1809-avoid-excessive-locals.md)|Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, což je označováno jako „uložení hodnoty do registru“.  Pokud chcete zvýšit pravděpodobnost, že jsou všechny lokální proměnné uloženy v registrech procesoru, omezte počet lokálních proměnných na 64.|  
|[CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Kontroly statického konstruktoru mohou snížit výkon.|  
|[CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)|Privátní nebo interní člen (na úrovni sestavení) nemá v sestavení volající, není vyvolán modulem common language runtime a není vyvolán delegátem.|  
|[CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Instance typu na úrovni sestavení není vytvořena kódem v sestavení.|  
|[CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Knihovny tříd poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledávají hierarchii dědičnosti atributů. Zapečetění atributu eliminuje prohledávání hierarchie dědičnosti a může zlepšit výkon.|  
|[CA1814: Preferujte vícenásobná pole více než multidimenzionální](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Vícenásobné pole je pole, jehož prvky jsou pole. Pole tvořící prvky mohou být různě velká, což může vést k menšímu nevyužitému místu u některých sad dat.|  
|[CA1815: Přepište rovná se a operátor rovnosti na hodnotových typech](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Pro hodnotové typy používá zděděná implementace metody Equals knihovnu reflexe a porovnává obsah všech polí. Reflexe je výpočetně náročná a porovnání rovnosti všech polí může být zbytečné. Očekáváte-li, že uživatelé budou porovnávat nebo třídit instance či je používat jako klíče zatřiďovací tabulky, měl by typ hodnoty implementovat metodu Equals.|  
|[CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Metoda, která je implementací metody Dispose, nevolá uvolňování paměti. SuppressFinalize nebo metodou, která není implementací metody Dispose, volá uvolňování paměti. SuppressFinalize nebo metoda zavolá uvolňování paměti. SuppressFinalize a předává něco jiného (Me v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).|  
|[CA1819: Vlastnosti by neměly vracet pole](../code-quality/ca1819-properties-should-not-return-arrays.md)|Pole vrácená vlastnostmi nejsou chráněna proti zápisu, i v případě, že vlastnost je jen pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností.|  
|[CA1820: Testujte prázdné řetězce pomocí délky řetězce](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Porovnání řetězců pomocí vlastnosti String.Length nebo metody String.IsNullOrEmpty je výrazně rychlejší než při použití metody Equals.|  
|[CA1821: Odstraňte prázdné finalizační metody](../code-quality/ca1821-remove-empty-finalizers.md)|Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Prázdná finalizační metoda zvyšuje přidali režijní náklady bez žádnou výhodu.|  
|[CA1822: Označte členy jako statické](../code-quality/ca1822-mark-members-as-static.md)|Členové, kteří nemají přístup k instanci dat nebo metodám instance volání může být označený jako statické (sdílené v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Po označení metod jako statických bude kompilátor generovat těmto členům nevirtuální místa volání. Tím lze dosáhnout měřitelného zisku výkonu pro výkonově citlivý kód.|  
|[CA1823: Vyhněte se nepoužitým privátním polím](../code-quality/ca1823-avoid-unused-private-fields.md)|Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná.|  
|[CA1824: Označte sestavení pomocí atributu NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Atribut NeutralResourcesLanguage informuje správce prostředků o jazyku použitém pro vykreslení neutrální jazykové verze prostředků pro sestavení. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu.|



