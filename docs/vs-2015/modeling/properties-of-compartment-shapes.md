---
title: Vlastnosti obrazců oddílů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: bb5730093a9eda6464bd6b67fa09976a4e9cd2f6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216382"
---
# <a name="properties-of-compartment-shapes"></a>Vlastnosti obrazců prostoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obrazce oddílu jsou jedním z obrazce, které můžete použít k zobrazení doménové třídy v jazyka specifického pro doménu. Můžete rozbalit nebo sbalit oddíly.  
  
 Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Obrazce oddílu mají vlastnosti, které jsou uvedeny v následující tabulce.  
  
|Vlastnost|Popis|Výchozí|  
|--------------|-----------------|-------------|  
|Rozbalte výchozí stav sbalení|Pokud `Expanded`, sbaleno se zobrazí při vytvoření. Pokud `Collapsed`, nejsou.|Rozbalení|  
|Barva výplně|Barva výplně tohoto obrazce.|Prázdné|  
|Režim přechodu výplně|Režim přechodu výplně tohoto obrazce.|Vodorovná|  
|Geometrie|Geometrie tohoto obrazce (obdélník nebo zaoblení obdélníku).|Obdélník|  
|Má výchozí body připojení|Pokud `True`obrazce použije nahoře, dole, vlevo a správný připojovací body ve vygenerovaném návrháři.|False|  
|Jeden oddíl hlavičky je viditelný|Pokud `False`a je obrazec vybrán jeden oddíl, není záhlaví tohoto oddílu viditelné.|Hodnota TRUE|  
|Barva obrysu|Barva obrysu tohoto obrazce.|Černá|  
|Styl přerušování obrysu|Styl přerušování obrysu tohoto obrazce (plný, pomlčku, tečka, DashDot, DashDotDot, vlastní).|Plná|  
|Tloušťka obrysu|Tloušťka obrysu tohoto obrazce.|0.03125|  
|Barva textu|Barva použitá pro dekoratéry textu, které jsou spojeny s tímto obrazcem.|Černá|  
|Modifikátor přístupu|Úroveň přístupu obrazec oddílu (`public` nebo `internal`).|Public|  
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojový kód, který je generován z obrazce oddílu|\<žádné >|  
|Generuje Double odvozené|Pokud `True`, se vygeneruje základní třídu a částečné třídy (pro podporu přizpůsobení pomocí přepisů). Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Má vlastní konstruktor|Pokud `True`, poskytneme vám vlastního konstruktoru ve zdrojovém kódu. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojový kód, který je generován z obrazec oddílu (`none`, `abstract` nebo `sealed`).|Žádné|  
|Základní obrazec oddílu|Základní třída tohoto obrazce.|(žádné)|  
|Název|Název tohoto obrazce.|Aktuální název|  
|Obor názvů|Obor názvů, který je přidružen s tímto obrazcem.|Aktuální obor názvů|  
|Popis typu|Jak popisek je definován (fixní, proměnná nebo žádný). Pokud pevně daná, a potom hodnoty `Fixed Tooltip Text` vlastnost se používá jako popis tlačítka; Pokud je proměnná, pak popisek je definován ve vlastním kódu.|žádná|  
|Poznámky|Neformální poznámky, které jsou spojeny s tímto obrazcem.|\<žádné >|  
|Počáteční výška|Počáteční výška tohoto obrazce v palcích. Obrazce oddílu jde výška oddílu záhlaví a nebude možné změnit.|1|  
|Počáteční šířka|Počáteční šířka tohoto obrazce v palcích.|1.5|  
|Barva výplně vystavené jako vlastnost<br /><br /> Režim přechodu výplně vystavené<br /><br /> Barva obrysu vystavena jako vlastnost<br /><br /> Styl přerušování obrysu vystavena jako vlastnost<br /><br /> Vystavené jako vlastnost zpřístupní tloušťku obrysu<br /><br /> Zpřístupní barvu textu|Pokud `True`, může uživatel nastavit vlastnost stanovených tvaru. Nastavit, klikněte pravým tlačítkem na definici obrazce a klikněte na tlačítko **přidat vystavený**.|False|  
|Popis|Používá se k dokumentu vygenerovaného návrháře.|\<žádné >|  
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u tohoto obrazce.|\<žádné >|  
|Pevný Text popisu tlačítka|Text, který se používá pro pevný popis.|\<žádné >|  
|Klíčové slovo nápovědy|Klíčové slovo, je použít k indexování nápovědy klávesy F1 pro tento obrazec.|\<žádné >|  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



