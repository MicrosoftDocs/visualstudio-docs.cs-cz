---
title: 'Postupy: Přidání aktualizační metody | Microsoft Docs'
description: Naučte se, jak uživatelům umožnit aktualizovat obchodní data v externím seznamu SharePointu přidáním metody aktualizace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d6337ac237c2a030593b90b29af5e8474052de99
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216732"
---
# <a name="how-to-add-an-updater-method"></a>Postupy: Přidání aktualizační metody
  Můžete uživatelům umožnit aktualizovat obchodní data v externím seznamu služby SharePoint vytvořením *metody aktualizace* . Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Vytvoření aktualizační metody

1. V Návrháři BDC vyberte entitu.

2. Na panelu nabídek vyberte **Zobrazit**  >  **Další**  >  **Podrobnosti o metodě služby Windows BDC**.

    Otevře se okno Podrobnosti metody služby BDC. Další informace o tomto okně najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit metodu** aktualizace.

    Visual Studio přidá do modelu následující prvky. Tyto prvky se zobrazí v okně Podrobnosti metody služby BDC.

   - Metoda, která má název **Update**.

   - Vstupní parametr pro metodu.

   - Popisovač typu pro parametr Ve výchozím nastavení používá Visual Studio popisovač typu entity, který jste definovali pro vyhledávací metodu (například: kontakt).

   - Instance metody pro metodu.

     Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Pokud identifikátor typu entity představuje pole v databázové tabulce, které není automaticky vygenerováno, nastavte vlastnost **pole před** aktualizacemi na **hodnotu true**.

4. V **Průzkumník řešení** otevřete místní nabídku souboru kódu služby, který byl vygenerován pro danou entitu, a pak zvolte možnost **Zobrazit kód**.

    V **editoru kódu** se otevře soubor kódu entity Service. Další informace o tomto souboru najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Přidejte kód do metody Update pro aktualizaci dat. Následující příklad aktualizuje informace pro kontakt v ukázkové databázi AdventureWorks pro SQL Server.

   > [!NOTE]
   > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet5":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet5":::

## <a name="see-also"></a>Viz také
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
