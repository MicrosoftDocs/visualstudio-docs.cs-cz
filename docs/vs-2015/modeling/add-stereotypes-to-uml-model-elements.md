---
title: Přidání stereotypů k prvkům modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292332"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Přidávání stereotypů k elementům modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stereotyp můžete přidat do prvku modelu UML a opatřit ho pomocí specializovaných vlastností. Chcete-li přidat stereotyp do prvku modelu, musí být stereotyp definován v profilu a musíte propojit profil s balíčkem nebo modelem, který obsahuje prvek modelu. Každý stereotyp lze přidat pouze do určitých druhů prvků modelu, jako jsou například třídy UML, případy použití nebo komponenty.

 Například pokud chcete definovat třídu UML se stereotypem «Specification "Specification", je nutné ji vytvořit v rámci balíčku nebo modelu, který je propojen se standardním profilem L2.

 Ve výchozím nastavení je každý model propojen s profily Standard UML L2 a L3.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Připojení profilu k modelu nebo balíčku

1. Otevřete **Průzkumníka modelů UML**. V nabídce **Architektura** přejděte na **okna**a potom klikněte na **Průzkumník modelů UML**.

2. Vyhledejte balíček nebo model, který obsahuje všechny prvky, pro které chcete použít stereotypy v profilu.

3. Klikněte pravým tlačítkem na balíček nebo model a pak klikněte na **vlastnosti**.

4. V okně **vlastnosti** nastavte vlastnost **Profiles** na profily obsahující stereotypy, které chcete použít.

     Stereotypy profilu budou nyní k dispozici pro všechny prvky uvnitř modelu nebo balíčku. Pokud balíček obsahuje další balíčky, stereotypy budou také k dispozici pro prvky uvnitř těchto.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Přidání stereotypů k prvkům modelu nebo vztahům

1. Klikněte pravým tlačítkem myši na prvek modelu nebo na vztah, a to buď v diagramu, nebo v **Průzkumníku modelů UML**, a pak klikněte na **vlastnosti**.

    > [!NOTE]
    > Chcete-li přidat stejné stereotypy k několika prvkům, můžete vybrat několik prvků a pak na jednu z nich kliknout pravým tlačítkem.

2. Klikněte na vlastnost **Stereotypy** a vyberte stereotypy, které chcete použít.

     Vybrané stereotypy se zobrazují v rámci «dvojité šipky» v elementu modelu pro většinu druhů elementu a vztahu.

    > [!NOTE]
    > Pokud nemůžete zobrazit vlastnost **Stereotypy** , nebo pokud se stereotyp, který chcete, nezobrazuje, ověřte, zda je prvek modelu uvnitř balíčku nebo modelu, ke kterému byl příslušný profil propojen.

3. Některé Stereotypy umožňují nastavit hodnoty dalších vlastností prvku modelu. Chcete-li zobrazit tyto vlastnosti, rozbalte vlastnost **Stereotypy** .

### <a name="to-create-model-elements-within-a-package"></a>Vytvoření prvků modelu v rámci balíčku

1. Vytvořte balíček buď v diagramu tříd UML, nebo v **Průzkumníku modelů UML**.

2. Prvky modelu přidejte do balíčku jedním z následujících způsobů:

    - V diagramu tříd UML klikněte na nástroj pro prvek a potom klikněte dovnitř balíčku v diagramu.

         \- nebo –

    - V Průzkumníku modelů UML klikněte pravým tlačítkem na balíček, přejděte na **Přidat**a potom klikněte na typ prvku.

         \- nebo –

    - V Průzkumníku modelů UML přetáhněte existující prvek do balíčku.

         \- nebo –

    - Propojte diagram s balíčkem a potom v diagramu vytvořte prvky.

         Provedete to tak, že kliknete pravým tlačítkem myši na prázdnou část diagramu a pak kliknete na **vlastnosti**. V okně **vlastnosti** nastavte **propojený balíček** na požadovaný balíček.

         V rámci tohoto balíčku budou definovány všechny nové prvky, které vytvoříte v diagramu.

         To lze provést pouze s některými typy diagramu.

## <a name="see-also"></a>Viz také
 [Definování profilu pro rozšiřování modelu UML](../modeling/define-a-profile-to-extend-uml.md) [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md)

