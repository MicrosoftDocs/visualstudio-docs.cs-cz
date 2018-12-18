---
title: 'Postupy: Přidání aktualizační metody | Dokumentace Microsoftu'
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4d50180173673b4999c18b8980c682d79637bd3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951415"
---
# <a name="how-to-add-an-updater-method"></a>Postupy: Přidání aktualizační metody
  Můžete povolit uživatelům aktualizovat tak, že vytvoříte obchodních dat v Sharepointovém seznamu externích *Updater* metody. Další informace najdete v tématu [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Chcete-li vytvořit metodu Updater  
  
1. V Návrháři služby BDC Zvolte entitu.  
  
2. V panelu nabídky zvolte **zobrazení** > **ostatní Windows** > **podrobnosti metody služby BDC**.  
  
    Otevře se okno Podrobnosti metody služby BDC. Další informace o tomto okně najdete v tématu [přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. V **přidejte metodu** klikněte na položku **vytvořit metodu Updater**.  
  
    Visual Studio přidá následující prvky modelu. Tyto prvky se zobrazí v okně Podrobnosti metody služby BDC.  
  
   - Metoda s názvem **aktualizace**.  
  
   - Vstupní parametr metody.  
  
   - Popisovač typu pro parametr. Ve výchozím nastavení, Visual Studio používá popisovače typu entity, který jste definovali pro metody Finder (například: kontakt).  
  
   - Instance metody k metodě.  
  
     Další informace najdete v tématu [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
   > [!NOTE]  
   >  Pokud identifikátor entity typu představuje pole v databázové tabulce, který je generován automaticky, nastavte **pole předběžný Aktualizátor** vlastnost **True**.  
  
4. V **Průzkumníka řešení**, otevřete místní nabídku souboru služby kód, který byl vygenerován pro entitu a pak zvolte **zobrazit kód**.  
  
    Soubor kódu služby entity se otevře v **Editor kódu**. Další informace týkající se tohoto souboru najdete v tématu [vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Přidejte kód do metody Update k aktualizaci dat. Následující příklad aktualizuje informace o kontaktu v ukázkové databázi AdventureWorks pro SQL Server.  
  
   > [!NOTE]  
   >  Nahraďte hodnotu `ServerName` pole s názvem vašeho serveru.  
  
    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Viz také:
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Postupy: přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)   
 [Postupy: Přidání specifické vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Postupy: přidání metody vytvoření](../sharepoint/how-to-add-a-creator-method.md)   
 [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)   
 [Postupy: přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)   
 [Přehled nástroje pro navrhování modelů služby BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Postupy: Přidání parametru k metodě](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)  
  
 
