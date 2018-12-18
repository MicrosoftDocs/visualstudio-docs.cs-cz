---
title: 'Návod: Nasazení definice seznamu úloh projektu | Dokumentace Microsoftu'
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
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e0a0338f14ecdea36c5a5678a42a76ae234bb6d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280360"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Návod: Nasazení definice seznamu úloh projektu

Tento návod ukazuje, jak používat [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] vytvořit, upravit, ladit a nasadit Sharepointového seznamu, aby sledování úkolů v projektu.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

- Podporované vydání systému Microsoft Windows a SharePoint.

- Visual Studio 2017 nebo služby Azure DevOps.

## <a name="create-a-sharepoint-list"></a>Vytvoření Sharepointového seznamu

Vytvoření seznamu projektu služby SharePoint a přidružení definice seznamu úkolů.

1. Otevřít **nový projekt** dialogového okna rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.

2. V **šablony** podokně, vyberte **projektu služby SharePoint 2010** šablony, pojmenujte projekt **ProjectTaskList**a klikněte na tlačítko **OK**tlačítko.

     **Průvodce přizpůsobením SharePoint** se zobrazí.

3. Zadejte místní web služby SharePoint, který používáte pro ladění, zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko.

4. Otevřete místní nabídku pro projekt a klikněte na tlačítko **přidat** > **nová položka**.

5. V **šablony** podokně, vyberte **seznamu** šablony a klikněte na tlačítko **přidat** tlačítko.

     **Průvodce přizpůsobením SharePoint** se zobrazí.

6. V **zadejte název chcete pro seznam zobrazit?** zadejte **seznamu úkolů projektu**.

7. Zvolte **vytvořit nepřizpůsobitelná seznam založený na existujícím typu seznamu z** přepínač a pak ve svém seznamu zvolte **úlohy**a klikněte na tlačítko **Dokončit** tlačítko.

     Seznam, funkce a balíku joinkind **Průzkumníka řešení**.

## <a name="add-an-event-receiver"></a>Přidat přijímače událostí

V seznamu úkolů můžete přidat přijímače událostí, který automaticky nastaví splatnosti datum a popis úlohy. Následující procedura přidá obslužnou rutinu jednoduché události pro instanci seznamu jako přijímače událostí.

1. Otevřete místní nabídku pro uzel projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.

2. V seznamu šablon služby SharePoint, zvolte **příjemce událostí** šablony a pojmenujte jej **ProjectTaskListEventReceiver**.

     **Průvodce přizpůsobením SharePoint** se zobrazí.

3. Na **zvolit nastavení příjemce událostí** zvolte **události položky seznamu** jako typ příjemce událostí v **jaký typ příjemce událostí požadujete** seznamu.

4. V **jaká položka by měla být zdroj událostí** klikněte na položku **úlohy**.

5. V seznamu událostí ke zpracování, zaškrtněte políčko vedle položky **byla přidána položka**a klikněte na tlačítko **Dokončit** tlačítko.

     Přidání nového uzlu příjemce událostí do projektu se souborem kódu, který je pojmenován **ProjectTaskListEventReceiver**.

6. Přidejte kód, který `ItemAdded` metoda ve **ProjectTaskListEventReceiver** soubor kódu. Do úlohy pokaždé, když je přidán nový úkol, je přidán výchozí datum splatnosti a popis. Výchozí hodnota z důvodu je datum 1. července 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Přizpůsobit funkci seznamu úkolů projektu

Při vytváření řešení služby SharePoint sady Visual Studio automaticky vytvoří funkce pro výchozí položky projektu. Nastavení seznamu úkolů projektu pro web služby SharePoint lze přizpůsobit pomocí návrháře funkcí.

1. V **Průzkumníka řešení**, rozbalte **funkce**.

2. Otevřete místní nabídku pro **Feature1**a klikněte na tlačítko **Návrhář zobrazení**.

3. V **Title** zadejte **funkci seznamu úkolů projektu**.

4. V **oboru** klikněte na položku **webové**.

5. V **vlastnosti** okno, zadejte **1.0.0.0** hodnotu **verze** vlastnost.

## <a name="customize-the-project-task-list-package"></a>Přizpůsobení balíčku seznamu úloh projektu

Při vytváření projektu služby SharePoint sady Visual Studio automaticky přidá funkce, které obsahují výchozí položky projektu do balíčku. Nastavení seznamu úkolů projektu pro web služby SharePoint lze přizpůsobit pomocí návrháře balíčků.

1. V **SolutionExplorer**, otevřete místní nabídku pro **balíčku**a klikněte na tlačítko **Návrhář zobrazení**.

2. V **název** zadejte **ProjectTaskListPackage**.

3. Vyberte **resetovat Webový Server** zaškrtávací políčko.

## <a name="build-and-test-the-project-task-list"></a>Vytváření a testování seznamu úkolů projektu

Při spuštění projektu se otevře web služby SharePoint. Však musí ručně přejdete do umístění seznamu úkolů.

1. Zvolte **F5** klíč pro sestavování a nasazování seznamu úkolů projektu.

     Otevře se web služby SharePoint.

2. Zvolte **Domů** kartu.

3. Na levém bočním panelu, vyberte **seznamu úkolů projektu** odkaz.

     Zobrazí se stránka seznamu úkolů projektu.

4. V **nástroje seznamu** , vyberte **položky** kartu.

5. V **položky** skupině, zvolte **nová položka** tlačítko.

6. V **Title** textové pole, zadejte **Task1**.

7. Zvolte **Uložit** tlačítko.

     Po aktualizaci lokality **Task1** úloh se zobrazí s termínem splnění 7/1/2009.

8. Zvolte **Task1**.

     Zobrazí se v podrobném zobrazení úlohy a popis se zobrazí "Toto je důležité úlohy."

## <a name="deploy-the-project-task-list"></a>Nasadit projekt seznamu úkolů

Po sestavení a testování seznamu úkolů projektu, můžete ji nasazujete *místní systém* nebo *vzdálený systém*. Místní systém je do stejného počítače, na kterém jste vytvořili řešení, že vzdálený systém je do jiného počítače.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Nasazení seznamu úkolů projektu do místního systému

Na řádku nabídek sady Visual Studio, zvolte **sestavení** > **nasadit řešení**.

Recykluje se fond aplikací IIS, odvolá všechny existující verze řešení, zkopíruje balíček řešení sady Visual Studio (*.wsp*) souboru na Sharepointu a potom aktivuje její funkce. Nyní můžete řešení služby SharePoint. Další informace o postupu konfigurace nasazení najdete v tématu [postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Nasazení seznamu úkolů projektu do vzdáleného systému

1. Na řádku nabídek sady Visual Studio, zvolte **sestavení** > **publikovat**.

2. V **publikovat** dialogového okna zvolte **publikování do souborového systému** přepínač.

     V cílovém umístění můžete změnit **publikovat** dialogové okno kliknutím tlačítko se třemi tečkami ![ikonu se třemi tečkami](../sharepoint/media/ellipsisicon.gif "ikonu se třemi tečkami") a pak přejdete do jiného umístění.

3. Zvolte **publikovat** tlačítko.

     A *.wsp* vytvoří soubor řešení.

4. Kopírovat *.wsp* souboru do vzdáleného systému SharePoint.

5. Pomocí prostředí PowerShell `Add-SPUserSolution` příkaz k instalaci balíčku na vzdálenou instalaci služby SharePoint. (Pro řešení farmy, použijte `Add-SPSolution` příkazu.)

     Například `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Pomocí prostředí PowerShell `Install-SPUserSolution` příkaz pro nasazení řešení. (Pro řešení farmy, použijte `Install-SPSolution` příkazu.)

     Například `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Další informace o vzdáleném nasazení naleznete v tématu [pomocí řešení](http://go.microsoft.com/fwlink/?LinkId=217680) a [přidání a nasazení řešení pomocí prostředí PowerShell ve službě SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Další kroky

Další informace o postupu při přizpůsobení a nasazení řešení služby SharePoint v následujících tématech:

- [Návod: Vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)

- [Prostředí Windows PowerShell pro SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Viz také:
[Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
