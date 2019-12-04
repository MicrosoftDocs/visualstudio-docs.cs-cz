---
title: 'Postupy: určení dalších možností instrumentace | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2d1f7e912ed5960c52e3f0bfa40fe9b87e91a2e6
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778697"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Postupy: určení dalších možností instrumentace

Binární soubory můžete instrumentovat pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio nebo pomocí nástrojů příkazového řádku. Pokud instrumentovat binární data z integrovaného vývojového prostředí (IDE), můžete řídit objem dat shromažďovaných během instrumentace tím, že zadáte další možnosti instrumentace pro nástroj [VSInstr](../profiling/vsinstr.md) . Tyto možnosti jsou k dispozici v relaci nebo na cílové úrovni. Pokud například chcete zahrnout nebo vyloučit konkrétní funkce během procesu instrumentace, použijte možnost Další instrumentace na cílové úrovni.

> [!IMPORTANT]
> Každý vložený test upraví chování původního programu mírně. Tato změna způsobí režii v době analýzy. I když je aproximace této režie odečtena, má stále jemný efekt časování u vícevláknových aplikací. Možnosti nástroje [VSInstr](../profiling/vsinstr.md) slouží k řízení shromažďování dat během profilace.

## <a name="to-specify-additional-instrumentation-option"></a>Určení dalších možností instrumentace

1. V **prohlížeč výkonu**vyberte **relaci výkonu** , klikněte na ni pravým tlačítkem a vyberte **vlastnosti**.

2. Na **stránkách vlastnosti**klikněte na **Upřesnit** vlastnosti.

3. Možnosti typu v poli **Další možnosti instrumentace** .

     Například použijte/CONTROL: THREAD k určení úrovně profilace. Úplný seznam možností najdete v tématu [VSInstr](../profiling/vsinstr.md).

4. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)
[profilu z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
