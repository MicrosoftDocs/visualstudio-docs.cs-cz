---
title: 'Postupy: vytvoření přijímače událostí | Microsoft Docs'
description: Vytvořte přijímač událostí, abyste mohli reagovat na to, kdy uživatel komunikuje s položkami SharePointu, jako jsou seznamy nebo položky seznamu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: 1943bd8a652a88d218912ab0fc0f6227bf83bc95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885700"
---
# <a name="how-to-create-an-event-receiver"></a>Postupy: vytvoření přijímače událostí
  Vytvořením *přijímačů událostí* můžete reagovat, když uživatel komunikuje s položkami SharePointu, jako jsou seznamy nebo položky seznamu. Například kód v přijímači událostí může být aktivován, když uživatel změní kalendář nebo odstraní název ze seznamu kontaktů. V tomto tématu se dozvíte, jak přidat přijímač událostí do instance seznamu.

 Chcete-li provést tento postup, musíte mít nainstalované [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a podporované edice Windows a SharePointu. Vzhledem k tomu, že tento příklad vyžaduje projekt služby SharePoint, musíte také provést postup v tématu [Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Přidání přijímače událostí
 Projekt, který jste vytvořili v [návodu: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) zahrnuje vlastní sloupce webu, vlastní seznam a typ obsahu. V následujícím postupu rozbalíte tento projekt přidáním jednoduché obslužné rutiny události (přijímač událostí) do instance seznamu, která ukazuje, jak zpracovávat události, ke kterým dochází v položkách SharePointu, jako jsou seznamy.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Přidání přijímače událostí do instance seznamu

1. Otevřete projekt, který jste vytvořili v [návodu: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. V **Průzkumník řešení** vyberte uzel projektu služby SharePoint, který je pojmenován **Clinic**.

3. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

4. V části **Visual C#** nebo **Visual Basic** rozbalte uzel **SharePoint** a pak zvolte položku **2010** .

5. V podokně **šablony** zvolte položku **přijímač událostí**, pojmenujte ji **TestEventReceiver1** a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

6. V seznamu **jaký typ přijímače událostí chcete?** vyberte možnost **události položky seznamu**.

7. V seznamu **jaká položka by měla být zdroj události?** vyberte **pacienty (Clinic\Patients)**.

8. V seznamu **zpracovat následující události** zaškrtněte políčko vedle **položky bylo přidáno** a pak klikněte na tlačítko **Dokončit** .

     Soubor s kódem pro nového příjemce události obsahuje jedinou metodu s názvem `ItemAdded` . V dalším kroku přidáte kód do této metody tak, aby každý kontakt byl ve výchozím nastavení pojmenován Scott Brown.

9. Existující metodu nahraďte `ItemAdded` následujícím kódem a pak zvolte klávesu **F5** :

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Kód se spustí a SharePointový web se zobrazí ve webovém prohlížeči.

10. Na panelu Rychlé spuštění zvolte odkaz **pacienty** a pak zvolte odkaz **Přidat novou položku** .

     Otevře se vstupní formulář pro nové položky.

11. Do polí zadejte data a pak klikněte na tlačítko **Uložit** .

     Po kliknutí na tlačítko **Uložit** se sloupec **název pacienta** automaticky aktualizuje na název Scott Brown.

## <a name="see-also"></a>Viz také

- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)