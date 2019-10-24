---
title: Vlastnosti obrazových obrazců
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: beb401b4056edd8f1edac5e61d02237c60504cd9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748294"
---
# <a name="properties-of-image-shapes"></a>Vlastnosti obrazových obrazců

Pomocí tvarů obrázků lze určit, jak se ve vygenerovaném návrháři zobrazí doménové třídy. Definujte tvar obrázku nastavením vlastnosti `Image` třídy na předdefinovaný soubor obrázku. Podporovány jsou následující formáty:

- . gif

- . jpg

- . jpeg

- . bmp

- . WMF

- . EMF

- formát. png

Ve výchozím nastavení se soubory prostředků návrháře, jako jsou soubory obrázků, nacházejí ve složce **Resources** v projektu **DSL** .

Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

Obrazce obrázků mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně tohoto obrazce|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce|Horizontální|
|Má výchozí spojovací body|Pokud `True`, tvar použije ve vygenerovaném návrháři horní, dolní, levý a pravý spojovací bod.|False|
|Barva obrysu|Barva obrysu tohoto obrazce|zůstane|
|Styl přerušované čáry obrysu|Styl přerušování obrysu tohoto obrazce (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Solid|
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce|0,03125|
|Barva textu|Barva použitá pro text dekoratéry, která je přidružena k tomuto obrazci.|zůstane|
|Modifikátor přístupu|Modifikátor přístupu obrazce geometrie (veřejný nebo interní).|Public|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto obrazce.|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, bude vygenerována jak základní třída, tak i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud `True`, bude ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z obrazce obrázku (`none`, `abstract` nebo `sealed`).|žádná|
|Základní obrazec obrázku|Základní třída tohoto obrazce|nTato|
|Name|Název tohoto obrazce|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto obrazci.|Aktuální obor názvů|
|Typ popisu|Místo, kde je popisek definován (pevná, proměnná nebo žádný). Pokud je pevná, pak se jako popis používá hodnota vlastnosti `Fixed Tooltip Text`; Pokud je proměnná, pak je popis definovaný ve vlastním kódu.|žádná|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto obrazci.|\<none >|
|Počáteční výška|Počáteční výška tohoto obrazce v palcích|první|
|Počáteční Šířka|Počáteční šířka tohoto obrazce v palcích|1,5|
|Vystavená Barva výplně jako vlastnost<br /><br /> Zpřístupněný režim přechodu výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vykrytý styl přerušované čáry jako vlastnost<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True`, může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|False|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři pro tento obrazec.|\<none >|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none >|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento element.|\<none >|
|Image|Cesta k souboru obrázku, který se používá pro tento obrazec.|\<none >|

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)