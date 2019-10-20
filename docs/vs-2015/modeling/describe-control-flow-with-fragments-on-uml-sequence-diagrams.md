---
title: Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f48891107c2eb3250b6b050e00c3650812d386
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669819"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Kombinované fragmenty* v sekvenčním diagramu UML umožňují zobrazit cykly, větve a další alternativy.

 Kombinovaný fragment se skládá z jednoho nebo více *operandů interakce*a každý z nich obsahuje jednu nebo více zpráv, interakce používá nebo kombinované fragmenty.

> [!NOTE]
> Toto téma se týká fragmentů v sekvenčních diagramech. Další informace o tom, jak číst sekvenční diagramy UML, najdete v tématu [sekvenční diagramy UML: referenční informace](../modeling/uml-sequence-diagrams-reference.md). Další informace o vykreslování sekvenčních diagramů UML najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

 ![Kombinovaný fragment se dvěma operandy interakce](../modeling/media/uml-seqfragments.png "UML_SeqFragments")

 Prvky zobrazené na obrázku jsou následující.

1. Kombinovaný fragment. Existuje několik druhů kombinovaných fragmentů. V tomto příkladu je Kombinovaný fragment kombinace kláves ALT, který můžete použít k zobrazení, zda mohou nastat alternativní posloupnosti zpráv.

2. Operandy interakce. Každý Kombinovaný fragment obsahuje alespoň jeden operand interakce, který může obsahovat zprávy, použití interakce a menší kombinované fragmenty. V tomto příkladu má Kombinovaný fragment ALT dvě operace interakce, které zobrazují dvě alternativní posloupnosti zpráv.

3. Jednotlivé operandy interakce můžete vybrat samostatně kliknutím dovnitř. V tomto příkladu je vybrána horní operand interakce, aby bylo možné zobrazit jeho hranici. Obvykle je viditelný pouze dělicí čára mezi operandy interakce.

    > [!NOTE]
    > Chcete-li vybrat horní operand interakce, nemusíte kliknout na horní část kombinovaného fragmentu.

4. Chrání. Každému operandu interakce můžete dát ochranu. Popisuje podmínku, pod kterou budou provedeny zprávy uvnitř operandu interakce.

## <a name="creating-combined-fragments"></a>Vytváření kombinovaných fragmentů
 Seznam druhů fragmentů, které můžete vytvořit, najdete v tématu [typy kombinovaného fragmentu](#KindsOfFragment).

#### <a name="to-create-a-combined-fragment"></a>Vytvoření kombinovaného fragmentu

1. Vyberte jednu zprávu nebo posloupnost zpráv, které začínají stejnou životností nebo výskytem spuštění.

   > [!NOTE]
   > Pokud vyberete více než jednu zprávu, musí vytvořit nepřerušovanou sekvenci.

2. Klikněte pravým tlačítkem myši na jednu ze zpráv, ukažte na možnost **prostorový s**a pak klikněte na druh kombinovaného fragmentu, který chcete, jako je například kombinace **kombinace kláves ALT**.

    Zobrazí se nový Kombinovaný fragment. Nadpis označuje druh kombinovaného fragmentu, který jste vybrali, například **ALT**.

    Uvnitř kombinovaného fragmentu je k dispozici fragment obsahující zprávy, které jste vybrali.

   K některým druhům kombinovaného fragmentu můžete přidat další operandy interakce.

   Po změně uspořádání zpráv v rámci kombinovaného fragmentu vyberte možnost změnit **uspořádání rozložení** v místní nabídce, aby se změnila velikost kombinovaného rámce fragmentu.

#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Přidání nového operandu interakce do kombinovaného fragmentu

1. Klikněte pravým tlačítkem myši na prázdné místo v rámci operandu interakce (2), mimo libovolný obsažený fragment a pod nadpisem kombinovaného fragmentu.

2. Přejděte na **Přidat**.

3. Klikněte na **operand interakce před**nebo **operand interakce po**.

4. Do nového operandu interakce můžete přidat zprávy pomocí nástrojů pro zprávy nebo zkopírováním a vložením existujících zpráv.

   Vlastnost **Guard** operandu interakce můžete nastavit tak, aby popsala podmínky, za kterých se zprávy uvnitř nich provádějí. Například v kombinovaných fragmentech **smyčky** můžete použít Guard k určení podmínky, během které smyčka pokračuje. V kombinovaném fragmentu **ALT** můžete zadat samostatnou podmínku pro každý operand interakce.

#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Nastavení ochrany operandu interakce

1. Klikněte na prázdné místo uvnitř operandu interakce (2), mimo libovolný obsažený fragment.

    Kolem operandu interakce se zobrazí ohraničení výběru a kolem podmínky Guard.

    Nadpis v okně **vlastnosti** zobrazuje **operand interakce**.

2. Zadejte podmínku Guard.

    Podmínka se zobrazí u horní části fragmentu (4).

   Můžete nastavit vlastnosti některých druhů kombinovaných fragmentů.

#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Nastavení nebo zobrazení vlastností kombinovaného fragmentu

- Klikněte pravým tlačítkem na název kombinovaného fragmentu a pak klikněte na **vlastnosti**.

    > [!NOTE]
    > Různé druhy kombinovaného fragmentu mají různé vlastnosti.

## <a name="KindsOfFragment"></a>Druhy kombinovaného fragmentu

### <a name="fragments-describing-control-flow"></a>Fragmenty popisující tok řízení
 Jednoduchý sekvenční diagram zobrazuje jenom jednu typickou sekvenci. Pomocí následujících typů kombinovaných fragmentů můžete popsat variace, ke kterým může dojít v různých případech.

|Typ fragmentu|Popis|
|-------------------|-----------------|
|**Přihlásit**|Volitelné. Vloží sekvenci, která může nebo nemusí nastat. V poli Guard můžete určit podmínku, za kterou dojde.|
|**ALT**|Obsahuje seznam fragmentů, které obsahují alternativní posloupnosti zpráv. V některých případech dojde pouze k jedné sekvenci.<br /><br /> Do každého fragmentu můžete umístit Guard, abyste označili, pod jakým podmíněným stavem může běžet. Guard **Else** označuje fragment, který by se měl spustit, pokud žádné jiné Guard neplatí. Pokud jsou všechny ochranné kryty nepravdivé a neexistují žádné **Další**, nespustí se žádné z fragmentů.|
|**Procházet**|Fragment se několikrát opakuje. V poli Guard můžete určit podmínku, pod kterou by se měla opakovat.<br /><br /> Kombinované fragmenty smyčky mají vlastnosti **minimum** a **Maximum**, které označují minimální a maximální počet pokusů, kolikrát může být fragment opakován. Výchozí hodnota není nijak omezena.|
|**Rozdělován**|Pokud se tento fragment spustí, zbývající část sekvence se odopustila. Můžete použít Guard k označení podmínky, ve které dojde k přerušení.|
|**Nemají**|Zpracování. Události v fragmentech je možné pronechávat.|
|**Kritické**|Používá se v rámci fragmentu par nebo Seq. Označuje, že zprávy v tomto fragmentu nesmí být prokládané s ostatními zprávami.|
|**SEQ**|Existují dva nebo více fragmentů operandů. Zprávy týkající se stejné životnosti se musí nacházet v pořadí fragmentů. Pokud nezahrnují stejné životnosti, mohou být zprávy z různých fragmentů prokládané paralelně.|
|**Zásadní**|Existují dva nebo více fragmentů operandů. Fragmenty musí nastat v uvedeném pořadí.|

### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmenty o tom, jak interpretovat sekvenci
 Sekvenční diagram ve výchozím nastavení uvádí řadu zpráv, ke kterým může dojít. V běžícím systému se další zprávy mohou vyskytnout, že jste se nerozhodli zobrazit v diagramu.

 Ke změně této interpretace lze použít následující typy fragmentů.

|Typ fragmentu|Popis|
|-------------------|-----------------|
|**Byste**|Určuje seznam zpráv, které tento fragment popisuje. V běžícím systému se můžou vyskytovat další zprávy, ale pro účely tohoto popisu nejsou významné.<br /><br /> Zadejte seznam do vlastnosti **Messages** .|
|**Ohled**|Seznam zpráv, které tento fragment nepopisuje. Mohou nastat ve spuštěném systému, ale nejsou významné pro účely tohoto popisu.<br /><br /> Zadejte seznam do vlastnosti **Messages** .|
|**Uplatňuje**|Fragment operandu určuje pouze platné sekvence. Obvykle se používá v rámci typu "vzít" nebo ignorovat fragment.|
|**Výdej**|Sekvence zobrazená v tomto fragmentu nesmí nastat. Obvykle se používá v rámci typu "vzít" nebo ignorovat fragment.|

## <a name="see-also"></a>Viz také
 [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md) pro [sekvenční diagramy UML: referenční informace](../modeling/uml-sequence-diagrams-reference.md) k [úpravám modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)
