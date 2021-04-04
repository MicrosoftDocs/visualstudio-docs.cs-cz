---
title: 'Postupy: Přidání metody autora | Microsoft Docs'
description: Zjistěte, jak přidat metodu autora, která přidá nová data do zdroje dat entity ve službě BDC (Business Data Connectivity) na SharePointu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 950745a533fbea8d360c8bea6d839a304dd6e0d7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216407"
---
# <a name="how-to-add-a-creator-method"></a>Postupy: Přidání metody autora
  Metoda Creator přidá nová data do zdroje dat entity. Služba BDC (Business Data Connectivity) volá tuto metodu, když uživatel vybere tlačítko **Nová položka** na **pásu karet** seznamu, který je založený na modelu. Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Přidání metody autora

1. V **Návrháři BDC** vyberte entitu.

2. Na panelu nabídek vyberte **Zobrazit**  >  **Další**  > **Podrobnosti o metodě služby Windows BDC**.

    Otevře se okno **Podrobnosti metody služby BDC** . Další informace o tomto okně najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit metodu autora**.

    Visual Studio přidá do modelu následující elementy a tyto prvky se zobrazí v okně **Podrobnosti metody služby BDC** .

   - Metoda s názvem **Create**.

   - Vstupní parametr pro metodu.

   - Návratový parametr pro metodu.

   - Deskriptory typů pro parametry.

   - Instance metody pro metodu.

     Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

4. V **Průzkumník řešení** otevřete místní nabídku souboru kódu služby, který byl vygenerován pro danou entitu, a pak zvolte možnost **Zobrazit kód**.

    V editoru kódu se otevře soubor kódu entity Service. Další informace o souboru kódu entity Service najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Přidejte kód do metody Creator, která přidá data do zdroje dat. Následující příklad přidá kontakt na ukázkovou databázi AdventureWorks pro SQL Server.

   > [!NOTE]
   > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet4":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet4":::

## <a name="see-also"></a>Viz také
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
