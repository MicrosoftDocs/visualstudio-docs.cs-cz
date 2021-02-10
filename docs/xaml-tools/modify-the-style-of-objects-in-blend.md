---
title: Úpravy stylu objektů
titleSuffix: Blend for Visual Studio
description: Naučte se, jak upravit styl objektů v Blend pro Visual Studio použitím štětců, nastavením vizuálních stavů a aplikováním opakovaně použitelných stylů a šablon.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2b98f814e1f310c7d7f281457589a1a9f7d21653
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966549"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>Úprava stylu objektů v Blend pro Visual Studio

Nejjednodušší způsob, jak přizpůsobit objekt, je nastavit vlastnosti v podokně **vlastnosti** .

Pokud chcete znovu použít nastavení nebo skupiny nastavení, vytvořte opakovaně použitelný prostředek. Může se jednat o *styl*, *šablonu* nebo něco jednoduchého jako vlastní barva. Můžete také nastavit, aby se ovládací prvek zobrazoval odlišně v závislosti na jeho stavu. Například tlačítko se změní na zelenou, jakmile na něj uživatel klikne.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Štětce: Změna vzhledu objektu

Pokud chcete změnit jeho vzhled, použijte k objektu štětce.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malování opakujícího se obrázku nebo vzoru na objekt

Vykreslí opakující se obrázek nebo vzor objektu pomocí *štětce dlaždice*.

Chcete-li vytvořit štětec dlaždice, začněte tím, že vytvoříte prostředek *štětce obrázku*, *Kreslicí štětce* nebo *vizuálního štětce* .

Vytvoření obrázkového štětce pomocí obrázku. Následující ilustrace znázorňují obrázek štětce, obrázek štětce vedle sebe a Překlopí obrázek štětce.

![Obrázek štětce](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![štětec Mage vedle sebe](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Překlopení obrázku štětce](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Vytvořte štětec kresby pomocí vektorového vykreslování, jako je například cesta nebo tvar. Následující ilustrace znázorňují kreslicí štětce, kreslicí štětce vedle sebe a vykreslení štětce Překlopí.

![Kreslicí štětec](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Kreslení štětce vedle sebe](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Vykreslování štětce převráceno](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Vytvořte vizuální štětce z ovládacího prvku, jako je tlačítko. Následující ilustrace znázorňují vizuální štětec a vizuální štětce vedle sebe.

![Vizuální štětec](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Vizuální štětec vedle sebe](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Styly a šablony: vytvoření konzistentního vzhledu napříč ovládacími prvky

Vzhled a chování ovládacího prvku můžete navrhovat jednou a použít tento návrh i na jiné ovládací prvky, abyste je nemuseli udržovat individuálně.

**Měli byste použít styl?**: Pokud chcete nastavit pouze výchozí vlastnosti (například barvu tlačítka), použijte *styl*. Ovládací prvek můžete upravit i po použití stylu.

**Měli byste použít šablonu?**: Pokud chcete změnit strukturu ovládacího prvku, použijte *šablonu*. Představte si převod grafiky nebo loga na tlačítko. Nemůžete změnit ovládací prvek poté, co jste na něj použili šablonu.

### <a name="create-a-template-or-style"></a>Vytvoření šablony nebo stylu

Existují dva způsoby, jak vytvořit šablonu. Libovolný objekt na návrhové ploše můžete převést na ovládací prvek nebo můžete šablonu založit na stávajícím ovládacím prvku.

Chcete-li převést libovolný objekt na šablonu ovládacího prvku, vyberte objekt a potom v nabídce **nástroje** zvolte možnost **vytvořit k ovládacímu prvku**.

Pokud chcete šablonu založenou na existujícím ovládacím prvku, vyberte objekt na návrhové ploše. Pak v horní části návrhové plochy zvolte tlačítko s popisem cesty, zvolte **Upravit šablonu** a pak zvolte **Upravit kopii** nebo **vytvořit prázdné**.

![Nabídka upravit šablonu](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Chcete-li vytvořit styl, vyberte objekt a potom v nabídce **objekt** zvolte možnost **Upravit styl** a pak zvolte možnost **Upravit kopii** nebo **vytvořit prázdnou**.

- Vyberte možnost **Upravit kopii** a začněte s výchozím stylem nebo šablonou ovládacího prvku.

- Vyberte **vytvořit prázdné** a začněte od začátku.

Možnost **Upravit aktuální** se zobrazí pouze v případě, že upravíte styl nebo šablonu, kterou jste již vytvořili. Nezobrazí se pro ovládací prvek, který stále používá výchozí systémovou šablonu.

V dialogovém okně **vytvořit prostředek stylu** můžete buď pojmenovat styl nebo šablonu, abyste ji mohli použít později, nebo můžete použít styl nebo šablonu pro všechny ovládací prvky tohoto typu.

![Dialogové okno vytvořit prostředek stylu](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Pro každý typ ovládacího prvku nelze vytvářet styly ani šablony. Pokud je ovládací prvek nepodporuje, tlačítko s popisem cesty se nezobrazí nad návrhovou plochou.
> Pokud se chcete vrátit do oboru úprav hlavního dokumentu, klikněte na **vrátit obor a** ![ vraťte rozsah do ikony ](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png) .

### <a name="apply-a-style-or-template-to-a-control"></a>Použití stylu nebo šablony pro ovládací prvek

V okně [objekty a časová osa](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) klikněte pravým tlačítkem myši na objekt, zvolte možnost **Upravit šablonu** a pak zvolte **použít prostředek**.

![Nabídka použít prostředek](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Obnovení výchozího stylu nebo šablony ovládacího prvku

Vyberte ovládací prvek a v okně * * Vlastnosti * * * * vyhledejte vlastnost **style** nebo **template** . Zvolte **Upřesnit možnosti** a potom v místní nabídce klikněte na **obnovit** .

## <a name="visual-states"></a>Vizuální stavy

Vizuální stavy umožňují změnit vzhled ovládacího prvku na základě jeho stavu. Ovládací prvky mohou mít různé vizuální vzhledy na základě interakcí uživatelů. Například můžete nastavit, aby se tlačítko zeleně, když na něj uživatel klikne, nebo můžete spustit animaci. Zkraťte nebo prodlužte dobu mezi vizuálními stavy pomocí přechodů.

![Myš nad stavem](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Podívejte se na krátké video:** ![ Tlačítko Přehrát – ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [umožňuje spravovat stav ovládacích prvků WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Prostředky: vytvořit barvy, styly a šablony a později je znovu použít

V projektu můžete převést prakticky cokoli na prostředek. Prostředek je pouze objekt, který lze použít na různých místech aplikace. Můžete například vytvořit barvu jednou, nastavit ji jako prostředek a potom použít tuto barvu u několika objektů. Chcete-li změnit barvu všech těchto objektů, stačí změnit zdroj barvy.

![Tlačítko převést barvu na prostředek](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Dialogové okno vytvořit prostředek barvy](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Viz také

- [Vytvoření uživatelského rozhraní pomocí nástroje Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
