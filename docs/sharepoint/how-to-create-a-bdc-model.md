---
title: 'Postupy: vytvoření modelu služby BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 139da31ced1d32def450a1dc176ca241b0c4677f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014537"
---
# <a name="how-to-create-a-bdc-model"></a>Postupy: vytvoření modelu služby BDC
  Můžete vytvořit model služby připojení obchodních dat (BDC) pomocí šablony pro daný druh položky a potom přidat model do libovolného projektu služby SharePoint. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md). Další informace o návrhu modelu naleznete v tématu [design a model připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Vytvoření projektu služby BDC

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

    > [!NOTE]
    > Pokud je vaše rozhraní IDE nastaveno na použití Visual Basic vývojové nastavení, vyberte **soubor**  >  **Nový projekt**.

     Otevře se dialogové okno **Nový projekt** .

2. V buď **Visual Basic** nebo **Visual C#**, vyberte možnost **Office/SharePoint**, **řešení služby SharePoint**.

3. V podokně **šablony** zvolte položku **SharePoint 2013 – prázdná položka projektu** a pak klikněte na tlačítko **OK** .

     Otevře se **Průvodce přizpůsobením SharePointu** .

4. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL webu služby SharePoint v místním počítači, zvolte přepínač **nasadit jako řešení farmy** a pak klikněte na tlačítko **Dokončit** .

     Model budete testovat na SharePointovém webu, který jste zadali.

    > [!IMPORTANT]
    > Projekt je nutné nasadit jako řešení farmy, protože modely služby BDC podporují pouze řešení farmy.

     Vytvoří se prázdný projekt služby SharePoint.

5. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

6. V dialogovém okně **Přidat novou položku** vyberte uzel **Office/SharePoint** .

7. V seznamu šablon služby SharePoint vyberte možnost **Model připojení obchodních dat (pouze řešení farmy)**.

8. Do pole **název** zadejte název modelu služby BDC a pak klikněte na tlačítko **Přidat** .

     Položka **modelu připojení obchodních dat** se přidá do projektu. Ve výchozím nastavení se model zobrazuje v Návrháři služby BDC. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Viz také
- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Postupy: Zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
