---
title: Vlastnosti konektorů
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2244b191bac2456886368992d1dc8f1c571dc227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658250"
---
# <a name="properties-of-connectors"></a>Vlastnosti konektorů
Konektory reprezentují doménové vztahy ve vygenerovaném návrháři.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Konektory mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barevných|Barva této spojnice|zůstane|
|Styl přerušovanosti|Styl přerušovanosti čáry pro tento konektor (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Solid|
|Styl konce zdroje|Styl konce zdroje pro tento konektor (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond nebo žádný).|Žádné|
|Styl konce cíle|Styl konce cíle pro tento konektor (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond nebo None).|Žádné|
|Barva textu|Barva, která se používá pro text dekoratéry, který je spojený s tímto konektorem.|zůstane|
|Silnější|Tloušťka čáry pro tuto spojnici měřená v palcích|0,03125|
|Modifikátor přístupu|Úroveň přístupu třídy (`public` nebo `internal`).|Public|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto konektoru.|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, bude vygenerována jak základní třída, tak i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud `True`, bude ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z konektoru (`none`, `abstract` nebo `sealed`).|žádná|
|Základní konektor|Základní třída této spojnice.|nTato|
|Name|Název této spojnice|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k této spojnici.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka (pevná, proměnná nebo žádný). Pokud je pevná, pak se jako popis používá hodnota vlastnosti `Fixed Tooltip Text`; Pokud je proměnná, pak je popis definovaný ve vlastním kódu.|\<none >|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto konektoru.|\<none >|
|Styl směrování|Styl použitý ke směrování konektoru @No__t_0 spojnice nastaví otočení vpravo podle potřeby; konektor `Straight` ne.|Osmicípá|
|Vystavená barva jako vlastnost<br /><br /> Nevystavený čárkovaný styl jako vlastnost<br /><br /> Vystavená tloušťka jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True`, může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|False|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři pro tento konektor.|\<none >|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none >|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento element.|\<none >|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)