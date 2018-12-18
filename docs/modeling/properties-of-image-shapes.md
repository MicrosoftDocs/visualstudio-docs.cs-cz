---
title: Vlastnosti obrazových obrazců
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20da1fc95160be69c1388f9d2986c7dc254eefa2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967126"
---
# <a name="properties-of-image-shapes"></a>Vlastnosti obrazových obrazců

Obrazce obrázku můžete použít k určení, jak se zobrazí ve vygenerovaném návrháři doménovými třídami. Definování obrazce obrázku tak, že nastavíte `Image` vlastnost třídy do souboru předdefinované. Podporují se následující formáty:

- GIF

- .jpg

- .jpeg

- BMP

- .wmf

- .EMF

- ve formátu PNG

Ve výchozím nastavení, soubory Návrháře prostředků, jako jsou obrázky, jsou umístěny v **prostředky** složky **Dsl** projektu.

Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

Obrazce obrázku mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně tohoto obrazce.|Prázdné|
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce.|Vodorovná|
|Má výchozí body připojení|Pokud `True`obrazce použije nahoře, dole, vlevo a správný připojovací body ve vygenerovaném návrháři.|False|
|Barva obrysu|Barva obrysu tohoto obrazce.|Černá|
|Styl přerušování obrysu|Styl přerušování obrysu tohoto obrazce (plný, Dash, tečka, DashDot, DashDotDot nebo vlastní).|Plná|
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce.|0.03125|
|Barva textu|Barva, která je použitá pro dekoratéry textu, které jsou spojeny s tímto obrazcem.|Černá|
|Modifikátor přístupu|Modifikátor přístupu tohoto obrazce Geometrie (veřejné nebo interní).|Public|
|Vlastní atributy|Použít k přidání atributů do třídy zdrojový kód, který je generován z tohoto obrazce.|\<žádné >|
|Generuje Double odvozené|Pokud `True`, se vygeneruje základní třídu a částečné třídy (pro podporu přizpůsobení pomocí přepisů). Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud `True`, poskytneme vám vlastního konstruktoru ve zdrojovém kódu. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojový kód, který je generován z obrazce obrázku (`none`, `abstract` nebo `sealed`).|žádná|
|Základní obrazec obrázku|Základní třída tohoto obrazce.|(žádné)|
|Název|Název tohoto obrazce.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen s tímto obrazcem.|Aktuální obor názvů|
|Popis typu|Místo, kde je definován popisek (fixní, proměnná nebo žádný). Pokud pevně daná, a potom hodnoty `Fixed Tooltip Text` vlastnost se používá jako popis tlačítka; Pokud je proměnná, pak popisek je definován ve vlastním kódu.|žádná|
|Poznámky|Neformální poznámky, které jsou spojeny s tímto obrazcem.|\<žádné >|
|Počáteční výška|Počáteční výška tohoto obrazce v palcích.|1|
|Počáteční šířka|Počáteční šířka tohoto obrazce v palcích.|1.5|
|Barva výplně vystavené jako vlastnost<br /><br /> Režim přechodu výplně vystavené<br /><br /> Barva obrysu vystavena jako vlastnost<br /><br /> Styl přerušování obrysu vystavena jako vlastnost<br /><br /> Vystavené jako vlastnost zpřístupní tloušťku obrysu<br /><br /> Zpřístupní barvu textu|Pokud `True`, může uživatel nastavit vlastnost stanovených tvaru. Nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na tlačítko **přidat vystavený**.|False|
|Popis|Používá se k dokumentu vygenerovaného návrháře.|\<žádné >|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u tohoto obrazce.|\<žádné >|
|Pevný Text popisu tlačítka|Text, který se používá pro pevný popis.|\<žádné >|
|Klíčové slovo nápovědy|Klíčové slovo, je použít k indexování nápovědy klávesy F1 pro tento element.|\<žádné >|
|Image|Cesta k souboru obrázku, který se používá pro tento obrazec.|\<žádné >|

## <a name="see-also"></a>Viz také

- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)