---
title: Jak použít soubor prostředků v projektu služby SharePoint | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1693308c591e60a2df0e4d8e18ece8cc9b598fd2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585742"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Použití souboru prostředků v projektu služby SharePoint

  Pomocí souboru prostředků můžete poskytnout lokalizované názvy, definovat vlastnosti a použít oprávnění pro objekty, které jsou definovány v modelu služby připojení obchodních dat. Chcete-li zadat tyto informace, přidejte položku **prostředku připojení obchodních dat** k projektu, který obsahuje položku **modelu připojení obchodních dat** . Pak můžete zadat názvy, vlastnosti a oprávnění úpravou XML pro soubor prostředků.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Přidání souboru prostředků služby BDC do projektu služby SharePoint

1. V **Průzkumník řešení**rozbalte složku pro projekt služby SharePoint a pak zvolte složku, která obsahuje model služby BDC.

2. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

3. Rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V dialogovém okně **Přidat novou položku** vyberte **položku prostředek připojení obchodních dat**.

5. Do pole **název** zadejte název souboru prostředků a pak klikněte na tlačítko **Přidat** .

     Soubor prostředků s příponou. BCDR se přidá do projektu a otevře se pro úpravy.

6. Přidejte XML pro definování lokalizovaných názvů, vlastností a oprávnění, která chcete použít pro model služby BDC.

     Informace o tom, jak definovat tyto prvky, naleznete v tématu [model a soubory prostředků](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>Viz také
- [Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Postupy: Zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
