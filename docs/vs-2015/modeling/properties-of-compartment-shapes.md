---
title: Vlastnosti obrazců oddílů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3caf9828f678c72bf756063183f7d867c5c0e66
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652050"
---
# <a name="properties-of-compartment-shapes"></a>Vlastnosti obrazců prostoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obrazce oddílu jsou jedním z tvarů, které můžete použít k zobrazení doménové třídy v jazyce specifickém pro doménu. Můžete rozbalit a sbalit oddíly.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Obrazce oddílů mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|--------------|-----------------|-------------|
|Výchozí rozbalit stav sbalení|Pokud `Expanded`, oddíly se zobrazí při vytváření. Pokud `Collapsed`, nejsou.|Rozbalil|
|Barva výplně|Barva výplně tohoto obrazce|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce|Horizontální|
|Geometrie|Geometrie tohoto obrazce (obdélník nebo zaoblený obdélník)|plocha|
|Má výchozí spojovací body|Pokud `True`, tvar použije ve vygenerovaném návrháři horní, dolní, levý a pravý spojovací bod.|False|
|Je viditelný nadpis v jednom oddílu|Pokud `False` a tvar má jeden oddíl, záhlaví oddílu není viditelné.|Podmínka|
|Barva obrysu|Barva obrysu tohoto obrazce|zůstane|
|Styl přerušované čáry obrysu|Styl přerušování obrysu tohoto obrazce (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka, vlastní).|Solid|
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce|0,03125|
|Barva textu|Barva použitá pro text dekoratéry, která je přidružena k tomuto obrazci.|zůstane|
|Modifikátor přístupu|Úroveň přístupu k obrazci oddílu (`public` nebo `internal`).|Public|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z tohoto obrazce oddílu|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, bude vygenerována jak základní třída, tak i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud `True`, bude ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z obrazce oddílu (`none`, `abstract` nebo `sealed`).|Žádné|
|Základní obrazec oddílu|Základní třída tohoto obrazce|nTato|
|Name|Název tohoto obrazce|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto obrazci.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka (pevná, proměnná nebo žádný). Pokud je pevná, pak se jako popis používá hodnota vlastnosti `Fixed Tooltip Text`; Pokud je proměnná, pak je popis definovaný ve vlastním kódu.|žádná|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto obrazci.|\<none >|
|Počáteční výška|Počáteční výška tohoto obrazce v palcích U obrazců oddílu se jedná o výšku pouze oddílu záhlaví a nelze ji změnit.|první|
|Počáteční Šířka|Počáteční šířka tohoto obrazce v palcích|1,5|
|Vystavená Barva výplně jako vlastnost<br /><br /> Zpřístupněný režim přechodu výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vykrytý styl přerušované čáry jako vlastnost<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True`, může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|False|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři pro tento obrazec.|\<none >|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none >|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento tvar.|\<none >|

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
