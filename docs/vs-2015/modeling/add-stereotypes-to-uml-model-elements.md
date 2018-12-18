---
title: Přidávání stereotypů k elementům modelu UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dbd5f4288833a29bdfef2df97ee71ac765ae168f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725376"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Přidávání stereotypů k elementům modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stereotyp můžete přidat na prvek modelu UML poznámku a zadat speciální vlastnostmi. Přidání stereotyp na prvek modelu, stereotyp musí být definován v profilu a profilu je třeba propojit na balíček nebo model, který obsahuje prvek modelu. Každý stereotyp lze přidat pouze pro některé typy prvku modelu, jako je například třídy UML, případy použití nebo komponenty.  
  
 Například pokud chcete definovat pomocí stereotyp «specifikace» třída UML, je musíte jej vytvořit v rámci balíčku nebo modelu, který je propojený s standardní L2 profilu.  
  
 Ve výchozím nastavení je každý model podle propojen s standardní L2 profilů UML a L3.  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Odkaz na model nebo balíček profilu  
  
1.  Otevřít **Průzkumníku modelů UML**. Na **architektura** nabídky, přejděte k **Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
2.  Vyhledejte balíček nebo model, který obsahuje všechny prvky, které chcete použít stereotypy v profilu.  
  
3.  Klikněte pravým tlačítkem na balíček nebo model a pak klikněte na tlačítko **vlastnosti**.  
  
4.  V **vlastnosti** okno, nastaveno **profily** vlastnost profily, které obsahují Stereotypy, které chcete použít.  
  
     Stereotypy profilu bude nyní k dispozici na všechny prvky uvnitř modelu nebo balíčku. Pokud balíček obsahuje další balíčky, Stereotypy bude také k dispozici na prvky v nich obsažené.  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>K přidávání stereotypů k prvkům modelu nebo vztahy  
  
1.  Klikněte pravým tlačítkem na model prvku nebo vztahu, v diagramu nebo v **Průzkumníku modelů UML**a potom klikněte na tlačítko **vlastnosti**.  
  
    > [!NOTE]
    >  Pokud chcete přidat do několika prvků stejného Stereotypy, můžete vybrat několik prvků a klikněte pravým tlačítkem na jeden z nich.  
  
2.  Klikněte na tlačítko **Stereotypy** vlastnosti a vyberte Stereotypy, které chcete použít.  
  
     Vybrané Stereotypy se zobrazí v rámci "odlišené dvojitou» v prvku modelu pro většinu typů prvků a vztahů.  
  
    > [!NOTE]
    >  Pokud nevidíte **Stereotypy** vlastnost, nebo pokud chcete stereotyp nezobrazí, ověřte, zda prvek modelu je uvnitř balíčku nebo modelu, ke kterému je propojená příslušný profil.  
  
3.  Některé Stereotypy umožní nastavit hodnoty dalších vlastností pro ovládací prvek modelu. Chcete-li zobrazit tyto vlastnosti, rozbalte **Stereotypy** vlastnost.  
  
### <a name="to-create-model-elements-within-a-package"></a>Chcete-li vytvořit prvky modelu v rámci balíčku  
  
1.  Vytvoření balíčku v diagramu tříd UML, nebo v **Průzkumníku modelů UML**.  
  
2.  Do balíčku přidáte prvky modelu, v jednom z následujících způsobů:  
  
    -   V diagramu tříd UML klikněte na nástroj pro daný element a klikněte do balíčku v diagramu.  
  
         \- nebo –  
  
    -   V Průzkumníku modelů UML, klikněte pravým tlačítkem na balíček, přejděte na **přidat**a potom klikněte na typ elementu.  
  
         \- nebo –  
  
    -   V Průzkumníku modelů UML přetáhněte existující prvek do balíčku.  
  
         \- nebo –  
  
    -   Odkaz na balíček diagramu a pak vytvořte prvků v diagramu.  
  
         Chcete-li to provést, klikněte pravým tlačítkem na prázdnou část diagramu a potom klikněte na **vlastnosti**. V **vlastnosti** okno, nastavte **odkazovaný balíček** pro vámi požadovaný balíček.  
  
         Nové prvky, které vytvoříte v diagramu budou definované v rámci daného balíčku.  
  
         Provést pouze u některých typů diagramu.  
  
## <a name="see-also"></a>Viz také  
 [Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md)   
 [Barva tříd UML podle stereotypu](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)



