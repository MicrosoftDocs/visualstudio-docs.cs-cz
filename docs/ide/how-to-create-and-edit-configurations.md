---
title: 'Postupy: vytvoření a úprava konfigurací'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d3f6b271eb6b9b663e30953fa597fb7d8cec6ac
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348523"
---
# <a name="how-to-create-and-edit-configurations"></a>Postupy: vytvoření a úprava konfigurací

Můžete vytvořit několik konfigurací sestavení řešení. Například můžete nakonfigurovat sestavení pro ladění, testerům můžete najít a opravit problémy, a můžete nakonfigurovat různé druhy sestavení, které můžete distribuovat do různých zákazníků.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [vytvoření a úprava konfigurací v sadě Visual Studio pro Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Vytvoření konfigurace sestavení

Můžete použít **nástroje Configuration Manager** dialogové okno Vybrat nebo změnit existující konfiguraci sestavení nebo vytvářet nové kategorie.

Otevřete **nástroje Configuration Manager** v dialogu **Průzkumníka řešení**, otevřete místní nabídku řešení a klikněte na tlačítko **nástroje Configuration Manager**.

> [!NOTE]
> Pokud **nástroje Configuration Manager** příkaz nezobrazí v místní nabídce vyhledejte v části **sestavení** nabídky na řádku nabídek. Pokud tam není, na panelu nabídek zvolte **nástroje** > **možnosti**a potom v levém podokně **možnosti** dialogového okna rozbalte **Projekty a řešení** > **Obecné**a v pravém podokně, vyberte **zobrazit pokročilé konfigurace sestavení** zaškrtávací políčko.

V **nástroje Configuration Manager** dialogové okno, můžete použít **konfigurace aktivního řešení** rozevíracího seznamu vyberte konfiguraci sestavení celého řešení, upravit existující nebo vytvořte nový konfigurace. Můžete použít **platformou aktivního řešení** rozevírací seznam a vyberte platformu, že konfigurace cíle, upravte nějaký existující, nebo přidat novou platformu. **Projektu kontexty** podokně je seznam projektů v řešení. Pro každý projekt můžete vybrat konfigurace specifické pro projekt a platformy, upravte stávající, nebo vytvořit novou konfiguraci nebo přidat novou platformu. Můžete také vybrat zaškrtávací políčka, která udává, jestli je každý projekt zahrnuty při konfiguraci celé řešení použijete k vytvoření buildu nebo nasazení řešení.

 Po nastavení konfigurace, které chcete, můžete nastavit vlastnosti projektu, které jsou vhodné pro tuto konfiguraci.

### <a name="to-set-properties-based-on-configurations"></a>Chcete-li nastavit vlastnosti konfigurace

-   V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.

     **Stránky vlastností** otevře se okno.

     Můžete nastavit vlastnosti pro konkrétní konfiguraci. Například pro konfiguraci vydané verze, můžete zadat, že je kód zoptimalizovaný při řešení je sestaveno a pro konfiguraci ladění, můžete určit, že `DEBUG` symbol podmíněné kompilace je součástí. Další informace o nastavení stránky vlastností naleznete v tématu [spravovat vlastnosti projektu a řešení](../ide/managing-project-and-solution-properties.md).

## <a name="create-and-modify-project-configurations"></a>Vytvoření a změny konfigurace projektu

### <a name="to-create-a-project-configuration"></a>Pro vytvoření konfigurace projektu

1.  Otevřít **nástroje Configuration Manager** dialogové okno.

2.  Vyberte projekt v **projektu** sloupce.

3.  V **konfigurace** rozevíracího seznamu pro daný projekt, zvolte **nový**.

     **Nové konfigurace projektu** zobrazí se dialogové okno.

4.  V **název** pole, zadejte název pro novou konfiguraci.

5.  Používané k nastavení vlastností z existující konfigurace projektu, **Kopírovat nastavení z:** rozevíracím seznamu klikněte na položku konfigurace.

6.  Chcete-li vytvořit konfiguraci celé řešení ve stejnou dobu, vyberte **vytvořit nová konfigurace řešení** zaškrtávací políčko.

### <a name="to-rename-a-project-configuration"></a>Chcete-li přejmenovat konfigurace projektu

1.  Otevřít **nástroje Configuration Manager** dialogové okno.

2.  V **projektu** sloupce, vyberte projekt, který obsahuje konfiguraci projektu, kterou chcete přejmenovat.

3.  V **konfigurace** rozevíracího seznamu pro daný projekt, zvolte **upravit**.

     **Upravit konfigurace projektu** zobrazí se dialogové okno.

4.  Vyberte název konfigurace projektu, který chcete změnit.

5.  Vyberte **přejmenovat**a pak zadejte nový název.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Vytvoření a úprava konfigurací sestavení celé řešení

### <a name="to-create-a-solution-wide-build-configuration"></a>Chcete-li vytvořit řešení celou konfiguraci sestavení

1.  Otevřít **nástroje Configuration Manager** dialogové okno.

2.  V **konfigurace aktivního řešení** rozevíracím seznamu klikněte na položku **nový**.

     **Nová konfigurace řešení** zobrazí se dialogové okno.

3.  V **název** textové pole, zadejte název pro novou konfiguraci.

4.  Chcete-li použít nastavení z existující konfigurace řešení, v **Kopírovat nastavení z:** rozevíracím seznamu klikněte na položku konfigurace.

5.  Pokud chcete vytvořit konfigurace projektu ve stejnou dobu, vyberte **vytvořit nové konfigurace projektu** zaškrtávací políčko.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Přejmenování řešení celou konfiguraci sestavení

1.  Otevřít **nástroje Configuration Manager** dialogové okno.

2.  V **konfigurace aktivního řešení** rozevíracím seznamu klikněte na položku **upravit**.

     **Upravit konfiguraci řešení** zobrazí se dialogové okno.

3.  Vyberte název konfigurace řešení, které chcete změnit.

4.  Vyberte **přejmenovat**a pak zadejte nový název.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Chcete-li změnit konfiguraci sestavení celé řešení

1.  Otevřít **nástroje Configuration Manager** dialogové okno.

2.  V **konfigurace aktivního řešení** rozevíracího seznamu vyberte konfigurace, kterou chcete.

3.  V **projektu kontexty** podokno pro každý projekt, vyberte **konfigurace** a **platformy** a vyberte, jestli se má **sestavení**ho a zda má být **nasadit** ho.

## <a name="see-also"></a>Viz také:

- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Sestavení a vyčištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Vytvoření a úprava konfigurací (Visual Studio for Mac)](/visualstudio/mac/create-and-edit-configurations)