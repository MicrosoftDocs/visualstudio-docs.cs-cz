---
title: Jak použít soubor prostředků v projektu služby SharePoint | Microsoft Docs
titleSuffix: ''
description: Použijte soubor prostředků v projektu služby SharePoint, abyste mohli poskytnout lokalizované názvy, definovat vlastnosti a aplikovat oprávnění pro objekty definované v modelu služby BDC.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ecc2bfab37e534e4edc005273ab5fc826b771228
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304368"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Použití souboru prostředků v projektu služby SharePoint

  Pomocí souboru prostředků můžete poskytnout lokalizované názvy, definovat vlastnosti a použít oprávnění pro objekty, které jsou definovány v modelu služby připojení obchodních dat. Chcete-li zadat tyto informace, přidejte položku **prostředku připojení obchodních dat** k projektu, který obsahuje položku **modelu připojení obchodních dat** . Pak můžete zadat názvy, vlastnosti a oprávnění úpravou XML pro soubor prostředků.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Přidání souboru prostředků služby BDC do projektu služby SharePoint

1. V **Průzkumník řešení** rozbalte složku pro projekt služby SharePoint a pak zvolte složku, která obsahuje model služby BDC.

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
