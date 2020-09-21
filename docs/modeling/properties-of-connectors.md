---
title: Vlastnosti konektorů
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d2d3d747c128cfa2afbb63ae43289e0b50519b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810064"
---
# <a name="properties-of-connectors"></a>Vlastnosti konektorů
Konektory reprezentují doménové vztahy ve vygenerovaném návrháři.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Konektory mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Color|Barva této spojnice|Black|
|Styl přerušovanosti|Styl přerušovanosti čáry pro tento konektor (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Plná|
|Styl konce zdroje|Styl konce zdroje pro tento konektor (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond nebo žádný).|Žádné|
|Styl konce cíle|Styl konce cíle pro tento konektor (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond nebo None).|Žádné|
|Barva textu|Barva, která se používá pro text dekoratéry, který je spojený s tímto konektorem.|Black|
|Tloušťka|Tloušťka čáry pro tuto spojnici měřená v palcích|0,03125|
|Modifikátor přístupu|Úroveň přístupu třídy ( `public` nebo `internal` ).|Public|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto konektoru.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Nepravda|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Nepravda|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z konektoru ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní konektor|Základní třída této spojnice.|(žádná)|
|Název|Název této spojnice|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k této spojnici.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka (pevná, proměnná nebo žádný). Je-li tento parametr zadán, je hodnota `Fixed Tooltip Text` vlastnosti použita jako popis; je-li proměnná, je popis tlačítka definován ve vlastním kódu.|\<none>|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto konektoru.|\<none>|
|Styl směrování|Styl použitý ke směrování konektoru `Rectilinear`Spojnice nastaví otočení vpravo podle potřeby; `Straight` konektor ne.|Osmicípá|
|Vystavená barva jako vlastnost<br /><br /> Nevystavený čárkovaný styl jako vlastnost<br /><br /> Vystavená tloušťka jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True` může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|Nepravda|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tento konektor.|\<none>|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento element.|\<none>|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))