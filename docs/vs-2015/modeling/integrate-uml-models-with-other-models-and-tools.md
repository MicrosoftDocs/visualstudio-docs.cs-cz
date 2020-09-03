---
title: Integrace modelů UML s jinými modely a nástroji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ea0c562bb9c2a8050fc1365fac19df20232f80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918358"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrace modelů UML s jinými modely a nástroji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modely UML je možné integrovat s jinými modely a s jazyky specifickými pro doménu.

 Modely můžete integrovat následujícími způsoby, a to tak, že napíšete kód rozšíření pro provádění nejrůznějších funkcí:

 Připojte odkazy z libovolného prvku k ostatním položkám, jako jsou například soubory nebo prvky v jiných modelech.
V prvku UML můžete ukládat odkazy na jiné prvky, soubory nebo objekty UML pomocí kódování svých identit jako řetězců.

 Můžete například napsat rozšíření, které může propojit libovolnou akci UML (tj. element v diagramu činnosti) do jiného diagramu činnosti. Když uživatel dvakrát klikne na akci, otevře se druhý diagram. To umožní uživateli podrobnější zobrazení akce.

 Existují dva způsoby, jak můžete ukládat řetězce a další data v jakémkoli elementu:

- **Vlastnosti stereotypu** Můžete definovat profil UML, ve kterém definujete stereotyp, který přidá vlastnosti ke specifikovaným typům prvku UML. Můžete například definovat profil, který do akce UML přidá vlastnost s názvem **MoreDetail** . Můžete napsat kód rozšíření, který ukládá odkazovaná data v akci, a to použitím stereotypu pro akci a následným uložením dat do vlastnosti.

   Stereotyp a jeho vlastnosti jsou viditelné uživateli v okno Vlastnosti.

   Pro nasazení tohoto rozšíření byste měli zabalit definici profilu a kód rozšíření v jednom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření.

   Další informace najdete v tématu [Definování profilu pro rozšiřování UML](../modeling/define-a-profile-to-extend-uml.md).

- **Odkazy.** K jakémukoli prvku UML lze připojit sadu řetězců. Můžete napsat kód, který ukládá informace, jako je název souboru nebo identifikátor GUID jiného elementu. To se dá udělat bez zadání dalších definic. Odkazy nejsou přímo viditelné pro uživatele.

Existují dva způsoby, jak zakódovat odkazy na prvky modelu:

- **Identifikátor GUID a název** cílového prvku modelu a modelu, který ho obsahuje, nebo konkrétní diagram, který ho zobrazuje

- **Odkazy na ModelBus** ModelBus je architektura pro vytváření a rozpoznávání odkazů mezi modely. Zahrnuje výběr ModelBus, který umožňuje uživateli vybrat prvek v modelu. Také pomáhá uživateli přeložit odkazy, které jsou ztraceny z důvodu změn v cílovém modelu.

   Další informace naleznete v tématu [integrování modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Rozšiřte změny z jednoho modelu do jiného.
  Můžete například synchronizovat název prvku s názvem propojeného diagramu, aby uživatel, který si ho změnil, změnil. Existují dva mechanismy:

1. **Pravidla VMSDK** se dají použít k rozšíření změn v rámci stejného modelu.

2. **Události VMSDK** lze použít k šíření změn mimo model – například pro změnu názvu souboru propojeného dokumentu nebo pro změnu elementu v jiném modelu.

   Informace o obou těchto mechanismech naleznete v tématu [How to: reagovat na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Přetažením prvků pro jejich zkopírování z jednoho modelu do jiného můžete uživateli umožnit vytvořit prvky přetažením položek do diagramu UML. Vytvořený element nemusí být kopií originálu. Můžete například nechat uživatele přetáhnout diagram aktivity z Průzkumníka řešení do jiného diagramu činnosti a vytvořit novou akci.

   Další informace najdete v tématu [Definování obslužné rutiny gesta v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) a [Postup: Přidání obslužné rutiny](../modeling/how-to-add-a-drag-and-drop-handler.md)přetažení myší.

## <a name="see-also"></a>Viz také
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definování obslužné rutiny gesta v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Postupy: Přidání obslužné rutiny přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md) [Postupy: reakce na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)
