---
title: 'Postupy: instalace Vizualizátoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796971"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po vytvoření Vizualizér je nutné nainstalovat vizualizér, aby byl dostupný v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Instalace Vizualizátoru je jednoduchý proces.  
  
> [!NOTE]
> V aplikacích pro **Store** se podporují jenom standardní texty, HTML, XML a vizualizace JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.  
  
### <a name="to-install-a-visualizer"></a>Instalace Vizualizátoru  
  
1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.  
  
2. Zkopírujte knihovnu DLL do některého z následujících umístění:  
  
    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3. Pokud chcete použít spravovaný Vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.  
  
4. Restartujte ladicí relaci.  
  
## <a name="see-also"></a>Viz také  
 [Vytvořit vlastní vizualizace](../debugger/create-custom-visualizers-of-data.md)   
 [Postupy: Zápis vizualizéru](../debugger/how-to-write-a-visualizer.md)
