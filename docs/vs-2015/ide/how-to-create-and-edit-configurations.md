---
title: 'Postupy: vytvoření a úprava konfigurací | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f171c337f73db495b7b71aded24f669b6e613a07
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887784"
---
# <a name="how-to-create-and-edit-configurations"></a>Postupy: Vytvoření a úprava konfigurací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit několik konfigurací sestavení řešení. Například můžete nakonfigurovat sestavení pro ladění, testerům můžete najít a opravit problémy, a můžete nakonfigurovat různé druhy sestavení, které můžete distribuovat do různých zákazníků.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-build-configurations"></a>Vytváření konfigurací sestavení  
 Můžete použít **nástroje Configuration Manager** dialogové okno Vybrat nebo změnit existující konfiguraci sestavení, nebo můžete vytvořit nové.  
  
#### <a name="to-open-the-configuration-manager-dialog-box"></a>Chcete-li otevřít dialogové okno nástroje Configuration Manager  
  
- V **Průzkumníka řešení**, otevřete místní nabídku řešení a klikněte na tlačítko **nástroje Configuration Manager**.  
  
  > [!NOTE]
  >  Pokud **nástroje Configuration Manager** příkaz nezobrazí v místní nabídce vyhledejte v části **sestavení** nabídky na řádku nabídek. Pokud tam není, na panelu nabídek zvolte **nástroje**, **možnosti**a potom v levém podokně **možnosti** dialogového okna rozbalte **projekty a Řešení**, **Obecné**a v pravém podokně, vyberte **zobrazit pokročilé konfigurace sestavení** zaškrtávací políčko.  
  
   V **nástroje Configuration Manager** dialogové okno, můžete použít **konfigurace aktivního řešení** rozevíracího seznamu vyberte konfiguraci sestavení celého řešení, upravit existující nebo vytvořte nový konfigurace. Můžete použít **platformou aktivního řešení** rozevírací seznam a vyberte platformu, že konfigurace cíle, upravte nějaký existující, nebo přidat novou platformu. **Projektu kontexty** podokně je seznam projektů v řešení. Pro každý projekt můžete vybrat konfigurace specifické pro projekt a platformy, upravte stávající, nebo vytvořit novou konfiguraci nebo přidat novou platformu. Můžete také vybrat zaškrtávací políčka, která udává, jestli je každý projekt zahrnuty při konfiguraci celé řešení použijete k vytvoření buildu nebo nasazení řešení.  
  
  Po nastavení konfigurace, které chcete, můžete nastavit vlastnosti projektu, které jsou vhodné pro tuto konfiguraci.  
  
#### <a name="to-set-properties-based-on-configurations"></a>Chcete-li nastavit vlastnosti konfigurace  
  
-   V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.  
  
     **Stránky vlastností** otevře se okno.  
  
     Můžete nastavit vlastnosti pro konkrétní konfiguraci. Například pro konfiguraci vydané verze, můžete zadat, že je kód zoptimalizovaný při řešení je sestaveno a pro konfiguraci ladění, můžete určit, že `DEBUG` symbol podmíněné kompilace je součástí. Další informace o nastavení stránky vlastností naleznete v tématu [Úvod do Návrháře projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## <a name="creating-and-modifying-project-configurations"></a>Vytvoření a úprava konfigurace projektu  
  
#### <a name="to-create-a-project-configuration"></a>Pro vytvoření konfigurace projektu  
  
1.  Otevřít **nástroje Configuration Manager** dialogové okno.  
  
2.  Vyberte projekt v **projektu** sloupce.  
  
3.  V **konfigurace** rozevíracího seznamu pro daný projekt, zvolte **nový**.  
  
     **Nové konfigurace projektu** zobrazí se dialogové okno.  
  
4.  V **název** pole, zadejte název pro novou konfiguraci.  
  
5.  Používané k nastavení vlastností z existující konfigurace projektu, **Kopírovat nastavení z:** rozevíracím seznamu klikněte na položku konfigurace.  
  
6.  Chcete-li vytvořit konfiguraci celé řešení ve stejnou dobu, vyberte **vytvořit nová konfigurace řešení** zaškrtávací políčko.  
  
#### <a name="to-rename-a-project-configuration"></a>Chcete-li přejmenovat konfigurace projektu  
  
1.  Otevřít **nástroje Configuration Manager** dialogové okno.  
  
2.  V **projektu** sloupce, vyberte projekt, který obsahuje konfiguraci projektu, kterou chcete přejmenovat.  
  
3.  V **konfigurace** rozevíracího seznamu pro daný projekt, zvolte **upravit**.  
  
     **Upravit konfigurace projektu** zobrazí se dialogové okno.  
  
4.  Vyberte název konfigurace projektu, který chcete změnit.  
  
5.  Vyberte **přejmenovat**a pak zadejte nový název.  
  
## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Konfigurace sestavení pro vytváření a úpravy celé řešení  
  
#### <a name="to-create-a-solution-wide-build-configuration"></a>Chcete-li vytvořit řešení celou konfiguraci sestavení  
  
1.  Otevřít **nástroje Configuration Manager** dialogové okno.  
  
2.  V **konfigurace aktivního řešení** rozevíracím seznamu klikněte na položku **nový**.  
  
     **Nová konfigurace řešení** zobrazí se dialogové okno.  
  
3.  V **název** textové pole, zadejte název pro novou konfiguraci.  
  
4.  Chcete-li použít nastavení z existující konfigurace řešení, v **Kopírovat nastavení z:** rozevíracím seznamu klikněte na položku konfigurace.  
  
5.  Pokud chcete vytvořit konfigurace projektu ve stejnou dobu, vyberte **vytvořit nové konfigurace projektu** zaškrtávací políčko.  
  
#### <a name="to-rename-a-solution-wide-build-configuration"></a>Přejmenování řešení celou konfiguraci sestavení  
  
1.  Otevřít **nástroje Configuration Manager** dialogové okno.  
  
2.  V **konfigurace aktivního řešení** rozevíracím seznamu klikněte na položku **upravit**.  
  
     **Upravit konfiguraci řešení** zobrazí se dialogové okno.  
  
3.  Vyberte název konfigurace řešení, které chcete změnit.  
  
4.  Vyberte **přejmenovat**a pak zadejte nový název.  
  
#### <a name="to-modify-a-solution-wide-build-configuration"></a>Chcete-li změnit konfiguraci sestavení celé řešení  
  
1.  Otevřít **nástroje Configuration Manager** dialogové okno.  
  
2.  V **konfigurace aktivního řešení** rozevíracího seznamu vyberte konfigurace, kterou chcete.  
  
3.  V **projektu kontexty** podokno pro každý projekt, vyberte **konfigurace** a **platformy** a vyberte, jestli se má **sestavení**ho a zda má být **nasadit** ho.  
  
## <a name="see-also"></a>Viz také  
 [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)   
 [Sestavování a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [NIB postupy: Změna vlastností projektu a nastavení konfigurace](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)



