---
title: 'Návod: nasazení definice Seznam úkolů projektu | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b5639fe7a1b35dea41b14be3730986ad7c7309b7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015771"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Návod: nasazení definice seznamu úkolů projektu

Tento návod ukazuje, jak použít [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] k vytvoření, přizpůsobení, ladění a nasazení sharepointového seznamu pro sledování úkolů projektu.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

- Podporované edice Microsoft Windows a SharePointu.

- Visual Studio 2017 nebo Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Vytvoření SharePointového seznamu

Vytvořte projekt SharePointového seznamu a přidružte definici seznamu k úkolům.

1. Otevřete dialogové okno **Nový projekt** , rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

2. V podokně **šablony** zvolte šablonu **projektu SharePoint 2010** , pojmenujte projekt **ProjectTaskList**a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

3. Zadejte místní web služby SharePoint, který používáte pro ladění, zvolte přepínač **nasadit jako řešení farmy** a pak klikněte na tlačítko **Dokončit** .

4. Otevřete místní nabídku projektu a pak zvolte možnost **Přidat**  >  **novou položku**.

5. V podokně **šablony** zvolte šablonu **seznamu** a pak klikněte na tlačítko **Přidat** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

6. V poli **jaký název chcete zobrazit pro váš seznam?** zadejte **projekt seznam úkolů**.

7. Zvolte možnost **vytvořit nepřizpůsobitelný seznam na základě existujícího typu seznamu** možností a potom v seznamu vyberte položku **úlohy**a pak klikněte na tlačítko **Dokončit** .

     V **Průzkumník řešení**se zobrazí seznam, funkce a balíček.

## <a name="add-an-event-receiver"></a>Přidat přijímač událostí

V seznamu úkolů můžete přidat přijímač událostí, který automaticky nastaví datum splatnosti a popis úkolu. Následující postup přidá jednoduchou obslužnou rutinu události do instance seznamu jako přijímač událostí.

1. Otevřete místní nabídku uzlu projektu, zvolte možnost **Přidat**a poté možnost **Nová položka**.

2. V seznamu šablon služby SharePoint vyberte šablonu **příjemce událostí** a pojmenujte ji **ProjectTaskListEventReceiver**.

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

3. Na stránce **zvolit nastavení přijímače událostí** vyberte v seznamu typ přijímače událostí, **který chcete používat** , jako typ přijímače událostí možnost **události položky seznamu** .

4. V seznamu **jaká položka by měla být zdroj události** vyberte možnost **úlohy**.

5. V seznamu událostí, které mají být zpracovány zaškrtněte políčko vedle **položky bylo přidáno**, a poté klikněte na tlačítko **Dokončit** .

     Do projektu se přidá nový uzel přijímače událostí se souborem kódu s názvem **ProjectTaskListEventReceiver**.

6. Přidejte kód do `ItemAdded` metody v souboru kódu **ProjectTaskListEventReceiver** . Pokaždé, když se přidá nový úkol, do úkolu se přidá výchozí datum splatnosti a popis. Výchozí datum splatnosti je 1. července 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Přizpůsobení funkce seznamu úkolů projektu

Když vytvoříte řešení služby SharePoint, Visual Studio automaticky vytvoří funkce pro výchozí položky projektu. Můžete přizpůsobit nastavení seznamu úkolů projektu pro web služby SharePoint pomocí návrháře funkcí.

1. V **Průzkumník řešení**rozbalte možnost **funkce**.

2. Otevřete místní nabídku pro **Feature1**a pak zvolte možnost **Návrhář zobrazení**.

3. Do pole **název** zadejte **funkce Project seznam úkolů**.

4. V seznamu **obor** vyberte možnost **Web**.

5. V okně **vlastnosti** zadejte **1.0.0.0** jako hodnotu vlastnosti **Version** .

## <a name="customize-the-project-task-list-package"></a>Přizpůsobení balíčku seznamu úkolů projektu

Při vytváření projektu služby SharePoint sada Visual Studio automaticky přidá funkce, které obsahují výchozí položky projektu, do balíčku. Můžete přizpůsobit nastavení seznamu úkolů projektu pro web služby SharePoint pomocí návrháře balíčků.

1. V **SolutionExplorer**otevřete místní nabídku pro **balíček**a zvolte možnost **Návrhář zobrazení**.

2. Do pole **název** zadejte **ProjectTaskListPackage**.

3. Vyberte zaškrtávací políčko **resetovat webový server** .

## <a name="build-and-test-the-project-task-list"></a>Sestavování a testování seznamu úkolů projektu

Při spuštění projektu se otevře web služby SharePoint. Je však nutné ručně přejít do umístění seznamu úkolů.

1. Kliknutím na klávesu **F5** sestavíte a nasadíte seznam úkolů projektu.

     Otevře se web služby SharePoint.

2. Klikněte na kartu **Domů** .

3. Na levém bočním panelu vyberte odkaz **projekt seznam úkolů** .

     Zobrazí se stránka Seznam úkolů projektu.

4. Na kartě **Nástroje seznamu** klikněte na kartu **položky** .

5. Ve skupině **položky** klikněte na tlačítko **Nová položka** .

6. Do textového pole **název** zadejte **Task1**.

7. Klikněte na tlačítko **Uložit** .

     Po obnovení lokality se zobrazí úloha **Task1** s datem splatnosti 7/1/2009.

8. Vyberte **Task1**.

     Zobrazí se podrobné zobrazení úlohy a popis zobrazuje "Toto je kritická úloha."

## <a name="deploy-the-project-task-list"></a>Nasazení seznamu úkolů projektu

Po sestavení a otestování seznamu úkolů projektu jej můžete nasadit do *místního systému* nebo do *vzdáleného systému*. Místní systém je stejný počítač, na kterém jste toto řešení vyvinuli, zatímco vzdálený systém je jiný počítač.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Nasazení seznamu úkolů projektu do místního systému

Na řádku nabídek sady Visual Studio vyberte **sestavení**  >  **nasadit řešení**.

Sada Visual Studio recykluje fond aplikací služby IIS, odvolá všechny existující verze řešení, zkopíruje soubor balíčku řešení (*. wsp*) do služby SharePoint a poté aktivuje jeho funkce. Nyní můžete použít řešení v SharePointu. Další informace o postupu konfigurace nasazení najdete v tématu [Postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Nasazení seznamu úkolů projektu do vzdáleného systému

1. Na řádku nabídek sady Visual **Studio vyberte možnost**  >  **publikovat**.

2. V dialogovém okně **publikovat** klikněte na tlačítko možnosti **publikovat do systému souborů** .

     Cílové umístění můžete změnit v dialogovém okně **publikovat** tak, že vyberete ikonu tří teček se ![třemi tečkami](../sharepoint/media/ellipsisicon.gif "Ikona se třemi tečkami") a pak přejdete na jiné místo.

3. Klikněte na tlačítko **publikovat** .

     Pro řešení se vytvoří soubor *. wsp* .

4. Zkopírujte soubor *. wsp* do vzdáleného systému SharePoint.

5. `Add-SPUserSolution`K instalaci balíčku na vzdálené instalaci služby SharePoint použijte příkaz prostředí PowerShell. (Pro řešení farmy použijte `Add-SPSolution` příkaz.)

     Například, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. `Install-SPUserSolution`K nasazení řešení použijte příkaz prostředí PowerShell. (Pro řešení farmy použijte `Install-SPSolution` příkaz.)

     Například, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Další informace o vzdáleném nasazení najdete v tématu [používání řešení](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) a [přidávání a nasazování řešení pomocí PowerShellu v SharePointu 2010](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx).

## <a name="next-steps"></a>Další kroky

Další informace o přizpůsobení a nasazení řešení služby SharePoint najdete v následujících tématech:

- [Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)

- [Prostředí Windows PowerShell pro SharePoint Server 2010](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Viz také:
[Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
