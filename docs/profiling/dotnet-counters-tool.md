---
title: Vizualizace čítačů dotnet | Microsoft Docs
description: Naučte se používat nástroj čítače .NET v profileru výkonu sady Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905025"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Vizualizace čítačů dotnet z profileru sady Visual Studio


Nástroj čítače .NET umožňuje vizualizovat [čítače dotnet](/dotnet/core/diagnostics/dotnet-counters) v průběhu času přímo v rámci profileru sady Visual Studio.


> [!NOTE]
> Nástroj čítače .NET vyžaduje Visual Studio 2019 verze 16,7 nebo novější a cílí na .NET Core 3.0 +.

## <a name="setup"></a>Nastavení

1. V aplikaci Visual Studio otevřete Profiler výkonu (**ALT + F2** nebo **Profiler-> výkonu**).

2. Zaškrtněte políčko **čítače rozhraní .NET** .

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Byl vybrán nástroj čítače.":::

3. Kliknutím na tlačítko **Spustit** nástroj spustíte.

Další informace o tom, jak optimalizovat výkon nástroje, najdete v tématu [optimalizace nastavení profileru](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Pochopení vašich dat

I když nástroj zpočátku shromažďuje data, vidíte živé hodnoty [čítačů dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Shromažďování nástroje čítače .NET":::

Grafy čítačů můžete zobrazit také tak, že vyberete zaškrtávací políčko vedle názvů čítačů. V každém okamžiku můžete zobrazit grafy více čítačů.


Jakmile budete pracovat s aplikací a shromažďovat data, můžete zastavit shromažďování pro ještě podrobnější sestavu. Provedete to tak, že stisknete tlačítko **Zastavit shromažďování** .


Po načtení sestavy by se měla zobrazit finální sestava podobná té, kterou vidíte níže.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Sestava nástroje čítače .NET.":::

Tato sestava obsahuje následující hodnoty:

- Min – minimální hodnota pro tento čítač ve vybraném časovém rozsahu.
- Max – maximální hodnota pro tento čítač ve vybraném časovém rozsahu.
- Average – průměrná hodnota pro tento čítač ve vybraném časovém rozsahu.

Sloupce v tabulce můžete filtrovat nebo přidat tak, že kliknete pravým tlačítkem na záhlaví sloupců a vyberete záhlaví.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Sloupce nástroje čítače .NET.":::

Grafy můžete v podrobné sestavě zobrazit také zaškrtnutím políčka vedle položky čítače. Data v tabulkách představují hodnoty celé doby trvání shromážděného trasování ve výchozím nastavení. Pokud chcete data filtrovat podle určitého časového rozsahu, klikněte a přetáhněte je na grafy.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtrování času nástroje čítače .NET":::

Tabulka aktualizuje příslušné hodnoty pro čas vybraný v grafech. Pomocí tlačítka **Vymazat výběr** obnovíte vybraný časový rozsah na celé trasování.


## <a name="see-also"></a>Viz také

- [Optimalizace nastavení profileru](../profiling/optimize-profiler-settings.md)
- [čítače dotnet](/dotnet/core/diagnostics/dotnet-counters)
