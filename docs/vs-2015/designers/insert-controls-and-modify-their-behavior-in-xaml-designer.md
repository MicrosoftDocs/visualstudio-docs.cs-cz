---
title: Vložení ovládacích prvků a změna jejich chování v Návrhář XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02d51c5799391863262d285e1cda209a3b7938d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300867"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Vložení ovládacích prvků a změna jejich chování v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ovládací prvky umožňují uživatelům pracovat s vaší aplikací. Můžete je použít ke shromažďování informací a k provádění akcí, jako je například animace objektu nebo dotazování na zdroj dat.

 **V tomto tématu:**

- [Přidání ovládacích prvků na návrhovou plochu](#Insert)

- [Udělat ovládací prvky jako věci](#Modify)

## <a name="add-controls-to-the-artboard"></a><a name="Insert"></a> Přidání ovládacích prvků na návrhovou plochu
 Ovládací prvky lze přetáhnout z panelu **aktiva** na návrhovou **plochu**a následně je upravit v okně **vlastnosti** .

 ![Prostředky Blend &#45; &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")

 Tato videa ukazují, jak používat některé z nejběžnějších ovládacích prvků.

|Řízení|Podívejte se na krátké video|
|-------------|-------------------------|
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Přidání ovládacích prvků](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [návrh tlačítka](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Přidání imagí do TextBlock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [sestaví posuvník pomocí popisku](https://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A) .|
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [funguje s GridSplitter](https://www.youtube.com/watch?v=bf4t6c8ms2w)|

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Nastavení ovládacího prvku na obrázek, tvar nebo cestu
 Libovolný objekt lze vytvořit do ovládacího prvku.

 ![Dialogové okno vytvořit v Blendu do ovládacího prvku](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")

 Představte si například obrázek televizoru ve středu stránky. Ovládací prvky můžete nastavit na malém obrázku, který bude vypadat jako na televizních tlačítkách. Pak by uživatelé mohli kanál změnit kliknutím na tato tlačítka.

 To je možné, protože tlačítka jsou nyní ovládacími prvky. S ovládacími prvky můžete reagovat na interakce s uživatelem; v takovém případě, když uživatel klikne na tlačítko.

 Chcete-li vytvořit ovládací prvek, vyberte objekt. Potom v nabídce **nástroje** klikněte na tlačítko **nastavit ovládací prvek**.

## <a name="make-controls-do-things"></a><a name="Modify"></a> Udělat ovládací prvky jako věci
 Ovládací prvky mohou provádět akce, když uživatelé s nimi pracují. Například mohou spustit animaci, aktualizovat zdroj dat nebo přehrát video.

 Použijte *triggery*, *chování*a *události* , aby ovládací prvky provedly věci.

### <a name="triggers"></a>Aktivační události
 *Aktivační událost* změní vlastnost nebo provede úkol v reakci na událost nebo změnu v jiné vlastnosti. Můžete například změnit barvu tlačítka, když na něj uživatel najede myší.

 ![Panel triggery](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")

 **Podívejte se na krátké video:** ![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") – [přidejte Trigger vlastnosti](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).

### <a name="behaviors"></a>Chování
 *Chování* je opakovaně použitelný balíček kódu. Může to udělat trochu víc než změnit vlastnosti. Může provádět akce, jako je dotazování datové služby. Blend se dodává s malým počtem těchto dat, ale můžete přidat další. Přetáhněte chování na libovolný objekt na návrhové ploše a pak přizpůsobení chování nastavením vlastností.

 ![Akcí fluidmovebehavior na panelu Vlastnosti](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tipy pro prolnutí: Úvod k použití chování část 1](https://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Události
 Pro maximální flexibilitu zpracujte *událost*. Budete muset napsat nějaký kód.

 **Podívejte se na krátké video:** ![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Přidat událost myši](https://www.youtube.com/watch?v=2PMxAlb-x_E).
