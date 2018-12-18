---
title: Integrace modelů UML s jinými modely a nástroji | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d1cc5a26a9c2febb0dd1dff3c0d14ba3786dde9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764130"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrace modelů UML s jinými modely a nástroji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modely UML je možné integrovat s jinými modely a jazyky specifickými pro doménu.  
  
 Napsáním kódu rozšíření provádět celou řadu funkcí můžete integrovat modely následujícími způsoby:  
  
 Připojte odkazy z libovolného elementu k ostatním položkám, jako jsou například soubory nebo na prvky v dalších modelů.  
 V elementu UML můžete ukládat odkazy na další prvky UML, souborů a dalších objektů podle jejich identity jako řetězce kódování.  
  
 Můžete například napsat rozšíření, které lze propojit žádnou akci UML (to znamená, elementu v diagramu činnosti) do jiného diagramu činnosti. Když uživatel pokliká akce, otevře se jiného diagramu. To umožňuje uživateli zadat s dalšími podrobnostmi akce.  
  
 Existují dva způsoby, ve kterých můžete ukládat řetězce a další data v libovolný element:  
  
- **Vlastnosti stereotypu.** Můžete definovat profil UML, ve kterém definujete stereotypu, která přidává vlastnosti k zadané typy prvku modelu UML. Například můžete definovat profil, který přidává vlastnost s názvem **MoreDetail** akci UML. Můžete napsat kód, rozšíření, že úložiště propojení dat v akci použitím stereotyp na akci, a potom ukládání dat ve vlastnosti.  
  
   Stereotyp a její vlastnosti jsou viditelné pro uživatele v okně Vlastnosti.  
  
   Nasazení tohoto rozšíření, bude balíček definice profilu a kódu rozšíření v jediném [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření.  
  
   Další informace najdete v tématu [definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md).  
  
   Ukázkový projekt, ve kterém je nasazený profil společně s příkazy a obslužnými rutinami gest, naleznete v tématu [vzorku: profilů UML](http://go.microsoft.com/fwlink/?LinkID=213811).  
  
- **Odkazy.** Sada řetězců můžete připojit k libovolnému prvku UML. Můžete napsat kód, který ukládá informace, jako je název souboru nebo identifikátor GUID jiného elementu. To můžete udělat bez zadání dalších definic. Odkazy nejsou přímo viditelná pro uživatele.  
  
   Další informace najdete v tématu [připojení referenčních řetězců k UML model prvky](../modeling/attach-reference-strings-to-uml-model-elements.md). Ukázku najdete v tématu [propojení elementů UML diagramů nebo jiných souborů](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
  Existují dva způsoby, jak kódovat odkazy na prvky modelu:  
  
- **Identifikátor GUID a název souboru** cílového elementu modelu a model, který ji obsahuje nebo konkrétní diagram, který se zobrazí.  
  
   Příklad najdete v tématu [propojení elementů UML diagramů nebo jiných souborů](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
- **Odkazy na ModelBus.** ModelBus je architektura určená k vytváření a překladu odkazů mezi modely. Její součástí jsou nástroje pro výběr ModelBus, který umožňuje uživateli vybrat prvek v modelu. Pomáhá také uživatele k vyřešení odkazů, které byly ztraceny z důvodu změn v cílovém modelu.  
  
   Další informace najdete v tématu [integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
  Šíření změny z jednoho modelu.  
  Název elementu může třeba synchronizovat s názvem propojené diagramu tak, že pokud uživatel změní jednu, druhý také změní. Jak to udělat dvěma způsoby:  
  
1. **Pravidla vmsdk následující položky** je možné změny uvnitř stejného modelu.  
  
    Příklad najdete v tématu [propojení elementů UML diagramů nebo jiných souborů](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
2. **Události vmsdk následující položky** je možné šířící změny mimo model – třeba, změňte název souboru dokumentu, propojené nebo změně prvku v jiném modelu.  
  
   Informace o obou těchto mechanismů najdete v tématu [postupy: reakce na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
   Přetáhněte prvků, které se zkopírují z jednoho modelu na jiný  
   Můžete nechat uživatele vytvořit prvky přetažením položky do diagramu UML. Vytvořený element nemá být kopii původní. Například můžete umožnit uživateli přetáhnout diagram aktivity z Průzkumníka řešení do jiného diagramu činnosti, vytvořte novou akci.  
  
   Další informace najdete v části [definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) a [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="samples"></a>Ukázky kódu  
 Podrobnosti najdete v ukázce kódu [propojení elementů UML diagramů nebo jiných souborů](http://go.microsoft.com/fwlink/?LinkId=213813). Ukázka umožňuje uživatelům přetažením souboru na libovolný prvek UML a později otevřít dvojitým kliknutím element. Diagram aktivity může například odkaz na prvek případu použití. Zobrazuje ikona, u které prvky mají odkazy.  
  
 Tento vzorový kód ukazuje následujících postupů:  
  
- [Připojení referenčních řetězců k elementům modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
   Vzorový kód ukládá cesty k souborům a element identifikátory GUID referenčních řetězců, které jsou spojeny s prvkem.  
  
- Jak přidat dekoratéry elementů UML. Obecné informace o dekoratéry najdete v tématu [přizpůsobení textových a obrazových polí](../modeling/customizing-text-and-image-fields.md).  
  
   Ukázka přidá dekoratér bitové kopie, aby vytvořené tvary UML.  
  
- [Postupy: reakce na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
   Vzorek ukazuje, jak definovat pravidlo, které jsou reaguje na nové obrazce v diagramu.  
  
- [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
   Vzorek ukazuje, jak zpracovávat položky přetažen z Průzkumníka Windows (nebo Průzkumníka souborů), Průzkumník řešení a další prvky UML.  
  
  Příklad, ve kterém je UML model číst DSL, najdete v části [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="see-also"></a>Viz také  
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Postupy: reakce na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [Ukázka: Profilů UML](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [Propojení elementů UML diagramů nebo jiných souborů](http://go.microsoft.com/fwlink/?LinkId=213813)



