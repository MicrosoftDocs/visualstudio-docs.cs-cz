---
title: Vložení ovládacích prvků a změna jejich chování v Návrháři XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 739c43b0ed6665684f0a38b35dfd6eccdf8f5b2c
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977801"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Vložení ovládacích prvků a změna jejich chování v Návrháři XAML

Ovládací prvky umožňují uživatelům, aby komunikovali s vaší aplikací. Můžete je použít ke shromažďování informací a k provádění akcí, jako animace objektu nebo dotazování na zdroj dat.

## <a name="add-controls-to-the-artboard"></a>Přidání ovládacích prvků na návrhové ploše

Můžete přetáhnout ovládací prvky z **prostředky** panelu na **návrhové plochy**a následnou úpravou v **vlastnosti** okna.

![Blend ovládací prvky karet prostředky](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Nastavení ovládacího prvku mimo obrázek, tvar nebo cesta

Můžete vytvořit libovolný objekt do ovládacího prvku.

![Dialogové okno vytvořit do ovládacího prvku programu Blend](../designers/media/blend_makeintocontrol_xaml.png)

Představte si například obrázek televize uprostřed stránky. Může nastavit ovládací prvky mimo malé obrázky, které vypadají jako televizní tlačítka. Poté mohou uživatelé kliknout na těchto tlačítek změna kanálu.

To je možné, protože tlačítka jsou nyní ovládacích prvků. Pomocí ovládacích prvků můžete reagovat na akce uživatele; v tomto případě, když uživatel klikne na tlačítko.

Chcete-li ovládací prvek, vyberte objekt. Potom na **nástroje** nabídky, klikněte na tlačítko **vytvořit ovládací prvek**.

## <a name="make-controls-do-things"></a>Ujistěte se, všechno ovládacích prvků

Ovládací prvky můžete provádět akce, když uživatelé komunikovat s nimi. Můžete například spustit animaci, aktualizovat zdroj dat nebo přehrávání videa.

Použití *triggery*, *chování*, a *události* aby všechno ovládací prvky.

### <a name="triggers"></a>Aktivační procedury

A *aktivační událost* změní vlastnost nebo provede úlohu v reakci na událost nebo změnu jiné vlastnosti. Můžete například změnit barvu tlačítka, když uživatel najede myší ho.

![Na panelu aktivační události](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>Chování

A *chování* je opakovaně použitelné balíček kódu. To můžete udělat trochu více než změnit vlastnosti. Může provádět akce, jako je dotaz datové služby. Blend se dodává s malá skupina chování ale můžete přidat další. Chování přetáhnout na libovolný objekt v vaše návrhové plochy a poté přizpůsobit chování nastavením vlastností.

![FluidMoveBehavior, na panelu Vlastnosti](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Podívejte se na video:** ![ikonu přehrávání](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend tipy: Úvod do používání chování část 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Události

Pro maximální flexibilitu a zpracování *události*. Bude nutné napsat kód.