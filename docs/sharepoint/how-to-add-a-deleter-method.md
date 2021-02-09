---
title: 'Postupy: Přidání metody odstranění | Microsoft Docs'
description: Naučte se, jak přidat metodu odstranění do návrháře služby BDC v aplikaci Visual Studio, takže koncový uživatel může odstranit záznam dat z externího seznamu na webu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 33ca8abf7a35bafd04c38fbb4a681245f2701f8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879719"
---
# <a name="how-to-add-a-deleter-method"></a>Postupy: Přidání metody odstranění
  Můžete povolit koncovému uživateli odstranit datový záznam z externího seznamu na webu služby SharePoint přidáním metody odstranění do modelu. Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Vytvoření metody odstranění

1. V **Návrháři BDC** vyberte entitu.

2. Na panelu nabídek vyberte **Zobrazit**  >  **Další**  >  **Podrobnosti o metodě služby Windows BDC**.

    Otevře se okno **Podrobnosti metody služby BDC** . Další informace o tomto okně najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit metodu odstranění**.

    Visual Studio přidá do modelu následující prvky. Tyto prvky se zobrazí v okně **Podrobnosti metody služby BDC** .

   - Metoda s názvem **Delete**

   - Vstupní parametr pro metodu.

   - Popisovač typu pro parametr

   - Instance metody pro metodu.

     Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

4. V **Průzkumník řešení** otevřete místní nabídku souboru kódu služby, který byl vygenerován pro danou entitu, a pak zvolte možnost **Zobrazit kód**.

    V editoru kódu se otevře soubor kódu entity Service. Další informace o souboru kódu entity Service najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

5. K odstranění záznamu přidejte do metody Delete kód. Následující příklad odstraní položku řádku z prodejní objednávky pomocí ukázkové databáze AdventureWorks pro SQL Server.

   > [!NOTE]
   > Metoda v tomto příkladu používá dva vstupní parametry.

   > [!NOTE]
   > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>Viz také
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
