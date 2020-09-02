---
title: 'Postupy: Přidání vyhledávací metody | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fa8f8eb34943cc17bc6cabca8e93ea7569a7ba6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016726"
---
# <a name="how-to-add-a-finder-method"></a>Postupy: Přidání vyhledávací metody
  Chcete-li povolit službě BDC (Business Data Connectivity) zobrazit seznam entit ve webové části nebo seznamu, je nutné vytvořit *vyhledávací* metodu. Vyhledávací metoda je speciální metoda, která vrací kolekci instancí entit. Další informace najdete v tématu [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Vytvoření vyhledávací metody

1. V **Návrháři BDC**vyberte entitu.

    Další informace naleznete v tématu [How to: Add a entity to a model](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na panelu nabídek vyberte **Zobrazit**  >  **Další**  >  **Podrobnosti o metodě služby Windows BDC**.

    Otevře se okno **Podrobnosti metody služby BDC** . Další informace o okně **Podrobnosti metody služby BDC** najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit vyhledávací metodu**.

    Visual Studio přidá metodu, návratový parametr a popisovač typu.

4. Nakonfigurujte popisovač typu jako popisovač typu kolekce entit. Další informace o tom, jak vytvořit popisovač typu kolekce entit, naleznete v tématu [How to: define Type Descriptor parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Pokud jste přidali konkrétní vyhledávací metodu k entitě, nemusíte tento krok provádět. Visual Studio používá popisovač typu, který jste definovali v konkrétní vyhledávací metodě.

5. V **Průzkumník řešení**otevřete místní nabídku souboru kódu služby, který byl vygenerován pro danou entitu, a pak zvolte možnost **Zobrazit kód**. Další informace o souboru kódu služby najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Přidejte kód do metody Finder. Tento kód provádí následující úlohy:

   - Načte data ze zdroje dat.

   - Vrátí seznam entit služby BDC.

     Následující příklad vrátí kolekci `Contact` entit pomocí dat z ukázkové databáze AdventureWorks pro SQL Server.

   > [!NOTE]
   > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Viz také
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
