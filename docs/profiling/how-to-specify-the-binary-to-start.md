---
title: Zadejte binární soubor, který se má spustit. | Microsoft Docs
description: Přečtěte si, jak je nutné zadat informace v <Target> dialogovém okně stránky vlastností, abyste mohli profilovat binární soubory, jako jsou knihovny DLL.
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 715c92a26ae33a4e909ec737c866be1cdc15251e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721837"
---
# <a name="how-to-specify-the-binary-to-start"></a>Postupy: Určení binárního souboru ke spuštění

Chcete-li profilovat binární soubory, jako jsou knihovny DLL, je nutné zadat informace v dialogovém okně **\<Target> stránky vlastností** . Tyto informace označují, kde projekt knihovny DLL může najít volající aplikaci.

1. V **prohlížeč výkonu** klikněte pravým tlačítkem myši na cílový binární soubor a pak klikněte na **vlastnosti**.

2. V dialogovém okně **stránky vlastností** klikněte na vlastnosti **spuštění** .

3. Vyberte zaškrtávací políčko **přepsat vlastnosti projektu** .

4. Do textového pole **spustitelný soubor ke spuštění** zadejte umístění souboru.

5. Do textového pole **argumenty** zadejte argumenty, které jsou požadovány ke spuštění aplikace.

6. Do textového pole **pracovní adresář** zadejte umístění adresáře.

7. Klikněte na **OK**.

## <a name="see-also"></a>Viz také

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
