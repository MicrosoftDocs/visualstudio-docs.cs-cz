---
title: Vlastnosti geometrických obrazců | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10b6d282475d3298f15319d89684f9b042bee5f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671404"
---
# <a name="properties-of-geometry-shapes"></a>Vlastnosti geometrických obrazců
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí obrazců geometrie můžete určit, jak se mají instance doménových tříd zobrazovat v jazyce specifickém pro doménu. Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Obrazce geometrie mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|--------------|-----------------|-------------|
|Barva výplně|Barva výplně tohoto obrazce|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce (vodorovná, svislá, dopředný, úhlopříčný, obrácený nebo žádný).|Vodorovně|
|Geometrie|Geometrie tohoto obrazce (obdélník, zaoblený obdélník, elipsa nebo kroužek).|Obdélník|
|Má výchozí spojovací body|Pokud `True` bude obrazec používat horní, dolní, levý a pravý spojovací bod ve vygenerovaném návrháři.|Ne|
|Barva obrysu|Barva obrysu tohoto obrazce|Black|
|Styl přerušované čáry obrysu|Styl přerušování obrysu tohoto obrazce (Solid, pomlčka, tečka, čárka tečka, čárka tečka tečka nebo vlastní).|Plná|
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce|0,03125|
|Barva textu|Barva použitá pro text dekoratéry, která je přidružena k tomuto obrazci.|Black|
|Modifikátor přístupu|Modifikátor přístupu třídy (veřejné nebo interní).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je generována pro tento obrazec.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z obrazce ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní obrazec geometrie|Základní třída tohoto obrazce|(žádná)|
|Název|Název tohoto obrazce|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto obrazci.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka (pevná, proměnná nebo žádný). Je-li tento parametr zadán, je hodnota `Fixed Tooltip Text` vlastnosti použita jako popis; je-li proměnná, je popis tlačítka definován ve vlastním kódu.|Žádné|
|Poznámky|Neformální poznámky, které jsou spojeny s tímto elementem.|\<none>|
|Počáteční výška|Počáteční výška tohoto obrazce v palcích|1|
|Počáteční Šířka|Počáteční šířka tohoto obrazce v palcích|1.5|
|Vystavená Barva výplně jako vlastnost<br /><br /> Zpřístupněný režim přechodu výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vykrytý styl přerušované čáry jako vlastnost<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|Pokud `True` může uživatel nastavit uvedenou vlastnost tvaru. Pokud to chcete nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na **Přidat vystavené**.|Ne|
|Popis|Popis, který se používá k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tento obrazec.|\<none>|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento tvar.|\<none>|

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
