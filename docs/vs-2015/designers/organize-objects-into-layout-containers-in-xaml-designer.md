---
title: Uspořádání objektů do kontejnerů rozložení v Návrhář XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90c30f27ada6673608a1c5cf9500207f9aeb2d72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664196"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Uspořádání objektů do kontejnerů rozložení v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Představte si, kde byste chtěli, aby se objekty zobrazovaly na stránce. objekty, jako jsou obrázky, tlačítka a videa. Možná budete chtít, aby se zobrazovaly v řádcích a sloupcích, na jednom řádku svisle nebo vodorovně nebo na pevných pozicích.

 Až budete mít možnost si představit, jak se stránka může zobrazit, vyberte panel rozložení. Všechny stránky začínají na jeden, protože potřebujete něco k přidání vašich objektů do. Ve výchozím nastavení se jedná o **mřížku** , ale můžete ji změnit.

 Panely rozložení vám pomohou uspořádat objekty na stránce, ale mají větší hodnotu. Umožňují vám navrhovat různé velikosti a rozlišení obrazovky. Když uživatelé spustí vaši aplikaci, vše v panelu rozložení mění velikost tak, aby odpovídala skutečnému vzhledu zařízení na obrazovce. Samozřejmě, pokud nechcete, aby to vaše rozložení mělo, můžete toto chování přepsat pro část rozložení nebo celé rozložení. Můžete použít vlastnosti Height a Width k řízení.

 Tato stránka popisuje panely rozložení a ovládací prvky a následně vás přesměruje na krátká videa, která vám pomůžou začít s nimi.

> [!NOTE]
> Některá videa mohou odkazovat na Blend nebo Blend Expression, který používá stejného návrháře XAML jako sadu Visual Studio a Blend pro Visual Studio.

## <a name="layout-panels"></a>Panely rozložení
 Začněte svou stránku výběrem jednoho z těchto panelů rozložení. Vaše stránka může mít víc než jednu. Například můžete začít s panelem rozložení **mřížky** a pak přidat **StackPanel** do oblasti v **mřížce** , aby bylo možné uspořádat ovládací prvky v daném prvku svisle.

 Níže jsou používány následující panely rozložení, ale existují i jiné. Můžete je najít na panelu **aktiva** .

- [Mřížka](#Grid)

- [UniformGrid](#Uniform)

- [Plátno](#Canvas)

- [StackPanel](#Stack)

- [WrapPanel](#Wrap)

- [DockPanel](#Dock)

### <a name="grid"></a><a name="Grid"></a> Mřížky
 Uspořádá objekty do řádků a sloupců.

 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pomocí mřížek](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)

### <a name="uniformgrid"></a><a name="Uniform"></a> UniformGrid
 Uspořádejte objekty do oblastí mřížky EQUAL nebo Uniform. Tento panel je skvělý pro uspořádání seznamu imagí.

 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")

 (K dispozici pouze pro projekty WPF)

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)

### <a name="canvas"></a><a name="Canvas"></a> Kreslicí
 Uspořádejte objekty tak, jak chcete. Když uživatelé spustí vaši aplikaci, budou mít tyto prvky na obrazovce pevně stanovené pozice.

 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících na plátně](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)

### <a name="stackpanel"></a><a name="Stack"></a> StackPanel
 Uspořádá objekty v jednom řádku vodorovně nebo svisle.

 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s StackPanel a objektu WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)

### <a name="wrappanel"></a><a name="Wrap"></a> Objektu WrapPanel
 Uspořádá objekty postupně zleva doprava. Když je panel mimo prostor v pravém horním rohu, *zalomí* obsah na další řádek, a tak dále zleva doprava (shora dolů). Můžete také nastavit orientaci svislého panelu, aby objekty byly předávány shora dolů a zleva doprava.

 (K dispozici pouze pro projekty WPF)

 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s StackPanel a objektu WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)

### <a name="dockpanel"></a><a name="Dock"></a> DockPanel
 Uspořádejte objekty tak, aby zůstaly nebo *ukotveny*k jednomu okraji panelu.

 (K dispozici pouze pro projekty WPF)

 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF-DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Ovládací prvky rozložení
 Můžete také přidat objekty do ovládacích prvků rozložení. Nejsou jako panel rozložení s funkcemi, ale můžou být pro určité scénáře užitečné.

 Následující ovládací prvky rozložení se používají nejoblíbenějším, ale existují i jiné. Můžete je najít na panelu **aktiva** .

- [Ohraničení](#Border)

- [Překryvný](#Popup)

- [ScrollViewer](#Scroll)

- [UniformGrid](#Uniform)

- [Viewbox](#View)

### <a name="border"></a><a name="Border"></a> Sousedící
 Vytvořte ohraničení, pozadí nebo obojí kolem objektu. Do **ohraničení**lze přidat pouze jeden objekt. Chcete-li použít ohraničení nebo pozadí pro více než jeden objekt, přidejte do **ohraničení**panel rozložení. Pak přidejte objekty do tohoto panelu nebo ovládacího prvku.

 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujících s ohraničením](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)

### <a name="popup"></a><a name="Popup"></a> Oken
 Zobrazit informace nebo možnosti uživatelům v okně. Do **překryvného okna**lze přidat pouze jeden objekt. Ve výchozím nastavení obsahuje **automaticky otevírané okno** **mřížku** , ale můžete ho změnit.

### <a name="scrollviewer"></a><a name="Scroll"></a> ScrollViewer
 Možnost Povolit používá se k posouvání stránky nebo oblasti stránky. Do **ScrollViewer** můžete přidat pouze jeden objekt, aby bylo mnohem vhodné přidat panel rozložení, jako je například **Mřížka** nebo **StackPanel**.

 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")

### <a name="viewbox"></a><a name="View"></a> Viewbox
 Škálujte objekty podobně, jako byste měli ovládací prvek Lupa. Do **Viewbox**můžete přidat pouze jeden objekt. Chcete-li tento efekt použít pro více než jeden objekt, přidejte do **Viewbox**panel rozložení a pak přidejte ovládací prvky do tohoto panelu rozložení.

 (K dispozici pouze pro projekty WPF)

 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")

## <a name="see-also"></a>Viz také
 [Práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md) [vytváření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
