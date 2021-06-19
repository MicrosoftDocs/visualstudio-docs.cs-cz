---
title: Vlastnosti obrazových obrazců
description: Přečtěte si o tvarech obrázků a o tom, jak lze pomocí obrazců určit, jak se třídy domény zobrazují ve vygenerované návrháři.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98198b1197de6f5fda6a05a5bae58378a323f718
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390552"
---
# <a name="properties-of-image-shapes"></a>Vlastnosti obrazových obrazců

Pomocí obrazců můžete určit, jak se třídy domény zobrazují ve vygenerované návrháři. Definujte tvar obrázku nastavením `Image` vlastnosti třídy na předdefinovaný soubor obrázku. Podporují se následující formáty:

- .gif

- .jpg

- .jpeg

- .bmp

- Wmf

- Emf

- .png

Ve výchozím nastavení jsou soubory prostředků návrháře, například soubory obrázků, umístěny ve složce **Resources** v **projektu Dsl.**

Další informace najdete v [tématu Definování jazyka Domain-Specific .](../modeling/how-to-define-a-domain-specific-language.md) Další informace o použití těchto vlastností naleznete v tématu [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

Tvary obrázků mají vlastnosti uvedené v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně tohoto tvaru|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto tvaru.|Vodorovně|
|Má výchozí body připojení|Pokud použije tvar horní, dolní, levý a pravý spojovací `True` bod ve vygenerované návrháři.|Ne|
|Barva obrysu|Barva obrysu tohoto tvaru.|Black|
|Styl pomlčky obrysu|Styl pomlčky obrysu tohoto tvaru (Solid, Dash, Dot, DashDot, DashDotDot nebo Custom).|Plná|
|Tloušťka obrysu|Tloušťka obrysu tohoto tvaru|0.03125|
|Barva textu|Barva, která se používá pro dekorátory textu, které jsou přidruženy k tomuto tvaru.|Black|
|Modifikátor přístupu|Modifikátor přístupu tvaru geometrie (veřejný nebo interní).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je generována z tohoto tvaru.|\<none>|
|Vygeneruje dvojitě odvozený|Pokud `True` , bude vygenerována základní i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud , bude ve zdrojovém `True` kódu k dispozici vlastní konstruktor. Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z tvaru obrázku ( `none` `abstract` nebo `sealed` ).|žádné|
|Tvar základního obrázku|Základní třída tohoto tvaru.|(žádná)|
|Name|Název tohoto tvaru.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto tvaru.|Aktuální obor názvů|
|Typ popisu|Místo, kde je popis definovaný (pevný, proměnný nebo žádný). Pokud je tato hodnota opravená, použije se hodnota vlastnosti jako popisek. Pokud je proměnná proměnná, popis je definovaný ve `Fixed Tooltip Text` vlastním kódu.|žádné|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto tvaru.|\<none>|
|Počáteční výška|Počáteční výška tohoto tvaru v palcích|1|
|Počáteční šířka|Počáteční šířka tohoto tvaru v palcích|1.5|
|Vystavená barva výplně jako vlastnost<br /><br /> Vystavený přechodový režim výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vystavená vlastnost pomlčky obrysu jako<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|V `True` případě může uživatel nastavit uvedenou vlastnost obrazce. Tuto možnost nastavíte tak, že kliknete pravým tlačítkem na definici obrazce a kliknete na **Add Exposed (Přidat vystavený).**|Ne|
|Description|Slouží k zdokumentování generovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerované návrháři pro tento tvar.|\<none>|
|Oprava textu popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo nápovědy|Klíčové slovo , které se používá k indexování nápovědy F1 pro tento prvek.|\<none>|
|Image|Cesta k souboru obrázku, který se používá pro tento tvar.|\<none>|

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))