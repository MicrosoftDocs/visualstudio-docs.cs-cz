---
title: Chyby aplikace analýzy kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66d611903c71cc526c01c1062c85ceef2e7975f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225014"
---
# <a name="code-analysis-application-errors"></a>Chyby aplikace Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Tato část se odkaz chybové zprávy, které jsou generovány nástroj pro analýzu spravovaného kódu. Chcete-li získat nápovědu pro určité chybové zprávě, zadejte číslo chyby v **vyhledejte** pole v indexu.

## <a name="in-this-section"></a>V tomto oddílu

|||
|-|-|
|[CA0001](ca0001.md)|V rámci nástroj pro analýzu spravovaného kódu, který nenaznačuje, že očekávané chybovou podmínku došlo k výjimce.|
|[CA0051](ca0051.md)|Nebyla vybrána žádná pravidla.|
|[CA0052](ca0052.md)|Nebyly vybrány žádné cíle pro analýzu.|
|[CA0053](ca0053.md)|Pravidlo sestavení nelze načíst.|
|[CA0054](ca0054.md)|Vlastní pravidlo sestavení má neplatné XML prostředky.|
|[CA0055](ca0055.md)|Nepovedlo se načíst soubor:\<cesta >|
|[CA0056](ca0056.md)|Soubor projektu má nesprávnou verzi nástroje pro analýzu.|
|[CA0057](ca0057.md)|Porušení nelze mapovat na aktuální sadu cílů a pravidla.|
|[CA0058](ca0058.md)|Nepovedlo se načíst odkazované sestavení.|
|[CA0059](ca0059.md)|Přepínač příkazového řádku došlo k chybě.|
|[CA0060](ca0060.md)|Nepovedlo se načíst sestavení, které jsou nepřímo odkazovány.|
|[CA0061](ca0061.md)|Pravidlo "*RuleId*' nebyl nalezen.|
|[CA0062](ca0062.md)|Pravidlo "*RuleId*'odkazované v sadě pravidel'*RuleSetName*' nebyl nalezen.|
|[CA0063](ca0063.md)|Nepovedlo se načíst soubor sady pravidel nebo jeden z jeho souborů sady pravidel závislé.|
|[CA0064](ca0064.md)|Nebyla provedena žádná analýza, protože zadanou sadu pravidel neobsahovala žádná pravidla FxCop.|
|[CA0065](ca0065.md)|Nepodporovaná konstrukce metadat: typ '*TypeName*"obsahuje vlastnost i pole se stejným názvem"*PropertyFieldName*.|
|[CA0066](ca0066.md)|Hodnota '*VersionID*"k dispozici na **/TargetFrameworkVersion** není rozpoznána verze.|
|[CA0067](ca0067.md)|Adresář nebyl nalezen.|
|[CA0068](ca0068.md)|Ladění nelze najít informace pro cílové sestavení *"AssemblyName"*.|
|[CA0069](ca0069.md)|Pomocí alternativní platformy. *FrameworkVersion1* nebyl nalezen. Pomocí *FrameworkVersion2* místo. Pro nejlepší výsledky analýzy Ujistěte se prosím, že je nainstalované správné rozhraní .NET Framework.|
|[CA0070](ca0070.md)|Nelze načíst sestavení nebo typ z důvodu oprávnění zabezpečení.|
|[CA0501](ca0501.md)|Nelze číst výstup sestavy.|
|[CA0502](ca0502.md)|Nepodporovaný jazyk.|
|[CA0503](ca0503.md))|Vlastnost je deprectated. Nahrazující vlastnost|
|[CA0504](ca0504.md)|Pravidlo adresář byl ignorován, protože neexistuje|
|[CA0505](ca0505.md)|Vlastnost je deprectated. Nahrazující vlastnost|
|[FxCopCmd – chyby](fxcopcmd-errors.md)|Chyby analýzy spravovaného kódu.|
|[Chyby zásad Analýzy kódu](../code-quality/code-analysis-policy-errors.md)|Vrácení analýzy kódu se změnami chyby zásad.|

## <a name="related-sections"></a>Související oddíly

- [Pokyny pro psaní bezpečného kódu](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Prostředky pro řešení potíží s chybami v nástrojích pro správu životního cyklu aplikací](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)