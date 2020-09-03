---
title: Vlastnosti konektorů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ea629e504c3ba74d35f3ad8aa89bc22cfae30df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652043"
---
# <a name="properties-of-connectors"></a>Vlastnosti konektorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Konektory reprezentují doménové vztahy ve vygenerovaném návrháři.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Konektory mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|--------------|-----------------|-------------|
|Color|Barva této spojnice|Black|
|Styl přerušovanosti|Styl přerušovanosti čáry pro tento konektor (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Plná|
|Styl konce zdroje|Styl konce zdroje pro tento konektor (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond nebo žádný).|Žádné|
|Styl konce cíle|Styl konce cíle pro tento konektor (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond nebo None).|Žádné|
|Barva textu|Barva, která se používá pro text dekoratéry, který je spojený s tímto konektorem.|Black|
|Tloušťka|Tloušťka čáry pro tuto spojnici měřená v palcích|0,03125|
|Modifikátor přístupu|Úroveň přístupu třídy ( `public` nebo `internal` ).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto konektoru.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z konektoru ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní konektor|Základní třída této spojnice.|(žádná)|
|Název|Název této spojnice|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k této spojnici.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka (pevná, proměnná nebo žádný). Je-li tento parametr zadán, je hodnota `Fixed Tooltip Text` vlastnosti použita jako popis; je-li proměnná, je popis tlačítka definován ve vlastním kódu.|\<none>|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto konektoru.|\<none>|
|Styl směrování|Styl použitý ke směrování konektoru `Rectilinear`Spojnice nastaví otočení vpravo podle potřeby; `Straight` konektor ne.|Osmicípá|
|Vystavená barva jako vlastnost<br /><br /> Nevystavený čárkovaný styl jako vlastnost<br /><br /> Vystavená tloušťka jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True` může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|Ne|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tento konektor.|\<none>|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento element.|\<none>|

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
