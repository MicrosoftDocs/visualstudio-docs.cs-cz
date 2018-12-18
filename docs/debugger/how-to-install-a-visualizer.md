---
title: 'Postupy: instalace Vizualizéru | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87feaebf16168744467137fdf4af54538a316cdf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473774"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření vizualizéru, musíte nainstalovat vizualizér tak, že bude k dispozici v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalace vizualizéru je jednoduchý proces.  
  
> [!NOTE]
>  V aplikacích pro UPW, pouze standardní text, HTML, XML a JSON vizualizérech podporují. Vizualizérech vlastní (vytvořené uživatelem) nejsou podporovány.  
  
### <a name="to-install-a-visualizer"></a>Instalace vizualizéru  
  
1.  Vyhledejte knihovnu DLL, která obsahuje vizualizér, kterou jste vytvořili.  
  
2.  Kopie knihovny DLL na jednu z následujících umístění:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Pokud chcete použít spravované vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.  
  
4.  Restartujte relaci ladění.  
  
## <a name="see-also"></a>Viz také  
 [Vytvořit vlastní Vizualizérech](../debugger/create-custom-visualizers-of-data.md)   
 [Postupy: zápis Vizualizéru](../debugger/how-to-write-a-visualizer.md)