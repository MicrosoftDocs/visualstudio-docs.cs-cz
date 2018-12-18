---
title: 'Postupy: vytvoření přijímače událostí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd4528a47215254684be51400329b05c3998bbab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635145"
---
# <a name="how-to-create-an-event-receiver"></a>Postupy: vytvoření přijímače událostí
  Vytvořením *přijímače událostí*, reagovat, když uživatel komunikuje s položek služby SharePoint, například seznamy nebo položky seznamu. Kód v přijímače událostí například může aktivuje, když uživatel změní kalendář nebo odstraní názvu ze seznamu kontaktů. Podle tohoto tématu se dozvíte, jak přidat přijímače událostí pro instanci seznamu.

 K dokončení těchto kroků, je třeba mít nainstalovanou [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a podporované edice systému Windows a SharePoint. Vzhledem k tomu, že tento příklad vyžaduje projektu služby SharePoint, je také nutné dokončit postup v tématu [návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Přidání přijímače událostí
 Projekt, který jste vytvořili v [návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) zahrnuje sloupců vlastního webu, z vlastního seznamu a typu obsahu. V následujícím postupu budete rozbalte tento projekt tak, že přidáte obslužnou rutinu události jednoduché (přijímače událostí) na instanci seznamu do ukazují, jak zpracovávat události, ke kterým dochází v položky služby SharePoint, například v seznamech.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Chcete-li přidat přijímače událostí pro instanci seznamu

1.  Otevřete projekt, který jste vytvořili v [návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2.  V **Průzkumníka řešení**, zvolte uzel projektu služby SharePoint, který se nazývá **Clinic**.

3.  V panelu nabídky zvolte **projektu** > **přidat novou položku**.

4.  V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** položky.

5.  V **šablony** podokně zvolte **příjemce událostí**, pojmenujte ho **TestEventReceiver1**a klikněte na tlačítko **OK** tlačítko.

     **Průvodce přizpůsobením SharePoint** se zobrazí.

6.  V **jaký typ příjemce událostí požadujete?** klikněte na položku **události položky seznamu**.

7.  V **jaká položka by měla být zdroj událostí?** klikněte na položku **pacientů (Clinic\Patients)**.

8.  V **zpracovávat následující události** seznam, zaškrtněte políčko vedle položky **byla přidána položka**a klikněte na tlačítko **Dokončit** tlačítko.

     Soubor kódu pro nového příjemce událostí obsahuje jedinou metodu s názvem `ItemAdded`. V dalším kroku přidáte kód pro tuto metodu tak, aby každý kontakt bude mít název Scott Brown ve výchozím nastavení.

9. Nahraďte existující `ItemAdded` metoda s tímto kódem a klikněte na tlačítko **F5** klíč:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Spuštění kódu a Sharepointový web se zobrazí ve webovém prohlížeči.

10. Na panelu Rychlé spuštění zvolte **pacientů** propojit a klikněte na tlačítko **přidat novou položku** odkaz.

     Otevře se formulář vstupu pro nové položky.

11. Do polí zadejte data a klikněte na tlačítko **Uložit** tlačítko.

     Po zvolení **Uložit** tlačítko, **pacienta název** sloupce automaticky aktualizuje na název Scott Brown.

## <a name="see-also"></a>Viz také:

- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)