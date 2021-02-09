---
title: 'Postupy: vytvoření přijímače událostí pro konkrétní instanci seznamu | Microsoft Docs'
titleSuffix: ''
description: Vytvoření přijímače událostí pro konkrétní instanci seznamu. Přijímač událostí instance seznamu reaguje na události, ke kterým dochází v jakékoli instanci definice seznamu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 664a7ac4e763b2378cf30603c417aacde27c2e47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925498"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Postupy: vytvoření přijímače událostí pro specifickou instanci seznamu
  Přijímač událostí instance seznamu reaguje na události, ke kterým dochází v jakékoli instanci definice seznamu. I když šablona příjemce událostí nepovoluje cílení na konkrétní instanci seznamu, můžete změnit přijímač událostí, který je vymezen na definici seznamu, aby odpovídal na události v konkrétní instanci seznamu.

 Chcete-li cílit na konkrétní instanci seznamu, v *Elements.xml* pro přijímače událostí nahraďte `ListTemplateId` `ListUrl` a přidejte adresu URL instance seznamu.

## <a name="create-a-list-instance-event-receiver"></a>Vytvoření přijímače událostí instance seznamu
 Následující kroky ukazují, jak upravit přijímač událostí položky seznamu tak, aby odpovídal jenom událostem, ke kterým dochází v instanci Custom oznámení – seznam.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Úprava přijímače událostí tak, aby reagoval na konkrétní instanci seznamu

1. V prohlížeči otevřete web služby SharePoint.

2. V navigačním podokně **jsou uvedeny** odkazy.

3. Na stránce **veškerý obsah webu** klikněte na odkaz **vytvořit** .

4. V dialogovém okně **vytvořit** vyberte typ **oznámení** , pojmenujte oznámení **TestAnnouncements** a pak klikněte na tlačítko **vytvořit** .

5. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvořte projekt přijímače událostí.

6. V seznamu **jaký typ přijímače událostí chcete?** vyberte možnost **události položky seznamu**.

    > [!NOTE]
    > Můžete také vybrat jakýkoli jiný typ přijímače událostí, který má obor na definici seznamu, například **vypsat události e-mailu** nebo **Zobrazit události pracovního postupu**.

7. V seznamu **jaká položka by měla být zdroj události?** vyberte možnost **oznámení**.

8. V seznamu **zpracovat následující události** vyberte zaškrtávací políčko a **přidejte položku** a pak klikněte na tlačítko **Dokončit** .

9. V **Průzkumník řešení** v části EventReceiver1 otevřete *Elements.xml*.

     Přijímač událostí aktuálně odkazuje na definici seznamu oznámení pomocí následujícího řádku:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Změňte tento řádek na následující text:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Tím příjemce událostí přesměruje jenom na události, ke kterým dojde v novém seznamu oznámení **TestAnnouncements** , který jste právě vytvořili. Můžete změnit `ListURL` atribut tak, aby odkazoval na libovolnou instanci seznamu na sharepointovém serveru.

10. Otevřete soubor kódu pro přijímač událostí a vložte zarážku do metody ItemAdding.

11. Klikněte na klávesu **F5** a sestavte a spusťte řešení.

12. V SharePointu klikněte v navigačním podokně na odkaz **TestAnnouncements** .

13. Klikněte na odkaz **Přidat nové oznámení** .

14. Zadejte název oznámení a pak klikněte na tlačítko **Uložit** .

     Všimněte si, že při přidání nové položky do seznamu vlastních oznámení je dosaženo zarážky.

15. Pokračujte kliknutím na klávesu **F5** .

16. V navigačním podokně klikněte na odkaz **seznamy** a pak zvolte odkaz **oznámení** .

17. Přidejte nové oznámení.

     Všimněte si, že příjemce událostí se na novém oznámení neaktivuje, protože příjemce je nakonfigurovaný tak, aby reagoval jenom na události v instanci seznamu vlastní oznámení **TestAnnouncements**.

## <a name="see-also"></a>Viz také
- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
