---
title: 'Postup: Zadejte binární hodnotu na začátek | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fd3379b9769cfd6bfe1335b12545e635a9bde782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778684"
---
# <a name="how-to-specify-the-binary-to-start"></a>Postup: Zadejte binární soubor, který má být zahájen

Chcete-li profilovat binární soubory, například knihovny ** \<** DLL, musíte zadat informace do dialogového okna Cílové> stránky vlastností. Tyto informace označují, kde projekt DLL může najít volající aplikaci.

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na cílový binární soubor a potom klepněte na příkaz **Vlastnosti**.

2. V dialogovém okně **Stránky vlastností** klikněte na vlastnosti **Spustit.**

3. Zaškrtněte políčko **Přepsat vlastnosti projektu.**

4. V textovém poli **Spustitelný soubor** zadejte umístění souboru.

5. V textovém poli **Argumenty** zadejte argumenty, které jsou nutné ke spuštění aplikace.

6. V textovém poli **Pracovní adresář** zadejte umístění adresáře.

7. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
