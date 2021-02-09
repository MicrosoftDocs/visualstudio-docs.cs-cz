---
title: Vlastnosti obrazových obrazců
description: Přečtěte si o obrazových obrazech a o tom, jak můžete pomocí tvarů obrázků určit, jak se ve vygenerovaném návrháři zobrazí doménové třídy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8bbd2fff30ab59d14c8aa2762d8cca942063bd79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918344"
---
# <a name="properties-of-image-shapes"></a>Vlastnosti obrazových obrazců

Pomocí tvarů obrázků lze určit, jak se ve vygenerovaném návrháři zobrazí doménové třídy. Definujte obrazový tvar nastavením `Image` vlastnosti třídy na předdefinovaný soubor obrázku. Podporovány jsou následující formáty:

- .gif

- .jpg

- .jpeg

- .bmp

- . WMF

- . EMF

- .png

Ve výchozím nastavení se soubory prostředků návrháře, jako jsou soubory obrázků, nacházejí ve složce **Resources** v projektu **DSL** .

Další informace najdete v tématu [definování Domain-Specificho jazyka](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti použít, najdete v tématu [přizpůsobení a rozšíření Domain-Specificho jazyka](../modeling/customizing-and-extending-a-domain-specific-language.md).

Obrazce obrázků mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně tohoto obrazce|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce|Vodorovně|
|Má výchozí spojovací body|Pokud `True` bude obrazec používat horní, dolní, levý a pravý spojovací bod ve vygenerovaném návrháři.|Ne|
|Barva obrysu|Barva obrysu tohoto obrazce|Black|
|Styl přerušované čáry obrysu|Styl přerušování obrysu tohoto obrazce (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Plná|
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce|0,03125|
|Barva textu|Barva použitá pro text dekoratéry, která je přidružena k tomuto obrazci.|Black|
|Modifikátor přístupu|Modifikátor přístupu obrazce geometrie (veřejný nebo interní).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto obrazce.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z obrazce obrázku ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní obrazec obrázku|Základní třída tohoto obrazce|(žádná)|
|Název|Název tohoto obrazce|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto obrazci.|Aktuální obor názvů|
|Typ popisu|Místo, kde je popisek definován (pevná, proměnná nebo žádný). Je-li tento parametr zadán, je hodnota `Fixed Tooltip Text` vlastnosti použita jako popis; je-li proměnná, je popis tlačítka definován ve vlastním kódu.|žádné|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto obrazci.|\<none>|
|Počáteční výška|Počáteční výška tohoto obrazce v palcích|1|
|Počáteční Šířka|Počáteční šířka tohoto obrazce v palcích|1.5|
|Vystavená Barva výplně jako vlastnost<br /><br /> Zpřístupněný režim přechodu výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vykrytý styl přerušované čáry jako vlastnost<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True` může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|Ne|
|Description|Slouží k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tento obrazec.|\<none>|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento element.|\<none>|
|Image|Cesta k souboru obrázku, který se používá pro tento obrazec.|\<none>|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))