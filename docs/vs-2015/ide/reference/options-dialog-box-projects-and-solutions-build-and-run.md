---
title: Dialogové okno Možnosti, projekty a řešení, sestavit a spustit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9669437ff47bc141c898a61c055b3a0de8d5d235
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189290"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Dialogové okno Možnosti, projekty a řešení, sestavit a spustit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
V tomto dialogovém okně můžete zadat maximální počet projekty Visual C++ nebo Visual C#, které můžete vytvářet ve stejnou dobu, určité výchozí chování sestavení a některá nastavení protokolu sestavení. Chcete-li otevřít **možnosti** dialogového okna zvolte **nástroje**, **možnosti** na řádku nabídek. Chcete-li získat přístup k této sadě možností, rozbalte **projekty a řešení**a klikněte na tlačítko **sestavíte a spustíte**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **maximální počet paralelních projektu sestavení**  
 Určuje maximální počet projekty Visual C++ a Visual C#, které můžete vytvářet ve stejnou dobu. K optimalizaci procesu sestavení, je maximální číslo sestavení paralelního projektu automaticky nastaví počet procesorů počítače. Maximální počet je 32.  
  
 **Pouze při spuštění sestavit projekty a závislosti**  
 Spouštěný projekt a jeho závislosti jsou vytvořeny-li toto zaškrtávací políčko je zaškrtnuto, pokud zvolíte klávesu F5; Zvolte **ladění**, **Start** v nabídce panelu; nebo zvolte **sestavení**, **sestavení** na řádku nabídek. Všechny projekty, závislosti a soubory řešení jsou vytvořeny, pokud toto políčko není zaškrtnuto, pokud zvolíte klávesu F5; Zvolte **ladění**, **Start** v nabídce panelu; nebo zvolte **sestavení**, **sestavení** na řádku nabídek. Tato možnost je ve výchozím nastavení zaškrtnuto.  
  
 **Spustit, pokud projekty jsou zastaralé**  
 > [!NOTE]
>  Tento seznam se vztahuje na [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] pouze pro projekty.  
  
 Ve výchozím nastavení, zobrazí se zpráva Pokud konfigurace projektu je zastaralý. když stisknutím klávesy F5 nebo vyberte **ladění**, **Start** na řádku nabídek. Můžete určit, zda chcete i přesto se projekt sestavil a určuje, zda se zobrazí zpráva. Tuto možnost použijte k určení, zda zpráva se zobrazí a jaké chování sestavení by měl být pokud zpráva se nezobrazí.  
  
 **Vždy sestavovat**  
 Do pole zpráva se nezobrazí a sestavení projektu bez ohledu na aktuální konfiguraci. Tato možnost je nastavena, když vyberete **tento dialog již příště nezobrazovat** pole ve zprávě a klikněte na tlačítko **Ano** tlačítko.  
  
 **Nikdy nesestavovat**  
 Do pole zpráva se nezobrazí a projekt není sestaven. Tato možnost je nastavena, když vyberete **tento dialog již příště nezobrazovat** pole ve zprávě a klikněte na tlačítko **ne** tlačítko.  
  
 **Dotázat se na sestavení**  
 Zobrazí okno se zprávou pokaždé, když konfigurace projektu je zastaralý.  
  
 **Při spuštění, při sestavení nebo dojde k chybě nasazení**  
 Pokud při spuštění sestavení z dojde k chybám sestavení **sestavení** nabídky, se zobrazí zpráva. Můžete zadat, jestli se má pokračovat spuštěním aplikace a určuje, zda zpráva se zobrazí pokaždé, když se chyby, která sestavení. Tuto možnost použijte k určení, zda zpráva se zobrazí a jaké chování je třeba pokud se nezobrazí zpráva.  
  
> [!NOTE]
>  Tato možnost se vztahuje na [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] pouze pro projekty.  
  
 **Dotázat se na spuštění**  
 Zobrazí okno se zprávou, které chyby sestavení pokaždé, když dojde k.  
  
 **Nespouštět**  
 Nezobrazuje okno se zprávou a aplikace není spuštěna. Tato možnost je nastavena, když vyberete **tento dialog již příště nezobrazovat** zaškrtněte políčko v okně se zprávou a klikněte na tlačítko **ne** tlačítko.  
  
 **Spustit starou verzi**  
 Do pole zpráva se nezobrazí a nově vytvořený verze aplikace není spuštěna. Tato možnost je nastavena, když vyberete **tento dialog již příště nezobrazovat** zaškrtněte políčko v okně se zprávou a klikněte na tlačítko **Ano** tlačítko.  
  
 **Nové řešení použít aktuálně zvolený projekt jako spouštěný projekt**  
 Pokud je toto políčko zaškrtnuto, nová řešení použít aktuálně zvolený projekt jako projekt po spuštění.  
  
 **Podrobnost výstupu sestavení projektu nástroje MSBuild**  
 Určuje, kolik informací se zobrazí v **výstup** okna pro sestavení.  
  
 **Úroveň podrobností MSBuild projektu sestavení protokolu souborů**  
 > [!NOTE]
>  Tato možnost se týká pouze projektů Visual C++.  
  
 Určuje, kolik informací je zapsána do souboru protokolu sestavení, které se nacházejí v \\... \\ *ProjectName*\Debug\\*ProjectName*. log.  
  
## <a name="see-also"></a>Viz také  
 [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)



