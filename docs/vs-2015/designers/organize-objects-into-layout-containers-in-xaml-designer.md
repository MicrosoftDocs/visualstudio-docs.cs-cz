---
title: Uspořádání objektů do kontejnerů rozložení v Návrháři XAML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c92af4e78715c608fdee860690fd58561b8bb2d5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219554"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Uspořádání objektů do kontejnerů rozložení v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Představte si, kam chcete objektů se zobrazí na stránce. objekty, jako jsou obrázky, tlačítka a videa. Možná budete chtít zobrazit řádky a sloupce, na jednom řádku svisle nebo vodorovně nebo v pevné umístění.  
  
 Poté, co jste využili příležitost dobře se rozmyslete si, jak může zobrazit na stránce, zvolte panely rozložení. Všechny stránky spustit s jednou, protože potřebujete něco, co můžete přidat objekty do. Ve výchozím nastavení je **mřížky** ale můžete výběr změnit.  
  
 Panely rozložení můžete uspořádat objekty na stránce, ale více než oni. Jejich pomáhají navrhovat pro jiné velikosti obrazovky a jejich řešení. Když uživatelé spustí aplikaci, všechno v panelu rozložení změní velikost tak, aby odpovídaly nemovitosti obrazovku svého zařízení. Samozřejmě pokud nechcete, aby si rozložení, které provedete, můžete přepsat toto chování pro část rozložení nebo celý rozložení. Chcete-li ovládací prvek, který můžete použít vlastností výšky a šířky.  
  
 Tato stránka popisuje panely rozložení a ovládací prvky a pak přesměruje vás krátká videa, které vám pomůžou začít s nimi.  
  
> [!NOTE]
>  Některé z videa, která mohou odkazovat na Blendu nebo Expression Blend, která pomocí stejného návrháře XAML sady Visual Studio i programu Blend for Visual Studio.  
  
## <a name="layout-panels"></a>Panely rozložení  
 Vaše stránka Začněte výběrem jedné z těchto panelů rozložení. Stránka může mít více než jeden. Například můžete začít s **mřížky** rozložení panelu a pak přidejte **StackPanel** na oblast v **mřížky** tak, aby si můžete uspořádat ovládací prvky v tomto elementu svisle.  
  
 Následující panely rozložení jsou nejvíce popularly používá, ale existují i další. Najdete je všechny in **prostředky** panelu.  
  
-   [Mřížka](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Plátno](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Mřížka  
 Uspořádání objektů do řádků a sloupců.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441F-9136-98375fee87b7")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pomocí mřížky](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 Uspořádání objektů do mřížky stejných, nebo jednotných, oblastí. Tento panel se skvěle hodí k uspořádání seznamu imagí.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (K dispozici pouze pro projekty WPF)  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracovat UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Plátno  
 Uspořádání objektů požadovaným způsobem. Když uživatelé spustí aplikaci, budou tyto prvky pevné umístění na obrazovce.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracovat na plátno](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 Uspořádání objektů v jednom řádku vodorovně nebo svisle.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práce s StackPanel a WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 Uspořádání objektů postupně zleva doprava. Když je spuštěna na panelu dochází volné místo na pravé hraně ho *zabalí* obsah na další řádek, a tak dále zleva doprava, shora dolů. Můžete provést také orientace zalamovacího panelu svislé tak, aby objekty směrovat z horní části shora dolů, zleva doprava.  
  
 (K dispozici pouze pro projekty WPF)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práce s StackPanel a WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 Uspořádat objekty tak, aby zůstanou, nebo *ukotvit*, k jednomu z okrajů panelu.  
  
 (K dispozici pouze pro projekty WPF)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF – DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Rozložení ovládacích prvků  
 Do rozložení ovládacích prvků také můžete přidat objekty. Nejsou jako plně funkční jako panel rozložení, ale mohou být užitečné je pro určité scénáře.  
  
 Následující ovládací prvky rozložení se nejvíce popularly používají, ale existují i další. Najdete je všechny in **prostředky** panelu.  
  
-   [Ohraničení](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Ohraničení  
 Vytvoření ohraničení, pozadí nebo obojí kolem objektu. Můžete přidat pouze jeden objekt **ohraničení**. Pokud chcete použít ohraničení a pozadí pro více než jeden objekt, přidání panelu rozložení **ohraničení**. Potom můžete přidáte objekty do tohoto panelu nebo ovládacího prvku.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [práce s ohraničení](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> Automaticky otevíraného okna  
 Zobrazit informace nebo uživatelům v okně Možnosti. Můžete přidat pouze jeden objekt **automaticky otevírané okno**. Ve výchozím nastavení **automaticky otevírané okno** obsahuje **mřížky** ale můžete výběr změnit.  
  
###  <a name="Scroll"></a> Scrollviewer –  
 Povolte použití přejděte dolů na stránce nebo oblasti stránky. Můžete přidat pouze jeden objekt **ScrollViewer** , je velmi výhodné, chcete-li přidat panel rozložení, jako **mřížky** nebo **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
###  <a name="View"></a> Viewbox  
 Škálování objekty, které podobně jako s ovládacím prvkem přiblížení. Můžete přidat pouze jeden objekt **Viewbox**. Pokud chcete k použití tohoto efektu pro více než jeden objekt, přidat do panelu rozložení **ViewBox**a pak přidejte své ovládací prvky do panelu rozložení.  
  
 (K dispozici pouze pro projekty WPF)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Viz také  
 [Práce s elementy v Návrháři XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)



