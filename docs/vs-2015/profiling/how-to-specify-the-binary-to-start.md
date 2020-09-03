---
title: 'Postupy: Určení binárního souboru ke spuštění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 919e84393cf4aef929a504aadbefe905afe24bfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203426"
---
# <a name="how-to-specify-the-binary-to-start"></a>Postupy: Určení binárního souboru ke spuštění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li profilovat binární soubory, jako jsou knihovny DLL, je nutné zadat informace v dialogovém okně ** \<Target> stránky vlastností** . Tyto informace označují, kde projekt knihovny DLL může najít volající aplikaci.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Určení spustitelného souboru, který se má spustit  
  
1. V **prohlížeč výkonu**klikněte pravým tlačítkem myši na cílový binární soubor a pak klikněte na **vlastnosti**.  
  
2. V dialogovém okně **stránky vlastností** klikněte na vlastnosti **spuštění** .  
  
3. Vyberte zaškrtávací políčko **přepsat vlastnosti projektu** .  
  
4. Do textového pole **spustitelný soubor ke spuštění** zadejte umístění souboru.  
  
5. Do textového pole **argumenty** zadejte argumenty, které jsou požadovány ke spuštění aplikace.  
  
6. Do textového pole **pracovní adresář** zadejte umístění adresáře.  
  
7. Klikněte na **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
