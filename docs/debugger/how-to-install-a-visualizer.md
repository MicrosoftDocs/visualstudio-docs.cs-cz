---
title: 'Postupy: instalace Vizualizátoru | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 494287c6691d27eb636f92eff324eecf49daf5fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187576"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření Vizualizér musíte nainstalovat vizualizér, aby byl dostupný v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalace Vizualizátoru je jednoduchý proces.

> [!NOTE]
> V aplikacích pro UWP jsou podporované jenom standardní vizualizace textu, HTML, XML a JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.

### <a name="to-install-a-visualizer"></a>Instalace Vizualizátoru

1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Pokud chcete použít spravovaný Vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.

4. Restartujte ladicí relaci.

## <a name="see-also"></a>Viz také:
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [How to: Write a Visualizer](create-custom-visualizers-of-data.md)