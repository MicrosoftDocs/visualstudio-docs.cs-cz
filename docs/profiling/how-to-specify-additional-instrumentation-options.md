---
title: 'Postup: Zadání dalších možností instrumentace | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778697"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Postupy: Určení dalších možností instrumentace

Můžete instrumentovat binární soubory pomocí ide sady Visual Studio nebo pomocí nástrojů příkazového řádku. Pokud instrumentujete binární soubor z ide, můžete řídit objem dat, která jsou shromažďována během instrumentace zadáním dalších možností instrumentace pro nástroj [VSInstr.](../profiling/vsinstr.md) Tyto možnosti jsou k dispozici na úrovni relace nebo cílové úrovně. Chcete-li například zahrnout nebo vyloučit určité funkce během procesu instrumentace, použijte možnost další instrumentace na cílové úrovni.

> [!IMPORTANT]
> Každá sonda, která je vložena mírně upraví chování původního programu. Tato změna způsobí režii v době analýzy. I když aproximace této režie se odečte, stále má jemné časování účinky na vícevláknové aplikace. Možnosti nástroje [VSInstr](../profiling/vsinstr.md) pomáhají řídit shromažďování dat během profilování.

## <a name="to-specify-additional-instrumentation-option"></a>Určení další možnosti instrumentace

1. V **Průzkumníku výkonu**vyberte **relaci výkonu** a potom klepněte pravým tlačítkem myši a vyberte **vlastnosti**.

2. Na **stránkách vlastností**klepněte na **vlastnosti Upřesnit.**

3. Zadejte možnosti do pole **Další možnosti instrumentace.**

     Například použijte /CONTROL:THREAD k určení úrovně profilování. Úplný seznam možností naleznete v tématu [VSInstr](../profiling/vsinstr.md).

4. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také

[Konfigurace profilu výkonových relací](../profiling/configuring-performance-sessions.md)
[z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
