---
title: 'Postupy: určení příkazů před a po instrumentaci | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab7ecbe97ba0b174a1cc4c0f0d169834ce25e8d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788902"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Postupy: Určení příkazů k provedení před instrumentací a po instrumentaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zadat příkazy, které se spustí před nebo po binárních souborech v relaci výkonu. Libovolný příkaz, který lze vydat z příkazového řádku, lze zadat jako událost před instrumentací nebo po instrumentaci. Můžete například zadat příkazy, které automatizují Opětovné podepsání sestavení pomocí klíče silného názvu v dávkovém souboru, který je spuštěn po instrumentaci binárních souborů.  
  
 Můžete zadat příkazy pro všechny instrumentované binární soubory při spuštění profilování nebo pro jednotlivé binární soubory. Můžete ale zadat jenom jeden příkaz před instrumentací, který se spustí před a jenom jeden příkaz po instrumentaci, který se spustí po procesu instrumentace. Nemůžete zadat příkazy pro všechny binární soubory a pro jednotlivé binární soubory. Když zadáte příkazy pro všechny binární soubory, příkazy se spustí před nebo po instrumentaci každého binárního souboru v relaci.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Pracovní adresář, ve kterém jsou spouštěny příkazy, závisí na operačním systen, kde běží [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] a na cílové platformě profilované aplikace.  
  
  **32 – bitové počítače**  
  
  V 32 počítačích je výchozím adresářem nástrojů profileru Drive\Program Files\Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools.  
  
  **64bitové počítače**  
  
  Na 64 počítačů zadejte cestu podle cílové platformy profilované aplikace:  
  
- Pro 32 aplikací je výchozím adresářem nástrojů profileru:  
  
   *Jednotka*\Program Files (x86) \Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools  
  
- Pro 64 aplikací je výchozím adresářem nástrojů profileru:  
  
   *Jednotka*\Program Files (x86) \Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Určení příkazů před instrumentací  
  
1. Proveďte jeden z následujících kroků:  
  
    - Chcete-li určit příkazy před instrumentací pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu**a potom klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.  
  
    - Chcete-li určit příkazy před instrumentací pro konkrétní binární soubor, klikněte pravým tlačítkem myši na název binárního souboru v seznamu **cílů** relace výkonu a poté vyberte možnost **vlastnosti**.  
  
2. Na **stránkách vlastností**klikněte na **instrumentace**.  
  
3. Do textového pole **příkazový řádek** v části **události před instrumentací**zadejte příkaz.  
  
    > [!NOTE]
    > Můžete kliknout na tlačítko se třemi tečkami **(...)** sousedící s polem **příkazového řádku** a vyhledat a vybrat odpovídající soubor. exe,. cmd nebo. bat.  
  
4. Klikněte na **OK**.  
  
     Pokud chcete zakázat spuštění příkazu bez jeho odebrání, zaškrtněte políčko **vyloučit z instrumentace** . Chcete-li upravit nastavení kompilátoru nebo linkeru, použijte stránky vlastností projektu.  
  
### <a name="to-specify-post-instrument-commands"></a>Určení příkazů po instrumentaci  
  
1. Proveďte jeden z následujících kroků:  
  
    - Chcete-li určit příkazy po instrumentaci pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu**a potom klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.  
  
    - Chcete-li určit příkazy po instrumentaci pro konkrétní binární soubor, klikněte pravým tlačítkem myši na název binárního souboru v seznamu **cílů** relace výkonu a poté vyberte možnost **vlastnosti**.  
  
2. Na **stránkách vlastností**klikněte na **instrumentace**.  
  
3. Do textového pole **příkazový řádek** zadejte příkaz v části **události po instrumentaci**.  
  
    > [!NOTE]
    > Můžete kliknout na tlačítko se třemi tečkami **(...)** sousedící s polem **příkazového řádku** a vyhledat a vybrat odpovídající soubor. exe,. cmd nebo. bat.  
  
4. Klikněte na **OK**.  
  
     Pokud chcete zakázat spuštění příkazu bez jeho odebrání, zaškrtněte políčko **vyloučit z instrumentace** . Chcete-li upravit nastavení kompilátoru nebo linkeru, použijte stránky vlastností projektu.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
