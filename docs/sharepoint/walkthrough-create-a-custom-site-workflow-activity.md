---
title: 'Návod: Vytvoření vlastní pracovní postup aktivity na webu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2adb6dd8788027d89a743518adee4425e424ce60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894167"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Návod: Vytvoření vlastní pracovní postup aktivity webu
  Tento návod ukazuje, jak vytvořit vlastní aktivitu pro pracovní postup na úrovni serveru pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Pracovní postupy na úrovni serveru platí pro celý web, nikoli pouze seznam na webu.) Vlastní aktivita vytvoří zálohu seznam oznámení a pak do něj zkopíruje obsah seznam oznámení.  
  
 Tento návod demonstruje následující úkoly:  
  
- Vytvoření pracovního postupu úrovni webu.  
  
- Vytváří se vlastní pracovní aktivitu.  
  
- Vytváření a odstraňování Sharepointového seznamu.  
  
- Kopírování položky z jednoho seznamu do jiného.  
  
- Zobrazení seznamu na panelu Rychlé spuštění.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.
  
-   Visual Studio.  
  
## <a name="create-a-site-workflow-custom-activity-project"></a>Vytvoření projektu webu vlastní aktivity pracovního postupu
 Nejprve vytvořte projekt k uložení a otestovat vlastní pracovní aktivitu.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Vytvoření projektu webu vlastní aktivity pracovního postupu  
  
1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt** dialogové okno.  
  
2.  Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
3.  V **šablony** podokně, vyberte **projektu služby SharePoint 2010** šablony.  
  
4.  V **název** zadejte **AnnouncementBackup**a klikněte na tlačítko **OK** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
5.  Na **zadejte web a úroveň zabezpečení pro ladění** zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko tak, aby přijímal vztah důvěryhodnosti úroveň a výchozí web.  
  
     Tento krok nastaví úroveň důvěryhodnosti řešení jako řešení farmy, jediná dostupná možnost pro projekty pracovního postupu.  
  
6.  V **Průzkumníka řešení**, zvolte uzel projektu a pak na panelu nabídek zvolte **projektu** > **přidat novou položku**.  
  
7.  V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
8.  V **šablony** podokně, vyberte **sekvenčního pracovního postupu (pouze řešení farmy)** šablony a klikněte na tlačítko **přidat** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
9. Na **zadejte název pracovního postupu pro ladění** stránce, přijměte výchozí název (AnnouncementBackup - Workflow1). Změňte typ šablony pracovního postupu na **pracovní postup webu**a klikněte na tlačítko **Další** tlačítko.  
  
10. Zvolte **Dokončit** tlačítko potvrďte zbývající výchozí nastavení.  
  
## <a name="add-a-custom-workflow-activity-class"></a>Přidání třídy activity vlastní pracovní postup
 V dalším kroku přidejte třídu do projektu tak, aby obsahovala kód pro vlastní pracovní aktivitu.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Chcete-li přidat třídy activity vlastní pracovní postup  
  
1.  V panelu nabídky zvolte **projektu** > **přidat novou položku** zobrazíte **přidat novou položku** dialogové okno.  
  
2.  V **nainstalované šablony** stromové zobrazení, zvolte **kód** uzel a klikněte na tlačítko **třídy** šablony v seznamu šablon položek projektu. Použití výchozího názvu Class1. Zvolte **přidat** tlačítko.  
  
3.  Veškerý kód v Class1 nahraďte následujícím kódem:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Uložte projekt a pak na panelu nabídek zvolte **sestavení** > **sestavit řešení**.  
  
     Class1 se zobrazí jako vlastní akce v **nástrojů** na **AnnouncementBackup součásti** kartu.  
  
## <a name="add-the-custom-activity-to-the-site-workflow"></a>Přidat vlastní aktivity pracovního postupu lokality
 V dalším kroku přidáte aktivitu do pracovního postupu tak, aby obsahovala vlastní kód.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Chcete-li přidat vlastní aktivity do pracovního postupu lokality
  
1.  V Návrháři pracovních postupů v návrhovém zobrazení otevřete Workflow1.  
  
2.  Přetáhněte Class1 z **nástrojů** tak, aby se objevila pod `onWorkflowActivated1` aktivity nebo otevřete místní nabídku pro Class1, zvolte **kopírování**, otevřete místní nabídku pro řádek u `onWorkflowActivated1` aktivita a klikněte na tlačítko **vložit**.  
  
3.  Uložte projekt.  
  
## <a name="test-the-site-workflow-custom-activity"></a>Vlastní aktivita pracovního postupu lokality testu
 V dalším kroku spusťte projekt a spustit webový pracovní postup. Vlastní aktivita vytvoří záložní seznam oznámení a zkopíruje obsah z aktuální seznam oznámení do něj. Kód také zkontroluje, jestli seznam záloh je už před vytvořením jedné. Pokud záložní seznam již existuje, je odstranit. Kód také přidá odkaz do nového seznamu na panelu Rychlé spuštění webu služby SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Testování webu vlastní aktivity pracovního postupu  
  
1.  Zvolte **F5** klávesy spusťte projekt a nasaďte ji do služby SharePoint.  
  
2.  Na panelu Rychlé spuštění zvolte **uvádí** odkazu zobrazíte všechny seznamy, které jsou k dispozici na Sharepointovém webu. Všimněte si, že existuje pouze jeden seznam oznámení s názvem o **oznámení**.  
  
3.  V horní části stránky na webovou stránku služby SharePoint, zvolte **pracovní postupy uzlu** odkaz.  
  
4.  V části úvodní části nového pracovního postupu, vyberte **AnnouncementBackup - Workflow1** odkaz. To spustí pracovní postup lokalitě a spouští kód ve vlastní akci.  
  
5.  Na panelu Rychlé spuštění zvolte **oznámení zálohování** odkaz. Všimněte si, že všechna oznámení, které jsou součástí **oznámení** seznamu byly zkopírovány do tohoto nového seznamu.  
  
## <a name="see-also"></a>Viz také:
 [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
