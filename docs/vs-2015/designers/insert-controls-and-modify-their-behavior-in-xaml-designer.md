---
title: Vložení ovládacích prvků a změna jejich chování v Návrháři XAML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca377bcb37b44e1545d0502289217d331a495fae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179371"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Vložení ovládacích prvků a změna jejich chování v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ovládací prvky umožňují uživatelům, aby komunikovali s vaší aplikací. Můžete je použít ke shromažďování informací a k provádění akcí, jako animace objektu nebo dotazování na zdroj dat.  
  
 **V tomto tématu:**  
  
-   [Přidání ovládacích prvků na návrhové ploše](#Insert)  
  
-   [Ujistěte se, všechno ovládacích prvků](#Modify)  
  
##  <a name="Insert"></a> Přidání ovládacích prvků na návrhové ploše  
 Můžete přetáhnout ovládací prvky z **prostředky** panelu na **návrhové plochy**a následnou úpravou v **vlastnosti** okna.  
  
 ![Blend &#45; prostředky &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")  
  
 Tato videa se dozvíte, jak používat některé z běžných ovládacích prvků.  
  
|Ovládací prvek|Podívejte se na krátké video|  
|-------------|-------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [přidat ovládací prvky](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [navrhnout tlačítko](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [přidání obrázků na objektech textblock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815C-e98c930ac189")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [sestavení posuvníku s popisem](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracovat pomocí prvku GridSplitter](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Nastavení ovládacího prvku mimo obrázek, tvar nebo cesta  
 Můžete vytvořit libovolný objekt do ovládacího prvku.  
  
 ![Dialogové okno vytvořit do ovládacího prvku blendu](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")  
  
 Představte si například obrázek televize uprostřed stránky. Může nastavit ovládací prvky mimo malé obrázky, které vypadají jako televizní tlačítka. Poté mohou uživatelé kliknout na těchto tlačítek změna kanálu.  
  
 To je možné, protože tlačítka jsou nyní ovládacích prvků. Pomocí ovládacích prvků můžete reagovat na akce uživatele; v tomto případě, když uživatel klikne na tlačítko.  
  
 Chcete-li ovládací prvek, vyberte objekt. Potom na **nástroje** nabídky, klikněte na tlačítko **vytvořit ovládací prvek**.  
  
##  <a name="Modify"></a> Ujistěte se, všechno ovládacích prvků  
 Ovládací prvky můžete provádět akce, když uživatelé komunikovat s nimi. Například, můžete spustit animaci, aktualizovat zdroj dat nebo přehrávání videa.  
  
 Použití *triggery*, *chování*, a *události* aby všechno ovládací prvky.  
  
### <a name="triggers"></a>Aktivační procedury  
 A *aktivační událost* změní vlastnost nebo provede úlohu v reakci na událost nebo změnu jiné vlastnosti. Můžete například změnit barvu tlačítka, když uživatel najede myší ho.  
  
 ![Na panelu "Triggery"](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [přidat aktivační proceduru vlastností](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>Chování  
 A *chování* je opakovaně použitelné balíček kódu. To můžete udělat trochu více než změnit vlastnosti. Může provádět akce, jako je dotaz datové služby. Blend se dodává s malá skupina z nich, ale můžete přidat další. Chování přetáhnout na libovolný objekt v vaše návrhové plochy a poté přizpůsobit chování nastavením vlastností.  
  
 ![FluidMoveBehavior, na panelu Vlastnosti](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Blend tipy: Úvod do používání chování část 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Události  
 Pro maximální flexibilitu a zpracování *události*. Bude nutné napsat kód.  
  
 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [přidejte událost myši](https://www.youtube.com/watch?v=2PMxAlb-x_E).



