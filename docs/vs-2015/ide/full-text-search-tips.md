---
title: Tipy pro fulltextové vyhledávání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85770dfd3c610f92bcb190b7a2c151b40cd31a4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850045"
---
# <a name="full-text-search-tips"></a>Tipy pro fulltextové vyhledávání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedním ze užitečnější metody v nápovědě k vyhledání informací o je provádění fulltextové vyhledávání. Upravit a přizpůsobit si výsledky, je třeba pochopit, jak ovlivňuje syntaxi dotazu. Toto téma obsahuje tipy, postupy a informace o syntaxi podrobné abychom vám lépe zručné vaše dotazy.  
  
## <a name="full-text-search-tips"></a>Tipy pro fulltextové vyhledávání  
 Můžete vytvořit více cílené hledání, které vracejí pouze tato témata této zájem, pokud víte, jak interpretovat nápovědy formátování, které použijete v dotazech. Tyto formáty zahrnují speciální znaky, rezervovaná slova a filtry.  
  
### <a name="general-guidelines"></a>Obecné pokyny  
 Následující tabulka obsahuje některé základní pravidla a pokyny pro vývoj vyhledávacích dotazů v nápovědě.  
  
|Syntaxe|Popis|  
|------------|-----------------|  
|Rozlišování velikosti písmen|Hledání se malá a velká písmena. Vývoj vašich kritérií vyhledávání pomocí velká nebo malá písmena. Například "OLE" a "ole" vrátí stejné výsledky.|  
|Kombinace znaků|Nelze vyhledat pouze jednotlivé písmena (a – z) nebo číslice (0 – 9). Pokud se pokusíte vyhledávání pro určité vyhrazená slova, například "a", "od" a "s", budou ignorovány. Další informace najdete v tématu "Slova ignoruje při hledání (nevýznamová slova)" dále v tomto tématu.|  
|Pořadí vyhodnocení|Vyhledávací dotazy jsou vyhodnoceny zleva doprava.|  
  
### <a name="search-syntax"></a>Syntaxe vyhledávání  
 Pokud zadáte hledaný řetězec, který obsahuje více slov, jako je například "word1 word2," Tento řetězec je zadat text "word1 word2 a", který vrátí pouze témata, která obsahují všechny jednotlivých slov ve vyhledávacím řetězci.  
  
> [!IMPORTANT]
> 1. Vyhledávání frází nejsou podporovány. Pokud chcete zadat více slov ve vyhledávaném řetězci, bude vrácená témata obsahují všechna slova, která jste zadali, ale ne nutně přesnou frázi, které jste zadali.  
>    2.  Použijte logické operátory Pokud chcete určit vztah mezi slovy ve vaší vyhledávací fráze. Můžete zahrnout logické operátory, jako je například AND, OR, NOT a TÉMĚŘ, pro další upřesněte hledání. Například pokud hledáte "deklarace TÉMĚŘ sjednocení", budou výsledky hledání obsahují témata obsahující slova "deklarace" a "sjednocení" více než pár slov od sebe navzájem. Další informace najdete v tématu [logické operátory ve vyhledávacích výrazech](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filtry  
 Výsledky hledání můžete omezit pomocí operátorů rozšířené vyhledávání. Nápověda obsahuje tři kategorie, které můžete použít pro filtrování výsledků fulltextové vyhledávání: název, kód a – klíčové slovo. Další informace najdete v tématu [Pokročilí operátoři vyhledávání ve vyhledávacích výrazech](../ide/advanced-search-operators-in-search-expressions.md).  
  
### <a name="ranking-of-search-results"></a>Řazení výsledků hledání  
 Vyhledávací algoritmus platí určitá kritéria umožňující řazení výsledků vyšší nebo nižší v seznamu výsledků hledání. Obecně platí:  
  
1.  Obsah, který zahrnuje hledaná slova v názvu je vyšší než obsah, který není řazením.  
  
2.  Obsah, který obsahuje hledaná slova v těsné blízkosti je vyšší než obsah, který není řazením.  
  
3.  Obsah, který obsahuje vyšší hustotu slova je vyšší než obsah, který má nižší hustotu slova řazením.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Slova v hledání (nevýznamová slova) ignoruje.  
 Nejčastěji se vyskytující slova nebo čísel, které jsou někdy označovány jako nevýznamová slova, se automaticky ignorují během fulltextového vyhledávání. Například pokud hledáte pro frázi "průchodu", zobrazí výsledky hledání témata obsahující slovo "heslo" ale ne "až".  
  
## <a name="see-also"></a>Viz také  
 [Vyhledejte informace](../ide/locate-information.md)   
 [Logické operátory ve vyhledávacích výrazech](../ide/logical-operators-in-search-expressions.md)



