---
title: Vizualizace ukázkových dat v uživatelském rozhraní XAML
titleSuffix: Blend for Visual Studio
description: Naučte se generovat ukázková data od začátku nebo ze stávající třídy v Blend pro Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7b8025f7212d28d2cfce482f67ef672a472993bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920106"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Zobrazit data v Blend pro Visual Studio

Ukázková data můžete zobrazit v návrháři při přizpůsobování rozložení stránek. Můžete vygenerovat ukázková data od začátku nebo pomocí existující třídy. Můžete se také připojit k *živým datům* , která se zobrazí v aplikaci při jejím spuštění.

> [!NOTE]
> Panel **data** v Blendu je podporován pouze pro projekty, které cílí na .NET Framework. Pro projekty UWP nebo projekty, které cílí na .NET Core, se nepodporuje.

## <a name="generate-sample-data"></a>Generování ukázkových dat

Chcete-li generovat ukázková data, otevřete dokument XAML. Na panelu **data** klikněte na tlačítko **Vytvořit Ukázková** data ![ Vytvořit Ukázková data ](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) a pak zvolte **Nová ukázková data**.

Na panelu **data** definujte strukturu vašich dat a potom ji navažte na prvky uživatelského rozhraní na libovolné stránce.

![Panel data](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Pokud chcete, aby se vaše ukázková data zobrazovala na stránkách, když aplikaci spouštíte, zvolte možnost **zdroj** dat ![ Ikona Možnosti zdroje dat ](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png) a pak zvolte **Povolit při spuštění aplikace**.

![Povolit při spuštění položky nabídky aplikace](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Podívejte se na krátké video:** ![ Ikona přehrát – ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Vytvořit Ukázková data od začátku](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2&preserve-view=true)

## <a name="generate-sample-data-from-a-class"></a>Generování ukázkových dat z třídy

Pokud jste již vytvořili třídy, které popisují strukturu vašich dat, můžete z nich vygenerovat ukázková data.

Chcete-li generovat ukázková data z třídy, otevřete dokument XAML a poté na panelu **data** klikněte na tlačítko **Vytvořit Ukázková** data ![ Vytvořit Ukázková data ](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) a potom klikněte na možnost **Vytvořit Ukázková data z třídy**.

**Podívejte se na krátké video:** ![ Ikona přehrát ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [se smíchá s několika vazbami dat pomocí Blendu](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Viz také

- [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)