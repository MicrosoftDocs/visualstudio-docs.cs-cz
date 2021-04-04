---
title: 'Návod: Vytvoření vlastní aktivity pracovního postupu webu | Microsoft Docs'
description: V tomto návodu najdete informace v tématu Postup vytvoření vlastní aktivity pro pracovní postup SharePointu na úrovni webu pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29a3cd6fe37ec824a3db3a2c83aad7434d0018cb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218045"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Návod: Vytvoření vlastní aktivity pracovního postupu webu
  Tento návod ukazuje, jak vytvořit vlastní aktivitu pro pracovní postup na úrovni webu pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Pracovní postupy na úrovni webu platí pro celou lokalitu, ne jenom pro seznam na webu.) Vlastní aktivita vytvoří seznam oznámení o zálohování a potom do něj zkopíruje obsah seznamu oznámení.

 Tento názorný postup ukazuje následující úlohy:

- Vytváření pracovního postupu na úrovni webu.

- Vytvoření vlastní aktivity pracovního postupu.

- Vytvoření a odstranění seznamu služby SharePoint.

- Kopírování položek z jednoho seznamu do jiného.

- Zobrazení seznamu na panelu Rychlé spuštění

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

- Visual Studio

## <a name="create-a-site-workflow-custom-activity-project"></a>Vytvořit projekt vlastní aktivity pracovního postupu webu
 Nejprve vytvořte projekt pro blokování a testování vlastní aktivity pracovního postupu.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Vytvoření projektu vlastní aktivity pracovního postupu webu

1. Na panelu nabídek vyberte možnost **soubor**  >  **Nový**  >  **projekt** . zobrazí se dialogové okno **Nový projekt** .

2. Rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

3. V podokně **šablony** vyberte šablonu **projektu SharePoint 2010** .

4. Do pole **název** zadejte **AnnouncementBackup** a poté klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

5. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zvolte možnost **nasadit jako řešení farmy** a pak kliknutím na tlačítko **Dokončit** přijměte úroveň vztahu důvěryhodnosti a výchozí web.

     Tento krok nastaví úroveň důvěryhodnosti pro řešení jako řešení farmy, což je jediná dostupná možnost pro projekty pracovního postupu.

6. V **Průzkumník řešení** zvolte uzel projektu a potom v řádku nabídek zvolte **projekt**  >  **Přidat novou položku**.

7. V části **Visual C#** nebo **Visual Basic** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

8. V podokně **šablony** zvolte šablonu **sekvenční pracovní postup (pouze řešení farmy)** a pak klikněte na tlačítko **Přidat** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

9. Na stránce **Zadejte název pracovního postupu pro ladění** přijměte výchozí název (AnnouncementBackup-Workflow1). Změňte typ šablony pracovního postupu na **pracovní postup webu** a potom klikněte na tlačítko **Další** .

10. Kliknutím na tlačítko **Dokončit** Potvrďte zbývající výchozí nastavení.

## <a name="add-a-custom-workflow-activity-class"></a>Přidání vlastní třídy aktivity pracovního postupu
 Dále do projektu přidejte třídu, která bude obsahovat kód pro vlastní aktivitu pracovního postupu.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Přidání vlastní třídy aktivity pracovního postupu

1. Na panelu nabídek vyberte možnost **projekt**  >  **Přidat novou položku** , chcete-li zobrazit dialogové okno **Přidat novou položku** .

2. V zobrazení stromu **nainstalovaných šablon** zvolte uzel **kódu** a pak zvolte šablonu **třídy** v seznamu šablon položek projektu. Použijte výchozí název Class1. Vyberte tlačítko **Přidat**.

3. Nahraďte celý kód v Class1 následujícím způsobem:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. Uložte projekt a potom v řádku nabídek zvolte **sestavit**  >  **sestavení řešení**.

     Class1 se zobrazí jako vlastní akce v **sadě nástrojů** na kartě **komponenty AnnouncementBackup** .

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Přidání vlastní aktivity do pracovního postupu webu
 Dále přidejte aktivitu do pracovního postupu, která bude obsahovat vlastní kód.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Přidání vlastní aktivity do pracovního postupu webu

1. Otevřete Workflow1 v Návrháři postupu v návrhovém zobrazení.

2. Přetáhněte Class1 ze **sady nástrojů** tak, aby se zobrazila pod `onWorkflowActivated1` aktivitou, nebo otevřete místní nabídku pro Class1, zvolte **Kopírovat**, otevřete místní nabídku pro řádek v rámci `onWorkflowActivated1` aktivity a pak zvolte **Vložit**.

3. Uložte projekt.

## <a name="test-the-site-workflow-custom-activity"></a>Testování vlastní aktivity pracovního postupu webu
 Dále spusťte projekt a spusťte pracovní postup webu. Vlastní aktivita vytvoří seznam oznámení o zálohování a zkopíruje obsah ze seznamu aktuálních oznámení do něj. Kód také kontroluje, zda seznam zálohování již existuje, a teprve potom ho vytvořte. Pokud seznam zálohování již existuje, bude odstraněn. Kód také přidá odkaz na nový seznam na panelu Rychlé spuštění webu služby SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Testování vlastní aktivity pracovního postupu webu

1. Kliknutím na klávesu **F5** spusťte projekt a nasaďte ho na SharePoint.

2. Na panelu Rychlé spuštění klikněte na odkaz **seznamy** pro zobrazení všech seznamů, které jsou k dispozici na webu služby SharePoint. Všimněte si, že pro oznámení s názvem **oznámení** je k dispozici pouze jeden seznam.

3. V horní části webové stránky služby SharePoint vyberte odkaz **pracovní postupy webu** .

4. V části začít nový pracovní postup vyberte odkaz **AnnouncementBackup-Workflow1** . Tím se spustí pracovní postup webu a spustí se kód ve vlastní akci.

5. Na panelu Rychlé spuštění klikněte na odkaz **záloha oznámení** . Všimněte si, že všechna oznámení, která jsou obsažena v seznamu **oznámení** , byla zkopírována do tohoto nového seznamu.

## <a name="see-also"></a>Viz také
- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
