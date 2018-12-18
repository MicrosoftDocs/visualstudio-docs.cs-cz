---
title: 'Postupy: nastavení příkazů nasazení služby SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 060acd0164ff7819d2abfb8d92f2394b4bcc0672
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120373"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Postupy: nasazení sady SharePoint – příkazy
  Proces nasazení můžete přizpůsobit nastavení příkazy před nasazením a po nasazení. Tyto příkazy spustit před a po dalších akcí nasazení při ladění řešení služby SharePoint v sadě Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Chcete-li přidat příkaz před nasazením  
  
1.  Na řádku nabídek zvolte **projektu** > **\<*ProjectName*> vlastnosti**.  
  
2.  Vyberte **SharePoint** kartě.  
  
3.  V **před nasazením příkazového řádku** textové pole, zadejte MS-DOS nebo MSBuild příkazy k přizpůsobení tohoto kroku.  
  
     Například pro zobrazení seznamu obsah adresáře, než bude dokončeno nasazení, zadejte **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Chcete-li přidat příkaz po nasazení  
  
1.  Na řádku nabídek zvolte **projektu** > **\<*ProjectName*> vlastnosti**.  
  
2.  Vyberte **SharePoint** kartě.  
  
3.  V **po nasazení příkazového řádku** text zadejte MS-DOS nebo MSBuild příkazy k přizpůsobení tohoto kroku.  
  
     Po dokončení nasazení, zobrazit obsah adresáře, zadejte **dir**. Chcete-li proměnnou MSBuild zkopírujte sestavení z adresáře sestavení, zadejte **zkopírujte $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Viz také:
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
