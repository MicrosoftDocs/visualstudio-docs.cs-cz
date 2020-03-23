---
title: Přehled uživatelského rozhraní nástrojů pro specifické domény | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bffb1f7fe6449f078c21c14b0a070cbd23db539
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652127"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Přehled uživatelského rozhraní Jazykových nástrojů specifických pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při prvním otevření řešení nástroje jazyka DSL (Domain [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Specific Language Tools) v programu bude uživatelské rozhraní vypadat podobně jako následující obrázek.

 ![návrhář dsl](../modeling/media/dsl-designer.png "dsl_designer")

 V následující tabulce je vysvětleno, jak se používají části ui.

|**Element**|**Definice**|
|-----------------|--------------------|
|Diagram|Diagram zobrazuje model domény.<br /><br /> Diagram má dvě strany. Jedna strana definuje typy prvků v modelech. Druhá strana definuje, jak budou vaše modely vypadat na obrazovce.|
|Sada nástrojů|Přetáhněte nástroje z panelu nástrojů a přidejte do diagramu třídy domén a typy tvarů. Chcete-li přidat relace, spojnice a mapy obrazců, klepněte na nástroj, potom klepněte na zdrojový uzel v diagramu a potom na cílový uzel.|
|Průzkumník modelu DSL|**Dsl Explorer** se zobrazí, když definice DSL je aktivní okno. Zobrazuje DSL jako strom. DSL Explorer umožňuje upravovat funkce modelu, které nejsou zobrazeny v diagramu. Můžete například přidat položky panelu nástrojů a zapnout proces ověření pomocí **průzkumníka DSL**.|
|Okno Podrobnosti dsl|Okno **Podrobnosti DSL** zobrazuje vlastnosti prvků modelu domény, které umožňují řídit způsob zobrazení prvků a kopírování a odstraňování prvků.<br /><br /> - Ve výchozím nastavení se vedle oken **Seznam chyb** a **Výstup** zobrazí okno **Podrobnosti DSL.**|

## <a name="the-domain-model-diagram"></a>Diagram modelu domény
 Diagram modelu domény je rozdělen na dvě části. Jedna strana diagramu zobrazuje prvky a vztahy v modelu. Na druhé straně ukazuje, jak má být model zobrazen, a zahrnuje obrazce, které se používají k zobrazení prvků a vlastností diagramu modelu. Následující obrázek znázorňuje prvky diagramu.

 ![dsl designer s plavkou](../modeling/media/dsl-desinger.png "dsl_desinger")

 Následující tabulka vysvětluje některé prvky diagramu modelu domény.

|**Termín**|**Definice**|
|--------------|--------------------|
|Třída domény|Třídy domény jsou typy prvků ve vašich modelech.<br /><br /> Třída domény se může v diagramu zobrazit více než jednou, pokud je cílem více než jednoho vztahu.<br /><br /> Chcete-li přidat třídu domény, přetáhněte nástroj třídy domény z **panelu nástrojů** na stranu **Třídy a vztahy** diagramu.|
|Vztah domény|Vztahy domény jsou typy vazeb mezi prvky ve vašich modelech.<br /><br /> *Vztah vložení* označuje, že cílový prvek je vlastněn nebo obsažen zdrojovým prvkem a zobrazí se jako plná čára. Každý prvek v modelu by měl být cílem jednoho vztahu vkládání, aby model tvoří strom. *Referenční vztah* označuje obecné propojení mezi prvky modelu a zobrazí se jako přerušovaná čára. Libovolný prvek může mít libovolný počet odkazů.<br /><br /> Vytvořte relaci kliknutím na nástroj na **panelu nástrojů**, kliknutím na třídu zdrojové domény a následným klepnutím na cílovou třídu.|
|Tvary a spojnice|Tvary určují, jak mají být prvky modelu zobrazeny v diagramu DSL., Konektory určují řádky v diagramu DSL, který lze použít k zobrazení relací.<br /><br /> Chcete-li vytvořit obrazec nebo spojnici, přetáhněte nástroj na stranu **prvky diagramu.**|
|Mapy obrazců|Mapa obrazce se zobrazí jako čára v diagramu modelu domény, která propojuje obrazec s zobrazenou třídou domény nebo spojnicí s zobrazeným vztahem domény.|

## <a name="see-also"></a>Viz také
 [Přehled jazykových nástrojů specifických pro doménu,](../modeling/overview-of-domain-specific-language-tools.md) který je [jazykově slovníku specifických pro](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) [doménu, který přizpůsobuje a rozšiřuje jazyk specifický pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)
