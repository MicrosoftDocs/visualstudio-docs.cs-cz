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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575a55ae654ada9774abed510d66b94e4ce9d271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899538"
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
