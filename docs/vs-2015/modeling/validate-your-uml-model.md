---
title: Ověření modelu UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fea958a20e5eee78f79f324ad19ef646f7920951
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739973"
---
# <a name="validate-your-uml-model"></a>Ověření modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Některé z modelů UML, které nakreslíte v sadě Visual Studio může být považovány za neplatné ve vašem projektu. Například může vyžadovat, že případ použití musí být vždy spojeny do sekvenčního diagramu, který má životnosti představující actors případu použití. Můžete nainstalovat nebo můžete definovat *omezení* , které pomohou vašemu týmu v souladu s požadavky na takovou situaci. Omezení můžete použít, když uživatel uloží nebo otevře model a můžete vyvolat příkaz nabídky.  
  
 Bez omezení jsou součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], protože závisejí na tom, jak váš tým interpretuje a používá modelů UML. Ale můžete definovat vlastní omezení a nainstalovat omezení, které jsou definovány jinými uživateli. Zjistěte, jak definovat omezení a balíček pro distribuci, naleznete v tématu [definovat omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="invoking-validation"></a>Vyvolání ověřování  
 Pokud jste nainstalovali rozšíření ověřování, omezení, které poskytuje může použít v následujících případech. Některá omezení jsou nastavené na použití pouze některé z těchto případů.  
  
- **Příkaz ověření.** Volání ověřovací kdykoli, klikněte na tlačítko **ověřit Model UML** na **architektura** nabídky.  
  
  > [!NOTE]
  >  Příkaz se zobrazí jenom v případě, že omezení ověření jsou nainstalovány.  
  
- **Při uložení modelu.** Omezení ověřování lze použít při uložení modelu. Účelem těchto omezení je pomohou Ujistěte se, že neukládejte modelu, který je neplatný podle interpretace váš projekt.  
  
   Jestliže nejsou chyby, můžete být vyzváni, zda chcete uložit model. Můžete opravit chyby, a přesto uložit model.  
  
- **Při otevření modelu.** Při otevření modelu metody ověřování lze použít k obnovení chybové zprávy, které existovaly při uložení modelu. Chyby mohou být způsobeny také nekonzistence mezi změny, které jsou provedeny podle uživatelů, kteří pracují na různých součástí modelu. Další informace najdete v tématu [sdílení modelů a export diagramů](../modeling/share-models-and-exporting-diagrams.md).  
  
  Chyby ověření jsou hlášeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna chyby.  
  
  V diagramu vyberte prvky, které nejsou správné, klikněte dvakrát na chybu. Tento postup funguje pouze v případě nesprávné elementy jsou viditelné v diagramu otevřete.  
  
## <a name="installing-validation-constraints"></a>Instalace omezení ověřování  
 Omezení jsou zabaleny v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soubory Extension (VSIX). Sadou omezujících podmínek, bude obvykle součástí rozšíření, která také obsahuje další definice, jako je například příkazy nabídek, profily a položky panelu nástrojů.  
  
#### <a name="to-install-a-visual-studio-extension"></a>Chcete-li nainstalovat rozšíření sady Visual Studio  
  
1.  Dvakrát klikněte **VSIX** souboru v Průzkumníku Windows (nebo Průzkumníka souborů).  
  
2.  Restartujte všechny instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , který je již spuštěna.  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>Zakázání a odinstalaci omezení ověření  
 Pokud chcete, aby fungoval s modelem, ke kterému se nedá použít omezení, můžete dočasně zakázat rozšíření, který je obsahuje. Tímto způsobem můžete pracovat s různými druhy modelu v různou dobu, povolování a zakazování různých rozšíření.  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Pro zakázání nebo odinstalaci rozšíření sady Visual Studio  
  
1.  Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.  
  
2.  Společně s rozšířením, klikněte na tlačítko **zakázat** dočasně zakázat rozšíření. Můžete znovu povolit ho později tak, že vrací **rozšíření a aktualizace** okna.  
  
     \- nebo –  
  
     Klikněte na tlačítko **odinstalovat** se odebrat rozšíření.  
  
3.  Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)   
 [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)



