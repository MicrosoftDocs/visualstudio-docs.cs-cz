---
title: 'Sekvenční diagramy UML: referenční informace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9b02bbad4fa897404f6c20e12b1705a3ae9ac8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661706"
---
# <a name="uml-sequence-diagrams-reference"></a>Sekvenční diagramy UML: Referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio znázorňuje *sekvenční diagram* interakci, která představuje sekvenci zpráv mezi instancemi tříd, komponent, subsystémů nebo Actors. Čas vychází z diagramu a zobrazuje tok řízení od jednoho účastníka k druhému. Použijte sekvenční diagramy k vizualizaci instancí a událostí namísto tříd a metod. V diagramu se může zobrazit víc než jedna instance stejného typu. Může se také zobrazit více než jeden výskyt stejné zprávy.

 Sekvenční diagramy UML jsou součástí modelu UML a existují pouze v rámci projektů modelování UML. Chcete-li vytvořit sekvenční diagram UML, v nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**. Přečtěte si další informace o tom, jak vytvářet a kreslit [sekvenční diagramy UML](../modeling/uml-sequence-diagrams-guidelines.md) nebo [diagramy modelování UML](../modeling/edit-uml-models-and-diagrams.md) .

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-sequence-diagrams"></a>Čtení sekvenčních diagramů
 Následující tabulka popisuje prvky, které lze zobrazit v sekvenčním diagramu. Přečtěte si další informace o těchto [vlastnostech prvků](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).

 ![Části sekvenčního diagramu](../modeling/media/uml-sequence.png "UML_Sequence")

|**Automatického**|**Element**|**Popis**|
|---------------|-----------------|---------------------|
|první|**Životnost**|Svislá čára, která představuje sekvenci událostí, ke kterým dojde v rámci interakce, zatímco čas pokračuje v řádku. Tímto účastníkem může být instance třídy, komponenty nebo objektu actor.|
|odst|**Tříd**|Účastník, který je externě pro systém, který vyvíjíte.<br /><br /> Symbol objektu actor lze vytvořit v horní části životnosti nastavením jeho vlastnosti **actor** .|
|3|**Synchronní zpráva**|Odesílatel čeká na odpověď na synchronní zprávu předtím, než pokračuje. Diagram znázorňuje volání i návrat. Synchronní zprávy slouží k reprezentaci běžných volání funkcí v rámci programu a také k jiným druhům zprávy, která se chová stejným způsobem.|
|4|**Asynchronní zpráva**|Zpráva, která nevyžaduje odpověď předtím, než odesilatel pokračuje. Asynchronní zpráva zobrazuje pouze volání od odesílatele. Slouží k reprezentaci komunikace mezi samostatnými vlákny nebo vytvořením nového vlákna.|
|5|**Výskyt spuštění**|Svislý šedý obdélník, který se zobrazí na životnosti účastníka a představuje období, po kterém účastník provádí operaci.<br /><br /> Spuštění začíná, když účastník obdrží zprávu. Pokud byla zpráva iniciovaná jako synchronní zpráva, spuštění skončí s šipkou «Return» zpátky odesilateli.|
|6|**Zpráva zpětného volání**|Zpráva, která se vrátí účastníkovi, který čeká na návrat z předchozího volání. Výsledný výskyt spuštění se zobrazí nad existujícím.|
|čl|**Samostatná zpráva**|Zpráva od účastníka do sebe samé. Výsledný výskyt spuštění se zobrazí nad odesláním.|
|8|**Vytvořit zprávu**|Zpráva, která vytvoří účastníka Pokud účastník obdrží zprávu o vytvoření, měla by být první obdržená.|
|9|**Nalezená zpráva**|Asynchronní zpráva z neznámého nebo neurčeného účastníka.|
|10pruhový|**Ztracená zpráva**|Asynchronní zpráva na neznámého nebo neurčeném účastníkovi.|
|odst|**Vytvořena**|Komentář lze připojit k jakémukoli bodu na životnosti.|
|12,5|**Použití interakce**|Vloží sekvenci zpráv, které jsou definovány v jiném diagramu.<br /><br /> Chcete-li vytvořit **interakci**, klikněte na nástroj a přetáhněte mezi životnosti, které chcete zahrnout.|
|13,5|**Kombinovaný fragment**|Kolekce fragmentů. Každý fragment může uzavřít jednu nebo více zpráv. Existují různé druhy kombinovaných fragmentů. Další informace najdete v tématu [Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Chcete-li vytvořit fragment, klikněte pravým tlačítkem myši na zprávu, přejděte na příkaz **uzavřít pomocí**a potom klikněte na typ fragmentu.|
|čtrnáct|**Ochrana fragmentů**|Dá se použít k určení podmínky, která se vztahuje na to, jestli dojde k fragmentu.<br /><br /> Pokud chcete nastavit ochranu, vyberte nějaký fragment a potom vyberte ochranu a zadejte hodnotu.|
|**Znak**|**Událost zničení**|Představuje bod, ve kterém je objekt odstraněn nebo již není přístupný. Zobrazuje se v dolní části každé životnosti.|
||**Působení**|Kolekce zpráv a životností, které jsou zobrazeny v sekvenčním diagramu. Chcete-li zobrazit vlastnosti interakce, je nutné ji vybrat v **Průzkumníku modelů UML**.|
||**Sekvenční diagram**|Diagram, který zobrazuje interakci. Chcete-li zobrazit jeho vlastnosti, klikněte na prázdnou část diagramu. **Poznámka:**  Všechny názvy sekvenčního diagramu, zobrazená interakce a soubor, který obsahuje diagram, mohou být rozdílné.|

## <a name="see-also"></a>Viz také
 [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md) [upravují modely UML a diagramy](../modeling/edit-uml-models-and-diagrams.md) [případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) diagramy [tříd](../modeling/uml-class-diagrams-reference.md) UML: referenční [diagramy komponent UML](../modeling/uml-component-diagrams-reference.md) : Referenční dokumentace diagramů komponent UML: [referenční](../modeling/uml-component-diagrams-reference.md) dokumentace
