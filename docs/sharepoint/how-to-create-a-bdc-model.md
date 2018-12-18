---
title: 'Postupy: vytvoření modelu služby BDC | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a0e2bc47c902707ee896c46fa0d9988551fa6fd
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757919"
---
# <a name="how-to-create-a-bdc-model"></a>Postupy: vytvoření modelu služby BDC
  Business Data Connectivity (BDC) modelu můžete vytvořit pomocí šablony pro tento typ položky a potom přidat model do jakéhokoli projektu služby SharePoint. Další informace najdete v tématu [vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md). Další informace o tom, jak návrhu modelu najdete v tématu [návrhu modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Vytvoření projektu BDC  
  
1.  Na řádku nabídek zvolte **soubor** > **nový** > **projektu**.  
  
    > [!NOTE]  
    >  Pokud vaše IDE nastaven pro použití vývojové nastavení jazyka Visual Basic, zvolte **soubor** > **nový projekt**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
2.  V části buď **jazyka Visual Basic** nebo **Visual C#**, zvolte **Office/SharePoint**, **řešení služby SharePoint**.  
  
3.  V **šablony** podokně, vyberte **SharePoint 2013 – prázdný projekt** položku a potom vyberte **OK** tlačítko.  
  
     **Průvodce vlastním nastavením SharePoint** otevře.  
  
4.  Na **zadejte úroveň lokality a zabezpečení pro ladění** stránky, zadejte adresu URL webu služby SharePoint v místním počítači, zvolte **nasadit jako řešení farmy** možnost tlačítko a potom vyberte **Dokončit** tlačítko.  
  
     Budete testovat modelu na web služby SharePoint, který jste zadali.  
  
    > [!IMPORTANT]  
    >  Projekt musí nasadit jako řešení farmy, protože BDC modely podporují pouze řešení ve farmách.  
  
     Prázdný projekt SharePoint je vytvořen.  
  
5.  Na řádku nabídek zvolte **projektu** > **přidat novou položku**.  
  
6.  V **přidat novou položku** dialogovém okně vyberte **Office/SharePoint** uzlu.  
  
7.  V seznamu šablon služby SharePoint, zvolte **modelu připojení obchodních dat (pouze řešení farmy)**.  
  
8.  V **název** pole, zadejte název modelu služby BDC a potom zvolte **přidat** tlačítko.  
  
     A **modelu připojení obchodních dat** položka byla přidána do projektu. Ve výchozím nastavení zobrazí v Návrháři BDC se modelu. Další informace najdete v tématu [vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Viz také:
 [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Postupy: určení lokalizovaných názvů, vlastností a oprávnění pomocí zdrojového souboru](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Postupy: zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
