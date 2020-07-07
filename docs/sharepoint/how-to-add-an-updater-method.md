---
title: 'Postupy: Přidání aktualizační metody | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c76373c710908a8ae7edc49c4e26ff7e94336a6d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014990"
---
# <a name="how-to-add-an-updater-method"></a>Postupy: Přidání aktualizační metody
  Můžete uživatelům umožnit aktualizovat obchodní data v externím seznamu služby SharePoint vytvořením *metody aktualizace* . Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Vytvoření aktualizační metody

1. V Návrháři BDC vyberte entitu.

2. Na panelu nabídek vyberte **Zobrazit**  >  **Další**  >  **Podrobnosti o metodě služby Windows BDC**.

    Otevře se okno Podrobnosti metody služby BDC. Další informace o tomto okně najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit metodu**aktualizace.

    Visual Studio přidá do modelu následující prvky. Tyto prvky se zobrazí v okně Podrobnosti metody služby BDC.

   - Metoda, která má název **Update**.

   - Vstupní parametr pro metodu.

   - Popisovač typu pro parametr Ve výchozím nastavení používá Visual Studio popisovač typu entity, který jste definovali pro vyhledávací metodu (například: kontakt).

   - Instance metody pro metodu.

     Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Pokud identifikátor typu entity představuje pole v databázové tabulce, které není automaticky vygenerováno, nastavte vlastnost **pole před** aktualizacemi na **hodnotu true**.

4. V **Průzkumník řešení**otevřete místní nabídku souboru kódu služby, který byl vygenerován pro danou entitu, a pak zvolte možnost **Zobrazit kód**.

    V **editoru kódu**se otevře soubor kódu entity Service. Další informace o tomto souboru najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Přidejte kód do metody Update pro aktualizaci dat. Následující příklad aktualizuje informace pro kontakt v ukázkové databázi AdventureWorks pro SQL Server.

   > [!NOTE]
   > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>Viz také:
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
