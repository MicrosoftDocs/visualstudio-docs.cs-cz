---
title: 'Postupy: určení příkazů k provedení před instrumentací a po instrumentaci | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b88d49be8ee4651d82135b3e8d27bef8218ffd43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772219"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Postupy: Určení příkazů k provedení před instrumentací a po instrumentaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zadat příkazy, které spustit před nebo po jsou instrumentované binární soubory v relaci výkonu. Jakýkoli příkaz, který může být vydán z příkazového řádku můžete zadat jako před instrumentací nebo události po instrumentaci. Například můžete zadat příkazy, které automatizují opětovného podepsání sestavení silným názvem klíčem v dávkovém souboru, který se spouští po binární soubory jsou instrumentovány.  
  
 Můžete zadat příkazy pro instrumentované binární soubory při spuštění profilování nebo jednotlivých binárních souborů. Můžete však zadat jenom jeden příkaz před instrumentací prováděný a pouze jeden příkaz po instrumentaci spustit po dokončení procesu instrumentace. Nelze zadat příkazy pro obě všechny binární soubory a jednotlivých binárních souborů. Při zadávání příkazů pro všechny binární soubory jsou spouštěny příkazy před nebo po instrumentaci každého binárního souboru v relaci.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Pracovní adresář, ve kterém jsou spouštěny příkazy závisí na provozní systen, kde je spuštěn nástroj [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] a na cílové platformě profilované aplikace.  
  
  **32bitových počítačích**  
  
  Na 32bitových počítačích je výchozí adresář nástrojů profilování 10.0\Team disk\Program Files\Microsoft Visual Studio Tools nástroje.  
  
  **64bitové počítače**  
  
  Na 64bitových počítačích zadejte cestu podle cílové platformy profilované aplikace:  
  
- Pro 32bitové aplikace je výchozí adresář nástrojů profilování:  
  
   *Jednotka*\Program soubory (x86) \Microsoft Visual Studio 10.0\Team nástroje nástroje  
  
- Pro 64bitové aplikace je výchozí adresář nástrojů profilování:  
  
   *Jednotka*\Program soubory (x86) \Microsoft Visual Studio 10.0\Team nástroje Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Chcete-li určit příkazy před instrumentací  
  
1.  Proveďte jeden z následujících kroků:  
  
    -   Pokud chcete zadat příkazy před instrumentací pro všechny binární soubory do relace výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu**a pak klikněte pravým tlačítkem a vyberte **vlastnosti**.  
  
    -   Pokud chcete zadat příkazy před instrumentací pro konkrétní binární soubor, klikněte pravým tlačítkem na název binárního souboru v **cíle** seznam výkonnostní relaci a pak vyberte **vlastnosti**.  
  
2.  V **stránky vlastností**, klikněte na tlačítko **instrumentace**.  
  
3.  Zadejte příkaz v **příkazového řádku** textového pole pod **události před Instrumentací**.  
  
    > [!NOTE]
    >  Můžete kliknout na tlačítko se třemi tečkami **(...)**  , který je vedle **příkazového řádku** pole vyhledejte a vyberte příslušný soubor .exe, .cmd nebo. bat.  
  
4.  Klikněte na tlačítko **OK**.  
  
     Chcete-li zakázat spouštění příkazu ale neodebrali, vyberte **vyloučit z instrumentace** zaškrtávací políčko. Pokud chcete upravit kompilátoru nebo linkeru, nastavení, použijte stránky vlastností projektu.  
  
### <a name="to-specify-post-instrument-commands"></a>Chcete-li určit příkazy po instrumentaci  
  
1.  Proveďte jeden z následujících kroků:  
  
    -   Pokud chcete zadat příkazy po instrumentaci pro všechny binární soubory do relace výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu**a pak klikněte pravým tlačítkem a vyberte **vlastnosti**.  
  
    -   Pokud chcete zadat příkazy po instrumentaci pro konkrétní binární soubor, klikněte pravým tlačítkem na název binárního souboru v **cíle** seznam výkonnostní relaci a pak vyberte **vlastnosti**.  
  
2.  V **stránky vlastností**, klikněte na tlačítko **instrumentace**.  
  
3.  Zadejte příkaz v **příkazového řádku** textového pole pod **události po instrumentaci**.  
  
    > [!NOTE]
    >  Můžete kliknout na tlačítko se třemi tečkami **(...)**  , který je vedle **příkazového řádku** pole vyhledejte a vyberte příslušný soubor .exe, .cmd nebo. bat.  
  
4.  Klikněte na tlačítko **OK**.  
  
     Chcete-li zakázat spouštění příkazu ale neodebrali, vyberte **vyloučit z instrumentace** zaškrtávací políčko. Pokud chcete upravit kompilátoru nebo linkeru, nastavení, použijte stránky vlastností projektu.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)



