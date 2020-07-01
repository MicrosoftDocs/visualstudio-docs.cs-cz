---
title: Vlastnosti obrazových obrazců
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a9fc3c2d9c7f3f30f035eed036d2a9fb63d667
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520845"
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

Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

Obrazce obrázků mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně tohoto obrazce|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce|Vodorovně|
|Má výchozí spojovací body|Pokud `True` bude obrazec používat horní, dolní, levý a pravý spojovací bod ve vygenerovaném návrháři.|False|
|Barva obrysu|Barva obrysu tohoto obrazce|Black|
|Styl přerušované čáry obrysu|Styl přerušování obrysu tohoto obrazce (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Plná|
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce|0,03125|
|Barva textu|Barva použitá pro text dekoratéry, která je přidružena k tomuto obrazci.|Black|
|Modifikátor přístupu|Modifikátor přístupu obrazce geometrie (veřejný nebo interní).|Public|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto obrazce.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z obrazce obrázku ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní obrazec obrázku|Základní třída tohoto obrazce|(žádná)|
|Name|Název tohoto obrazce|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto obrazci.|Aktuální obor názvů|
|Typ popisu|Místo, kde je popisek definován (pevná, proměnná nebo žádný). Je-li tento parametr zadán, je hodnota `Fixed Tooltip Text` vlastnosti použita jako popis; je-li proměnná, je popis tlačítka definován ve vlastním kódu.|žádné|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto obrazci.|\<none>|
|Počáteční výška|Počáteční výška tohoto obrazce v palcích|1|
|Počáteční Šířka|Počáteční šířka tohoto obrazce v palcích|1.5|
|Vystavená Barva výplně jako vlastnost<br /><br /> Zpřístupněný režim přechodu výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vykrytý styl přerušované čáry jako vlastnost<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True` může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|False|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tento obrazec.|\<none>|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento element.|\<none>|
|Image|Cesta k souboru obrázku, který se používá pro tento obrazec.|\<none>|

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)