---
title: 'Postupy: Přidání konkrétní vyhledávací metody | Microsoft Docs'
description: Získejte instanci entity přidáním vyhledávací metody. Služba BDC volá metodu, když uživatel vybere entitu ve webové části nebo v externím seznamu obchodních dat.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 237cd28bffece4517e80b979602ac8d2ed357aa2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882684"
---
# <a name="how-to-add-a-specific-finder-method"></a>Postupy: Přidání konkrétní vyhledávací metody
  Jednu instanci entity můžete vrátit vytvořením *konkrétní vyhledávací* metody. Služba BDC (Business Data Connectivity) spouští konkrétní vyhledávací metodu, když uživatel zvolí entitu ve webové části nebo v externím seznamu obchodních dat. Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Vytvoření konkrétní vyhledávací metody

1. V **Návrháři BDC** vyberte entitu.

    Informace o tom, jak přidat entitu do **návrháře služby BDC** v aplikaci Visual Studio, naleznete v tématu [How to: Add a entity to a model](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **ostatní okna**, **Podrobnosti metody služby BDC**.

    Otevře se okno **Podrobnosti metody služby BDC** . Další informace o tomto okně najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit konkrétní vyhledávací metodu**.

    Visual Studio přidá do modelu následující prvky. Tyto prvky se zobrazí v okně **Podrobnosti metody služby BDC** .

   - Metoda.

   - Vstupní parametr pro metodu.

   - Návratový parametr pro metodu.

   - Popisovač typu pro každý parametr.

   - Instance metody pro metodu.

     Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Otevřete okno **vlastnosti** sady Visual Studio.

5. Nakonfigurujte popisovač typu návratového parametru jako popisovač typu entity. Informace o tom, jak vytvořit popisovač typu entity, naleznete v tématu [How to: define a Type deskriptor parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Pokud jste k entitě přidali vyhledávací metodu, nemusíte tento krok provádět. Visual Studio používá popisovač typu, který jste definovali v metodě Finder.

   > [!NOTE]
   > Pokud pole identifikátor typu entity představuje pole v databázové tabulce, které je automaticky vygenerováno, nastavte vlastnost **atributu jen pro čtení** pole identifikátor na **hodnotu true**.

6. V okně **Podrobnosti metody** vyberte instanci metody metody.

7. V **okně Vlastnosti** nastavte vlastnost **název návratového parametru** na název návratového parametru metody. Další informace o vlastnostech instance metody naleznete v tématu [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. V **Průzkumník řešení** otevřete místní nabídku souboru kódu služby, který byl vygenerován pro danou entitu, a pak zvolte možnost **Zobrazit kód**.

    V editoru kódu se otevře soubor kódu entity Service. Další informace o souboru kódu entity Service najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Přidejte kód do konkrétní vyhledávací metody. Tento kód provádí následující úlohy:

   - Načte záznam ze zdroje dat.

   - Vrátí entitu ke službě BDC.

     Následující příklad vrátí kontakt z ukázkové databáze AdventureWorks pro SQL Server.

     > [!NOTE]
     > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>Viz také
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
