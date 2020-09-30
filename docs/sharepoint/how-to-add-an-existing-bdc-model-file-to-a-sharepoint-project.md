---
title: 'Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbfbd4e485a359b7e760188217326d23d3b0aa47
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584617"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint
  Pomocí sady Visual Studio můžete přizpůsobit, zabalit a znovu nasadit model připojení obchodních dat (*. bdcm*) do libovolného projektu sharepointové farmy. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Přidání souboru modelu služby BDC do projektu služby SharePoint

1. V **Průzkumník řešení**vyberte složku projektu služby SharePoint.

2. Na panelu nabídek vyberte **projekt**  >  **Přidat existující položku**.

3. V dialogovém okně **Přidat existující položku** vyhledejte umístění definičního souboru modelu, který chcete přidat do projektu, zvolte soubor a klikněte na tlačítko **Přidat** .

    Pokud model nedefinuje *obchodní systém (LOB) typu sestavení .NET*, otevře se dialogové okno **Přidat rozhraní .NET Assembly LobSystem** .

4. Pokud se zobrazí dialogové okno, proveďte jeden z následujících kroků:

   - Chcete-li napsat vlastní kód a použít návrháře k definování metadat pro importovaný model, klikněte na tlačítko **Ano** , pojmenujte systém a pak klikněte na tlačítko **OK** .

   - V opačném případě klikněte na tlačítko **ne** a pak klikněte na tlačítko **OK** .

     Položka **modelu připojení obchodních dat** se přidá do projektu.

## <a name="see-also"></a>Viz také
- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Postupy: Zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
