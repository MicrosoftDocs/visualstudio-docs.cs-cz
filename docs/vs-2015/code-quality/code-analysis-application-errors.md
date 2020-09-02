---
title: Chyby aplikace Analýzy kódu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef5ccc0cf432a5c6782b76c4623bfdc55f66a8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538552"
---
# <a name="code-analysis-application-errors"></a>Chyby aplikace Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Tato část je odkazem na chybové zprávy, které jsou generovány nástrojem pro analýzu spravovaného kódu. Nápovědu k určité chybové zprávě získáte tak, že do pole **Hledat** v indexu zadáte číslo chyby.

## <a name="in-this-section"></a>V tomto oddílu

|Položka|Hodnota|
|-|-|
|[CA0001](ca0001.md)|V nástroji pro analýzu spravovaného kódu se vyvolala výjimka, která neindikuje očekávanou chybovou podmínku.|
|[CA0051](ca0051.md)|Nebyla vybrána žádná pravidla.|
|[CA0052](ca0052.md)|Nebyly vybrány žádné cíle pro analýzu.|
|[CA0053](ca0053.md)|Sestavení pravidla nelze načíst.|
|[CA0054](ca0054.md)|Sestavení vlastního pravidla obsahuje neplatné prostředky XML.|
|[CA0055](ca0055.md)|Nepodařilo se načíst soubor:\<path>|
|[CA0056](ca0056.md)|Soubor projektu má nesprávnou verzi nástroje pro analýzu.|
|[CA0057](ca0057.md)|Porušení nelze mapovat na aktuální sadu cílů a pravidel.|
|[CA0058](ca0058.md)|Nelze načíst sestavení, na které odkazuje.|
|[CA0059](ca0059.md)|Chyba přepínače příkazového řádku.|
|[CA0060](ca0060.md)|Nelze načíst sestavení, která jsou odkazována nepřímo.|
|[CA0061](ca0061.md)|Pravidlo '*RuleId*' nebylo nalezeno.|
|[CA0062](ca0062.md)|Pravidlo '*RuleId*' odkazované v sadě pravidel '*RuleSetName*' nebylo nalezeno.|
|[CA0063](ca0063.md)|Nepovedlo se načíst soubor sady pravidel nebo jeden z jeho závislých souborů sady pravidel.|
|[CA0064](ca0064.md)|Nebyla provedena žádná analýza, protože zadaná sada pravidel neobsahuje žádná pravidla FxCop.|
|[CA0065](ca0065.md)|Nepodporovaná konstrukce metadat: typ*TypeName*obsahuje vlastnost i pole se stejným názvem '*PropertyFieldName*'.|
|[CA0066](ca0066.md)|Hodnota '*VersionID*' poskytnutá **/TargetFrameworkVersion** není rozpoznaná verze.|
|[CA0067](ca0067.md)|Adresář nebyl nalezen.|
|[CA0068](ca0068.md)|Pro cílové sestavení *' AssemblyName '* nebyly nalezeny informace o ladění.|
|[CA0069](ca0069.md)|Použití alternativní platformy. *FrameworkVersion1* se nepovedlo najít. Místo toho použijte *FrameworkVersion2* . Pro dosažení co nejlepších výsledků analýz Prosím zajistěte, aby byla nainstalovaná správná .NET Framework.|
|[CA0070](ca0070.md)|Nejde načíst sestavení nebo typ z důvodu oprávnění zabezpečení.|
|[CA0501](ca0501.md)|Nelze načíst výstup sestavy.|
|[CA0502](ca0502.md)|Nepodporovaný jazyk|
|[CA0503](ca0503.md)|Vlastnost je zastaralá. Použít vlastnost převádějící|
|[CA0504](ca0504.md)|Adresář pravidel se ignoroval, protože neexistuje.|
|[CA0505](ca0505.md)|Vlastnost je zastaralá. Použít vlastnost převádějící|
|[FxCopCmd chyby](fxcopcmd-errors.md)|Chyby analýzy spravovaného kódu|

## <a name="related-sections"></a>Související oddíly

- [Pokyny pro psaní zabezpečeného kódu](https://msdn.microsoft.com/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Prostředky pro řešení chyb v nástrojích pro správu životního cyklu aplikací](https://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)