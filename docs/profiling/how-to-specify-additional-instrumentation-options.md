---
title: Zadat další možnosti instrumentace | Microsoft Docs
description: Přečtěte si, jak můžete instrumentovat binární soubory pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio nebo pomocí nástrojů příkazového řádku.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5652088b3b90c7dd9df067c81d8eb38fe348ec19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906876"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Postupy: Určení dalších možností instrumentace

Binární soubory můžete instrumentovat pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio nebo pomocí nástrojů příkazového řádku. Pokud instrumentovat binární data z integrovaného vývojového prostředí (IDE), můžete řídit objem dat shromažďovaných během instrumentace tím, že zadáte další možnosti instrumentace pro nástroj [VSInstr](../profiling/vsinstr.md) . Tyto možnosti jsou k dispozici v relaci nebo na cílové úrovni. Pokud například chcete zahrnout nebo vyloučit konkrétní funkce během procesu instrumentace, použijte možnost Další instrumentace na cílové úrovni.

> [!IMPORTANT]
> Každý vložený test upraví chování původního programu mírně. Tato změna způsobí režii v době analýzy. I když je aproximace této režie odečtena, má stále jemný efekt časování u vícevláknových aplikací. Možnosti nástroje [VSInstr](../profiling/vsinstr.md) slouží k řízení shromažďování dat během profilace.

## <a name="to-specify-additional-instrumentation-option"></a>Určení dalších možností instrumentace

1. V **prohlížeč výkonu** vyberte **relaci výkonu** , klikněte na ni pravým tlačítkem a vyberte **vlastnosti**.

2. Na **stránkách vlastnosti** klikněte na **Upřesnit** vlastnosti.

3. Možnosti typu v poli **Další možnosti instrumentace** .

     Například použijte/CONTROL: THREAD k určení úrovně profilace. Úplný seznam možností najdete v tématu [VSInstr](../profiling/vsinstr.md).

4. Klikněte na **OK**.

## <a name="see-also"></a>Viz také

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
