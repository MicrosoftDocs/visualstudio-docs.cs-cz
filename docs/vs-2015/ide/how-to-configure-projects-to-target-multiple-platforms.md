---
title: 'Postupy: Konfigurace projektů pro více cílových platforem | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a3010e6304124ee306c5ecad3593df98d555523
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921831"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Postupy: Konfigurace projektů pro více cílových platforem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje způsob, jak řešení, které cílí několika různými architekturami procesoru nebo platformy, najednou. Vlastnosti, které chcete nastavit tyto jsou přístupné prostřednictvím **nástroje Configuration Manager** dialogové okno.  
  
## <a name="targeting-a-platform"></a>Cílení na platformy  
 **Nástroje Configuration Manager** dialogové okno umožňuje vytvořit a nastavit na úrovni řešení a projektu konfigurace a platformy. Každou kombinaci konfigurace na úrovni řešení a cíle může mít jedinečnou sadu vlastností, které jsou spojené s, což umožňuje snadno přepínat mezi, například konfiguraci vydané verze, který cílí [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] platformy, konfiguraci vydané verze který cílí na x x86 platformu a konfiguraci ladění, který se zaměřuje x86 platformy.  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Chcete-li nastavit konfiguraci tak, aby cílit na různé platformy  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **nástroje Configuration Manager**.  
  
2.  V **pole platforma aktivního řešení**, vyberte platformu vašeho řešení do cíle, nebo vyberte  **\<nový >** vytvořit nové platformy. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zkompiluje pro zaměření na platformu, která je nastavena jako aktivní platformu v aplikaci **nástroje Configuration Manager** dialogové okno.  
  
## <a name="removing-a-platform"></a>Odebrání platformu  
 Pokud je dobré si uvědomit, že nemáte žádné požadavky platformu, můžete ho pomocí dialogového okna nástroje Configuration Manager odebrat. Tato akce odebere všechna nastavení řešení a projektů, které jste nakonfigurovali pro kombinaci konfigurace a cíl.  
  
#### <a name="to-remove-a-platform"></a>Chcete-li odebrat platformu  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **nástroje Configuration Manager**.  
  
2.  V **pole platforma aktivního řešení**vyberte  **\<Upravit >**. **Upravit platformy řešení** zobrazí se dialogové okno.  
  
3.  Klikněte na platformu, kterou chcete odebrat a klikněte na tlačítko **odebrat**.  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>Cílení na více platforem s jedním z řešení  
 Vzhledem k tomu, že můžete změnit nastavení založené na kombinaci konfigurace a nastavení platformy, můžete nastavit řešení, které můžete cílit na více než jednu platformu.  
  
#### <a name="to-target-multiple-platforms"></a>Pro více cílových platforem  
  
1.  Použití **nástroje Configuration Manager** přidat alespoň dvě cílové platformy pro řešení.  
  
2.  Vyberte platformu, kterou chcete cílit na z **platformou aktivního řešení** seznamu.  
  
3.  Sestavte řešení.  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>Chcete-li sestavení více konfigurací řešení najednou  
  
1. Použití **nástroje Configuration Manager** přidat alespoň dvě cílové platformy pro řešení.  
  
2. Použití **dávkové sestavení** okna k sestavení několika konfigurací řešení najednou.  
  
   Je možné mít nastaveno na hodnotu, například platformu úrovni řešení [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], a mít žádné projekty v rámci tohoto řešení, které cílí na stejnou platformu. Také je možné mít více projektů v řešení, každý cílí na různé platformy. Doporučuje se, že pokud některou z těchto situací, můžete vytvořit novou konfiguraci pomocí popisný název, aby nedocházelo k záměně.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md)   
 [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)   
 [Sestavování a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)



