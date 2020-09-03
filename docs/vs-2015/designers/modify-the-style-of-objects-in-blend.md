---
title: Úprava stylu objektů v Blendu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0335efcb0c42c6fce06df448a0503457e79ec345
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664235"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Úpravy stylu objektů v Blendu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejjednodušší způsob, jak přizpůsobit objekt, je nastavit vlastnosti v podokně **vlastnosti** .

 Pokud chcete znovu použít nastavení nebo skupiny nastavení, vytvořte znovu použitelný prostředek. Může se jednat o *styl*, *šablonu*nebo něco jednoduchého jako vlastní barva. Můžete také nastavit, aby se ovládací prvek zobrazoval odlišně v závislosti na jeho stavu. Například tlačítko se změní na zelenou, jakmile na něj uživatel klikne.

 **V tomto tématu**:

- [Štětce: Změna vzhledu objektu](#Brushes)

- [Styly a šablony: vytvoření konzistentního vzhledu napříč ovládacími prvky](#Styles)

- [Vizuální stavy: Změna vzhledu ovládacího prvku na základě jeho stavu](#Visual)

- [Prostředky: vytvořit barvy, styly a šablony a později je znovu použít](#Resources)

## <a name="brushes-modify-the-appearance-of-an-object"></a><a name="Brushes"></a> Štětce: Změna vzhledu objektu
 Pokud chcete změnit jeho vzhled, použijte k objektu štětce.

 **Podívejte se na krátké video:** ![nakonfigurujte nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Editor štětců](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malování opakujícího se obrázku nebo vzoru na objekt
 Vykreslí opakující se obrázek nebo vzor objektu pomocí *štětce dlaždice*.

 Chcete-li vytvořit štětec dlaždice, začněte tím, že vytvoříte prostředek *štětce obrázku*, *Kreslicí štětce*nebo *vizuálního štětce* .

 Vytvoření obrázkového štětce pomocí obrázku. Následující ilustrace znázorňují obrázek štětce, obrázek štětce vedle sebe a Překlopí obrázek štětce.

 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")

 Vytvořte štětec kresby pomocí vektorového vykreslování, jako je například cesta nebo tvar. Následující ilustrace znázorňují kreslicí štětce, kreslicí štětce vedle sebe a vykreslení štětce Překlopí.

 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")

 Vytvořte vizuální štětce z ovládacího prvku, jako je tlačítko. Následující ilustrace znázorňují vizuální štětec a vizuální štětce vedle sebe.

 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")

 **Podívejte se na krátké video:** ![Konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [štětce dlaždice](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a><a name="Styles"></a> Styly a šablony: vytvoření konzistentního vzhledu napříč ovládacími prvky
 Vzhled a chování ovládacího prvku můžete navrhovat jednou a použít tento návrh i na jiné ovládací prvky, abyste je nemuseli udržovat individuálně.

 **Měli byste použít styl?**: Pokud chcete nastavit pouze výchozí vlastnosti (například barvu tlačítka), použijte *styl*. Ovládací prvek můžete upravit i po použití stylu.

 **Měli byste použít šablonu?**: Pokud chcete změnit strukturu ovládacího prvku, použijte *šablonu*. Představte si převod grafiky nebo loga na tlačítko. Nemůžete změnit ovládací prvek poté, co jste na něj použili šablonu.

### <a name="create-a-template-or-style"></a>Vytvoření šablony nebo stylu
 Existují dva způsoby, jak vytvořit šablonu. Libovolný objekt na návrhové ploše můžete převést na ovládací prvek nebo můžete šablonu založit na stávajícím ovládacím prvku.

 Chcete-li převést libovolný objekt na šablonu ovládacího prvku, vyberte objekt a potom v nabídce **nástroje** zvolte možnost **vytvořit k ovládacímu prvku**.

 Pokud chcete šablonu založenou na existujícím ovládacím prvku, vyberte objekt na návrhové ploše. Pak v horní části návrhové plochy zvolte tlačítko s popisem cesty, zvolte **Upravit šablonu**a pak zvolte **Upravit kopii** nebo **vytvořit prázdné**.

 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")

 Chcete-li vytvořit styl, vyberte objekt a potom v nabídce **objekt** zvolte možnost **Upravit styl**a pak zvolte možnost **Upravit kopii** nebo **vytvořit prázdnou**.

- Vyberte možnost **Upravit kopii** a začněte s výchozím stylem nebo šablonou ovládacího prvku.

- Vyberte **vytvořit prázdné** a začněte od začátku.

  Možnost **Upravit aktuální** se zobrazí pouze v případě, že upravíte styl nebo šablonu, kterou jste již vytvořili. Nezobrazí se pro ovládací prvek, který stále používá výchozí systémovou šablonu.

  V dialogovém okně **vytvořit prostředek stylu** můžete buď pojmenovat styl nebo šablonu, abyste ji mohli použít později, nebo můžete použít styl nebo šablonu pro všechny ovládací prvky tohoto typu.

  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")

> [!NOTE]
> Pro každý typ ovládacího prvku nelze vytvářet styly ani šablony. Pokud je ovládací prvek nepodporuje, tlačítko s popisem cesty se nezobrazí nad návrhovou plochou.
>
> Pokud se chcete vrátit do oboru úprav hlavního dokumentu, klikněte na **vrátit rozsah do** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b") .
>
> ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [vytvoří styl](https://www.youtube.com/watch?v=W8YdXDPeKdc).

### <a name="apply-a-style-or-template-to-a-control"></a>Použití stylu nebo šablony pro ovládací prvek
 Klikněte pravým tlačítkem myši na objekt na panelu [objekty a časová osa](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) , zvolte možnost **Upravit šablonu**a pak zvolte možnost **použít prostředek**.

 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")

### <a name="restore-the-default-style-or-template-of-a-control"></a>Obnovení výchozího stylu nebo šablony ovládacího prvku
 Vyberte ovládací prvek a na panelu [vlastnosti](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) vyhledejte vlastnost **styl** nebo **Šablona** . Potom klikněte na možnost **Pokročilá nastavení** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb") a potom v místní nabídce klikněte na tlačítko **obnovit** .

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a><a name="Visual"></a> Vizuální stavy: Změna vzhledu ovládacího prvku na základě jeho stavu
 Ovládací prvky mohou mít různé vizuální vzhledy na základě interakcí uživatelů. Například můžete nastavit, aby se tlačítko zeleně, když na něj uživatel klikne, nebo můžete spustit animaci. Můžete zkrátit nebo prodloužit dobu mezi vizuálními stavy pomocí přechodů.

 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [spravuje stav ovládacích prvků WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a><a name="Resources"></a> Prostředky: vytvořit barvy, styly a šablony a později je znovu použít
 V projektu můžete převést prakticky cokoli na prostředek. Prostředek je pouze objekt, který lze použít na různých místech aplikace. Můžete například vytvořit barvu jednou, nastavit ji jako prostředek a potom použít tuto barvu u několika objektů. Chcete-li změnit barvu všech těchto objektů, stačí změnit zdroj barvy.

 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-B153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [se stručným dotykem o prostředcích](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).

## <a name="see-also"></a>Viz také
 [Vytvoření uživatelského rozhraní pomocí nástroje Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
