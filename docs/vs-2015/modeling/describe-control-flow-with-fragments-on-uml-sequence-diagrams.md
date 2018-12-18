---
title: Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4ab4c65e554e9eef75a1761719ce19f3312e07ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727651"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sekvenčním diagramu UML *kombinované fragmenty* umožňují zobrazit smyčky, větve a další možnosti.  
  
 Do kombinovaného fragmentu se skládá z jedné nebo více *interakce operandy*, a každá z těchto obklopuje jeden nebo více zpráv, interakcí nebo kombinované fragmenty.  
  
> [!NOTE]
>  Toto téma se věnuje fragmentů v sekvenčních diagramech. Další informace o tom, jak číst sekvenčních diagramech UML, naleznete v tématu [sekvenční diagramy UML: referenční](../modeling/uml-sequence-diagrams-reference.md). Další informace o tom, jak nakreslit sekvenční diagramy UML, naleznete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![Kombinované Fragment používá dva operandy interakce](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 Prvky zobrazené na obrázku jsou následující.  
  
1.  Do kombinovaného fragmentu. Existuje několik druhů kombinované fragmenty. V tomto příkladu je Alt kombinovaného fragmentu, což vám umožní zobrazit, že může dojít, alternativní pořadí zpráv.  
  
2.  Operandy interakce. Každý kombinovaného fragmentu obsahuje alespoň jeden operand interakce, které mohou obsahovat zprávy, interakcí a menší kombinované fragmenty. V tomto příkladu kombinaci kláves Alt fragment má dvě operace interakce zobrazující dvě alternativní pořadí zpráv.  
  
3.  Operandem interakce můžete vybrat samostatně kliknutím dovnitř. V tomto příkladu je vybraná operand nejvyšší interakce, tak, aby uvidíte jeho hranice. Obvykle je viditelná pouze zřejmý mezi operandy interakce.  
  
    > [!NOTE]
    >  Vyberte horní interakce operand, že nesmí kliknete na tlačítko Zavřít příliš do horní části kombinovaného fragmentu.  
  
4.  Chrání. Operandem interakce může poskytnout ochranu. Popisuje podmínky, pod kterým bude provedena zprávy uvnitř operand interakce.  
  
## <a name="creating-combined-fragments"></a>Vytvoření kombinované fragmenty  
 Seznam typů fragment můžete vytvořit, naleznete v tématu [typy kombinovat Fragment](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>K vytvoření kombinovaného fragmentu  
  
1. Vyberte jednu zprávu nebo s posloupností zpráv, všechny začíná stejné výskyt životnosti nebo spuštění.  
  
   > [!NOTE]
   >  Pokud vyberete více než jedna zpráva, že musí tvořit bez přerušení pořadí.  
  
2. Klikněte pravým tlačítkem na zprávy, přejděte na **obklopit fragmentem**a potom klikněte na typ kombinovaného fragmentu, můžete se například **Alt kombinovat Fragment**.  
  
    Zobrazí se nové kombinovaného fragmentu. Určuje typ, který jste vybrali, jako například kombinovaného fragmentu záhlaví **Alt**.  
  
    Uvnitř kombinovaného fragmentu je fragment, která obsahuje zprávy, které jste vybrali.  
  
   Můžete přidat další interakce operandy pro některé druhy kombinovaného fragmentu.  
  
   Po změně uspořádání zpráv do kombinovaného fragmentu, zvolte **změnit uspořádání rozložení** v místní nabídce pro změnu velikosti kombinovaného fragmentu rámce.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Chcete-li přidat nový operand interakce do kombinovaného fragmentu  
  
1. Klikněte pravým tlačítkem na prázdné místo uvnitř operand interakce (2), mimo všechny obsažené fragment a pod nadpisem kombinovaného fragmentu.  
  
2. Přejděte na **přidat**.  
  
3. Klikněte na tlačítko **interakce Operand před**, nebo **Operand interakce po**.  
  
4. Můžete taky přidat zprávy uvnitř nové operand interakce pomocí nástrojů, zprávy, nebo zkopírováním a vložením existující zprávy.  
  
   Můžete nastavit **Guard** vlastnost operand interakce popisují podmínky, ve kterých se provádějí zprávy dovnitř. Například v **smyčky** kombinovat fragment, vám pomůže ochranného zařízení zadat podmínky, během které smyčky pokračuje. V **Alt** kombinovat fragment, můžete zadat samostatné podmínku pro každý operand interakce.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Chcete-li nastavit guard operand interakce  
  
1. Klikněte do prázdného místa v operandu interakce (2), mimo všechny obsažené fragment.  
  
    Ohraničení výběru se zobrazí kolem operand interakce a kolem podmínku.  
  
    Záhlaví **vlastnosti** okno zobrazuje **interakce Operand**.  
  
2. Zadejte podmínku.  
  
    Podmínka se zobrazí v horní části fragmentu (4).  
  
   Můžete nastavit vlastnosti některé druhy kombinované fragmenty.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Nastavit nebo zobrazit vlastnosti kombinovaného fragmentu  
  
-   Klikněte pravým tlačítkem na název kombinovaného fragmentu a potom klikněte na tlačítko **vlastnosti**.  
  
    > [!NOTE]
    >  Různé druhy kombinovaného fragmentu mají různé vlastnosti.  
  
##  <a name="KindsOfFragment"></a> Druhy kombinovaného fragmentu  
  
### <a name="fragments-describing-control-flow"></a>Fragmenty popis toku řízení  
 Jednoduchý sekvenční diagram ukazuje pouze jeden typická posloupnost. Následující typy kombinované fragmenty slouží k popisu změn, které mohou nastat v různých případech.  
  
|Typ fragmentu|Popis|  
|-------------------|-----------------|  
|**Odhlásit se**|Volitelné. Vloží sekvenci, která můžou nebo nemusí dojít. Můžete určit, v guard, podmínky, ve kterém se vyskytuje.|  
|**ALT**|Obsahuje seznam fragmenty, které obsahují alternativní pořadí zpráv. Pouze jeden posloupnost ve všech případech mohou oprávnění.<br /><br /> Ochranu můžete umístit v každém fragmentu k označení, za jakých podmínek můžete spustit. Ochranu z **else** označuje fragment, který se má spustit žádné guard má hodnotu true. Pokud jsou všechny chrání false a není žádná **else**, potom žádný fragmentů spustí.|  
|**smyčka**|Fragment zopakuje některé počtu opakování. V ochranného zařízení můžete určit podmínky, pod kterou by měla opakovat.<br /><br /> Smyčka kombinované fragmenty mít vlastnosti **Min** a **maximální**, který udává minimální a maximální počet případů, kdy se fragment můžete opakovat. Výchozí hodnota je bez omezení.|  
|**Konec**|Pokud se provádí tento fragment, opuštění zbývající části sekvence. Ochranného zařízení můžete použít k označení stavu, ve kterém dojde k přerušení.|  
|**Pamětích**|Paralelní. Události v tyto fragmenty mohou být prokládané.|  
|**Kritická**|Použít v rámci pamětích nebo Seq fragment. Označuje, že zprávy v tomto fragmentu nesmí být proloženy další zprávy.|  
|**SEQ**|Existují dva nebo více fragmentů operand. Zprávy týkající se stejnou životnost se musí vyskytovat v pořadí tyto fragmenty. Tam, kde nezahrnují stejné životnosti, zprávy z různých fragmenty mohou být prokládané paralelně.|  
|**Striktní**|Existují dva nebo více fragmentů operand. Tyto fragmenty se musí objevit v daném pořadí.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmenty o tom, jak interpretovat sekvence  
 Ve výchozím nastavení oznámením sekvenční diagram řadu zprávy, které se může stát. Další zprávy v systému, může stát, že jste se rozhodli zobrazit v diagramu.  
  
 Chcete-li změnit toto vyhodnocení je možné následující typy fragment.  
  
|Typ fragmentu|Popis|  
|-------------------|-----------------|  
|**Vezměte v úvahu**|Určuje seznam zpráv, které popisuje tento fragment. Další zprávy může dojít v běžící systém, ale nejsou důležité pro účely tohoto popisu.<br /><br /> Zadejte v seznamu **zprávy** vlastnost.|  
|**Ignorovat**|Seznam zpráv, které tento fragment nepopisuje. Může dojít v běžící systém, ale nejsou důležité pro účely tohoto popisu.<br /><br /> Zadejte v seznamu **zprávy** vlastnost.|  
|**Kontrolní výraz**|Operand fragment určuje pouze platné pořadí. Obvykle se používá v rámci fragment zvažte nebo ignorovat.|  
|**záporné**|Pořadí uvedené v tomto fragmentu nesmí dojít. Obvykle se používá v rámci fragment zvažte nebo ignorovat.|  
  
## <a name="see-also"></a>Viz také  
 [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)



