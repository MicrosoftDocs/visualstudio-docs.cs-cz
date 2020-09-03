---
title: Uspořádání objektů do kontejnerů rozložení v Návrháři XAML
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ebe96ec84d957c5ac8dcb6bad0a388ba3318c0fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86459291"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Uspořádání objektů do kontejnerů rozložení v Návrháři XAML

Tento článek popisuje panely rozložení a ovládací prvky pro Návrhář XAML.

Představte si, kde byste chtěli zobrazit objekty na objektech stránky, jako jsou &mdash; obrázky, tlačítka a videa. Možná budete chtít, aby se zobrazovaly v řádcích a sloupcích, na jednom řádku svisle nebo vodorovně nebo na pevných pozicích.

Až budete mít možnost si představit, jak se stránka může zobrazit, vyberte panel rozložení. Všechny stránky začínají na jednom, protože potřebujete něco, ke kterému přidáte objekty. Ve výchozím nastavení je to **Mřížka**, ale můžete ji změnit.

Panely rozložení vám pomohou uspořádat objekty na stránce, ale mají větší hodnotu. Umožňují vám navrhovat různé velikosti a rozlišení obrazovky. Když uživatelé spustí vaši aplikaci, vše v panelu rozložení mění velikost tak, aby odpovídala skutečnému vzhledu zařízení na obrazovce. Samozřejmě, pokud nechcete, aby to vaše rozložení mělo, můžete toto chování přepsat pro část rozložení nebo celé rozložení. Můžete použít vlastnosti Height a Width k řízení.

## <a name="layout-panels"></a>Panely rozložení

Začněte svou stránku výběrem jednoho z těchto panelů rozložení. Vaše stránka může mít víc než jednu. Například můžete začít s panelem rozložení **mřížky** a pak přidat **StackPanel** do oblasti v **mřížce** , aby bylo možné uspořádat ovládací prvky v daném prvku svisle.

Níže jsou používány následující panely rozložení, ale existují i jiné. Vše najdete v **sadě nástrojů v sadě** Visual Studio nebo na panelu **aktiva** v Blend pro Visual Studio.

### <a name="grid"></a>Mřížka

Uspořádá objekty do řádků a sloupců.

![Panel rozložení mřížky](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Uspořádejte objekty do oblastí mřížky EQUAL nebo Uniform. Tento panel je skvělý pro uspořádání seznamu imagí.

(K dispozici pouze pro projekty WPF.)

![Panel rozložení UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Plátno

Uspořádejte objekty tak, jak chcete. Když uživatelé spustí vaši aplikaci, budou mít tyto prvky na obrazovce pevně stanovené pozice.

![Panel rozložení plátna](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Uspořádá objekty v jednom řádku vodorovně nebo svisle.

![Panel rozložení StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Uspořádá objekty postupně zleva doprava. Když je panel mimo prostor v pravém horním rohu, *zalomí* obsah na další řádek, a tak dále zleva doprava (shora dolů). Můžete také nastavit orientaci svislého panelu, aby objekty byly předávány shora dolů a zleva doprava.

(K dispozici pouze pro projekty WPF.)

![Panel rozložení objektu WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Uspořádejte objekty tak, aby zůstaly nebo *ukotveny*k jednomu okraji panelu.

(K dispozici pouze pro projekty WPF.)

![Panel rozložení DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Podívejte se na krátké video:** ![ Tlačítko Přehrát ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF – DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Ovládací prvky rozložení

Můžete také přidat objekty do ovládacích prvků rozložení. Nejsou jako panel rozložení s funkcemi, ale můžou být pro určité scénáře užitečné.

Následující ovládací prvky rozložení jsou nejoblíbenější, ale existují i jiné. Vše najdete v **sadě nástrojů v sadě** Visual Studio nebo na panelu **aktiva** v Blend pro Visual Studio.

### <a name="border"></a>Ohraničení

Vytvořte ohraničení, pozadí nebo obojí kolem objektu. Do **ohraničení**lze přidat pouze jeden objekt. Chcete-li použít ohraničení nebo pozadí pro více než jeden objekt, přidejte do **ohraničení**panel rozložení. Pak přidejte objekty do tohoto panelu nebo ovládacího prvku.

![Ovládací prvek rozložení ohraničení](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Překryvný

Zobrazit informace nebo možnosti uživatelům v okně. Do **překryvného okna**lze přidat pouze jeden objekt. Ve výchozím nastavení obsahuje **automaticky otevírané okno** **mřížku**, ale můžete ho změnit.

### <a name="scrollviewer"></a>ScrollViewer

Umožní uživatelům procházet stránku nebo oblast stránky. Do **ScrollViewer**můžete přidat pouze jeden objekt, takže má smysl přidat panel rozložení, jako je například **Mřížka** nebo **StackPanel**.

![Ovládací prvek rozložení ScrollViewer](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Škálujte objekty podobně, jako byste měli ovládací prvek Lupa. Do **Viewbox**můžete přidat pouze jeden objekt. Chcete-li tento efekt použít pro více než jeden objekt, přidejte do **Viewbox**panel rozložení a pak přidejte ovládací prvky do tohoto panelu rozložení.

![Ovládací prvek rozložení ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Viz také

- [Práce s elementy v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
